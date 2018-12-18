---
title: Saklı yazı tipi ve renk ayarlarını erişme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 953f74b309d8dc147d04d86b843f138002de972f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910686"
---
# <a name="access-stored-font-and-color-settings"></a>Yazı tipi ve renk ayarlarını erişim depolanan
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı (IDE) depolar değiştirilen ayarların yazı tipi ve renkler kayıt defterinde. Kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> bu ayarlara erişmek için arabirim.

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Yazı tipleri ve renkler durumu kalıcılığını başlatmak için
 Yazı tipi ve renk bilgileri, aşağıdaki kayıt defteri konumunda kategoriye göre depolanır: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio sürümü >* \FontAndColors\\  *\<CategoryGUID >*] burada  *\<CategoryGUID >* GUID kategorisidir.

 Bu nedenle, Kalıcılık başlatmak için bir VSPackage gerekir:

-   Elde bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> çağırarak arabirim `QueryService` küresel hizmet sağlayıcısına.

     `QueryService` bir hizmet kimliği bağımsız değişkeni kullanılarak çağrılmalıdır `SID_SVsFontAndColorStorage` ve arabirimi kimliği bağımsız değişkeninin `IID_IVsFontAndColorStorage`.

-   Kullanım <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> bağımsız değişken olarak kategorinin GUID ve modu bayrağını kullanarak kalıcı için bir kategori açmak için yöntemi.

     Tarafından belirtilen modu `fFlags` değerden bağımsız değişkeni, oluşturulan <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> sabit listesi. Bu modu denetler:

    -   Erişilebilir ayarları <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> arabirimi.

    -   Tüm ayarları veya kullanıcıları değiştirin ve aracılığıyla alınabilir olan yalnızca bu ayarları <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> arabirimi.

    -   Değişiklikleri kullanıcı ayarlarına yayma şekilde.

    -   Kullanılan renk değerleri biçimi.

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Yazı tipleri ve renkler durumu kalıcılığını kullanmak için
 Kalıcı yazı tipleri ve renkler içerir:

- Kayıt defterinde depolanan ayarlarla IDE ayarları eşitleniyor.

- Kayıt defteri değişikliği bilgilerini yayılıyor.

- Ayarlama ve kayıt defterinde depolanan ayarları alınıyor.

  IDE ayarları ile depolama ayarını eşitleme büyük ölçüde saydamdır. Temel IDE için güncelleştirilmiş ayarları otomatik olarak Yazar **görünen öğeler** kategoriler kayıt defteri girişleri.

  Birden çok VSPackages belirli bir kategoriye paylaşıyorsanız, VSPackage olaylar oluşturulur gerektirmelidir olduğunda yöntemlerinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> arabirimi depolanmış kayıt defteri ayarlarını değiştirmek için kullanılır.

  Varsayılan olarak, olay oluşturma etkin değil. Olay oluşturma etkinleştirmek için bir kategori kullanarak açılmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Bir kategori açma neden uygun çağırmak IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> bir VSPackage'ı uygulayan bir yöntem.

> [!NOTE]
>  Değişiklikleri **yazı tipi ve renk** özellik sayfası oluşturma bağımsız olayları <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> yöntemleri çağrılmadan önce önbelleğe alınmış yazı tipi ve renk ayarlarını güncelleştirmesi gerekli olup olmadığını belirlemek için arabirim <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> sınıfı.

### <a name="store-and-retrieve-information"></a>Store ve bilgileri alınamıyor
 VSPackage elde etmek veya bir kullanıcı için açık bir kategorideki bir adlandırılmış görüntü öğesini değiştirebilirsiniz bilgi yapılandırmak için çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> yöntemleri.

 Yazı tipi hakkında bilgi için belirli bir kategoriye kullanılarak elde öznitelikleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> yöntemleri.

> [!NOTE]
>  `fFlags` Geçirilen bağımsız değişken <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> kategori açıldığında yöntemi davranışını tanımlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> yöntemleri. Varsayılan olarak, bu yöntemler, yalnızca değişen öğeleri görüntüleme hakkında bilgi döndürür. Ancak, bir kategori kullanarak açtıysanız <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> bayrak, hem güncelleştirildi ve değişmeden görünen öğeler tarafından erişilebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.

 Varsayılan olarak, yalnızca değiştirilen **görünen öğeler** bilgileri, kayıt defterinde tutulur. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Arabirimi, yazı tipleri ve renkler için tüm ayarları almak için kullanılamaz.

> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> Ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> yöntemleri REGDB_E_KEYMISSING, (bilgi almaya kullanıldıklarında 0x80040152L) hakkında değişmeden döndürür **görünen öğeler**.

 Tüm ayarları **görünen öğeler** belirli bir **kategori** yöntemleri kullanılarak elde edilebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> arabirimi.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [Özel kategoriler uygulamak ve öğeleri görüntüleme](../extensibility/implementing-custom-categories-and-display-items.md)