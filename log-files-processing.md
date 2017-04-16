# GCPlot Connector

GCPlot Connector is a special mechanism for continuous connection between GCPlot platform and your JVMs. The main benefit is automation of log files processing  - they come to the platform as a stream and being processed into reports in non-stop.

The easiest way to start with GCPlot Connector is to install & configure a special [gcpc tool](/log-files-processing/connector-installation-and-configuration.md) near your JVM, enable "GCPlot Default" Logs Source \(in Analysis Group configuration\) - and enjoy! Nevertheless, other log sources are also supported, such as custom S3 Storage. We are working further to extend this list.

Before connecting your JVM, you should first create and configure appropriately in the GCPlot Platform. [The next article](/log-files-processing/configuring-analyze.md) describes such configuration in details.

You can also explore our [complete example](/log-files-processing/example.md) of GCPlot Connector functionality usage.

