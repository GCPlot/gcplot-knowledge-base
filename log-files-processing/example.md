# Example

This example is aimed to show the full cycle of JVM GC logs connection to GCPlot Platform.

#### Story

Suppose I have some small cluster, located in Europe. Here I have Ubuntu 16.04 server with the Cassandra database, which I want to connect to GCPlot in order to monitor GC activity and pauses.

#### Step 1 - Install gcpc

I'd prefer to install `gcpc` tool using APT. First, I will check which Java version is installed by default on my server:

```bash
root@ubuntu-1gb-fra1-01:~# java -version
openjdk version "1.8.0_121"
OpenJDK Runtime Environment (build 1.8.0_121-8u121-b13-0ubuntu1.16.04.2-b13)
OpenJDK 64-Bit Server VM (build 25.121-b13, mixed mode)
```

This matches Java 7+ requirement, so we can go on with installation:

```
root@ubuntu-1gb-fra1-01:~# echo "deb [trusted=yes] https://repo.fury.io/gcplotdev/ /" >> /etc/apt/sources.list.d/fury.list
root@ubuntu-1gb-fra1-01:~# apt-get update
root@ubuntu-1gb-fra1-01:~# apt-get install gcpc
The following NEW packages will be installed:
  gcpc
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 9,130 kB of archives.
After this operation, 12.3 MB of additional disk space will be used.
Get:1 https://repo.fury.io/gcplotdev  gcpc 0.0.2-1 [9,130 kB]
Fetched 9,130 kB in 5s (1,755 kB/s) 
Selecting previously unselected package gcpc.
Preparing to unpack .../gcpc_0.0.2-1_all.2-1-all ...
Unpacking gcpc (0.0.2-1) ...
Processing triggers for systemd (229-4ubuntu16) ...
Processing triggers for ureadahead (0.100.0-19) ...
Setting up gcpc (0.0.2-1) ...
Processing triggers for systemd (229-4ubuntu16) ...
Processing triggers for ureadahead (0.100.0-19) ...
```

After that I'd like to check that `gcpc` service is now available and stopped:

```
root@ubuntu-1gb-fra1-01:~# service gcpc status
● gcpc.service
   Loaded: loaded (/etc/init.d/gcpc; bad; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:systemd-sysv-generator(8)
```

Everything is good. Now I need to go and register my server in the GCPlot Platform.

#### GCPlot Configuration

I'm going to add my JVM with Cassandra under a name "cassandra" and fill in some other properties.

![](/assets/Screen Shot 2017-04-18 at 9.45.42 AM.png)After clicking "Save changes" I can now see it in the list:

![](/assets/Screen Shot 2017-04-18 at 9.48.09 AM.png)

Now I'd like to find out my "EU Cluster" analysis group and "cassandra" JVM IDs:

![](/assets/Screen Shot 2017-04-18 at 9.49.09 AM.png)![](/assets/Screen Shot 2017-04-18 at 9.49.36 AM.png)

So, Analysis Group ID is `ba9d422b-9337-4462-8b1a-36487ef41462`, and JVM ID is `6eea39a1-03b3-430f-ba18-2c57c0c5a797`.

I'll also go to my [Profile page](/gcplot-overview/you-profile.md) to get my API Token, which will be needed for `gcpc`

The last thing is to enable proper Data Source in Analysis Group, so it will start checking for GC log files:

![](/assets/Screen Shot 2017-04-18 at 9.53.08 AM.png)

Now we are ready to configure the `gcpc` tool on the server. I will need to edit `/etc/default/gcpc`file for that. It's contents are empty currently:

```
## Account token value
export ACCOUNT_TOKEN=

## Analyze Group ID
export ANALYZE_GROUP_ID=

## Comma-separated list of JVM ID(s)
export JVM_IDS=

## Comma-separated directories with the GC log files, one per each JVM
## Warning! The directories must be provided in the same order as JVM_IDS
export LOGS_DIRS=

# GC Log Files extension suffix (before .N number for rotating logs),
# often set with "-Xloggc" JVM flag
export EXTENSION=.log
```

After filling in it would look like this:

```
## Account token value
export ACCOUNT_TOKEN=a357570c551d2cb56b56ee3c25952d3b1a0271af9d94be7a842c76f7816d0ad3

## Analyze Group ID
export ANALYZE_GROUP_ID=ba9d422b-9337-4462-8b1a-36487ef41462

## Comma-separated list of JVM ID(s)
export JVM_IDS=6eea39a1-03b3-430f-ba18-2c57c0c5a797

## Comma-separated directories with the GC log files, one per each JVM
## Warning! The directories must be provided in the same order as JVM_IDS
export LOGS_DIRS=/var/log/cassandra

# GC Log Files extension suffix (before .N number for rotating logs),
# often set with "-Xloggc" JVM flag
export EXTENSION=gc.log
```

Please note the EXTENSION variable change. Since I use general logs directory `/var/log/cassandra`, and don't want gcpc to try to upload my application/error logs along with GC ones:

```
root@ubuntu-1gb-fra1-01:/var/log/cassandra# ls -la
total 308
drwxr-xr-x  2 cassandra cassandra   4096 Apr 18 07:07 .
drwxrwxr-x 10 root      syslog      4096 Apr 18 07:07 ..
-rw-r--r--  1 cassandra cassandra 183372 Apr 18 07:07 debug.log
-rw-r--r--  1 cassandra cassandra  55714 Apr 18 07:08 gc.log.0.current
-rw-r--r--  1 cassandra cassandra  61903 Apr 18 07:07 system.log
```

After all that, I am ready to start `gcpc`:

```
root@ubuntu-1gb-fra1-01:/var/log/cassandra# service gcpc start
root@ubuntu-1gb-fra1-01:/var/log/cassandra# service gcpc status
● gcpc.service
   Loaded: loaded (/etc/init.d/gcpc; bad; vendor preset: enabled)
   Active: active (exited) since Tue 2017-04-18 07:09:24 UTC; 2s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 11982 ExecStart=/etc/init.d/gcpc start (code=exited, status=0/SUCCESS)
```

You can also check `gcpc` application logs to make sure everything is smooth:

```
2017/04/18 07:10:58.871 INFO [c.g.c.Bootstrap] Starting GCPlot connector.
2017/04/18 07:10:58.875 INFO [c.g.c.Bootstrap] Using Java Version 1.8.0_121 by Oracle Corporation, amd64 Linux 4.4.0-72-generic
2017/04/18 07:11:01.253 INFO [c.g.c.Bootstrap] Starting directory [/var/log/cassandra] watcher daemon for JVM [6eea39a1-03b3-430f-ba18-2c57c0c5a797].
```

After some time we can see that new logs were processed by GCPlot:

![](/assets/Screen Shot 2017-04-18 at 10.27.22 AM.png)

If you want to see DEBUG info here as well, just edit `/var/lib/gcpc/bin/logback.xml`:

```
   ...
     <root level="debug">
        <appender-ref ref="FILE_INFO" />
    </root>
   ...
```

Then restart gcpc:

```
root@ubuntu-1gb-fra1-01:~# service gcpc restart
```



