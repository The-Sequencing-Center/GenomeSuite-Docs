# Launch GenomeSuite Analyzer on EC2

To launch the GenomeSuite Analyzer AMI (Amazon Machine Image) using EC2:

## Select an EC2 region

1. Navigate to the EC2 Dashboard and confirm you are in the correct region. 

1. In the top-right corner of the EC2 Dashboard, click on the **Region** selector drop-down.

1. Select one of the four regions from the list of regions GenomeSuite Analyzer is available in four AWS regions.
    - US East (N. Virginia) us-east-1   
    - US East (Ohio) us-east-2  
    - US West (Oregon) us-west-2   
    - Canada (Central) ca-central-1  

## Launch the GenomeSuite Analyzer AMI

1. In the left-hand menu under **Images**, click on **AMIs**.

1. At the top of the AMIs page, click **Owned by me** and choose **Public images** from the drop-down list.

1. In the search bar, type **GenomeSuite_Analyzer_v.1.3.0** and press Enter.

1. From the results, select the checkbox next to the **GenomeSuite_Analyzer_v.1.3.0** AMI to highlight the row.

1. With the AMI row selected, click on the **Launch instance from image** button at the top right of the page to launch the instance.

## Configure the instance

1. On the **Launch an Instance** page, enter a name for your instance in the **Name** field.

1. Under **Instance Type**, select one of the following options:

    For human exome, use these instance types:

    - `p3.2xlarge`
    - `p3.8xlarge`
    - `p3.16xlarge`

    For human whole genome, use this instance type:

    - `p4d.24xlarge`

    These instance types are optimized for high-performance computing tasks using Nvidia GPU's.

1. Under **Key Pair (login)**, select the key pair you created earlier (e.g., `GenomeSuite-Analyzer-keypair`).

1. Under **Network Settings** > **Edit**, choose **Select existing security group** and select the security group you created earlier (e.g., `GenomeSuite-Analyzer-sg`).

1. Under **Configure Storage**, set the storage size to **2048 GiB**. Ensure the storage type is set to **gp3** (General Purpose SSD).

## Launch the instance

1. Review the configurations to ensure everything is set correctly.

1. Click the **Launch Instance** button at the bottom of the page.

    - If you get an error message `Insufficient Capacity`, this means all of the available computing resources are in use.

1. At this point, you have two options:

    1. Wait a few minutes and try to launch the instance again.  
    1. Choose a different region and try to launch the instance again.

    Typically, there are computing resources available in one of the regions. 

1. Once launched, you will be taken to a page showing the status of your instance. The instance will take a few minutes to initialize.

1. After the instance is running, you can find it under **Instances** in the EC2 Dashboard. Make sure the instance status is **Running** before attempting to connect.