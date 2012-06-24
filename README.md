# Ushahidi Virtual Machines

These are pre-built virtual machine images intended for brief demonstrations and experimentation. They are not  security hardened and should not be used in real environments. These VMs are provided as-is and without support. You can email evan@ushahidi.com with questions.

The motto of this project is: Boot up, show off, and throw away.

Keep the image around and have a clean, functioning installation of Ushahidi ready whenever you need it.

## What’s included

* Ushahidi 2.4
* Ubuntu 12.04 LTS (Precise Pangolin)
* Nginx 1.1.19
* MySQL 5.5
* PHP 5.3.10
* Git

## Requirements

Ushahidi VM is lightweight and should run comfortablably with 512MB of memory, perhaps less. From the shell you can use htop to monitor CPU and memory usage.

## Setting Up

Ushahidi VM is currently available for [VirtualBox](https://www.virtualbox.org/), a free virtualization tool from Oracle. VirtualBox is compatible with Windows, Mac, Linux, and Solaris. You will need to have [downloaded](https://www.virtualbox.org/wiki/Downloads) and [installed](https://www.virtualbox.org/manual/ch02.html) VirtualBox before proceeding.

Next, download the Ushahidi VM image. We’ve packed the VM as a VirtualBox Appliance, which makes it relatively simple to setup. From the VirtualBox GUI choose to “Import Appliance” and select the Ushahidi VM image. It may take a few minutes for the files to be extracted.

> Note: For simplicity sake, do not reset the MAC address of the network cards if asked. This may result in you having to manually reenable network interfaces inside the VM.

Once imported you will see a new “Ushahidi VM” listing in your VirtualBox interface. Before booting it up, you’ll want to attach it to a physical or virtual network adapter. Right click the Ushahidi listing, choose Settings and then dive into the Network tab. For “Adapter 1”, pick a network configuration of your choice, and press OK to save the choice.

Finally, start your Ushahidi VM.

## Using It

### Shell Access

You can use a pre-configured user account to access the shell; "demo" is both the username and password of this account. Again: This VM is not secured and would be easily exploited in a live environment.

### Finding Your IP

Depending on your network adapter choice, you will likely have been assigned a LAN IP by your network. You can type “ip a” from the shell to see a list of addresses your VM is running on. One should be a local loopback address (127.0.0.1) and the other will be your network accessible IP.

### Configuring the Machine

#### Recommended Method

We recommend editing your hosts file. On Windows, this file is at C:\Windows\system32\drivers\hosts. On Mac OS X, it's at /prviate/etc/hosts. On Linux, it's at /etc/hosts. Note that this file usually requires root or adminstrative priviledges in order to make changes, so sudo or otherwise launch your editor accordingly.

Add a new line to this file beginning with the IP address you gathered in the previous step, followed by a space and the domain "demo.ushahidi.com". So, for example, your new line might read something like "10.0.0.1 demo.ushahidi.com", without the quotes.

Save and close your hosts file. Continue to "Accessing Ushahidi" below.

#### Alternative Method

Record the IP address attained in the previous step. In the "Accessing Ushahidi" section that follows, replace 'demo.ushahidi.com' with that series of characters. Note that this method may not work properly, or may require modifications to the /etc/nginx/sites-enabled/ushahidi file.

### Accessing Ushahidi

Open your web browser and visit http://demo.ushahidi.com/. You should be greeted by a clean Ushahidi installation, ready to be worked with.

To administer your Ushahidi installation, load http://demo.ushahidi.com/admin/. The username and password are both ‘admin’.

## Upgrading Ushahidi

We will try to upgrade these images with new versions of Ushahidi as time permits, but if you’d like to upgrade to new versions in the term simply cd into the /var/www directory and use “git pull” to sync it.

You may need to run a database upgrade script afterwards, just as you would with any other installation. Modifications to configuration files will need to be re-applied as well.

As Ushahidi VM does not contain an FTP server by default, the quick upgrade option will not work.

## Final Thoughts

These virtual machines are provided for demonstration purposes only. They are not intended for live environments. They are neither security hardened nor stable enough for production applications. Remember the mantra: Boot up, show off, and throw away.

If you’d like something more persistent and less complicated, consider using [Crowdmap.com](http://crowdmap.com) where Ushahidi provides free hosting of deployments.
