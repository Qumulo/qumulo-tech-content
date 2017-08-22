---
url: create-virtual-cluster-vmware  
category: How To  
title: How to create a Qumulo virtual cluster in VMware  
meta-description: Meta description for SEO purposes. Format is TBD  
---
## Create a Virtual Cluster in VMware

### Requirements
- Make sure the minimum system requirements are satisfied for VMware for your hardware.
- For best performance, Qumulo recommends at least **8GB of RAM and an SSD** to host the virtual images.
- **Four (4)** instances of Qumulo Core are required to form a complete cluster.

#### Step 1: Launch the `.ova`
Start with the downloaded `.ova` file and double click on it to launch VMware. You will be prompted for a local storage path to save the virtual machine (if possible, save the virtual machine on an SSD device):

![Qumulo Virtual Cluster - Launch VM creation](images/initial_vmware_launch.png "Initial Qumulo VMWare image luanch screen in Windows")

#### Step 2: Create and configure instances of Qumulo Core
1. Next, a warning will present itself:
![Qumulo Virtual Cluster - OVF specification compliance check](images/vmware_relax_spec_1.png "Qumulo VMware intial warning")

1. It is safe to ignore this warning.
Click _Retry_ and provisioning will continue:
![Qumulo Virtual Cluster - Continue Provisioning](images/vmware_provisioning_continues.png "Continue Provisioning")

1. The virtual machine will now allow you to change the default settings:
![Qumulo Virtual Cluster - Change default settings](images/vmware_default_settings.png "Change default settings")

1. Choose the appropriate networking option:
![Qumulo Virtual Cluster Setup - Choose networking option](images/gui_menu_networkconfiguration.png "Choose networking option")

    - **NAT** will use the IP address of the machine that VMware is running on, and hide the internal IP addresses from your network.
    - **Bridged** will allow the virtual machines to present themselves as additional network interfaces. If your computer is assigned an address via DHCP, then the virtual machines will also automatically be assigned IP addresses.
    - This can be changed later, but will require restarting the virtual machines.

1. Launch additional instances from the same initial .ova file.  A total of **four (4)** instances are required to be deployed.  Follow the same steps for each instance.
![Qumulo Virtual Cluster Setup - Create node 2](images/launch_instance_2.png "Choose networking option")

1. Note how VMware has appended a (2) to the name for this image.
Again, click “Retry” and the instance will launch:
![Qumulo Virtual Cluster - OVF specification compliance check](images/vmware_relax_spec_2.png "Compliance check warning 2")

1. Repeat for instances #3 and #4:
![Qumulo Virtual Cluster - OVF specification compliance check](images/vmware_relax_spec_3.png "Compliance check warning 3")
![Qumulo Virtual Cluster - OVF specification compliance check](images/vmware_relax_spec_4.png "Compliance check warning 4")

1. Verify all four instances have been created:
![Qumulo Virtual Cluster - Verify four virtual node instances](images/four_instances.png "Verify four virtual node instances")

#### Step 3: Start the instances
1. Start one of the instances by selecting one listed under “My Computer” and then click “Power on this virtual machine”:
![Qumulo Virtual Cluster - OVF specification compliance check](images/vmware_relax_spec_2.png "Compliance check warning 2")

1. After a few seconds, the End User License Agreement (EULA) appears:
![Qumulo Virtual Cluster - EULA](images/vm_qumulo_eula.png "Qumulo EULA")

1. Scroll down within the VMware window, check both boxes and click “Submit” to accept the EULA:
![Qumulo Virtual Cluster](images/vm_qumulo_eula_submit.png "Qumulo EULA")

1. You should see the initial cluster config screen:
![Qumulo Virtual Cluster](images/initial_config_node1.png "Node 1")

1. Start the additional instances one at a time, waiting until the EULA appears **before** starting the next instance:
![Qumulo Virtual Cluster](images/launch_instance_2.png "Instance 2")

1. Once all 4 instances are running, select the first instance that you accepted the EULA on.  You should see 4 nodes available:
![Qumulo Virtual Cluster](images/initial_config_allnodes_ready.png "All nodes running")

#### Step 4: Configure the initial server
1. Begin configuring the initial server settings:
Name the cluster; in this example we have named our cluster _qumulo-VM_.

1. Next, scroll down to set the admin password.  This will be required to administer the cluster:
![Qumulo Virtual Cluster](images/initial_config_admin_password.png "Set admin password")

    Initially, the cluster nodes communicate with each other via IPv6. We will set the IP addresses if necessary after the cluster forms.

1. Once all the required fields are populated, click “Create cluster” to start the cluster up:
![Qumulo Virtual Cluster](images/initial_config_create_cluster.png "Create cluster")

1. An additional dialog will ask for verification. Click _Yes, Create Cluster_ to create the cluster:
![Qumulo Virtual Cluster](images/initial_config_create_cluster_verify.png "Verify create cluster")

1. You should see the cluster being created:
![Qumulo Virtual Cluster](images/initial_config_status_create_cluster.png "Create cluster status")

1. After a few seconds you should see the main cluster admin page:
![Qumulo Virtual Cluster](images/main_cluster_page.png "Main cluster page")

1. If DHCP is available, then the cluster will self-assign IP addresses. In this example, the first node has an IPv4 address of `10.0.0.12`. The cluster can now be accessed via a web browser (Chrome is recommended).

1. If DHCP is not available, static IP addresses will have to be assigned manually.
    1. Click on _Cluster_ and then _Network Configuration_:
    ![Qumulo Virtual Cluster](images/main_cluster_page.png "Main cluster page")

    1. Next, begin configuring the subnet mask, gateway, DNS servers, and Search Domains, and if applicable, change the MTU size:
    ![Qumulo Virtual Cluster](images/gui_page_networkconfiguration.png "Main cluster page")

    1. Scroll down and set the static IP addresses:
    ![Qumulo Virtual Cluster](images/gui_page_networkconfiguration_2.png "Main cluster page")

    1. **Optional:** Floating IP addresses can be assigned that will redistribute in case of a node failure.

    1. Finally, scroll down and click “Save”:
    ![Qumulo Virtual Cluster](images/gui_page_networkconfiguration_3.png "Main cluster page")

    1. A dialog should appear:
    ![Qumulo Virtual Cluster](images/gui_status_networkconfiguration.png "Main cluster page")

    1. Static networking should now be successfully configured:
    ![Qumulo Virtual Cluster](images/gui_page_info_networkconfiguration.png "Main cluster page")

    1. Scrolling down will show the IPv4 addresses assigned to each node:
    ![Qumulo Virtual Cluster](images/gui_page_info_networkconfiguration_nodes.png "Main cluster page")

#### Done!
This concludes initial configuration.  The Qumulo cluster is now sharing data and exports and shares may now be created.
