---
permalink: /user-guide
title: User Guide
---

## Installation

### Step 1: Download tera-proxy

The most convenient way for most users will be to download the latest ZIP from the releases page. Go ahead and extract it anywhere that's convenient for you.

You don't have to download both, just pick one for you. Be aware that not all modules supports both proxies, make sure you know which version you want to download, I'll put side note for the modules which supports only that one.

**Pinkie's proxy**: [Pinkie's releases](https://github.com/tera-proxy/tera-proxy/releases)

**Caali's proxy**: [Caali's releases](https://github.com/caali-hackerman/tera-proxy/releases) *supports auto-updating*

### Step 2: Download modules

tera-proxy does very little on its own. If you want something done, find (or [make]({{ '/developer-guide' | absolute_url }})!) a module for it.

Let's say you'd like to install [auto-vanguard](https://github.com/tera-mods/auto-vanguard) so you never forget to turn in a Vanguard quest ever again.

First, go to its [GitHub page](https://github.com/tera-mods/auto-vanguard). Near the top, it'll list the number of commits, branches, and releases. Click on [releases](https://github.com/tera-mods/auto-vanguard/releases) if there are any, and you can get download the prepackaged module from there.

However, auto-vanguard has no prepackaged releases, so instead you can click the green "Clone or download" button and click on "Download ZIP". Extract it anywhere convenient and you should have a folder called `auto-vanguard-master` with one file in it.

Over in your tera-proxy installation, go to: `tera-proxy/bin/node_modules/` and then put the folder in there. You’re done!

Beware that some modules can be dependents therefore you should remove the branch naming from file name after extracting (yes, I'm talking about `-master`) it can lead to errors that the required module not found.

For the vast majority of modules, you *should* have a file in at least one of the following places:

- `tera-proxy/bin/node_modules/<module_name>/index.js`
- `tera-proxy/bin/node_modules/<module_name>/package.json`
- `tera-proxy/bin/node_modules/<module_name>.js`

If neither of those exist, you might have an extra folder. Try moving things up a folder until you have one of the files above.

**If you have an existing installation of tera-proxy,** you can simply copy over your old `tera-proxy/bin/node_modules`.

### Step 3: Run tera-proxy

In the provided tera-proxy download, there should be a file called `TeraProxy.bat`. Right-click it, select "Run as administrator", and you're set.

If you got tera-proxy from somewhere else and there is no `TeraProxy.bat`, follow whatever instructions you were given. If you didn't get instructions or forgot them, you're on your own.

### Step 4: Connect to tera-proxy

tera-proxy modifies the server list to allow you to connect to it.

If TERA is already open, you'll need to at least go back to the server select screen *after launching tera-proxy*.

If TERA is already closed when you launch tera-proxy, you're all set! Just start up the game and it should work fine.

### Step 5: Enjoy!

You're done! Go have fun with your fancy new modules.

## FAQ

#### There was a TERA patch and the proxy broke!

**Pinkie proxy:** 
Unfortunately, you'll need to update tera-proxy every major patch. Check the [tera-proxy releases page](https://github.com/tera-proxy/tera-proxy/releases) to see if there's a new version. If you're in a region like KR, you may have to wait a day or so, if it didn't then you might wanna check if there is any news in [pinkie's discord](https://discord.gg/RR9zf85).

**Caali proxy:**
Try restarting your proxy after few minutes/hours to see if it got updated for that region, if it didn't then you might wanna check if there is any news in [caali's discord](https://discord.gg/dUNDDtw), if there is none just have patiance. If you're in a region like KR, you may have to wait a few longer.

#### My proxy is closing immeditally after running it!

check [CommonErrors]({{ '/errors' | absolute_url }}) page.

#### What's with this timeout error?

By default, tera-proxy attempts to proxy to the region set in the `tera-proxy/bin/config.json`.

**Pinkie proxy:** 
If you don't have that file, then you should run `server-select.exe` & pick your region from there. Note: "TH" can be used for both TH and SEA regions in this proxy.

**Caali proxy:**
The proxy takes some time to startup as it check if there is some missing files.
Note: "SE" can be used for both TH and SEA regions in this proxy.
Lets say for example your region is JP, you have to go and edit the `"region"` in the `tera-proxy/bin/config.json` file and it should look something like:

```css
	"region": "JP"
```

You don't have to change any other values in there.

Available regions for caali's proxy: EU, JP, KR, NA, RU, TW, TH, SE.

