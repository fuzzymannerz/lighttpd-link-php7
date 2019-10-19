# lighttpd-link-php7
A lighttpd powered lightweight web server for the Steam Link **with 100% more PHP!**

![](https://i.imgur.com/u2bKzlA.png)

Could be used for system monitoring pages, web dashboards and so on...

For the version without PHP, [have a look at this one](https://github.com/fuzzymannerz/lighttpd-Link)!

----

# Requirements
- A Steam Link (obviously)
- SSH access to said Steam Link ([How to do just that](https://github.com/ValveSoftware/steamlink-sdk#ssh-access))

----

# How To Install
1. [Download the archive](https://github.com/fuzzymannerz/lighttpd-link-php7/archive/master.zip) and extract it somewhere.
2. Upload everything inside the "*Upload*" folder to the steam link's filesystem root via SSH. (Mounted or WinSCP etc...)

----

# Usage
### Important One Time Setup:
```bash
chmod 755 /usr/local/sbin/lighttpd && chmod -R 755 /home/steam/php7.3.10/bin && chmod -R 755 /home/steam/php7.3.10/sbin && ldconfig
```

### To Start:
```bash
lighttpd -f /home/steam/http/serve.conf
```

It will now run as a background process until stopped or until the Steam Link is turned off.
### To Stop:
```bash
pkill lighttpd
```
See `home/steam/http/serve.conf` for a basic configuration example.    
Refer to https://redmine.lighttpd.net/projects/1/wiki/TutorialConfiguration for more info.

----

# Uninstallation
If you factory reset your Steam Link lighttpd-Link will be removed.    
Otherwise you can run the fancy uninstall script.

**To unininstall everything, including the "*/home/steam/http*" folder:**
```bash
wget https://raw.githubusercontent.com/fuzzymannerz/lighttpd-Link/master/rmLighttpd-Link.sh && chmod +x rmLighttpd-Link.sh && sh rmLighttpd-Link.sh
```

**To just remove all files apart from the "*/home/steam/http*" folder:**
```bash
wget https://raw.githubusercontent.com/fuzzymannerz/lighttpd-Link/master/rmLighttpd-Link.sh && chmod +x rmLighttpd-Link.sh && sh rmLighttpd-Link.sh keephttp
```

**Then remove the PHP folder**
```bash
rm -rf /home/steam/php7.3.10
```
