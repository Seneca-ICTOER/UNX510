---
id: lab1
title: Lab 1 - Creating Your VM in Azure
sidebar_position: 1
description: Creating Your VM in Azure
---


# Lab 1 - Creating Your VM in Azure

## Purpose / Objectives of Lab 1

In this lab, you will login to **Microsoft Azure** for the first time, navigate your way to **DevTest Labs**, and create your Linux virtual machine.

The main purpose of this lab is to:
1. Create your Linux virtual machine environment using a pre-built image
2. Remotely connect to your new Linux environment
3. Learn basic management of VMs from the Azure web interface.

This VM will be used extensively throughout the rest of this course.

While you are working through this lab, it is highly recommended that you write down general notes and commands to help you remember how to do this lab.

If you encounter technical issues, please contact your professor via e-mail or in your section's Microsoft Teams group.
### Minimum Requirements

Before beginning, you must have:
1. Attended the **Week 1** lectures (or watched the posted recording).
2. Your Seneca login credentials.
3. A computer with an Internet connection. (Windows/macOS/Linux)
4. A mobile device (phone/tablet) to setup 2FA (two-factor authentication).
## Investigation 1: Connecting to Your Azure Account

In this investigation, you'll log in to your Seneca-provided Azure account and ensure you have access to our DevTest Labs digital classroom
### Part 1: Logging In For The First Time

1. **Follow the link to our DevTest Lab in Azure found on Blackboard.**
2. Enter your Seneca credentials. (Same username and password you use for your e-mail)
3. You'll next be asked to set up two-factor authentication. Do not bypass this step!
4. Once you've set that up, verify it by logging out and logging back in again.
5. Conduct a small celebration (pat on the back, a quick jig, perhaps a fist pump) and move on to Investigation 2.
### Part 2: Logging In Afterwards

