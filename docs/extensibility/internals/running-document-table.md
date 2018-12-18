---
title: Belge tablosu çalıştıran | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a49a5267fcccbde60e194e3fc58b0f6b6ea7552
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134106"
---
# <a name="running-document-table"></a>Çalışan belge tablosu
IDE çalışan belge tablosu (RDT) olarak adlandırılan bir iç yapısındaki tüm açık belgelerin listesini tutar. Bu liste, bellekte olup bu belgeleri şu anda düzenlenmekte olan bağımsız olarak tüm açık belgeleri içerir. Kalıcı, dosyaları bir proje veya ana proje dosyası (örneğin, bir .vcxproj) dahil olmak üzere herhangi bir öğeyi belgedir.  
  
## <a name="elements-of-the-running-document-table"></a>Çalışan belge tablosu öğeleri  
 Çalışan belge tablosu aşağıdaki girdileri içerir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Belge ad|Belge verileri nesneyi benzersiz şekilde tanımlayan bir dize. Bu dosyaları (örneğin, C:\MyProject\MyFile) yöneten bir proje sistemine mutlak dosya yolunu olacaktır. Bu dize bir veritabanında depolanan yordamları gibi dosya sistemleri dışında mağazalarındaki kaydedilmiş projeleri için de kullanılır. Bu durumda, proje sistemi algılar ve belge depolamak nasıl belirlemek için büyük olasılıkla ayrıştırma benzersiz bir dize stok.|  
|Hiyerarşi sahibi|Belge tarafından temsil edilen sahibi olan hiyerarşi nesnesi bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirimi.|  
|Öğe kimliği|Hiyerarşi içindeki belirli bir öğenin öğe tanımlayıcısı. Bu değer bu belgenin sahibi hiyerarşideki tüm belgeler arasında benzersiz olduğundan, ancak bu değer farklı hiyerarşileri arasında benzersiz olması garanti edilmez.|  
|Belge veri nesnesi|En azından bu olan bir `IUnknown`<br /><br /> nesne. IDE herhangi belirli bir arabirim ötesinde gerektirmez `IUnknown` özel düzenleyicinin belge veri nesnesi için arabirim. Ancak, standart bir düzenleyici için düzenleyicisinin uyarlamasını <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> arabirimi projeye ait dosya Kalıcılık çağrıları işlemek için gereklidir. Daha fazla bilgi için bkz: [kaydetme bir standart belge](../../extensibility/internals/saving-a-standard-document.md).|  
|Bayraklar|Girişleri RDT eklendiğinde bir okuma veya düzenleme kilidi uygulanmış olup olmadığını denetleyen belge kaydedilip kaydedilmediğini bayrakları ve benzeri belirtilebilir. Daha fazla bilgi için bkz: <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> numaralandırması.|  
|Kilit sayısı Düzenle|Düzen sayısı kilitler. Bir düzen kilit bazı Düzenleyicisi belgeyi düzenlemek için açık olduğunu gösterir. Düzen kilit sayısı sıfır olarak geçiş yaptığında değiştirildi kullanıcı belgeyi kaydedin istenir. Örneğin, bir belge kullanarak bir düzenleyicide açın her zaman **yeni pencere** komutu, bir düzenleme kilit RDT bu belgede için eklenir. Ayarlanacak bir düzen kilitleme sırayla belge gerekir bir hiyerarşiye sahip veya kimliği öğesi|  
|Okuma kilit sayısı|Kilit sayısı okuyun. Belge bir sihirbaz gibi bazı mekanizması aracılığıyla okunduğu okuma kilidi gösterir. Okuma kilidi, belge düzenlenemez belirten çalışırken bir belge RDT canlı tutar. Belge olmayan bir hiyerarşiye sahip ya da kimliği öğesi olsa bile okuma kilidi ayarlayabilirsiniz Bu özellik, bellekte bir belgeyi açın ve herhangi bir hiyerarşi tarafından ait olan belge olmadan RDT girmek sağlar. Bu özellik nadiren kullanılır.|  
|Kilit sahibi|Örneği bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> arabirimi. Kilit sahibi belgeleri dışında bir düzenleyicide açıp sihirbazları gibi özellikler tarafından uygulanır. Kilit sahibi belgenin belge hala düzenleniyor sırada kapalı önlemek için bir düzen kilit eklemek bu özellik sağlar. Normalde, düzenleme kilitleri yalnızca belge pencereleri (diğer bir deyişle, düzenleyiciler) tarafından eklendi.|  
  
 Her giriş RDT benzersiz hiyerarşisi veya onunla ilişkili genellikle projesinde bir düğüme karşılık gelen öğe kimliği vardır. Düzenlemek için kullanılabilir tüm belgeler, tipik olarak bir hiyerarşi tarafından sahibi olur. RDT yapılan girişleri kontrol hangi proje veya — daha doğru bir şekilde — hangi hiyerarşi, şu anda düzenlenmekte olan belge veri nesnesi sahip. RDT bilgileri kullanarak, IDE aynı anda birden fazla proje tarafından açılmış bir belge engelleyebilir.  
  
 Hiyerarşi ayrıca verilerinin kalıcılığı denetler ve bilgileri güncelleştirmek için RDT kullanır **kaydetmek** ve **Kaydet** iletişim kutuları. Ne zaman kullanıcılar belge değiştirin ve ardından **çıkış** komutunu **dosya** menüsünde IDE ister bunlarla **Değişiklikleri Kaydet** tüm projeleri göstermek için iletişim kutusu ve şu anda değiştiren proje öğeleri. Bu belgeleri kaydetmek için hangisinin seçmelerini sağlar. Kaydetmek için belgeler listesine (değişikliklerinin bu belgeleri) RDT oluşturulur. İçinde görmeyi beklediğiniz tüm öğeleri **Değişiklikleri Kaydet** uygulama çıkarken iletişim kutusu RDT kayıtları olmalıdır. Hangi belgeler kaydedilir ve kaydetme hakkında kullanıcıya sorulmadan olup RDT koordinatları her belge için bayrakları girdisinde belirtilen değerleri kullanarak işlemi. RDT bayrakları hakkında daha fazla bilgi için bkz: <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> numaralandırması.  
  
