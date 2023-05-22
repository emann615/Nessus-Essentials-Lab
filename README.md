# Nessus Essentials Lab: Vulnerability Management

## Description
Nessus is a proprietary vulnerability scanner developed by Tenable, Inc that can remotely scan a computer or network for vulnerabilities. In this lab, I will install Nessus Essentials on a Windows 10 virtual machine and use it to run three scans against the Windows Server 2022 domain controller I set up in my previous [Active Directory Home Lab](https://github.com/emann615/ActiveDirectoryLab).

<div style="page-break-after: always; visibility: hidden"></div>

The first scan will be a non-credentialed scan before any updates have been applied to the domain controller. The second scan will be a credentialed scan before any updates have been applied. The third and final scan will be a credentialed scan of the domain controller after updates have been applied. At the end of this lab, I will compare the results of the three scans.
<br />

## Table of Contents

   * [Languages and Utilities Used](#Languages-and-Utilities-Used)
   * [Environments Used](#Environments-Used)
   * [Prerequisite](#Prerequisite)
   * [Part 1: Download Nessus on the PC 1 VM](#Part-1-Download-Nessus-on-the-PC-1-VM)
   * [Part 2: Install Nessus on the PC 1 VM](#Part-2-Install-Nessus-on-the-PC-1-VM)
   * [Part 3: Find the IP Address of the Domain Controller](#Part-3-Find-the-IP-Address-of-the-Domain-Controller)
   * [Part 4: Create a New Scan in Nessus](#Part-4-Create-a-New-Scan-in-Nessus)
   * [Part 5: Run Scan 1 (Non-credentialed) and View the Results](#Part-5-Run-Scan-1-Non-credentialed-and-View-the-Results)
   * [Part 6: Run Scan 2 (Credentialed) and View the Results](#Part-6-Run-Scan-2-Credentialed-and-View-the-Results)
   * [Part 7: Update the Windows Server](#Part-7-Update-the-Windows-Server)
   * [Part 8: Run Scan 3 (Credentialed) and View the Results](#Part-8-Run-Scan-3-Credentialed-and-View-the-Results)
   * [Results](#Results)

## Languages and Utilities Used

* **VirtualBox** 
* **Active Directory**
* **Nessus Essentials**

## Environments Used

* **Windows 10**
* **Windows Server 2022**

## Prerequisite

* Follow the steps in my [Active Directory Home Lab](https://github.com/emann615/ActiveDirectoryLab) to:
   * Download and Install Oracle VirtualBox.
   * Create a domain controller (DC) virtual machine running Windows Server 2022
      * Make sure you do not install any system updates.
   * Set up Active Directory on the  domain controller.
   * Create a second virtual machine (PC 1) running Windows 10.
   * Connect the PC 1 virtual machine to the domain.

## Walk-through

### Part 1: Download Nessus on the PC 1 VM

1. Start up the **DC** virtual machine and the PC 1 virtual machine.
2. Log in to the **PC 1** virtual machine using the admin account you created in Active Directory.
3. Open **Microsoft Edge**.
4. Go to the following link: https://www.tenable.com/downloads/nessus 
5. Under **Version**, make sure the latest version of Nessus is selected.
6. Under **Platform**, make sure **Windows - x86_64** is selected.
7. Click **Download**, and click **I Agree on the License Agreement**.

### Part 2: Install Nessus on the PC 1 VM

1. Once Nessus has finished downloading, double click the file to start the installation process
2. Once the installation wizard pops up, click **Next**.
3. Select **I accept the terms in the license agreement**, and click **Next**.
4. Click **Next** again, and click **Install** on the last page.
5. Click **Yes** when asked “Do you want to allow this app to make changes to your device?”.
6. Once Nessus has finished installing, click **Finish**.
7. A new page will open up in **Microsoft Edge**. Click **Connect via SSL**.
8. Click **Advanced**, and click **Continue to local host (unsafe)**.
9. Once Nessus has finished initializing, click **Continue**.
10. Select **Register for Nessus Essentials**, and click **Continue**.
11. Under **Get an activation code**, type in your first name, last name, and email.
12. Click **Register**, and an activation code will be sent to your email.
13. Find the activation code that was sent to your email
14. Enter the code in the box under **Activation Code**, and click **Continue**.
15. On the **License Information** page, click **Continue** again
16. Create a username and password for Nessus. Then click **Submit**.
17. Wait for the plugins to finish downloading then you will be taken to the **My Scans** page inside Nessus.
18. Before you can create your first scan, you will have to wait for the plugins to finish downloading.
    * You can hover your mouse over the spinning circle icon in the top menu bar to track the progress.
19. Copy and save the local URL for Nessus so it is easy to access in the future.
    * **Nessus URL:**  https://localhost:8834/# 

### Part 3: Find the IP Address of the Domain Controller

1. Go to the **DC** virtual machine, and log in.
2. Click **Start**, and type cmd.
3. Hit **Enter** to open **Command Prompt**.
4. Type **ipconfig** into Command Prompt, and hit **Enter**.
5. Find the address next to **IPv4 Address**.

### Part 4: Create a New Scan in Nessus

1. Go back to the **PC 1** virtual machine.
2. Click **Create a new scan** in Nessus.
3. Click **Basic Network Scan**.
4. In the box next to **Name**, type in a name for your scan.
5. In the box next to **Targets**, type in the IP address of your domain controller.
6. Click **Save** to save your scan.

### Part 5: Run Scan 1 (Non-credentialed) and View the Results

1. From the **My Scans** page, click the Launch icon to begin running your scan.
2. Wait for the scan to finish. You will see a check mark next to the scan once it is complete.
3. Double click the scan to view the results.
4. In the **Host** tab you will see a bar that displays the vulnerability count and graphical depiction of the vulnerabilities that were found based on percentage.
   * Vulnerabilities are categorized based on their risk level (Critical, High, Medium, Low, Info).
5. Click the bar that displays the vulnerability count to open up a detailed list of specific vulnerabilities that were found.
6. Click each vulnerability to see more details, including a description and proposed solution for the vulnerability.

### Part 6: Run Scan 2 (Credentialed) and View the Results

1. Go back to the **My Scans** page.
2. Click the check box next to the scan.
3. Click the dropdown arrow next to **More**, and click **Configure**.
4. Select the **Credentials** tab, and click **Windows**.
5. Type in the username and password for the admin account you created in Active Directory, and click **Save**.
6. Go back to the **My Scans** page, and click the **Launch** icon next to the scan to run it.
7. Double click the scan to view the results.
8. Select the **History** tab to view a list of scans you have completed.
9. Click each scan to review the results.
10. Compare the results of the non-credentialed scan to the results of the credentialed scan you just ran.
11. Select the **Vulnerabilities** tab to see a detailed list of vulnerabilities that were found after the credentialed scan.
    * The credentialed scan should find a lot more vulnerabilities than the non-credentialed scan.

### Part 7: Update the Windows Server

1. Go back to the **DC** virtual machine, and log in.
2. Click **Start**, and select **Settings**.
3. Click **Updates and Security**.
4. Click **Windows Update**.
5. Click **Install now** to install the updates.
6. Keep installing updates until your system is completely up to date.
   * You may be required to restart the machine several times to apply the updates.

### Part 8: Run Scan 3 (Credentialed) and View the Results

1. Go back to the **PC 1** virtual machine and log in.
2. From the **My Scans** page inside Nessus, click the **Launch** icon to begin running your second credentialed scan.
3. Once the scan is complete, double click it to review the results.
4. Select the **History** tab to compare the results of the three scans.
   * Most of the vulnerabilities found after the first credentialed scan should now be fixed.

## Results

### Scan 1 Results (Non-credentialed)
| Risk Raiting | Count | Percentage |
| --- | --- | --- |
| Critical | 0 | 0.00% |
| High | 0 | 0.00% |
| Medium | 1 | 1.45% |
| Low | 1 | 1.45% |
| Info | 67 | 97.10% |
| **Total** | **69** | **100.00%** |

The first scan was a non-credentialed scan before any updates were applied to the domain controller. This scan produced 1 medium, 1 low, and 67 info results. Non-credentialed scans are not as useful as credentialed scans when trying to get an accurate view of vulnerabilities that exist on a device or network because they lack proper access. Non-credentialed scans cannot see vulnerabilities that may exist on parts of a device or network that are off limits without proper authentication. As a result, non-credentialed scans produce far less results than credentialed scans.

### Scan 2 Results (Credentialed)
| Risk Raiting | Count | Percentage |
| --- | --- | --- |
| Critical | 10 | 3.79% |
| High | 7 | 2.65% |
| Medium | 6 | 2.27% |
| Low | 1 | 0.38% |
| Info | 240 | 90.91% |
| **Total** | **264** | **100.00%** |

The second scan was a credentialed scan before any updates were applied to the domain controller. This scan produced 10 critical, 7 high, 6 medium, 1 low, and 240 info results. Since this scan was configured with the proper credentials, a lot more results were produced.


### Scan 3 Results (Credentialed)
| Risk Raiting | Count | Percentage |
| --- | --- | --- |
| Critical | 0 | 0.00% |
| High | 0 | 0.00% |
| Medium | 1 | 1.09% |
| Low | 1 | 1.09% |
| Info | 90 | 97.83% |
| **Total** | **92** | **100.00%** |

The third scan was a credentialed scan after updates had been applied to the domain controller. The results of this scan showed far less vulnerabilities than the previous credentialed scan I ran before updates were applied.This scan produced 1 medium, 1 low, and 90 info results. All of the critical and high level vulnerabilities were fixed, and the medium rank vulnerability appears to be a false positive. By making sure the operating system on my domain controller is completely up to date with all the latest patches, I was able to drastically reduce the number of vulnerabilities and increase its security posture.

