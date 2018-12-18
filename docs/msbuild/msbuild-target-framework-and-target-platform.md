---
title: MSBuild hedef çerçevesi ve hedef Platform | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfb45efc199ea1f643c71bdc19a90862bb6c5dd6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916068"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild hedef çerçevesi ve hedef platform
Çalıştırmak için bir proje oluşturulabilmeden bir *hedef Framework'ü*, .NET Framework'ün belirli bir sürümü olduğu ve bir *hedef platform*, belirli yazılım mimarisi olduğu.  Örneğin, 802 x 86 işlemci ailesi ("x86") ile uyumlu bir 32 bit platformda .NET Framework 2.0 üzerinde çalışacak bir uygulamayı hedefleyebilirsiniz. Hedef Çerçeve ve hedef platform bileşimi olarak da bilinen *hedef bağlam*.  
  
## <a name="target-framework-and-profile"></a>Hedef framework ve profili  
 Hedef Framework'ü belirli sürümüdür [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , projenizi çalıştırmak için oluşturulmuştur. Derleyici özelliklerini ve framework'ün bu sürümüne özel derleme başvurularını sağladığından, hedef framework'ün belirtimi gereklidir.  
  
 Şu anda, .NET Framework'ün aşağıdaki sürümler kullanılabilir duruma gelir:  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] (Visual Studio 2005'te dahil) 2.0  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0 (dahil [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 (dahil [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.2  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6 (dahil [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.1  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.2  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7.1  

.NET Framework sürümleri her başvurmak kullanılabilir hale derlemeler listesi içinde birbirinden farklı. Örneğin, projeniz .NET Framework sürüm 3.0 hedefleyen sürece veya yukarıda Windows Presentation Foundation (WPF) uygulamaları oluşturamaz.  

Hedef Framework'ü belirtilen `TargetFrameworkVersion` proje dosyasındaki özellik. Visual Studio tümleşik geliştirme ortamında (IDE) proje özellik sayfalarını kullanarak bir proje için hedef çerçeveyi değiştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Kullanılabilir değerler için `TargetFrameworkVersion` olan `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v4.6.1`, `v4.6.2`, `v4.7`, ve `v4.7.1`.  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 A *hedef profil* hedef framework'ün bir alt kümesidir. Örneğin, .NET Framework 4 istemci profili, MSBuild derlemelere başvuruları içermez.  
  
 Hedef profil belirtilen `TargetFrameworkProfile` bir proje dosyası bir özellik. Hedef profil IDE'de proje özelliği sayfalarından hedef çerçeve denetimi kullanarak değiştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Hedef platform  
 A *platform* , belirli bir çalışma zamanı ortamı tanımlayan donanım ve yazılım birleşimidir. Örneğin,  
  
-   `x86` Intel 80 x 86 işlemcisi ya da eşdeğerine çalışan 32 bit Windows işletim sistemi belirtir.  

-   `x64` x64 Intel işlemci veya eşdeğeri, çalışan bir 64 bit Windows işletim sistemi belirtir.
  
-   `Xbox` Xbox 360'ı Microsoft Platformu belirtir.  

A *hedef platform* projenizi çalıştırmak için oluşturulmuştur belirli platformudur. Hedef platform belirtilen `PlatformTarget` özelliğinde bir proje dosyası oluşturun. Hedef platform proje özelliği sayfalarından kullanarak değiştirebileceğiniz veya **Configuration Manager** IDE.  

```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
</PropertyGroup>  

```  

A *hedef Yapılandırması* bir hedef platformu için bir alt kümesidir. Örneğin, `x86``Debug` yapılandırma çoğu kod iyileştirmeleri dahil değildir. Hedef yapılandırmasında belirtilen `Configuration` özelliğinde bir proje dosyası oluşturun. Proje özellik sayfalarını kullanarak hedef yapılandırmasını değiştirebilirsiniz veya **Configuration Manager**.  

```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
