# SSH-With-VPS<br>
<p>
<b>A simple setup for using a VPS as a proxy to surf the web.</b><br>
</p>
<p>
Note: This type of tunnel can be used on any operating system, however the scope<br>
of this article concerns setting up with a Windows home computer.<br>
</p>
<p>
This article will show you a very simple way to create an encrypted SSH tunnel<br>
between your computer and a VPS.  This can be used to bypass corporate network<br>
limits, bypass NAT, and when used with dnscrypt, surf the web without your IPS,<br>
company, hotel, wifi connection, etc, knowing your surging destinations.  It<br>
will also protect you from snooping when you are using any wifi connection.<br>
This setup will securly work in place of having to setup a VPN on server.<br>
</p>
<p>
(DnsCrypt is not required for this setup to work.  However, your surfing<br>
destination Ip addresses will probably be leaked because you will be using the<br>
unencrypted DNS server used by your local machine.  The remote machine you are<br>
connected to may also sniff you DNS requests and thereby block you. The DnsCrypt<br>
installation and setup on a computer is not covered in this article, but can be<br>
found here: https://dnscrypt.org/  Also see: https://simplednscrypt.org/).<br>
</p>
<p>
<b>Necessities and Requirements:</b><br>
</p>
<p>
* A Windows computer<br>
* A VPS (A 512 MB DigitalOcean Debian 8.6 x64 was used for this setup)<br>
* Putty freeware program<br>
</p>
<p>
<b>Simple Setup:</b><br>
</p>
<p>
* Create your VPS:<br>
</p>
<p>
It is best to create and 'Add your SSH key' to a VPS, but simply using a good,<br>
long password containing some non-alpha characters can be used to login to your<br>
VPS also.  Your VPS is going to be enduring continuous behind the scene attacks<br>
by hackers in an attempt to break into and use it for nefarious purposes.  Thus<br>
an SSH key or good password is most necessary.  Once the VPS has been created,<br>
copy or write down its IP Address for later use.  This is all you need to do<br>
concerning setting up the VPS.<br>
</p>
<hr>
<p>
<b>* PuTTY Setup:</b><br>
</p>
<p>
Download and install PuTTY from:<br>
  http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html<br>
Download the 'Zip:' or 'Installer:', either will work.<br>
</p>
<p>
Start PuTTY by clicking on its desktop icon or the putty.exe in its folder.<br>
Click on the top 'Session' item in the menu tree on the left side of the PuTTY<br>
interface.<br><br>
</p>
<p align="left">
<b>A. Session window:</b><br>
<img src="/image/Putty-Session1.png" width="466" height="445"><br>
1. In the 'Host Name (or IP address)' box, enter the IP address you recorded after<br>
&nbsp;&nbsp;&nbsp;&nbsp;creating you VPS.<br>
2. Port 22 should be in 'Port' (unless you have changed your SSH port number).<br>
3. Connection type: 'SSH'.<br>
4. Type a name to identify these PuTTY connection parameters in the 'Saved Sessions'<br>
&nbsp;&nbsp;&nbsp;&nbsp;box.  The name 'SSH web tunnel' (without the single quotes) will be used for this<br>
&nbsp;&nbsp;&nbsp;&nbsp;demonstration, but any name can be used.  After all your PuTTY parameters are<br>
&nbsp;&nbsp;&nbsp;&nbsp;setup, you will be able to double click on this name in the listbox below the<br>
&nbsp;&nbsp;&nbsp;&nbsp;'Saved Sessions' box to make the connection.<br>
5. Go ahead and save what has been done thus far by clicking the 'Save' button<br>
&nbsp;&nbsp;&nbsp;&nbsp;on the right side of the PuTTY interface.<br><br>
</p>
<p align="left">
<b>B. Click on the 'Window/Behaviour' item in the menu tree.</b><br>
<img src="/image/Putty-Behavior.png" width="466" height="445"><br>
1. In the 'Window title:' box, enter 'SSH web tunnel' (without the single quotes).<br><br>
</p>

<p align="left">
<b>C. Click on the 'Connection/Data' item in the menu tree.</b><br>
<img src="/image/Putty-Data.png" width="466" height="445"><br>
1. In the 'Auto-login username' box, enter 'root' (without the single quotes).<br><br>
</p>
<p align="left">
<b>D. Click on the 'Connection/SSH/Auth' item in the menu tree (click the + next to<br>
&nbsp;&nbsp;&nbsp;&nbsp;'SSH' to expand the tree if necessary).</b><br>
  <img src="/image/Putty-Key.png" width="466" height="445"><br>
1. If you have created an SSH keys for logging in, place the path to your secret<br>
&nbsp;&nbsp;&nbsp;&nbsp;key in the 'Private key file for authenication:' box (possibly a ?.ppk file).<br>
&nbsp;&nbsp;&nbsp;&nbsp;Otherwise, leave the box blank.<br><br>
</p>
<p align="left">
<b>E. Click on the 'Connection/Tunnels/' item in the menu tree.</b><br>
  <img src="/image/Putty-Tunnnel A.png" width="466" height="445"><br>
1. Enter 8080 into the 'Source port' box.<br>
2. Click on the 'Dynamic' line or check its button in the second from bottom row.<br>
3. Now click the Add button and you will see 'D8080' appear in the listbox below<br>
&nbsp;&nbsp;&nbsp;&nbsp;'Forwarded ports:'.<br>
&nbsp;&nbsp;Result should look like this:<br>
<p align="left">
  <img src="/image/Putty-Tunnnel B.png" width="466" height="445"><br><br>
</p>
<p>
<b>F. Last, once again click on the top 'Session' item in the menu tree and click the<br>
&nbsp;&nbsp;&nbsp;&nbsp;'Save' button.  This must be done to save all the subsequent added parameters.</b><br>
</p>
<p>
Now double click on the name you gave your parameters for your connection to<br>
the VPS in the Session window (or single click on the name, click the 'Load'<br>
button, and then the 'Open' button at the bottom of the PuTTY interface).  You<br>
should see a window popup connecting you to your VPS.  Answer 'Yes' to the<br>
'Putty Security Alert' window message that will popup the first time you connect.<br>
If you are using a password, enter it at the password prompt.  If there is a<br>
problem with connecting, close the window, start PuTTY again, single click on the<br>
connection name again, and click the 'Load' button above the Save button.<br>
Examine all your parameters again to see if there is an error.<br>
(Note the 'Connection/Tunnels' window will have reset to its original defaults,<br>
however the D8080 should still be in the 'Forwarded ports:' listbox.)<br>
<br>
<br>
</p>
<p>
<b>* Browser parameters setup:</b><br>
<p>
You now must set your browser to connect to PuTTY.  I am using FireFox as the<br>
browser for this demonstration.  Using FireFox with FoxyProxy makes switching<br>
between your normal connection and your VPS very easy.<br>
</p>
<p>
A. Setup without FoxyProxy:<br>
&nbsp;&nbsp;&nbsp;&nbsp;Go to 'Tools/Options/Advanced/Network'.  Click the 'Settings...' button next to<br>
&nbsp;&nbsp;&nbsp;&nbsp;'Configure how Firefox connects to the Internet' and set the parameters as below:<br>
&nbsp;&nbsp;&nbsp;&nbsp;1. Check the 'Manual proxy configuration:' box.<br>
&nbsp;&nbsp;&nbsp;&nbsp;2. Enter 127.0.0.1 into the 'HTTP Proxy:' box and 8080 into the 'Port:' box.<br>
&nbsp;&nbsp;&nbsp;&nbsp;3. Check the 'SOCKS v5' box.<br>
&nbsp;&nbsp;&nbsp;&nbsp;4. Click the OK button.<br>
</p>
<p>
B. Setup with FoxyProxy:<br>
&nbsp;&nbsp;&nbsp;&nbsp;If using FireFox with FoxyProxy, open the FoxyProxy window, click 'Add New Proxy'.<br>
&nbsp;&nbsp;&nbsp;&nbsp;In the 'General' tab, make the 'Proxy Name' the same name you gave to the PuTTY<br>
&nbsp;&nbsp;&nbsp;&nbsp;'Session' = 'SSH web tunnel' (however, it can be any name).  In the 'Proxy Details'<br>
&nbsp;&nbsp;&nbsp;&nbsp;tab, click 'Manual Proxy Configuration'.  In 'Host or IP Address', enter 127.0.0.1.<br>
&nbsp;&nbsp;&nbsp;&nbsp;In 'Port', enter 8080.  Check 'SOCKS proxy?' and 'SOCKS v5'.<br>
</p>
<p>
After you make the changes to the browser network parameters, you should be able<br>
to brows through the VPS.  If using FoxyProxy, remember that you have to right click<br>
and select the FoxyProxy line for the VPS = 'SSH web tunnel'.<br>
</p>
<p>
To shutdown the PuTTY connection, type 'exit' at the connection window prompt.<br>
<br>
<br>
</p>
