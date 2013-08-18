# How-Tos
## Serving Documents via HTTP
    while true; do nc -l -p 80 -q 1 < error.html; done
    while true; do { echo -e 'HTTP/1.1 200 OK\r\n'; cat index.html; } | nc -l 8080; done
    python -m SimpleHTTPServer
    twistd -n web –path .
    php -S localhost:8000

## View markdown files in lynx
    pandoc -s -f markdown -t html =(curl https://raw.github.com/cyberhouse/doc/master/README.md) | lynx -stdin
    pandoc -s -f markdown -t html doc/README.md | lynx -stdin

## Cookies and Login with ``curl``
    curl -d @$HOME/.credentials --cookie-jar /tmp/cjar -k https://example.com/?do=login; curl -k --cookie /tmp/cjar --cookie-jar /tmp/cjar https://example.com/foo|lynx -stdin

## See File Access for a Specific Path
    lsof +D /var/log

## Find Rogue Internet Gateways on your Network
    nmap -sn 172.16.35.0/24 --script ip-forwarding --script-args="target=www.google.com"

## Remote Network Protocol Analyzing with `tcpdump` or `tshark` and Wireshark
    ssh server1 tcpdump -i eth3 -U -s0 -w - 'tcp port 80' | wireshark -k -w /tmp/gw.cap -b filesize:50000 -b files:10 -i -
    ssh server1 'tshark -f "port !22" -w -' | wireshark -k -i -

## Create Diff with remote file
    diff .ssh/config <(ssh trillian 'cat .ssh/config')

## Create cronjob programmatically
    crontab -l > /tmp/$(whoami)-crontab
    echo '* * * * * www-data /var/www/html/typo3/cli_dispatch.phpsh scheduler' >> /tmp/$(whoami)-crontab
    crontab /tmp/$(whoami)-crontab
    rm /tmp/$(whoami)-crontab

## Forward Ports
	socat TCP4-LISTEN:1234,fork TCP4:192.168.1.1:22' forwards your port   1234 to another machine's port 22. Very useful for quick NAT red

## Sysstat's ``sar`` with 24h Time Format
	sar -o /tmp/sarlog -A 5 >/dev/null 2>&1
	LANG=C; S_TIME_FORMAT="%T; sar -f /tmp/sarlog|les

## Setting and Removing the Immutable Bit
	chattr +i /etc/shadow; lsattr /etc/shadow
	chattr -i /etc/shadow; lsattr /etc/shadow
	
<!---
 vim: expandtab tabstop=4 shiftwidth=4
-->
