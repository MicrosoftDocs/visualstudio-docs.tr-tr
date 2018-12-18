---
title: 'Nasıl yapılır: bir DataRow belirli sürümlerini alma | Microsoft Docs'
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
- row states
- updating datasets, row states
- DataRow object
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 5bd8ae12c77c671e375043a0381a4b580d1a03d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255495"
---
# <a name="how-to-get-specific-versions-of-a-datarow"></a>Nasıl yapılır: Bir DataRow Satırının Belirli Sürümlerini Alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri satırlarına değişiklik yapıldığında, hem özgün veri kümesini tutar (<xref:System.Data.DataRowVersion>) ve yeni (<xref:System.Data.DataRowVersion>) satır sürümleri. Örneğin, çağırmadan önce `AcceptChanges` yöntemi, uygulamanız bir kaydın farklı sürümlerine erişebilir (sınıfında tanımlandığı gibi <xref:System.Data.DataRowVersion> numaralandırma) ve değişiklikleri buna göre işleyebilir.  
  
> [!NOTE]
>  Bir satırın farklı sürümleri, düzenlendiğinde ve önce var olur yalnızca mevcut `AcceptChanges` yöntemi çağrılır. Sonra `AcceptChanges` yönteminin çağrılıp çağrılmadığını, geçerli ve orijinal sürümler aynıdır.  
  
 Geçirme <xref:System.Data.DataRowVersion> değeri sütun diziniyle (veya sütun adı bir dize olarak) yanı sıra söz konusu sütunun belirli bir satır sürümündeki değeri döndürür. Değiştirilen sütun sırasında tanımlanan <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.ColumnChanged> , farklı incelemek için iyi bir zamandır dolayısıyla bu olaylar, farklı satır sürümlerini doğrulama amacıyla. Ancak, kısıtlamaları geçici olarak askıya aldıysanız, bu olaylar oluşmaz ve hangi sütunların değiştiğini programlı bir şekilde tanımlamak ihtiyacınız olacak. İle Yinelem yaparak bunu yapabilirsiniz <xref:System.Data.DataTable.Columns%2A> toplama ve farklı karşılaştırma <xref:System.Data.DataRowVersion> değerleri.  
  
## <a name="accessing-the-original-version-of-a-datarow"></a>DataRow özgün sürümüne erişme  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Bir kaydın orijinal sürümünü almak için  
  
-   Öğesinde geçen bir sütun değerine erişin <xref:System.Data.DataRowVersion> döndürmek istediğiniz satırın.  
  
     Aşağıdaki örnek nasıl kullanabileceğinizi gösteren bir <xref:System.Data.DataRowVersion> orijinal değerini almak için değer bir `CompanyName` alanındaki bir <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="accessing-the-current-version-of-a-datarow"></a>Geçerli bir DataRow sürümüne erişme  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Bir kaydın geçerli sürümünü almak için  
  
-   Bir sütun değerine erişin ve hangi satır sürümünü döndürmek istediğinizi belirterek dizine bir parametre ekleyin.  
  
     Aşağıdaki örnek nasıl kullanabileceğinizi gösteren bir <xref:System.Data.DataRowVersion> değeri geçerli değerini almak için bir `CompanyName` alanındaki bir <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri kaydetme](../data-tools/saving-data.md)   
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Veri uygulamaları Visual Studio'da genel bakış](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)