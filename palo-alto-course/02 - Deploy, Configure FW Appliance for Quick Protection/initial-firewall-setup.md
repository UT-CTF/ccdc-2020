# Initial Firewall Setup

### Default user

User: admin

Pass: admin

## CLI

`configure` - enter configuration mode

`show jobs all` - list commit history

## Web Interface Method

- Set IP to 192.168.1.2

- Connect to 192.168.1.1 in browser

- Login admin, admin

- Go to Device > Setup > Management Interface Settings

  - Change IP to appropriate IP address in network (10.0.0.4)

  - Default gateway was 10.0.0.1

- Go to Services

  - Add primary DNS server (4.2.2.2)

- Commit

- Connect to new IP on computer (10.0.0.4)

- Connect in browser (10.0.0.4)

### Activate License

- Go to Device > Licenses

  - Activate license

### Set up Dynamic Updates

- Go to Device > Dynamic Updates

  - Check Now

  - Download content package

  - Install

  - Check Now (again)

  - Download and install antivirus package

  - Set Schedule in antivirus and application threats

    - Recurrence: hourly

- Commit

### Install Latest Software

- Device > Software

  - Check Now

  - Download and install latest version

  - Reboot firewall

### Add Security Profiles

- Login again

- Go to Objects > Security Profiles > URL Filtering Profile

  - Name: url

  - Set all actions to alert

- Go to Objects > Application Filter

  - Add

    - Technology: peer-to-peer

- Go to Profiles > Security

  - Add

    - Source: trust

    - Destination: untrust

    - Application: peer-to-peer

    - Action: deny

  - Put the rule above rule 1

  - Choose rule 1

    - Actions > Profile Setting

      - Profile Type: Profiles

      - URL: select custom one

      - All other: Default

- Commit

### Interfaces

- Go to Network > Interfaces > Ethernet

  - Untrust - router/upstream

  - Trust - switch

- Management also connected to switch
