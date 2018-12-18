---
title: TryCatch etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 74b54ef6b82e4f98ab94972b5d9b0155c16060a9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241000"
---
# <a name="trycatch-activity-designer"></a>TryCatch Etkinlik Tasarımcısı
**TryCatch** etkinlik Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.Activities.Statements.TryCatch> etkinlik.  
  
## <a name="the-trycatch-activity"></a>TryCatch etkinlik  
 <xref:System.Activities.Statements.TryCatch> Etkinliği içeren bir <xref:System.Activities.Statements.TryCatch.Try%2A> etkinliği, koleksiyonu **Catch\<TException >** ve <xref:System.Activities.Statements.TryCatch.Finally%2A> etkinlik. A <xref:System.Activities.Statements.Catch%601> türü **TException** içeren bir <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> ve <xref:System.Activities.Statements.Catch%601.Action%2A>. Birlikte işleme mekanizması tipik bir özel durum tabanlı hata uygulamak için kullanılırlar. A <xref:System.Activities.Statements.TryCatch> etkinlik çalıştığında yürütmek onun <xref:System.Activities.Statements.TryCatch.Try%2A> etkinlik. Varsa <xref:System.Activities.Statements.TryCatch.Try%2A> etkinlik hiçbir özel durum oluşturursa <xref:System.Activities.Statements.TryCatch> etkinliği kullanır, **Catch < TException\>**  özel durum eşleşmesi için koleksiyonu. Bir eşleşme varsa sonra <xref:System.Activities.Statements.Catch%601.Action%2A> karşılık gelen **Catch\<TException >** , hata işleme mantığı için özel olarak yürütülür. Etkinlikler, <xref:System.Activities.Statements.TryCatch.Try%2A> bölümü başarıyla tamamlanması veya etkinliklerinin <xref:System.Activities.Statements.TryCatch.Catches%2A> başarıyla tamamlanması <xref:System.Activities.Statements.TryCatch> etkinliği yürütür, <xref:System.Activities.Statements.TryCatch.Finally%2A> etkinlik. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Özel durumlar](http://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136).  
  
### <a name="using-the-trycatch-activity-designer"></a>TryCatch etkinlik Tasarımcısı kullanma  
 **TryCatch** etkinlik Tasarımcısı bulunabilir **hata işleme** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araçkutusu** sol tarafındaki sekmesinde [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menü veya DNTL + ALT + X.)  
  
 **TryCatch** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey yerde etkinlikleri genellikle yerleştirilir, örneğin olarak içinde bir <xref:System.Activities.Statements.Sequence>. Bu, oluşturur bir <xref:System.Activities.Statements.TryCatch> etkinliği ile bir varsayılan <xref:System.Activities.Activity.DisplayName%2A> TryCatch biri. <xref:System.Activities.Activity.DisplayName%2A> Değeri üst bilgisinde düzenlenebilir **TryCatch** etkinlik Tasarımcısı veya **DisplayName** özellik kılavuzunda kutusu. Diğer özellikler yüzeyine düzenlenmelidir **TryCatch** etkinlik Tasarımcısı.  
  
 Sağ üst köşesindeki genişletme düğmesine **TryCatch** görmek için tasarımcı **deneyin**, **yakalar**, ve **son** kutusu Genişletilmiş Görünüm. Bir catch eklemek için tıklatın **yeni catch ekleme** düğmesini **TryCatch** Tasarımcısı. Düğme türü açılan kutuya değiştirir. Bir özel durum türü seçin ve yakalama eklemek için ENTER tuşuna basın. Ekledikten sonra bir **Catch**, catch alanı genişler ve bir etkinlik yakalama yürütme mantığı tanımlamak için yakalama uygulamasına bırakılabilir. Genişletilmiş catch alanının sağ tarafında bir metin kutusu olduğuna dikkat edin. Bu metin kutusunu kullanarak özel durum değişkeninin adı verebilirsiniz. Özel durum değişkeni yalnızca aynı içindeki etkinlikler için kullanılabilir **Catch**.  
  
 **TryCatch** Tasarımcısı düzenlemeyi desteklemiyor **Catch**. Özel durum türü değiştirmek istiyorsanız, silmek sahip **Catch** ve yeni bir tane ekleyin. A **Catch** seçip silerek veya kullanılarak silinebilir **Sil** sağ tıklayarak erişilen bağlam menüsünde menüsü.  
  
### <a name="the-trycatch-properties"></a>TryCatch özellikleri  
 Aşağıdaki tabloda <xref:System.Activities.Statements.TryCatch>özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|İsteğe bağlı kolay adı belirtir <xref:System.Activities.Statements.TryCatch> etkinlik. TryCatch varsayılandır.|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Etkinlik yürütülmesi ilk <xref:System.Activities.Statements.TryCatch> yürütür.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Koleksiyonu **Catch** , denetlenecek öğelerin <xref:System.Activities.Statements.TryCatch.Try%2A> etkinlik bir özel durum oluşturur.<br /><br /> En az bir etkinlik ekleyin <xref:System.Activities.Statements.TryCatch.Catches%2A> veya bir etkinlikte <xref:System.Activities.Statements.TryCatch.Finally%2A> blok.|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Etkinlik zaman yürütülecek <xref:System.Activities.Statements.TryCatch.Try%2A> ve gerekli tüm etkinlikleri <xref:System.Activities.Statements.TryCatch.Catches%2A> koleksiyonu tam yürütme.<br /><br /> En az bir etkinlik ekleyin <xref:System.Activities.Statements.TryCatch.Catches%2A> veya bir etkinlikte <xref:System.Activities.Statements.TryCatch.Finally%2A> blok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koleksiyon](../workflow-designer/collection-activity-designers.md)   
 [yeniden oluşturma](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)