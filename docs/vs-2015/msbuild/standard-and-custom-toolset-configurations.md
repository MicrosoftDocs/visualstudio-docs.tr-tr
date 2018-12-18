---
title: Standart ve özel araç takımı yapılandırmaları | Microsoft Docs
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
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a1d57903ec2a8c3afb439f27433898467028eb6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906708"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standart ve Özel Araç Takımı Yapılandırmaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Bir MSBuild araç takımı, görevleri ve hedefleri uygulaması projesi oluşturmak için kullanabileceğiniz araçları başvurular içerir. Standart bir araç takımı MSBuild içerir, ancak özel araç takımları de oluşturabilirsiniz. Bir araç takımı belirtme hakkında daha fazla bilgi için bkz: [araç takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)  

## <a name="standard-toolset-configurations"></a>Standart araç takımı yapılandırmaları  
 MSBuild 12.0, aşağıdaki standart araç takımları içerir:  


| ToolsVersion | Araç yolu (olarak MSBuildToolsPath veya MSBuildBinPath derleme özelliğinde belirtilen) |
|--------------|--------------------------------------------------------------------------------------|
|     2,0      |           *Windows yükleme yolu*\Microsoft.Net\Framework\v2.0.50727\            |
|     3.5      |              *Windows yükleme yolu*\Microsoft.NET\Framework\v3.5\               |
|     4.0      |           *Windows yükleme yolu*\Microsoft.NET\Framework\v4.0.30319\            |
|     12.0     |                          *% ProgramFiles %* \MSBuild\12.0\bin                           |

 `ToolsVersion` Değeri belirleyen araç takımı tarafından kullanılan bir projeyi Visual Studio oluşturur. İçinde [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] varsayılan değer (olsun, proje dosyasında belirtilen hangi sürümü) "12.0" dır ancak kullanarak bu özniteliği geçersiz kılabilirsiniz **/toolsversion** geçiş komut isteminde. Bu öznitelik ve belirtmek üzere diğer yöntemler hakkında bilgi için `ToolsVersion`, bkz: [ToolsVersion ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).  

 Varsa `ToolsVersion` belirlenmezse, kayıt defteri anahtarı **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\\< sürüm numarası\>\DefaultToolsVersion** tanımlar `ToolsVersion`, olduğu her zaman 2.0.  

 Aşağıdaki kayıt defteri anahtarlarını MSBuild.exe yükleme yolunu belirtin.  

|Kayıt Defteri Anahtarı|Anahtar adı|Dize anahtar değeri|  
|------------------|--------------|----------------------|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0\|MSBuildToolsPath|.NET framework 2.0 yükleme yolu|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\|MSBuildToolsPath|.NET framework 3.5 yükleme yolu|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\|MSBuildToolsPath|.NET framework 4 yükleme yolu|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\12.0\|MSBuildToolsPath|MSBuild yükleme yolu|  

### <a name="sub-toolsets"></a>Alt araç takımları  
 Önceki tablodaki kayıt defteri anahtarı bir alt varsa, MSBuild bunu bir araç kümesi alt yolu üst araç takımı yolunda geçersiz kılabilir belirlemek için kullanır. Aşağıdaki alt anahtarını bir örnek verilmiştir:  

 \HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  

 Araç takımında alt özellik tanımları, herhangi bir özelliği, hem taban araç takımını hem de seçili alt araç tanımlanmışsa kullanılır. Örneğin, MSBuild 4.0 araç takımı tanımlar `SDK40ToolsPath` 7.0a için SDK, ancak ' % s'MSBuild 4.0\11.0 işaret edecek şekilde araç takımı için 8.0a işaret edecek şekilde aynı özelliğe tanımlar SDK. Varsa `VisualStudioVersion` ayarlanmamış, `SDK40ToolsPath` , ancak 7.0a noktasında olduğu `VisualStudioVersion` özelliği 8.0a için bunun yerine noktasında olduğu 11.0 için ayarlanır.  

 `VisualStudioVersion` Yapı özelliği, bir alt Araç Takımı'nın etkin olduğu olup olmadığını gösterir. Örneğin, bir `VisualStudioVersion` MSBuild 12.0 alt araç "12.0" değerini belirtir. Daha fazla bilgi için alt araç takımları bölümüne bakın. [araç takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  

