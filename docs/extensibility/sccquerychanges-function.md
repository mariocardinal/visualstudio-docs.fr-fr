---
title: Fonction de SccQueryChanges | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccQueryChanges
helpviewer_keywords: SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 589013b996f9ed018e28292a27c6a760eef1dae7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sccquerychanges-function"></a>SccQueryChanges (fonction)
Cette fonction énumère une liste donnée de fichiers, en fournissant des informations sur la modification du nom de chaque fichier via une fonction de rappel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte plug-in de contrôle de code source.  
  
 nFiles  
 [in] Nombre de fichiers dans `lpFileNames` tableau.  
  
 lpFileNames  
 [in] Tableau des noms de fichiers pour obtenir des informations.  
  
 pfnCallback  
 [in] Fonction de rappel à appeler pour chaque nom de fichier dans la liste (voir [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) pour plus d’informations).  
  
 pvCallerData  
 [in] Valeur qui sera transmis sans modification à la fonction de rappel.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Le processus de requête s’est terminé correctement.|  
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert dans le contrôle de code source.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|  
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée ou générale s’est produite.|  
  
## <a name="remarks"></a>Remarques  
 Les modifications demandées sont à l’espace de noms : en particulier, changement de nom, l’ajout et suppression d’un fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Codes d’erreur](../extensibility/error-codes.md)