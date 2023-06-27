# Creating Your First Instance

## Terminology
*   Instance/Server
*   Flavor
*   Volume
*   Image

## Log In Through Exosphere

There are multiple dashboards you can use to log in. Exosphere is by far the most user-friendly, so that's what we will use for this guide.

1.  Start by going to [https://jetstream2.exosphere.app/](https://jetstream2.exosphere.app/).
   
2.  Click on the "Add Allocation" card.
   
   <img src="/images/exo-add-alloc.png" alt="A screenshot showing the 'Add Allocation' button on the Exosphere home page" width="40%"/>

3.  Click on "Add ACCESS Account" to log in to your ACCESS account.
   
   <img src="/images/exo-add-access-acct.png" alt="A screenshot showing the 'Add ACCESS account' button" width="50%"/>

4.  Once you click on “Add ACCESS account”, you will be redirected to a CILogon page, a platform that manages ACCESS log ins. Select ACCESS CI (XSEDE) from the “Select an Identity Provider” drop down menu.

    <img src="/images/exo-cilogon-dropdown.png" alt="A screenshot showing the 'Select an Identity Provider' dropdown, with 'ACCESS CI (XSEDE)' selected" width="50%"/>

5.  Log in using your **ACCESS credentials**. Please note that this may require multi-factor (Duo) authentication. If you need help setting up or changing your multi-factor authentication method, please open an [ACCESS Help Ticket](https://support.access-ci.org/user/login?destination=/open-a-ticket){target=_blank}, as Jetstream2 staff cannot fix this for you directly.

6.  After you log in with your ACCESS credentials, Exosphere will prompt you to select from the allocations that you are a member of. Any un-selected allocations will not be added the Exosphere interface, so select all that you may want to use.

7.  Finally, click on the card corresponding to the allocation you want to use.

## Creating an Instance

Once you have logged in and selected an allocation, select “Create” and then “Instance”.

<img src="/images/exo-create-dropdown.png" alt="screenshot of create dropdown" width="80%"/>

### Choose an Instance Source
Here you have a choice between a few different Operating Systems. We recommend Ubuntu 22.04 (latest) if you are a new user and don't know what to choose. That is what we will be choosing for this guide.

On the left panel under Ubuntu, select "22.04 (latest)".

<img src="/images/exo-select-image-ubuntu-22.png" alt="A screenshot showing which source to choose" width="50%"/>

### Create Instance

#### Name 
Choose a name for your instance. Be descriptive! Other users on your allocation can see your instance, so name your instance such that they (and yourself) remember what it's for a year from now.

<img src="/images/exo-choose-name.png" alt="screenshot showing instance name" max-width="50%"/>

#### Flavor
Choose your flavor. For this guide we will select an m3.small. 

<img src="/images/exo-select-flavor.png" alt="screenshot showing flavor to choose" max-width="50%"/>

For playing around with instances and doing testing, an m3.tiny or m3.small is usually sufficient and a good way to preserve your SUs. We chose to go with an m3.small because we will be showing off the web desktop in this guide and an m3.tiny is just a bit too slow for that.

See [VM Sizes and configurations](../general/vmsizes.md){target=_blank} for more details on all of the different flavors you can choose from.

#### Choose a root disk size
Leave this option as its default (20 GB for m3.quad or smaller, 60 GB for m3.medium or larger). 

<img src="/images/exo-choose-root-disk-size.png" alt="screenshot showing flavor to choose" width="max-50%"/>

The root disk is where applications, scripts, and log files are stored. If you set a custom disk size here, that storage space will count towards your 1 TB default storage space. If you leave it as default, it won't count against you. For storing data, best practice is to create a separate data volume and mount it. We will be covering that later.

#### How many Instances?
Leave this value at '1'.

<img src="/images/exo-choose-num-instances.png" alt="screenshot showing flavor to choose" max-width="50%"/>

You will most likely never need to use this option. It's useful in saving time if you need to create multiple identical instances at once.

#### Enable web desktop?

Choose 'Yes'

<img src="/images/exo-choose-web-desktop.png" alt="screenshot showing flavor to choose" max-width="50%"/>

This will enable you to use your instance with a full desktop, as if you had the computer hooked up to a monitor right in front of you. Only leave this at 'No' if you are comfortable using a computer solely from the command line. There is a slight performance cost in using the desktop, which is why we opted for an m3.small for this guide instead of an m3.tiny, but this cost may not be meaningful on a larger flavor.

#### Choose an SSH public key

For now, choose 'None'.

Exosphere automatically creates an ssh key so you can log in to your instance from the Exosphere interface, so we don't have to worry about uploading our own keys. However, if you are an advanced user who would like to SSH into your instance like you would any other server (i.e without using Exosphere), you will need to upload your SSH key. SSH keys are outside the scope of this guide though, so if you would like to learn more about this, there are plenty of guides out there ([like this one](https://dev.to/risafj/ssh-key-authentication-for-absolute-beginners-in-plain-english-2m3f)).

#### Advanced Options

Let's keep that hidden for now. Feel free to explore these options if you're curious, but don't change anything if you are following along with this guide.

#### Click Create!
You are now ready to create your instance. Scroll the rest of the way down and click the big red "Create" button. After you do that, you should be taken back to the Exosphere homepage for your project. You should see the instance you just created there with a yellow 'Building' tag. 

<img src="/images/exo-go-to-Instances.png" alt="screenshot showing flavor to choose" max-width="50%"/>

You are now ready to log into your instance and start installing software. Go ahead and click anywhere on the 'Instances' card to navigate to the Instances Preview page, then proceed to the next page in this guide.
