# Connect to GenomeSuite Analyzer on EC2

You can now access the GenomeSuite Analyzer instance that is running on AWS EC2. 

## Connect to your EC2 instance

1. Ensure you have the `.pem` key pair file that was created when you launched your EC2 instance.

1. Set the correct permissions for the key pair file by running the following command:

     ```
     chmod 400 /path/to/your-keypair.pem
     ```
    Replace `/path/to/your-keypair.pem` with the actual path to your `.pem` file.

1. Connect to your EC2 instance by running the following command in Terminal:

     ```
     ssh -i /path/to/your-keypair.pem ubuntu@your-instance-public-dns
     ```
    Replace `/path/to/your-keypair.pem` with the path to your .pem file and `your-instance-public-dns` with the Public DNS address of your EC2 instance. You can find the Public DNS in the AWS Management Console under the **Instances** section.

1. **Access your EC2 instance:**
   * Once connected, you will have shell access to your EC2 instance, allowing you to manage it as needed.

### Additional tips

**Using SSH config file:** If you frequently connect to the same instance, consider setting up an SSH config file to simplify the connection command.

**Security considerations:** Ensure your `.pem` file is kept secure, as it provides access to your EC2 instance.
