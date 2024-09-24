# Running and Terminating GenomeSuite Analyzer

To run GenomeSuite Analyzer on the EC2 instance, follow these steps:

## Navigate to the GenomeSuite Analyzer Directory

1. **Change to the Home Directory:**
   * Once logged in, you should already be in the `/home/ubuntu` directory. To confirm, run:
     ```
     cd /home/ubuntu
     ```
   * If you're already there, this command won't change anything.

2. **Navigate to the GenomeSuite Analyzer Distribution Directory:**
   * Run the following command to change into the GenomeSuite Analyzer distribution directory:
     ```
     cd Sniffles/dist
     ```

## Run GenomeSuite Analyzer

1. **Run GenomeSuite Analyzer with the Required Parameters:**
   * Execute GenomeSuite Analyzer by running the following command:
     ```
     ./sniffles -b bucketname -s samplename
     ```
   * Replace `bucketname` with the name of the S3 bucket where your POD5 files are stored.
   * Replace `samplename` with an arbitrary name of your choice for the sample being processed.

**Example Command:**
If your S3 bucket is named `sniffles-sample` and your sample name is `sample1`, the command would look like this:
```
./sniffles -b sniffles-sample -s sample1
```

## Monitor GenomeSuite Analyzer Output

* GenomeSuite Analyzer will start processing the data. You should see output in the terminal indicating the progress of the operation. Depending on the size of the dataset, this may take some time.

## Create a New AMI

This is a **one-time** step.

When the GenomeSuite Analyzer job is done, and before terminating the running EC2 instance, it is VERY IMPORTANT that you create a new AMI. By creating a new AMI you will save all your configuration settings from above. You can then use this new AMI for all future runs. 

To create a new AMI from a running EC2 instance using the EC2 console, follow these steps:

### Step 1: Access the EC2 Console

1. **Navigate to the EC2 Dashboard:**
   * In the AWS Management Console, type "EC2" in the search bar and select "EC2" from the drop-down menu.

2. **Access the Instances Section:**
   * In the EC2 Dashboard, click on "Instances" in the left-hand menu under the "Instances" section. This will display a list of all running EC2 instances.

### Step 2: Create an AMI from the Running Instance

1. **Select the Instance:**
   * Locate the running instance from which you want to create an AMI. Click the checkbox next to the instance to select it.

2. **Open the Instance Actions Menu:**
   * With the instance selected, click on the "Actions" drop-down menu at the top right of the page.

3. **Select Create Image:**
   * From the "Actions" drop-down menu, navigate to "Image and templates" and then select "Create image". This will open the Create Image dialog box.

4. **Configure the Image Settings:**
   * Image Name: Enter a name for your AMI in the "Image name" field.
   * Image Description (optional): You can provide a description of the AMI for future reference.

5. **Create the Image:**
   * Once you have configured all the settings, click on the "Create image" button at the bottom of the dialog box.

### Step 3: Monitor the AMI Creation Process

1. **View the Image Creation Progress:**
   * AWS will start creating the AMI. To monitor its progress, click on "AMIs" in the left-hand menu under the "Images" section.
   * You will see your new AMI listed with a status of "pending". Once the status changes to "available", the AMI is ready to use.

## Terminate GenomeSuite Analyzer EC2 Instance

When the GenomeSuite Analyzer job is finished, it's very important that you terminate the running GenomeSuite Analyzer EC2 instance. You do not want to accumulate unnecessary charges by letting the instance continue running.

To terminate an EC2 instance, follow these steps:

### Step 1: Access the EC2 Dashboard

1. **Navigate to the Instances Section:**
   * On the EC2 Dashboard, in the left-hand menu, click on "Instances" under the "Instances" section.

### Step 2: Select the Instance to Terminate

1. **Find the Instance:**
   * Locate the instance you want to terminate. You can use the search bar at the top to filter instances by name, instance ID, or other attributes.

2. **Select the Instance:**
   * Click the checkbox next to the instance you want to terminate to select it.

### Step 3: Terminate the Instance

1. **Terminate the Instance:**
   * With the instance selected, click on the "Instance state" button at the top of the page.
   * From the dropdown menu, select "Terminate instance".

2. **Confirm the Termination:**
   * A confirmation dialog will appear asking if you're sure you want to terminate the instance. Confirm by clicking "Terminate".

3. **Monitor Termination Process:**
   * The instance will begin shutting down and its state will change to "shutting-down" and then to "terminated". Once terminated, the instance will no longer incur charges.