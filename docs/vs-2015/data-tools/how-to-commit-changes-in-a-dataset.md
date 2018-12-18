---
title: 'Nasıl yapılır: bir veri kümesinde değişiklikleri işleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataSet.AcceptChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], committing changes
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 41d27c248763f42db6543db0a9b4e56e4c4eac82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276438"
---
# <a name="how-to-commit-changes-in-a-dataset"></a>Nasıl yapılır: Bir Veri Kümesinde Değişiklikleri İşleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir veri kümesindeki kayıtları güncelleştirme, ekleme ve silme kayıtlarını yaptığınız gibi veri kümesini kayıtları geçerli ve özgün sürümlerini korur. Ayrıca, her satır 's <xref:System.Data.DataRow.RowState%2A> özelliği kayıtları, özgün durumdaki veya güncelleştirildi, eklenen veya silinmiş olup olmadığını izler. Bu bilgiler, belirli bir satır sürümü bulmak, ihtiyacınız olduğunda yararlıdır. Genellikle, bir alt kümesini göndermek için başka bir işlem için tüm kayıtlar elde edersiniz. Daha fazla bilgi için [nasıl yapılır: değiştirilen satırları alma](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9). Değiştirilen satırları işledikten sonra çağırarak yaptığınız değişiklikleri kaydetmeniz `AcceptChanges` yöntemi <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow>. `AcceptChanges` Yöntemi otomatik güncelleştirme yöntemlerini çağırmak çıktığında çağrılan bir [TableAdapter](../data-tools/tableadapter-overview.md) veya veri bağdaştırıcısı. Çağrı `AcceptChanges` sonra bir veritabanına değişiklikleri gönderme.  
  
 Çağırdığınızda <xref:System.Data.DataSet.AcceptChanges%2A> üzerinde <xref:System.Data.DataSet>, <xref:System.Data.DataRow> hala düzenleme modunda nesneleri başarıyla son düzenlemeler. <xref:System.Data.DataRow.RowState%2A> Her özellik <xref:System.Data.DataRow> de değişir; <xref:System.Data.DataRowState> ve <xref:System.Data.DataRowState> satırlar haline <xref:System.Data.DataRowState>, ve <xref:System.Data.DataRowState> satır kaldırılır.  
  
 Varsa <xref:System.Data.DataSet> içeren <xref:System.Data.ForeignKeyConstraint> çağırma nesnelerinin <xref:System.Data.DataSet.AcceptChanges%2A> yöntemi de neden olur <xref:System.Data.AcceptRejectRule> uygulanacak.  
  
### <a name="to-commit-changes-in-a-dataset"></a>Bir veri kümesindeki değişiklikleri kaydetmek için  
  
-   Çağrı `AcceptChanges` yöntemini ya da bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow> bu nesnelerdeki değişiklikleri kaydetmek için.  
  
     Aşağıdaki örnek nasıl çağrılacağını gösterir `AcceptChanges` değişiklikleri uygulamak için gereken yöntemini `Customers` tablosu veri kaynağı güncelleştirdikten sonra:  
  
     [!code-csharp[VbRaddataEditing#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#11)]
     [!code-vb[VbRaddataEditing#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Verileri kaydetme](../data-tools/saving-data.md)   
 [Nasıl yapılır: değiştirilen satırları alma](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)