sshpass
=======

This is forked from [https://github.com/bdelliott/sshpass](https://github.com/bdelliott/sshpass). I fixed some simple bugs to make it work. 

* 2014Nov13 FIXED: "global name 'keychainservice' is not defined" error on line 37. 
* 2014Nov13 FIXED: store password in keychain with the account in the form of `username@host`
* 2014Nov14 Feature: add a naive solution to support `sftp`.

If you need to login to a server that, for whatever reason, has public key auth disabled, you can use this script
to automate login via username and password.

Your password will be stored in the appropriate keyring backend. (e.g. Keychain on Mac OS X)

Requires:
---------

* Python
* pip (or easy_install)
* pip install pexpect
* pip install keyring


Usage on Mac:
-------

In iterm2 profile, set command as follow:

    python /path/to/sshpass.py -p [port] [username]@[password]

then start new tab with that profrile and enjoy.

##Security Note

Use it with caution. coz `keyring` will get all your password **without authentication**. So if some python programmer sit in front of your mac and have the basic info of your account name, which is very easy to accquire, and type few commands will get your password in keychain! 
There are some advices to strengthen security level:

* Since keyring use the combination of `(servicename, account)` to get your password back. So you can change a customized `keychainservice` string to strengthen security, which is `ssh_py_default` known by everyone.
* Have your keychain locked always to make it harder to get your account name and some other useful info. 
* Further more, lock your mac whenever you level the desk.