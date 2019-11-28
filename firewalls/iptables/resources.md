# Resources

https://www.howtogeek.com/177621/the-beginners-guide-to-iptables-the-linux-firewall/
https://help.ubuntu.com/community/IptablesHowTo
https://www.thegeekstuff.com/2011/01/iptables-fundamentals
https://www.tecmint.com/basic-guide-on-iptables-linux-firewall-tips-commands/

## Basic Guide to iptables

iptables -> Tables -> Chains -> Rules

### 3 Main files

1. **/etc/init.d/iptables** – init script to start|stop|restart and save rulesets.
2. **/etc/sysconfig/iptables** – where Rulesets are saved.
3. **/sbin/iptables** – binary.

### 3 tables

- **Filter**
  - Default table
  - INPUT - incoming to firewall
  - OUTPUT - outgoing from server
  - FORWARD - routed through local server
- **NAT**
  - PREROUTING - alters packets before routing
  - POSTROUTING - alters packets when they're leaving the system
  - OUTPUT - for locally generated packets on the firewall
- **Mangle**

### 4 chains

1. **INPUT** : Default chain originating to system.
2. **OUTPUT** : Default chain generating from system.
3. **FORWARD** : Default chain packets are send through another interface.
4. **RH-Firewall-1-INPUT** : The user-defined custom chain.
