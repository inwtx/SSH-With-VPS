# SSH-With-VPS
A simple setup for using a VPS as a proxy to surf the web.

Note: This type of tunnel can be used on any operating system, however the scope
of this article concerns setting up with a Windows home computer.

This article will show you a very simple way to create an encrypted SSH tunnel
between your computer and a VPS.  This can be used to bypass corporate network
limits, bypass NAT, and when used with dnscrypt, surf the web without your IPS,
company, hotel, wifi connection, etc, knowing your surging destinations.  It
will also protect you from snooping when you are using any wifi connection.
This setup will securly work in place of having to setup a VPN on server.

(DnsCrypt is not required for this setup to work.  However, your surfing
destination Ip addresses will probably be leaked because you will be using the
unencrypted DNS server used by your local machine.  The remote machine you are
connected to may also sniff you DNS requests and thereby block you. The DnsCrypt
installation and setup on a computer is not covered in this article, but can be
found here: https://dnscrypt.org/.)
