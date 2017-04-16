# Data Source Configuration

When you create a new [Analysis Group](/gcplot-overview/analyze-groups.md) and wish [JVMs](/gcplot-overview/analyze-groups.md#jvms) inside it to start receiving GC logs from your servers, you should first decide from which Data Source they will be coming. At this moment there are two possible options: **GCPlot Default** and **External S3 Storage**:

![](/assets/Screen Shot 2017-04-16 at 6.08.22 PM.png)

#### GCPlot Default

This is the easiest option, which normally should be your default choice. If you select it, [gcpc](/log-files-processing/connector-installation-and-configuration.md) will be uploading logs into our internal storage and delete them from it after it will analyze them. All connections are SSL-secured.

No additional configuration is required here.

#### External S3 Storage

This is an option for GCPlot to take JVM GC log files from external S3 storage, which is owned by you. The configuration looks like this:![](/assets/Screen Shot 2017-04-16 at 6.22.27 PM.png)

* `Bucket Name` - the name of the bucket in S3
* `Access Key` and `Secret Key` - this keys are typically generated in AWS console for the new user. Read [this article](https://aws.amazon.com/blogs/security/wheres-my-secret-access-key/) for more information about it.
* `Region` - the Amazon region where your bucket is located.
* `Path Prefix` - the path to the root folder where log files will reside.

And that's it! If properly configured, [gcpc](/log-files-processing/connector-installation-and-configuration.md) will start uploading GC log files into your own S3 storage.



