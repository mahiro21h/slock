slock - simple screen locker (patched)
============================
the reference client for testing new security improvements to screen lockers for [xlibre xserver](https://github.com/X11Libre/xserver)

NOTE: be sure to run `setxkbmap -option "terminate:ctrl_alt_bksp"` before testing dontzap. [see](https://www.x.org/archive/X11R7.5/doc/RELNOTES.txt) for more info


Planned changes
---------------
- [x] perform security checks on `exec_path`
  - [x] verify that `exe_path` is null terminated
  - [x] verify that `exe_path` points to a valid executable
- [ ] securely re-launch screen locker
  - [x] monitor and re-launch screen locker if it crashes
  - [x] ~~cover screens with fallback windows until screen locker creates its windows~~ no longer necessary
  - [ ] handle failed re-launch attempts
    - [x] check for failure of `fork()` and `execv()`
    - [x] stop re-launching if attempts exceed limit
    - [ ] update screenlocker windows to inform user that the session is now locked
- [x] screen locker always above all windows
  - [x] ~~add new window attribute specifically for screen locker windows~~ doesn't appear to be necessary
  - [x] new windows are never stacked above screen locker windows
- [ ] use xnamespace extension
- [ ] ensure extension works in the case where the system is woken up after being suspended
- [ ] ensure extension works in the case where xserver's internal screensaver kicks in while screen is locked?
- [ ] handle multiple screens
- [ ] secure input
  - [ ] only screen locker has access to keyboard and mouse while screen is locked


Requirements
------------
you need to build the following patched dependencies and install them starting from top to bottom (make sure you have xlibre-xserver installed before installing):

- [xorgproto](https://github.com/mahiro21h/xorgproto/tree/myextension)
- [xcbproto](https://github.com/mahiro21h/xcbproto/tree/myextension)
- [libxcb](https://github.com/mahiro21h/libxcb/tree/myextension)
- [xlibre-xserver](https://github.com/mahiro21h/xserver/tree/myextension)


Installation
------------
see [original readme](README)
