# Analyze Groups

The central part of GCPlot is its ability to process logs and store the result, be it single file uploaded by hands or realtime connection with some remote server. And here comes the typical problem for such cases - how to organize everything with the least complexity and the best usability.

We have tried to solve this with the thing called **Analyze Group**. Inside it you can add any number of JVMs, each representing the unique instance running on your server\(s\). There is also a special Analyze Group called **Files**, which contains all the GC log files uploaded manually \(via Quick Upload\).

Here is a simple diagram which shows the typical flow:

![](/assets/Untitled Diagram %282%29.png)

This is the screenshot of such structure created in GCPlot UI:

![](/assets/Screen Shot 2017-04-13 at 11.45.50 PM.png)







