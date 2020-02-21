# Host Mobility Yocto/OE-core Setup

Fork of [Toradex repo manifest](http://git.toradex.com/cgit/toradex-bsp-platform.git/)

To simplify installation we provide a repo manifest which manages the different git repositories
and the used versions. (more on repo: http://code.google.com/p/git-repo/ )

Before proceeding take a look at [Yocto Manual - Build Host Packages](http://www.yoctoproject.org/docs/2.3/mega-manual/mega-manual.html#packages).

Install the repo bootstrap binary:

```
sudo apt-get install repo
or
mkdir ~/bin
PATH=~/bin:$PATH
curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

Create a directory for your `hostmobility-bsp-platform` setup to live in and clone the meta information.
```
$ mkdir hostmobility-bsp-platform
$ cd hostmobility-bsp-platform
$ repo init -u git@github.com:hostmobility/hostmobility-bsp-platform.git -b master
$ repo sync
```

Setup build environment.
```
$ export TEMPLATECONF=${PWD}/layers/meta-hostmobility-distro/conf
$ . layers/openembedded-core/oe-init-build-env build
or
Follow the instructions in mx4-deploy to make a ".img" file
```
**NOTE!** You need to run the above command on each new session. If you all ready have an build directory it will be un-touched and only environment will be setup.

Start baking!
```
$ bitbake console-hostmobility-image
```

Build result will end up in `hostmobility-bsp-platform/deploy` directory.
