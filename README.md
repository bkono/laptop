Laptop
======

Laptop is a script to set up a Mac OS X or Linux laptop for Rails development.

Important BK Note
-----------------

This repository, while still functional and a very reasonable approach to setup, is slowly being
superceded by a combination of the chef-based [kitchenplan](kitchenplan.github.io/kitchenplan),
[bkono kitchenplan config](github.com/bkono/kitcheplan-config), and
[chef-zgen](github.com/bkono/chef-zgen). There are a number of reasons for this shift, but the
primary two are easier idempotency via chef, and (through chef-zgen) dotfiles and potential
chef-solo based reuse across linux servers and OSX desktops alike. I highly encourage you to check
out these three projects for your next box repave.


Requirements
------------

### Mac OS X

Install a C compiler:

For Snow Leopard (10.6): use [OS X GCC
Installer](https://github.com/kennethreitz/osx-gcc-installer/).

For Lion (10.7) or Mountain Lion (10.8): use [Command Line Tools for
XCode](https://developer.apple.com/downloads/index.action).

For Mavericks (10.9): installed with the script, no prerequisite.

_BK Note_
On fresh installs of Mavericks I have had a variety of issues when not doing the
previous pre-req steps. To prevent issues, I recommend:

    Install Xcode
    Run `sudo xcodebuild -license` # be sure to agree to the license
    Run `xcode-select --install`   # follow the dialog box prompts

### Linux

We support:

* [14.04: Trusty Tahr](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes),
* [13.10: Saucy Salamander](https://wiki.ubuntu.com/SaucySalamander/ReleaseNotes),
* [12.04 LTS: Precise Pangolin](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes),
* Debian stable (currently [wheezy](http://www.debian.org/releases/stable/)).
* Debian testing (currently [jessie](http://www.debian.org/releases/testing/)).

Install
-------

### Mac OS X

Read, then run the script:

    bash <(curl -s https://raw.githubusercontent.com/bkonowitz/laptop/master/mac) 2>&1 tee ~/laptop.log

### linux

read, then run the script:

    bash <(wget -qo- https://raw.githubusercontent.com/bkonowitz/laptop/master/linux) 2>&1 tee ~/laptop.log

### bk approved setup

prior to following the mac instructions above run:

    curl -o ~/.laptop.local https://raw.githubusercontent.com/bkonowitz/laptop/master/bk.laptop.local

read, then run the script:

    bash <(curl -s https://raw.githubusercontent.com/bkonowitz/laptop/master/mac) 2>&1 tee ~/laptop.log

After the script completes, open a new shell (or preferably, switch to the newly
installed Iterm2) to fully load the new development environment.

_BK Note_
The |& approach was causing issues on fresh builds in terminal. Swapped back to
old style of 2>&1.

Debugging
---------

Your last Laptop run will be saved to `~/laptop.log`. Read through it to see if
you can debug the issue yourself. If not, copy the lines where the script
failed into a [new GitHub
Issue](https://github.com/thoughtbot/laptop/issues/new) for us. Or, attach the
whole log file as an attachment.

What it sets up
---------------

* Zsh as your shell
* Bundler gem for managing Ruby libraries
* Exuberant Ctags for indexing files for vim tab completion
* Foreman for serving Rails apps locally
* Heroku Config plugin for local `ENV` variables
* Heroku Toolbelt for interacting with the Heroku API
* Hub gem for interacting with the GitHub API
* Homebrew for managing operating system libraries (OS X only)
* ImageMagick for cropping and resizing images
* Node.js and NPM, for running apps and installing JavaScript packages
* Parity for development, staging, and production parity
* Postgres for storing relational data
* Qt for headless JavaScript testing via Capybara Webkit
* Rails gem for writing web applications
* Rbenv for managing versions of the Ruby programming language
* Redis for storing key-value data
* Ruby Build for installing Rubies
* Ruby stable for writing general-purpose code
* The Silver Searcher for finding things in files
* Tmux for saving project state and switching between projects
* Watch for periodically executing a program and displaying the output

It should take less than 15 minutes to install (depends on your machine).

Laptop can be run multiple times on the same machine safely. It will upgrade
already installed packages and install and activate a new version of ruby (if
one is available).

Make your own customizations
----------------------------

Put your customizations in `~/.laptop.local`. For example, your
`~/.laptop.local` might look like this:

    #!/bin/sh

    brew tap caskroom/cask
    brew install brew-cask

    brew cask install dropbox
    brew cask install google-chrome
    brew cask install rdio

You should write your customizations such that they can be run safely more than
once. See the `mac` and `linux` scripts for examples.

Laptopped Linux Vagrant boxes
-----------------------------

We now publish [Vagrant](http://vagrantup.com) boxes for every supported Linux
distro. These boxes have the laptop script applied already and are ready to go.

Create a Vagrantfile:

    vagrant init thoughtbot/ubuntu-14-04-server-with-laptop

In the same directory as your Vagrantfile:

    vagrant up
    vagrant ssh

Laptopped vagrantcloud boxes currently available:

* `thoughtbot/debian-wheezy-64-with-laptop`
* `thoughtbot/debian-jessie-64-with-laptop`
* `thoughtbot/ubuntu-14-04-server-with-laptop`
* `thoughtbot/ubuntu-13-10-server-with-laptop`
* `thoughtbot/ubuntu-12-04-server-with-laptop`

See our [vagrantcloud profile](https://vagrantcloud.com/thoughtbot). You must
have Vagrant >= 1.5.0 to use vagrantcloud images directly.

Credits
-------

![thoughtbot](http://thoughtbot.com/assets/tm/logo.png)

Laptop is maintained and funded by [thoughtbot, inc](http://thoughtbot.com/community).
The names and logos for thoughtbot are trademarks of thoughtbot, inc.

Thank you, [contributors](https://github.com/thoughtbot/laptop/graphs/contributors)!

Contributing
------------

Please see [CONTRIBUTING.md](https://github.com/thoughtbot/laptop/blob/master/CONTRIBUTING.md).

License
-------

Laptop is © 2011-2014 thoughtbot, inc. It is free software, and may be
redistributed under the terms specified in the LICENSE file.
