---
layout: post
comments: true
---

If you want to distribute release of your software, you can proceed as
the following for people to verify the legitimacy of the files you are
releasing.

First, create a tarball if necessary.

```sh
tar cz release/ -f release.tar.gz
```

Second, create a checksum for the files in the current directory and
redirect the standard outut into a file.

```
sha256sum ./* >> SHA256SUM.txt
```

Then, GPG sign the checksum file.

```
gpg --detach-sign SHA256SUM.txt
```

You can then, distribute the checksum file and the related signature
with your release files.  This will enable people to verify the origin
of the files and to make sure that they didn't get tempered during
transit.

```
gpg --verify SHA256SUM.txt.sig SHA256SUM.txt
```
