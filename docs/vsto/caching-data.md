---
title: Verileri önbelleğe
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b46fa8b0138eff03757a7bd7828053cee039090f
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248130"
---
# <a name="cache-data"></a>Verileri önbelleğe
  Böylece veriler erişilebilir, çevrimdışı veya Microsoft Office Word veya Microsoft Office Excel açmadan belge düzeyi özelleştirmesinde veri nesneleri önbelleğe alabilir. Nesne, nesne önbelleğe almak için belirli gereksinimleri karşılayan bir veri türü olmalıdır. .NET Framework'teki birçok ortak veri türleri dahil olmak üzere, bu gereksinimleri karşılayan <xref:System.String>, <xref:System.Data.DataSet>, ve <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Nesne verileri önbelleğe eklemek için iki yolu vardır:  
  
- Çözüm derlenirken, nesne verileri önbelleğe eklemek için uygulama <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> özniteliği için nesne bildirimi. Daha fazla bilgi için [nasıl yapılır: Çevrimdışı veya sunucuda kullanmak için verileri önbelleğe](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
- Program aracılığıyla bir nesneyi çalışma zamanında verileri önbelleğe eklemek için `StartCaching` gibi bir konak yöntemi öğesi `ThisDocument` veya `ThisWorkbook` sınıfları. Daha fazla bilgi için [nasıl yapılır: Bir Office belgesi bir veri kaynağını programlamayla önbelleğe alma](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
  Bir nesne için veri önbelleğini ekledikten sonra erişim ve Word veya Excel başlatmadan önbelleğe alınmış verileri değiştirme. Daha fazla bilgi için [sunucudaki belgelerde verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Önbelleğe alınacak veri nesneleri için gereksinimleri  
 Nesne, çözümünüzü veri nesnesinde önbelleğe almak için bu gereksinimleri karşılaması gerekir:  
  
- Okuma/yazma ortak alan veya bir konak öğesi özelliği gibi olması `ThisDocument` veya `ThisWorkbook` sınıfları.  
  
- Bir dizin oluşturucu veya diğer parametreli özellik olmamalıdır.  
  
  Ayrıca, veri nesnesi getirilmeli <xref:System.Xml.Serialization.XmlSerializer> nesne türü diğer bir deyişle, sınıf şu özelliklere sahip olması gerekir:  
  
- Genel bir tür olabilir.  
  
- Genel parametresiz oluşturucusu vardır.  
  
- Ek güvenlik ayrıcalıkları gerektiren kod yürütmesine değil.  
  
- (Diğer özellikleri yoksayılacak) yalnızca okuma/yazma genel özellikleri kullanıma sunar.  
  
- Çok boyutlu diziler (iç içe geçen diziler kabul edilir) sunmamalısınız.  
  
- Özellikler ve alanları arabirimlerden döndürmez.  
  
- Uygulamaz <xref:System.Collections.IDictionary> bir koleksiyonu.  
  
  Bir veri nesnesi önbellek zaman [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] depolanan XML dizesine nesneyi serileştiren bir *özel XML bölümleri* belgedeki. Daha fazla bilgi için [özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Önbelleğe alınmış veri boyut sınırları  
 Bir belgedeki veri önbelleğini ve veri önbelleğindeki herhangi tek bir nesnenin boyutunu ekleyebilirsiniz veri toplam miktarı için bazı limitler mevcuttur. Bu sınırları aşmanız halinde veri veri önbelleğine kaydedildiğinde uygulama beklenmedik bir şekilde kapanabilir.  
  
 Bu sınırlar önlemek için aşağıdaki yönergeleri izleyin:  
  
- 10 MB'tan büyük olan herhangi bir nesne için veri önbelleğini eklemeyin.  
  
- Daha fazla 100 MB Toplam veri tek bir belge verileri önbelleğe eklemeyin.  
  
  Bunlar yaklaşık değerlerdir. Tam sınırları kullanılabilir RAM ve çalışan işlemlerin sayısı dahil olmak üzere çeşitli etkenlere bağlıdır.  
  
## <a name="control-the-behavior-of-cached-objects"></a>Önbelleğe alınan nesneleri davranışını denetleme  
 Önbelleğe alınmış nesnenin davranışını üzerinde daha fazla denetim kazanmak için uygulayabileceğiniz <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> arabirimde önbelleğe alınan nesnenin türü. Örneğin, bir nesne değiştirildiğinde nasıl kullanıcı bilgilendirilir denetlemek istiyorsanız bu arabirimi uygulayabilir. Nasıl uygulanacağını gösteren kod örnekleri için <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, bkz: `ControlCollection` sınıfı dinamik denetim örneği Excel ve Word Dinamik Denetim örneği [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Önbelleğe alınan verilerin parola korumalı belgeleri üzerinde yapılan değişiklikler kalıcı  
 Veri nesneleri, parola korumalı belgede önbelleğe alma, önbelleğe alınan verilerde yapılan değişiklikleri kaydedilmedi. İki yöntemi geçersiz kılarak, önbelleğe alınan verilerde yapılan değişiklikleri kaydedebilirsiniz. Belge kaydedildiğinde geçici olarak korumayı kaldırmak için bu yöntemleri geçersiz kılın ve ardından Kaydet korumayı yeniden işlemi tamamlanmıştır.  
  
 Daha fazla bilgi için [nasıl yapılır: Bir parola korumalı belgede veriyi önbelleğe alma](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Null değerler için veri önbelleğini eklerken veri kaybını önleme  
 Verileri önbelleğe birini eklediğinizde, bu nesneleri önbelleğe alınmış tüm nesneler olmayan bir başlatılmalıdır**null** Belge kaydedildi ve önce değer. Tüm önbelleğe alınmış nesneye sahipse bir **null** belgenin kaydedilip kapalı, değer [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] otomatik olarak önbelleğe alınan tüm nesneler veri önbellekten kaldırır.  
  
 Bir nesne ile eklerseniz bir **null** kullanarak veri önbelleğini değerine <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> özniteliği tasarım zamanında kullanabilirsiniz <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> belge açılmadan önce önbelleğe alınmış verileri başlatmak için sınıfın nesneleri. Bu özellik, Word veya Excel belge bir son kullanıcı tarafından açılmadan önce yüklü olmayan bir sunucuda önbelleğe alınmış verileri başlatmak istiyorsanız kullanışlıdır. Daha fazla bilgi için [sunucudaki belgelerde verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Çevrimdışı veya sunucuda kullanmak için verileri önbelleğe](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Nasıl yapılır: Bir Office belgesi bir veri kaynağını programlamayla önbelleğe alma](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Nasıl yapılır: Bir parola korumalı belgede veriyi önbelleğe alma](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [İzlenecek yol: Önbellekteki veri kümesini kullanarak bir ana ayrıntı ilişkisi oluşturma](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  