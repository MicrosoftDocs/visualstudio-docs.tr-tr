---
title: Çalıştırılan Belge tablosu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd7b8cd44c72ea058f71575bdd1774efafa86731
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746296"
---
# <a name="running-document-table"></a>Çalıştırılan Belge Tablosu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE, tüm açık belgelerde çalıştırılan Belge tablosu (RDT) olarak adlandırılan bir iç yapıyı listesini tutar. Bu liste, bellekte olup bu belgeler şu anda düzenlenmekte olan bağımsız olarak tüm açık belgeleri içerir. Kalıcı, dosyaları bir proje veya ana proje dosyasında (örneğin, bir .vcxproj dosyası) dahil olmak üzere herhangi bir öğeyi bir belgedir.  
  
## <a name="elements-of-the-running-document-table"></a>Çalıştırılan Belge tablosu öğeleri  
 Çalıştırılan Belge tablosu aşağıdaki girişleri içerir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Belge adı|Belge veri nesnesi benzersiz olarak tanımlayan bir dize. Bu dosyaları (örneğin, C:\MyProject\MyFile) yöneten bir proje sistemi için mutlak dosya yolu olabilir. Bu dize, bir veritabanındaki saklı yordamlar gibi dosya sistemleri dışındaki depolardan kaydedilmiş projeleri için de kullanılır. Bu durumda, proje sistemi tanıyabilir ve belge depolamak nasıl belirlemek için büyük olasılıkla ayrıştırma benzersiz bir dize stok.|  
|Hiyerarşi sahibi|Belge tarafından temsil edilen sahibi olan hiyerarşi nesnesinin bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirimi.|  
|Öğe kimliği|Hiyerarşi içindeki belirli bir öğenin öğe tanımlayıcısı. Bu değer, bu belge sahibi hiyerarşideki tüm belgeler arasında benzersiz, ancak bu değeri farklı Hiyerarşiler arasında benzersiz olması garanti edilmez.|  
|Belge veri nesnesi|Budur en az bir `IUnknown`<br /><br /> nesne. IDE dışında herhangi bir belirli arabirimi gerektirmez `IUnknown` arabirimi için bir özel düzenleyicinin belge veri nesnesi. Ancak, standart bir düzenleyici için düzenleyicinin uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> arabirimi, proje dosyası Kalıcılık çağrıları işlemek için gereklidir. Daha fazla bilgi için [bir standart belge kaydetme](../../extensibility/internals/saving-a-standard-document.md).|  
|Bayraklar|Bir okuma veya düzenleme kilidi uygulanıp uygulanmayacağını belgenin kaydedilip kaydedilmediğini kontrol bayraklar ve benzeri, girişler için RDT eklendiğinde belirtilebilir. Daha fazla bilgi için <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> sabit listesi.|  
|Kilit sayacını Düzenle|Düzenleme kilitlerin sayısı. Bir düzen kilit bazı Düzenleyicisi belgeyi düzenlemek için açık olduğunu gösterir. Düzenleme kilit sayısı sıfıra yaptığında, değiştirildi kullanıcı belgeyi kaydedin istenir. Örneğin, bir belge kullanarak bir düzenleyicide her açışlarında **yeni pencere** komutu, bir düzenleme kilidi RDT bu belgeye eklenir. Ayarlanacak bir düzenleme kilidi için sırayla belge gerekir bir hiyerarşiniz veya öğesi kimliği|  
|Okuma kilidi sayısı|Kilit sayısı okuyun. Bir okuma kilidi belgenin bir sihirbaz gibi bazı mekanizması aracılığıyla okunan olduğunu gösterir. Bir okuma kilidi, belge düzenlenemez belirten çalışırken bir belge RDT içinde canlı tutar. Belge bir hiyerarşiniz etmez veya öğesi kimliği olsa bile bir okuma kilidi ayarlayabilirsiniz. Bu özellik, bellekte bir belgeyi açın ve RDT içinde herhangi bir hiyerarşi tarafından ait belge olmadan girin sağlar. Bu özellik nadiren kullanılır.|  
|Kilit sahibi|Örneği bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> arabirimi. Kilit sahibi belgeleri dışında bir düzenleyicide açıp sihirbazları gibi özellikler tarafından uygulanır. Kilit sahibi hala düzenleniyor sırada kapalı belge önlemek için belgenin bir düzenleme kilit eklemek bu özellik sağlar. Normalde, Düzen kilitleri yalnızca belge pencereleri (diğer bir deyişle, Düzenleyicileri) tarafından eklendi.|  
  
 Her giriş RDT benzersiz bir hiyerarşi veya ilişkili genellikle projedeki bir düğüme karşılık gelen öğe kimliği vardır. Tüm belgeleri düzenlemek için kullanılabilen bir hiyerarşi tarafından genellikle sahibi olur. Hangi proje içinde RDT yapılan girişleri denetlemek veya — daha doğru bir şekilde — hangi hiyerarşi, şu anda düzenlenmekte olan belge veri nesnesi sahip. İçinde RDT bilgileri kullanarak, IDE aynı anda birden fazla proje tarafından açılmış bir belge engelleyebilirsiniz.  
  
 Hiyerarşi ayrıca veri kalıcılığı denetler ve bilgileri güncelleştirmek için RDT kullanır **Kaydet** ve **Kaydet** iletişim kutuları. Kullanıcılar, bir belgeyi değiştirme ve ardından **çıkış** komutunu **dosya** menüsünde, IDE bunları ister **Değişiklikleri Kaydet** tüm projeleri gösterecek şekilde iletişim kutusu ve şu anda değiştirilen proje öğeleri. Bu, kullanıcıların belgeleri kaydetmek için hangi izin verir. Kaydetmek için belgelerin listesini (diğer bir deyişle, değişiklikleriniz var. Bu belgeleri) RDT oluşturulur. İçinde görmeyi beklediğiniz tüm öğeler **Değişiklikleri Kaydet** uygulama çıkarken iletişim kutusu içinde RDT kayıtları sahip olmalıdır. Hangi belgelerin kaydedilir ve kullanıcı bir kaydetme hakkında istenir mi RDT koordinatları bayrakları giriş her belge için belirtilen değerleri kullanarak işlemi. RDT bayrakları hakkında daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> sabit listesi.  
  
