An internal lan with some hosts (pc1 `192.168.100.10`, `2001:db8:cafe:1::10`), a DMZ (`203.0.113.0/24`, `2001:db8:cafe:2::/64`) with two servers,
a router (`192.168.100.1`, `2001:db8:cafe:1`, `203.0.113.1`, `2001:db8:cafe:2::1`, `198.51.100.29/24`, `2001:db8:beef:1::29/64`).

In the DMZ you've got 
  one Web server (`203.0.113.80`, `2001:db8:cafe:2:80`) on TCP ports 80 and 443,
  and one mail server (`203.0.113.25`, `2001:db8:cafe:2:25`) on TCP port 25.

Your security policy is as follows:
1.Your internal pcs may freely access any Web service, anywhere, on ports
  80 and 443, but only if they initiate the connection themselves (i.e.
  they are allowed to browse the Web). No one outside the internal lan 
  can initiate connections to internal lan, on any port.

2.Everyone, including the Internet, can access Web (both ports) and mail
  in DMZ to access their main functions and for ping. However, no host in
  DMZ can initiate connections anywhere else.

3.Internal users can access the Web servers and mail servers in DMZ via SSH,
  too. They can also use SSH to hosts on the Internet. However, hosts in
  DMZ can only be contacted on port 22 by hosts in the internal lan.

NOTE: if you obtain the error "Table does not exist (do you need 
to insmod?)" issue the following command in the host machine

$ `sudo modprobe ip6table_filter`

![ex3](https://github.com/edoardottt/MSc-CyberSecurity-Sapienza/blob/main/Practical-Network-Defense/tests/lab4/ex3/ex3.png)
