# Installation

This page is a description of `gcpc` agent installation using different approaches.

## Downloads

0.0.2 \[[tar.gz](https://downloads.gcplot.com/connector/gcpc-0.0.2.tar.gz)\] \[[deb](https://downloads.gcplot.com/connector/bin/gcpc_0.0.2-1_all.deb)\] \[[rpm](https://downloads.gcplot.com/connector/bin/gcpc-0.0.2-2.all.rpm)\]

## Requirements

`gcpc` requires Java SE/JDK of version 7+ to be installed on the target machine. You can also change Java Home directory using tool [configuration](/log-files-processing/connector-installation-and-configuration/configuration.md).

## APT \(Linux/Debian\)

The easiest way to install `gcpc` on Linux/Debian is to use `apt` package manager.

First of all, you have to add our repository to apt list of packages:

```
$ echo "deb [trusted=yes] https://repo.fury.io/gcplotdev/ /" >> /etc/apt/sources.list.d/fury.list
```

Then we need to force `apt` to update:

```
$ apt-get update
```

After that we are ready to install it:

```
$ apt-get install gcpc
```

## YUM \(Fedora\)

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
$ yum --disablerepo=* --enablerepo=fury list available
```

After that you are ready to install `gcpc`:

```
$ yum install gcpc
```

## Install from tar.gz \(Unix\)

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
$ useradd -r gcpc -d /opt/gcpc -s /bin/bash
$ chown -R gcpc:gcpc /opt/gcpc
```

Now the task is to separate your `gcpc` confguration file from the installation directory:

```
$ mv /opt/gcpc/bin/settings /etc/default/gcpc
```

Finally, open the `/opt/gcpc/bin/gcpc` file in a text edit of your choice \(vim, nano, etc\). You will notice this lines in the begging:

```
GCP_CONFIG=$GCP_DIRECTORY/bin/settings
GCP_USER=gcpc
```

Change `GCP_CONFIG` appropriately to:

```
GCP_CONFIG=/opt/default/gcpc
```

and also change `GCP_USER` to the user name under which you wish to run `gcpc`, if required.

When all edits are complete, save and close the file.

## Install from tar.gz \(macOS\)

First let's see what user we are running:

```
$ whoami
myuser
```

The next steps are the same as with other platforms - download, extract, move:

```
$ cd /tmp
$ wget https://downloads.gcplot.com/connector/gcpc-0.0.2.tar.gz
$ tar xvfz gcpc-0.0.2.tar.gz
$ sudo mkdir -p /opt/gcpc
$ sudo mv /tmp/gcpc-0.0.2/ /opt/gcpc
```

After that we need to move configuration file out of installation directory \(to save it during future updates\):

```
$ mkdir -p ~/.gcpc
$ sudo mv settings ~/.gcpc/settings
$ dirname ~/.gcpc
/Users/myuser
```

So, `/Users/myuser/.gcpc/config`now is our path to the configuration file. Open the `/opt/gcpc/bin/gcpc` file in a text edit of your choice \(vim, nano, etc\). You will notice this lines in the begging:

```
GCP_CONFIG=$GCP_DIRECTORY/bin/settings
GCP_USER=gcpc
```

Change `GCP_CONFIG` appropriately to:

```
GCP_CONFIG=/Users/myuser/.gcpc/config
GCP_USER=myuser
```

Save and close the file. 

