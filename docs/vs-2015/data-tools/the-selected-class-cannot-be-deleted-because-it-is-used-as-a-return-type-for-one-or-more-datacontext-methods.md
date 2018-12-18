---
title: Bir veya birden çok DataContext yöntemi için dönüş türü kullanıldığından, seçilen sınıf silinemiyor | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 084843636d62bd7d85c5bbc141aa0fe8ddf81462
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236268"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Seçilen sınıf bir veya birden çok DataContext yöntemi için bir dönüş türü olarak kullanıldığından silinemiyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Dönüş türü bir veya daha fazla <xref:System.Data.Linq.DataContext> yöntemleri, seçilen varlığın sınıftır. Silme için dönüş türü olarak kullanılacak bir varlık sınıfı bir <xref:System.Data.Linq.DataContext> yöntemi derleme projenin başarısız olmasına neden olur. Seçilen varlık sınıfını silmek için tanımlamak <xref:System.Data.Linq.DataContext> yöntemleri kullanmak ve dönüş türleri farklı varlık sınıfa ayarlayın.  
  
 Geri dönüş türleri <xref:System.Data.Linq.DataContext> kendi özgün otomatik olarak oluşturulan türler, yöntemlere silin <xref:System.Data.Linq.DataContext> yöntemleri bölmesinden yöntemi ve sonra nesneyi sürükleyin **Sunucu Gezgini** / **Veritabanı Gezgini** O/R Tasarımcısı yeniden sürükleyin.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tanımlamak <xref:System.Data.Linq.DataContext> varlık sınıfı seçerek bir dönüş türü olarak kullanan yöntemleri bir <xref:System.Data.Linq.DataContext> yöntemleri yönteminde bölmesinde ve İnceleme **dönüş türü** özelliğinde **özellikleri** penceresi .  
  
2.  Ayarlama **dönüş türü** farklı varlık sınıfı ya da silme <xref:System.Data.Linq.DataContext> yöntemleri bölmesinden yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [İzlenecek yol: LINQ to SQL sınıfları (O R Designer) oluşturma](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [DataContext yöntemi (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Nasıl yapılır: Bir DataContext metodunun dönüş türünü değiştirme (O/R Tasarımcısı)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)

