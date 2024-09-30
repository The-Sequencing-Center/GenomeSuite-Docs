# Run GenomeSuite Analyzer

To run GenomeSuite Analyzer on the EC2 instance, follow these steps:

1. When you are logged into your EC2 instance with your AWS credentials, you should already be in the `/home/ubuntu` directory. Confirm this by running the following command:

     ```
     cd /home/ubuntu
     ```
   If you are already there, this command won't change anything.

1. Change into the GenomeSuite Analyzer distribution directory by running the following command:

     ```
     cd analyzer/dist
     ```

1. Start GenomeSuite Analyzer by running the following command:

    ```
    ./analyzer -b bucketname -s samplename -f filetype -m modelname
    ```
    
    - Replace `bucketname` with the name of the S3 bucket where your POD5, FAST5 or BAM files are stored.
    - Replace `samplename` with an arbitrary name of your choice for the sample being processed.
    - Replace `filetype` with `pod5`, `fast5` or `bam`. This parameter specifies the file format of the sample files. All sample files must be the same filet
    - Replace `modelname` with a dorado basecaller model name.

    GenomeSuite Analyzer will start processing the data. You should see output in the terminal indicating the progress of the operation. Depending on the size of the dataset, this may take some time.

## Example commands

Use the following command to show help:

```
./analyzer --help
```

If your S3 bucket is named GenomeSuite-Analyzer-sample, and you are using POD5 files, the command would look like this:

```
./analyzer -b GenomeSuite-Analyzer-sample -s sample1 -f pod5
```

If your S3 bucket is named GenomeSuite-Analyzer-sample, and you are using FAST55 files, the command would look like this:

```
./analyzer -b GenomeSuite-Analyzer-sample -s sample1 -f fast5
```

If your S3 bucket is named GenomeSuite-Analyzer-sample, and you are processing a BAM file, the command would look like this:

```
./analyzer -b GenomeSuite-Analyzer-sample -s sample1 -f bam
```

If you want to see a list of available Nanopore Dorado basecalling models:

```
./analyzer -m
```

## Create a New AMI

This is a *one-time step*.

When the GenomeSuite Analyzer job is done, and before terminating the running EC2 instance, it is **VERY IMPORTANT** that you create a new AMI. By creating a new AMI you will save all your configuration settings from above. You can then use this new AMI for all future runs. 

To create a new AMI from a running EC2 instance using the EC2 console, follow these steps:

1. In the AWS Management Console, type **EC2** in the search bar and select **EC2** from the drop-down menu.

1. In the EC2 Dashboard, click on **Instances** in the left-hand menu under the **Instances** section. This displays a list of all running EC2 instances.

1. Find the running instance from which you want to create an AMI. 

1. Click the checkbox next to the instance to select it.

1. With the instance selected, click on the **Actions** drop-down menu at the top right of the page.

1. From the **Actions** drop-down menu, navigate to **Image and templates** and then select **Create image**. This opens the **Create Image** dialog box.

1. Configure the image settings.

    - **Image Name:** Enter a name for your AMI in the **Image name** field.
    - **Image Description (optional):** You can provide a description of the AMI for future reference.

1. Once you have configured all the settings, click on the **Create image** button at the bottom of the dialog box. AWS will start creating the AMI. 

1. To monitor its progress, click on **AMIs** in the left-hand menu under the **Images** section.

    - You will see your new AMI listed with a status of **Pending**. Once the status changes to **Available**, the AMI is ready to use.

## Terminate the EC2 instance

When the GenomeSuite Analyzer job is finished, it is very important that you terminate the running GenomeSuite Analyzer EC2 instance. You do not want to accumulate unnecessary charges by letting the instance continue running.

To terminate an EC2 instance, follow these steps:

1. On the EC2 Dashboard, in the left-hand menu, click on **Instances** under the **Instances** section.

1. Find the instance you want to terminate. You can use the search bar at the top to filter instances by name, instance ID, or other attributes.

1. Click the checkbox next to the instance you want to terminate to select it.

1. With the instance selected, click on the **Instance state** button at the top of the page.

1. From the dropdown menu, select **Terminate instance**. A confirmation dialog will appear asking if you are sure you want to terminate the instance. 

1. Click **Terminate** to confirm.

    - The instance will begin shutting down and its state will change to **shutting-down** and then to **terminated**. Once terminated, the instance will no longer incur charges.