---
title: Saklı yazı tipi ve renk ayarlarını erişme | Microsoft Docs
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
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee5ed57639127bd6c30d2e7e1373a56848eca504
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772826"
---
# <a name="accessing-stored-font-and-color-settings"></a>Saklı yazı tipi ve renk ayarlarını erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tümleşik geliştirme ortamı (IDE) depolar değiştirilen ayarların yazı tipi ve renkler kayıt defterinde. Kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> bu ayarlara erişmek için arabirim.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Yazı tipleri ve renkler durum Kalıcılığına başlatmak için  
 Yazı tipi ve renk bilgileri, aşağıdaki kayıt defteri konumunda kategoriye göre depolanır: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio sürümü >* \FontAndColors\\  *\<CategoryGUID >*] burada  *\<CategoryGUID >* GUID kategorisidir.  
  
 Bu nedenle, Kalıcılık başlatmak için bir VSPackage gerekir:  
  
-   Elde bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> çağırarak arabirim `QueryService` küresel hizmet sağlayıcısına.  
  
     `QueryService` bir hizmet kimliği bağımsız değişkeni kullanılarak çağrılmalıdır `SID_SVsFontAndColorStorage` ve arabirimi kimliği bağımsız değişkeninin `IID_IVsFontAndColorStorage`.  
  
-   Kullanım <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> bağımsız değişken olarak kategorinin GUID ve modu bayrağını kullanarak kalıcı için bir kategori açmak için yöntemi.  
  
     Tarafından belirtilen modu `fFlags` değerden bağımsız değişkeni, oluşturulan <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> sabit listesi. Bu modu denetler:  
  
    -   Erişilebilir ayarları <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> arabirimi.  
  
    -   Tüm ayarları veya yalnızca kullanıcıları değiştiren ve aracılığıyla alınabilir olan <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> arabirimi.  
  
    -   Değişiklikleri kullanıcı ayarlarına yayma şekilde.  
  
    -   Kullanılan renk değerleri biçimi.  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Yazı tipleri ve renkler durum Kalıcılığına kullanmak için  
 Kalıcı yazı tipleri ve renkler içerir:  
  
- Kayıt defterinde depolanan ayarlarla IDE ayarları eşitleniyor.  
  
- Kayıt defteri değişikliği bilgilerini yayılıyor.  
  
- Ayarlama ve kayıt defterinde depolanan ayarları alınıyor.  
  
  IDE ayarları ile depolama ayarını eşitleme büyük ölçüde saydamdır. Temel IDE için güncelleştirilmiş ayarları otomatik olarak Yazar **görünen öğeler** kategoriler kayıt defteri girişleri.  
  
  Birden çok VSPackages belirli bir kategoriye paylaşıyorsanız, VSPackage olaylar oluşturulur gerektirmelidir olduğunda yöntemlerinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> arabirimi depolanmış kayıt defteri ayarlarını değiştirmek için kullanılır.  
  
  Varsayılan olarak, olay oluşturma etkin değil. Olay oluşturma etkinleştirmek için bir kategori kullanarak açılmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Bu uygun çağırmak IDE neden <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> bir VSPackage'ı uygulayan bir yöntem.  
  
> [!NOTE]
>  Değişiklikleri **yazı tipi ve renk** özellik sayfası oluşturma bağımsız olayları <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> yöntemleri çağrılmadan önce önbelleğe alınmış yazı tipi ve renk ayarlarını güncelleştirmesi gerekli olup olmadığını belirlemek için arabirim <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> sınıfı.  
  
### <a name="storing-and-retrieving-information"></a>Depolama ve bilgileri alınıyor  
 VSPackage elde etmek veya bir kullanıcı için açık bir kategorideki bir adlandırılmış görüntü öğesini değiştirebilirsiniz bilgi yapılandırmak için çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> yöntemleri.  
  
 Yazı tipi hakkında bilgi için belirli bir kategoriye kullanılarak elde öznitelikleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> yöntemleri.  
  
> [!NOTE]
>  `fFlags` Geçirilen bağımsız değişken <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> kategori açıldığında yöntemi davranışını tanımlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> yöntemleri. Varsayılan olarak, bu yöntemler yalnızca dönüş bilgi aboutdisplay itemsthat değişti. Ancak, bir kategori kullanarak açtıysanız <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> bayrak, hem güncelleştirildi ve değişmeden görünen öğeler tarafından erişilebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.  
  
 Varsayılan olarak, yalnızca değiştirilen **görünen öğeler** bilgileri, kayıt defterinde tutulur. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Arabirimi, yazı tipleri ve renkler için tüm ayarları almak için kullanılamaz.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> Ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> yöntemleri REGDB_E_KEYMISSING, (bilgi almaya kullanıldıklarında 0x80040152L) hakkında değişmeden döndürür **görünen öğeler**.  
  
 Tüm ayarları **görünen öğeler** belirli bir **kategori** yöntemleri kullanılarak elde edilebilir `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Özel Kategoriler ve Görüntüleme Öğeleri Uygulama](../extensibility/implementing-custom-categories-and-display-items.md)

