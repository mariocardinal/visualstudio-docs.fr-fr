---
title: IDiaSourceFile::get_checksum | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2bcfbc701f6f4799a51d09fac4c4eb184e6f5d7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
Récupère les octets de la somme de contrôle.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cbData`  
 [in] Taille de la mémoire tampon de données, en octets.  
  
 `pcbData`  
 [out] Retourne le nombre d’octets de la somme de contrôle. Ce paramètre ne peut pas être `NULL`.  
  
 `data`  
 [dans, out] Une mémoire tampon est remplie avec les octets de la somme de contrôle. Si ce paramètre est `NULL`, puis `pcbData` retourne le nombre d’octets requis.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Pour déterminer le type d’algorithme de somme de contrôle qui a été utilisé pour générer les octets de la somme de contrôle, appelez le [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) (méthode).  
  
 La somme de contrôle est généralement générée à partir de l’image du fichier source pour les modifications dans le fichier source sont reflétées dans les modifications effectuées dans les octets de la somme de contrôle. Si les octets de la somme de contrôle ne correspondent pas généré à partir de l’image chargée du fichier, puis le fichier doit être considérée comme une somme de contrôle endommagés ou falsifiés.  
  
 Les sommes de contrôle standards ne sont jamais plus de 32 octets de taille mais ne supposent pas qui est la taille maximale d’une somme de contrôle. Définir le `data` paramètre `NULL` pour obtenir le nombre d’octets requis pour récupérer la somme de contrôle. Allouer une mémoire tampon de la taille appropriée, puis appelez cette méthode une fois de plus, avec la nouvelle mémoire tampon.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)