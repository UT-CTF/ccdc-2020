# Tools

snmpwalk
- domain
- bios groups

hydra
- bruteforce logins
- slow to avoid timeouts, so you want a smaller password lists

dig
- dns lookups

SMB (server message block) for inter-node communication
- 139, 445 ports
- domain controllers 53 (DNS), 88 (kerberos), 389 (ldap)
	- AD is an implementation of ldap

RDP
- 3389 port

Kerberoasting
- https://www.blackhillsinfosec.com/a-toast-to-kerberoast/
- https://www.varonis.com/blog/kerberos-how-to-stop-golden-tickets/

Null Session - Anonymous
- connect with empty username and password

enum4linux
- Null session enumeration

NTLM
- checks password hash
- https://en.wikipedia.org/wiki/NT_LAN_Manager

CrackMapExec
- grab plaintext passwords out of memory

Getting System
- higher than admin

Responder
- DNS spoofing tool

Bettercap
- ARP spoofing
- ARP maps IP to MAC addresses

psexec
- https://ss64.com/nt/psexec.html

Bloodhound
- Map out the network
