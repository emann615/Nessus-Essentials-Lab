# Nessus Essentials Lab: Vulnerability Management

 ### [YouTube Demonstration](https://www.youtube.com/watch?v=_r7OhxCgxOo&t=2s)

## Description
Nessus is a proprietary vulnerability scanner developed by Tenable, Inc that can remotely scan a computer or network for vulnerabilities. In this lab, I will install Nessus Essentials on a Windows 10 virtual machine and use it to run three scans against the Windows Server 2022 domain controller I set up in my previous Active Directory Home Lab.

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

## Table of Contents:

   * [Part 1: Install VirtualBox](#part-1-install-virtualbox)
   * [Part 2: Download Windows 10 and Windows Server 2022 ISO Files](#part-2-download-windows-10-and-windows-server-2022-iso-files)
   * [Part 3: Create Domain Controller Virtual Machine](#part-3-create-domain-controller-virtual-machine)
   * [Part 4: Install and Set Up Windows Server 2022 on the DC Virtual Machine](#part-4-install-and-set-up-windows-server-2022-on-the-dc-virtual-machine)
   * [Part 5: Install VirtualBox Guest Additions](#part-5-install-virtualbox-guest-additions)
   * [Part 6: Set Up IP Addressing and Rename the PC](#part-6-set-up-ip-addressing-and-rename-the-pc)
   * [Part 7: Install Active Directory Domain Services and Create Your Domain](#part-7-install-active-directory-domain-services-and-create-your-domain)
   * [Part 8: Create Dedicate Domain Admin Account](#part-8-create-dedicate-domain-admin-account)
   * [Part 9: Install RAS / NAT](#part-9-install-ras--nat)
   * [Part 10: Set Up a DHCP Server On Your Domain Controller](#part-10-set-up-a-dhcp-server-on-your-domain-controller)
   * [Part 11: Use PowerShell Script to Create Users](#part-11-use-powershell-script-to-create-users)
   * [Part 12: Create Client Virtual Machine](#part-12-create-client-virtual-machine)
   * [Part 13: Install and Set Up Windows 10 on the Client Virtual Machine](#part-13-install-and-set-up-windows-10-on-the-client-virtual-machine)
   * [Part 14: Rename the PC and Join the Domain](#part-14-rename-the-pc-and-join-the-domain)
   * [Part 15: Find the Client Computer on the Domain Controller](#part-15-find-the-client-computer-on-the-domain-controller)

## Walk-through:

### Part 1: Install VirtualBox

1. Download **VirtualBox** by going to the following link: https://www.virtualbox.org/wiki/Downloads
   * Download the version for whatever OS you are using.
2. Download the **VirtualBox Extension Pack** from the same page.
3. Open the files you downloaded to install **VirtualBox** and the **VirtualBox Extension Pack**.
