# Installation

This page is a description of `gcpc` agent installation using different approaches.

* [APT](#apt)
* [Yum](#yum)
* [tar.gz \(Unix\)](#targzunix)
* [tar.gz \(macOS\)](#macos)

After the installation is complete, you have to go to the [Configuration page](/log-files-processing/connector-installation-and-configuration/configuration.md) to receive further instructions before running `gcpc`.

## Downloads

0.0.2 \[[tar.gz](https://downloads.gcplot.com/connector/gcpc-0.0.2.tar.gz)\] \[[deb](https://downloads.gcplot.com/connector/bin/gcpc_0.0.2-1_all.deb)\] \[[rpm](https://downloads.gcplot.com/connector/bin/gcpc-0.0.2-2.all.rpm)\]

## Requirements

`gcpc` requires Java SE/JDK of version 7+ to be installed on the target machine. You can also change Java Home directory using tool [configuration](/log-files-processing/connector-installation-and-configuration/configuration.md).

## APT \(Linux/Debian\) {#apt}

The easiest way to install `gcpc` on Linux/Debian is to use `apt` package manager.

First of all, you have to add our repository to apt list of packages:

```
$ echo "deb [trusted=yes] https://repo.fury.io/gcplotdev/ /" >> /etc/apt/sources.list.d/fury.list
```

Then we need to force `apt` to update:

```
$ sudo apt-get update
```

After that we are ready to install it:

```
$ sudo apt-get install gcpc
```

## YUM \(Fedora\) {#yum}

You can also install `gcpc` via `yum` .

First create a new file **/etc/yum.repos.d/fury.repo**:

```
$ touch /etc/yum.repos.d/fury.repo
```

Then add next lines to it \(using vim or nano\):

```
[fury]
name=gcpc
baseurl=https://repo.fury.io/gcplotdev/
enabled=1
gpgcheck=0
```

After that check that everything is fine:

```
$ sudo yum --disablerepo=* --enablerepo=fury list available
```

After that you are ready to install `gcpc`:

```
$ sudo yum install gcpc
```

## Install from tar.gz \(Unix\) {#targzunix}

First step is to download the latest package of gcpc. Current latest version is 0.0.2:

```
$ cd /tmp
$ wget https://downloads.gcplot.com/connector/gcpc-0.0.2.tar.gz
$ tar xvfz gcpc-0.0.2.tar.gz
```

After that all files will be extracted to the `gcpc-0.0.2/` directory. We will need to move them from the temporary directory:

```
$ mkdir -p /opt/gcpc
$ mv /tmp/gcpc-0.0.2/ /opt/gcpc
```

That's it. Optionally, you can create a new user, which will be used to run an agent:

```
$ sudo useradd -r gcpc -d /opt/gcpc -s /bin/bash
$ sudo chown -R gcpc:gcpc /opt/gcpc
```

Now the task is to separate your `gcpc` confguration file from the installation directory. Also we would want to move an executable to the `init.d` directory with Unix services:

```
$ sudo mv /opt/gcpc/bin/settings /etc/default/gcpc
$ sudo mv /opt/gcpc/bin/gcpc /etc/init.d/gcpc
```

Finally, open the `/opt/gcpc/bin/gcpc` file in a text edit of your choice \(vim, nano, etc\). You will notice this lines in the begging:

```
GCP_DIRECTORY=$PARENT_DIR
GCP_CONFIG=$GCP_DIRECTORY/bin/settings
GCP_USER=gcpc
```

Change `GCP_CONFIG` and `GCP_DIRECTORY` appropriately to:

```
GCP_DIRECTORY=/opt/gcpc
GCP_CONFIG=/etc/default/gcpc
```

and also change `GCP_USER` to the user name under which you wish to run `gcpc`, if required.

Save and close the file. Installation is ready.

## Install from tar.gz \(macOS\) {#macos}

First, let's see what the user is currently used:

```
$ whoami
myuser
```

Remember that value, we will use it later. The next steps are the same as with other platforms - download, extract, move:

```
$ cd /tmp
$ wget https://downloads.gcplot.com/connector/gcpc-0.0.2.tar.gz
$ tar xvfz gcpc-0.0.2.tar.gz
$ mkdir -p ~/.gcpc
$ mv /tmp/gcpc-0.0.2/ ~/.gcpc
```

After that we need to move configuration file out of installation directory \(to save it during future updates\):

```
$ mkdir -p ~/.gcpc/data && mkdir -p ~/.gcpc/log
$ mv ~/.gcpc/bin/settings ~/.gcpc/settings
$ dirname ~/.gcpc
/Users/myuser
```

So, `/Users/myuser/.gcpc/config`now is our path to the configuration file. Open the `/Users/myuser/.gcpc/bin/gcpc` file in a text edit of your choice \(vim, nano, etc\). You will notice this lines in the begging:

```
GCP_CONFIG=$GCP_DIRECTORY/bin/settings
GCP_USER=gcpc
```

Change `GCP_CONFIG` appropriately to:

```
GCP_CONFIG=/Users/myuser/.gcpc/config
GCP_USER=myuser
```

Open `/Users/myuser/.gcpc/config` file with any text edit and change next variables:

```
export DATA_DIR=/Users/myuser/.gcpc/data
export GCP_APP_LOG_DIR=/Users/myuser/.gcpc/log
```

Save and close the file. Installation is ready.

