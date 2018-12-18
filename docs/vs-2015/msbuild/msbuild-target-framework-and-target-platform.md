---
title: MSBuild hedef çerçevesi ve hedef Platform | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74ca7eb25aac26eb66628ea76be502e4a244a2bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923374"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild Hedef Çerçevesi ve Hedef Platformu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Çalıştırmak için bir proje oluşturulabilmeden bir *hedef Framework'ü*, .NET Framework'ün belirli bir sürümü olduğu ve bir *hedef platform*, belirli yazılım mimarisi olduğu.  Örneğin, 802 x 86 işlemci ailesi ("x86") ile uyumlu bir 32 bit platformda .NET Framework 2.0 üzerinde çalışacak bir uygulamayı hedefleyebilirsiniz. Hedef Çerçeve ve hedef platform bileşimi olarak da bilinen *hedef bağlam*.  
  
## <a name="target-framework-and-profile"></a>Hedef Framework ve profili  
 Hedef Framework'ü belirli sürümüdür [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , projenizi çalıştırmak için oluşturulmuştur. Derleyici özelliklerini ve framework'ün bu sürümüne özel derleme başvurularını sağladığından, hedef framework'ün belirtimi gereklidir.  
  
 Şu anda, .NET Framework'ün aşağıdaki sürümler kullanılabilir duruma gelir:  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] (Visual Studio 2005'te dahil) 2.0  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.0 (dahil [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.5 (dahil [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 (Visual Studio 2010'da dahildir)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5 (dahil [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.1 (dahil [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.2  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.6 (dahil [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)])  
  
  .NET Framework sürümleri her başvurmak kullanılabilir hale derlemeler listesi içinde birbirinden farklı. Örneğin, projeniz .NET Framework sürüm 3.0 hedefleyen sürece veya yukarıda Windows Presentation Foundation (WPF) uygulamaları oluşturamaz.  
  
  Hedef Framework'ü belirtilen `TargetFrameworkVersion` proje dosyasındaki özellik. Visual Studio tümleşik geliştirme ortamında (IDE) proje özellik sayfalarını kullanarak bir proje için hedef çerçeveyi değiştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Kullanılabilir değerler için `TargetFrameworkVersion` olan `v2.0`, `v3.0`, `v3.5`, `v4.0`, `v4.5`, `v4.5.1`, `v4.5.2`, ve `v4.6`.  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 A *hedef profil* hedef framework'ün bir alt kümesidir. Örneğin, .NET Framework 4 istemci profili, MSBuild derlemelere başvuruları içermez.  
  
 Hedef profil belirtilen `TargetFrameworkProfile` bir proje dosyası bir özellik. Hedef profil IDE'de proje özelliği sayfalarından hedef çerçeve denetimi kullanarak değiştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Hedef Platform  
 A *platform* , belirli bir çalışma zamanı ortamı tanımlayan donanım ve yazılım birleşimidir. Örneğin,  
  
- `x86` Intel 80 x 86 işlemcisi ya da eşdeğerine çalışan 32 bit Windows işletim sistemi belirtir.  
  
- `Xbox` Xbox 360'ı Microsoft Platformu belirtir.  
  
  A *hedef platform* projenizi çalıştırmak için oluşturulmuştur belirli platformudur. Hedef platform belirtilen `Platform` özelliğinde bir proje dosyası oluşturun. Hedef platform proje özelliği sayfalarından kullanarak değiştirebileceğiniz veya **Configuration Manager** IDE.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 A *hedef Yapılandırması* bir hedef platformu için bir alt kümesidir. Örneğin, `x86``Debug` yapılandırma çoğu kod iyileştirmeleri dahil değildir. Hedef yapılandırmasında belirtilen `Configuration` özelliğinde bir proje dosyası oluşturun. Proje özellik sayfalarını kullanarak hedef yapılandırmasını değiştirebilirsiniz veya **Configuration Manager**.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)



