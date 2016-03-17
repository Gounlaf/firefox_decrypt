#### About

Firefox Decrypt is a tool to extract passwords from Firefox/Thunderbird
profiles.

It can be used to recover passwords from a profile protected by a Master
Password as long as the latter is known.
If a profile is not protected by a Master Password, a password will still be
requested but can be left blank.

This tool does not try to crack or brute-force the Master Password in any way.
If the Master Password is not known it will simply fail to recover any data.

This script is written in Python and is compatible with versions 2.7+ and 3.4+.

Additionally it requires access to libnss3 which is part of Firefox and
Thunderbird, although depending on system configuration, the script may fail to
locate it there.

Alternatively you can install libnss3 (Debian/Ubuntu) or nss (Arch/Gentoo/...).
libnss3 is part of http://www.mozilla.org/projects/security/pki/nss/


#### Usage

Simply run:

```
python firefox_decrypt.py
```

and it will prompt for which profile to use and the master password of that
profile.

If you don't keep your Firefox profiles on a standard folder you can call the
script with:

```
python firefox_decrypt.py /folder/containing/profiles.ini/
```

If you don't want to display all passwords on screen you can use:

```
python firefox_decrypt.py | grep -C2 keyword
```
where keyword is part of the expected output (URL, username, email, password ...)

Since version **0.4** it is now also possible to export stored passwords to
*pass* from http://passwordstore.org . To do so use:

```
python firefox_decrypt.py --export-pass
```
and **all** existing passwords will be exported after the pattern
`web/<address>[:<port>]/<login>`.

There is currently no way of selectively exporting passwords.


#### Changelog

##### 0.4
- Add option to export passwords to *pass* from http://passwordstore.org

##### 0.3
- Polyglot Python 2 and 3. Python 3 now supported.
- Improved debugging information with -v or -vv

##### 0.2
- Added support for logins.json. New format since Firefox 32.

##### 0.1
- Initial version supporting Firefox 3.5 and up.
