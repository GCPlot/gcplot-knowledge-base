# Reports

The reports are, by no means, the most interesting part of the story. When you upload your GC logs file by hands or setup logs pipe from your servers via Connector, you will finally open the desirable report. Let's see what it can tell us. Here is the screenshot with a typical recently processed file report:

![](/assets/Screen Shot 2017-04-14 at 9.16.12 AM.png)

We will analyze each part of the report in details in the sections below.

#### Dates & Times Range

This is the most powerful part of report. You can select the desirable interval of interest, be it a whole week or 3 seconds. The timezone is configured in the parent Analysis Group.

![](/assets/Screen Shot 2017-04-14 at 10.13.33 AM.png)

By default we load the whole day before the last event processed. Current limit is 3 months.

If Time Range check box is not selected, the whole day will be considered.

> #### Hint
>
> Note that we, of course, apply some sampling when showing you the graphs. But the algorithm for it is quite simple - the wider interval, the more sampled events. If you want to reduce the impact of sampling, just narrow down your date & time range on the interval of interest to you.

### Report Data

#### General Stats

General Stats page just shows brief info about the file/JVM - initial and last GC event dates, name, etc.

Also, sometimes GC log file contains info about JVM flags used to start your VM, server RAM/Swap memory status. We will also show everything here.

#### Pauses

This tab contains all the verbose stats & graphs about GC pauses - Young/Tenured/Full collections, split on STW \(Stop-The-World\) and Concurrent, Percentiles and etc.

Percentiles shows the distribution of STW pauses by the percent of occurrence:

![](/assets/Screen Shot 2017-04-14 at 10.28.31 AM.png)

For example, line `99% | 117.416` means that 99% of STW events are under 117.416 milliseconds.

There are also four graphs: 

* `Pause Durations (Stop-The-World only)` - pauses in milliseconds

* `Log(x) Pause Durations (Stop-The-World only)` - Log10\(x\) of pauses, which is very helpful for seeing distribution of low values

* `Concurrent Phase Durations (Non-STW)` - concurrent collections durations in milliseconds \(if available\)

* `Log(x) Concurrent Phase Durations (Non-STW)` - Log10\(x\) of concurrent durations \(if available\)

And finally you can see how much time does STW and Concurrent collections took comparing to the whole time application was running: 

![](/assets/Screen Shot 2017-04-14 at 10.34.01 AM.png)

