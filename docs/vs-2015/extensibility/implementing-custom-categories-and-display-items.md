---
title: Uygulama özel kategoriler ve öğeleri görüntüleme | Microsoft Docs
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
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 394f8f99539ab49c1201fa61ce612aee22ff2064
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769122"
---
# <a name="implementing-custom-categories-and-display-items"></a>Uygulama özel kategoriler ve öğeleri görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage denetim yazı tipleri ve renkler için kendi metin sağlayabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] özel kategoriler ve görüntü öğeleri aracılığıyla tümleşik geliştirme ortamı (IDE).  
  
 Özel kategorileri ve görüntü öğeleri olan **yazı tipleri ve renkler** özellik sayfası. Açmak için **yazı tipleri ve renkler** özellik sayfasında **Araçları** menüsünde tıklatın **seçenekleri**. Genişletin **ortam** ve ardından **yazı tipleri ve renkler**.  
  
 Bu mekanizma kullanırken VSPackage'ları uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> ve onun ilişkili arabirim.  
  
 Bu mekanizma İlkesi, tüm mevcut değiştirmek için kullanılabilir **görüntü öğeleri** ve **kategorileri** bunları içeren. Ancak onu değiştirmek için kullanılmamalıdır **metin EditorCategory** veya kendi **görüntü öğeleri**. Daha fazla bilgi için [yazı tipi ve renk genel bakış](../extensibility/font-and-color-overview.md).  
  
 Özel uygulamak için **kategorileri** veya **görüntü öğeleri**, VSPackage gerekir:  
  
- Oluşturma veya kayıt defterinde kategorileri tanımlama.  
  
   IDE'nin uygulaması **yazı tipleri ve renkler** özellik sayfası, belirli bir kategori destekleyen hizmeti için doğru bir şekilde sorgulamak için bu bilgileri kullanır.  
  
- Oluşturma veya kayıt defterinde grupları (isteğe bağlı) tanımlama.  
  
   İki veya daha fazla kategori birleşimini gösteren bir grup tanımlamak yararlı olabilir. Bir grubu tanımlanmazsa, IDE, otomatik olarak alt kategorileri birleştirir ve grup içindeki öğeleri görüntüle dağıtır.  
  
- IDE desteği uygulayın.  
  
- Yazı tipi ve renk değişiklikleri işleyin.  
  
  Bilgi için [erişme depolanan yazı tipi ve renk ayarlarını](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Oluşturma veya kategori tanımlamak için  
  
- Özel bir kategori altında kayıt defteri girdisi türü oluşturun [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio sürümü >* \FontAndColors\\`<Category>`]  
  
   *\<Kategori >* kategorisi yerelleştirilmemiş adıdır.  
  
- Kayıt defteri iki değerlerle doldurun:  
  
  |Ad|Tür|Veri|Açıklama|  
  |----------|----------|----------|-----------------|  
  |Kategori|REG_SZ|GUID|Kategori tanımlamak için bir GUID oluşturulur.|  
  |Paket|REG_SZ|GUID|Kategori destekleyen VSPackage hizmeti GUİD'si.|  
  
  Kayıt defterinde belirtilen hizmet uygulaması sağlamalısınız <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> karşılık gelen bir kategorisi için.  
  
## <a name="to-create-or-identify-groups"></a>Oluşturma veya grupları tanımlamak için  
  
- Özel bir kategori altında kayıt defteri girdisi türü oluşturun [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio sürümü >* \FontAndColors\\  *\<grup >*]  
  
   *\<Grup >* yerelleştirilmemiş grubunun adıdır.  
  
- Kayıt defteri iki değerlerle doldurun:  
  
  |Ad|Tür|Veri|Açıklama|  
  |----------|----------|----------|-----------------|  
  |Kategori|REG_SZ|GUID|Grubu tanımlamak için bir GUID oluşturulur.|  
  |Paket|REG_SZ|GUID|Kategori destekleyen hizmeti GUİD'si.|  
  
  Kayıt defterinde belirtilen hizmet uygulaması sağlamalısınız `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` ilgili grup.  
  
## <a name="to-implement-ide-support"></a>IDE desteği uygulamak için  
  
- Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, ya da döndüren bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> arabirimi veya `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` IDE her arabirimi **kategori** veya sağlanan GUID grubu.  
  
- İçin her **kategori** destekliyorsa, ayrı bir örneğini bir VSPackage'ı uygulayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> arabirimi.  
  
- Yöntemleri aracılığıyla uygulanan <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> IDE ile sağlamanız gerekir:  
  
  -   Listesini **görüntü öğeleri** içinde **kategorisi.**  
  
  -   Yerelleştirilebilir adlarını **görüntü öğeleri**.  
  
  -   Her üye için bilgi görüntüler **kategori**.  
  
  > [!NOTE]
  >  Her **kategori** en az bir içeren **görüntü öğesi**.  
  
- IDE kullanır `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` çeşitli kategorileri birleşimini tanımlamak için arabirim.  
  
   Uygulaması ile bir IDE sağlar:  
  
  -   Listesini **kategorileri** belirli bir grup oluşturur.  
  
  -   Erişim örneklerini <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> her Destek **kategori** grup içinde.  
  
  -   Yerelleştirilebilir grubu adları.  
  
- IDE güncelleştiriliyor:  
  
   IDE hakkındaki bilgileri saklar **yazı tipi ve renk** ayarları. Bu nedenle, IDE'nin herhangi bir değişiklikten sonra **yazı tipi ve renk** yapılandırması önerilir önbelleği güncel olduğundan emin olmak için.  
  
  Önbelleği güncelleştiriliyor aracılığıyla gerçekleştirilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> arabirim ve gerçekleştirilen genel veya açık yalnızca seçilen öğeleri olabilir.  
  
## <a name="to-handle-font-and-color-changes"></a>Yazı tipi ve renk işlemek için değişiklikler  
 VSPackage görüntülenen metin renklendirmesi doğru desteklemek için VSPackage'ı destekleyen renklendirme hizmeti aracılığıyla yapılan kullanıcı tarafından başlatılan değişiklikleri yanıtlamalıdır **yazı tipleri ve renkler** Özellikler sayfası. VSPackage bunu şu şekilde yapar:  
  
-   Uygulayarak IDE tarafından oluşturulan olayları işleme <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> arabirimi.  
  
     IDE kullanıcı değişiklik aşağıdaki uygun yöntemi çağıran **yazı tipleri ve renkler** sayfası. Örneğin, çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> yeni bir yazı tipi seçtiyseniz yöntemi.  
  
     veya  
  
-   IDE değişiklikleri için yoklama.  
  
     Bu sistem uygulanan yapılabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> arabirimi. Öncelikle desteği için Kalıcılık, ancak <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> yöntemi, yazı tipi ve renk bilgilerini almak için kullanılabilir **görüntü öğeleri**. Daha fazla bilgi için [erişme depolanan yazı tipi ve renk ayarlarını](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    >  Emin olmak için yoklama işlemi tarafından elde edilen sonuçları doğru olduğundan, kullanmak yararlı olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> önbellek temizleme ve güncelleştirme alma yöntemleri çağrılmadan önce gerekli olup olmadığını belirlemek için arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Yazı tipi ve metin renklendirmesi için renk bilgilerini alma](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Saklı yazı tipi ve renk ayarlarını erişme](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Nasıl yapılır: yerleşik yazı tipi ve renk şeması erişim](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Yazı Tipi ve Renklere Genel Bakış](../extensibility/font-and-color-overview.md)

