# Host Mobility Yocto/OE-core Setup

Fork of Toradex repo manifest (http://git.toradex.com/toradex-bsp-platform.git)

To simplify installation we provide a repo manifest which manages the different git repositories
and the used versions. (more on repo: http://code.google.com/p/git-repo/ )

Install the repo bootstrap binary:
```
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
$ TEMPLATECONF=${PWD}/layers/meta-hostmobility-distro/conf . layers/openembedded-core/oe-init-build-env build
You had no conf/local.conf file. This configuration file has therefore been
created for you with some default values. You may wish to edit it to, for
example, select a different MACHINE (target hardware). See conf/local.conf
for more information as common configuration options are commented.

You had no conf/bblayers.conf file. This configuration file has therefore been
created for you with some default values. To add additional metadata layers
into your configuration please add entries to conf/bblayers.conf.

The Yocto Project has extensive documentation about OE including a reference
manual which can be found at:
    http://yoctoproject.org/documentation

For more information about OpenEmbedded see their website:
    http://www.openembedded.org/


### Shell environment set up for builds. ###

You can now run 'bitbake <target>'

Host Mobility targets are:
    console-hostmobility-image

You can also run generated qemu images with a command like 'runqemu qemux86'
```
**NOTE!** You need to run the above command on each new session. If you all ready have an build directory it will be un-touched and only environment will be setup.

Start baking!
```
$ bitbake console-hostmobility-image
```

Build result will end up in `hostmobility-bsp-platform/deploy` directory.
