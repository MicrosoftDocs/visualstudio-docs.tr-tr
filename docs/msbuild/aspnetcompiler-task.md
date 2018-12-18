---
title: ASP.NET uygulamaları derleneceği AspNetCompiler görevi kullanılarak | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 69971e72569dcae1f02f1e2b7988ef15f881fe85
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945175"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler görevi
`AspNetCompiler` Görev sarar *aspnet_compiler.exe*, önceden derlemek için bir yardımcı program [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamalar.  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Parametreleri aşağıdaki tabloda açıklanmıştır `AspNetCompiler` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AllowPartiallyTrustedCallers`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Bu parametre `true`, tanımlayıcı ad bütünleştirilmiş kod kısmen güvenilen arayanlara izin verir.|  
|`Clean`|İsteğe bağlı `Boolean` parametresi<br /><br /> Bu parametre `true`, uygulamanın temiz oluşturulacaktır. Önceden derlenmiş bileşenler yeniden derlenecek. Varsayılan değer `false` şeklindedir. Bu parametre için karşılık gelen **- c** açın *aspnet_compiler.exe*.|  
|`Debug`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Bu parametre `true`, hata ayıklama bilgileri (. PDB dosyası), derleme sırasında yayınlanır. Varsayılan değer `false` şeklindedir. Bu parametre için karşılık gelen **-d** açın *aspnet_compiler.exe*.|  
|`DelaySign`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Bu parametre `true`, derlemenin tam olarak oluştururken imzalı değil.|  
|`FixedNames`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Bu parametre `true`, derlenmiş bütünleştirilmiş sabit adlar verilir...|  
|`Force`|İsteğe bağlı `Boolean` parametresi<br /><br /> Bu parametre `true`, zaten varsa, görev hedef dizine üzerine yazar. Mevcut içerik kaybolur. Varsayılan değer `false` şeklindedir. Bu parametre için karşılık gelen **-f** açın *aspnet_compiler.exe*.|  
|`KeyContainer`|İsteğe bağlı `String` parametresi.<br /><br /> Tanımlayıcı ad anahtar kapsayıcısı belirtir.|  
|`KeyFile`|İsteğe bağlı `String` parametresi.<br /><br /> Tanımlayıcı ad anahtar dosyası fiziksel yolunu belirtir...|  
|`MetabasePath`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın tam IIS metatabanı yolu belirtir. Bu parametre ile birleştirilemez `VirtualPath` veya `PhysicalPath` parametreleri. Bu parametre için karşılık gelen **-m** açın *aspnet_compiler.exe*.|  
|`PhysicalPath`|İsteğe bağlı `String` parametresi.<br /><br /> Derlenecek uygulamanın fiziksel yolu belirtir. Bu parametre yoksa, IIS metabase uygulamayı bulmak için kullanılır. Bu parametre için karşılık gelen **-p** açın *aspnet_compiler.exe*.|  
|`TargetFrameworkMoniker`|İsteğe bağlı `String` parametresi.<br /><br /> Hangi .NET Framework sürümünü gösteren TargetFrameworkMoniker belirtir *aspnet_compiler.exe* kullanılmalıdır. Yalnızca .NET Framework adlar kabul eder.|  
|`TargetPath`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın derlenmiş olan fiziksel yolunu belirtir. Belirtilmezse, yerinde önceden derlenmiş uygulamasıdır.|  
|`Updateable`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Bu parametre `true`, önceden derlenmiş uygulama güncelleştirilebilir.  Varsayılan değer `false` şeklindedir. Bu parametre için karşılık gelen **-u** açın *aspnet_compiler.exe*.|  
|`VirtualPath`|İsteğe bağlı `String` parametresi.<br /><br /> Derlenecek uygulamanın sanal yolu. Varsa `PhysicalPath` belirtilen fiziksel yola uygulamayı bulmak için kullanılır. Aksi takdirde, IIS metabase kullanılır ve uygulamanın varsayılan sitenin olduğu varsayılır. Bu parametre için karşılık gelen **- v** açın *aspnet_compiler.exe*.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.ToolTask> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [ToolTaskExtension taban sınıfı](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `AspNetCompiler` derleneceği görev bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulama.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
