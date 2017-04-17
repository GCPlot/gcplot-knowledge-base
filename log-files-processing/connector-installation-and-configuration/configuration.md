# Configure & Run

Before starting `gcpc` agent you have to properly configure it, i.e. point to an actual Analysis Group and JVM\(s\) in the GCPlot Platform.

The whole configuration is located in a single file, which location depends on your [installation](/log-files-processing/connector-installation-and-configuration/installation.md) method. For **APT**, **Yum**, **tar.gz** this is normally `/opt/default/gcpc`. Open it with the text editor of your choice, and you should notice a lot of variables, some of which are empty:

```bash
#!/bin/bash

###################################
#
# WARNING! Values below should be OBLIGATORILY modified
#
###################################

## Account token value
export ACCOUNT_TOKEN=

## Analyze Group ID
export ANALYZE_GROUP_ID=

## Comma-separated list of JVM ID(s)
export JVM_IDS=

## Comma-separated directories with the GC log files, one per each JVM
## Warning! The directories must be provided in the same order as JVM_IDS
export LOGS_DIRS=

###################################

# Uncomment next line if you want to explicitly define Java home dir
#export JAVA_HOME=/path/to/java/home

export JAVA_PROC_ARGS="-Xmx128m -Xms128m"

# Connector working data directory
export DATA_DIR=/var/lib/gcpc

# GCPC Application logs location
export GCP_APP_LOG_DIR=/var/log/gcpc

# GCPlot API Host
export GCP_HOST=gs.gcplot.com

# Whether to use HTTPS for connections
export USE_HTTPS=true

# GC Log Files extension suffix (before .N number for rotating logs),
# often set with "-Xloggc" JVM flag
export EXTENSION=.log

export RELOAD_CONFIG_MS=30000
export SYNC_FILES_MS=5000
export TTL=86400000
```

As you can see, you are obligated to fill 4 variables. We will iterate and describe each of them.

---

#### ACCOUNT\_TOKEN

This is your personal API token. You can find it on your [Personal Profile](/gcplot-overview/you-profile.md) page. Example:

```bash
export ACCOUNT_TOKEN="8tnc94t787tg47q43gct4g3"
```

---

#### ANALYZE\_GROUP_\__ID

A unique ID of the Analysis Group, under which the JVM\(s\) which you want to connect are created.

![](/assets/Screen Shot 2017-04-17 at 9.34.08 PM.png)

Example:

```bash
export ANALYZE_GROUP_ID="141fbb62-cff5-4d1b-94e7-b9549d219d80"
```

---

#### JVM\_IDS

Fill that field with the JVM ID\(s\) from Analysis Group which GC logs you want to connect with. If you connect multiple JVMs on the same machine, fill them **comma-separated without whitespaces**. 

You can find JVM ID by clicking on it in the left sidebar and going to Manage tab:

![](/assets/Screen Shot 2017-04-17 at 9.12.41 PM.png)Example of adding two JVMs:

```
export JVM_IDS="18fa4c0d-2899-4257-b7d2-32aed4aa2a9b,358acf95-a92f-4262-ab15-200f57540583"
```

---

#### LOGS\_DIRS

The list of directories where GC logs are located by each JVM. 

> #### Important!
>
> The order, in which logs directories are passed into this parameter should exactly match the order in which JVM\_IDS are passed, so that gcpc can match each directory to each JVM ID. 
>
> For example, if logs directory for JVM "X" is "/X", and for JVM "Y" is "/Y", then parameters should look like: 
>
> ```
> export JVM_IDS="X,Y"
> export LOGS_DIRS="/X,/Y"
> ```

Example:

```
export LOGS_DIRS=/var/log/eu1,/var/log/eu2
```

---

Other fields has default values and could be omitted. We will describe them briefly:

| Name | Description |
| :--- | :--- |
| JAVA\_HOME | Custom Java Home location for gcpc. |
| EXTENSION | The extension of GC log files to look. By default it's ".log". This shouldn't include rotations sub-extensions, like ".log.5" or ".log.current", as gcpc detects that automatically. |
| JAVA\_PROC\_ARGS | JVM arguments for the gcpc process. |
| DATA\_DIR | Directory where temporary and persistent data, needed for gcpc will be located. |
| GCP\_APP\_LOG\_DIR | Application logs directory of the agent. Helpful for debug and troubleshooting. |
| GCP\_HOST | Main API host of GCPlot. Should normally never be changed. |
| USE\_HTTPS | Whether to use secure connections. By default true. Our general recommendation is to never change this value without a good reason. |
| RELOAD\_CONFIG\_MS | How often to reload Analysis Group config from GCPlot. |



