# Ways of Sending Data

GCPlot currently supports any sorts of Hotspot JVM of all stable versions. Typical GC log is a text-based file, which is being written distinctly from any other application log by JVM. At this moment GCPlot can consume them using the following three methods:

* [Manual Upload](#manual-upload)
* [GCPlot Connector](/log-files-processing.md)
* [API](#api)

You can choose the option that fits best for your purpose, or combine them. We will look in details at each of them.

#### Manual Upload

In order to manually upload the file, you need to click on a "Upload GC Log" item in the left sidebar.

After that, you will be offered to choose the log file and press the Upload button. The file upload & processing will start after that:

![](/assets/Screen Shot 2017-07-05 at 11.34.10 PM.png)

When everything will successfully complete, the page will be reloaded and the new report for this file will be available under **Files** analysis group.

#### **API**

There is also an option to upload files via API. After successful execution new file will be available under **Files** group.

**URL**: [https://gs.gcplot.com/gc/jvm/log/process?](https://gs.gcplot.com/gc/jvm/log/process)

**Method**: POST

**Content-Type**: multipart/form-data

**URL** **Parameters **\(should be inserted after `?` character in URL\):

| Name | Description | Example |
| :--- | :--- | :--- |
| token | Your personal unique token. You can find it in your [personal profile page](/gcplot-overview/you-profile.md). | token=cyot7yn74tcwotctwno4t |

 **Example**:

```bash
curl -v -include --form upload=@/path/to/gc.log https://gs.gcplot.com/gc/jvm/log/process?token=cyot7yn74tcwotctwno4t
```

 

