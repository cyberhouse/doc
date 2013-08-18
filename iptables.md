# How-Tos
## Deactivate All Rules
    #!/bin/sh
    iptables -F
    iptables -X
    iptables -t nat -F
    iptables -t nat -X
    iptables -t mangle -F
    iptables -t mangle -X
    iptables -P INPUT ACCEPT
    iptables -P FORWARD ACCEPT
    iptables -P OUTPUT ACCEPT

## Set Up Default Rules (Debian)

    pre-up iptables-restore < /etc/iptables.rules

<!---
 vim: expandtab tabstop=4 shiftwidth=4
-->
