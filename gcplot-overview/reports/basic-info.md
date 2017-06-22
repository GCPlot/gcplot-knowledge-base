#### Date & Time Range

In this panel, you can select the interval to build a report. There are two main options: you can select both the days interval \(left\) and the hour / minute / second interval \(right\). The dates and time will be in the timezone specified in the Analysis Group settings.

![](/assets/Screen Shot 2017-04-14 at 10.13.33 AM.png)

By default we load the whole current day. The max limit for date range is 3 months.

If Time Range check box is not selected, the 00:00:00-23:59:59 will be considered.

> #### Hint
>
> Note that we, of course, apply some sampling when showing you the graphs. But the algorithm for it is quite simple - the wider interval, the harder is sampling. If you want to reduce the impact of sampling, just narrow down your date & time range on the interval of interest to you.

#### General Stats

General Stats page just shows brief info about the file/JVM - initial and last GC event dates, name, etc.

Also, sometimes GC log file contains info about JVM flags used to start your VM, server RAM/Swap memory status. If it's available, we will show it.

#### Objects

This is a quite tiny tab with a very general info about memory load/usage. There are basically four rows here:

* `Promoted Total` - total amount of memory that was promoted from Young to Old Generation for the given interval.

* `Promotion Rate` - the speed of promotion in MB/Second.

* `Allocated Total` - the total amount of new objects that were allocated during application runtime for the given interval.

* `Allocation Rate` - the speed of the allocation in MB/Second.



