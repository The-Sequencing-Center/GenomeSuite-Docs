# Configure the EC2 instance

There are a couple ways to configure and connect to an EC2 instance depending on your operating system. Follow the applicable instructions below.


## Option 1: Install and configure the AWS CLI on Mac

This is a *one-time step*.

To connect to your EC2 instance using a Mac Terminal, you will first need to install the AWS CLI and then configure it. 

### Install the AWS CLI on Mac

1. On your Mac, open the **Terminal** application. This should be located in the **Applications** directory. 

1. Homebrew is a package manager for macOS that simplifies the installation of software. If you do not have Homebrew installed, run the following command in Terminal and follow the on-screen instructions:

     ```
     /bin/bash -c **$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)**
     ```

1. Once Homebrew is installed, install the AWS CLI by running the following command:

     ```
     brew install awscli
     ```

1. Verify that the AWS CLI is installed correctly by running the following command:

     ```
     aws --version
     ```
    You should see output showing the installed version of the AWS CLI.

### Configure the AWS CLI on Mac

1. In Terminal, configure the AWS CLI by running the following command:

     ```
     aws configure
     ```

1. When prompted, enter the following AWS credential information:
    - **AWS Access Key ID:** Enter your [AWS Access Key ID](#how-to-get-your-aws-access-key-id-and-aws-secret-access-key).
    - **AWS Secret Access Key:** Enter your [AWS Secret Access Key](#how-to-get-your-aws-access-key-id-and-aws-secret-access-key).
    - **Default region name:** Enter your preferred region (for example, `us-east-1`).
    - **Default output format:** Enter **None**.


## Option 2: Install and configure the AWS CLI on Windows

This is a *one-time step*.

To configure the AWS CLI on a Windows machine and connect to an EC2 instance, follow these steps:

### Install AWS CLI on Windows

1. Open PowerShell or Command Prompt by searching for it in the **Start** menu.

1. Download and run the .msi [AWS CLI installer for Windows](https://awscli.amazonaws.com/AWSCLIV2.msi).
    - Follow the on-screen instructions to complete the installation. The installer will automatically install the AWS CLI to your system.

4. In PowerShell or Command Prompt, verify that the AWS CLI is installed correctly by running the following command :

     ```
     aws --version
     ```

    You should see output showing the installed version of the AWS CLI, confirming that it is ready to use.

### Configure the AWS CLI on Windows

1. In PowerShell or Command Prompt, configure the AWS CLI by running the following command:

     ```
     aws configure
     ```

1. When prompted, enter the following AWS credential information:
    - **AWS Access Key ID:** Enter your [AWS Access Key ID](analyzer-how-to-get-aws-keys.md).
    - **AWS Secret Access Key:** Enter your [AWS Secret Access Key](analyzer-how-to-get-aws-keys.md).
    - **Default region name:** Enter your preferred region (for example, us-east-1).
    - **Default output format:** Enter **None**.

## Optional steps

### Set environment variables

If you want to make sure the AWS CLI is accessible from any directory, ensure that the installation path is included in your system's environment variables. This is typically done automatically by the installer.

### Connect to EC2 instance using SSH

To connect to your EC2 instance using SSH from Windows, you can use PuTTY or the Windows Subsystem for Linux (WSL) with an SSH client. Ensure that you have your `.pem` key file and that it is converted to `.ppk` if using PuTTY.