---
title: "Errors – NodeJs"
permalink: /errors/nodejs
date: 2018-12-06T10:51:09Z
redirect_from:
  - /errors/nodejs/
  - /errors/nodejs-errors/
  - /errors/nodejserrors/
---


* `EACCES`(Permission denied): An attempt was made to access a file in a way forbidden by its file access permissions.

---

* `EADDRINUSE`(Address already in use): An attempt to bind a server to a local address failed due to another server on the local system already occupying that address.

---

* `ECONNREFUSED`(Connection refused): No connection could be made because the target machine actively refused it. This usually when trying to connect to a service that is inactive on the foreign host.

---

* `ECONNABORTED`(Socket aborted): A connection abort was caused internal to your host machine.

---

* `ECONNRESET`(Connection reset by peer): A connection was forcibly closed by a peer. This normally results from a loss of the connection on the remote socket due to a timeout or reboot.

---

* `EEXIST`(File exists): An existing file was the target of an operation that required that the target not exist.

---

* `EISDIR`(Is a directory): An operation expected a file, but the given pathname was a directory.

---

* `EMFILE`(Too many open files in system): Maximum number of file descriptors allowable on the system has been reached.

---

* `ENOENT`(No such file or directory): No entity (file or directory) could be found by the given path. Commonly raised by "fs" operations to indicate a component of the specified pathname does not exist.

---

* `ENOTDIR`(Not a directory): A component of the given pathname existed, but was not a directory as expected. Commonly raised by "fs.readdir".

---

* `ENOTEMPTY`(Directory not empty): A directory with entries was the target of an operation that requires an empty directory — usually "fs.unlink".

---

* `EPERM`(Operation not permitted): An attempt was made to perform an operation that requires elevated privileges.

---

* `ETIMEDOUT`(Operation timed out): A connect or send request failed because the connected party did not properly respond after a period of time.

---

* `ERR_ARG_NOT_ITERABLE`: An iterable argument (i.e. a value that works with `for...of` loops) was required, but not provided.

---

* `ERR_INVALID_CALLBACK`: A callback function was required but was not been provided.

---

* `ERR_MISSING_MODULE`: An ES6 module could not be resolved.

---

* `ERR_MODULE_RESOLUTION_LEGACY`: A failure occurred resolving imports in an ES6 module.

---

* `ERR_OUT_OF_RANGE`: A given value is out of the accepted range.

---

* `ERR_STREAM_DESTROYED`: A stream method was called that cannot complete because the stream was destroyed using `stream.destroy()`.

---

* `ERR_SOCKET_CLOSED`: An attempt was made to operate on an already closed socket.

---

* `MODULE_NOT_FOUND`: A module file could not be resolved while attempting a `require()` or import operation.

