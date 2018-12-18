---
title: MSBuild araç takımı (ToolsVersion) | Microsoft Docs
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
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd516501acfc7690c12a253adc5da6cf163b5592
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851835"
---
# <a name="msbuild-toolset-toolsversion"></a>MSBuild Araç Takımı (ToolsVersion)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild, bir uygulama oluşturmak için bir araç takımı görevleri, hedefler ve araçları kullanır. MSBuild araç takımı, genellikle microsoft.common.tasks dosya, Microsoft.common.targets'ı dosya ve csc.exe ve vbc.exe gibi derleyicileri içerir. Çoğu araç takımları, .NET Framework'ün birden fazla sürümü ve birden fazla sistemi platformu uygulamaları derlemek için kullanılabilir. Ancak, MSBuild 2.0 araç takımı, yalnızca .NET Framework 2.0 hedeflemek için kullanılabilir.  
  
## <a name="toolsversion-attribute"></a>ToolsVersion özniteliği  
 Araç kümesinde belirtin `ToolsVersion` özniteliği [proje](../msbuild/project-element-msbuild.md) proje dosyasındaki öğesi. Aşağıdaki örnek proje MSBuild 12.0 araç setini kullanarak oluşturulması gerektiğini belirtir.  
  
```  
<Project ToolsVersion="12.0" ... </Project>  
```  
  
