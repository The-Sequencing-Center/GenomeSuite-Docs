# Launching GenomeSuite Analyzer on EC2

To launch the GenomeSuite Analyzer AMI (Amazon Machine Image) using EC2, follow these steps:

## Step 1: Start at the EC2 Dashboard

1. **Navigate to the EC2 Dashboard:**
   * Once on the EC2 Dashboard, confirm you are in the correct region.

## Step 2: Select a Region

    1. GenomeSuite Analyzer is available in four AWS regions:  
        * US East (N. Virginia) us-east-1   
        * US East (Ohio) us-east-2  
        * US West (Oregon) us-west-2   
        * Canada (Central) ca-central-1   
    2. Choose a Region:
        * In the top-right corner of the EC2 Dashboard, click on the region selector drop-down.  
        * Select one of the four regions from the list of regions.

## Step 3: Find the GenomeSuite Analyzer AMI

1. **Navigate to AMIs:**
   * In the left-hand menu under **Images**, click on **AMIs**.

2. **Filter for Public Images:**
   * At the top of the AMIs page, find the drop-down list labeled **Owned by me**. Click on it and choose **Public images**.

3. **Search for the GenomeSuite Analyzer AMI:**
   * In the search bar, type **Sniffles_v.1.1.0** and press Enter.

4. **Select the AMI:**
   * Find the AMI named **Sniffles_v.1.1.0** in the results.
   * Click the checkbox next to this AMI to highlight the row.

5. **Launch the Instance:**
   * With the AMI row selected, click on the **Launch instance from image** button at the top right of the page.

## Step 4: Configure the Instance

1. **Name the Instance:**
   * On the **Launch an Instance** page, provide a name for your instance in the **Name** field.

2. **Select the Instance Type:**
   * Under **Instance Type**, select one of the following options:

   `For human exome, use these instance types:`
   1. `p3.2xlarge`
   2. `p3.8xlarge`
   3. `p3.16xlarge`

   `For human whole genome, use this instance type:`
   1. `p4d.24xlarge`

   These instance types are optimized for high-performance computing tasks using Nvidia GPU's.

3. **Configure Key Pair:**
   * Under **Key Pair (login)**, select the key pair you created earlier (e.g., `**sniffles-keypair**`).

4. **Set Network Settings:**
   * Under **Network Settings**, select **Edit**.
   * Choose **Select existing security group** and select the security group you created earlier (e.g., `**sniffles-sg**`).

5. **Configure Storage:**
   * Under **Configure Storage**, set the storage size to **2048 GiB**.
   * Ensure the storage type is set to **gp3** (General Purpose SSD).

## Step 5: Launch the Instance

1. **Review the Settings:**
   * Double-check all configurations to ensure everything is set correctly.

2. **Launch the Instance:**
   * Click on the **Launch Instance** button at the bottom of the page.  
   * If you get an error message “Insufficient Capacity”, this means all of the available computing resources are in use.    

        At this point, you have two options:  
           
           1) Wait a few minutes and try to launch the instance again.  
           2) Choose a different Region and try to launch the instance again.
       
        Typically, there are computing resources available in one of the regions. 

3. **Instance Initialization:**
   * Once launched, you will be taken to a page showing the status of your instance. The instance will take a few minutes to initialize.

4. **Verify the Instance:**
   * After the instance is running, you can find it under **Instances** in the EC2 Dashboard. Make sure the instance status is **running** before attempting to connect.