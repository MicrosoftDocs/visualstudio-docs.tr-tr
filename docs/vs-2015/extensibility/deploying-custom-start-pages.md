---
title: Özel başlangıç sayfaları dağıtma | Microsoft Docs
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
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e788f9bb1ca0333fd20237103cf6bce136af2e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795121"
---
# <a name="deploying-custom-start-pages"></a>Özel Başlangıç Sayfaları Dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel başlangıç sayfaları VSIX dağıtımı kullanarak veya dosyaları hedef bilgisayarda doğru konumlara kopyalayarak dağıtabilirsiniz.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Başlangıç sayfası proje şablonunu kullanarak VSIX dağıtımı  
 Başlangıç sayfası proje şablonunu kullanarak bir başlangıç sayfası oluşturduğunuzda ve ardından projeyi Visual Studio dağıtabileceğiniz bir .vsix dosyasını oluşturur. Bir .vsix dosyasında bir başlangıç sayfası paketleme, dağıtım için hedef kitle bağlı olarak, aşağıdaki seçenekleri sunar:  
  
- .Vsix dosyasını bir ağ paylaşımına veya genel bir Web sitesi koyabilirsiniz. Birisi bir dosyayı açtığında, başlangıç sayfası otomatik olarak yüklenir.  
  
- .Vsix dosyasına yükleyebilirsiniz [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=123847) Web sitesi kullanıcılar kullanarak yükleyebilir **Uzantı Yöneticisi**.  
  
  Böylece değiştirebilir ve orijinal korumak başlangıç sayfası proje şablonu Visual Studio Başlangıç sayfası varsayılan bir kopyasını oluşturur.  
  
  Başlangıç sayfası proje şablonu kullanarak edinebilirsiniz **Uzantı Yöneticisi** veya Web sitesinden indirerek.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Başlangıç sayfası proje şablonunu kullanarak olmadan VSIX dağıtımı  
 Başarılı bir VSIX dağıtımı bir uzantının VSIX kayıt işlemine ve tarafından tanınan klasörlerinde yüklenmesini gerektirir **Uzantı Yöneticisi**. Başlangıç sayfası proje şablonu doğru klasörleri belirttiğinden, VSIX dağıtımı için bir uzantı paketini istediğinizde bunu kullanmanızı öneririz. Ancak, şablon kullanamazsınız bir durum varsa, bunu kullanmadan bir VSIX dağıtımı oluşturabilirsiniz.  
  
 Başlangıç sayfası proje şablonunu kullanarak olmadan bir VSIX dağıtımı oluşturmak için öncelikle bu iki yöntemden biriyle başlangıç sayfası için bir .vsix dosyası oluşturun:  
  
- Özel başlangıç sayfası dosyalarınızı boş bir VSIX projesine ekleniyor. Daha fazla bilgi için [VSIX proje şablonu](../extensibility/vsix-project-template.md).  
  
- Bir .vsix dosyasını el ile oluşturarak. Daha fazla bilgi için [nasıl yapılır: el ile bir uzantı (VSIX dağıtımı) paketi](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
  Bir başlangıç sayfası tanımak Visual Studio için `Content Element` VSIX bildirim içermelidir bir `CustomExtension Element` olan `Type` özniteliğini `"StartPage"`. VSIX dağıtımı kullanarak yüklü olan bir başlangıç sayfası uzantısı görünür **başlangıç sayfasını Özelleştir** listesini **başlangıç** seçenekleri sayfasında olarak **[yüklü uzantı]** *Uzantı adı*.  
  
  Başlangıç sayfası paketinizi derlemeleri içerir, böylece Visual Studio başladığında kullanılabilir bağlama yolu kayıt eklemeniz gerekir. Bunu yapmak için paketinizi aşağıdaki bilgileri içeren bir .pkgdef dosyası içerdiğinden emin olun.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>Tüm kullanıcılar için VSIX dağıtımı  
 Varsayılan olarak, VSIX paketinde dağıtılan uzantıları yalnızca geçerli kullanıcı için yükleyin. Tüm kullanıcıların dağıtım oluşturarak, hedef makinenin tüm kullanıcıları için bir başlangıç sayfası yükleme yapabilirsiniz.  
  
##### <a name="to-create-an-all-users-deployment"></a>Tüm kullanıcılar dağıtımı oluşturmak için  
  
1.  .Vsixmanifest uzantı dosyası kod Görünümü'nde açın.  
  
2.  İçinde `Identifier` VSIX bildirimi öğesi < ekleme bir `AllUsers` değerine sahip öğe `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Bu VSIX Yükleyicisi için yönetici izinleri iste ve dosyalar için \Common7\IDE\Extensions yüklemeyi neden olur.  
  
3.  .Pkgdef dosyası açın.  
  
4.  Varsayılan başlangıç sayfasını HKLM altında aşağıdakileri ekleyerek ayarlamak için .pkgdef değiştirme burada *MyStartPage.xaml* başlangıç sayfası içeren .xaml dosyasının adıdır.  
  
     [$RootKey$ \StartPage\Default]  
  
     "URI"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     Bu yeni başlangıç sayfası konumu aramak için görsel komutla bildirir.  
  
## <a name="file-copy-deployment"></a>Dosya kopyası dağıtımını  
 Özel başlangıç sayfası dağıtmak için bir .vsix dosyası oluşturmak sahip değil. Bunun yerine, biçimlendirme ve destekleyici dosyaları doğrudan kullanıcının \StartPages\ klasöre kopyalayabilirsiniz. **Başlangıç sayfasını Özelleştir** listesini **başlangıç** Seçenekleri sayfası listeler her, klasörün yolu ile birlikte .xaml dosyasında — Örneğin, %USERPROFILE%\My Documents\Visual Studio  *Sürüm*\StartPages\\*dosya adı*.xaml. Başlangıç sayfası özel derlemeler için başvurular içeriyorsa, bunları kopyalayın ve bunları \PrivateAssemblies\ klasöre yapıştırın.  
  
 Bir başlangıç paketleme olmadan oluşturulan sayfası dağıtmak için bir .vsix dosyası içinde öneririz temel dosya kopyalama stratejisi kullanın, örneğin, bir toplu betik veya sayesinde herhangi bir dağıtım teknolojisi gerekli dizinlerde dosyaları yerleştirin.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>El ile özel bir başlangıç sayfası yüklemek için  
  
1.  Derlemeleri dışında destek dosyalarıyla birlikte Başlangıç sayfası biçimlendirme içeren .xaml dosyasını kopyalayın ve bunları kullanıcının \StartPages\ klasörüne yapıştırın.  
  
2.  Başlangıç sayfası derlemeleri gerektiriyorsa, bunları kopyalayıp bunları... \\ *Visual Studio yükleme klasörü*\Common7\IDE\PrivateAssemblies\\.  
  
3.  İçinde **başlangıç sayfasını Özelleştir** listesini **başlangıç** seçenekleri sayfasında, yeni başlangıç sayfası seçin. Daha fazla bilgi için [başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Başlangıç Sayfasına Kullanıcı Denetimi Ekleme](../extensibility/adding-user-control-to-the-start-page.md)

