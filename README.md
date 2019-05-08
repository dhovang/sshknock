# sshknock
Very simple single port ssh port knocker. Same script contains both client and server. When server receives a good packet (UDP) it will use iptables to open port 22 for traffic from the originating IP for a preset amount of time using iptables. Open IPs are kept in a dbm database.

This script can be started either as a server or as a client:

sshknock server

or

sshknock [host] [password]

Before you start the server, make sure you edit the config at the top of the file.
