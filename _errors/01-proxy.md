---
title: "Errors - Proxy"
permalink: /errors/proxy
date: 2018-12-06T09:04:17Z
redirect_from:
  - /errors/proxy/
  - /errors/proxy-errors/
  - /errors/proxyerrors/
---


* Tera-proxy stays at "listening" even after I start the game.
  - cause: Either incorrect game region(`proxy/bin/config.json`) or software on your computer bypassing your hosts file.
  - solution: Make sure your antivirus isn't overriding hosts modification, your VPN is correctly configurated.
  - solution2: If you don't have antivirus or VPN then probably it's malware (usually adware) where you need to run a full scan for viruses using [malwarebytes](https://www.malwarebytes.com/) or some antivirus.

---

* Proxy is closing immeditally after running it.
  - cause: Most likely the user you're logged in has no access permissions for the "hosts" file security.
  - solution: Open "run" OR "cmd" & type `explorer %WinDir%\System32\Drivers\Etc` => on "hosts" file, right click => Properties => Security => Edit => at `All Application packages` give it "full control" then add new "users" then press OK => make sure you check the "full control" and Apply => then close and try again.
  - solution2: Make sure you're running a administrator user, open control panel => User Accounts => Change your account type => Make sure you've "Administrator" checked, if it's not, then check it and Apply => restart pc.
  - solution3: open run and type `Netplwiz` => click on your account => properties => Group Membership tab => check the "Administrator" radio button & OK => restart pc.
  - solution4: Open cmd as administrator(r-click => run as admin) and type `net localgroup administrators X /add` Where X is your user name, case-sensitive => restart pc.

---

* `ERROR: Hosts file is set to read-only.`
  - solution: Locate `hosts` file (mostly in `c:/windows/system32/drivers/etc`) and make sure it's attributes (properties) not set to `read-only`.
  - solution2: if the above didn't help, make sure you disable antivirus hosts block modify, if no option then disable the whole antivirus.

---

* `ERROR: Another instance of TeraProxy is already running, please close it then try again.`
  - solution: Close the another instance of TeraProxy. If that didn't help, restart your pc.

---

* `ERROR: Another process is already using port "num".`
  - solution: If the name is showed up in the cmd after that error, simple just go and disable or uninstall that program/service.
  - solution2: Common programs/services that can be using port 80:
  1. programs: Skype (in options, disable its use of port 80), IIS (you can disable it via going to "windows features" & uncheck it's checkbox => restart pc).
  2. services: W3SVC, MsDepSvc, MSSQLSERVER, PeerDistSvc. (Open cmd, to stop type `sc stop X` & to disable it `sc config X start= disabled` \| where `X` is the service name).
  - solution3: 
  1. Open cmd and type `netstat -nao | find ":X"` where "X" is the number of port, with quotations and colon, e.g `netstat -nao | find ":80"`.
  2. Get the process id from last column, and type it in this command: `tasklist /svc /FI "PID eq X"` where `X` is the process id, no quotations.
  3. Now you should get results as a formated table, from first column pick the name(s) and try to change it's port number, disable or uninstall it 
  * Note that some services hides under other services, e.g "IIS" service hides under "system" which you can't stop or disable. - Incase you got sth like `system` or `svchost.exe` try to check it's services (it's written at 3rd column), if there are too many with same name e.g `svchost.exe`, you can list them by typing `tasklist /svc /fi "imagename eq svchost.exe"`.

---

* `ERROR: Insufficient permission to modify hosts file.`
  - cause: Permission denied (directory permissions). Commonly by not running the proxy as administrator, or some antivirus is blocking the modification for "hosts" file.
  - solution: Right click on `TeraProxy.bat` and "Run as administrator". 
  - solution2: If the above didn't help, then check the antivirus's settings, if you don't find any option to stop blocking modification of "hosts" then you've to disable or uninstall it.

---

* `Warning: require('vec3') is deprecated.`
  - cause: the module is using old way to require the tera-vec3.
  - solution is `const Vec3 = require('tera-vec3');`

---

* `DeprecationWarning: Long.JS is deprecated. Use BigInt equivalents instead.`
  - cause: the module is using old way to deal with numbers "Long.js".
  - solution: You can ignore this if the module is working. If not, remove the module.

---

* `WARNING FOR DEVELOPERS: In X - require()'ing X is deprecated, use x instead!`
  - cause: the module is using old way to require the X module.
  - solution: You can ignore this if the module is working. If not, remove the module.

---

* `WANRING: Module X does not support auto-updating!`
  - solution: You can ignore this if you don't want auto update, if you do check the "module.json" & make `disableautoupdate` to false.

---

* `ERROR: Unable to auto-update the proxy!: StatusCodeError: 404` \| `ERROR: Unable to auto-update the proxy!: RequestError: Error: connect ETIMEDOUT XXX.216.248.21:443`
  - cause: Probably s

---

* `ERROR: Unable to auto-update module X`
  - cause: most likely it's your connection (if the requestError was one of these: [ECONNRESET, ECONNREFUSED, ETIMEDOUT]), or the module in github no longer has those files (To fix this get new version).
  - solution: Make sure you can visit `github.com` then try running the proxy again, if there didn't help, restart your pc/router.

---

* `ERROR: Module X could not be updated and will not be loaded!`
  - cause: there was a error while trying to update the module so for safety reasons the proxy won't load the outdated module.
  - solution: Try restarting proxy, if there didn't help, restart your pc/router. If none of that helped, you need to manually get new version of the module and replace your current.

---

* `error: Required mod not found: X`
  - cause: the module is trying to require a module X that can't be found.
  - solution: You probably forgot to download the dependincies for the module, try and see if you can find that X, download, extract, rename to the exact spelling of X (without the `-master`), move it to `tera-proxy/bin/node_modules/`.
  - solution2: If that didn't help, check the readme you might missed some part or you may ask for help in discord servers.

---

* `error: no mapping for protocol version X` \| `unmapped protocol version X` \| `unrecognized protocol version X`
  - cause: outdated module/proxy or non-public definition. \| (If there was no update) 
  - cause2: (Mosty **NA**, **SEA**) in rare causes the launcher breaks & failed to install proper version of game. (To fix this, try repair button in launcher if there didn't help, reinstall the whole game).

---

* `unrecognized hook target packet<ver>`  \| `invalid code "null"` \| `mapping not found for opcode X`
  - cause: Missing opcode.

---

* `version is required`
  - cause: Non valid version type while trying toClient/toServer/send functions.

---

* `obsolete definition (X)`  \| `definition not found (X)` \| `error: no definition found for message`
  - cause: the module is requiring non-existing packet, might be mistyped, or outdated.

---

* `* hook must request version '*' or 'raw' (given: X)`
  - cause: The hook is requesting an wildcard '*' packets with number version.

---

* `error: Cannot destructure property 'X' of 'undefined' or 'null'.`
  - cause: This error appears if you try to deconstruct an object in function args where `X` is undefined or null.

---

* `error: Cannot set property 'X' of undefined`
  - cause: This error appear if you try to set property of an object or array where the `X` is undefined.

---

* `RangeError: Maximum call stack size exceeded`
  - cause: The variable couldn't handle that many arguments. (Mostly you left cache = false).
  - solution: If you're a user, run server-select.exe and uncheck `Enable module unloading upon disconnection`. \| if developer... you're on your own.

---

* `SyntaxError: Unexpected token X`
  - cause: A specific language construct was expected, but something else was provided. This might be a simple typo.
  - solution: if you downloaded this then modified it, best option is to redownload it.
  - solution2: if you're developer/expert go into that location where it says and try to add/remove what is causing that error - you can check validation of your code [here].

---

* `SyntaxError: Octal literals are not allowed in strict mode.`
  - cause: Octal literals are not allowed because disallowing them discourages programmers from using leading zeros as padding in a script.
- example:

  ```js
  var eight = 0008,
      nine = 00009,
      ten = 000010,
      eleven = 011;
    
  console.log(eight, nine, ten, eleven); // '8, 9, 8, 9'
  ```
  - solution: Instead you should pad with leading spaces. \| if it's a value and you want to compare it, convert it to string first.

---

* `RefernceError: X is not defined` \| `error: X is not defined` *Strict mode*
  - cause: Non defined variable / Accidentally mistyping made a global variable.
  - solution: Make sure you declare that `X` by `let`, `var`, or `const`.

---

* `ERROR: Timeout while trying to load the server list.` \| `StatusCodeError: 404` \| `RequestError: Error: connect ETIMEDOUT XXX.YYY.SSS.ZZZ:PPP` \| `ERROR: Unable to auto-update the proxy`
  - cause: Your connection to the official servers/to the internet is not working properly.
  - solution: Try restarting your pc/router.
  - solution2: If that didn't help, try open cmd and type `ipconfig /flushdns` => `ipconfig /renew`.

---

* `Error: self signed certificate in certificate chain`
  - cause: An improperly configured web proxy which tries to intercept SSL traffic. Usually caused by antivirus(Kaspersky) or a virus.
  - solution: Turn the antivirus off completely. If that didn't help then it's likely an virus, run a full scan for viruses using [malwarebytes](https://www.malwarebytes.com/) or some antivirus.

---

* `error: The value of "offset" is out of range. It must be >= X and <= Y. Received Z` \| `error: Cannot set the value of "offset"` \| `Offset is out of bounds`.
  - cause: The buffer received a value (more or less) than the hooked one.
- explain: Mostly caused by *other* outdated(or new) module trying to send an packet with certain versioning, and this module is trying to hook/send another version.

---

* `UnhandledPromiseRejectionWarning: Error: Can't find module 'X'`
  - cause: The proxy core modules can't be found, probably your installation of proxy didn't go well.
  - solution: Get fresh copy of proxy, and make sure your modules go to `proxy/bin/node_modules`, don't touch `proxy/node_modules`.
  - solution2: If that didn't help, make sure you're using 7z as program to extract, sometimes other programs extract with some missing/corrupted file(s).

---

* `Error: Cannot find module 'x'`
  - cause: The module is try to require another module that can't be found.
  - solution: probably the module has a pre-packaged in it's github's "releases" which you have to download. If no, then try re-downloading it/check it's readme. If none of these helped, then you probably need to `npm install` it.

---

* `TypeError`: An object represents an error when a value is not of the expected type.
* `InternalError`: An object indicates an error that occurred internally in the JavaScript engine.
* `RangeError`: An object indicates an error when a value is not in the set or range of allowed values.
* `ReferenceError`: An object represents an error when a non-existent variable is referenced.
* `SyntaxError`: An object represents an error when trying to interpret syntactically invalid code.
* `URIError`: An object represents an error when a global URI handling function was used in a wrong way.

