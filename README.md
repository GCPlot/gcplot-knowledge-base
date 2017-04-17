# GCPlot Knowledge Base

Welcome to the [GCPlot](https://gcplot.com) documentation!

GCPlot is, simply put, a Java Garbage Collector logs analyzer. Basically, it's an effort to solve all GC logs reading/analyzing problems once and forever. As a developers, we were tired about the current situation and efforts needed to just compare some number of GC configurations, so we just decided to start from scratch and build the best we need. That's why it's simply made by developers to the developers.

All you have to do is to deliver your raw log data to it, and enjoy the thorough [reports](/gcplot-overview/reports.md), graphs, measurements, etc. The reports are properly time-based - you can manage the current interval and decide - whether to dig deeper, by selecting, for example, 30 seconds interval with the most comprehensive details, or look on your GC report from the bird's eye view by choosing the last month.

The next thing is the persistence of the reports - the just shouldn't fade away after some time. No problem, we are keeping them forever.

Finally, how actually to deliver logs to our platform? Many ways. You can do it [manually, via API or with our smart GCPlot Connector](/ways-of-sending-logs.md) agent. Manual approach means that you just upload files one-by-one by hand and see the reports based on this files only. [GCPlot Connector](/log-files-processing.md) allows you to continuously connect your JVM\(s\) logs to our system, and just build reports from time to time with the interval of interest.

We are also working on a comprehensive alerting system. And a lot of other things. Very cool. Refer to the [Analyze Groups](/gcplot-overview/analyze-groups.md) page for the details about registering your JVMs in our system and GCPlot Connector [dedicated page](/log-files-processing.md).

And yes, currently we are in _beta_, so everything is free to use. Knowing how much we already can, this is surely a good deal.

