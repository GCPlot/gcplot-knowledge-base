# Analysis Groups

The central part of GCPlot is its ability to process logs and store the result, be it single file uploaded by hands or realtime connection with some remote server. And here comes the typical problem for such cases - how to organize everything with the least complexity and the best usability.

We have tried to solve this with the thing called **Analysis Group**. Inside it you can add any number of JVMs, each representing the unique instance running on your server\(s\). There is also a special Analysis Group called **Files**, which contains all the GC log files uploaded manually \(via Quick Upload\).

> #### Hint
>
> The best use case is to create the new Analysis Group for each cluster of servers you have.

Here is a simple diagram which shows the typical flow \(read more about our GCPlot Connector in [this section](/log-files-processing.md)\):

![](/assets/Untitled Diagram %282%29.png)

This is the screenshot of such structure created in GCPlot UI:

![](/assets/Screen Shot 2017-04-14 at 8.47.53 AM.png)

So, basically, the main purpose of Analysis Groups is to aggregate some JVM's reports under some logical group. You can also manage such things as Timezone, Logs Source, etc from it. This will apply to all JVMs inside it. 



