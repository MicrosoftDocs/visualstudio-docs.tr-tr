---
title: Yalıtılmış kabuğun öğeleri | Microsoft Docs
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
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e567fc212b9981d925fc11e8e0ae48132b3b05bf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816820"
---
# <a name="elements-of-the-isolated-shell"></a>Yalıtılmış kabuğun öğeleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kayıt defteri ayarları, çalışma zamanı ayarlarını ve uygulama giriş noktası, yalıtılmış Kabuk uygulaması ve kendi .vsct, .pkgdef, and.pkgundef dosyaları değiştirebilirsiniz.  
  
## <a name="registry-settings"></a>Kayıt defteri ayarları  
 .pkgdef ve .pkgundef dosyaları hem yalıtılmış Kabuk uygulaması için kayıt defteri ayarlarını değiştirin. Uygulamayı çalıştırdığınızda, aşağıdaki sırayla kayıt defteri ayarları tanımlanır:  
  
 Uygulamayı çalıştırdığınızda, aşağıdaki sırayla kayıt defteri ayarları tanımlanır:  
  
1.  Uygulama için kayıt defteri anahtarı oluşturulur.  
  
2.  Kayıt defteri, belirtilen anahtarları ve girişleri tanımlayarak uygulamanın .pkgdef dosyasından güncelleştirilir.  
  
3.  Uygulamanızın bir parçası olan her paket için bu paket .pkgdef dosyasından kayıt defteri güncelleştirilir. Her paket uygulamanın .pkgdef dosyasında $RootKey$ \Packages tarafından tanımlanan\\{*vsPackageGuid*} paketi için anahtar.  
  
4.  Kayıt defteri AppEnvConfig.pkgdef ve BaseConfig.pkgdef içinde güncelleştirilir *Visual Studio SDK yükleme yolunu*\Common7\IDE\ShellExtensions\Platform dizin. Bu, Visual Studio'nun bir parçası ve ayrıca Visual Studio Kabuğu (yalıtılmış mod) yeniden dağıtılabilir paketi parçası dosyalarıdır.  
  
5.  Kayıt defteri, belirtilen anahtarları ve girişleri kaldırarak uygulama .pkgundef dosyasından güncelleştirilir.  
  
## <a name="run-time-settings"></a>Çalışma zamanı ayarları  
 Bir kullanıcının yalıtılmış Kabuk uygulaması başladığında Visual Studio Kabuğu başlangıç giriş noktası çağırır. Uygulama ayarları, uygulamanız başlatıldığında, şu şekilde tanımlanır:  
  
1. Visual Studio Kabuğu uygulama kayıt defteri belirli anahtarlar için denetler. Bir anahtarı ayarı, başlangıç giriş noktası çağrısında belirtilirse, bu değeri kayıt defteri değerini geçersiz kılar.  
  
2. Kayıt defteri ya da giriş noktası parametresi bir ayarın değerini belirtir ve ayarı için varsayılan değer kullanılır.  
  
   Bir kullanıcı, komut satırından, uygulama başlatıldığında, tüm komut satırı anahtarları bunları Devenv yaptığı aynı şekilde davranır Visual Studio Kabuğu geçirilir. Devenv anahtarları hakkında daha fazla bilgi için bkz. [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md) ve [VSPackage geliştirme için Devenv komut satırı anahtarları](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Bir paket için komut satırı anahtarları nasıl kayıtları hakkında daha fazla bilgi için bkz. [komut satırı anahtarları ekleme](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Başlangıç giriş noktası  
 Appenvstub.dll dosyası, yalıtılmış Kabuk erişimi için giriş noktaları içerir. Uygulama başladığında, başlangıç giriş noktası Appenvstub.dll çağırır.  
  
 Uygulama davranışını başlangıç Giriş noktasına geçirilir son parametresinin değerini değiştirerek değiştirebilirsiniz. Daha fazla bilgi için [yalıtılmış Kabuk giriş noktası parametreleri (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>. Vsct dosyası  
 .Vsct dosyası standart hangi Visual Studio kullanıcı Arabirimi öğeleri uygulamada kullanılabilir belirtmenize olanak sağlar. Daha fazla bilgi için [. Vsct dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>. Pkgundef dosyası  
 Uygulama, Visual Studio zaten yüklü olduğu bir bilgisayara yüklendiğinde, Visual Studio kayıt defteri girdilerini bir kopyasını uygulama için yapılır. Varsayılan olarak, uygulama bilgisayarda yüklü olan VSPackages kullanır. .Pkgundef dosyası uygulamadan Visual Studio Kabuğu veya uzantıları belirli öğeleri kaldırmak için kayıt defteri girdilerini dışlamanıza olanak sağlar. Daha fazla bilgi için [. Pkgundef dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 .Pkgundef dosyası uygulamadan Visual Studio Kabuğu veya uzantıları belirli öğeleri kaldırmak için kayıt defteri girdilerini dışlamanıza olanak sağlar. Daha fazla bilgi için [. Pkgundef dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Paket hariç tutabilirsiniz GUID'leri kümesini listelenir [paket GUID'leri, Visual Studio özellikleri](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>. Pkgdef dosyası  
 .Pkgdef dosyası, uygulama için uygulama yüklendiğinde, ayarladığınız kayıt defteri girişleri tanımlamanıza olanak sağlar. .Pkgdef dosyası açıklamasını ve Visual Studio Kabuğu kullanan kayıt defteri girdilerini listesi için bkz [. Pkgdef dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Değiştirme dizeleri  
 .Pkgdef ve .pkgundef dosyalarında kullanılan değiştirme dizeleri listelenen [değiştirme dizeleri kullanılır. Pkgdef ve. Pkgundef dosyaları](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Diğer ayarlar  
 Yalıtılmış Kabuk uygulaması üzerinde Microsoft.VisualStudio.GraphModel.dll bağlıysa, yalıtılmış Kabuk uygulamanızın .config dosyasına aşağıdaki bağlama yeniden yönlendirmesini ekleme gerekir:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```

