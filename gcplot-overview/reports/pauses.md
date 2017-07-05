# Pauses

This tab contains all the verbose stats & graphs about GC pauses - Young/Tenured/Full collections, split on STW \(Stop-The-World\) and Concurrent; percentiles and etc.

Percentiles shows the distribution of STW pauses by the percent of occurrence:

![](/assets/Screen Shot 2017-04-14 at 10.28.31 AM.png)

For example, line `99% | 117.416` means that 99% of STW events are under 117.416 milliseconds.

GCPlot can also calculate very useful average rates for the selected interval, like in the next example:

![](/assets/Screen Shot 2017-07-05 at 11.23.30 PM.png)

This means that for each minute the cumulative average STW pause is ~853 ms, which is produced by ~22 events. In other words, for each 60 seconds the application is fully stopped for  ~853 ms.

There are also four graphs:

* `Pause Durations (Stop-The-World only)` - GC pauses in milliseconds

* `Log(x) Pause Durations (Stop-The-World only)` - Log10\(x\) of GC pauses, which is very helpful for seeing distribution of low values

* `Concurrent Phase Durations (Non-STW)` - concurrent collections durations in milliseconds \(if available\)

* `Log(x) Concurrent Phase Durations (Non-STW)` - Log10\(x\) of concurrent durations \(if available\)

These are examples of such graphs built from some log file:

![](/assets/Screen Shot 2017-04-15 at 8.58.34 PM.png)![](/assets/Screen Shot 2017-04-15 at 8.59.00 PM.png)![](/assets/Screen Shot 2017-04-15 at 8.59.23 PM.png)![](/assets/Screen Shot 2017-04-15 at 8.59.41 PM.png)

And finally you can see how much time does STW and Concurrent collections took relatively to the time where application-only was running:

![](/assets/Screen Shot 2017-04-14 at 10.34.01 AM.png)

