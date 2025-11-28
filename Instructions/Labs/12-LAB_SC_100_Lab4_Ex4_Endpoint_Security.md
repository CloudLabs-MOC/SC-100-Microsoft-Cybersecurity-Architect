# Lab 02: Endpoint Security

## Exercise Overview
Contoso uses Microsoft Intune to manage its devices and provides its employees with Windows 10 and Windows 11 devices. The company has implemented several configuration profiles in the past. However, a company-wide infrastructure analysis revealed that the existing policies were created independently, making it difficult to view them holistically and trace them. As the company's cyber security architect, you have decided to consolidate all the necessary and critical configurations in one place. 

In addition, the analysis revealed that Tailwind Traders uses macOS devices in its environment. As part of the upcoming merger, you plan to prepare the Contoso tenant for the new macOS devices.

## Exercise Objectives

After completing this exercise, you'll be able to:

- Deploy endpoint security baseline policies to strengthen device security.
- Deploy antivirus software on macOS devices to protect against threats.
- Encrypt macOS devices to ensure data security and compliance.


## Estimated Duration: 60 Minutes

## Architecture Diagram

 ![](../media/lab4/lab4ex3.png)

## Explanation of Components

The architecture for this lab involves the following key components:

- **Endpoint Security Baseline Policy Deployment**: Configures and deploys security baseline policies to ensure consistent security configurations across organizational endpoints.

- **Antivirus Deployment on macOS Devices**: Installs and configures antivirus software on macOS devices to provide real-time protection against malware and security threats.

- **macOS Device Encryption**: Encrypts macOS devices to protect sensitive data and ensure that information remains secure in the event of device loss or theft.

## Part 1: Design a solution

### Design Approach

In the given scenario, the following requirements can be outlined:

- Consolidate all configurations for Windows devices in one place
- Protect MacOS devices

Microsoft Endpoint Manager, with security baselines, centrally manages and secures endpoints, including desktops, laptops, mobile devices, and servers. It integrates tools like Intune and Configuration Manager, enabling efficient deployment of applications, policy enforcement, compliance, and device monitoring. 

A security baseline policy comprises a set of configuration settings recommended by Microsoft, detailing their security implications. These settings are formulated based on input from Microsoft security engineering teams, product groups, partners, and customers. These baselines encompass device configuration settings similar to those within various Intune policies. Customizing each deployed baseline enables the enforcement of necessary settings and values. When establishing a security baseline profile within Intune, you're essentially creating a template comprising multiple device configuration profiles. These recommendations must be regularly reviewed and adapted according to the respective business requirements.

### Proposed Solution

|Requirement|Solution|Action plan|
|----|----|----|
|Consolidate all configurations for Windows devices in one place|Microsoft Endpoint Manager - Endpoint Security|Deploy security baseline policies
|Protect MacOS devices|Microsft Endpoint Manager|Deploy antivirus on macOS devices|

## Part 2: Implement the solution 

### Task 1: Deploy endpoint security baseline policies

In this task, you will create **endpoint security baseline policies** for **Windows devices** in **Intune** to secure your endpoints and consolidate multiple policies in one place.

1. Log into the  VM **LON-SC1** with the local **Administrator** account. The password should be provided by your lab hosting provider.

1. Sign-in to the Microsoft Intune admin center **`https://intune.microsoft.com`** as :

    - **Email/Username:** **<inject key="AzureAdUserEmail"></inject>**  
    - **Password:** <inject key="AzureAdUserPassword"></inject>

1. If you see an information box on the top right of the screen that says **Manage multifactor authentication**, close it by selecting the **X**.

1. In the Microsoft Intune admin center, in the left navigation pane select **Endpoint Security** (1).

1. On the **Endpoint security | Overview** page, under **Overview** select **Security baselines** (2).

1. On the **Endpoint security | Security baselines** page select **Security Baseline for Windows 10 and later** (3).

   ![](../media/lab4/essb.png)

1. On the **Security Baseline for Windows 10 and later | Profiles** page select **+ Create policy** (1).

1. Review the description on the **Create a profile** blade and select **Create** (2).

    ![](../media/lab4/cpw.png)

1. On the **Basics** blade enter:

    - Name: **`Secure Windows Endpoints`** (1)

    - Description: **`The Security Baseline for Windows 10 and later represents the recommendations for configuring Windows.`** (2).

1. Select **Next** (3).

    ![](../media/lab4/basicblade.png)

1. On the **Configuration settings** blade investigate the different configuration options. When you have finished, select **Next**.

    ![](../media/lab4/configw.png)

1. On the **Scope tags** blade select **Next**.

1. On the **Assignments** blade under **Included groups** select **Add all users** (1) and select **Next** (2).

    ![](../media/lab4/addallu.png)

1. On the **Review + create** blade select **Create**.

    ![](../media/lab4/rcc.png)

1. Go back to **Endpoint security | Security baselines** page.

1. On the **Endpoint security | Security baselines** (1) page select **Microsoft Defender for Endpoint Security Baseline** (2).

   ![](../media/lab4/sbdf.png)

1. On the **Microsoft Defender for Endpoint Security baseline | Profiles** select **+ Create policy** (1).

1. Review the description on the **Create a profile** blade and select **Create** (2).

    ![](../media/lab4/cpdef.png)

1. On the **Basics** blade enter:
    - Name: **`Defender for Endpoint Security Baseline`** (1)
    - Description: **`Security best practices for the Microsoft security stack on devices managed by Intune.`** (2)

1. Select **Next** (3).

    ![](../media/lab4/defbasic.png)

