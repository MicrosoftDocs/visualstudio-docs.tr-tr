---
title: Seçenekler sayfaları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 236d9a0be82885bdf8040c97601429279e74dd15
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949649"
---
# <a name="create-options-pages"></a>Seçenekler sayfaları oluşturma
İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yönetilen paket çerçevesini türetilen sınıflar <xref:Microsoft.VisualStudio.Shell.DialogPage> genişletmek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ekleyerek IDE **seçenekleri** altında sayfaları **Araçları** menüsü.  
  
 Bir nesneyi uygulama bir verilen **araçları seçeneği** sayfasıdır belirli VSPackages ilişkilendirilmiş <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> nesne.  
  
 Belirli bir uygulama nesnesi ortamı oluşturur çünkü **Araçlar Seçenekler** sayfa sayfa IDE tarafından görüntülendiğinde:  
  
-   A **araçları seçeneği** VSPackage uygulama nesnesi değil ve kendi nesne üzerinde sayfa'nin uygulanmasını.  
  
-   Bir nesne birden çok uygulayamaz **Araçlar Seçenekler** sayfaları.  
  
## <a name="register-as-a-tools-options-page-provider"></a>Araç Seçenekleri sayfası sağlayıcısı kaydetme  
 Bir VSPackage'ı destekleyen kullanıcı yapılandırması üzerinden **Araçlar Seçenekler** sayfaları bu sağlayan nesneleri gösterir **Araçlar Seçenekler** örneklerini uygulayarak sayfaları <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> içinuygulanan<xref:Microsoft.VisualStudio.Shell.Package>uygulaması.  
  
 Bir örneği olmalıdır <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> için her <xref:Microsoft.VisualStudio.Shell.DialogPage>-uygulayan bir tür türetilmiş bir **Araçlar Seçenekler** sayfası.  
  
 Her bir örneği <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> uygulayan bir tür kullanan **Araçlar Seçenekler** sayfası, kategori ve tanımlamak için kullanılan alt kategorisi içeren dizeleri bir **Araçlar Seçenekler** sayfası ve kaynak bilgi türü sağlayarak olarak kaydetmek için bir **Araçlar Seçenekler** sayfası.  
  
## <a name="persist-tools-options-page-state"></a>Araçlar Seçenekler Sayfa durumu Sürdür  
 Varsa bir **Araçlar Seçenekler** sayfa uygulaması Otomasyon desteği etkinleştirilmiş kayıtlı ise, IDE'nin yanı sıra diğer tüm sayfa durum devam ederse **Araçlar Seçenekler** sayfaları.  
  
 Bir VSPackage'ı kullanarak kendi Kalıcılık yönetebilirsiniz <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Tek veya diğer Kalıcılık yöntemi kullanılmalıdır.  
  
## <a name="implement-dialogpage-class"></a>DialogPage sınıf uygulama  
 VSPackage'nın uygulamasını sağlayan bir nesne bir <xref:Microsoft.VisualStudio.Shell.DialogPage>-türetilmiş bir tür, aşağıdaki devralınan özellikler avantajlarından faydalanabilirsiniz:  
  
- Varsayılan kullanıcı arabirimi pencere.  
  
- Bir ya da Eğer Kalıcılık mekanizması kullanılabilir varsayılan <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> sınıfına uygulanan veya <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> özelliği `true` için <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> sınıfa uygulanır.  
  
- Otomasyon desteği.  
  
  Bir nesne uygulamak için en düşük gereksinimi bir **Araçlar Seçenekler** kullanarak sayfa <xref:Microsoft.VisualStudio.Shell.DialogPage> genel özelliklerin ektir.  
  
  Sınıf düzgün olarak kayıtlı bir **Araçlar Seçenekler** genel özelliklerini kullanılabilir sonra sayfa sağlayıcısı **seçenekleri** bölümünü **Araçları** menü biçiminde bir Özellik Kılavuzu.  
  
  Bu varsayılan özellikler geçersiz kılınabilir. Örneğin, daha karmaşık bir kullanıcı oluşturmak için arabirimi yalnızca varsayılan uygulamasını geçersiz kılma gerektirir <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıda bir seçenekler sayfası, basit "Hello world" uygulamasıdır. Visual Studio Paket şablonla tarafından oluşturulan varsayılan projeye aşağıdaki kodu ekleyerek **menü komutu** seçeneği belirlenmiş yeterince seçeneği sayfa işlevselliği gösterir.  
  
### <a name="description"></a>Açıklama  
 "Hello world" en az bir seçenekler sayfası aşağıdaki sınıfı tanımlar. Açıldığında, kullanıcının ortak ayarlayıp `HelloWorld` özellik kılavuzunda özelliği.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Açıklama  
 Paket yüklediğinde, paket sınıfına aşağıdaki öznitelik uygulama sayfasında seçenekleri kullanılabilir hale getirir. Kategori ve sayfa için rastgele kaynak kimliklerini sayılardır ve Boole değeri en sonda sayfasında Otomasyon destekleyip desteklemediğini belirtir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki olay işleyicisini sonucu Seçenekler sayfasında özellik değerine bağlı olarak görüntüler. Kullandığı <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> sonucuyla yöntemi açıkça cast sayfa tarafından kullanıma sunulan özelliklere erişmek için özel seçeneğini sayfa türü.  
  
 Paket şablon tarafından oluşturulan bir proje söz konusu olduğunda bu işlevden çağırma `MenuItemCallback` varsayılan komutu eklemek için işlevi eklenen **Araçları** menüsü.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kullanıcı ayarlarını ve seçeneklerini genişletme](../../extensibility/extending-user-settings-and-options.md)   
 [Seçenekler sayfaları için Otomasyon desteği](../../extensibility/internals/automation-support-for-options-pages.md)