tcsh-archive-keyring
====================

The TCSH project signs the `Release` files in its repository for Debian
and Ubuntu with the keys contained in this package.

Included in this package:

* `/usr/share/keyrings/tcsh-archive-keyring.gpg`

    A keyring including all keys actively used to sign the repository.

* `/usr/share/doc/tcsh-archive-keyring/tcsh.list`

    A source configuration for `apt(8)`.

More information about the archive authentication feature can be found
in the manpage for `apt-secure(8)`.