Logging in after initial setup is quite easy.
1. Navigate to the Azure portal: [https://portal.azure.com](https://portal.azure.com)
2. Use your Seneca credentials.
3. Complete 2FA authentication.
4. Our classroom DevTest Lab will be in your recent list, or you can use the search bar to bring up DevTest Labs by looking for **UNX510**. (_DO NOT search for_ Virtual Machines _in the search bar._ You will find yourself in the wrong area and things will not work.)

## Investigation 2: Managing a CentOS Linux VM in Azure

In this investigation, you'll create, configure, and manage a Linux CentOS Minimal Virtual Machine using Microsoft Azure and a pre-built image.

This means no tedious and time-consuming Linux installation!

This is a command line only OS, so you'll be using SSH to remotely connect to the VM and issue basic commands.
### Part 1: Creating A Linux VM From An Image

To create your Linux Virtual machine, perform the following steps:

1. Navigate to _DevTest Labs > UNX510 > My virtual machines_
2. Click the **+ Add** button.
3. Wait for the _Choose a base_ listing to populate. This may take a few moments.
4. Select the item titled **CentOS-based 7.9**. Be careful here! There are many other options.
5. A new blade, _Create lab resource_ appears.
6. In the _Virtual machine name_ field, type: **yourSenecaUsername-lnx** (you only have 15 characters, you may need to abbreviate)
7. _Username:_ **yourSenecaUsername**
8. _Use a saved secret:_ Unchecked
9. _Password_: Your choice, but use the same for all VMs and resources in this course.
10. _Save as default password:_ Checked.
11. _Virtual machine size_: **Standard_B1s**
12. _OS disk type_: **Standard HDD**
13. Leave the remaining options as they are.
14. Click on the **Create** button at the bottom of the screen.
15. You are now back in the _My virtual machines_ blade while Azure creates your personal virtual machine. This may take a few minutes.
16. When it finishes, you should see a **Your deployment is complete.** message near the top of the page. Congratulations!
17. Click on the **Go to resource** button at the bottom left of the page.
18. **Take a full desktop screenshot of the results in the above step and add it as an attachment to this question.**
19. Move on to the next section of the lab.

When deployment is complete, click on the new VM in _My virtual machines_ to verify its status and find the VM's address. **Write this address down.**
### Part 2: Accessing Your CentOS VM Remotely Using SSH

Requirements: An SSH Client
- **Windows:** Use the built-in Command Prompt or PowerShell.
- **macOS/Linux:** Use the built-in _Terminal_ application.

We will be accessing our new Linux VM remotely using SSH.
1. In the _Overview_ tab for the Virtual Machine created in _Part 1_, look for
2. **IP address or FQDN** entry. This is the address you will use to connect in this section. Write it down (Hover over the URL, and you'll see a _Copy to clipboard_ icon).
3. **NAT protocol / Port to connect** entry. This is the port you'll use to connect in this section. Write it down. (Don't use the _Copy to clipboard_ icon, as all you want is the port number, i.e. **30070** for example.)
4. **On Windows Using Command Prompt, or macOS/Linux Using Terminal**: From the command line, enter the following (using your address from the _Overview_ tab): **ssh -p portnumber yourSenecaUsername@address**
5. When prompted for a password, use the one you gave when you created the VM. (You won't see anything as you type here; that's normal.)
6. If login is successful, you should see a prompt like this: 
```bash
[cjohnson30@cjohnson30-lnx ~]$
```

> ![Image: Windows Command Prompt - SSH Login to CentOS](https://seneca-ictoer.github.io/OPS705/assets/images/azure-cmdssh-login-215094b605d9dece8d2379958baf28ba.png)﻿﻿
	 
8. To prove you've completed this section, run the following command: **hostnamectl**
9. **Take a full desktop screenshot of the results in the above step and add it as an attachment to this question.**
10. To quit your remote SSH session, type: **exit**
11. **Do not skip Part 3 at this stage! Otherwise, you'll be bleeding funds by leaving the VM running.**
### Part 3: Fully Stopping Your Windows Virtual Machine

This section is fairly simple. The one thing to never forget: Ensure your VM's status is set to **Stopped (Deallocated)**.

1. In the _Overview_ blade of your CentOS Linux VM, click on the **Stop** button.
2. A notification will appear in the top right of your browser window, confirming your action.
3. Don't worry about going into the Linx OS and shutting down first. Azure sends a signal to the VM to shut down safely.
4. If your VM status says stopped, but does not include the **(Deallocated)** text, then resources are still being held by the VM and we're still being charged. The stop button will still be available, so click it.
5. **Take a full desktop screenshot of the results in the above step and add it as an attachment to this question.**

> ![Image: Azure VM - Deallocated](https://seneca-ictoer.github.io/OPS705/assets/images/azure-deallocated-730a3ca2469cfa2107a3688a87f5cd0f.png)*Figure 2.* Example of _Deallocated_ view in Azure

## Investigation 4: Managing Your VM Directly Through Azure's UI

In this quick investigation, we'll walk through how to directly manage virtual machines from the Azure Dashboard interface on a basic level. This is useful for starting up VMs, shutting them down when unresponsive, and deleting them when you're finished.

(**Warning:** Do not delete the VM created in this lab!)

>  **IMPORTANT - After creating your VM for the first time, you must log out and log back in to Azure.** When you first create a VM in DevTest Labs (DTL) and it's in a fully running state, you need to log out and log back into the Azure Portal for permissions to be added properly to your account. If you don't, you'll get _Permission denied_ warnings from Azure if you try to do this investigation.
### Part 1: Powering On A Virtual Machine

From the _DevTest Labs_ blade:

1. Click on the _My virtual machines_ menu bar item.
2. Click on the virtual machine you'd like to manage to move to its _Overview_ blade.
3. Click the **Start** menu button near the top.
### Part 2: Powering Off A Virtual Machine

From the _DevTest Labs_ blade:

1. Click on the _My virtual machines_ menu bar item.
2. Click on the virtual machine you'd like to manage to move to its _Overview_ blade.
3. Click the **Stop** menu button near the top.

Remember the difference between the status _Stopped_ and _Stopped (deallocated)_!
### Part 3: Restarting A Virtual Machine

There are two methods to restarting a VM. Either within the OS, or through the Azure Dashboard.

**From inside the Linux OS:**

1. Run the following: 

```bash
sudo reboot
```

2. You will then be disconnected from your remote session. Wait a few minutes while the VM restarts, and reconnect.

**From Azure Dashboard:**

3. Click on the **Restart** button from the VM's _Overview_ blade.
4. Wait until the VM's status has changed to **Running** before logging back in.
### Part 4: Deleting A Virtual Machine

Deleting a Virtual Machine is useful when you no longer need it long-term, or if there's a catastrophic issue with the OS inside. Be careful! Any saved data inside the VM will be deleted as well!

1. Navigate to the VM's _Overview_ blade.
2. If the VM status isn't **Stopped (Deallocated)**, stop the VM. Wait until its status updates.
3. Click on the **Delete** button at the top of the blade.
### Part 5: A Note About Resource Usage

As mentioned during our lecture and throughout this lab, using resources responsibly is incredibly important. We pay for what we use. While we have a fail-safe in place to stop all VMs at **2:00am EST daily**, don't rely on it!

**Fully stop your VM when you're not using them.**

Your total allowed resource allocation has been restricted for this course. This means you can only have one VM in existence at a time. If you have one already, you won't be able to add another until you delete one.
