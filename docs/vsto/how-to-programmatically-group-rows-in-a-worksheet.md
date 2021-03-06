---
title: "Comment : regrouper des lignes dans une feuille de calcul par programmation | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c11911d6d9e7b92b7a86b21723c8788afe15a57b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Comment : regrouper des lignes dans une feuille de calcul par programmation
  Vous pouvez regrouper une ou plusieurs lignes entières. Pour créer un groupe dans une feuille de calcul, utilisez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>À l’aide d’un contrôle NamedRange  
 Si vous ajoutez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à un projet au niveau du document au moment du design, vous pouvez utiliser le contrôle à créer par programmation un groupe. L’exemple suivant suppose qu’il existe trois <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôles sur la feuille de calcul : `data2001`, `data2002`, et `dataAll`. Chaque plage nommée fait référence à une ligne entière dans la feuille de calcul.  
  
#### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Pour créer un groupe de contrôles NamedRange sur une feuille de calcul  
  
1.  Regrouper les trois plages nommées en appelant le <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> méthode de chaque plage. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Pour dissocier des lignes, appelez le <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> (méthode).  
  
## <a name="using-native-excel-ranges"></a>À l’aide de plages Excel natives  
 Le code suppose que vous avez trois plages Excel nommées `data2001`, `data2002`, et `dataAll` sur une feuille de calcul.  
  
#### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Pour créer un groupe de plages Excel dans une feuille de calcul  
  
1.  Regrouper les trois plages nommées en appelant le <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> méthode de chaque plage. L’exemple suivant suppose qu’il existe trois <xref:Microsoft.Office.Interop.Excel.Range> contrôles nommés `data2001`, `data2002`, et `dataAll` sur la même feuille de calcul. Chaque plage nommée fait référence à une ligne entière dans la feuille de calcul.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Pour dissocier des lignes, appelez le <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  