## <a name="edit-locks-and-read-locks"></a>Düzenleme kilitler ve okuma kilitlerini  
 Düzenleme kilitler ve okuma kilitlerini RDT içinde yer alır. Belge penceresi artırır ve azaltır düzenleme kilitleyin. Bu nedenle, bir kullanıcı yeni bir belge penceresi açıldığında, düzenleme kilit sayacını artırır bir. Düzenleme kilit sayısı sıfır ulaştığında, sürdürülmesi veya ilişkili belge için verileri kaydetmek için hiyerarşi sinyal. Hiyerarşi sonra veri deposundaki bir öğe olarak veya bir dosya kalıcı hale getirilmesine de dahil olmak üzere herhangi bir yolla kalıcı hale getirebilirsiniz. Kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> düzenleme kilidi Ekle ve okuma kilitlerini arabirimi ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> bu kilitleri kaldırma yöntemi.  
  
 Normalde, belge penceresi için bir düzenleyici örneği oluşturulduğunda, pencere çerçevesi otomatik olarak belge için bir düzen kilit içinde RDT ekler. Bir belgenin özel bir görünüm oluşturursanız, ancak, standart belge penceresi kullanmaz (diğer bir deyişle, uygulamıyor <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> arabirimi), ardından kendi düzenleme kilidi ayarlamanız gerekir. Örneğin, bir Sihirbazı'nda, bir düzenleyicide açılmış olmadan bir belge düzenlenmiştir. Belge kilit sihirbazlar ve benzer varlıklar tarafından açılması için sırada bu varlıkları uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> arabirimi. Belge kilit tutucusu kaydetmek için çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> yöntemi ve geçirin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> uygulaması. Bunun yapılması, belge kilit tutucusu için RDT ekler. Bir belge içinde bir özel araç penceresini açarsanız, belge kilit tutucusu uygulamak için başka bir senaryodur. Bu örnekte, belgeyi Kapat araç penceresi oluşturulamıyor. Ancak, bir belge kilit tutucusu RDT içinde olarak kaydederek IDE uygulamanıza çağırabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> yakın bir belgenin istemek için yöntemi.  
  
## <a name="other-uses-of-the-running-document-table"></a>Diğer kullanımları çalıştırılan Belge tablosu  
 IDE içindeki diğer varlıkların RDT belgeler hakkında bilgi almak için kullanın. Örneğin, Kaynak Denetim Yöneticisi'nde RDT sistemin bir belge düzenleyicisinde, dosyanın yeni sürümünü aldıktan sonra yeniden bildirmek için kullanır. Bunu yapmak için Kaynak Denetim Yöneticisi'nde herhangi biri açık olup olmadığını görmek için RDT dosyaları arar. Bunlar ardından kaynak denetimi Yöneticisi'nde ilk hiyerarşi uyguladığını görmek için denetler <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> yöntemi. Proje uygulamazsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> yöntemi ve kaynak denetim uygulaması Yöneticisi denetler <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> doğrudan belge veri nesnesi üzerinde yöntemi.  
  
 IDE RDT resurface için de kullanır (bir Öne Getir) bir kullanıcı belge isterse açık bir belgede. Daha fazla bilgi için [Aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Bir dosya içinde RDT açık olup olmadığını belirlemek için aşağıdakilerden birini yapın.  
  
-   Öğenin açık olup olmadığını öğrenmek belge ad (diğer bir deyişle, tam belge yolu) için sorgu.  
  
-   Proje sistemi için tam belge yolu isteyin ve ardından öğesi içinde RDT aramak için hiyerarşi veya öğe kimliği kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [RDT_ReadLock kullanımı](../../extensibility/internals/rdt-readlock-usage.md)   
 [Kalıcılık ve Çalıştırılan Belge Tablosu](../../extensibility/internals/persistence-and-the-running-document-table.md)

