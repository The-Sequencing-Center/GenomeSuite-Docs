# How to get your AWS Access Key ID and AWS Secret Access Key

## For new users

1. Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and navigate to the **IAM (Identity and Access Management) Console**.

1. To create a New IAM User:
    1. In the IAM Dashboard, click **Users** in the left-hand menu.
    1. Click **Add user**.
    1. Provide a username and check the **Programmatic access** checkbox to generate an access key.
    1. Click **Next: Permissions** to assign appropriate permissions, either directly or by attaching a policy (e.g., AmazonS3FullAccess if you need S3 access).
    1. Follow the remaining prompts and then click **Create user**. You will see a page with the Access Key ID and Secret Access Key. 

1. Download the credentials as a `.csv` file or view them directly on the page.

    **Important:** This is the only time you'll be able to view the Secret Access Key, so make sure to store it securely.

## For existing users

1. Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and navigate to the **IAM Console**.

1. In the IAM Dashboard, click **Users** in the left-hand menu.

1. Click on your username to access the details.

1. Create a New Access Key (if none exists or if you need a new one):
    1. Go to the **Security credentials** tab.
    1. Scroll down to the **Access keys** section.
    1. Click on **Create access key**. AWS will generate a new Access Key ID and Secret Access Key for you.

1. Download the credentials as a `.csv `file or view them directly on the page. Ensure it is stored securely.

1. Verify your configuration by listing the S3 buckets or EC2 instances:

     ```
     aws s3 ls
     ```
     or
     ```
     aws ec2 describe-instances
     ```
    If configured correctly, this returns a list of your S3 buckets or EC2 instances.