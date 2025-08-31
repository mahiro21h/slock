slock - simple screen locker (patched)
============================
patched simple screen locker which can disable tty switching and zapping for [xlibre xserver](https://github.com/X11Libre/xserver)

NOTE: be sure to run `setxkbmap -option "terminate:ctrl_alt_bksp"` before testing dontzap. [see](https://www.x.org/archive/X11R7.5/doc/RELNOTES.txt) for more info


Planned changes
---------------
- [x] perform security checks on `exec_path `
  - [x] verify that `exe_path` is null terminated
  - [x] verify that `exe_path` points to a valid executable
- [-] securely re-launch screen locker
  - [x] monitor and re-launch screen locker if it crashes
  - [ ] cover screens with fallback windows until screen locker creates its windows
- [ ] screen locker always above all windows
  - [ ] add new window attribute specifically for screen locker windows
  - [ ] new windows are never stacked above screen locker windows
- [ ] use xnamespace extension


Requirements
------------
you need to install the following patched packages starting from top to bottom:

- [xorgproto](https://github.com/mahiro21h/xorgproto/tree/myextension)
- [xcbproto](https://github.com/mahiro21h/xcbproto/tree/myextension)
- [libxcb](https://github.com/mahiro21h/libxcb/tree/myextension)
- [xlibre-xserver](https://github.com/mahiro21h/xserver/tree/myextension) (make sure you have xlibre-xserver==25.0.0.9 before installing)


Installation
------------
Edit config.mk to match your local setup (slock is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install slock
(if necessary as root):

    make clean install


Running slock
-------------
Simply invoke the 'slock' command. To get out of it, enter your password.
