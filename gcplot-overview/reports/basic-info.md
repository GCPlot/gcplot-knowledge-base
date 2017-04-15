#### Date & Time Range

This is the most powerful part of report. You can select the desirable interval of interest, be it a whole week or 3 seconds. The timezone is configured in the parent Analysis Group.

![](/assets/Screen Shot 2017-04-14 at 10.13.33 AM.png)

By default we load the whole day before the last event processed. Current limit is 3 months.

If Time Range check box is not selected, the whole day will be considered.

> #### Hint
>
> Note that we, of course, apply some sampling when showing you the graphs. But the algorithm for it is quite simple - the wider interval, the more sampled events. If you want to reduce the impact of sampling, just narrow down your date & time range on the interval of interest to you.

#### JVM ID



#### General Stats

General Stats page just shows brief info about the file/JVM - initial and last GC event dates, name, etc.

Also, sometimes GC log file contains info about JVM flags used to start your VM, server RAM/Swap memory status. We will also show everything here.

#### Objects

This is a quite tiny tab with a very general info with a memory load stats. There are basically for lines:

* `Promoted Total` - total amount of memory that was promoted from Young to Old Generation for the given interval.

* `Promotion Rate` - the speed of promotion in MB/Second.

* `Allocated Total` - the total amount of new objects that were allocated during application runtime for the given interval.

* `Allocation Rate` - the speed of the allocation in MB/Second.



