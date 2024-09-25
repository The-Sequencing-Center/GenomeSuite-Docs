# Getting started

GenomeSuite Analyzer runs on the [Amazon Web Services (AWS)](https://aws.amazon.com/) platform. If you do not have an AWS account, start with [Create an AWS Account](#create-an-aws-account). If you do have an AWS account, you can skip to the step [Log into Your AWS Account](#log-into-your-aws-account).

Some steps are identified as a “**one-time step**”.  This means you should only have to perform this step once during initial setup.

GenomeSuite Analyzer can process POD5, FAST5 or BAM files. You will have to choose one filetype for each run.

## Create an AWS account

This is a **one-time** step.

To create an AWS account:

1. Open the [AWS account creation](https://aws.amazon.com/resources/create-account/) page and **Create an AWS Account**.

1. Fill in the details and click **Verify email address**. You will receive an email with a verification code that you need to enter on the sign up page.

1. Set up your root user password and confirm it.

1. Choose between a Personal or Professional account. The features and functions are the same, but the information required might differ slightly.

1. Fill in your contact information and read the AWS Customer Agreement. Once done, click **Continue**.

1. Provide a valid payment method (credit/debit card). This step is mandatory even if you plan to use the free tier services. You may also need to verify your payment method by entering a code sent by AWS.

1. AWS will ask you to provide a phone number to verify your identity. You will receive a call or SMS with a verification code that you need to enter to proceed.

1. Select one of the available support plans (Basic, Developer, Business, or Enterprise). The Basic support plan is free.

   - After selecting your support plan, AWS will begin activating your account. This process usually takes a few minutes but can take up to 24 hours. Once activation is complete, you will receive a confirmation email.

After your account is activated, you can sign in to the [AWS Management Console](https://aws.amazon.com/console/) and start using AWS services.

## Log into your AWS account

To log in to your AWS account, follow these steps:

1. Open your web browser and go to the [AWS Management Console](https://aws.amazon.com/console/) login page.

1. On the login page, you will see two options:
   - **Root user:** Use this if you are logging in as the account owner or the main administrator.
      - If you are the root user, click **Root user** and enter your email address associated with the AWS account. Click **Next**.
   - **IAM user:** Use this if you have been assigned a user account within an AWS organization.
      - If you are an IAM user, click **IAM user** and enter your IAM username along with the account ID or alias. Click **Next**.

1. Enter the password for your account, and click **Sign In**.

   - If Multi-Factor Authentication (MFA) is enabled for your account, you will be prompted to enter the code from your authentication device, such as a mobile app. Enter the code and proceed.

1. After successful authentication, you will be directed to the AWS Management Console, where you can start managing your AWS services.

## Create an S3 bucket

This is a **one-time** step.

You will now create an AWS S3 bucket that will contain all of your Nanopore POD5 sample files. 

To create an S3 bucket in your AWS account:

1. From the [AWS Management Console](https://aws.amazon.com/console/), type **S3** into the search bar at the top and select **S3** from the drop-down list. This takes you to the Amazon S3 dashboard.

1. On the S3 dashboard, click the **Create bucket** button.

1. To configure the bucket settings, enter a name for the bucket in the **Bucket** name field.
   - **Bucket name:** Bucket names must be globally unique across all existing bucket names in Amazon S3. 
      - If you choose a name that is already taken, you'll have to try other names until you find a unique name.
      - The name must not contain spaces and must adhere to the bucket naming rules (e.g., lowercase letters, numbers, and hyphens).
   - **Region:** Select the region **US East (N. Virginia) us-east-1**. This is the region where the S3 bucket will be created.

1. Set the bucket options.
   - **Block Public Access Settings:** By default, S3 buckets are set to block all public access. You can leave this option enabled unless you specifically need the bucket to be public.

   - **Bucket Versioning:** To enable versioning, which keeps multiple versions of an object in the same bucket, you may optionally choose to enable this in **Bucket Versioning**.

   - **Tags, Object Lock, and Encryption:** You may also enable additional optional settings such as adding tags, enabling object lock, and set default encryption, but these are not necessary can be configured later.

1. Review your bucket settings configuration and click **Create bucket**.

1. After the bucket is created, you are taken back to the S3 dashboard, where you will see the bucket name listed among your S3 buckets. Verify that the bucket was created successfully.

## Upload POD5 files to an S3 bucket

There are several methods available for uploading POD5 files to S3 buckets. These methods are beyond the scope of this document. For human whole genome sequencing, the aggregate size of these files is quite large, ca. 1TB or more, and may need special methods to upload in reasonable time. 

Please contact us at [support@thesequencingcenter.com](mailto:support@thesequencingcenter.com) to review and discuss options for uploading large datasets.

## Store POD5 files in S3 bucket

If you already have an AWS account and an S3 bucket with POD5 files in it, you have two choices. You can use the existing bucket name with GenomeSuite Analyzer or you can copy or move the files from the existing bucket to another bucket within the same AWS account. 

To copy or move files, follow these instructions:

1. In the S3 dashboard, click on the bucket that contains the POD5, FAST5 or BAM files you want to copy or move.

1. Browse the folders in your source bucket and select the files you want to copy or move.
   - You can select multiple files by holding the **Ctrl** key (or **Cmd** on Mac) while clicking.

1. After selecting the files, click the **Actions** button at the top of the screen, and choose either **Copy** or **Move**.
   - A dialog box appears asking where you want to copy or move the files.

1. In the **Destination** field, click **Browse S3** and navigate to the destination bucket. Specify the exact location within the bucket by selecting a folder or leave it blank to place the files directly in the bucket's root.

1. Once the destination is set, click **Copy** or **Move**. Depending on the size and number of files, this may take a few moments.

1. Navigate to the destination bucket and verify that the files have been successfully copied or moved.

## Create a key pair

This is a one-time step.

To create a key pair in AWS, follow these steps:

1. In the AWS Management Console, type **EC2** in the search bar and select **EC2** from the drop-down menu.

1. In the EC2 Dashboard in the left-hand side menu, click on the **Key Pairs** option under the **Network & Security** section.

1. Click the **Create Key Pair** button.

1. Configure the key pair settings:
   - **Name:** Enter a name for your key pair, such as `GenomeSuite-Analyzer-keypair`. The name must be unique within your AWS region.
   - **Key Pair Type:** Choose the key pair type, typically **ED25519**.
   - **Private Key File Format:** Choose the format for the private key file. Options include:
     - **.pem:** For SSH clients (like OpenSSH) on Linux or macOS.
     - **.ppk:** For PuTTY, a popular SSH client on Windows.
   - **Tags:** (Optional) You can add tags to your key pair for easier management.

1. Click **Create key pair**. AWS will generate the key pair and automatically download the private key file to your computer.

## Secure the private key

1. Save the private key.
   - The private key file will automatically download to your computer. This file is crucial for connecting to your EC2 instances securely, so store it in a safe location. If you lose this file, you will not be able to connect to your instances using this key pair.

1. To set the correct key pair permissions on a Linux or macOS system, run the following command:

   ```
   chmod 400 /path/to/your-keypair.pem
   ```

1. Store the private key in a secure location. Do not share it with anyone or commit it to version control systems like Git.

**Important:**
- **One-time download:** The private key file can only be downloaded once at the time of creation. If you lose the private key, you will need to create a new key pair and update your instances to use the new key.

- **Accessing EC2 instances:** When launching a new EC2 instance, you will be able to select this key pair for SSH access. Ensure the correct permissions are set on your private key file before attempting to connect.

## Create a security group

This is a one-time step.

To create a security group in AWS for EC2 that allows SSH logins on port 22, follow these steps:

1. In the AWS Management Console, type **EC2** in the search bar and select **EC2** from the drop-down menu.

1. From the left-hand menu in the EC2 Dashboard, click the **Security Groups** option under the **Network & Security**.

1. Click the **Create security group** button to create and configure a new security group.
   - **Name:** Enter a name for your security group, such as **GenomeSuite-Analyzer-sg**.
   - **Description:** Provide a brief description of the security group, like "Security group for SSH access to EC2 instances".
   - **VPC:** Choose the appropriate VPC (Virtual Private Cloud) where you want this security group to be used. If you only have one VPC, it will be selected by default.

1. To configure the inbound rules for SSH access, click **Add Rule** from the **Inbound rules** section.
   - **Type:** From the drop-down list, select **SSH**. This will automatically set the **Port Range** to 22.
   - **Source:** You can choose **My IP** to allow SSH access only from your current IP address.
     - Alternatively, select **Anywhere** (0.0.0.0/0) to allow SSH access from any IP address, but note that this is less secure and should be used with caution.
     - You can also specify a custom IP range if you only want to allow SSH access from specific IP addresses or ranges.

1. Review the rules you added to ensure they match your requirements. Once satisfied with the configuration, click **Create security group**.

1. Attach the security group to an EC2 instance.

   - **During EC2 Instance Launch:** When launching a new EC2 instance, you can select this security group under the **Configure Security Group** section.

   - **For Existing Instances:** If you want to assign this security group to an existing instance, go to the **Instances** section, select your instance, click **Actions** > **Networking** > **Change Security Groups**, and then select the **analyzer-sg** security group.

**Important**
- **Security Considerations:** Allowing SSH access from any IP address (0.0.0.0/0) is convenient, but can expose your instance to potential attacks. It is recommended to restrict access to specific IP addresses whenever possible.

- **Firewall Settings:** Ensure that any local firewalls on your machine or network allow outbound connections on port 22.