# Analysis Groups

The central part of GCPlot is its ability to process GC logs and building the reports from it, either from single file uploaded by hands or real-time agent from the remote server. And quite often they need to be organized somehow. For that, you can create an **Analysis Group**. Inside it you can add any number of JVMs, each representing the unique VM instance, which runs on your server\(s\). There is also a special Analysis Group called **Files**, which contains all the GC log files uploaded [manually](/ways-of-sending-logs.md) \(via Quick Upload\).

> #### Hint
>
> The best use case is to create the new Analysis Group for each cluster of servers you have.

Here is a simple diagram which shows the typical flow:

![](/assets/Untitled Diagram %283%29.png)

This is the screenshot of such structure created in GCPlot UI:![](/assets/Screen Shot 2017-06-22 at 7.48.40 AM.png)

So, again, the main purpose of Analysis Group is to aggregate some JVM's reports under some logical structure. You can also manage here things like Timezone, Data Source, etc. This settings will apply to all JVMs inside it.

#### JVMs {#jvms}

You can add any number of JVMs inside Analysis Group - just go to "JVMs" tab and start editing/adding/removing them:

![](/assets/Screen Shot 2017-04-16 at 6.03.13 PM.png)

JVM in terms of GCPlot is a special continuous report of any real JVM that you own. In order to start filling it with real data, you should connect given JVM with your GC log files. There is a dedicated [GCPlot Connector](/log-files-processing.md) article, which describes everything in the details.

#### Analysis Group ID {#analysis-group-id}

You can find the ID of Analysis Group by clicking on `config` box in the left sidebar. You will also be able to change different configurations here:

![](/assets/Screen Shot 2017-04-16 at 5.53.26 PM.png)

