---
title: Update data by using a TableAdapter | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
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
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 130c127cb0787e3f13f90adfef72de072300fcf3
ms.contentlocale: fr-fr
ms.lasthandoff: 08/30/2017

---
# <a name="update-data-by-using-a-tableadapter"></a>Update data by using a TableAdapter
After the data in your dataset has been modified and validated, you can send the updated data back to a database by calling the `Update` method of a [TableAdapter](../data-tools/create-and-configure-tableadapters.md). The `Update` method updates a single data table and runs the correct command (INSERT, UPDATE, or DELETE) based on the <xref:System.Data.DataRow.RowState%2A> of each data row in the table. When a dataset has related tables, Visual Studio generates a TableAdapterManager class that you  use to do the updates. The TableAdapterManager class ensures that updates are made in the correct order based on the foreign-key constraints that are defined in the database. When you use data-bound controls, the databinding architecture creates a member variable of the TableAdapterManager class called tableAdapterManager. 
  
> [!NOTE]
>  When you try to update a data source with the contents of a dataset, you can get errors.To avoid errors, we recommend that you put the code that calls the adapter's `Update` method inside a `try`/`catch` block.  
  
 The exact procedure for updating a data source can vary depending on business needs, but  includes the following steps:  
  
1.  Call the adapter's `Update` method in a `try`/`catch` block.  
  
2.  If an exception is caught, locate the data row that caused the error. 
  
3.  Reconcile the problem in the data row (programmatically if you can, or by presenting the invalid row to the user for modification), and then try the update again (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="save-data-to-a-database"></a>Save data to a database  
 Call the `Update` method of a TableAdapter. Pass the name of the data table that contains the values to be written to the database.  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>To update a database by using a TableAdapter  
  
-   Enclose the TableAdapter's`Update` method in a `try`/`catch` block. The following example shows how to  update  the contents of the `Customers` table in `NorthwindDataSet` from within a `try`/`catch` block .  
  
     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]  [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## <a name="see-also"></a>See Also  
 [Save data back to the database](../data-tools/save-data-back-to-the-database.md)