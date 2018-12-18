---
title: Komut tasarımı | Microsoft Docs
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
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9aed86eef616702363a661ece0ab565a768f2f75
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750128"
---
# <a name="command-design"></a>Komut Tasarımı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir komut için bir VSPackage'ı eklediğinizde, görüntülenecek olduğu, kullanılabilir olduğunda ve nasıl işleneceğini olduğunu belirtmeniz gerekir.  
  
## <a name="defining-commands"></a>Komutlarını tanımlama  
 Yeni komutlar tanımlamak için VSPackage projenizde Visual Studio komut tablosu (.vsct) dosyası içerir. Visual Studio Paket şablonu kullanarak bir VSPackage oluşturduysanız, bu dosyalardan biri proje içerir. Daha fazla bilgi için [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio komutları görüntüleyebilmesi bulduğu tüm .vsct dosyaları birleştirir. Bu dosyalar ikili VSPackage farklı olduğundan, Visual Studio komutları paketi yok. Daha fazla bilgi için [nasıl VSPackages Ekle kullanıcı arabirimi öğeleri](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio kullanan <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> menüsü kaynaklarını ve komutları tanımlayan kayıt öznitelik. Daha fazla bilgi için [uygulama](../../extensibility/internals/command-implementation.md).  
  
 Komutlar, çalışma zamanında bir dizi farklı yolla değiştirilebilir. Bunlar gösterilen veya gizli, devre dışı bırakabilir veya etkinleştirilebilir. Bunlar farklı metin veya simgelerini görüntülemek veya farklı değerler içerir. Visual Studio, VSPackage'ı yüklemeden önce özelleştirme büyük ölçüde gerçekleştirilebilir. Daha fazla bilgi için [nasıl VSPackages Ekle kullanıcı arabirimi öğeleri](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Komut işleyicileri  
 Bir komut oluşturduğunuzda komutu yürütmek için bir olay işleyicisi sağlamanız gerekir. Kullanıcı komutu seçtiğinde, uygun şekilde yönlendirilmelidir. Bir komut yönlendirme etkinleştirmek veya devre dışı bırakmak, gizleme veya görüntülemek ve kullanıcı bunu yapmak seçerse çalıştırmak için doğru VSPackage gönderme anlamına gelir. Daha fazla bilgi için [yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Visual Studio komut ortamı  
 Visual Studio VSPackages herhangi bir sayıda barındırabilir ve her biri kendi komut kümesi katkıda bulunabilir. Ortamın geçerli görev için uygun olan komutları görüntüler. Daha fazla bilgi için [kullanılabilirlik](../../extensibility/internals/command-availability.md) ve [seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md).  
  
 Yeni komutlar, menüler, araç çubukları veya kısayol menüleri tanımlayan bir VSPackage'ı yerel veya yönetilen bütünleştirilmiş kodlar içindeki kaynaklara başvuran bir kayıt defteri girdileri ile yükleme sırasında Visual Studio için komut bilgileri sağlar. Her kaynak bir Visual Studio komut tablosu (.vsct) dosyası derleme yaparken, üretilen ikili verileri (.cto) kaynak dosyası, ardından başvuruyor. Bu birleştirilmiş komut kümelerini, menüleri ve araç çubuklarını yüklü her VSPackage'ı yüklemek zorunda kalmadan sağlamak Visual Studio sağlar.  
  
### <a name="command-organization"></a>Komut kuruluş  
 Ortam, grubu, öncelik ve menü komutları yerleştirir.  
  
- Grupları mantıksal koleksiyonlarıdır ilgili komutlar, örneğin, **Kes**, **kopyalama**, ve **Yapıştır** komut grubu. Menülerde görünür komutları gruplarıdır.  
  
- Öncelik grubundaki tek tek komutlarla menüsünde görünme sırasını belirler.  
  
- Menü grupları için kapsayıcı görevi görür.  
  
  Ortamın bazı komutlar, grupları ve menüler önceden belirler. Daha fazla bilgi için [varsayılan komut, Grup ve araç çubuğu yerleştirme](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Bir komutu bir birincil grubu olarak atanabilir. Ana menü yapısı ve komut konumunu birincil grup denetimleri **Özelleştir** iletişim kutusu. Bir komutu birden çok grupta yer görünebilir; Örneğin, bir komut ana menüsündeki kısayol menüsünde ve araç çubuğundaki olabilir. Daha fazla bilgi için [nasıl VSPackages Ekle kullanıcı arabirimi öğeleri](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Komut Yönlendirme  
 Nesne örneklerinde metotları çağırma işleminin çağırma ve komutları Vspackage'lar için yönlendirme işlemi farklıdır.  
  
 Ortam, en dıştaki (Genel) bağlam sıralı olarak geçerli seçime göre en içteki (yerel) komut içeriğinden komutları yönlendirir. Komutu yürütebilmek için olan ilk bağlam işleme sertifikadır. Daha fazla bilgi için [yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md).  
  
 Çoğu durumda, ortam komutlarını kullanarak işleme <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi. Komut yönlendirme şeması komutları işlemek birçok farklı nesne sağladığından <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> herhangi bir sayıda nesneleri uygulanması olabilir; bunlar dahil Microsoft ActiveX denetimleri, pencere görünümü uygulamaları, belge nesneleri, proje hiyerarşileri VSPackage için ve nesneleri kendilerini (genel komutları). Bazı özel durumlarda, örneğin, bir hiyerarşide komutları yönlendirme <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirimi uygulanmış.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Uygulama](../../extensibility/internals/command-implementation.md)|VSPackage'ı komutları uygulamak açıklar.|  
|[Kullanılabilirlik](../../extensibility/internals/command-availability.md)|Visual Studio bağlam hangi komutları kullanılabilir etiketleneceğini nasıl açıklar.|  
|[Yönlendirme Algoritması](../../extensibility/internals/command-routing-algorithm.md)|Visual Studio komut yönlendirme mimarisi farklı VSPackage'ları tarafından işlenecek komutları nasıl sağladığını açıklar.|  
|[Yerleştirme Yönergeleri](../../extensibility/internals/command-placement-guidelines.md)|Visual Studio ortamında komutları konumlandırmak nasıl önerir.|  
|[VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|VSPackage en iyi kullanarak Visual Studio komut mimarisi nasıl açıklar.|  
|[Varsayılan Komut, Grup ve Araç Çubuğu Yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Nasıl VSPackages Visual Studio'ya dahil olan komutları en iyi şekilde kullanabileceğinizi açıklar.|  
|[VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)|Visual Studio VSPackages nasıl yüklenir açıklar.|  
|[Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Vspackage'larda komut Görünüm ve düzeninin açıklamak için kullanılan XML tabanlı .vsct dosyaları hakkında bilgi sağlar.|