## <a name="edit-locks-and-read-locks"></a>Düzen kilitleri ve okuma kilitleri  
 Düzen kilitleri ve okuma kilitleri RDT bulunur. Azaltır ve belge penceresi artışlarla düzenleme kilitleyin. Bu nedenle, yeni bir belge penceresi bir kullanıcı oturum açtığında, düzenleme kilit sayısı artışlarla tarafından. Düzenleme kilit sayısı sıfır ulaştığında, hiyerarşi devam veya ilişkili belge için verileri kaydetmek için sinyal gönderdi. Hiyerarşi sonra verileri bir dosya veya bir havuzda bir öğe olarak kalıcı yapma dahil olmak üzere herhangi bir şekilde kalıcı olmasını sağlayabilirsiniz. Kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> düzenleme kilitleri ekleyin ve kilitleri, okumak için arabirimi ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> bu kilitleri kaldırmak için yöntemi.  
  
 Normalde, bir düzenleyici belge penceresini örneği oluşturulduğunda pencere çerçevesi otomatik olarak belge için bir düzen kilit RDT ekler. Bir belgenin özel görünüm oluşturursanız, ancak, standart belge penceresine kullanmaz (uygulamayan diğer bir deyişle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> arabirimi), sonra da kendi düzenleme kilit ayarlamanız gerekir. Örneğin, bir Sihirbazı'nda bir düzenleyicide açık olmayan bir belge düzenlenmiştir. Sihirbazlar ve benzer varlıklar tarafından açılacak belge kilit için sırayla bu varlıkları uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> arabirimi. Belge kilit sahibi kaydetmek için arama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> yöntemi ve geçişinde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> uygulaması. Bunun yapılması, belge kilit sahibi RDT ekler. Bir belge kilit sahibi uygulamak için başka bir özel araç penceresi aracılığıyla bir belge açarsanız senaryodur. Bu örnekte, belgeyi Kapat aracı penceresi oluşturulamıyor. Ancak, bir belge kilit sahibi RDT içinde olarak kaydederek IDE uygulamanıza çağırabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> belgenin bir kapanış isteyecek şekilde yöntemi.  
  
## <a name="other-uses-of-the-running-document-table"></a>Diğer kullanımları çalışan belge tablosu  
 IDE içinde diğer varlıklar RDT belgeler hakkında bilgi almak için kullanın. Örneğin, Kaynak Denetim Yöneticisi'nde, dosyayı en yeni sürümünü aldıktan sonra düzenleyicisinde, bir belgeyi yeniden sisteme bildirmek için RDT kullanır. Bunu yapmak için Kaynak Denetim Yöneticisi'nde herhangi biri açık olup olmadığını görmek için RDT dosyaları arar. Bunlar sonra Kaynak Denetim Yöneticisi'ni ilk hiyerarşi uyguladığını bakar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> yöntemi. Proje uygulamazsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> yöntemi ve Kaynak Denetim Yöneticisi denetimleri bir uygulama için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> doğrudan belge veri nesnesi üzerinde yöntemi.  
  
 IDE RDT resurface için de kullanır (öne) bir kullanıcı bu belgeyi isterse açık bir belge. Daha fazla bilgi için bkz: [açık dosya komutunu kullanarak görüntüleme dosyaları](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Bir dosyanın RDT açık olup olmadığını belirlemek için aşağıdakilerden birini yapın.  
  
-   Öğesi açık olup olmadığını öğrenmek belge bilinen ad (diğer bir deyişle, tam belge yol) için sorgu.  
  
-   Proje sistemi için tam belge yolu isteyin ve sonra RDT öğesi arayın veya öğesi hiyerarşi kimliği kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [RDT_ReadLock kullanımı](../../extensibility/internals/rdt-readlock-usage.md)   
 [Kalıcılık ve Çalıştırılan Belge Tablosu](../../extensibility/internals/persistence-and-the-running-document-table.md)