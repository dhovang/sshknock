# sshknock
Very simple single port ssh port knocker. Same script contains both client and server. When server receives a good packet (UDP) it will use iptables to open port 22 for traffic from the originating IP for a preset amount of time using iptables. Open IPs are kept in a dbm database.

This script can be started either as a server or as a client:

    sshknock server

or

    sshknock host password [netcat port] [netcat delay]

Before you start the server, make sure you edit the config at the top of the file.

Please note that this script is not ment to provide "real security", but rather to prevent the logs to be flooded with annoying attempts to connect to public ssh services.

In order to knock automatically, put a ProxyCommand in your ssh config for the host, like this:

    Host MyHost
      User MyUserName
      HostName ip-or-fqdn
      ProxyCommand bash -c '/path/to/sshknock %h YourKnockPassword && sleep 0.2 && exec /bin/nc %h %p'

Alternatively, you can use the built-in netcat function like so:

    Host MyHost
      User MyUserName
      HostName ip-or-fqdn
      ProxyCommand /usr/bin/env python3 /path/to/sshknock %h YourKnockPassword %p

TODO list:
- Move some stuff to configuration file
- Make it work with Python3