1. On the **Configuration settings** blade investigate the different configuration options. When you have finished, select **Next**.

    ![](../media/lab4/condefnxt.png)

1. On the **Scope tags** blade select **Next**.

1. On the **Assignments** blade, under **Included groups** select **Add all users** (1) and select **Next** (2).

    ![](../media/lab4/alldef.png)

1. On the **Review + create** blade select **Create**.

    ![](../media/lab4/rcdef.png)

   >**Success!** You have successfully created two security baseline policies for Windows devices.

### Task 2: Deploy antivirus on macOS devices

In this task, after securing **Windows devices** with endpoint security baseline policies, you will deploy **antivirus** and enable **encryption** on **macOS devices** to prepare your environment for merging with **Tailwind Traders**.

1. You should still be logged into the Microsoft Intune admin center **https://intune.microsoft.com**.

1. In the Microsoft Intune admin center, in the left navigation pane select **Endpoint Security** (1).

1. On the **Endpoint security | Overview** page under **Manage** (2) select **Antivirus** (3).

1. On the **Endpoint security | Antivirus** page select **+ Create policy** (4).

1. On the **Create a profile** pane, under **Platform** select **macOS** (5) and under **Profile** select **Microsoft Defender Antivirus** (6).

1. Select **Create** (7).

    ![](../media/lab4/mcav.png)

1. On the **Basics** blade enter:

    - Name: **`Deploy antivirus on macOS devices`** (1)
    
    - Description: **`Deploy antivirus and enable encryption on macOS devices to prepare your environment for merging with Tailwind Traders.`** (2)

1. Select **Next** (3).

    ![](../media/lab4/avbas.png)

1. On the **Configuration settings** tab ensure the settings are configured as follows:

1. Under **Cloud delivered protection preferences**:
    - Enable / disable cloud delivered protection: **Enabled (Default) (1)**
    - Enable/ disable automatic sample submissions: **Enabled (Default) (2)**
    - Diagnostic collection level: **optional (Default) (3)**
    - Automatic security intelligence update: **Enabled (Default) (4)**

      ![](../media/lab4/cdpp.png)

1. Under **Antivirus engine**:
    - Enable real-time protecion: **Enabled (Default) (1)**
    - Enable passive mode: **Disabled (Default) (2)**
    - Exclusion merge: **admin_only (3)**

        ![](../media/lab4/aven.png)

1. Under **Threat type settings** select **+ Add** (1):
    - In the text box for Threat type, ensure **potentially_unwanted_application** (2) is selected.
    - Action to take: **block** (3)
    - Threat type settings merge: **admin_only** (4)

        ![](../media/lab4/tts.png)

1. Enable file hash computation: **True** (1)

1. Run a scan after definitions are updated: **Enabled (Default)** (2)

1. Enforcement level: **real_time (Default)** (3)

    ![](../media/lab4/fhash.png)

1. Under **Network protection**:
    - Enforcement level: **block** (1)

1. Under **Tamper protection**:
    - Enforcement level: **block (Default)** (2)

1. Select **Next** (3).

    ![](../media/lab4/nptp.png)

1. On the **Scope tags** blade select **Next**.

1. On the **Assignments** tab, in the text box 
enter **All users** (1) and select **All users** (2)

1. Select **Next** (3).

    ![](../media/lab4/allav.png)

1. On the **Review + create** tab select **Save**.

    ![](../media/lab4/avdone3.png)

    >**Success!** You have successfully configured and deployed antivirus for macOS devices.

### Task 3: Encrypt macOS devices

In this task you will encrypt macOS devices.

1. In the Microsoft Intune admin center, in the left navigation pane select **Endpoint Security** (1).

1. On the **Endpoint security | Overview** page, under **Manage** (2) select **Disk encryption** (3).

1. On the **Endpoint security | Disk encryption** page select **+ Create Policy** (4).

1. On the **Create a profile** pane, under **Platform** select **macOS** (5) and under **Profile** select **MacOS Filevault** (6).

1. Select **Create** (7).

    ![](../media/lab4/esde.png)

1. On the **Basic** blade enter:

    - Name: **`Encrypt macOS devices`** (1)
    - Description: **`FileVault provides built-in Full Disk Encryption for macOS devices.`** (2)
    - Select **Next**. (3)

    ![](../media/lab4/diskbasic.png)

1. On the **Configuration settings** blade under **Encryption** configure the following settings:

    - Escrow location description:  
  **`To recover a lost or recently rotated recovery key, log in to the Intune Company Portal website using any device. Navigate to the Devices section within the portal, choose the device with FileVault enabled, and then select the option to retrieve the recovery key.`** (1)

    - Defer: **Enabled** (2)

    - Defer Don’t Ask At User Logout: **Enabled** (3)

    - Defer Force At User Login Max Bypass Attempts: **Configured** (4)

    - Number of bypass attempts: **3** (5)

    - Enable FileVault: **On** (6)

    - Recovery Key Rotation in Months: **6 months** (7)

    - Use Recovery Key: **Enabled** (8)

    - Select **Next**. (9)

        ![](../media/lab4/diskconfig.png)

1. On the **Scope tags** blade select **Next**.

1. On the **Assignments** blade, under **Included groups** select **Add all users** (1) then select **Next** (2).

    ![](../media/lab4/diskusr.png)

1. On the **Review + create** blade select **Create**.

    ![](../media/lab4/diskdone.png)

   >**Success!** You have successfully configured and deployed a FileVault profile to encrypt macOS devices.

### Review

In this exercise, you have completed the following:
- Deployed endpoint security baseline policies.
- Deployed antivirus on macOS devices.
- Encrypted macOS devices.


### You have successfully completed the lab.
