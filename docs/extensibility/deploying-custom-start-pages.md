---
title: Özel başlangıç sayfaları dağıtma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 81b4fb4938c1b87f4a9ca31cdc6035c4c6f124d1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926468"
---
# <a name="deploy-custom-start-pages"></a>Özel başlangıç sayfaları dağıtma

Özel başlangıç sayfaları VSIX dağıtımı kullanarak veya dosyaları hedef bilgisayarda doğru konumlara kopyalayarak dağıtabilirsiniz.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Başlangıç sayfası proje şablonunu kullanarak VSIX dağıtımı

Başlangıç sayfası proje şablonunu kullanarak bir başlangıç sayfası oluşturmak ve ardından projeyi oluşturun, Visual Studio oluşturur bir *.vsix* dağıtabileceğiniz dosya. Bir başlangıç sayfası paketleme bir *.vsix* dosyasını, hedef kitle bağlı olarak dağıtım için aşağıdaki seçenekleri sağlar:

-   Koyabilirsiniz *.vsix* dosyası bir ağ paylaşımına veya genel bir Web sitesi. Birisi bir dosyayı açtığında, başlangıç sayfası otomatik olarak yüklenir.

-   Karşıya yüklediğiniz *.vsix* dosyasını [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=123847) Web sitesi kullanıcılar kullanarak yükleyebilir **Uzantı Yöneticisi**.

Böylece değiştirebilir ve orijinal korumak başlangıç sayfası proje şablonu Visual Studio Başlangıç sayfası varsayılan bir kopyasını oluşturur.

Başlangıç sayfası proje şablonu kullanarak edinebilirsiniz **Uzantı Yöneticisi** veya Web sitesinden indirerek.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Başlangıç sayfası proje şablonunu kullanarak olmadan VSIX dağıtımı
 Başarılı bir VSIX dağıtımı bir uzantının VSIX kayıt işlemine ve tarafından tanınan klasörlerinde yüklenmesini gerektirir **Uzantı Yöneticisi**. Başlangıç sayfası proje şablonu doğru klasörleri belirttiğinden, VSIX dağıtımı için bir uzantı paketini istediğinizde bunu kullanmanızı öneririz. Ancak, şablon kullanamazsınız bir durum varsa, bunu kullanmadan bir VSIX dağıtımı oluşturabilirsiniz.

 Başlangıç sayfası proje şablonunu kullanarak olmadan bir VSIX dağıtımı oluşturmak için öncelikle oluşturma bir *.vsix* bu iki yöntemden biriyle başlangıç sayfası dosyası:

- Özel başlangıç sayfası dosyalarınızı boş bir VSIX projesine ekleniyor. Daha fazla bilgi için [VSIX proje şablonu](../extensibility/vsix-project-template.md).

- El ile oluşturarak bir *.vsix* dosya. Oluşturmak için bir *.vsix* el ile dosya:

  1.  Oluşturma *extension.vsixmanifest* dosya ve *[Content_Types] .xml* dosyasında yeni bir klasör. Daha fazla bilgi için [bir VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md).

  2.  İki XML dosyalarını içeren klasörü Windows Gezgini'nde sağ tıklayın, **göndermek için**ve ardından sıkıştırılmış klasöre tıklayın. Sonuç Yeniden Adlandır *.zip* dosyasını *Filename.vsix*burada Filename paketinizi yükleyen yeniden dağıtılabilir dosya adıdır.

  Bir başlangıç sayfası tanımak Visual Studio için `Content Element` VSIX bildirim içermelidir bir `CustomExtension Element` olan `Type` özniteliğini `"StartPage"`. VSIX dağıtımı kullanarak yüklü olan bir başlangıç sayfası uzantısı görünür **başlangıç sayfasını Özelleştir** listesini **başlangıç** seçenekleri sayfasında olarak **[yüklü uzantı]** *Uzantı adı*.

  Başlangıç sayfası paketinizi derlemeleri içerir, böylece Visual Studio başladığında kullanılabilir bağlama yolu kayıt eklemeniz gerekir. Bunu yapmak için paketinizi içerdiğinden emin olun bir *.pkgdef* aşağıdaki bilgileri içeren dosya.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Tüm kullanıcılar için VSIX dağıtımı
 Varsayılan olarak, VSIX paketinde dağıtılan uzantıları yalnızca geçerli kullanıcı için yükleyin. Tüm kullanıcıların dağıtım oluşturarak, hedef makinenin tüm kullanıcıları için bir başlangıç sayfası yükleme yapabilirsiniz.

### <a name="to-create-an-all-users-deployment"></a>Tüm kullanıcılar dağıtımı oluşturmak için

1.  Açık *extension.vsixmanifest* dosyasında kod görünümü.

2.  İçinde `Identifier` VSIX bildirimi öğesi < ekleme bir `AllUsers` değerine sahip öğe `true`.

    ```
    <AllUsers>true</AllUsers>
    ```

     Bu VSIX Yükleyicisi için yönetici izinleri ister ve ardından dosyaları yüklemek neden *\Common7\IDE\Extensions*.

3.  Açık *.pkgdef* dosya.

4.  Değiştirme *.pkgdef* aşağıdakileri ekleyerek HKLM altında varsayılan başlangıç sayfasını ayarlama burada *MyStartPage.xaml* adıdır *.xaml* başlatma içeren dosya Sayfa.

     [$RootKey$ \StartPage\Default]

     "URI"="$PackageFolder$\\*MyStartPage.xaml*"

     Bu yeni başlangıç sayfası konumu aramak için Visual Studio bildirir.

## <a name="file-copy-deployment"></a>Dosya kopyası dağıtımını
 Oluşturmak zorunda değilsiniz bir *.vsix* özel bir başlangıç sayfası dağıtmak için dosya. Bunun yerine, biçimlendirme ve destek dosyaları doğrudan kullanıcının kopyalayabilirsiniz <em>\StartPages\* klasör. **Başlangıç sayfasını Özelleştir</em>*  listesini **başlangıç** seçenekleri sayfasında listeleri her *.xaml* dosya yolu ile birlikte bu klasördeki — Örneğin, *%USERPROFILE%\My Documents\Visual Studio {version} \StartPages\\{dosya adı} .xaml*. Başlangıç sayfası özel derlemeler için başvurular içeriyorsa, bunları kopyalayın ve bunları yapıştırın gerekir * \PrivateAssemblies\* klasör.

 Bir başlangıç paketleme olmadan oluşturulan sayfası dağıtmak için bir *.vsix* dosyası öneririz temel dosya kopyalama strateji, örneğin, bir toplu betik kullanın veya dosyaları sayesinde herhangi bir dağıtım teknolojisi koyun gerekli dizinler.

### <a name="to-manually-install-a-custom-start-page"></a>El ile özel bir başlangıç sayfası yüklemek için

1.  Kopyalama *.xaml* derlemeler dışındaki destek dosyalarıyla birlikte Başlangıç sayfası biçimlendirmesini içeren ve kullanıcının yapıştırın dosya * \StartPages\* klasör.

2.  Başlangıç sayfası derlemeleri gerektiriyorsa, bunları kopyalayıp bunları *... \\{Visual Studio yükleme klasörü} \Common7\IDE\PrivateAssemblies\\*.

3.  İçinde **başlangıç sayfasını Özelleştir** listesini **başlangıç** seçenekleri sayfasında, yeni başlangıç sayfası seçin. Daha fazla bilgi için [başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md)
- [Başlangıç sayfasına kullanıcı denetimi Ekle](../extensibility/adding-user-control-to-the-start-page.md)