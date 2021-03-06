---
title: "Contrôler les mises à jour applicables aux déploiements de Visual Studio | Microsoft Docs"
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
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 7267b279a94094eb58fe51edd1ad36cd8967c711
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau

Les administrateurs d’entreprise créent souvent une disposition qu’ils hébergent sur un partage de fichiers réseau en vue d’un déploiement pour les utilisateurs finaux.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Contrôle de l’emplacement où Visual Studio recherche des mises à jour
Par défaut, Visual Studio continue de rechercher en ligne des mises à jour même si l’installation a été déployée à partir d’un partage réseau. Si une mise à jour est disponible, l’utilisateur peut l’installer. Tout contenu mis à jour qui ne se trouve pas dans la disposition en mode hors connexion est téléchargée à partir du web.

Si vous souhaitez un contrôle direct sur l’emplacement où Visual Studio recherche les mises à jour, vous pouvez changer l’emplacement où il effectue sa recherche. Vous pouvez également déterminer la version avec laquelle vos utilisateurs sont mis à jour. Pour cela, suivez ces étapes :

 1. Créez une disposition en mode hors connexion :
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. Copiez-la dans le partage de fichiers dans lequel vous souhaitez l’héberger :
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. Modifiez le fichier response.json dans la disposition et modifiez la valeur `channelUri` pour qu’elle pointe vers une copie de channelManifest.json que contrôle l’administrateur.

  Veillez à placer une séquence d’échappement avec les barres obliques inverses dans la valeur, comme dans l’exemple suivant :

  ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
  ```

 Les utilisateurs finaux peuvent maintenant exécuter le programme d’installation à partir de ce partage pour installer Visual Studio.
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```

Quand un administrateur d’entreprise détermine que le moment est venu pour les utilisateurs d’effectuer une mise à jour vers une version plus récente de Visual Studio, il peut [mettre à jour l’emplacement de la disposition](update-a-network-installation-of-visual-studio.md) pour intégrer les fichiers mis à jour, comme suit.

 1. Utilisez une commande semblable à la commande suivante :
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 2. Vérifiez que le fichier response.json de la disposition mise à jour contient toujours vos personnalisations, en particulier la modification de channelUri, comme suit :
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 Les installations existantes de Visual Studio à partir de cette disposition recherchent les mises à jour sur `\\server\share\VS2017\ChannelManifest.json`. Si le fichier channelManifest.json est plus récent que celui que l’utilisateur a installé, Visual Studio informe l’utilisateur qu’une mise à jour est disponible.

 Les nouvelles installations installent automatiquement la version mise à jour de Visual Studio, directement à partir de la disposition.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Contrôle des notifications dans l’IDE de Visual Studio
Comme décrit plus haut, Visual Studio vérifie l’emplacement à partir duquel il a été installé, tel qu’un partage réseau ou via Internet, pour voir si des mises à jour sont disponibles. Quand une mise à jour est disponible, Visual Studio avertit l’utilisateur au moyen d’un indicateur de notification affiché en haut à droite de la fenêtre.

 ![Indicateur de notification des mises à jour](media/notification-flag.png)

Vous pouvez désactiver les notifications si vous ne souhaitez pas que les utilisateurs finaux soient avertis des mises à jour. (Par exemple, si vous fournissez des mises à jour via un mécanisme de distribution de logiciels central.)

Comme Visual Studio 2017 [stocke les entrées de Registre dans un Registre privé](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), vous ne pouvez pas modifier directement le Registre de la façon habituelle. Toutefois, Visual Studio comprend un utilitaire `vsregedit.exe` que vous pouvez utiliser pour modifier les paramètres de Visual Studio. Vous pouvez désactiver les notifications avec la commande suivante :

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0 
```
(Veillez à remplacer le répertoire pour faire correspondre l’instance installée que vous souhaitez modifier.)

> [!TIP]
> Utilisez [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) pour rechercher une instance spécifique de Visual Studio sur une station de travail cliente.

## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Outils de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)

