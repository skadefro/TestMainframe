# A virtual machine image for Hercules.  Copied here to allow simple testing and development of the TN3270.NET library

# To use this you need to jump through a few hoops:

You need 2 Windows command prompts:

In #1

==> cd musicsp
==> run

Wait a few seconds, then type

==> ipl 201


In #2

==> telnet localhost 3270

wait a few seconds, either just press OK and press enter, or just press enter.


Now connect to your localhost machine on port 3270 to connect to the mainframe session
