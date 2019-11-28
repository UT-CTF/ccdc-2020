# iptables

## Actions

### ACCEPT
Allow the connection
### DROP
Act like it never happened. Useful if you don't want people to know you exist.
### REJECT
Don't allow the connection, send back and error.

## Commands

### Change default action
```
iptables --policy INPUT ACCEPT/DROP/REJECT
iptables --policy OUTPUT ACCEPT/DROP/REJECT
iptables --policy FORWARD ACCEPT/DROP/REJECT
```

### Delete a specific rules
```
[root@tecmint ~]# iptables -D INPUT 5
```

### Flush ruleset
```
iptables -F
```

### Insert rule
```
[root@tecmint ~]# iptables -I INPUT 5 -s ipaddress -j DROP
```

### List rules
```
[root@tecmint ~]# iptables -L INPUT -n --line-numbers

Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
2    ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0
3    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
4    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:22
5    REJECT     all  --  0.0.0.0/0            0.0.0.0/0
```

### Save Changes
```
Ubuntu:

    sudo /sbin/iptables-save

Red Hat / CentOS:

    /sbin/service iptables save
```

### Set action based on state
```
iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -m state --state NEW,ESTABLISHED -j ACCEPT

iptables -A OUTPUT -p tcp --sport 22 -d 10.10.10.10 -m state --state ESTABLISHED -j ACCEPT
```

### Set action for connection from range of IPs
```
iptables -A INPUT -s 10.10.10.10 -j DROP
```

### Set action for connection from single IP
```
iptables -A INPUT -s 10.10.10.0/24 -j DROP
```

### Set action for connection to a specific port
```
iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -j DROP
```

## Flags

### -D `<chain> <rulenum>`
Delete rule

### -I `<chain> <rulenum> <rulespec>`
Insert rule

### -j `<target>`
This specifies the target of the rule; i.e., what to do if the packet matches it. The target can be a user-defined chain (other than the one this rule is in), one of the special built in targets which decide the fate of the packet immediately, or an extension. If this option is omitted in a rule (and -g is not used), then matching the rule will have no effect on the packet's fate, but the counters on the rule will be incremented.

### -L
List ruleset

### --line-numbers
Show line numbers to make adding/deleting easy

### -n
Display in numeric format

### -v
Verbose

### -s `<source>`
Set source for rules
