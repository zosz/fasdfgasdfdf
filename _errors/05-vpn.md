---
title: "Errors – VPN"
permalink: /errors/vpn
date: 2018-12-06T10:51:32Z
redirect_from:
  - /errors/vpn/
  - /errors/vpn-errors/
  - /errors/vpnerrors/
---


* How to use tera-proxy with gaming vpn service?
  1. Disable the automatically detected "TERA" game.
  2. Add `C:\Program Files\nodejs\node.exe` as a custom game (leave launcher blank).
  3. Run the VPN software as administrator.
  4. Start tera-proxy then start tera.

---

* How to use tera-proxy with shinra meter/TCC with vpn? \| It was working but after windows/driver update it stopped.
  1. Use raw socket mode (make sure you add the firewall role) or reinstall npcap (uninstall => reboot => install again) and check the options `winpcap compatible mode` & `Support looback traffic ("Npcap loopback adapter will be installed")` in installer.
  2. If your vpn is not working after you did that: then you need to add a line in "config/server-overrides.txt" inside shinra meter directory; e.g. if you're using vpn for ktera `xxx.xxx.xxx.xxx KR VPN` (Of course, replace xxx.xxx.xxx.xxx by the IP of your VPN. You can find, which one Tera.exe is connecting in resource manger).

