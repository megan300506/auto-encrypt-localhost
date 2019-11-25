# Nodecert

A Node.js wrapper for [mkcert](https://github.com/FiloSottile/mkcert/) that:

  * Uses the 64-bit release binaries to support Linux, macOS, and Windows.

  * Automatically installs the _certutil_ (nss) dependency on Linux on systems with apt, pacman, yum (untested) and  and on macOS if you have [Homebrew](https://brew.sh) or [MacPorts](https://www.macports.org/) (untested).

  * Creates a root Certificate Authority

  * Creates locally-trusted TLS certificates for localhost, 127.0.0.1, and ::1

You can use these certificates for local development without triggering self-signed certificate errors.

It should __just work™__ 🤞

I’d appreciate it if you can [help me test it](#help-wanted) on untested platforms and package managers 🤗

Nodecert is used in [Site.js](https://sitejs.org), a personal web tool for human beings (not startups or enterprises) that lets you develop, test, and deploy your secure static or dynamic personal web site with zero configuration.

For more details on how nodecert works behind the scenes, please [see the mkcert README](https://github.com/FiloSottile/mkcert/blob/master/README.md).

## Installation

```sh
npm i -g @ind.ie/nodecert
```

## Usage

### Command-line interface

```sh
nodecert
```

Your certificates will be created in the _~/.small-tech.org/nodecert_ directory.

## Caveats

### Windows

Locally-trusted certificates do not work under Firefox. Please use Edge or Chrome on this platform. This is [a mkcert limitation](https://github.com/FiloSottile/mkcert#supported-root-stores)

### API

```js
require('@ind.ie/nodecert')()
```

__As of version 3.1.1,__ you can now pass a custom directory for nodecert to use instead of the default (`~/.small-tech.org/nodecert`) and the created certificates will be stored there.

For example:

```js
const os = require('os)
const path = require('path')
const nodecert = require('@ind.ie/nodecert')

const customDirectory = path.join(os.homedir(), '.my-app', 'tls', 'local')

nodecert(customDirectory)
```

## Help wanted

* Linux: _certutil_ (nss) auto-installation has not been tested with yum.
* macOS: _certutil_ (nss) auto-installation has not been tested with MacPorts.

I can use your help in testing these out. Let me know if it works or blows up by [opening an issue on the GitHub mirror](https://github.com/indie-mirror/nodecert/issues). [Pull requests](https://github.com/indie-mirror/nodecert/pulls) are also [welcome](./CHANGELOG.md).

Thanks in advance! 🤓👍 – [Aral](https://ar.al)
