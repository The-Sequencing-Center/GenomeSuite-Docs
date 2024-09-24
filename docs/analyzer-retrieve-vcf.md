# Retrieving the VCF File

GenomeSuite Analyzer will generate a **VCF** file and store it in your S3 bucket. To download the VCF file from the S3 bucket, follow these steps:

## Step 1: Sign in to the AWS Management Console

1. **Navigate to the AWS Console:**
   * Open your web browser and go to the AWS Management Console.
   * Sign in with your AWS account credentials.

## Step 2: Access the S3 Service

1. **Open the S3 Dashboard:**
   * In the AWS Management Console, type **S3** into the search bar and select **S3** from the dropdown list to navigate to the S3 service.

## Step 3: Locate the VCF File in the S3 Bucket

1. **Find the Bucket:**
   * In the S3 Dashboard, find and click on the bucket name where the VCF file is stored (e.g., `sniffles-sample`).

2. **Locate the VCF File:**
   * Search for the VCF file using the naming convention `sample_name.vcf.gz`, where `sample_name` is the name you provided in the `-s` parameter when running GenomeSuite Analyzer. For example, if the sample name was `sample1`, look for the file named `sample1.vcf.gz`.

## Step 4: Download the VCF File

1. **Select the File:**
   * Once you locate the `sample_name.vcf.gz` file, click on the checkbox next to the file name to select it.

2. **Download the File:**
   * With the file selected, click on the **Download** button. The file will begin downloading to your local machine.