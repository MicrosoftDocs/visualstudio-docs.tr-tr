---
title: Standart ve özel araç takımı yapılandırmaları | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2018
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e9f851734a4066e1f6ab7956d124478e0cde76c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815487"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standart ve özel araç takımı yapılandırmaları
Bir MSBuild araç takımı, görevleri ve hedefleri uygulaması projesi oluşturmak için kullanabileceğiniz araçları başvurular içerir. Standart bir araç takımı MSBuild içerir, ancak özel araç takımları de oluşturabilirsiniz. Bir araç takımı belirtme hakkında daha fazla bilgi için bkz: [araç takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)  
  
## <a name="standard-toolset-configurations"></a>Standart araç takımı yapılandırmaları  
 MSBuild 15.0 aşağıdaki standart araç takımları içerir:  
  
|ToolsVersion|Araç yolu (olarak MSBuildToolsPath veya MSBuildBinPath derleme özelliğinde belirtilen)|  
|------------------| - |  
|2,0|*\<Windows yükleme yolu > \Microsoft.Net\Framework\v2.0.50727\\*|  
|3.5|*\<Windows yükleme yolu > \Microsoft.NET\Framework\v3.5\\*|  
|4.0|*\<Windows yükleme yolu > \Microsoft.NET\Framework\v4.0.30319\\*|  
|15.0|*\<Visual Studio yükleme yolu > \MSBuild\15.0\bin*|  
  
 `ToolsVersion` Değeri belirleyen araç takımı tarafından kullanılan bir projeyi Visual Studio oluşturur. Visual Studio 2017'de, varsayılan değer "15.0" (olsun, proje dosyasında belirtilen hangi sürümü) olmakla birlikte kullanarak bu özniteliği geçersiz kılabilirsiniz **/toolsversion** geçiş komut isteminde. Bu öznitelik ve belirtmek üzere diğer yöntemler hakkında bilgi için `ToolsVersion`, bkz: [geçersiz kılma ToolsVersion ayarlarını](../msbuild/overriding-toolsversion-settings.md).  
  
 Visual Studio 2017 için MSBuild yolu kayıt defteri anahtarı kullanmaz. MSBuild'ın Visual Studio 2017 ile yüklenen 15.0 önceki sürümleri için aşağıdaki kayıt defteri anahtarlarını MSBuild.exe yükleme yolunu belirtin.  
  
|Kayıt defteri anahtarı|Anahtar adı|Dize anahtar değeri|  
|------------------|--------------|----------------------|  
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\2.0\\** |**MSBuildToolsPath**|**.NET framework 2.0 yükleme yolu**|  
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\\** |**MSBuildToolsPath**|**.NET framework 3.5 yükleme yolu**|  
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\\** |**MSBuildToolsPath**|**.NET framework 4 yükleme yolu**|  
  
### <a name="sub-toolsets"></a>Alt araç takımları  
 Önceki tablodaki kayıt defteri anahtarı bir alt varsa, MSBuild araç takımı üst yolu geçersiz kılan bir sub-araç yolu belirlemek için kullanır. Aşağıdaki alt anahtarını bir örnek verilmiştir:  
  
 **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0**  
  
 Araç takımında alt özellik tanımları, herhangi bir özelliği, hem taban araç takımını hem de seçili alt araç tanımlanmışsa kullanılır. Örneğin, MSBuild 4.0 araç takımı tanımlar `SDK40ToolsPath` 7.0a için SDK, ancak ' % s'MSBuild 4.0\11.0 işaret edecek şekilde araç takımı için 8.0a işaret edecek şekilde aynı özelliğe tanımlar SDK. Varsa `VisualStudioVersion` ayarlanmamış, `SDK40ToolsPath` , ancak 7.0a noktasında olduğu `VisualStudioVersion` özelliği 8.0a için bunun yerine noktasında olduğu 11.0 için ayarlanır.  
  
 `VisualStudioVersion` Yapı özelliği, bir alt Araç Takımı'nın etkin olduğu olup olmadığını gösterir. Örneğin, bir `VisualStudioVersion` MSBuild 12.0 alt araç "12.0" değerini belirtir. Daha fazla bilgi için alt araç takımları bölümüne bakın. [araç takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
> [!NOTE]
>  Bu ayarların değiştirilmesi kaçınmanızı öneririz. Bununla birlikte, kendi ayarlarınızı ekleyebilir ve sonraki bölümde açıklandığı gibi bilgisayar genelinde özel araç takımı tanımları tanımlayın.  
  
