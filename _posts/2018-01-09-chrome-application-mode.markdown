---
layout:  post
title:   "Create web app using Google Chrome"
date:    2018-01-09 00:00:00 +0000
excerpt: "Create web app using Google Chrome application mode on macOS" 
image:   ""
---

In Google Chrome/Chromium browser one of a useful feature is application mode. 
It allows run the browser with simplifying UI without toolbar with predefined URL.
Moreover, you can run the browser with a separate profile.
These two features allow creating "web app".

For example, let's create "web app" for `google.com`.

First of all, create new app dirs:

```
mkdir -p Google.app/Contents/MacOS
```

Then we need create macos app manifest, `vim Google.app/Contents/Info.plist`:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" “http://www.apple.com/DTDs/PropertyList-1.0.dtd”>
<plist version=”1.0″>
<dict>
<key>CFBundleExecutable</key>
<string>App</string>
</dict>
</plist>
```

Then create shell script to run browser, `vim Google.app/Contents/MacOS/App`:

```
#!/bin/sh
exec /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --app="https://google.com/" --user-data-dir="$HOME/Library/google-app/Profile" "$@"
```

Not to forgot to make it executable:

```
chmod a+x Google.app/Contents/MacOS/App
```

That's all! Now you can run you Google.app:

```
open Google.app
```

And as a bonus, you can set an icon for it, for example [like this][change-an-application-icon].

P.S. There are other [command line switches for Google Chrome][chromium-cli-switches].

[chromium-cli-switches]: https://peter.sh/experiments/chromium-command-line-switches/
[change-an-application-icon]: https://superuser.com/questions/37811/how-can-i-change-an-application-icon-in-mac-os-x