---
permalink: /developer-guide
title: Developer Guide
---

tera-proxy is composed of a number of smaller modules:

* [`tera-data`](https://github.com/tera-proxy/tera-data) houses mappings of opcodes to packet names as well as crowdsourced definitions for packet structures.
* [`tera-data-parser`](https://github.com/tera-proxy/tera-data-parser-js) takes the above and performs serialization and deserialization between raw data buffers and JavaScript objects.
* [`tera-proxy-game`](https://github.com/tera-proxy/tera-proxy-game) is the actual game server proxy. It handles parsing and reconstructing network packets as well as allowing modules to add hooks for when certain network packets occur.
* [`tera-proxy-sls`](https://github.com/tera-proxy/tera-proxy-sls) allows retrieving the real server list, then serving up a modified version so you can point servers to the game proxy.

`tera-proxy` itself simply sets everything up for a user through one runnable script ([proxy.js](https://github.com/tera-proxy/tera-proxy/blob/master/bin/lib/proxy.js)). It is perfect for CLI usage but will likely be obsoleted when the GUI is completed.

**If you are just here to make modules,** you'll mostly be interested in `tera-proxy-game` and `tera-data`.

Each of the repositories has its own README should you want more information on any of them. The rest of this page will serve as a tutorial on how to make modules.

## Example: Creating a Simple Module

As an example of a simple module, we can make a module that replaces the string `"{me}"` in outgoing chat messages with the name of the character being played.

First, we're going to need the character's name. When you select a character to log in as, the server sends an `S_LOGIN` with that character's details. Packets are named such that if they begin with "S", they are sent from the server to the client, and ones that begin with "C" are sent from client to server. Checking `tera-data` for [`protocol/S_LOGIN.10.def`](https://github.com/tera-proxy/tera-data/blob/master/protocol/S_LOGIN.10.def), we see that it has a field called `"name"`, so we can most likely get the character's name from this packet.

We also need to know what a chat message packet is like, so again, we check `tera-data` and see [`protocol/C_CHAT.1.def`](https://github.com/tera-proxy/tera-data/blob/master/protocol/C_CHAT.1.def) for the definition of outgoing chat messages. Note that this does not include whispers, but we won't be touching that for now. We see that it has a field named `"message"`, so we can read and modify that if it contains `"{me}"` in it.

Here is what our module might look like:

```js
// The exported function must be constructible (not an arrow function).
// It receives, at minimum, one parameter, which is an instance of DispatchWrapper.
// The naming doesn't have to be 'dispatch' it can be anything convenient for you.
module.exports = function MeChatReplacement(dispatch) {
  // This is instantiated once per connection, so we can assume everything inside this
  // function body will be unique to a player. Anything outside of this block *may* be
  // persisted after disconnects and shared across connections, particularly if there
  // are multiple users logged into the proxy as is the case with multiboxing.

  // Declare a variable to track the player's name for the duration of the connection.
  let name;

  // Hook S_LOGIN to save the character's name.
  // Since we looked version 10 of the definition, we'll request that version.
  // Note that we use the exact packet name ('S_LOGIN') for the hook.
  dispatch.hook('S_LOGIN', 10, (event) => {
  // The `event` object contains all the fields that we saw from the definition file.
    name = event.name;
  });

  // Hook C_CHAT to change the message.
  dispatch.hook('C_CHAT', 1, (event) => {
    const { message } = event;

    // Make sure the message contains '{me}'.
    if (message.indexOf('{me}') !== -1) {
      // Modify the message in the provided `event` object.
      event.message = message.replace(/\{me\}/gi, name);

      // Return `true` to mark it as changed.
      // If you do not do this, any modifications to `event` will not be saved.
      return true;
    }
  });
};
```

It's as simple as that! Stick that somewhere like `tera-proxy/bin/node_modules/me-chat-replacement/index.js` and `tera-proxy` will load it up for use.

## Example: Creating a More Complex Module

(Coming soon...)

[//]: # "const fs = require('fs'), path = require('path'), oshomedir = require('os').homedir()"
    