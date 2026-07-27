# Lab 02: Endpoint Security

## Estimated Duration: 60 Minutes

## Exercise Overview
Contoso uses Microsoft Intune to manage its devices. A company-wide infrastructure analysis revealed that existing policies were created independently, making them difficult to view holistically. As the cyber security architect, you have decided to consolidate critical configurations using endpoint security baselines. Additionally, with the upcoming merger with Tailwind Traders, which uses macOS devices, you need to prepare the Contoso tenant for new macOS devices.

## Exercise Objectives

After completing this exercise, you'll be able to:

- Deploy endpoint security baseline policies for Windows devices
- Deploy antivirus protection for macOS devices.
- Configure disk encryption (FileVault) for macOS devices

## Architecture Diagram

 ![](../media/lab4/lab4ex3.png)

## Explanation of Components

The architecture for this lab involves the following key components:

- **Endpoint Security Baseline Policy Deployment**: Configures and deploys security baseline policies to ensure consistent security configurations across organizational endpoints.

- **Antivirus Deployment on macOS Devices**: Installs and configures antivirus software on macOS devices to provide real-time protection against malware and security threats.

- **macOS Device Encryption**: Encrypts macOS devices to protect sensitive data and ensure that information remains secure in the event of device loss or theft.

## Task 1: Deploy endpoint security baseline policies

In this task, you will create **endpoint security baseline policies** for **Windows devices** in **Intune** to secure your endpoints and consolidate multiple policies in one place.

1. Sign-in to the Microsoft Intune admin center **`https://intune.microsoft.com`** as :
   
    - **Email/Username:** **<inject key="AzureAdUserEmail"></inject>**  
    - **Password:** <inject key="AzureAdUserPassword"></inject>

1. In the Microsoft Intune admin center, in the left navigation pane select **Endpoint Security (1)**.

1. On the **Endpoint security | Overview** page, under **Overview** select **Security baselines (2)**.

1. On the **Endpoint security | Security baselines** page select **Security Baseline for Windows 10 and later (3)**.

    ![](../media/lab4/s1.png)

1. On the **Security Baseline for Windows 10 and later | Profiles** page select **+ Create profile**.

     ![](../media/lab4/s2.png)

1. Review the description on the **Create a profile** blade and select **Create**.

     ![](../media/lab4/s3.png)

1. On the **Basics** blade enter:
    
    - Name: **`Secure Windows Endpoints` (1)**
    
    - Description: **`The Security Baseline for Windows 10 and later represents the recommendations for configuring Windows.` (2)**.

1. Select **Next (3)**.

     ![](../media/lab4/s4.png)

1. On the **Configuration settings** blade investigate the different configuration options. When you have finished, select **Next**.

     ![](../media/lab4/s5.png)

1. On the **Scope tags** blade select **Next**.

     ![](../media/lab4/s6.png)

1. On the **Assignments** blade under **Included groups** select **Add all users (1)** and select **Next (2)**.

     ![](../media/lab4/s7.png)

1. On the **Review + create** blade select **Create**.

     ![](../media/lab4/s8n.png)

1. Go back to **Endpoint security | Security baselines** page.

1. On the **Endpoint security | Security baselines (1)** page select **Microsoft Defender for Endpoint Security Baseline (2)**.

    ![](../media/lab4/s9.png)

1. On the **Microsoft Defender for Endpoint Security baseline | Profiles** select **+ Create profile**.

     ![](../media/lab4/s10.png)

1. Review the description on the **Create a profile** blade and select **Create**.

     ![](../media/lab4/s11.png)

1. On the **Basics** blade enter:
    
    - Name: **`Defender for Endpoint Security Baseline` (1)**
    
    - Description: **`Security best practices for the Microsoft security stack on devices managed by Intune` (2)**.

1. Select **Next (3)**.

     ![](../media/lab4/s12.png)

1. On the **Configuration settings** blade investigate the different configuration options. When you have finished, select **Next**.

     ![](../media/lab4/s13.png)

1. On the **Scope tags** blade select **Next**.

     ![](../media/lab4/s14.png)

1. On the **Assignments** blade, under **Included groups** select **Add all users (1)** and select **Next (2)**.

     ![](../media/lab4/s15.png)

1. On the **Review + create** blade select **Create**.

     ![](../media/lab4/s16.png)

    >**Success!** You have successfully created two security baseline policies for Windows devices.

## Task 2: Deploy antivirus on macOS devices

In this task, after securing **Windows devices** with endpoint security baseline policies, you will deploy **antivirus** and enable **encryption** on **macOS devices** to prepare your environment for merging with **Tailwind Traders**.

1. You should still be logged into the Microsoft Intune admin center **https://intune.microsoft.com**.

1. In the Microsoft Intune admin center, in the left navigation pane select **Endpoint Security (1)**.

1. On the **Endpoint security | Overview** page under **Manage** select **Antivirus (2)**.

1. On the **Endpoint security | Antivirus** page select **+ Create policy (3)**.

     ![](../media/lab4/s17.png)

1. On the **Create a profile** pane, under **Platform** select **macOS (1)** and under **Profile** select **Microsoft Defender Antivirus (2)**.

