---
title: Bir işlemi kullanarak veri kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4c73dd654a2d48be963e592d94685c74d3a16057
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219581"
---
# <a name="save-data-by-using-a-transaction"></a>Bir işlemi kullanarak veri kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Kullanarak bir işlemde veri kaydetme <xref:System.Transactions> ad alanı. Kullanım <xref:System.Transactions.TransactionScope> sizin için otomatik olarak yönetilen bir işlem katılmak için nesne.  
  
 Bu nedenle el ile işlem kullanan projeler için bir başvuru eklemeniz gerekir projeleri System.Transactions derlemesine bir başvuru ile oluşturulmaz.  
  
> [!NOTE]
>  <xref:System.Transactions> Ad alanı, Windows 2000 veya sonraki sürümlerde desteklenir.  
  
 Örneği oluşturmak için bir işlem uygulamak için en kolay yolu olan bir <xref:System.Transactions.TransactionScope> nesnesine bir `using` deyimi. (Daha fazla bilgi için [Using deyimi](http://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1), ve [using deyimi](http://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) İçinde çalışan kodu `using` deyimi, işlem sırasında katılan.  
  
 Hareketi tamamlamak için çağrı <xref:System.Transactions.TransactionScope.Complete%2A> yöntemi kullanarak son deyim olarak engelleyin.  
  
 İşlem geri almak için çağrılmadan önce bir özel durum throw <xref:System.Transactions.TransactionScope.Complete%2A> yöntemi.  
  
 Daha fazla bilgi için [bir işlemde veri kaydetme](../data-tools/save-data-in-a-transaction.md).  
  
### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>System.Transactions DLL'ye bir başvuru eklemek için  
  
1.  Üzerinde **proje** menüsünde **Başvuru Ekle**.  
  
2.  Üzerinde **.NET** sekme (**SQL Server** SQL Server projeleri için sekmesinde), select **System.Transactions**ve ardından **Tamam**.  
  
     System.Transactions.dll referansı projeye eklenir.  
  
### <a name="to-save-data-in-a-transaction"></a>Bir işlemde verileri kaydetmek için  
  
-   Kullanarak içinde verileri kaydetmek için kod ekleme deyimi, işlem içerir. Aşağıdaki kod nasıl oluşturulup örneğini gösterir. bir <xref:System.Transactions.TransactionScope> kullanarak bir nesne ifadesi:  
  
     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

