# Installation

This page is a description of `gcpc` agent installation on the different platforms using different approaches.

## Downloads

0.0.2 \[[tar.gz](https://downloads.gcplot.com/connector/gcpc-0.0.2.tar.gz)\] \[[deb](https://downloads.gcplot.com/connector/bin/gcpc_0.0.2-1_all.deb)\] \[[rpm](https://downloads.gcplot.com/connector/bin/gcpc-0.0.2-2.all.rpm)\]

## APT \(Linux/Debian\)

The easiest way to install `gcpc` on Linux/Debian is to use `apt` package manager. 

First of all, you have to add our repository to apt list of packages:

`echo "deb [trusted=yes] https://repo.fury.io/gcplotdev/ /" >> /etc/apt/sources.list.d/fury.list`

Then we need to force `apt` to update:

`apt-get update`

After that we are ready to install it:

`apt-get install gcpc`

## YUM \(Fedora\)

You can also install `gcpc` via `yum` . 

First create a new file **/etc/yum.repos.d/fury.repo**:

`touc /etc/yum.repos.d/fury.repo`

Then add next lines to it \(using vim or nano\):

```
[fury]
name=gcpc
baseurl=https://repo.fury.io/gcplotdev/
enabled=1
gpgcheck=0
```

After that check that everything is fine:

`yum --disablerepo=* --enablerepo=fury list available`

After that you are ready to install `gcpc`:

`yum install gcpc`

## Install from Tarball \(tar.gz\)





