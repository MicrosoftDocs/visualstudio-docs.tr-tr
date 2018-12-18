---
title: Eski dil hizmetini geçirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 412b09016a3f889e0d6c5e40ff75895d5ae8ff48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135863"
---
# <a name="migrating-a-legacy-language-service"></a>Eski dil hizmetini geçirme
Visual Studio sonraki bir sürüme eski dil hizmeti projesini güncelleştirmek ve source.extension.vsixmanifest dosyası projeye ekleyerek geçirebilirsiniz. Visual Studio düzenleyicisinde, uyum için dil hizmeti önceki gibi çalışmaya devam eder.  
  
 Eski dil hizmetler bir VSPackage bir parçası olarak uygulanır, ancak dil hizmet özellikleri uygulamak için daha yeni MEF uzantıları kullanmak için bir yoludur. Bir dil hizmeti uygulamak için yeni yolu hakkında daha fazla bilgi için bkz: [Düzenleyicisi ve dil hizmeti uzantılarını](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Yeni Düzenleyicisi API mümkün olan en kısa sürede kullanmaya başlamanızı öneriyoruz. Bu dil hizmetinizin performansını ve yeni Düzenleyicisi özelliklerden yararlanmak sağlar.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Bir Visual Studio 2008 dil hizmeti çözümü daha sonraki bir sürüme geçiş  
 Aşağıdaki adımlar RegExLanguageService adlı bir Visual Studio 2008 örnek uyarlamak nasıl gösterir. Bu örnek, bir Visual Studio 2008 SDK'sı yükleme bulabilirsiniz *Visual Studio SDK yükleme yolu*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ klasör.  
  
> [!IMPORTANT]
>  Dil hizmetinizi renkleri tanımlamıyorsa, açıkça ayarlamalısınız <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> için `true` VSPackage üzerinde:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Visual Studio 2008 dil hizmeti daha sonraki bir sürüme geçirmek için  
  
1.  Visual Studio ve Visual Studio SDK'sı daha yeni sürümlerini yükleyin. SDK yükleme yolları hakkında daha fazla bilgi için bkz: [Visual Studio SDK'sını yükleme](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  (Bunu Visual Studio'da yüklemeden. RegExLangServ.csproj dosyayı düzenleyin.  
  
     İçinde `Import` Microsoft.VsSDK.targets dosyaya düğüm değeri aşağıdaki metinle değiştirin.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Dosyayı kaydedin ve kapatın.  
  
4.  RegExLangServ.sln çözümü açın.  
  
5.  **Tek yönlü yükseltme** penceresi görüntülenir. **Tamam**'ı tıklatın.  
  
6.  Proje özelliklerini güncelleştirin. Açık **proje özelliklerini** proje düğümünde seçerek penceresi **Çözüm Gezgini**, sağ ve seçme **özellikleri**.  
  
    -   Üzerinde **uygulama** sekmesinde, değiştirmek **hedef framework** için **4.6.1**.  
  
    -   Üzerinde **hata ayıklama** sekmesinde **başlangıç dış program** kutusuna  **\<Visual Studio yükleme yolu > \Common7\IDE\devenv.exe.**.  
  
         İçinde **komut satırı bağımsız değişkenleri** kutusuna /**rootsuffix Exp**.  
  
7.  Aşağıdaki başvuruları güncelleştirin:  
  
    -   Microsoft.VisualStudio.Shell.9.0.dll başvurusunu kaldırın, ardından Microsoft.VisualStudio.Shell.14.0.dll ve Microsoft.VisualStudio.Shell.Immutable.11.0.dll başvurular ekleyin.  
  
    -   Microsoft.VisualStudio.Package.LanguageService.9.0.dll başvurusunu kaldırın, ardından Microsoft.VisualStudio.Package.LanguageService.14.0.dll bir başvuru ekleyin.  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0.dll bir başvuru ekleyin.  
  
8.  VsPkg.cs dosyasını açın ve değerini değiştirmek `DefaultRegistryRoot` özniteliğini  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. Aşağıdaki öznitelik için VsPkg.cs eklemelisiniz özgün örnek onun dil hizmeti kaydetmez.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Source.extension.vsixmanifest dosyayı eklemeniz gerekir.  
  
    -   Bu dosya mevcut bir uzantı, proje dizinine kopyalayın. (Bu dosya almanın bir yolu olan bir VSIX proje oluşturmak için (altında **dosya**, tıklatın **yeni**, ardından **proje**. Altında Visual Basic veya C# tıklatın **genişletilebilirlik**seçeneğini belirleyip **VSIX proje**.)  
  
    -   Dosyayı projenize ekleyin.  
  
    -   Dosyanın içinde **özellikleri**ayarlayın **yapı eylemi** için **hiçbiri**.  
  
    -   Dosyasını açın **VSIX bildirim Düzenleyicisi**.  
  
    -   Aşağıdaki alanları değiştirin:  
  
    -   **Kimliği**: RegExLangServ  
  
    -   **Ürün adı**: RegExLangServ  
  
    -   **Açıklama**: bir normal ifade dili hizmeti.  
  
    -   Altında **varlıklar**, tıklatın **yeni**seçin **türü** için **Microsoft.VisualStudio.VsPackage**ayarlayın **kaynak** için **geçerli çözümdeki bir proje ile**ve ardından **proje** için **RegExLangServ**.  
  
    -   Dosyayı kaydedin ve kapatın.  
  
11. Çözümü oluşturun. Yerleşik dosyaları dağıtılan **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.  
  
12. Hata ayıklama başlatılamıyor. Visual Studio ikinci bir örneğini açıldı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski Dil Hizmeti Genişletilebilirliği](../../extensibility/internals/legacy-language-service-extensibility.md)