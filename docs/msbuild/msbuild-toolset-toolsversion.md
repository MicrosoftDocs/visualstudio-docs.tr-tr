---
title: MSBuild araç takımı (ToolsVersion) | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2018
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: feedf1789e4ee3f6b7e04966d945a5a2638242c3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821116"
---
# <a name="msbuild-toolset-toolsversion"></a>MSBuild Araç Takımı (ToolsVersion)
MSBuild, bir uygulama oluşturmak için bir araç takımı görevleri, hedefler ve araçları kullanır. MSBuild araç takımı genellikle içerir bir *microsoft.common.tasks* dosyası bir *microsoft.common.targets* dosya ve derleyiciler gibi *csc.exe* ve  *Vbc.exe*. Çoğu araç takımları, .NET Framework'ün birden fazla sürümü ve birden fazla sistemi platformu uygulamaları derlemek için kullanılabilir. Ancak, MSBuild 2.0 araç takımı, yalnızca .NET Framework 2.0 hedeflemek için kullanılabilir.  
  
## <a name="toolsversion-attribute"></a>ToolsVersion özniteliği  
 Araç kümesinde belirtin `ToolsVersion` özniteliği [proje](../msbuild/project-element-msbuild.md) proje dosyasındaki öğesi. Aşağıdaki örnek proje MSBuild 15.0 araç setini kullanarak oluşturulması gerektiğini belirtir.  
  
```xml  
<Project ToolsVersion="15.0" ... </Project>  
``` 

> [!NOTE] 
> Bazı proje türü kullanım `sdk` özniteliği yerine `ToolsVersion`. Daha fazla bilgi için [paketler, meta verileri ve çerçeveleri](/dotnet/core/packages) ve [csproj eklemeler biçimlendirmek için .NET Core](/dotnet/core/tools/csproj).
  
