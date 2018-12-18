---
title: Seçenekler sayfaları oluşturma | Microsoft Docs
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
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 076c4934fe4f81bd56edc70356ecdcc1101456e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760325"
---
# <a name="creating-options-pages"></a>Seçenekler Sayfaları Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İçinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yönetilen paket çerçevesini türetilen sınıflar <xref:Microsoft.VisualStudio.Shell.DialogPage> genişletmek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ekleyerek IDE **seçenekleri** altında sayfaları **Araçları** menüsü.  
  
 Bir nesneyi uygulama bir verilen **araçları seçeneği** sayfasıdır belirli VSPackages ilişkilendirilmiş <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> nesne.  
  
 Belirli bir uygulama nesnesi ortamı oluşturur çünkü **Araçlar Seçenekler** sayfa sayfa IDE tarafından görüntülendiğinde:  
  
-   A **araçları seçeneği** VSPackage uygulama nesnesi değil ve kendi nesne üzerinde sayfa'nin uygulanmasını.  
  
-   Bir nesne birden çok uygulayamaz **Araçlar Seçenekler** sayfaları.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Bir araç seçenekleri sayfası sağlayıcısı olarak kaydetme  
 Bir VSPackage'ı destekleyen kullanıcı yapılandırması üzerinden **Araçlar Seçenekler** sayfaları bu sağlayan nesneleri gösterir **Araçlar Seçenekler** örneklerini uygulayarak sayfaları <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> içinuygulanan<xref:Microsoft.VisualStudio.Shell.Package>uygulaması.  
  
 Bir örneği olmalıdır <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> için her <xref:Microsoft.VisualStudio.Shell.DialogPage>-uygulayan bir tür türetilmiş bir **Araçlar Seçenekler** sayfası.  
  
 Her bir örneği <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> uygulayan bir tür kullanan **Araçlar Seçenekler** sayfası, kategori ve tanımlamak için kullanılan alt kategorisi içeren dizeleri bir **Araçlar Seçenekler** sayfası ve kaynak bilgi türü sağlayarak olarak kaydetmek için bir **Araçlar Seçenekler** sayfası.  
  
## <a name="persisting-tools-options-page-state"></a>Kalıcı Araçlar seçenekleri sayfa durumu  
 Varsa bir **Araçlar Seçenekler** sayfa uygulaması Otomasyon desteği etkinleştirilmiş kayıtlı ise, IDE'nin yanı sıra diğer tüm sayfa durum devam ederse **Araçlar Seçenekler** sayfaları.  
  
 Bir VSPackage'ı kullanarak kendi Kalıcılık yönetebilirsiniz <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Tek veya diğer Kalıcılık yöntemi kullanılmalıdır.  
  
## <a name="implementing-dialogpage-class"></a>DialogPage sınıf uygulama  
 VSPackage'nın uygulamasını sağlayan bir nesne bir <xref:Microsoft.VisualStudio.Shell.DialogPage>-türetilmiş bir tür, aşağıdaki devralınan özellikler avantajlarından faydalanabilirsiniz:  
  
- Varsayılan kullanıcı arabirimi pencere.  
  
- Bir ya da Eğer Kalıcılık mekanizması kullanılabilir varsayılan <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> sınıfına uygulanan veya <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> özelliği `true` için <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> sınıfa uygulanır.  
  
- Otomasyon desteği.  
  
  Bir nesne uygulamak için en düşük gereksinimi bir **Araçlar Seçenekler** kullanarak sayfa <xref:Microsoft.VisualStudio.Shell.DialogPage> genel özelliklerin ektir.  
  
  Sınıf düzgün olarak kayıtlı bir **Araçlar Seçenekler** genel özelliklerini kullanılabilir sonra sayfa sağlayıcısı **seçenekleri** bölümünü **Araçları** menü biçiminde bir Özellik Kılavuzu.  
  
  Bu varsayılan özellikler geçersiz kılınabilir. Örneğin, daha karmaşık bir kullanıcı oluşturmak için arabirimi yalnızca varsayılan uygulamasını geçersiz kılma gerektirir <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıda bir basit "Merhaba Dünya" bir seçenekler sayfası uygulamasıdır. Visual Studio Paket şablonla tarafından oluşturulan varsayılan projeye aşağıdaki kodu ekleyerek **menü komutu** seçeneği belirlenmiş yeterince seçeneği sayfa işlevselliği gösterir.  
  
### <a name="description"></a>Açıklama  
 En az bir "Merhaba Dünya" Seçenekler sayfası aşağıdaki sınıfı tanımlar. Açıldığında, kullanıcının ortak ayarlayıp `HelloWorld` özellik kılavuzunda özelliği.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>Açıklama  
 Paket yüklediğinde, paket sınıfına aşağıdaki öznitelik uygulama sayfasında seçenekleri kullanılabilir hale getirir. Kategori ve sayfa için rastgele kaynak kimliklerini sayılardır ve Boole değeri en sonda sayfasında Otomasyon destekleyip desteklemediğini belirtir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki olay işleyicisini sonucu Seçenekler sayfasında özellik değerine bağlı olarak görüntüler. Kullandığı <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> sonucuyla yöntemi açıkça cast sayfa tarafından kullanıma sunulan özelliklere erişmek için özel seçeneğini sayfa türü.  
  
 Paket şablon tarafından oluşturulan bir proje söz konusu olduğunda bu işlevden çağırma `MenuItemCallback` varsayılan komutu eklemek için işlevi eklenen **Araçları** menüsü.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genişletme kullanıcı ayarları ve seçenekleri](../../extensibility/extending-user-settings-and-options.md)   
 [Seçenekler Sayfaları için Otomasyon Desteği](../../extensibility/internals/automation-support-for-options-pages.md)

