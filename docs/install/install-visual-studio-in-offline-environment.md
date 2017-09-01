---
title: "Considérations particulières pour installer Visual Studio dans un environnement hors connexion | Microsoft Docs"
description: "{{ESPACE RÉSERVÉ}}"
ms.date: 08/14/2017
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
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 62fc2d38a628cfc28913a0a45e1e3cb5d3852330
ms.contentlocale: fr-fr
ms.lasthandoff: 08/14/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Considérations particulières pour installer Visual Studio dans un environnement hors connexion

Visual Studio est avant tout conçu pour être installé sur un ordinateur connecté à Internet, puisque de nombreux composants sont régulièrement mis à jour. Toutefois, en suivant quelques étapes supplémentaires, il est possible de déployer Visual Studio dans un environnement sans aucune connexion Internet disponible.

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Installer les certificats nécessaires pour l’installation hors connexion de Visual Studio
Le moteur d’installation de Visual Studio n’installe que le contenu approuvé. Pour cela, il contrôle les signatures Authenticode du contenu à télécharger et vérifie que tout le contenu est approuvé avant de l’installer. Cela permet de protéger votre environnement contre des attaques au cas où l’emplacement de téléchargement est compromis. Par conséquent, le programme d’installation de Visual Studio nécessite l’installation de plusieurs certificats standard racines et intermédiaires Microsoft à jour sur un ordinateur d’utilisateur. Si l’ordinateur est demeuré à jour par le biais de Windows Update, les certificats de signature sont automatiquement mis à jour et, lors de l’installation, Visual Studio actualise les certificats obligatoires pour vérifier les signatures des fichiers.

Pour une entreprise équipée d’ordinateurs hors connexion qui n’ont pas les derniers certificats racines, un administrateur peut utiliser les instructions de la page [Configurer les racines de confiance et les certificats non autorisés](https://technet.microsoft.com/en-us/library/dn265983.aspx) pour les mettre à jour. Sinon, lorsque vous créez une disposition réseau, les certificats nécessaires sont téléchargés dans le dossier `certificates`. Vous pouvez alors installer les certificats manuellement en double-cliquant sur chaque fichier de certificat et en suivant les étapes de l’Assistant du gestionnaire de certificats. Si le système vous demande un mot de passe, laissez-le vide.

Si vous écrivez un script du déploiement de Visual Studio dans un environnement hors connexion sur des postes de travail clients, vous devez suivre ces étapes :

1. Copiez l’[outil Gestionnaire de certificat](https://msdn.microsoft.com/en-us/library/e78byta0.aspx) (`certmgr.exe`) dans le partage d’installation (par exemple, `\\server\share\vs2017`). `certmgr.exe` n’est pas inclus dans le cadre de Windows lui-même, mais il est disponible dans le cadre du kit [SDK Windows](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk).

2. Créez un fichier de commandes avec les commandes suivantes :

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

3. Déployez le fichier de commandes sur le client. Cette commande doit être exécutée à partir d’un processus avec élévation de privilèges.

### <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Quels sont les fichiers de certificats dans le dossier `certificates` ?
Les trois fichiers `.p12` figurant dans ce dossier contiennent chacun un certificat intermédiaire et un certificat racine. La plupart des systèmes tenus à jour via Windows Update disposent déjà de ces certificats.

* `ManifestSignCertificates.p12` contient :
    * Certificat intermédiaire : **Microsoft Code Signing PCA 2011**
        * Non requis Le cas échéant, améliore les performances dans certains scénarios.
    * Certificat racine : **Microsoft Root Certificate Authority 2011**
        * Obligatoire sur les systèmes Windows 7 Service Pack 1 qui ne disposent pas des dernières mises à jour Windows.
* `ManifestCounterSignCertificates.p12`
    * Certificat intermédiaire : **Microsoft Time-Stamp PCA 2010**
        * Non requis Le cas échéant, améliore les performances dans certains scénarios.
    * Certificat racine : **Microsoft Root Certificate Authority 2010**
        * Obligatoire pour les systèmes Windows 7 Service Pack 1 qui ne disposent pas des dernières mises à jour Windows.
* `vs_installer_opc.SignCertificates.p12`
    * Certificat intermédiaire : **Microsoft Code Signing PCA**
        * Obligatoire pour tous les systèmes. Notez que les systèmes dotés de toutes les mises à jour appliquées à partir de Windows Update n’ont peut-être pas ce certificat.
    * Certificat racine : **Microsoft Root Certificate Authority**
        * Obligatoire. Ce certificat est fourni avec les systèmes exécutant Windows 7 ou version ultérieure.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Pourquoi est-ce que les certificats du dossier `certificates` ne sont pas installés automatiquement ?
Quand une signature est vérifiée dans un environnement en ligne, les API Windows sont utilisées pour télécharger les certificats et les ajouter au système. La vérification que le certificat est approuvé et autorisé via les paramètres d’administration se produit pendant ce processus. Ce processus de vérification ne peut pas se produire dans la plupart des environnements hors connexion. L’installation manuelle des certificats permet aux administrateurs d’entreprise de s’assurer que les certificats sont approuvés et conformes à la stratégie de sécurité de leur organisation.

### <a name="checking-if-certificates-are-already-installed"></a>Vérification de l’installation des certificats
Une manière de vérifier l’installation du système consiste à suivre ces étapes :
1. Exécutez `mmc.exe`.<br/>
  a. Cliquez sur Fichier et sélectionnez **Ajouter/Supprimer un composant logiciel enfichable**.<br/>
  b. Double-cliquez sur **Certificats**, sélectionnez **Compte d’ordinateur** et cliquez sur **Suivant**.<br/>
  c. Sélectionnez **Ordinateur local**, cliquez sur **Terminer**, puis sur **OK**.<br/>
  d. Développez **Certificats (ordinateur local)**.<br/>
  e. Développez **Autorités de certification racines de confiance** et sélectionnez **Certificats**.<br/>
    * Recherchez les certificats racines nécessaires dans cette liste.<br/>
  
   f. Développez **Autorités de certification intermédiaires** et sélectionnez **Certificats**.<br/>
    * Recherchez les certificats intermédiaires obligatoires dans cette liste.<br/>

2. Cliquez sur Fichier et sélectionnez **Ajouter/Supprimer un composant logiciel enfichable**.<br/>
  a. Double-cliquez sur **Certificats**, sélectionnez **Mon compte d’utilisateur**, cliquez sur **Terminer**, puis sur **OK**.<br/>
  b. Développez **Certificats – Utilisateur actuel**.<br/>
  c. Développez **Autorités de certification intermédiaires** et sélectionnez **Certificats**.<br/>
    * Recherchez les certificats intermédiaires obligatoires dans cette liste.<br/>

Si les noms des certificats ne figuraient pas dans les colonnes **Délivré à**, ils doivent être installés.  Si un certificat intermédiaire se trouvait uniquement dans le magasin de certificats intermédiaires de l’**Utilisateur actuel**, il n’est donc disponible que pour l’utilisateur connecté et vous devrez peut-être l’installer pour d’autres utilisateurs.

## <a name="install-visual-studio"></a>Installer Visual Studio
Après avoir installé les certificats, le déploiement de Visual Studio peut se poursuivre en mode hors connexion, sans étapes spéciales supplémentaires, en suivant les instructions de la section [Déploiement à partir d’une installation réseau]((create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation) dans la page « Créer une installation réseau de Visual Studio ».


## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
