---
title: .NET Framework hedefleme hatalarının sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: acadd858a1327380fc606bed36994ba0dda47169
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280559"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>.NET Framework Hedefleme Hatalarının Sorunlarını Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu konuda başvurusu nedeniyle oluşabilecek MSBuild hataları açıklanır sorunlar ve bu hataların nasıl çözebilirsiniz.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Bir proje ya da farklı bir .NET Framework sürümünü hedefleyen derlemeye başvuru  
 Projelere veya farklı sürümlerini hedefleyen derlemelere başvuran uygulamalar oluşturabilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Örneğin, için istemci Profili'ni hedefleyen bir uygulama oluşturabilirsiniz [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ancak .NET Framework 2. 0'ı hedefleyen bir derlemeye başvurur. Ancak, önceki bir sürümünü hedefleyen bir proje oluşturursanız, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], projeye bir proje ya da için istemci Profili'ni hedefleyen derlemeye başvuru ayarlanamıyor [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] veya [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] kendisi. Hatayı gidermek için uygulamanızın bir profil veya projelere veya derlemelere göre uygulamanızı başvuran hedeflenen profiliyle uyumlu olan profilleri hedefler emin olun.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Bir proje .NET Framework'ün farklı bir sürüme yeniden hedeflenen  
 Hedef sürümü değiştirirseniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] uygulamanız için Visual Studio bazı başvuruları değiştirir, ancak bazı başvuruları el ile güncelleştirmeniz gerekebilir. Hedef uygulama değiştirirseniz, örneğin, bir durum önceden bahsedilmiş hatalarla oluşabilir [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)] ve uygulama kaynaklarına veya istemci profilini kullanan ayarları olduğunu [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)].  
  
 Uygulama ayarlarını geçici olarak çözmek için açık **Çözüm Gezgini**, seçin **tüm dosyaları göster**ve ardından Visual Studio XML düzenleyicisinde app.config dosyasını düzenleyin. Sürümü .NET Framework'ün uygun sürümünü eşleştirmek için ayarları değiştirin. Örneğin, 4.0.0.0 2.0.0.0 için sürüm ayarını değiştirebilirsiniz. Benzer şekilde, uygulamanın her zaman kaynakları eklemiştir açın **Çözüm Gezgini**, seçin **tüm dosyaları göster** sırasıyla, düğme **Projem** (Visual Basic) veya **Özellikleri** (C#) ve ardından Visual Studio XML düzenleyicisinde Resources.resx dosyasını düzenleyin. Sürüm ayarı 4.0.0.0 2.0.0.0 için değiştirin.  
  
 Uygulamanızın simgeleri veya bit eşlemleri gibi kaynaklara veya veri bağlantı dizeleri gibi ayarları varsa, ayrıca hata üzerinde tüm öğeleri kaldırarak çözebilirsiniz **ayarları** sayfasının **Proje Tasarımcısı**ve ardından gereken ayarları yeniden ekleme.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Bir proje .NET Framework'ün farklı bir sürüme yeniden hedeflenmiş ve başvuruları çözümlenmiyor  
 Bir proje farklı bir sürümüne yeniden hedefle varsa [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], başvurularınızı düzgün bazı durumlarda çözülemiyor olabilir. Açık tam derlemelere başvuruları genellikle bu soruna neden ancak çözümlenmiyor başvurularının kaldırılması ve sonra bunları projeye geri ekleyerek çözebilirsiniz. Alternatif olarak, başvuruları değiştirmek için proje dosyasını düzenleyebilirsiniz. İlk olarak, aşağıdaki biçimde başvuruları kaldırın:  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Ardından, bunları basit form ile değiştirin:  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
>  Projenizi kapatıp sonra ayrıca tüm başvuruları doğru çözümleyemiyorsa emin olmak için yeniden oluşturmalısınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET framework istemci profili](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)   
 [Belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)



