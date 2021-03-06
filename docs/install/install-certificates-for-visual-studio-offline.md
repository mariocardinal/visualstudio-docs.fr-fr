---
title: Install certificates needed for Visual Studio offline installation | Microsoft Docs
description: Describes the steps needed to install certificates for a Visual Studio offline installation
ms.date: 08/30/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 13659103061c6054698f4579b4b71d2669d2356d
ms.openlocfilehash: cc1f85852c8e00f2121bc9a68973bdbc35f5f1d5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/07/2017

---
# <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Install certificates needed for Visual Studio offline installation

Visual Studio is primarily designed to be installed on an internet-connected machine, since many components are updated regularly. However, with some extra steps, it's possible to deploy Visual Studio in an environment where a working internet connection is unavailable.

The Visual Studio setup engine installs only content that is trusted. It does this by checking Authenticode signatures of the content being downloaded and verifying that all content is trusted before installing it. This keeps your environment safe from attacks where the download location is compromised. Visual Studio setup therefore requires that several standard Microsoft root and intermediate certificates are installed and up-to- date on a user's machine. If the machine has been kept up to date with Windows Update, signing certificates usually are up to date. If the machine is connected to the internet, during installation Visual Studio may refresh certificates as necessary to verify file signatures. If the machine is offline, the certificates must be refreshed another way.

## <a name="how-to-refresh-certificates-when-offline"></a>How to refresh certificates when offline

There are three options for installing or updating certificates in an offline environment.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Option 1 - Manually install certificates from a layout folder

When you create a network layout, the necessary certificates are downloaded to the Certificates folder. You can then manually install the certificates by double-clicking each of the certificate files, and then clicking through the Certificate Manager wizard. If asked for a password, leave it blank.

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Option 2 - Distribute trusted root certificates in an enterprise environment

For enterprises with offline machines that do not have the latest root certificates, an administrator can use the instructions on the [Configure Trusted Roots and Disallowed Certificates](https://technet.microsoft.com/library/dn265983.aspx) page to update them.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Option 3 - Install certificates as part of a scripted deployment of Visual Studio

If you are scripting the deployment of Visual Studio in an offline environment to client workstations, you should follow these steps:

1. Copy the [Certificate Manager Tool](https://msdn.microsoft.com/library/e78byta0.aspx) (certmgr.exe) to the installation share (for example, \\server\share\vs2017). Certmgr.exe is not included as part of Windows itself, but is available as part of the [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Create a batch file with the following commands:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

3. Deploy the batch file to the client. This command should be run from an elevated process.

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>What are the certificates files in the Certificates folder?

The three .P12 files in this folder each contain an intermediate certificate and a root certificate. Most systems that are current with Windows Update have these certificates already installed.

* **ManifestSignCertificates.p12** contains:
    * Intermediate certificate: **Microsoft Code Signing PCA 2011**
        * Not required. Improves performance in some scenarios if present.
    * Root certificate: **Microsoft Root Certificate Authority 2011**
        * Required on Windows 7 Service Pack 1 systems that do not have the latest Windows Updates installed.
* **ManifestCounterSignCertificates.p12** contains:
    * Intermediate certificate: **Microsoft Time-Stamp PCA 2010**
        * Not required. Improves performance in some scenarios if present.
    * Root certificate: **Microsoft Root Certificate Authority 2010**
        * Required for Windows 7 Service Pack 1 systems that do not have the latest Windows Updates installed.
* **Vs_installer_opc.SignCertificates.p12** contains:
    * Intermediate certificate: **Microsoft Code Signing PCA**
        * Required for all systems. Note that systems with all updates applied from Windows Update might not have this certificate.
    * Root certificate: **Microsoft Root Certificate Authority**
        * Required. This certificate ships with systems running Windows 7 or later.

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Why are the certificates from the Certificates folder not installed automatically?

When a signature is verified in an online environment, Windows APIs are used to download and add the certificates to the system. Verification that the certificate is trusted and allowed via administrative settings occurs during this process. This verification process cannot occur in most offline environments. Installing the certificates manually allows enterprise administrators to ensure the certificates are trusted and meet the security policy of their organization.

## <a name="checking-if-certificates-are-already-installed"></a>Checking if certificates are already installed

One way to check on the installing system is to follow these steps:
1. Run **mmc.exe**.<br/>
  a. Click File, and then select **Add/Remove Snap-in**.<br/>
  b. Double-click **Certificates**, select **Computer account**, and then click **Next**.<br/>
  c. Select **Local computer**, click **Finish**, and then click **OK**.<br/>
  d. Expand **Certificates (Local Computer)**.<br/>
  e. Expand **Trusted Root Certification Authorities**, and then select **Certificates**.<br/>
    * Check this list for the necessary root certificates.<br/>
  
   f. Expand **Intermediate Certification Authorities**, and then select **Certificates**.<br/>
    * Check this list for the required intermediate certificates.<br/>

2. Click File and select **Add/Remove Snap-in**.<br/>
  a. Double-click **Certificates**, select **My user account**, click **Finish**, and then click **OK**.<br/>
  b. Expand **Certificates – Current User**.<br/>
  c. Expand **Intermediate Certification Authorities**, and then select **Certificates**.<br/>
    * Check this list for the required intermediate certificates.<br/>

If the certificates names were not in the **Issued To** columns, they must be installed.  If an intermediate certificate was only in the **Current User** Intermediate Certificate store, then it is available only to the user that is logged in. You might need to install it for other users.

## <a name="install-visual-studio"></a>Install Visual Studio

After you install the certificates, deployment of Visual Studio can proceed by using the instructions from the [Deploying from a network installation](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation) section of the "Create a network installation of Visual Studio" page.

## <a name="see-also"></a>See also
* [Install Visual Studio](install-visual-studio.md)
* [Visual Studio administrator guide](visual-studio-administrator-guide.md)
* [Use command-line parameters to install Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio workload and component IDs](workload-and-component-ids.md)

