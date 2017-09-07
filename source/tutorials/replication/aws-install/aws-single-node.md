# Installing a Single-node Cluster on AWS

In this procedure, you set up a single node QF2 cluster on AWS. The procedure assumes you already have AWS account and understand basic AWS operations such as getting AWS keys, selecting an AMI, selecting an EC2 instance and setting up security groups. 

We recommend you use Chrome as your browser.

## Get the AMI
1. Go to AWS Marketplace and get the AMI.
2. Go to the EC2 Dashboard and select **AMI**s.

![EC2 dashboard - AMI images](images/aws-images-ami.png)

3. Select the appropriate AMI source, either **Owned by me**, **Public images** or **Private images**.

![AMI source selection](images/aws-ami-selection.png)

4. The **Resource Group** screen appears. Select the AMI image, named **Qumulo**.

![AMI selection](images/aws-ami-imagechoose.png)

5. Click **Launch** to begin provisioning the image.

![AMI launch](images/aws-ami-launch-1.png)

6. Choose an instance type, then scroll down and click **Review and Launch**. 

![AMI instance type](images/aws-ami-instancetype-launch.png)

## Set up the security group

1. Click **Edit security groups**.

![AMI Edit security groups](images/aws-ami-editsecuritygroups-1.png)

2. Configure or select the security group. If you have an existing configuration that keeps the following ports open, you can use that. If not, create a new security group. Here are the ports that should be open:

* Port 22 &ndash; SSH
* Port 111 &ndash; NFS port mapper
* Port 443 &ndash; HTTPS
* Port 2049 &ndash; NFS
* Port 3712 &ndash; QF2 replication to/from instance
* Port 8000 &ndash; GUI

3. Here is an example screenshot that uses an existing security group. 

![AMI Select an existing security group](images/aws-ami-selectexisting-sec-group-2.png)

4. Click **Review and Launch**.
5. The **Review Instance Launch Page** appears. Review the settings and, if you are satisfied, click **Launch**.

![AMI Launch](images/ami-reviewandlaunch.png)

## Launch the instance

1. Select an existing key pair or create a new pair of keys. You need these keys to SSH into the instance. Click **Launch instance**.

![AMI security key pair](images/ami-launch-seckeypair.png)

2. The instance begins to launch.

![AMI initiate launch](images/ami-initiateinstancelaunch.png)

3. In a few moments, you will see the *Launch Status** screen. 

![Launch status screen](images/aws-launch-status-1.png)

4. Click **View Instances**. A status screen appears.

![AWS status screen](images/aws-instance-status-1.png)

Initialization times vary and can take as long as 10 minutes. You may need to refresh your browser to get status updates.

5. Keep checking the status screen until the **Status Checks** column shows **2/2 checks...**

![AWS instance IP address and public DNS name](images/aws-address.png)

Once it does, Use your browser to access the instance. To see the IP address, select the instance and scroll down. 

## Configure the QF2 cluster

1. Enter the IP address or DNS name in the browser. You will see a Chrome privacy error.

![Chrome privacy error](images/chrome-privacyerror.png)

2. Click **ADVANCED**. Click **Proceed to *web site***.

3. The Qumulo EULA appears. Scroll to the bottom, select both boxes, then click **Submit**.

![EULA submit](images/chrome-eula-submit.png)

3. Name the cluster. 

![Name cluster](images/chrome-createcluster-name.png)

4. Scroll down and set the password for the admin account.

![Set admin password](images/chrome-adminpassword.png)

5. Click **Create Cluster**.

6. A dialog box appears and asks for verification. Click **Yes, Create Cluster**.

![Yes, create cluster](images/chrome-createcluster-verify.png)

7. The status messaage appears.

![Creating cluster](images/chrome-creatingcluster-dialog.png)

8. Once the cluster is created, the GUI appears.

![QF2 GUI](images/chrome-qumulo-gui.png)

9. The cluster is ready to serve data.










