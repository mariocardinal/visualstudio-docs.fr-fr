---
title: "Avertissement du compilateur (niveau&#160;1) CS1692 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1692"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1692"
ms.assetid: 1a6d52e1-0ebb-4990-ac0b-36b05a884a19
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1692
Nombre non valide  
  
 Un certain nombre de directives de préprocesseur, telles que `#pragma` et `#line`, utilisent des nombres comme paramètres. Un de ces nombres n’est pas valide, car il est trop élevé, son format est incorrect, il contient des caractères non autorisés, etc. Pour corriger cette erreur, corrigez le nombre.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1692.  
  
```  
// CS1692.cs #pragma warning disable a  // CS1692 // Try this instad: // #pragma warning disable 1691 class A { static void Main() { } }  
```