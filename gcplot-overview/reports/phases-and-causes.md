# Phases & Causes

The next tab is "Phases & Causes" is responsible for showing all the possible reasons why GC was actually started \(since every garbage collections has actually a good reason to start\). This is called GC Causes. We had already written [a very comprehensive article](https://blog.gcplot.com/2017/01/19/java-gc-causes-distilled/) about it; after that it would be obvious what are the actual reasons behind each collection. 

Please note that your log files might lack info about GC Causes. In that case you will see a blank graph. This is the example of how it might look like:

![](/assets/Screen Shot 2017-04-15 at 8.39.43 PM.png)

Phases relates only to the **concurrent** garbage collectors \(CMS, G1\). They are typically a part of some big action - Old Generation GC. We provide an extremely detailed report about all of them as well as we do for each Generation. This is a typical analysis of Hotspot CMS garbage collector:

![](/assets/Screen Shot 2017-04-15 at 8.43.22 PM.png)

Please note that **Duration** here is a time when the given phase was running concurrently with the application threads. That said, Phases are not related to STW events completely. 

