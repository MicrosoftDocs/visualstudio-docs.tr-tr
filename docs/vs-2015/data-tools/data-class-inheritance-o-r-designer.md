---
title: Veri sınıfı devralma (O R Designer) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae36d6aac3ea9a4ff4de73dea57207b6f03abc72
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180524"
---
# <a name="data-class-inheritance-or-designer"></a>Veri sınıfı devralma (O/R Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Gibi diğer nesneler [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] sınıflar, devralma kullanabilirsiniz ve diğer sınıflarından türetilmiş. Kod içinde bir sınıf diğerinden devralır bildirmek nesneler arasındaki devralma ilişkileri belirtebilirsiniz. Bir veritabanında kalıtım ilişkileri çeşitli yollarla oluşturulur. [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) İlişkisel sistemlerde sık uygulandığı şekilde tek tablolu devralma kavramını destekler.  
  
 Tek tablo Devralmada hem temel sınıfını hem türetilen sınıflarını sütunlarını içeren bir tek veritabanı tablosu yok. İlişkisel verilerle bir ayrıştırıcı sütunu verilen kaydın ait olduğu sınıfı belirleyen bir değer içerir. Örneğin, herkesin şirket tarafından kullanılan içeren bir kişi tabloya göz önünde bulundurun. Bazı kişiler çalışanlar ve bazı kişiler yöneticileri. Kişiler Tablo 1 değeri, yöneticileri ve 2 değerini çalışanlar için sahip türü adlı bir sütun içerir. Tür sütunu ayrıştırıcı sütunu var. Bu senaryoda, çalışanların öğesinin oluşturabilir ve sınıf 2 tür değeri olan kayıtları ile doldurun.  
  
 Yapılandırdığınızda devralma varlık sınıfları kullanarak [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], iki kez tasarımcıya devralma verileri içeren tek bir tabloyu sürükleyin: devralma hiyerarşisinde her sınıf için bir kez. Tasarımcıya tabloları ekledikten sonra bunları bir devralma öğesinden bağlanın **Object Relational Designer** araç ve kümesi dört devralma özelliklerinde **özellikleri** penceresi.  
  
## <a name="inheritance-properties"></a>Devralma Özellikleri  
 Aşağıdaki tabloda, devralma özellikleri ve açıklamaları listelenmektedir:  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|Ayrıştırıcı özelliği|Geçerli kayda ait olduğu olduğu sınıfı belirleyen (sütuna eşlenmiş) özelliği.|  
|Temel sınıf ayrıştırıcı değeri|Bir kaydın temel sınıf olduğunu belirleyen (ayrıştırıcı özelliği belirtilen sütunda değeri).|  
|Türetilen sınıf ayrıştırıcı değeri|Bir kaydın türetilmiş sınıf olduğunu belirleyen değeri (ayrıştırıcı özelliği belirtilen özellik).|  
|Devralma varsayılanı|Özellik değeri olarak belirlenmiş doldurulup sınıfının **ayrıştırıcı özelliği** ya da eşleşmiyor **temel sınıf ayrıştırıcı değeri** veya **türetilen sınıfı Ayrıştırıcı değeri**.|  
  
 Devralma kullanan ve ilişkisel verilere karşılık gelen bir nesne modeli oluşturma biraz kafa karıştırıcı olabilir. Bu konu, temel kavramları ve devralma yapılandırmak için gerekli olan özellikler hakkında bilgi sağlar. Aşağıdaki konular, devralma ile nasıl yapılandıracağınızı öğrenmek için daha anlaşılır bir açıklama sağlar. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Tek Tablo Devralma kullanarak varlık sınıflarını yapılandırmayı açıklar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|  
|[İzlenecek Yol: Tek Tablo Devralma Kullanarak LINQ to SQL Sınıfı Oluşturma (O/R Tasarımcısı)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Tek Tablo Devralma kullanarak varlık sınıfları yapılandırma hakkında adım adım yönergeler sağlar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [İzlenecek yol: LINQ to SQL sınıfları (O R Designer) oluşturma](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [İzlenecek yol: Tek tablolu devralma (O/R Tasarımcısı) kullanarak LINQ to SQL sınıfları oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [Başlarken](http://msdn.microsoft.com/library/db8a557a-fef8-4f4f-bb91-8cff7250ee25)

