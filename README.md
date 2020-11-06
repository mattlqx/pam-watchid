PAM WatchID
-----------
A PAM plugin for authenticating using the new kLAPolicyDeviceOwnerAuthenticationWithBiometricsOrWatch API in macOS 10.15, written in Swift.

![](demo.gif)

Installation
------------

1. `$ sudo make install`
2. Edit `/etc/pam.d/sudo` to include as the first line: `auth sufficient pam_watchid.so "policy=watch"`

You can specify `policy=touch` if you only wish to support TouchID or leave blank to do either. In my testing on macOS Big Sur (11.0), I wasn't able to get both to work by not specifying the policy, so I included this way of choosing which to specify. You can do a watch policy on one line and a touch policy on the next. Doing this, I was able to prefer watch authentication but fallback to touch.

You can specify a reason with `"reason=authenticate with root"` but leaving it blank will include the command being run in the dialog.

_Note that you might have other `auth`, don't remove them._
