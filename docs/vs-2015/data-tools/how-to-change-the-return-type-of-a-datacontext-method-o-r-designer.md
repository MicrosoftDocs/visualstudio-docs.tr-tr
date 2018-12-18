---
title: 'Nasıl yapılır: bir DataContext yöntemi (O R Designer) dönüş türünü değiştirme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4999c9fd273b78ff740e53c25bbe5a4b0a3017f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211750"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Nasıl yapılır: bir DataContext yöntemi (O/R Tasarımcısı) dönüş türünü değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Dönüş türü bir <xref:System.Data.Linq.DataContext> yöntemi (bir saklı yordamı veya işlevi temel alarak oluşturduğunuz) farklı bağlı olarak burada bırak saklı yordamı veya işlevi [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Bir öğeyi doğrudan mevcut bir varlık sınıfı üzerine sürükleyip bıraktığınızda bir <xref:System.Data.Linq.DataContext> varlık sınıfı için dönüş türüne sahip yöntemi (saklı yordamı veya işlevi tarafından döndürülen veri şeması varlık sınıfı şeklini eşleşiyorsa) oluşturulur. Boş bir alanının bir öğeyi bırak varsa [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], <xref:System.Data.Linq.DataContext> otomatik olarak oluşturulan bir tür döndüren yöntem oluşturulur. Dönüş türünü değiştirebilirsiniz bir <xref:System.Data.Linq.DataContext> yöntemleri bölmesine ekledikten sonra yöntemi. İnceleme veya dönüş türünü değiştirmek için bir <xref:System.Data.Linq.DataContext> yöntemi seçin ve **dönüş türü** özelliğinde **özellikleri** penceresi.  
  
> [!NOTE]
>  Geri alınamaz <xref:System.Data.Linq.DataContext> kullanarak otomatik olarak oluşturulan türü döndürmek için bir varlık sınıfı için ayarlanmış bir dönüş türüne sahip yöntemleri **özellikleri** penceresi. Geri almak için bir <xref:System.Data.Linq.DataContext> yöntemi otomatik olarak üretilen bir tür dönmek için orijinal veritabanı nesnesi O/R Tasarımcısı yeniden sürüklemeniz gerekir.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Bir DataContext yöntemin dönüş türü bir varlık sınıfı için otomatik olarak oluşturulan türü değiştirmek için  
  
1.  Seçin <xref:System.Data.Linq.DataContext> yöntemleri bölmesinde yöntemi.  
  
2.  Seçin **dönüş türü** içinde **özellikleri** penceresi ve ardından kullanılabilir varlık sınıfı içinde **dönüş türü** listesi. İstenen varlık sınıfı listesinde değilse, ekleyin veya oluşturun [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] listesine eklenecek.  
  
3.  .Dbml dosyayı kaydedin.  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Bir DataContext yöntemin dönüş türü bir varlık sınıfından otomatik olarak üretilen türe geri değiştirmek için  
  
1.  Seçin <xref:System.Data.Linq.DataContext> yöntemleri bölmesinde yöntemi ve silin.  
  
2.  Veritabanı nesneyi sürükleyin **Sunucu Gezgini**/**veritabanı Gezgini** O/R Tasarımcısı'nın boş bir alana sürükleyin.  
  
3.  .Dbml dosyayı kaydedin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [DataContext yöntemi (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)

