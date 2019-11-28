# CCDC Threat Environment and Best Practices

## Part 1 - Threats

### CCDC Scored Services

HTTP, HTTPS, SMTP, POP3, SSH, SQL, DNS, FTP

### PA 3050 Appliance

12 ethernet ports

**Fiber optic ports** - probably not going to use

**2 high availability ports** - probably not going to use

*All trunk capable* (what)

**Management port** 

- Retrieve licenses and signatures from update server, used to acces WebUI and configure it. Can also use SSH

- 192.168.1.1 - need to change address to be accessible from client device to be consistent with network

- Most secure way to access it is through console port

- Doesn't have to be used for updates, etc. Can be done manually, this is default

**Console port**

### Typical Setup

Acting as firewall and gateway __OR__ acting alongside a gateway

### Management Interface

Connects to update server

- Licensing

- Signatures

- URL/Web categories

Configuration

- Web UI - nice graphic view of logs

- SSH - can lock down MGT port and only do configuration through this

### Locking down management through console port

- Change password

- Ensure no other users

- Only allow a certain IP address to access Web UI

### Services?

Can be anywhere - machines, provate cloud, hypervisors, etc.

Each has a virtual or physical firewall

### Where are the threats coming from?

Coming from external to internal - __North-South Traffic__

- Defend with a (fire)wall

Not always the case - malware could already be on laptops within the network - __East-West Traffic__

### Where are the trust zones?

Nowhere - __Zero-Trust__

Route everything through the firewall

### Policies

List of rules which packets are checked against, which have either allow/deny, then falls to deafult policy

### How to achieve this? (routing everything through firewall)

Plug in directly to ethernet ports (but there are only 12)

Use VLAN or trunks

## Part 2 - Best Practices

### Management Port

Default, has to be connected to an internet-facing port

Can change it to download to a data port, or put Web UI on data port, or transfer signatures from a client computer

### Cyberattack Life Cycle

__Reconaissance__

- Scanning - what ports are open?

- Firewall can prevent with Zone Protection Profile (assign to external zone)

  - If it receives so many scans from an IP address, it will block it

  - Can consume resources

__Weaponization__

- Firewall can't do anything about it

__Delivery__

- Main firewall protection vector

- Usually you will come in and the malware will already be delivered

__Exploitation__

- Not much a firewall can do

- Need to do on host

__Installation__

- Again, not much a firewall can do

- Need to do on host

__Command & Control__

- Tries to "phone home"

  - Gets instructions, then moves to next step

- Can block command and control traffic

__Act on Objective__

- See above

### 1. Complete Visibility

- Know applications to allow

  - Ones that keep services up and running

- SSL Decryption - decryption module

  - Decrypt packets so you can block them

### 2. Reduce Attack Surface Area

- Whitelist applications

  - Look inside application layer of every packet to check it

- Creating custom App-IDs

- Dynamic address lists and groups

  - Usually used for blocking traffic

- SSL protocol settings

  - Blocked bad/expired certs

  - Specify which type of TLS

__Default policy__ - allow within same zone, deny between zones

### 3. Protect against known attacks

- Assign security profiles (like extra rules) to security policy

  - Anti-virus profile

    - Updated daily

  - Vulnerability profile

  - Anti-spyware

  - File blocking (executables)

  - URL

    - Stored in cache memory

- Protext against DoS

  - Set up zone protection profile (assign to external interface)

  - DoS profile

  - Be very careful with these

### 4. Protect against unknown attacks

- WildFire analysis profile
  - Sends a copy of file to WildFire sandbox, which returns a report and generate a signature to block this malware

    - Signature is shared with everyone else in the world

    - Look at reports so you know malware came in

  - Make sure anti-virus profile is using WildFire signatures __NOT ENABLED BY DEFAULT__

  - Takes 5 minutes to update the anti-virus profile

### What to do when you walk into the room

- Secure management interface
  - Use console port
    - Change password

    - Restrict who can access command interface - permitted IP

    - Make sure you don't have any insecure services

    - Remove any admin users that you don't need that were there beforehand

### 
