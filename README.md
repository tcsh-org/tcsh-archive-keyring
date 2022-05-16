README for the tcsh-archive-keyring package
===========================================

Introduction
------------

The TCSH project signs the Release files in its Debian repository with
the keys contained in this package.

A quick overview about this package:

* /usr/share/keyrings/tcsh-archive-keyring.gpg:

    A keyring including all actively used keys to sign Release files in
    the TCSH Debian repository.

* /usr/share/doc/tcsh-archive-keyring/tcsh.list

    A source configuration for apt(8) for the TCSH Debian repository.

More information about the archive authentication feature can be found
in the manpage apt-secure(8).
