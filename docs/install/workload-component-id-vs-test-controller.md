---
title: Visual Studio Test Controller 2017 workload and component IDs | Microsoft Docs
description: Use Visual Studio workload and component IDs to distribute automated tests to multiple machines
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 08/30/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: fbbda9c8-d2c6-474d-b52d-a95227d52fe7
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 96018963278cd1d53b226473baade41da1e98111
ms.openlocfilehash: 4af6768bbb9f3e4e494ea85596a9706103537824
ms.contentlocale: fr-fr
ms.lasthandoff: 08/30/2017

---

# <a name="visual-studio-test-controller-2017-component-directory"></a>Visual Studio Test Controller 2017 component directory

The tables on this page list the IDs that you can use to install Visual Studio by using the command line. Note that we will add additional components as we release updates to Visual Studio.

Also note the following about the page:

* Each workload has its own section, followed by the workload ID and a table of the components that are available for the workload.
* By default, the **Required** components will be installed when you install the workload. If you choose to, you can also install the **Recommended** and **Optional** components.
* We've also added a section that lists the additional components that are not affiliated with any workload.

For more information about how to use these IDs, see [Use Command-Line Parameters to Install Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) page. And, for a list of workload and component IDs for other products, see [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) page.

## <a name="test-controller"></a>Test Controller

**ID:** Microsoft.VisualStudio.Workload.TestController

**Description:** Distribute automated tests to multiple machines

### <a name="components-included-by-this-workload"></a>Components included by this workload

Component ID | Name | Version | Dependency type
--- | --- | --- | ---
Microsoft.VisualStudio.ComponentGroup.TestTools.TestController | Test Controller core features | 15.0.26711.1 | Required

## <a name="unaffiliated-components"></a>Unaffiliated components

These are components that are not included with any workload, but may be selected as an individual component.

Component ID | Name | Version
--- | --- | ---
n/a | n/a | n/a

## <a name="see-also"></a>See also

* [Visual Studio workload and component IDs](workload-and-component-ids.md)
* [Visual Studio administrator guide](visual-studio-administrator-guide.md)
* [Use command-line parameters to install Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Command-line parameter examples](command-line-parameter-examples.md)
* [Create an offline installation of Visual Studio](create-an-offline-installation-of-visual-studio.md)
