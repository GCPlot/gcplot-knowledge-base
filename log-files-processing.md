# GCPlot Connector

GCPlot Connector is a special mechanism for continuous connection between GCPlot platform and your JVMs. The main benefit is the automation of GC logs processing  - they come to the platform and being processed into reports as a stream.

The easiest way to start with GCPlot Connector is to install & configure a special [gcpc tool](/log-files-processing/connector-installation-and-configuration.md) near your JVM\(s\), select "GCPlot Default" option in Data Source \(in [Analysis Group](/gcplot-overview/analyze-groups.md) configuration\) - and enjoy! Nevertheless, other Data Sources are also supported, such as your custom S3 Storage. We are working further to extend this list.

> #### Important!
>
> Please read our [Limitations](/log-files-processing/troubleshooting.md) page carefully before considering connecting. If you have the problems described here, make sure they are fixed before the integration.

You will also need to register and configure correct Analysis Group and JVM\(s\) in the GCPlot Platform. [The next article](/log-files-processing/configuring-analyze.md) describes such configuration in the details.

You can also explore our [complete example](/log-files-processing/example.md) of GCPlot Connector usage.

