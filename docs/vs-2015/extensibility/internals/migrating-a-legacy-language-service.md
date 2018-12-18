---
title: Eski dil hizmetini geçirme | Microsoft Docs
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
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 826a27fd3e3041e99f34acce0474a8e71837c69d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807614"
---
# <a name="migrating-a-legacy-language-service"></a>Eski Dil Hizmetini Geçirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eski dil hizmeti projesini güncelleştirmek ve source.extension.vsixmanifest dosyası projeye eklenirken Visual Studio'nun sonraki bir sürüme geçiş yapabilirsiniz. Visual Studio Düzenleyicisi, uyum için dil hizmeti önceki gibi çalışmaya devam eder.  
  
 Eski dil Hizmetleri bir VSPackage'ı bir parçası olarak uygulanır, ancak dil hizmeti özellikleri uygulamak için daha yeni MEF uzantıları kullanmaktır. Dil hizmeti uygulamak için en yeni yolu hakkında daha fazla bilgi için bkz: [düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Yeni bir düzenleyici API hemen kullanmaya başlamak öneririz. Bu dil hizmetinizin performansını ve yeni düzenleyici özellikleri yararlanmanıza olanak tanır.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Bir Visual Studio 2008 dil hizmeti çözümü sonraki bir sürüme geçirme  
 Aşağıdaki adımlarda, uyum RegExLanguageService adlı bir Visual Studio 2008 örneği gösterilmektedir. Bu örnek, bir Visual Studio 2008 SDK'sını yükleme bulabilirsiniz *Visual Studio SDK yükleme yolunu*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ klasör.  
  
> [!IMPORTANT]
>  Dil hizmetinizi renkleri tanımlamıyorsa, açıkça ayarlamalısınız <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> için `true` VSPackage'ı üzerinde:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Bir Visual Studio 2008 dil hizmeti sonraki bir sürüme geçirmek için  
  
1.  Visual Studio ve Visual Studio SDK'ın daha yeni sürümlerini yükleyin. SDK'sını yükleme yöntemleri hakkında daha fazla bilgi için bkz. [Visual Studio SDK'sını yükleme](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  (Bunu Visual Studio'da yüklenmeden. RegExLangServ.csproj dosyayı Düzenle  
  
     İçinde `Import` Microsoft.VsSDK.targets dosyaya düğüm değeri aşağıdaki metinle değiştirin.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Dosyayı kaydedin ve kapatın.  
  
4.  RegExLangServ.sln çözümü açın.  
  
5.  **Tek yönlü yükseltme** penceresi görüntülenir. **Tamam**'ı tıklatın.  
  
6.  Proje özelliklerini güncelleştirin. Açık **proje özellikleri** 'nde proje düğümüne seçerek penceresi **Çözüm Gezgini**, sağ ve seçme **özellikleri**.  
  
    -   Üzerinde **uygulama** sekmesinde, **hedef Framework'ü** için **4.6.1**.  
  
    -   Üzerinde **hata ayıklama** sekmesinde **harici program Başlat** kutusuna  **\<Visual Studio yükleme yolu > \Common7\IDE\devenv.exe.**.  
  
         İçinde **komut satırı bağımsız değişkenleri** kutusuna /**rootsuffix Exp**.  
  
7.  Aşağıdaki başvuruları güncelleştirin:  
  
    -   Microsoft.VisualStudio.Shell.9.0.dll başvurusunu kaldırın, sonra Microsoft.VisualStudio.Shell.14.0.dll ve Microsoft.VisualStudio.Shell.Immutable.11.0.dll başvurular ekleyin.  
  
    -   Microsoft.VisualStudio.Package.LanguageService.9.0.dll başvurusunu kaldırın, sonra Microsoft.VisualStudio.Package.LanguageService.14.0.dll bir başvuru ekleyin.  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0.dll bir başvuru ekleyin.  
  
8.  VsPkg.cs dosyasını açın ve değeri değiştirin `DefaultRegistryRoot` özniteliğini  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. Aşağıdaki özniteliği için VsPkg.cs eklemelisiniz özgün örnek kendi dil hizmeti kaydetmez.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Source.extension.vsixmanifest dosyası eklemeniz gerekir.  
  
    -   Bu dosya, var olan bir uzantı, proje dizinine kopyalayın. (Bu dosya yapmanın bir yolu olan bir VSIX projesi oluşturmak için (altında **dosya**, tıklayın **yeni**, ardından **proje**. Altında Visual Basic veya C# tıklatın **genişletilebilirlik**, ardından **VSIX projesi**.)  
  
    -   Dosyayı projenize ekleyin.  
  
    -   Dosyanın içinde **özellikleri**ayarlayın **derleme eylemi** için **hiçbiri**.  
  
    -   Dosyasını açın **VSIX bildirim Düzenleyicisi**.  
  
    -   Aşağıdaki alanları değiştirin:  
  
    -   **Kimliği**: RegExLangServ  
  
    -   **Ürün adı**: RegExLangServ  
  
    -   **Açıklama**: bir normal ifade dil hizmeti.  
  
    -   Altında **varlıklar**, tıklayın **yeni**seçin **türü** için **Microsoft.VisualStudio.VsPackage**ayarlayın **kaynak** için **mevcut çözümde bir proje**ve ardından **proje** için **RegExLangServ**.  
  
    -   Dosyayı kaydedin ve kapatın.  
  
11. Çözümü oluşturun. Yerleşik dosyaları dağıtılan **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.  
  
12. Hata ayıklama başlatılamıyor. Visual Studio ikinci bir örneğini açıldı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski Dil Hizmeti Genişletilebilirliği](../../extensibility/internals/legacy-language-service-extensibility.md)

