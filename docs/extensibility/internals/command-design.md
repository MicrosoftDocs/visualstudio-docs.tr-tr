---
title: Komut tasarımı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5bd810d0c2f33d4a8ddbffd876357ead7e0e5e7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816514"
---
# <a name="command-design"></a>Komut tasarımı
Bir komut için bir VSPackage'ı eklediğinizde, görüntülenecek olduğu, kullanılabilir olduğunda ve nasıl işleneceğini olduğunu belirtmeniz gerekir.  
  
## <a name="define-commands"></a>Komutlar tanımlayın  
 Yeni komutlar tanımlamak için Visual Studio komut tablosu içerir (*.vsct*) VSPackage projenizdeki dosya. Visual Studio Paket şablonu kullanarak bir VSPackage oluşturduysanız, bu dosyalardan biri proje içerir. Daha fazla bilgi için [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio tüm birleştirir *.vsct* komutları görüntüleyebilmesi bu dosyaları bulur. Bu dosyalar ikili VSPackage farklı olduğundan, Visual Studio komutları paketi yok. Daha fazla bilgi için [nasıl VSPackages kullanıcı arabirimi öğeleri ekleyebilir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio kullanan <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> menüsü kaynaklarını ve komutları tanımlayan kayıt öznitelik. Daha fazla bilgi için [komut uygulama](../../extensibility/internals/command-implementation.md).  
  
 Komutlar, çalışma zamanında bir dizi farklı yolla değiştirilebilir. Bunlar gösterilen veya gizli, devre dışı bırakabilir veya etkinleştirilebilir. Bunlar farklı metin veya simgelerini görüntülemek veya farklı değerler içerir. Visual Studio, VSPackage'ı yüklemeden önce özelleştirme büyük ölçüde gerçekleştirilebilir. Daha fazla bilgi için [nasıl VSPackages kullanıcı arabirimi öğeleri ekleyebilir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Komut işleyicileri  
 Bir komut oluşturduğunuzda komutu yürütmek için bir olay işleyicisi sağlamanız gerekir. Kullanıcı komutu seçtiğinde, uygun şekilde yönlendirilmelidir. Bir komut yönlendirme etkinleştirmek veya devre dışı bırakmak, gizleme veya görüntülemek ve kullanıcı bunu yapmak seçerse çalıştırmak için doğru VSPackage gönderme anlamına gelir. Daha fazla bilgi için [komut yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="visual-studio-command-environment"></a>Visual Studio komut ortamı  
 Visual Studio VSPackages herhangi bir sayıda barındırabilir ve her biri kendi komut kümesi katkıda bulunabilir. Ortamın geçerli görev için uygun olan komutları görüntüler. Daha fazla bilgi için [komutu kullanılabilirlik](../../extensibility/internals/command-availability.md) ve [seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md).  
  
 Yeni komutlar, menüler, araç çubukları veya kısayol menüleri tanımlayan bir VSPackage'ı yerel veya yönetilen bütünleştirilmiş kodlar içindeki kaynaklara başvuran bir kayıt defteri girdileri ile yükleme sırasında Visual Studio için komut bilgileri sağlar. Her kaynak sonra bir ikili veri kaynağa başvuruda (*.cto*), Visual Studio komut tablosu derlerken, üretilen dosya (*.vsct*) dosyası. Bu birleştirilmiş komut kümelerini, menüleri ve araç çubuklarını yüklü her VSPackage'ı yüklemek zorunda kalmadan sağlamak Visual Studio sağlar.  
  
### <a name="command-organization"></a>Komut kuruluş  
 Ortam, grubu, öncelik ve menü komutları yerleştirir.  
  
- Grupları mantıksal koleksiyonlarıdır ilgili komutlar, örneğin, **Kes**, **kopyalama**, ve **Yapıştır** komut grubu. Menülerde görünür komutları gruplarıdır.  
  
- Öncelik grubundaki tek tek komutlarla menüsünde görünme sırasını belirler.  
  
- Menü grupları için kapsayıcı görevi görür.  
  
  Ortamın bazı komutlar, grupları ve menüler önceden belirler. Daha fazla bilgi için [varsayılan komut, Grup ve araç çubuğu yerleştirme](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Bir komutu bir birincil grubu olarak atanabilir. Ana menü yapısı ve komut konumunu birincil grup denetimleri **Özelleştir** iletişim kutusu. Bir komutu birden çok grupta yer görünebilir; Örneğin, bir komut ana menüsündeki kısayol menüsünde ve araç çubuğundaki olabilir. Daha fazla bilgi için [nasıl VSPackages kullanıcı arabirimi öğeleri ekleyebilir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Komut yönlendirme  
 Nesne örneklerinde metotları çağırma işleminin çağırma ve komutları Vspackage'lar için yönlendirme işlemi farklıdır.  
  
 Ortam, en dıştaki (Genel) bağlam sıralı olarak geçerli seçime göre en içteki (yerel) komut içeriğinden komutları yönlendirir. Komutu yürütebilmek için olan ilk bağlam işleme sertifikadır. Daha fazla bilgi için [komut yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md).  
  
 Çoğu durumda, ortam komutlarını kullanarak işleme <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi. Komut yönlendirme şeması komutları işlemek birçok farklı nesne sağladığından <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> herhangi bir sayıda nesneleri uygulanması olabilir; bunlar dahil Microsoft ActiveX denetimleri, pencere görünümü uygulamaları, belge nesneleri, proje hiyerarşileri VSPackage için ve nesneleri kendilerini (genel komutları). Bazı özel durumlarda, örneğin, bir hiyerarşide komutları yönlendirme <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirimi uygulanmış.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Komut uygulama](../../extensibility/internals/command-implementation.md)|VSPackage'ı komutları uygulamak açıklar.|  
|[Komut kullanılabilirliği](../../extensibility/internals/command-availability.md)|Visual Studio bağlam hangi komutları kullanılabilir etiketleneceğini nasıl açıklar.|  
|[Komut yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md)|Visual Studio komut yönlendirme mimarisi farklı VSPackage'ları tarafından işlenecek komutları nasıl sağladığını açıklar.|  
|[Komut yerleştirme yönergeleri](../../extensibility/internals/command-placement-guidelines.md)|Visual Studio ortamında komutları konumlandırmak nasıl önerir.|  
|[VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|VSPackage en iyi kullanarak Visual Studio komut mimarisi nasıl açıklar.|  
|[Varsayılan komut, Grup ve araç çubuğu yerleştirme](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Nasıl VSPackages Visual Studio'ya dahil olan komutları en iyi şekilde kullanabileceğinizi açıklar.|  
|[VSPackage'ları yönetme](../../extensibility/managing-vspackages.md)|Visual Studio VSPackages nasıl yüklenir açıklar.|  
|[Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|XML-tabanlı hakkında bilgi sağlar *.vsct* düzeninin ve görünümünün vspackage'larda komut açıklamak için kullanılan dosya.|