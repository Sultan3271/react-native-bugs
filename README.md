# react-native-bugs
1. ## Android Studio ( The emulator process for avd was terminated ) 
download Install Microsoft c++ redistributable X64 from browser,
and issue will be fixed

2. ## Ruby problem onn mac ( erro related nfk, cocoapods not installed, ruby version )
issue: etching nkf-0.2.0.gem Building native extensions. This could take a while... ERROR: Error installing nkf: ERROR: Failed to build gem native extension. current directory: /Library/Ruby/Gems/2.6.0/gems/nkf-0.2.0/ext/nkf /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/bin/ruby -I /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0 -r ./siteconf20250910-33693-1hr9q4a.rb extconf.rb creating Makefile current directory: /Library/Ruby/Gems/2.6.0/gems/nkf-0.2.0/ext/nkf make "DESTDIR=" clean
 
An error occurred while installing nkf (0.2.0), and Bundler cannot continue. Make sure that gem install nkf -v '0.2.0' --source 'https://rubygems.org/' succeeds before bundling. In Gemfile: cocoapods was resolved to 1.16.2, which depends on xcodeproj was resolved to 1.27.0, which depends on CFPropertyList was resolved to 3.0.7, which depends on nkf ✖ Installing Ruby Gems

### Solution
Got it — you’re still on **macOS system Ruby (2.6.10)**, not the Homebrew Ruby (3.4.5). That’s exactly why `nkf` keeps failing.

Let’s switch your shell to use the **Homebrew Ruby**.

---

### 🔧 Steps to fix

1. **Find where Homebrew Ruby is installed:**

```bash
brew --prefix ruby
```

On Apple Silicon, it’s usually:

```
/opt/homebrew/opt/ruby
```

On Intel Macs, it might be:

```
/usr/local/opt/ruby
```

---

2. **Update your shell config (`.zshrc`)**
   Add this line to the bottom of `~/.zshrc`:

```bash
export PATH="$(brew --prefix ruby)/bin:$PATH"
```

If you’re on Intel, that expands to:

```bash
export PATH="/usr/local/opt/ruby/bin:$PATH"
```

If you’re on Apple Silicon:

```bash
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
```

---

3. **Reload your shell**

```bash
source ~/.zshrc
```

---

4. **Verify Ruby version**

```bash
ruby -v
```

👉 should now show `ruby 3.4.5`

And check:

```bash
which ruby
```

👉 should point to `/opt/homebrew/opt/ruby/bin/ruby` (or `/usr/local/opt/ruby/bin/ruby`)

---

5. **Reinstall Bundler & CocoaPods**

```bash
gem install bundler
gem install cocoapods
```

---

⚡ After that, `pod install` will work without the `nkf` error.

---

Do you want me to give you the **exact `.zshrc` line** for your machine (Apple Silicon vs Intel)? If you paste me the result of:

```bash
uname -m
```

I’ll tell you which path to use.



3. ## Command PhaseScriptExecution failed with a nonzero exit code - Error when Archive/Build on Xcode(did everything but still)
 Solution That Worked for Me:
The problem was caused by a stale .xcode.env.local file that pointed to a removed Node.js version.
Check your nnode versionn(node -v) annd update it in xcode.env.local

4. ## compiledebugjavac failed (rn maps,screens, anyother library and also mentions cmake like 3.22.1)
  solution is: All you have to do is go to android/build.gradle and change your ndk to up version like from 27.xxxx to 28.xxx and also install it in android studio sdk tool








