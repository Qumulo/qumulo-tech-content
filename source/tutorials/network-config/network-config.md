---
title: Configure the network for static addresses
url: network-configuration
---
# Configure the network for static addresses

In this tutorial you use Network Configuration to manually assign IPv4 static addresses.

1. From the dashboard, point to **Cluster** and click **Network Configuration**. 

    ![Select Network Configuration](images/cluster-network-configuration.png)

2. The Network Configuration screen appears. In this example, the cluster is currently configured to use DHCP.

    ![Network configuration -- DHCP](images/network-config-dhcp-successful.png)

3. Click **Switch to Static IP** to manually assign IPv4 static addresses.
4. The Network Configuration IPv4 screen appears.

    ![Network configuration -- IPv4](images/network-config-static-1.png)

5. Fill in each of the fields as appropriate and change the MTU size, if necessary.
6. Scroll down and set the static IP addresses. Use either a comma-separated list or a range, using a dash.

    ![Network configuration -- set static IP addresses](images/network-config-2-staticIPs.png) 

7. Optionally, you can assign floating IP addresses that will automatically be reassigned to the remaining nodes if a node fails. 

    ![Network configuration -- set floating IP addresses](images/network-config-3-save.png)


8. Click Save.
9. A dialog box appears

    ![Network configuration -- refresh](images/network-config-refreshing-view.png)

10. The Network Configuration IPv4 screen shows that you are now using static networking.

    ![Network configuration -- using static](images/network-configuration-successful.png)

11. To change static settings, click **Edit Static Settings**.
12. To revert to DHCP, click **Switch to DHCP**.
13. The screen changes to show a pending state.

    ![Network configuration -- DHCP pending](images/network-config-dhcp-save.png)

14. Click **Save**.
15. A dialog box appears.

    ![Network configuration -- refresh](images/network-config-refreshing-view.png)

16. The screen changes to show you are now using DHCP.

    ![Network configuration -- switched to DHCP](images/network-config-dhcp-success2.png)

 