> [!NOTE]
>  Bu ayarların değiştirilmesi kaçınmanızı öneririz. Bununla birlikte, kendi ayarlarınızı ekleyebilir ve sonraki bölümde açıklandığı gibi bilgisayar genelinde özel araç takımı tanımları tanımlayın.  

## <a name="custom-toolset-definitions"></a>Özel araç takımı tanımları  
 Standart bir araç takımı, derleme gereksinimlerini yerine getirmiyor zaman özel bir araç kümesi oluşturabilirsiniz. Örneğin, hangi gerekir ayrı bir sistem oluşturmak için bir derleme Laboratuvar senaryo olabilir [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projeleri. Özel bir araç takımı'nı kullanarak için özel değerler atayabilirsiniz `ToolsVersion` özniteliği projeleri oluşturduğunuzda veya MSBuild.exe çalıştırın. Bunu yaparak, ayrıca kullanabileceğiniz `$(MSBuildToolsPath)` bu dizine yanı sıra bu araç takımı kullanan herhangi bir proje için kullanılabilecek kendi özel araç takımı özellikleri tanımlamaya .targets dosyaları aktarmak için özellik.  

 Özel bir araç takımı, MSBuild.exe (veya kullanmakta olduğunuz ise, MSBuild altyapısına barındıran özel aracı) yapılandırma dosyasında belirtin. Örneğin, MSBuild.exe yapılandırma dosyası ToolsVersion 12.0 varsayılan davranışı geçersiz kılma istediğinizde, aşağıdaki araç takımı tanımını içerebilir.  

```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  

 `<msbuildToolsets>` Ayrıca aşağıdaki gibi yapılandırma dosyasında tanımlanmalıdır.  

```  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  

> [!NOTE]
>  Doğru bir şekilde okunacak `<configSections>` ilk alt bölümünde olmalıdır `<configuration>` bölümü.  

 `ToolsetConfigurationSection` Özel yapılandırma için bir MSBuild ana bilgisayarı tarafından kullanılabilecek özel yapılandırma bölümü var. Özel bir araç takımı kullanırsanız, bir ana bilgisayar yapılandırma dosyası girdileri sağlamak dışında yapı altyapısının başlatmak için herhangi bir işlem yok. Kayıt defterinde girişleri tanımlayarak, MSBuild.exe için geçerli bir bilgisayar genelinde araç takımları belirtebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ve MSBuild'ın tüm konaklar.  

> [!NOTE]
>  Bir yapılandırma dosyası için ayarları tanımlıyorsa bir `ToolsVersion` , zaten tanımlandı kayıt defterinde, iki tanımın birleştirilmez. Yapılandırma dosyası tanımında öncelik ve ayarlar kayıt defterinde için alan `ToolsVersion` göz ardı edilir.  

 Aşağıdaki özellikler değerine belirli `ToolsVersion` diğer bir deyişle kullanılan projeleri:  

- **$(MSBuildBinPath)** ayarlanır `ToolsPath` kayıt defteri veya yapılandırma dosyasında belirtilen değeri burada `ToolsVersion` tanımlanır. `$(MSBuildToolsPath)` Kayıt defteri veya yapılandırma dosyası ayarı core görevleri ve hedefleri konumunu belirtir. Proje dosyasında bu $(MSBuildBinPath) özelliğine ve $(MSBuildToolsPath) özelliğine eşler.  

- `$(MSBuildToolsPath)` yapılandırma dosyasında belirtilen MSBuildToolsPath özelliği tarafından sağlanan ayrılmış bir özelliktir. (Bu özellik değiştirir `$(MSBuildBinPath)`. Ancak, `$(MSBuildBinPath)` İleri Uyumluluk için gerçekleştirilir.) Özel bir araç takımı ya da tanımlamanız gerekir `$(MSBuildToolsPath)` veya `$(MSBuildBinPath)` ancak ikisi birden değil, her ikisi de aynı değere sahip.  

  MSBuildToolsPath özelliği eklemek için kullandığınız aynı sözdizimini kullanarak yapılandırma dosyasına, ToolsVersion özgü özel özellikleri de ekleyebilirsiniz. Bu özel özelliklerin proje dosyasının kullanılabilir hale getirmek için yapılandırma dosyasında belirtilen değerin adıyla aynı adı kullanın. Yapılandırma dosyasında araç takımları ancak sub-takımları tanımlayabilir.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)



