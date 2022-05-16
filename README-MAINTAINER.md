# Maintainer notes

## Adding a new team member key

```
make rings/team.gpg
gpg --no-default-keyring \
    --keyring rings/team.gpg \
    --no-auto-check-trustdb \
    --import $KEYFILE
jetring-gen \
    rings/team.gpg~ \
    rings/team.gpg \
    "add kim (ID: 65C26E471F45B123)"
jetring-accept team/ add-65C26E471F45B123 
gpg --output team/index.asc \
    --armor \
    --detach-sign \
    --sign team/index
```

## Adding a new archive key

```
make rings/tcsh-archive-keyring.gpg
gpg --no-default-keyring \
    --keyring rings/tcsh-archive-keyring.gpg \
    --no-auto-check-trustdb \
    --import $KEYFILE
jetring-gen \
    rings/tcsh-archive-keyring.gpg~ \
    rings/tcsh-archive-keyring.gpg \
    "add tcsh signing key 2022"
mv add-50C538DBEF9D37E1 add-tcsh-signing-key-2022
jetring-accept keys/ add-tcsh-signing-key-2022
gpg --output keys/index.asc \
    --armor \
    --detach-sign \
    --sign keys/index
```

Note that the filenames used for the changeset filenames must never
be subsets of another changeset filename, or the keyring build will
over-eagerly remove them and then fail.

## Removing an archive key

* Remove `keys/add-$foo`
* Remove the relevant entry from `keys/index`

```
gpg --output keys/index.asc \
    --armor \
    --detach-sign \
    --sign keys/index
```

Confirm that the result was as expected by:

```
make clean
make rings/tcsh-archive-keyring.gpg
```

and checking the contents of the keyring

## Pre-build

```
gpg --armor --detach-sign rings/tcsh-archive-keyring.gpg
```
