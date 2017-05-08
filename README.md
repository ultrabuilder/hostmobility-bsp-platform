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
mkdir hostmobility-bsp-platform
cd hostmobility-bsp-platform
repo init -u git@github.com:hostmobility/hostmobility-bsp-platform.git -b master
repo sync
```

Setup build environment and start baking!
```
TEMPLATECONF=${PWD}/layers/meta-hostmobility-distro/conf . layers/openembedded-core/oe-init-build-env build
bitbake console-hostmobility-image

```

You need to run the above command on each new session. If you all ready have an build directory it will be un-touched and only environment will be setup.

You will find the build result in `hostmobility-bsp-platform/deploy` directory.

