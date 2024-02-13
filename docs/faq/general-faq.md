#Jetstream2 FAQ Home

For specific FAQs, see the following pages:

* [Allocations FAQ](alloc.md)
* [Troubleshooting](trouble.md)
* [Security FAQ](security.md)
* [Software FAQ](software.md)
* [Gateways FAQ](gateways.md)

---
## General FAQs

### I'm getting an error trying to log into Exosphere or Horizon

If you get an error that looks like this trying to log in to Exosphere or Horizon:

> To use Jetstream2, your account must belong to an ACCESS allocation that is active on a Jetstream2 resource. Please visit https://docs.jetstream-cloud.org/faq/general-faq

you need to confirm that you either are the PI of an allocation or are on a valid allocation. If you need to be added to an allocation, you'll need to contact the PI of that allocation to do this. We are unable to add users to allocations.

If you are indeed on an allocation or are the PI of an allocation, please note that it can take up to four hours for allocations/users to become active. This is outside of our control. If you are still unable to log into [Exosphere](../ui/exo/login.md) or [Horizon](../ui/horizon/intro.md) after four hours from being added, please open a ticket via either the [ACCESS Help Form](https://support.access-ci.org/user/login?destination=/open-a-ticket){target=_blank} or the [Jetstream Help Form](https://jetstream-cloud.org/contact/index.html){target=_blank}.

!!! Note "Use ACCESS CI credentials if you're having trouble authenticating"

     We know ACCESS-CI credentials work correctly and recommend using those unless you are 100% sure you have linked credentials PREVIOUSLY in CILogon.<p>Please note that other CILogon credentials (i.e. for your home institution or Google) must be set up outside of this process. Follow these [Linking instructions](https://identity.access-ci.org/id-linking){target=_blank} to link your home institution or other organization (e.g. Google, ORCID, etc) credentials.


### I was added to an allocation but can't access Jetstream2?

It can take up to four hours for ACCESS to sync up everything to Jetstream2. If you were added recently, we recommend trying later. If you still cannot access your Jetstream2 account and your PI or resource manager has confirmed that you are on a valid allocation, [contact Jetstream2 help](https://jetstream-cloud.org/contact/index.html){target=_blank}.

!!! Note "Use ACCESS CI credentials if you're having trouble authenticating - see just above!"


---

### How do I cite Jetstream2 ?

The Jetstream2 team requests that all researchers using Jetstream2 cite us in any publications that utilize results that were computed or created on Jetstream2. We keep the most up to date citation information here - [Jetstream2 Citation Information](https://jetstream-cloud.org/research/index.html#cite-jetstream){target=_blank}

---

### I need a root disk larger than the maximum size for Jetstream2 instances. Can you create a custom flavor for me?

In OpenStack, flavors define the compute, memory, and storage capacity of instances. We may also refer to it in support tickets or documentation as the VM's size.

We won't create custom flavors, but there are ways to get larger root disks. You can [review the flavors](../general/vmsizes.md) and see if moving up from one of the smaller VMs to a slightly larger one would yield a larger root disk. The other option is to use a custom sized root disk using what Openstack calls "boot from volume", or a "volume-backed" instance. What this means is that instead of an ephemeral boot disk for the instance, a volume is used to be the root disk.

There are several upsides to this:

* You can have a root disk large enough to fit your needs
* The disk becomes reusable as a volume if necessary
* Shelving the instance is extremely fast compared to shelving a typical instance

The downside is that using boot from volume will count against your Jetstream2-Storage allocation whereas root disks do not.

Instructions for using boot from volume are here:

* [Exosphere: Choose a Root Disk Size](../ui/exo/create_instance.md#configure-instance)
* Cacao (link coming)
* [Horizon](../ui/horizon/launch.md#alternative-volume-backed-instance)
* [CLI](../ui/cli/launch.md)

---

### How do I get access to one of the Jetstream2 regional clouds?

The regional clouds of Jetstream2 (Arizona State University, Cornell University, University of Hawai'i, and Texas Advanced Computing Center) are available via invitation only. They have limited resources and the local PIs have discretion as to which projects may run there.

All allocations gain access to the primary Jetstream2 cloud at Indiana University. If you have an allocation and wish to have it added to a regional cloud, you can [request access using this form](https://jetstream-cloud.org/contact/index.html){target=_blank}

*As the regional clouds have autonomy over their access and because resources are limited, it's important to note that not all requests may be accommodated.*

---

### Will there be Microsoft Windows support on Jetstream2 ?

Microsoft Windows is not officially supported on Jetstream2. We will be making a limited number of images available for experimental use.

It is not known at this time whether GPUs will work on Microsoft-based instances. We will test this as time permits.

More information may be found on the [Microsoft Windows on Jetstream2](../general/windows.md) page.

---

### How do I share a volume between virtual machines?


You can’t easily share volumes in OpenStack without deploying a Shared File System service. However, the native Openstack Manila filesystems-as-a-service option is available.

Instructions for using manila on Jetstream2 are here - [Manila - Filesystems-as-a-service - on Jetstream2](https://docs.jetstream-cloud.org/general/manila/)

Please note, there are different quotas for block storage (volumes) and shares. There will be a self-service tool for managing those quotas soon, but for now, if you need to have your Jetstream2 Storage quota adjusted between block and share storage, please [contact us via the Jetstream2 contact form](https://jetstream-cloud.org/contact/index.html){target=_blank} with the amount you wish to move between the storage types.

---

### Can I set the password for a user on my virtual machine?

We generally don't recommend using password authentication on Jetstream2, recommending that you use SSH keys for access. That said, if you need to set a password for console access or for some other reason, you can do it like this:

    sudo passwd *username*

---

### How can I get my public IP number from my VM ?

If your VM has a public IP address and you need to find that IP (and don’t have ready access to the Jetstream2 interfaces), use wget or curl from the command line to get your public IP:

    wget http://169.254.169.254/latest/meta-data/public-ipv4 -qO -
    wget http://ipinfo.io/ip -qO -
    curl http://169.254.169.254/latest/meta-data/public-ipv4
    curl http://ipinfo.io/ip

*Note: http://169.254.169.254/latest/meta-data/public-ipv4 works even in conditions in which external DNS servers are not accessible.

---

### How do I get a jetstream-cloud.org DNS name for my instance?

Right now, every allocation's `auto_allocated_network` is set up with OpenStack Designate to automatically create DNS hostnames for instances. DNS hostnames are formatted as:

```instance-name.allocation-name.projects.jetstream-cloud.org```

Or a more real-life example:

```genome-browser.bio123456.projects.jetstream-cloud.org```

The DNS hostname points to your instance's public (a.k.a. floating) IP address, so this won't currently work if you remove an instance's public IP (or create an instance without a public IP).

If DNS hostnames are not working for your allocation or you'd like to set up Designate for another network, please [create a support ticket](https://jetstream-cloud.org/contact/index.html){target=_blank}.

!!! Note
    For information about hostnames outside the `projects.jetstream-cloud.org` space, see ["How do I set up a custom domain name for my gateway, site, or web service?"](gateways.md#how-do-i-set-up-a-custom-domain-name-for-my-gateway-site-or-web-service)

---

### Are there backups of Jetstream2 storage resources ?

Jetstream2 provides multiple forms of storage, including block (volumes), shares (Manila), and an object store. All of these storage formats are on erasure coded partitions that should provide protection against data loss in the case of hardware issues or outages.

Jetstream2, however, does not provide any backup service for data. Since the storage is not a shared filesystem as on traditional HPC, there are issues with providing consistent backup for all of the user-defined instance root disks, volumes, shares, and object store buckets. As such, we recommend that you keep a copy of any crucial data offsite. This is a good practice no matter what computing system you may be on.

Additionally, there are NSF-funded resources like the Open Storage Network (OSN) available for research storage for work in [active use](https://www.openstoragenetwork.org/motivation/our-policy/){target=_blank}. This is also an ACCESS allocated resource. More information may be found on the [Open Storage Network website](https://www.openstoragenetwork.org/){target=_blank}

---

### What are the IP ranges / CIDR blocks for Jetstream2 ?

The current CIDR blocks for Jetstream2 are:

```
149.165.152.0/22
149.165.159.0/24
149.165.168.0/21
```

---

### How do I keep a program running on a VM even if I log out or get disconnected?

If you want to start a workflow and have it run, that's a unix capability.

Tutorials like [How to Run Linux Commands in Background](https://linuxize.com/post/how-to-run-linux-commands-in-background/){target=_blank}

show a number of methods shown here on how to start a program and leave it running, even if your connection disconnects.

We would suggest looking at the nohup command. As that page says:

*"Another way to keep a process running after the shell exit is to use nohup.*

*The nohup command executes another program specified as its argument and ignores all SIGHUP (hangup) signals. SIGHUP is a signal that is sent to a process when its controlling terminal is closed."*

To run a command in the background using the nohup command, type:

    nohup command &

If you want to log any terminal output to a file, you can use one of these commands below.

To redirect standard output and standard error to different files:

    nohup myprogram > myprogram.out 2> myprogram.err

or to the same file:

    nohup myprogram > myprogram.out 2>&1
