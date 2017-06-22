# Memory

This tab shows a lot of graphs related to VM memory consumption and rate values. We will describe each briefly:

* `Promotion Rate` - the rate \(MB/second\) at which objects gets promoted from Young to Tenured space
* `Allocation Rate` - the rate \(MB/second\) at which new objects are being created
* `Young Generation Used Before GC` - the size of Young generation before garbage collection happens \(Eden + Survivor spaces\)
* `Young Generation Used After GC` - the size of Young generation after garbage collections. Typically, it's the size of Survivor space.
* `Young Total Size` - total size of Young generation.

* `Tenured Used` - the size of allocated memory in the Tenured space at each point of time.

* `Tenured Total Size` - the total Tenured space size at each point of time. Can differ when Adaptive Policy is enabled.

* `Heap Used Before GC` - total Heap occupation before any minor GC event.

* `Heap Used After GC` - Heap occupation after each minor GC.

* `Heap Total Size` - Total heap size.

If any graphs are missing, it means we don't have enough data from raw logs to render it.

