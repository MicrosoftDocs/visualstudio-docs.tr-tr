---
title: Ayarlar kategorileri için destek | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- settings, supporting with Visual Studio SDK
- Visual Studio SDK, supporting settings
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
manager: douge
ms.openlocfilehash: 53abd3c9f35f16c2f2ae62e2c4f339a86477a8b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244939"
---
# <a name="support-for-settings-categories"></a>Ayarlar kategorileri için destek
Ayarları kategorisi tümleşik geliştirme ortamı (IDE) özelleştirme seçenekleri grubundan oluşur. Örneğin, ayarları düzenini denetleyebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] windows ve menüler içeriği. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Üzerinde **Araçları** menüsünü tıklatın **içeri ve dışarı aktarma ayarları** başlatmak için **içeri ve dışarı aktarma ayarları Sihirbazı**. Sihirbaz üç seçenek sunar: dışarı aktarma, alma veya ayarlarınızı sıfırlayın. Dışarı aktarma seçerek, örneğin, açılır **dışarı aktarma ayarlarını seçin** Sihirbazı sayfası.  
  
 Bu sayfanın gezinti bölmesindeki ağaç denetimi kategorilerini listeler. Bir kategori olan bir "özel ayarları noktası olarak", diğer bir deyişle, bir onay kutusu olarak görünmesini ilgili ayarları grubudur. .Vsettings dosyada kalıcı hale getirmek için bir kategori seçmek için bu onay kutularını kullanın. Sihirbaz, .vsettings dosya adı ve yolu belirtin sağlar.  
  
> [!NOTE]
>  Ayarlar kaydedildi veya kategori olarak geri ve tek ayar adları Sihirbazı'nda görüntülenmez.  
  
 Yönetilen paket çerçevesini (MPF) en az ek kod oluşturma ayarlarını kategorileri destekler.  
  
-   Kategori için bir kapsayıcı tarafından sınıflara sağlamak VSPackage oluşturduğunuz <xref:Microsoft.VisualStudio.Shell.Package> sınıfı.  
  
-   Türevi göre kategorisi oluşturma gelen <xref:Microsoft.VisualStudio.Shell.DialogPage> sınıfı.  
  
-   İki bağlantı <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="support-for-settings-categories"></a>Ayarlar kategorileri için destek  
 <xref:Microsoft.VisualStudio.Shell.Package> Sınıfı kategoriler oluşturmak için destek sağlar. <xref:Microsoft.VisualStudio.Shell.DialogPage> Sınıfı bir kategori uygular. Varsayılan uygulaması <xref:Microsoft.VisualStudio.Shell.DialogPage> bir kategori olarak kullanıcıya genel özelliklerini sunar. Daha fazla bilgi için [ayarları kategorisi oluşturma](../extensibility/creating-a-settings-category.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Sınıfının Implements <xref:Microsoft.VisualStudio.Shell.IProfileManager>, Seçenekler sayfaları ve kullanıcı ayarları için Kalıcılık sağlar. <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> Ve <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> yöntemleri kalıcı bir .vssettings ayarlarına dosya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] olarak sağlayan bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>sırasıyla. <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> Yöntemi ayarları varsayılan değerlerine sıfırlar.  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Sınıfı uygulanmasını sağlar <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> akışı XML'den ad-değer çiftlerini okur ve yansıma genel özelliklerini bulmak için kullandığı yöntem <xref:Microsoft.VisualStudio.Shell.DialogPage> türetilmiş sınıf. Ad-değer çiftleri eşleşen adlara sahip özellikler, karşılık gelen değerler olarak verilir.  
  
 Varsayılan uygulaması <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> genel özelliklerini bulmak için yansıtma kullanır <xref:Microsoft.VisualStudio.Shell.DialogPage> türetilmiş bir sınıf ve özellik adlarını ve değerlerini ad-değer çiftleri olarak XML akışa yazar.  
  
### <a name="settings-category-registry-path"></a>Ayarları kategorisi kayıt defteri yolu  
 Kayıt defteri yolu ayarları kategorisi birleştirerek belirlenir <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, word, kullanıcı ayarlarını, ayarları kategorisi ve özel ayarları noktası adı. Ayarları kategorisi ve özel ayarları noktası adlarını alanına ve kayıt defterinde görüntülenen canonical, yerelleştirilmemiş adı oluşturmak için bir alt çizgi ile ayrılmış. Örneğin, ayarları kategorisi "My Category" ise, özel ayarları ApplicationRegistryRoot HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp yanı sıra adı "My ayarları"'ye gelin ve kayıt defteri anahtarı HKEY_LOCAL_ ayarları kategorisi vardır MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\My Category_My ayarları.  
  
> [!NOTE]
>  Kurallı ad, kullanıcı arabiriminde (UI) görünmüyor. Okunabilir bir adı bir programlı tanımlayıcısı (ProgID) gibi ayarları kategorisi ilişkilendirmek için kullanılır.  
  
### <a name="settings-category-attribute"></a>Ayarları kategorisi özniteliği  
 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Kategorileri özel ayarları noktalarına eşleme belirler **içeri ve dışarı aktarma ayarları Sihirbazı** sağladığı VSPackage içeren bir kategori ilişkilendirerek. Aşağıdaki kod parçasını göz önünde bulundurun:  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 Kaynak Kimliği 106 "My kategoriye" 107 ayarlarına"My" ve "Çeşitli seçenekleri" 108 eşler. Bu bildiren `MyPackage` kategorisi Category_My ayarlarım sağlar. Kategori tarafından sağlanan `OptionsPageGeneral` uygulamalıdır sınıfı <xref:Microsoft.VisualStudio.Shell.IProfileManager>. Genel özellikleri bu kategorideki ayarları olan `OptionsPageGeneral` sınıfı.  
  
 İçinde **içeri ve dışarı aktarma ayarları Sihirbazı**, ayarları noktası ayarlarım bir ada sahip. Ayarları noktası seçildiğinde, açıklama **çeşitli seçenekleri**, görünür. Ayarları noktası adını ve açıklamasını yerelleştirilmiş dize arar: kaynaklardan alınır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seçenekler sayfası oluşturma](../extensibility/creating-an-options-page.md)   
 [VSSDK örnekleri](../misc/vssdk-samples.md)   
 [VSPackage'ı durumu](../misc/vspackage-state.md)   
 [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)