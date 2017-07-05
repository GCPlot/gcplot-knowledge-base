# GCPlot Knowledge Base

GCPlot is a Java Garbage Collector \(GC\) logs analyzer. Basically, it's an effort to solve all GC logs reading/analyzing problems once and forever. As developers, we were tired about the current situation and efforts needed to just compare some number of GC configurations, so we decided to start from scratch and build a tool that suits best for us.

How to deliver logs to our platform? Many ways. You can do it [manually, via API or with our smart GCPlot Connector](/ways-of-sending-logs.md) agent. The manual approach means that you just upload files one-by-one by hand and see the reports based on this files only. [GCPlot Connector](/log-files-processing.md) allows you to continuously connect your JVM\(s\) to our system, and just build reports from time to time with the interval of interest.

The report itself consists of a lot of graphs, measurements, stats, etc about how exactly your GC works. You can also manage the timeline and decide - whether to dig deeper, by analyzing, for example, 2 minutes interval in the most details, or check everything from the bird's eye view by choosing the last month.

The next important thing is the persistence of the reports - they just shouldn't fade away after some time. No problem, we are keeping them forever.

We are also working on a comprehensive alerting system. And a lot of other things.

And yes, currently we are in _beta_, so everything is free for use. Knowing how much we already can, this is surely a good deal.

