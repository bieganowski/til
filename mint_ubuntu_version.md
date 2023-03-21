In order to find ubuntu version on Mint:

```bash
$ cat /etc/upstream-release/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu Focal Fossa"
```
(Ubuntu version 20.04)

To figure out which subrelease you are using, you need to know what kernel you are running, e.g.
```bash
$ uname -r
5.11.0-46-generic
```
(kernel above 5.11)