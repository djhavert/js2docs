# Interacting with Your Instance
## Accessing your Instance

### Web Shell

### Web Desktop

## Installing Software

### Load Modules

### Installing Other Software

## Transfer Files

## Adding Data Storage

You may have noticed that your instance only comes with 20 GB of storage on the root disk. If you are only storing some software and scripts, this may be enough, but if you plan to store large datasets, this most definitely will not be enough. Here we are going to walk through the best practices for storing data on Jetstream2.

### Creating a Volume

### Attaching a Volume

!!! Note "Drive Changed Locations?"

    When you attach a volume in Exosphere, it automatically mounts the drive to the first available slot. (| sda | sdb | sdc | sdd |, etc). sda is where your root disk is mounted, so if you attached another volume, it will be mounted to sdb. If you have multiple volumes and detach/reattach them regularly, then the volumes could be mounted in a different order than you're used to.

### Accessing the Volume

