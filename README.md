<p align="center" width="100%">
<a href="https://zt.dev"><img src="zt.png" width="100"></a>
</p>

<p align="center">
    <b>
    <a>@hanzozt/zt-browzer-sw-workbox-strategies</a>
    <br>
    <br>
    <b>
    This component contains a sub-component of the ServiceWorker used as part of the <a href="https://zt.dev/about">Hanzo ZT</a> Zero Trust browZer stack</b>
    
</p>

<p align="center">
    <br>
    <b>Are you interested in knowing how to easily embed programmable, high performance, zero trust networking into your app, on any internet connection, without VPNs?
    <br>
    Learn more about our <a href="https://zt.dev/about">Hanzo ZT</a> project by clicking the image below:</b>
    <br>
    <br>
    <a href="https://zt.dev"><img src="zt-dev-logo.png" width="200"></a>
</p>

---
[![Build](https://github.com/hanzozt/zt-browzer-sw-workbox-strategies/workflows/Build/badge.svg?branch=main)]()
[![CodeQL](https://github.com/hanzozt/zt-browzer-sw-workbox-strategies/workflows/CodeQL/badge.svg?branch=main)]()
[![Issues](https://img.shields.io/github/issues-raw/hanzozt/zt-browzer-sw-workbox-strategies)]()
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![LOC](https://img.shields.io/tokei/lines/github/hanzozt/zt-browzer-sw-workbox-strategies)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=rounded)](CONTRIBUTING.md)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v2.0%20adopted-ff69b4.svg)](CODE_OF_CONDUCT.md)

---

<!-- TOC -->

- [Overview](#overview)
- [Installation](#installation)
- [Contributing](#contributing)
- [License](#license)

<!-- /TOC -->


## Overview 

coming soon...

## Installation

The `zt-browzer-sw-workbox-strategies` is intended to be consumed by the [`zt-http-agent`](https://github.com/hanzozt/zt-http-agent), not as a general purpose module in your build. It is available through [npm](https://www.npmjs.com/package/@hanzozt/zt-browzer-sw-workbox-strategies), and installed via the following command:

    npm i @hanzozt/zt-browzer-sw-workbox-strategies

The the [`zt-http-agent`](https://github.com/hanzozt/zt-http-agent) serves the contents of `zt-browzer-sw` (and `zt-browzer-sw-workbox-strategies` which is embedded within `zt-browzer-sw`) in response to HTTP requests originating from the 
[`zt-browzer-runtime`](https://github.com/hanzozt/zt-browzer-runtime). It does so by using the code shown below:
 
```js     

// Locate the path to the ServiceWorker distro within the build of our running instance
let pathToZitiBrowzerSwModule = require.resolve('@hanzozt/zt-browzer-sw');

pathToZitiBrowzerSwModule = pathToZitiBrowzerSwModule.substring(0, pathToZitiBrowzerSwModule.lastIndexOf('/'));

// Read the component off the disk
fs.readFile( path.join( pathToZitiBrowzerSwModule, outgoing.path.split("/").pop() ), (err, data) => {

if (err) {  // If we can't read the file from disk

    res.writeHead(500, { 'x-zt-http-agent-err': err.message });
    res.end('');
    return;

} else {    // Emit the Service Worker onto the wire

    res.writeHead(200, { 
        'Content-Type': 'application/javascript',
        'Service-Worker-Allowed': '/',
        'x-zt-http-agent-info': 'self-configured zt service worker' 
    });

    res.write(data);  // the actual service worker code

    res.end('\n');
    return;
}

```


## Contributing

[![AllContibs](https://img.shields.io/github/contributors/hanzozt/zt-browzer-sw-workbox-strategies)]()


Your Contributions are welcome! Please see our [Contributing Guide](Contributing.md) for more details. Thanks to all our contributors!

[![Contibs](https://contrib.rocks/image?repo=hanzozt/zt-browzer-sw-workbox-strategies)]()



## License

Apache 2.0
