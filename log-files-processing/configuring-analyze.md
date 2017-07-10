# Data Source Configuration

When you create a new [Analysis Group](/gcplot-overview/analyze-groups.md) and want [JVMs](/gcplot-overview/analyze-groups.md#jvms) inside it to start receiving GC logs from your servers, you should first decide from which Data Source they will be coming. At this moment there are two possible options: **GCPlot Default** and **External S3 Storage**:

![](/assets/Screen Shot 2017-04-16 at 6.08.22 PM.png)

### GCPlot Default

This is the easiest option, which normally should be your default choice. If you select it, [gcpc](/log-files-processing/connector-installation-and-configuration.md) agent will be uploading logs into our internal storage and delete them from there after it analyzes them. All connections are SSL-secured.

No additional configuration is required.

### External S3 Storage {#external-s3-storage}

This is an option for GCPlot to take JVM GC log files from external S3 storage, which is owned by you. The configuration page looks like this:![](/assets/Screen Shot 2017-04-16 at 6.22.27 PM.png)

* `Bucket Name` - the name of the bucket in S3
* `Access Key` and `Secret Key` - this keys are typically generated in AWS console for the new user. Read [this article](https://aws.amazon.com/blogs/security/wheres-my-secret-access-key/) for more information about it.
* `Region` - the Amazon region where your bucket is located.
* `Path Prefix` - the path to the root folder where log files will reside.

If properly configured, [gcpc](/log-files-processing/connector-installation-and-configuration.md) will upload all your GC log files into this S3 storage, and GCPlot Platform will then be taking them from here as well.

#### Important!

  
If you wish to use your own S3 storage, the next operations must be available to GCPlot and gcpc: **PUT** and **DELETE**.  
If you worry about security, the best option is to create a new dedicated user in AWS and jail it into some S3 folder with only **PUT** and **DELETE** access rights. Like this:

```
{
   "Version":"2012-10-17",
   "Statement":[
      {
         "Sid":"Stmt1488701886000",
         "Effect":"Allow",
         "Action":[
            "s3:PutObject",
            "s3:DeleteObject"
         ],
         "Resource":[
            "arn:aws:s3:::mybucket/gcplot-logs/*"
         ]
      }
   ]
}
```

  
That way, when you will configure Data Source, `mybucket` will be a Bucket Name and `gcplot-logs/` will be the Path Prefix.  
In that case, GCPlot wouldn't has an access to any other resources in the bucket. Such case is also described in our example page with all screenshots.**  
  
  
**

  




