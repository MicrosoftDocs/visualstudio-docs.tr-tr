---
title: Özel Yönerge İşlemcisi Dağıtma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 16ee7eae30d947e6a83444c8e744cbaca398bf94
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894824"
---
# <a name="deploying-a-custom-directive-processor"></a>Özel Yönerge İşlemcisi Dağıtma

Özel yönerge işlemcisi, herhangi bir bilgisayarda Visual Studio'da kullanmak için bu konuda açıklanan yöntemlerin biriyle kaydetmeniz gerekir.

Diğer yöntemler şunlardır:

-   [Visual Studio uzantıları](../extensibility/shipping-visual-studio-extensions.md). Bu, yönerge işlemcisini hem kendi bilgisayar hem de diğer bilgisayarlara yüklemek/kaldırmak için bir yol sağlar. Genellikle, diğer özellikleri aynı VSIX'te paketleyebilirsiniz.

-   [VSPackage](../extensibility/internals/vspackages.md). Yönerge işlemcisinin yanı sıra diğer özellikleri de içeren bir VSPackage tanımlıyorsanız, yönerge işlemcisi kaydetmeye uygun bir yöntem yoktur.

-   Bir kayıt defteri anahtarı ayarlayın. Bu yöntemde, yönerge işlemcisi için bir kayıt defteri girdisini ekleyin.

Yalnızca, metin şablonunda Visual Studio veya MSBuild dönüştürmek istiyorsanız aşağıdaki yöntemlerden birini kullanmanız gerekir. Kendi uygulamanızda özel bir ana bilgisayar kullanıyorsanız, her yönerge için yönerge işlemcisi bulmak özel ana bilgisayarınızın sorumluluğundadır.

## <a name="deploying-a-directive-processor-in-a-vsix"></a>VSIX'te Yönerge İşlemcisini Dağıtma

Özel bir yönerge işlemcisi ekleyebilirsiniz bir [Visual Studio Uzantısı (VSIX)](../extensibility/starting-to-develop-visual-studio-extensions.md).

 Aşağıdaki iki öğenin .vsix dosyasında bulunduğundan emin olmanız gerekir:

-   Özel yönerge işlemcisi sınıfını içeren derleme (.dll).

-   Yönerge işlemcisini kaydeden .pkgdef dosyası. Dosyanın kök adı derleme ile aynı olmalıdır. Örneğin, dosyalarınız CDP.dll ve CDP.pkgdef olarak adlandırılabilir.

Bir .vsix dosyasının içeriğini denetlemek veya değiştirmek için, dosya adı uzantısını .zip olarak değiştirin ve açın. İçerikleri düzenledikten sonra, dosya adını .vsix olarak eski haline döndürün.

Bir .vsix dosyası oluşturmanın birkaç yolu vardır. Aşağıdaki yordam bir yöntemi açıklamaktadır.

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Bir VSIX projesinde özel bir yönerge işlemcisi geliştirmek için

1.  Visual Studio'da bir VSIX projesi oluşturun.

    -   İçinde **yeni proje** iletişim kutusunda **Visual Basic** veya **Visual C#**, ardından **genişletilebilirlik**. Tıklayın **VSIX projesi**.

2.  İçinde **source.extension.vsixmanifest**, içerik türü ve desteklenen sürümleri ayarlayın.

    1.  VSIX bildirim düzenleyicisinde **varlıklar** sekmesini, **yeni** ve yeni öğenin özelliklerini ayarlayın:

         **İçerik türü** = **VSPackage**

         **Kaynak proje** = \<*geçerli proje*>

    2.  Tıklayın **seçilen sürümler** ve yönerge işlemcisinin kullanılabilir olmasını istediğiniz yükleme türlerini işaretleyin.

3.  .pkgdef dosyası ekleyin ve özelliklerini VSIX'e dahil edecek şekilde ayarlayın.

    1.  Bir metin dosyası oluşturun ve adlandırın \< *assemblyName*> .pkgdef.

         \<*assemblyName*> genellikle projenin adı ile aynı olur.

    2.  Çözüm Gezgini'nde seçin ve özelliklerini aşağıdaki gibi ayarlayın:

         **Derleme eylemi** = **içerik**

         **Çıkış Dizinine Kopyala** = **her zaman Kopyala**

         **VSIX'e Ekle** = **True**

    3.  VSIX'in adını ayarlayın ve kimliğin benzersiz olmasını sağlayın.

4.  Aşağıdaki metni .pkgdef dosyasına ekleyin.

    ```
    [$RootKey$\TextTemplating]
    [$RootKey$\TextTemplating\DirectiveProcessors]
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]
    @="Custom Directive Processor description"
    "Class"="NamespaceName.ClassName"
    "CodeBase"="$PackageFolder$\AssemblyName.dll"
    ```

     Şu adları kendi adlarınızla değiştirin: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.

5.  Aşağıdaki başvuruları projeye ekleyin:

    -   **Microsoft.VisualStudio.TextTemplating.\*.0**

    -   **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0**

    -   **Microsoft.VisualStudio.TextTemplating.VSHost.\*.0**

6.  Projeye özel yönerge işlemcisi sınıfınızı ekleyin.

     Bu, uygulamanız gerekir, ortak bir sınıftır <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> veya <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

#### <a name="to-install-the-custom-directive-processor"></a>Özel Yönerge İşlemcisini yüklemek için

1.  Windows Gezgini'nde, yapı dizinini (genellikle bin\Debug veya bin\Release) açın.

2.  Yönerge işlemcisini başka bir bilgisayara yüklemek isterseniz .vsix dosyasını başka bir bilgisayara kopyalayın.