## <a name="custom-toolset-definitions"></a>Özel araç takımı tanımları  
 Standart bir araç takımı, derleme gereksinimlerini yerine getirmiyor zaman özel bir araç kümesi oluşturabilirsiniz. Örneğin, hangi gerekir ayrı bir sistem oluşturmak için bir derleme Laboratuvar senaryo olabilir [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projeleri. Özel bir araç takımı'nı kullanarak için özel değerler atayabilirsiniz `ToolsVersion` özniteliği, projeler oluşturun veya çalıştırdığınızda *MSBuild.exe*. Bunu yaparak, ayrıca kullanabileceğiniz `$(MSBuildToolsPath)` içeri aktarmak için özellik *.targets* bu dizine yanı sıra bu araç takımı kullanan herhangi bir proje için kullanılabilecek kendi özel araç takımı özellikleri tanımlama dosyaları.  
  
 Yapılandırma dosyası özel bir araç takımı belirtin *MSBuild.exe* (veya kullanmakta olduğunuz ise, MSBuild barındıran bir özel araç altyapısı). Örneğin, yapılandırma dosyası *MSBuild.exe* ToolsVersion 15.0 varsayılan davranışı geçersiz kılma istediğinizde, aşağıdaki araç takımı tanımını içerebilir.  
  
```xml  
<msbuildToolsets default="15.0">  
   <toolset toolsVersion="15.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 `<msbuildToolsets>` Ayrıca aşağıdaki gibi yapılandırma dosyasında tanımlanmalıdır.  
  
```xml  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=15.1.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  Doğru bir şekilde okunacak `<configSections>` ilk alt bölümünde olmalıdır `<configuration>` bölümü.  
  
 `ToolsetConfigurationSection` Özel yapılandırma için bir MSBuild ana bilgisayarı tarafından kullanılabilecek özel yapılandırma bölümü var. Özel bir araç takımı kullanırsanız, bir ana bilgisayar yapılandırma dosyası girdileri sağlamak dışında yapı altyapısının başlatmak için herhangi bir işlem yok. Kayıt defterinde girişleri tanımlayarak geçerli bilgisayar genelinde araç takımları belirtebilirsiniz *MSBuild.exe*, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ve MSBuild'ın tüm konaklar.  
  
> [!NOTE]
>  Bir yapılandırma dosyası için ayarları tanımlıyorsa bir `ToolsVersion` , zaten tanımlandı kayıt defterinde, iki tanımın birleştirilmez. Yapılandırma dosyası tanımında öncelik ve ayarlar kayıt defterinde için alan `ToolsVersion` göz ardı edilir.  
  
 Aşağıdaki özellikler değerine belirli `ToolsVersion` diğer bir deyişle kullanılan projeleri:  
  
- **$(MSBuildBinPath)** ayarlanır `ToolsPath` kayıt defteri veya yapılandırma dosyasında belirtilen değeri burada `ToolsVersion` tanımlanır. `$(MSBuildToolsPath)` Kayıt defteri veya yapılandırma dosyası ayarı core görevleri ve hedefleri konumunu belirtir. Proje dosyasında bu $(MSBuildBinPath) özelliğine ve $(MSBuildToolsPath) özelliğine eşler.  
  
- `$(MSBuildToolsPath)` yapılandırma dosyasında belirtilen MSBuildToolsPath özelliği tarafından sağlanan ayrılmış bir özelliktir. (Bu özellik değiştirir `$(MSBuildBinPath)`. Ancak, `$(MSBuildBinPath)` İleri Uyumluluk için gerçekleştirilir.) Özel bir araç takımı ya da tanımlamanız gerekir `$(MSBuildToolsPath)` veya `$(MSBuildBinPath)` ancak ikisi birden değil, her ikisi de aynı değere sahip.  
  
  MSBuildToolsPath özelliği eklemek için kullandığınız aynı sözdizimini kullanarak yapılandırma dosyasına, ToolsVersion özgü özel özellikleri de ekleyebilirsiniz. Bu özel özelliklerin proje dosyasının kullanılabilir hale getirmek için yapılandırma dosyasında belirtilen değerin adıyla aynı adı kullanın. Yapılandırma dosyasında araç takımları ancak sub-takımları tanımlayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)