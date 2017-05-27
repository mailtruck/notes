Step Seven — Set Up a Basic Firewall
Ubuntu 16.04 servers can use the UFW firewall to make sure only connections to certain services are allowed. We can set up a basic firewall very easily using this application.

Different applications can register their profiles with UFW upon installation. These profiles allow UFW to manage these applications by name. OpenSSH, the service allowing us to connect to our server now, has a profile registered with UFW.

You can see this by typing:

sudo ufw app list
Output
Available applications:
  OpenSSH
We need to make sure that the firewall allows SSH connections so that we can log back in next time. We can allow these connections by typing:

sudo ufw allow OpenSSH
Afterwards, we can enable the firewall by typing:

sudo ufw enable
Type "y" and press ENTER to proceed. You can see that SSH connections are still allowed by typing:

sudo ufw status
Output
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
OpenSSH (v6)               ALLOW       Anywhere (v6)
If you install and configure additional services, you will need to adjust the firewall settings to allow acceptable traffic in. You can learn some common UFW operations in this guide.