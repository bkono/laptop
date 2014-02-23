Laptop
======

The original Laptop is a script to set up a Mac OS X or Linux laptop for Rails development.

This version has been modified to include brew-casks for taking a machine from
an almost clean slate, all the way to bkonowitz approved _useable_.

Requirements
------------

### Universal

Git and SSH keys for accessing any private repos if using the additional
development setup components.

### Mac OS X

Install a C compiler:

For Snow Leopard (10.6): use [OS X GCC
Installer](https://github.com/kennethreitz/osx-gcc-installer/).

For Lion (10.7) or Mountain Lion (10.8): use [Command Line Tools for
XCode](https://developer.apple.com/downloads/index.action).

For Mavericks (10.9): run `sudo xcodebuild -license` and follow the instructions
to accept the XCode agreement.  Then run `xcode-select --install` in your
terminal and then click "Install". 

_NOTE: XCode is the preferred approach for
completing the Mac install, as it guarantees an installation of git and other needed
bootstrap components._

### Linux

We support:

* [13.10: Saucy Salamander](https://wiki.ubuntu.com/SaucySalamander/ReleaseNotes),
* [13.04: Raring Ringtail](https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes),
* [12.10: Quantal Quetzal](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes), and
* [12.04 LTS: Precise Pangolin](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes),
* Debian stable (currently [wheezy](http://www.debian.org/releases/stable/)).
* Debian testing (currently [jessie](http://www.debian.org/releases/testing/)).

Install
-------

### Mac OS X

Read, then run the script:

    bash <(curl -s https://raw.github.com/bkonowitz/laptop/master/mac)

After the script completes, open a new shell (or preferably, switch to the newly
installed Iterm2) to fully load the new development environment.

### Linux

Read, then run the script:

    bash <(wget -qO- https://raw.github.com/thoughtbot/laptop/master/linux)

### BK Approved setup

Read, then run the script:

    bash <(curl -s https://raw.github.com/bkonowitz/laptop/master/bk)

After the script completes, open a new shell (or preferably, switch to the newly
installed Iterm2) to fully load the new development environment.

### Universal

This is not a fully unattended install. At the beginning, and throughout the
application installs, you will be prompted for your password periodically. Best to
keep half an eye on the installation to keep it moving.

During the Mac and BK installs, your password will be needed at the following times:

- shell change to zsh (beginning)
- fixing zsh environment bug (first use of sudo, beginning)
- google-hangouts (middle)
- virtualbox (middle)
- crashplan (late)

What it sets up
---------------

* Zsh as your shell
* Bundler gem for managing Ruby libraries
* Exuberant Ctags for indexing files for vim tab completion
* Foreman gem for serving Rails apps locally
* Heroku Config plugin for local `ENV` variables
* Heroku Toolbelt for interacting with the Heroku API
* Hub gem for interacting with the GitHub API
* Homebrew for managing operating system libraries (OS X only)
* Postgres for storing relational data
* Rails gem for writing web applications
* Rbenv for managing versions of the Ruby programming language
* Redis for storing key-value data
* Ruby Build for installing Rubies
* Ruby stable for writing general-purpose code
* The Silver Searcher for finding things in files
* Tmux for saving project state and switching between projects
* Watch for periodically executing a program and displaying the output
* Vim plugins, shell scripts, and a snazzy zsh environment
* A lot of must_have apps, and much more ...

The best way to know what it does is to follow the install directions above
starting with the task *READ*.

It should take less than 45 minutes to install (depends on your machine).

Tweaking for your preferences
-------

You are encouraged to create your own Manifest and additional components.
Setting up a machine is a very personal task, so don't hesitate to take this
base and run with it!

To get going, simply create a new Manifest.foo file and list each component in
the order you want the install to proceed. Use the existing components as an
example, and add more for any functionality or configuration that helps get your
development environment setup 'just right'.

Once your Manifest file is setup, run bin/build.sh. This will cause all Manifest.xxxx
files to rebuild into single scripts named by their extension. Execute the newly
created version, and enjoy!

Original Credits
-------

![thoughtbot](http://thoughtbot.com/assets/tm/logo.png)

Laptop is maintained and funded by [thoughtbot, inc](http://thoughtbot.com/community).
The names and logos for thoughtbot are trademarks of thoughtbot, inc.

Thank you, [contributors](https://github.com/thoughtbot/laptop/graphs/contributors)!

Original License
-------

Laptop is © 2011-2014 thoughtbot, inc. It is free software, and may be
redistributed under the terms specified in the LICENSE file.
