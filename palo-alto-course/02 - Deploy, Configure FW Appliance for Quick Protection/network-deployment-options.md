# Network Deployment Options

## Layer 3, NAT and DHCP

### Change Security Zones

- Network > Zones

  - Trust > Type : Change to Layer 3

  - Untrust > Type : Change to Layer 3

- Network > Interfaces

  - ethernet1 (external) > Interface Type : Layer 3

    - Virtual Router: default

    - Security Zone: untrust

    - IPV4 Tab: Change IP to `198.51.100.2/28`

  - ethernet2 (internal) > Interface Type : Layer 3

    - Virtual Router: default

    - Security Zone: trust

    - IPV4 Tab: Change IP to `10.0.0.1/24`

    - Advanced Tab: Management Profile

      - Name: ping

      - Check `Ping`

- Virtual Router

  - Edit > Static Routes Tab > Add
    - Name: default_route

    - Destination: `0.0.0.0/0`

    - Interface: ethernet1

    - Next Hop: IP Address `198.51.100.1` (IP address of router upstream)

### DHCP

- DHCP > Add
  - Lease Tab

    - Interface: ethernet2

    - Mode: auto

      - enabled: always on

      - disable: off

      - auto: detect if another DHCP server is on your network

    - IP Pools > Add

      - `10.0.0.50 - 10.0.0.250`

    - Check `Ping IP when allocation new IP`

  - Options Tab

    - Gateway: `10.0.0.1` (IP address of firewall)

    - Subnet Mask: `255.255.255.0`

    - Primary DNS: `8.8.8.8` 

### Delete Old Virtual Wires

- Virtual Wires
  - Delete

### NAT Policy

- Policies Tab > NAT > Add

  - General

    - Name: outbound-net

  - Original Packet

    - Source Zone: trust

    - Destination Zone: untrust

    - Destination Interface: ethernet1

  - Translated Packet

    - Translation Type: Dynamic IP And Port

    - Address Type: Interface Address

    - Interface: ethernet1

    - IP Address: 198.51.100.2/28

- Commit Change
