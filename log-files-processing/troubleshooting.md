# Limitations

#### Log Files Rotation

In order `gcpc` can receive GC log files flow continuously and without gaps, they have to be rotating. You can control such behavior with `-XX:+UseGCLogFileRotation` and `-XX:NumberOfGCLogFiles=N`, where N is a max number of files. The example of directory structure with rotating logs:

```
$ ls -la
total 604
drwxr-xr-x 2 gcs gcs   4096 Apr 16 15:35 .
drwxr-xr-x 3 gcs gcs   4096 Apr  4 22:43 ..
-rw-rw-r-- 1 gcs gcs 131290 Apr 12 22:12 gc.log.0
-rw-rw-r-- 1 gcs gcs 131512 Apr 14 09:59 gc.log.1
-rw-rw-r-- 1 gcs gcs 131180 Apr 14 10:00 gc.log.2
-rw-rw-r-- 1 gcs gcs  88910 Apr 16 15:36 gc.log.3.current
```

In that case `gcpc` will known that `gc.log.3.current` file is currently being written, while `gc.log.0`, `gc.log.1` and `gc.log.2` can be already uploaded and processed.

#### Datestamps Required

Yes, basically GCPlot Connector ecosystem can't work with GC log files with **timestamps-only**, which are reset to zero with every new file. In that case it's extremely hard to match each log with each other and show you a continuous and correct report. 

If you have such problem, just add `-XX:+PrintGCTimeStamps -XX:+PrintGCDateStamps` flags to your JVM on startup. 

Here is an example of log file with **timestamps-only**:

```
0.000: [GC [1 CMS-initial-mark: 0K(12288K)] 281K(16320K), 0.0053399 secs]
0.006: [CMS-concurrent-mark-start]
0.057: [CMS-concurrent-mark: 0.051/0.051 secs]
0.057: [CMS-concurrent-preclean-start]
0.057: [CMS-concurrent-preclean: 0.000/0.000 secs]
```

And this is with **datestamps** presented as well:

```
2015-07-02T20:53:00.436+0200: 0.260: [GC (Allocation Failure) [PSYoungGen: 24571K->4081K(28672K)] 24571K->22186K(94208K), 0.0199218 secs] [Times: user=0.02 sys=0.02, real=0.02 secs]
2015-07-03T06:58:33.016+0200: 75416.800: [GC (GCLocker Initiated GC) [PSYoungGen: 616448K->6515K(650240K)] 1041014K->431081K(1705472K), 0.0239463 secs] [Times: user=0.09 sys=0.00, real=0.03 secs] 
2015-07-03T09:35:15.452+0200: 84819.235: [GC (Last ditch collection) [PSYoungGen: 0K->0K(678400K)] 575536K->575536K(2076672K), 0.0193629 secs] [Times: user=0.06 sys=0.01, real=0.01 secs] 
```



