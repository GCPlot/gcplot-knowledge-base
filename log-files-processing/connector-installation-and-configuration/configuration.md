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

| Name | Default Value | Description | Example |
| :--- | :--- | :--- | :--- |
| ACCOUNT\_TOKEN | - | This is your personal profile token. You can find it on your [personal profile](/gcplot-overview/you-profile.md) page. | export ACCOUNT\_TOKEN="8tnc94t787tg47q43gct4g3" |
| ANALYZE\_GROUP\_ID | - | This is an ID of the [Analysis Group](/gcplot-overview/analyze-groups.md), under which the JVM\(s\) you want to connect are located. ![](/assets/Screen Shot 2017-04-17 at 9.06.10 PM.png) | export ANALYZE\_GROUP\_ID="141fbb62-cff5-4d1b-94e7-b9549d219d80" |
| JVM\_IDS | - | Fill that field with JVM ID\(s\) from GCPlot Platform which you want to connect. Separate them **with comma without whitespaces**.![](/assets/Screen Shot 2017-04-17 at 9.12.41 PM.png) | export JVM\_IDS="18fa4c0d-2899-4257-b7d2-32aed4aa2a9b,358acf95-a92f-4262-ab15-200f57540583" |
| LOGS\_DIRS | - |  |  |



