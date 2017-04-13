# GCPlot Knowledge Base

Welcome to the [GCPlot](https://gcplot.com) documentation!

GCPlot is, simply put, a Java Garbage Collector logs analyzer. Basically, it's an effort to solve all GC logs reading/analyzing problems once and forever. As a developers, we were tired about the current situation and efforts needed to just compare some number of GC configurations, so we just decided to start from scratch and build the best we need. That's why it's simply made by developers to the developers.

All you have to do is to deliver your raw log data to it, and enjoy the thorough [reports](/gcplot-overview/reports.md), graphs, measurements, etc. The reports are properly time-based - you can manage the current interval and decide - whether to dig deeper, by selecting, for example, 30 seconds interval with the most comprehensive details, or look into your GC configuration from the bird's eye view by choosing last month. 

Another idea is that you should never loose already processed log files - no problem, they will be saved forever. Oh yeah!

Finally, how actually to deliver? No problem. You can do it [manually or with our smart connector](/ways-of-sending-logs.md). Manual approach means that you just upload files by hand one-by-one and face the result. [Connector](/log-files-processing.md) allows you to continuously connect your JVM\(s\) to the system, and just build reports from time to time. We are also working on a comprehensive alerting system. And a lot of other things. Very cool.

And yes, currently we are in _beta_, so everything is free to use. After everything written above it's just stunning.

