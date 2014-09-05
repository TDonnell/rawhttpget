rawhttpget
==========

HTTP GET with raw socket using Python


Basic HTTP GET program, completed using a raw socket. There was no purpose in doing it this way, but I was curious.

Two sockets were required because of the system on which I was working: one for outgoing information, one for incoming.

In order to function, it was also necessary to modify IP Tables on my Linux VM using:

% iptables -A OUTPUT -p tcp --tcp-flags RST RST -j DROP

This was required in order to drop outgoing TCP RST packets. Because I was using a raw socket, the kernel was unsure of what
to do with the incoming packets (which TCP port I was using), so it defaults to sending resets, believing that it has received them in error. In doing so, I was able to proceed as normal with scraping the packet stream for anything relevant to me, process it, and respond.
