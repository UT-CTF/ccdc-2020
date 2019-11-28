# Zone Protection Profiles

### Network Tab

- Network Profiles > Zone Protection > Add
  - Name: ZoneProtection

  - Flood Protection

    - SYN 

      - SYN Cookies - firewall acts as MitM for TCP handshake to validate connection

      - Random Early Drop 

        - If rate is betweem Activate and Maximum, drop rate will increase

        - If rate is above Maximum, all packets will be dropped

    - ICMP

    - 4:00
