---
title: "Outils de détection et de gestion des instances de Visual Studio | Microsoft Docs"
description: "{{ESPACE RÉSERVÉ}}"
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 1e81071d8a67fd5b8c38bcf87629604efe6fa4a5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---

# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Outils de détection et de gestion des instances de Visual Studio

## <a name="detecting-existing-visual-studio-instances"></a>Détection des instances existantes de Visual Studio
Nous avons mis à disposition plusieurs outils qui vous aideront à détecter et à gérer les instances de Visual Studio installées sur les ordinateurs clients :

* [VSWhere](https://github.com/microsoft/vswhere) : fichier exécutable intégré à Visual Studio ou disponible dans le cadre d’une distribution distincte qui vous permet de trouver l’emplacement de toutes les instances de Visual Studio sur un ordinateur particulier.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell) : scripts PowerShell qui utilisent l’API de configuration de l’installation pour identifier les instances installées de Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples) : exemples C# et C++ qui montrent comment utiliser l’API de configuration de l’installation pour interroger une installation existante.

De plus, l’[API de configuration de l’installation](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) fournit des interfaces destinées aux développeurs qui veulent créer leurs propres utilitaires d’interrogation des instances de Visual Studio.

## <a name="using-vswhereexe"></a>Utilisation de vswhere.exe
`vswhere.exe` est inclus automatiquement dans Visual Studio 2017 version 15.2 ou supérieure, ou vous pouvez le télécharger à partir de la [page des versions Release](https://github.com/Microsoft/vswhere/releases). Utilisez `vswhere -?` pour obtenir des informations d’aide sur l’outil. Par exemple, cette commande affiche toutes les versions Release de Visual Studio, y compris les anciennes versions du produit et les préversions, et renvoie les résultats au format JSON :

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

>[!TIP]
>Pour plus d’informations sur l’installation de Visual Studio 2017, consultez les [articles de blog de Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Modification du Registre pour une instance de Visual Studio
Dans Visual Studio 2017, les paramètres du Registre sont stockés à un emplacement privé, ce qui active plusieurs instances côte à côte de la même version de Visual Studio sur le même ordinateur.

Comme ces entrées ne sont pas stockées dans le Registre global, il existe des instructions spéciales pour l’utilisation de l’Éditeur du Registre afin d’apporter des modifications aux paramètres du Registre :

1. Si vous avez une instance de Visual Studio 2017 ouverte, fermez-la.
2. Démarrez `regedit.exe`.
3. Sélectionnez le nœud `HKEY_LOCAL_MACHINE`.
4. Dans le menu principal Regedit, sélectionnez **Fichier -> Charger la ruche...**, puis sélectionnez le fichier de Registre privé qui est stocké dans le dossier **AppData\Local**. Exemple :
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>` correspond à l’instance de Visual Studio que vous souhaitez parcourir.

Vous êtes invité à fournir un nom de ruche, qui devient le nom de votre ruche isolée. Après cela, vous devez être en mesure de parcourir le Registre sous la ruche isolée que vous avez créée.

> [!IMPORTANT]
> Avant de redémarrer Visual Studio, vous devez décharger la ruche isolée que vous avez créée. Pour ce faire, sélectionnez Fichier -> Décharger la ruche dans le menu principal Regedit. (Si vous ne le faites pas, le fichier reste verrouillé et Visual Studio n’est pas en mesure de démarrer.)

