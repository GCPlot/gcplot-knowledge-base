# Analysis Groups

The central part of GCPlot is its ability to process logs and store the result, be it single file uploaded by hands or realtime connection with some remote server. And here comes the typical problem for such cases - how to organize everything with the least complexity and the best usability.

We have tried to solve this with the thing called **Analysis Group**. Inside it you can add any number of JVMs, each representing the unique instance running on your server\(s\). There is also a special Analysis Group called **Files**, which contains all the GC log files uploaded manually \(via Quick Upload\).

> #### Hint
>
> The best use case is to create the new Analysis Group for each cluster of servers you have.

Here is a simple diagram which shows the typical flow \(read more about our GCPlot Connector in [this section](/log-files-processing.md)\):

![](/assets/Untitled Diagram %283%29.png)

This is the screenshot of such structure created in GCPlot UI:

![](/assets/Screen Shot 2017-04-16 at 5.54.10 PM.png)

So, basically, the main purpose of Analysis Groups is to aggregate some JVM's reports under some logical group. You can also manage such things as Timezone, Logs Source, etc from it. This will apply to all JVMs inside it.

#### JVMs {#jvms}

You can add any number of JVMs inside Analysis Group - just go to "JVMs" tab and start editing/adding/removing them:

![](/assets/Screen Shot 2017-04-16 at 6.03.13 PM.png)

JVM in terms of GCPlot is a special continuous report of any real JVM that you own. In order to start filling it with real data, you should connect given JVM with your GC log files. There is dedicated [GCPlot Connector](/log-files-processing.md) article, which describes everything in the details.

#### Analysis Group ID {#analysis-group-id}

You can find the ID of Analysis Group by clicking on `info` box in the left sidebar. You will also be able to change different configurations here:

![](/assets/Screen Shot 2017-04-16 at 5.53.26 PM.png)

