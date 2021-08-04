---
layout: post
comments: true
---

I'm currently going through the exercise of installing a Bitcoin full node.

In this post I will write about how I verified the Bitcoin core release signatures file.

- First download the Bitcoin tarball from [Bitcoin Core](https://bitcoin.org/en/download)
```bash
wget https://bitcoin.org/bin/bitcoin-core-0.21.1/bitcoin-0.21.1-x86_64-linux-gnu.tar.gz
```
- Compute it's signature using `sha256sum`
```bash
sha256sum bitcoin-0.21.1-x86_64-linux-gnu.tar.gz
```
- Then download release signatures from the same page
```bash
wget https://bitcoin.org/bin/bitcoin-core-0.21.1/SHA256SUMS.asc
```
- Check if the signature computed by `sha256sum` is same as the one in the release file
- Verify release signatures file
```bash
gpg --verify SHA256SUMS.asc
```
- Download the public key used to sign the release file [Wladimir J. van der Laan’s releases key](https://bitcoin.org/laanwj-releases.asc)
```bash
wget https://bitcoin.org/laanwj-releases.asc
```
- Print the key fingerprint
```bash
gpg --with-fingerprint laanwj-releases.asc
```
- Compare with the key fingerpring displayed by `gpg --verify`

References
==========

* https://bitcoin.org/en/full-node#linux-instructions
* https://bitcoin.org/en/download
* http://irtfweb.ifa.hawaii.edu/~lockhart/gpg/
