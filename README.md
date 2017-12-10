# alpine-pkg-http-parser

[![CircleCI](https://img.shields.io/circleci/project/sgerrand/alpine-pkg-http-parser/master.svg)](https://circleci.com/gh/sgerrand/alpine-pkg-http-parser)

This is the Node.js [HTTP message parser][http-parser] as an Alpine Linux package.

## Releases

See the [releases page][releases] for the latest download links.

## Installing

The current installation method for these packages is to pull them in using
`wget` or `curl` and install the local file with `apk`:

```
apk --no-cache add ca-certificates
wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://raw.githubusercontent.com/sgerrand/alpine-pkg-http-parser/master/sgerrand.rsa.pub
wget https://github.com/sgerrand/alpine-pkg-http-parser/releases/download/2.7.1-r0/http-parser-2.7.1-r0.apk
apk --allow-untrusted add http-parser-2.7.1-r0.apk
```

[http-parser]: https://github.com/nodejs/http-parser
[releases]: https://github.com/sgerrand/alpine-pkg-http-parser/releases/
