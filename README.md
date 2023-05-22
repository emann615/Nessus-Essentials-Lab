# Nessus Essentials Lab: Vulnerability Management

 ### [YouTube Demonstration](https://www.youtube.com/watch?v=_r7OhxCgxOo&t=2s)

## Description
Nessus is a proprietary vulnerability scanner developed by Tenable, Inc that can remotely scan a computer or network for vulnerabilities. In this lab, I will install Nessus Essentials on a Windows 10 virtual machine and use it to run three scans against the Windows Server 2022 domain controller I set up in my previous [Active Directory Home Lab](https://github.com/emann615/ActiveDirectoryLab).

<div style="page-break-after: always; visibility: hidden"></div>

The first scan will be a non-credentialed scan before any updates have been applied to the domain controller. The second scan will be a credentialed scan before any updates have been applied. The third and final scan will be a credentialed scan of the domain controller after updates have been applied. At the end of this lab, I will compare the results of the three scans.
<br />

## Languages and Utilities Used

* **VirtualBox** 
* **Active Directory**
* **Nessus Essentials**

## Environments Used

* **Windows 10**
* **Windows Server 2022**

## Prerequisite:

* Follow the steps in my [Active Directory Home Lab](https://github.com/emann615/ActiveDirectoryLab) to:
   * Download and Install Oracle VirtualBox.
   * Create a domain controller (DC) virtual machine running Windows Server 2022
      * Make sure you do not install any system updates.
   * Set up Active Directory on the  domain controller.
   * Create a second virtual machine (PC 1) running Windows 10.
   * Connect the PC 1 virtual machine to the domain.

## Walk-through:

### Table of Contents:

   * [Part 1: Download Nessus on the PC 1 VM](#part-1-install-virtualbox)
   * [Part 2: Install Nessus on the PC 1 VM](#part-2-download-windows-10-and-windows-server-2022-iso-files)
   * [Part 3: Find the IP address of the Domain Controller](#part-3-create-domain-controller-virtual-machine)
   * [Part 4: Create a New Scan in Nessus](#part-4-install-and-set-up-windows-server-2022-on-the-dc-virtual-machine)
   * [Part 5: Run Scan #1 (Non-credentialed) and View the Results](#part-5-install-virtualbox-guest-additions)
   * [Part 6: Run Scan #2 (Credentialed) and View the  Results](#part-6-set-up-ip-addressing-and-rename-the-pc)
   * [Part 7: Update the Windows Server](#part-7-install-active-directory-domain-services-and-create-your-domain)
   * [Part 8: Run Scan #3 (Credentialed) and View the Results](#part-8-create-dedicate-domain-admin-account)

### Part 1: Install VirtualBox

1. Download **VirtualBox** by going to the following link: https://www.virtualbox.org/wiki/Downloads
   * Download the version for whatever OS you are using.
2. Download the **VirtualBox Extension Pack** from the same page.
3. Open the files you downloaded to install **VirtualBox** and the **VirtualBox Extension Pack**.
