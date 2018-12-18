---
title: .NET Framework hedefleme hatalarının sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: troubleshooting
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bd1d899d3b3a84af2b07602b959dd031874e972c
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155457"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>.NET Framework hedefleme hatalarının sorunlarını giderme
Bu konuda başvurusu nedeniyle oluşabilecek MSBuild hataları açıklanır sorunlar ve bu hataların nasıl çözebilirsiniz.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Bir proje ya da farklı bir .NET Framework sürümünü hedefleyen derlemeye başvuru  
 Projelere veya farklı sürümlerini hedefleyen derlemelere başvuran uygulamalar oluşturabilirsiniz [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Örneğin, için istemci Profili'ni hedefleyen bir uygulama oluşturabilirsiniz [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] ancak .NET Framework 2. 0'ı hedefleyen bir derlemeye başvurur. Ancak, önceki bir sürümünü hedefleyen bir proje oluşturursanız, [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], projeye bir proje ya da için istemci Profili'ni hedefleyen derlemeye başvuru ayarlanamıyor [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] veya [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] kendisi. Hatayı gidermek için uygulamanızın bir profil veya projelere veya derlemelere göre uygulamanızı başvuran hedeflenen profiliyle uyumlu olan profilleri hedefler emin olun.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Bir proje .NET Framework'ün farklı bir sürüme yeniden hedeflenen  
 Hedef sürümü değiştirirseniz [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] uygulamanız için Visual Studio bazı başvuruları değiştirir, ancak bazı başvuruları el ile güncelleştirmeniz gerekebilir. Hedef uygulama değiştirirseniz, örneğin, bir durum önceden bahsedilmiş hatalarla oluşabilir [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)] ve uygulama kaynaklarına veya istemci profilini kullanan ayarları olduğunu [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)].  
  
 Uygulama ayarlarını geçici olarak çözmek için açık **Çözüm Gezgini**, seçin **tüm dosyaları göster**ve ardından düzenleme *app.config* dosyasını Visual Studio XML düzenleyicisinde. Sürümü .NET Framework'ün uygun sürümünü eşleştirmek için ayarları değiştirin. Örneğin, 4.0.0.0 2.0.0.0 için sürüm ayarını değiştirebilirsiniz. Benzer şekilde, uygulamanın her zaman kaynakları eklemiştir açın **Çözüm Gezgini**, seçin **tüm dosyaları göster** sırasıyla, düğme **Projem** (Visual Basic) veya **Özellikleri** (C#) ve ardından düzenleme *Resources.resx* dosyasını Visual Studio XML düzenleyicisinde. Sürüm ayarı 4.0.0.0 2.0.0.0 için değiştirin.  
  
 Uygulamanızın simgeleri veya bit eşlemleri gibi kaynaklara veya veri bağlantı dizeleri gibi ayarları varsa, ayrıca hata üzerinde tüm öğeleri kaldırarak çözebilirsiniz **ayarları** sayfasının **Proje Tasarımcısı**ve ardından gereken ayarları yeniden ekleme.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Bir proje .NET Framework'ün farklı bir sürüme yeniden hedeflenmiş ve başvuruları çözümlenmiyor  
 Bir proje farklı bir sürümüne yeniden hedefle varsa [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], başvurularınızı düzgün bazı durumlarda çözülemiyor olabilir. Açık tam derlemelere başvuruları genellikle bu soruna neden ancak çözümlenmiyor başvurularının kaldırılması ve sonra bunları projeye geri ekleyerek çözebilirsiniz. Alternatif olarak, başvuruları değiştirmek için proje dosyasını düzenleyebilirsiniz. İlk olarak, aşağıdaki biçimde başvuruları kaldırın:  
  
```xml  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Ardından, bunları basit form ile değiştirin:  
  
```xml  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
>  Projenizi kapatıp sonra ayrıca tüm başvuruları doğru çözümleyemiyorsa emin olmak için yeniden oluşturmalısınız.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET framework istemci profili](/dotnet/framework/deployment/client-profile)   
 [Belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Çoklu sürüm desteği](../msbuild/msbuild-multitargeting-overview.md)