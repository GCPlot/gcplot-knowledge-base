# Pauses

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

