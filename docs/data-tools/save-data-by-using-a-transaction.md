---
title: 'Nasıl yapılır: bir işlemi kullanarak veri kaydetme'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 28beeec474af9b05153e787c6cbe22034d09b350
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750994"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Nasıl yapılır: bir işlemi kullanarak veri kaydetme

Kullanarak bir işlemde veri kaydetme <xref:System.Transactions> ad alanı. Kullanım <xref:System.Transactions.TransactionScope> sizin için otomatik olarak yönetilen bir işlem katılmak için nesne.

Projeleri başvurusuyla oluşturulmaz *System.Transactions* derleme, bu nedenle el ile işlem kullanan projeler için bir başvuru eklemeniz gerekir.

Örneği oluşturmak için bir işlem uygulamak için en kolay yolu olan bir <xref:System.Transactions.TransactionScope> nesnesine bir `using` deyimi. (Daha fazla bilgi için [Using deyimi](/dotnet/visual-basic/language-reference/statements/using-statement), ve [Using deyimi](/dotnet/csharp/language-reference/keywords/using-statement).) İçinde çalışan kodu `using` deyimi, işlem sırasında katılan.

Hareketi tamamlamak için çağrı <xref:System.Transactions.TransactionScope.Complete%2A> yöntemi kullanarak son deyim olarak engelleyin.

İşlem geri almak için çağrılmadan önce bir özel durum throw <xref:System.Transactions.TransactionScope.Complete%2A> yöntemi.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>System.Transactions.dll bir başvuru eklemek için

1.  Üzerinde **proje** menüsünde **Başvuru Ekle**.

2.  Üzerinde **.NET** sekme (**SQL Server** SQL Server projeleri için sekmesinde), select **System.Transactions**ve ardından **Tamam**.

     Bir başvuru *System.Transactions.dll* projeye eklenir.

## <a name="to-save-data-in-a-transaction"></a>Bir işlemde verileri kaydetmek için

-   Kullanarak içinde verileri kaydetmek için kod ekleme deyimi, işlem içerir. Aşağıdaki kod nasıl oluşturulup örneğini gösterir. bir <xref:System.Transactions.TransactionScope> kullanarak bir nesne ifadesi:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
- [İzlenecek yol: Bir işlemde veri kaydetme](../data-tools/save-data-in-a-transaction.md)