3.  .vsix dosyasına çift tıklatın. Visual Studio uzantısı yükleyicisi görüntülenir.

4.  Visual Studio'yu yeniden başlatın. Artık, özel yönerge işlemcisine başvuran yönergeleri içeren metin şablonlarını çalıştırmak mümkün olacaktır. Her yönerge bu şekildedir:

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Özel yönerge işlemcisini kaldırmak veya kalıcı olarak devre dışı bırakmak için

1.  Visual Studio **Araçları** menüsünde tıklatın **Uzantı Yöneticisi**.

2.  Yönerge işlemcisini içeren VSIX'i seçin ve ardından **kaldırma** veya **devre dışı**.

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>VSIX'te bir Yönerge İşlemcisine Sorun Giderme İşlemi Yapma
 Yönerge işlemcisi çalışmazsa şu öneriler yardımcı olabilir:

-   Özel yönergede belirttiğiniz işlemci adının eşleşmesi gerekir `CustomDirectiveProcessorName` .pkgdef dosyasında belirttiğiniz.

-   `IsDirectiveSupported` Yöntemi döndürmelidir `true` adını geçirildiğinde, `CustomDirective`.

-   Uzantı Yöneticisi'nde uzantıyı göremiyorsanız, ancak sistem yüklemenizi izin vermez, uzantısını silin **%localappdata%\Microsoft\VisualStudio\\\*. 0\Extensions\\** .

-   .Vsix dosyasını açın ve içeriğini inceleyin. Açmak için, dosya adı uzantısını .zip olarak değiştirin. .dll, .pkgdef ve extension.vsixmanifest dosyalarını içerdiğini doğrulayın. .vsixmanifest uzantı dosyası SupportedProducts düğümü için uygun listeyi içermelidir ve buna ek olarak İçerik düğümü altında bir VsPackage düğümü içermelidir:

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>VSPackage'ta Yönerge İşlemcisini Dağıtma
 Yönerge işlemciniz GAC'ye yüklenecek VSPackage'ın parçasıysa sistemin sizin için .pkgdef dosyası oluşturmasını sağlayın.

 Paket sınıfınıza şu öznitelikleri yerleştirin:

```csharp
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]
```

> [!NOTE]
>  Bu öznitelik, yönerge işlemcisi sınıfına değil, paket sınıfına yerleştirilir.

 .pkgdef dosyası projeyi oluşturduğunuzda oluşturulur. VSPackage'i yüklediğinizde, .pkgdef dosyası yönerge işlemcisini kaydeder.

 .pkgdef dosyasının, genellikle bin\Debug veya bin\Release olan yapı klasöründe göründüğünü doğrulayın. Görünmezse, .csproj dosyasını bir metin düzenleyicisinde açın ve şu düğümü kaldırın: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`.

 Daha fazla bilgi için [VSPackages](../extensibility/internals/vspackages.md).

## <a name="setting-a-registry-key"></a>Bir Kayıt Defteri Anahtarını Ayarlama
 Bu, özel bir yönerge işlemcisi yükleme yöntemi en az tercih edilir. Yönerge işlemcisini etkinleştirmek veya devre dışı bırakmak için uygun bir yol sağlamaz; yönerge işlemcisinin başka kullanıcılara dağıtılması yöntemini de sağlamaz.

> [!CAUTION]
>  Kayıt defterinin hatalı şekilde düzenlenmesi sisteminizde ciddi arızalara yol açabilir. Kayıt defterinde değişiklikler yapmadan önce, bilgisayarınızdaki tüm değerli verileri yedeklediğinizden emin olun.

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Bir kayıt defteri anahtarı ayarlayarak bir yönerge işlemcisi kaydetmek için

1. `regedit`'i çalıştırın.

2. Regedit içinde şuraya gidin:

    **Hkey_local_machıne\software\microsoft\visualstudio\\\*.0\TextTemplating\DirectiveProcessors**

    Visual Studio Deneysel sürümüne yönerge işlemcisi eklemek isterseniz "11.0" "sonuna Exp" ekleyin.

3. Yönerge işlemcisi sınıfıyla aynı ada sahip bir kayıt defteri anahtarı ekleyin.

   -   Kayıt defteri ağacında sağ **DirectiveProcessors** düğümüne **yeni**ve ardından **anahtar**.

4. Yeni düğümünde, Sınıf ve CodeBase veya Derleme için dize değerlerini aşağıdaki tablolara göre ekleyin.

   1.  Oluşturduğunuz düğüme sağ tıklayın, fareyle **yeni**ve ardından **dize değeri**.

   2.  Değerin adını düzenleyin.

   3.  Adı çift tıklatın ve verileri düzenleyin.

   Özel yönerge işlemcisi GAC'de değilse, kayıt defteri alt anahtarları aşağıdaki tabloda gibi görünmelidir:

|Ad|Tür|Veri|
|-|-|-|
|(Varsayılan)|REG_SZ|(değer ayarlı değil)|
|örneği|REG_SZ|**\<Namespace adı >. \<Sınıf adı >**|
|CodeBase|REG_SZ|**\<Path >\\< derleme adınız\>**|

 Derleme GAC'deyse, kayıt defteri alt anahtarları aşağıdaki tabloda gibi görünmelidir:

|Ad|Tür|Veri|
|-|-|-|
|(Varsayılan)|REG_SZ|(değer ayarlı değil)|
|örneği|REG_SZ|\<**Tam nitelikli sınıf adınız**>|
|Derleme|REG_SZ|\<**GAC'deki derleme adınız**>|

## <a name="see-also"></a>Ayrıca bkz.

- [Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md)