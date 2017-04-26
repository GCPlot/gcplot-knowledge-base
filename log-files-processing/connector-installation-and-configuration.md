# gcpc Tool

`gcpc` is a special agent tool which is responsible for GC logs synchronization between your running JVM and GCPlot [Reports](/gcplot-overview/reports.md). It's written on and requires Java 6+. Next diagram represents a typical workflow:

![](/assets/gcpc.png)

When `gcpc` is started, it scans logs directory continuously for the new data and automatically gzip & upload them. After that, our GCPlot Logs Analyzer do the job and finally you can build a report in [GCPlot UI](https://gcplot.com) with the latest data from your server.

You can find a very comprehensive guides about its [installation](/log-files-processing/connector-installation-and-configuration/installation.md) and [configuration](/log-files-processing/connector-installation-and-configuration/configuration.md), as well as an [example](/log-files-processing/example.md).

