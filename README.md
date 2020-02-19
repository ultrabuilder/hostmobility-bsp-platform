###This manifest file is used by mx4-t30-fr-bsp-v1.5.x###
# Host Mobility oe-core Setup

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

Create a directory for your oe-core setup to live in and clone the meta information.
```
mkdir oe-core
cd oe-core
repo init -u git@github.com:hostmobility/hostmobility-bsp-platform.git -b master
repo sync
```

Optionally create a development branch in all git repositories

  repo start mybranch --all

Source the file export to setup the environment. On first invocation this also copies a sample
configuration to build/conf/*.conf.

  . export

Adapt build/conf/local.conf to your needs. At least check the variables BB_NUMBER_THREADS,
PARALLEL_MAKE, and MACHINE. Set MACHINE to a preferred value and when you need a different
one override it from the command line.

More information see Toradex developer website:

  http://developer.toradex.com/software-resources/arm-family/linux/board-support-package/openembedded-(core)

Inteded for internal use only:
```
# To generate a manifest from what is currently checked out:
repo manifest -r -o manifest.xml
```
