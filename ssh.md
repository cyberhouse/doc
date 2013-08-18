# How-Tos
## Kill Unresponsive Session

    newline + ~.

## Multi-hop SSH

Scenario: ``host1`` is accessible from the local machine,  but ``host2`` is only accessible from ``host1``, and ``host 3`` only through ``host2``.

###  ~/.ssh/config  

    Host host1
	  HostName host1.example.com
    Host host2
	  ProxyCommand ssh -q host1 nc -q0 host2 %p
    Host host3
	  ProxyCommand ssh -q host2 nc -q0 %h %p

### Command Line
	ssh -A -t host1.example.com ssh -A -t host2 ssh -A host3
   
<!---
 vim: expandtab tabstop=4 shiftwidth=4
-->
   