## <a name="how-the-toolsversion-attribute-works"></a>ToolsVersion özniteliği nasıl çalışır?  
 Visual Studio'da bir proje oluşturun veya mevcut bir projeyi yükseltmesine adlı bir öznitelik `ToolsVersion` otomatik olarak eklenir projeye dosya ve değerine karşılık gelen Visual Studio sürümü dahildir MSBuild'ın sürümü için. Daha fazla bilgi için [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Olduğunda bir `ToolsVersion` değer proje dosyasında tanımlanan, MSBuild, proje için kullanılabilir araç takımı özelliklerin değerlerini belirlemek için bu değeri kullanır. Bir araç takımı özelliği `$(MSBuildToolsPath)`, .NET Framework Araçları yolunu belirtir. Yalnızca bu araç takımı özelliği (veya `$(MSBuildBinPath)`), gerekli değildir.  
  
 Visual Studio 2013'te başlayarak, MSBuild araç takımı sürümü Visual Studio sürüm numarası ile aynı olur. Varsayılan olarak bu araç, Visual Studio içinden ve proje dosyasında belirtilen araç takımının sürüm ne olursa olsun komut satırında MSBuild.  Bu davranış /ToolsVersion bayrağı kullanılarak geçersiz kılınabilir. Daha fazla bilgi için [ToolsVersion ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).  
  
 Aşağıdaki örnekte, MSBuild kullanılarak Microsoft.CSharp.targets dosyayı bulur `MSBuildToolsPath` ayrılmış özelliği.  
  
```  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Değerini değiştirebilirsiniz `MSBuildToolsPath` özel bir araç kümesi tanımlayarak. Daha fazla bilgi için [standart ve özel araç takımı yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md)  
  
 Komut satırında bir çözüm derleyin ve belirtin, bir `ToolsVersion` msbuild.exe için tüm projeleri ve proje proje bağımlılıklarını göre yerleşik olan `ToolsVersion`çözümde her proje kendi belirtir bile `ToolsVersion`. Tanımlamak için `ToolsVersion` proje bazında değeri için bkz: [ToolsVersion ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).  
  
 `ToolsVersion` Özniteliği proje geçişi için de kullanılır. Visual Studio 2010'da Visual Studio 2008 proje açarsanız, örneğin, proje dosyası ToolsVersion içerecek şekilde güncelleştirilmiştir = "4.0". Ardından Visual Studio 2008'de bu projeyi açmaya çalışırsanız, yükseltilen tanımıyor `ToolsVersion` ve bu nedenle, öznitelik 3.5 hala ayarlanmış olsa projeyi oluşturur.  
  
 Visual Studio 2010 ve Visual Studio 2012 bir ToolsVersion 4. 0'ı kullanın. Visual Studio 2013'ün bir ToolsVersion 12.0 birini kullanır. Çoğu durumda, projenin yapmadan Visual Studio'nun üç sürümde de açabilirsiniz. Visual Studio, her zaman doğru araç takımı kullanır, ancak kullanılan sürümü proje dosyasında sürüm eşleşmiyorsa size bildirilir. Hemen hemen tüm durumlarda, bu uyarı araç takımları çoğu zaman uyumlu olarak zararsızdır.  
  
 Bu konunun ilerleyen bölümlerinde açıklanan Sub-takımları, MSBuild araçları kullanmak için hangi kümesi yapının çalıştırıldığı bağlama göre otomatik olarak değiştirmek izin verin. Örneğin, Visual Studio 2012'de, Visual Studio 2010'da, açıkça proje dosyasını değiştirmek zorunda kalmadan çalıştırıldığında çalıştırıldığında MSBuild daha yeni bir araç kümesi kullanır. Daha fazla bilgi için [yapmadan özel projeler sürümü kullanan](../misc/making-custom-projects-version-aware.md).  
  
## <a name="toolset-implementation"></a>Araç takımını uygulama  
 Bir araç takımı, çeşitli araçlar, hedefler ve araç takımı ' yapan görev yollarını seçerek uygulayın. MSBuild tanımlayan araç takımı araçlarında aşağıdaki kaynaklardan gelir:  
  
- .NET Framework klasör.  
  
- Ek yönetilen araçlar.  
  
  ResGen.exe ve Tlbimp.exe'nin yönetilen araçlar içerir.  
  
  MSBuild araç takımı erişmek için iki yol sunar:  
  
- Araç özelliklerini kullanarak  
  
- Kullanarak <xref:Microsoft.Build.Utilities.ToolLocationHelper> yöntemleri  
  
  Araç Özellikleri araçları yollarını belirtin. MSBuild değerini kullanır `ToolsVersion` araç özelliklerini ayarlamak için kayıt defteri anahtarı bilgileri sonra kullanır ve karşılık gelen kayıt defteri anahtarını bulmak için proje dosyasında özniteliği. Örneğin, varsa `ToolsVersion` değerine sahip `12.0`, MSBuild araç takımı özelliklerini bu kayıt defteri anahtarı göre ayarlar: HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0.  
  
  Araç özellikleri şunlardır:  
  
- `MSBuildToolsPath` MSBuild ikili dosyalarının yolunu belirtir.  
  
- `SDK40ToolsPath` MSBuild için ek yönetilen araçları yolunu belirtir (Bu 4.0 veya 4.5 olabilir) 4.x.  
  
- `SDK35ToolsPath` MSBuild 3.5 için ek yönetilen araçları yolunu belirtir.  
  
  Alternatif olarak, araç takımı program aracılığıyla yöntemleri çağırarak belirleyebilirsiniz <xref:Microsoft.Build.Utilities.ToolLocationHelper> sınıfı. Sınıfı, bu yöntem içerir:  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> .NET Framework klasörünün yolunu döndürür.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> .NET Framework klasöründe bir dosya yolunu döndürür.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> Yönetilen Araçları klasörünün yolunu döndürür.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> genellikle yönetilen Araçlar klasöründe bulunan bir dosyanın yolunu döndürür.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToBuildTools%2A> derleme araçları yolunu döndürür.  
  
### <a name="sub-toolsets"></a>Alt araç takımları  
 Bu konunun önceki kısımlarında açıklandığı gibi MSBuild olan temel araçları yolunu belirtmek için bir kayıt defteri anahtarını kullanır. Bir alt anahtar varsa, MSBuild ek araçlarını içeren bir alt-araç yolu belirlemek için kullanır. Bu durumda, araç takımını hem anahtarlarında tanımlanan özellik tanımları birleştirerek tanımlanır.  
  
> [!NOTE]
>  Araç takımı özellik adları çakışıyorsa, alt anahtar yolunu tanımlanan değerin kök anahtar yolu için tanımlanan değer geçersiz kılar.  
  
 Alt araç takımları varken etkin hale `VisualStudioVersion` özellik oluşturun. Bu özellik, bu değerlerden birini alabilir:  
  
- "10.0".NET Framework 4 alt araç belirtir  
  
- "11.0".NET Framework 4.5 alt araç belirtir  
  
- "12.0".NET Framework 4.5.1 alt araç belirtir  
  
  Alt-takımları 10.0 ve 11.0 ToolsVersion 4.0 ile kullanılmalıdır. Sonraki sürümlerde, alt araç kümesi sürümünü ve ToolsVersion eşleşmesi gerekir.  
  
  Bir derleme sırasında MSBuild otomatik olarak belirleyen ve ayarlar için varsayılan bir değer `VisualStudioVersion` zaten tanımlanmışsa özelliği.  
  
  MSBuild için aşırı yüklemeler sağlar `ToolLocationHelper` ekleme yöntemleri bir `VisualStudioVersion` numaralandırılmış bir parametre değeri  
  
  Alt araç takımları .NET Framework 4. 5 ' kullanılmaya başlanmıştır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Standart ve özel araç takımı yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)



