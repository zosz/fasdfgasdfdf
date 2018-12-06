---
title: "Errors – Game"
permalink: /errors/game
date: 2018-12-06T10:51:50Z
redirect_from:
  - /errors/game/
  - /errors/game-errors/
  - /errors/gameerrors/
---


* My game isn't starting without proxy. \| can't click anything on launcher without proxy \| `Termination Code 273` \| `Sls contains errors` \| `error: 0111:0001` \| `Server list cannot be retrieved or contains errors.` \| `Unable to connect to TERA Server List.`
  - cause: Your "hosts" file contains one of these: White spacing after the \| Or some vpn entry Or the old proxy entires('cause of improperly termination of tera-proxy).
  - solution: Run proxy as administrator and once everything loads, close it with the "X" button & try run the game.
  - solution2: If that above didn't help, you'll have to reset your host. Open "run" or "cmd" & type `explorer %WinDir%\System32\Drivers\Etc` rename your "hosts" to "hosts.old".

---

* The client was closed abnormally.
  - cause: Mostly an broken gpk / `S1Engine.ini` / proxy module / SweetFX or reShader(double load of `d3d9.dll`). \| might be missing some vs runtimes. \| your game stopped to respond.
  - solution: Temp move out the moded gpks/engine.ini and see if that will help. \| start your game without proxy. \| You may also try to install [2015](http://download.microsoft.com/download/6/A/A/6AA4EDFF-645B-48C5-81CC-ED5963AEAD48/vc_redist.x86.exe) vs runtimes. \| You can also try repair button.
  - solution2: If you are using SweetFX or ReShader, you can try to remove file `TERA\Binaries\d3d9.dll` and see if that will help.

---

* `Account blocked. Please contact support.` \| `User authentication failed.`
  - cause: Your ip changed to 2~3 different locations within 30 minutes period of time which caused to apply a 1hour temp ban to your account. (not tera proxy, probably a vpn).
  - solution: You've to wait for 1 hour (Do not attempt to login before that, else the timer for 1h will reset). If after 1h you still have it, then it's a 24hr ban due to more than 3 ip changes.
  - solution2: If you waited +24hrs and still have it, contact support they might have actually banned your account due to some reason.

---

* **EU** region: Your automatic login token has expired. Please log into your account again.
  - cause: You clicked play button so fast that the launcher still didn't read the login token yet.
  - solution: Give the launcher a second or two then click play.

---

* **RU** region: Error `(-105)` \| nothing loads. \| no play button \| can't click anything on launcher. \| I don't see any (Proxy) servers in the server list.
  - cause: inappropriate configuration of url in `launcher.ini`.
  - solution: In client folder, there is file called `launcher.ini` next to the 'launcher.exe' => open it => change the url to `start=http://launcher.tera-online.ru/launcher/` then try.
  - solution2: If the above one didn't help, then most likely the old entry still in yout hosts file, Open "run" OR "cmd" & type `explorer %WinDir%\System32\Drivers\Etc` rename your "hosts" to "hosts.old" and try.

