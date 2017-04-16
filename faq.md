# FAQ

Q: **What JVMs does your analyzer support?**

A: Currently, we support all stable versions of the Hotspot JVM. We are also planning to start supporting Java 9 new log format very soon.

---

Q: **Is GCPlot free to use?**

A: Yes, cloud platform at the moment is in _beta_ stage and completely free. If you want to have a private installation of it in your company, contact us at [sales@gcplot.com](mailto:sales@gcplot.com).

---

Q: **How to tell my JVM to start producing GC logs?**

A: Here are recommended parameters for the most detailed report:

`-XX:+PrintGCDetails -XX:+PrintTenuringDistribution -XX:+PrintGCTimeStamps -XX:+PrintGCDateStamps -Xloggc:/path/to/file`

---

Q: **Is it secure to use GCPlot?**

A: Absolutely. We use SSL connections **everywhere**, encrypted databases, making sure no single bit of your private information being transmitted openly.

---

Q: **I believe that report you generate isn't correct. What should I do?**

A: You should contact us directly by [support@gcplot.com](mailto:support@gcplot.com) or use [Google Forum](https://groups.google.com/forum/#!forum/gcplot). We will make sure that any bug will be fixed.

---

Q: **Can I select a particular interval while building the report?**

A: Of course. You can set the interval to the exact second, while the width of the interval can be started from the minute.

---

Q: **Which timezone is used for the reports?**

A: All reports are in the timezone of the parent Analysis Group, which can be configured at the creation time, or modified anytime later. On the server side we store everything in UTC.

---

Q: **Can I copy data from GCPlot and use it in other places?**

A: Yes. Just make sure you add "Generated with GCPlot" text below any screenshot or any other form of information copied from GCPlot.