1. Select **Create (3)**.

     ![](../media/lab4/s18.png)

1. On the **Basics** blade enter:
    
    - Name: **`Deploy antivirus on macOS devices` (1)**
    
    - Description: **`Deploy antivirus and enable encryption on macOS devices to prepare your environment for merging with Tailwind Traders.` (2)**

1. Select **Next (3)**

     ![](../media/lab4/s19.png)

1. On the **Configuration settings** tab ensure the settings are configured as follows:

1. Under **Cloud delivered protection preferences (1)**:
    
    - Enable / disable cloud delivered protection: **Enabled (Default) (2)**
    - Enable/ disable automatic sample submissions: **Enabled (Default) (3)**
    - Diagnostic collection level: **optional (Default) (4)**
    - Automatic security intelligence update: **Enabled (Default) (5)**

      ![](../media/lab4/s20.png)

1. Under **Antivirus engine (1)**:
    
    - Enable real-time protecion: **Enabled (Default) (2)**
    - Enable passive mode: **Disabled (Default) (3)**
    - Exclusion merge: **admin_only (4)**

      ![](../media/lab4/s21.png)

1. Under **Threat type settings** select **+ Add**:
    
    - In the text box for Threat type, ensure **potentially_unwanted_application (1)** is selected.
    - Action to take: **block (2)**
    - Threat type settings merge: **admin_only (3)**

      ![](../media/lab4/s22.png)

      ![](../media/lab4/s23.png)

1. Enable file hash computation: **True (1)**

1. Run a scan after definitions are updated: **Enabled (Default) (2)**

1. Enforcement level: **real_time (Default) (3)**

    ![](../media/lab4/s24.png)

1. Under **Network protection (1)**:
    
    - Enforcement level: **block (2)**

     ![](../media/lab4/s25.png)

1. Under **Tamper protection (1)**:
    
    - Enforcement level: **block (Default) (2)**

      ![](../media/lab4/s26.png)

1. Under **User interface preferences**
    
    - Control sign-in to consumer version: **enabled (Default) (1)**
    - Show / hide status menu icon: **Disabled (Default) (2)**
    - User initiated feedback: **enabled (Default) (3)**

1. Select **Next (4)**.

     ![](../media/lab4/s27.png)

1. On the **Scope tags** blade select **Next**.

    ![](../media/lab4/s28.png)

1. On the **Assignments** tab, in the text box 
enter **All users (1)** and select it **(2)**.

1. Select **Next (3)**.

     ![](../media/lab4/s29.png)

1. On the **Review + create** tab select **Create**.

      ![](../media/lab4/s30.png)

   >**Success!** You have successfully configured and deployed antivirus for macOS devices.

## Task 3: Encrypt macOS devices

In this task you will encrypt macOS devices.

1. In the Microsoft Intune admin center, in the left navigation pane select **Endpoint Security (1)**.

1. On the **Endpoint security | Overview** page, under **Manage** select **Disk encryption (2)**.

1. On the **Endpoint security | Disk encryption** page select **+ Create Policy (3)**.

     ![](../media/lab4/s31.png)

1. On the **Create a profile** pane, under **Platform** select **macOS (1)** and under **Profile** select **FileVault (2)**.

1. Select **Create (3)**.

    ![](../media/lab4/s32.png)

1. On the **Basic** blade enter:
    
    - Name: **`Encrypt macOS devices` (1)**
    - Description: **`FileVault provides built-in Full Disk Encryption for macOS devices.` (2)**
    - Select **Next (3)**.

      ![](../media/lab4/s33.png)

1. On the **Configuration settings** expand **Full Disk Encryption (1)** configure the following settings:
   
    - Defer: **Enabled (2)**
    - Defer Don't ask At User Logout: **Enabled (3)**.
    - Defer Force at User Login Max Bypass Attempts: set slider to **Configured (4)** then enter **3 (5)** in the field that follows.
    - Enable FileVault: **On (6)**
    - Personal recovery key rotation: **6 months (7)**
    - Under FileVault Recovery Key Escrow, in the location field enter: **`To recover a lost or recently rotated recovery key, log in to the Intune Company Portal website using any device. Navigate to the Devices section within the portal, choose the device with FileVault enabled, and then select the option to retrieve the recovery key. The portal will display the current recovery key for that device.` (8)** 
    - Select **Next (9)**.   
    
      ![](../media/lab4/s34.png)

      ![](../media/lab4/s35n.png)

1. On the **Scope tags** blade select **Next**.

     ![](../media/lab4/s36.png)

1. On the **Assignments** blade, under **Included groups** select **Add all users (1)** then select **Next (2)**.

     ![](../media/lab4/s37.png)

1. On the **Review + create** blade select **Create**.

    ![](../media/lab4/s38.png)

    >**Success!** You have successfully configured and deployed a FileVault profile to encrypt macOS devices.

### Summary

In this exercise, you have completed the following:
- Deployed endpoint security baseline policies.
- Deployed antivirus on macOS devices.
- Encrypted macOS devices.

### You have successfully completed the lab.
