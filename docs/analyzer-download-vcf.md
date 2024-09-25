# Download the VCF File

GenomeSuite Analyzer will generate a VCF file and store it in your S3 bucket. To download the VCF file from the S3 bucket, follow these steps:

1. Open your web browser and sign into the [AWS Management Console](https://aws.amazon.com/console/) with your AWS account credentials.

1. In the AWS Management Console, type **S3** into the search bar and select **S3** from the dropdown list to navigate to the S3 service.

1. In the S3 Dashboard, find and click on the bucket name where the VCF file is stored (e.g., `GenomeSuite-Analyzer-sample`).

2. **Locate the VCF File:**
   * Search for the VCF file using the naming convention `sample_name.vcf.gz`, where `sample_name` is the name you provided in the `-s` parameter when running GenomeSuite Analyzer. For example, if the sample name was `sample1`, look for the file named `sample1.vcf.gz`.

1. Once you find the `sample_name.vcf.gz` file, click on the checkbox next to the file name to select it.

2. With the file selected, the **Download** button. The file will begin downloading to your local machine.