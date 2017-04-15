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

* `Pause Durations (Stop-The-World only)` - GC pauses in milliseconds

* `Log(x) Pause Durations (Stop-The-World only)` - Log10\(x\) of GC pauses, which is very helpful for seeing distribution of low values

* `Concurrent Phase Durations (Non-STW)` - concurrent collections durations in milliseconds \(if available\)

* `Log(x) Concurrent Phase Durations (Non-STW)` - Log10\(x\) of concurrent durations \(if available\)

And finally you can see how much time does STW and Concurrent collections took comparing to the whole time application was running:

![](/assets/Screen Shot 2017-04-14 at 10.34.01 AM.png)

#### Memory

This tab shows a lot of graphs related to VM memory consumption and rate values. We will describe each briefly:

* `Promotion Rate` - the rate \(MB/second\) at which objects gets promoted from Young to Tenured space
* `Allocation Rate` - the rate \(MB/second\) at which new objects are being created
* `Young Generation Used Before GC` - the size of Young generation before garbage collection happens \(Eden + Survivor spaces\)
* `Young Generation Used After GC` - the size of Young generation after garbage collections. Typically, it's the size of Survivor space.
* `Young Total Size` - total size of Young generation.

* `Tenured Used` - the size of allocated memory in the Tenured space at each point of time.

* `Tenured Total Size` - the total Tenured space size at each point of time. Can differ when Adaptive Policy is enabled.

* `Heap Used Before GC` - total Heap occupation before any garbage collection event.

* `Heap Used After GC` - Heap occupation after each garbage collection.

* `Heap Total Size`

If any graphs are missing, it means we don't have enough data from raw logs to show it.

#### Tenuring Stats

Tenuring Stats shows the distribution of Survivor Space ages by an average Occupied mount of memory, as well as Total and Desired Survivor Size. GCPlot will also analyze it deeply and give some possible improvement suggestions based on it.

This info will be available only if `-XX:+PrintTenuringDistribution` flag was set on target VM. The example:

![](/assets/Screen Shot 2017-04-15 at 2.43.02 PM.png)

#### Generations

This is where the most detailed stats & info about each GC Generation falls. There are tables with total, occupied sizes by Generation, as well as STW pauses graphs, and, finally, the numerous statistical info, like Total, Min/Max, Average pause times, average interval between events and so on.

One note should be done here. Consider next table:

| Generation | Average | Min | Max |
| :--- | :--- | :--- | :--- |
| Young | `1.995 GB` | `25.255 MB` | `2.197 GB` |
| Tenured | `4.691 GB` | `2.132 GB` | `7.612 GB` |
| Heap | `6.672 GB` | `2.420 GB` | `9.643 GB` |

Each cell contains **average/min/max observed** value for the given generation. So, the rule like Young+Tenured=Heap may not work here.

For example: at one point of time we observed min Young as `5mb`, and in another time Tenured min was `10mb`. At third time we noticed Heap min size as `15mb`. At first glance, all three events were at the same time! But if `-XX:+UseAdaptiveSizePolicy` was enabled, all the magic ruins. When Young was just `5mb`, the Tenured easily might be `1gb`. So, please be accurate in your analysis and estimation.

#### Phases & Causes





