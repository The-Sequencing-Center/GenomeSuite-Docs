# Configure AWS Credentials

This is a one-time step.

After logging into the EC2 instance, you must configure your AWS credentials by following these steps:

1. Ensure you are [connected the EC2 instance](/docs/analyzer-connect.md) using SSH as previously explained.

1. In your EC2 instance, configure the AWS CLI by running the following command:

     ```
     aws configure
     ```

2. **Enter Your AWS Credentials:**
   * The CLI will prompt you to enter the following information:
     - AWS Access Key ID: Enter your AWS Access Key ID (see below).
     - AWS Secret Access Key: Enter your AWS Secret Access Key (see below).
     - Default region name: Enter the region where your S3 bucket is located (e.g., us-east-1).
     - Default output format: Enter None.

1. When prompted, enter the following AWS credential information:
    - **AWS Access Key ID:** Enter your [AWS Access Key ID](analyzer-how-to-get-aws-keys.md).
    - **AWS Secret Access Key:** Enter your [AWS Secret Access Key](analyzer-how-to-get-aws-keys.md).
    - **Default region name:** Enter your preferred region (for example, us-east-1).
    - **Default output format:** Enter **None**.

**Important Note:**
By configuring your AWS credentials directly on the EC2 instance, you enable the instance to interact with S3 buckets. This is essential for performing operations like uploading or downloading files from an S3 bucket.