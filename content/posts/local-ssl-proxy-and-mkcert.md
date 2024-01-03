+++
title = "local-ssl-proxy and mkcert"
author = ["Dmitry Markushevich"]
date = 2024-01-02T00:00:00-08:00
lastmod = 2024-01-02T17:02:50-08:00
tags = ["seedling"]
draft = false
+++

Ocassionally, it's helpful to run a local service with SSL. My particular scenario has an application that insists on redirecting everything to `https` even when running in development mode.

Start with by installing [local-ssl-proxy](https://www.npmjs.com/package/local-ssl-proxy):

```shell
npm install -g local-ssl-proxy
```

run it like so:

```shell
local-ssl-proxy --source 9001 --target 9000
```

if you want to avoid unsightly untrusted certificate errors install [mkcert](https://github.com/FiloSottile/mkcert):

```shell
brew install mkcert
mkcert -install
mkcert mydomainname.com
```

Assuming that `mydomainname.com` resolves to your `localhost` (via `/etc/hosts` trickery for example) you can now do

```shell
local-ssl-proxy --key mydomainname-key.pem --cert mydomainname.pem --source 443 --target 3000
```

and access `https://mydomainname.com` with no certificate errors.