## <a name="how-the-toolsversion-attribute-works"></a>ToolsVersion özniteliği nasıl çalışır?  
 Visual Studio'da bir proje oluşturun veya mevcut bir projeyi yükseltmesine adlı bir öznitelik `ToolsVersion` otomatik olarak eklenir projeye dosya ve değerine karşılık gelen Visual Studio sürümü dahildir MSBuild'ın sürümü için. Daha fazla bilgi için [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Olduğunda bir `ToolsVersion` değer proje dosyasında tanımlanan, MSBuild, proje için kullanılabilir araç takımı özelliklerin değerlerini belirlemek için bu değeri kullanır. Bir araç takımı özelliği `$(MSBuildToolsPath)`, .NET Framework Araçları yolunu belirtir. Yalnızca bu araç takımı özelliği (veya `$(MSBuildBinPath)`), gerekli değildir.  
  
 Visual Studio 2013'te başlayarak, MSBuild araç takımı sürümü Visual Studio sürüm numarası ile aynı olur. Varsayılan olarak bu araç, Visual Studio içinden ve proje dosyasında belirtilen araç takımının sürüm ne olursa olsun komut satırında MSBuild.  Bu davranış - ToolsVersion bayrağı kullanılarak geçersiz kılınabilir. Daha fazla bilgi için [geçersiz kılma ToolsVersion ayarlarını](../msbuild/overriding-toolsversion-settings.md).  
  
 Aşağıdaki örnekte, MSBuild bulur *Microsoft.CSharp.targets* kullanarak dosya `MSBuildToolsPath` ayrılmış özelliği.  
  
```xml  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Değerini değiştirebilirsiniz `MSBuildToolsPath` özel bir araç kümesi tanımlayarak. Daha fazla bilgi için [standart ve özel araç takımı yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md)  
  
 Komut satırında bir çözüm derleyin ve belirtin, bir `ToolsVersion` için *msbuild.exe*, tüm projeleri ve proje proje bağımlılıklarını göre yerleşik olan `ToolsVersion`bile çözümde her proje kendi belirtir `ToolsVersion`. Tanımlamak için `ToolsVersion` proje bazında değeri için bkz: [geçersiz kılma ToolsVersion ayarlarını](../msbuild/overriding-toolsversion-settings.md).  
  
 `ToolsVersion` Özniteliği proje geçişi için de kullanılır. Visual Studio 2010'da Visual Studio 2008 proje açarsanız, örneğin, proje dosyası ToolsVersion içerecek şekilde güncelleştirilmiştir = "4.0". Ardından Visual Studio 2008'de bu projeyi açmaya çalışırsanız, yükseltilen tanımıyor `ToolsVersion` ve bu nedenle, öznitelik 3.5 hala ayarlanmış olsa projeyi oluşturur.  
  
 Visual Studio 2010 ve Visual Studio 2012 bir ToolsVersion 4. 0'ı kullanın. Visual Studio 2013'ün bir ToolsVersion 12.0 birini kullanır. ToolsVersion 14.0 Visual Studio 2015 ve Visual Studio 2017 15.0 ToolsVersion kullanır. Çoğu durumda, birden fazla değişiklik yapmadan Visual Studio sürümlerinde projeyi açabilirsiniz. Visual Studio, her zaman doğru araç takımı kullanır, ancak kullanılan sürümü proje dosyasında sürüm eşleşmiyorsa size bildirilir. Hemen hemen tüm durumlarda, bu uyarı araç takımları çoğu zaman uyumlu olarak zararsızdır.  
  
 Bu konunun ilerleyen bölümlerinde açıklanan Sub-takımları, MSBuild araçları kullanmak için hangi kümesi yapının çalıştırıldığı bağlama göre otomatik olarak değiştirmek izin verin. Örneğin, Visual Studio 2012'de, Visual Studio 2010'da, açıkça proje dosyasını değiştirmek zorunda kalmadan çalıştırıldığında çalıştırıldığında MSBuild daha yeni bir araç kümesi kullanır.  
  
## <a name="toolset-implementation"></a>Araç takımını uygulama  
 Bir araç takımı, çeşitli araçlar, hedefler ve araç takımı ' yapan görev yollarını seçerek uygulayın. MSBuild tanımlayan araç takımı araçlarında aşağıdaki kaynaklardan gelir:  
  
- .NET Framework klasör.  
  
- Ek yönetilen araçlar.  
  
  Yönetilen araçlarda *ResGen.exe* ve *TlbImp.exe*.  

MSBuild araç takımı erişmek için iki yol sunar:  
  
-   Araç özelliklerini kullanarak  
  
-   Kullanarak <xref:Microsoft.Build.Utilities.ToolLocationHelper> yöntemleri  

Araç Özellikleri araçları yollarını belirtin. Visual Studio 2017'den başlayarak, MSBuild artık sabit bir konum vardır. Varsayılan olarak bulunur *MSBuild\15.0\Bin* klasörüyle ilgili Visual Studio yükleme konumu. Önceki sürümlerde, MSBuild değerini kullanır. `ToolsVersion` araç özelliklerini ayarlamak için kayıt defteri anahtarı bilgileri sonra kullanır ve karşılık gelen kayıt defteri anahtarını bulmak için proje dosyasında özniteliği. Örneğin, varsa `ToolsVersion` değerine sahip `12.0`, MSBuild araç takımı özelliklerini bu kayıt defteri anahtarı göre ayarlar: **HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0**.  
  
 Araç özellikleri şunlardır:  
  
-   `MSBuildToolsPath` MSBuild ikili dosyalarının yolunu belirtir.  
  
-   `SDK40ToolsPath` MSBuild için ek yönetilen araçları yolunu belirtir (Bu 4.0 veya 4.5 olabilir) 4.x.  
  
-   `SDK35ToolsPath` MSBuild 3.5 için ek yönetilen araçları yolunu belirtir.  

Alternatif olarak, araç takımı program aracılığıyla yöntemleri çağırarak belirleyebilirsiniz <xref:Microsoft.Build.Utilities.ToolLocationHelper> sınıfı. Sınıfı, bu yöntem içerir:  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> .NET Framework klasörünün yolunu döndürür.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> .NET Framework klasöründe bir dosya yolunu döndürür.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> Yönetilen Araçları klasörünün yolunu döndürür.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> genellikle yönetilen Araçlar klasöründe bulunan bir dosyanın yolunu döndürür.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToBuildTools%2A> derleme araçları yolunu döndürür.  
  
### <a name="sub-toolsets"></a>Alt araç takımları  
 MSBuild 15.0 önceki sürümler için MSBuild olan temel araçları yolunu belirtmek için bir kayıt defteri anahtarını kullanır. Bir alt anahtar varsa, MSBuild ek araçlarını içeren bir alt-araç yolu belirlemek için kullanır. Bu durumda, araç takımını hem anahtarlarında tanımlanan özellik tanımları birleştirerek tanımlanır.  
  
> [!NOTE]
>  Araç takımı özellik adları çakışıyorsa, alt anahtar yolunu tanımlanan değerin kök anahtar yolu için tanımlanan değer geçersiz kılar.  
  
 Alt araç takımları varken etkin hale `VisualStudioVersion` özellik oluşturun. Bu özellik, bu değerlerden birini alabilir:  
  
-   "10.0".NET Framework 4 alt araç belirtir  
  
-   "11.0".NET Framework 4.5 alt araç belirtir  
  
-   "12.0".NET Framework 4.5.1 alt araç belirtir 

Alt-takımları 10.0 ve 11.0 ToolsVersion 4.0 ile kullanılmalıdır. Sonraki sürümlerde, alt araç kümesi sürümünü ve ToolsVersion eşleşmesi gerekir.  

Bir derleme sırasında MSBuild otomatik olarak belirleyen ve ayarlar için varsayılan bir değer `VisualStudioVersion` zaten tanımlanmışsa özelliği.  

MSBuild için aşırı yüklemeler sağlar `ToolLocationHelper` ekleme yöntemleri bir `VisualStudioVersion` numaralandırılmış bir parametre değeri  

Alt araç takımları .NET Framework 4. 5 ' kullanılmaya başlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Standart ve özel araç takımı yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
