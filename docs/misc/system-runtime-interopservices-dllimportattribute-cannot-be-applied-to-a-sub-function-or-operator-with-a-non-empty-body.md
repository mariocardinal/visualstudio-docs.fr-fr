---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; un Sub, Function ou Operator avec un corps non vide | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31522"
  - "vbc31522"
helpviewer_keywords: 
  - "BC31522"
ms.assetid: 9548cf98-8a13-4f09-b6b5-2f57273c1571
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; un Sub, Function ou Operator avec un corps non vide
L’attribut `DllImportAttribute` a été appliqué à un `Sub`, `Function` ou `Operator` qui n’est pas vide.  
  
 **ID d’erreur :** BC31522  
  
### Pour corriger cette erreur  
  
-   Supprimez tout le code contenu dans le `Sub`, `Function` ou `Operator` pour utiliser cet attribut.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)