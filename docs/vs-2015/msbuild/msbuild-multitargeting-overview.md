---
title: MSBuild çoklu sürüm desteğine genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5d8d5aae19bee458a6d0750cb0d8cd4efa8c4d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243834"
---
# <a name="msbuild-multitargeting-overview"></a>MSBuild Çoklu Sürüm Desteğine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild kullanarak, .NET Framework'ün çeşitli sürümlerinden herhangi birini ve birkaç sistemi platformları herhangi birini çalıştırmak için bir uygulamayı derleyebilirsiniz. Örneğin, bir 32 bit platformda .NET Framework 2.0 üzerinde çalışacak bir uygulama derlemek ve bir 64-bit platformda .NET Framework 4.5 üzerinde çalıştırılacak aynı uygulamayı derleyin.  
  
> [!IMPORTANT]
>  Adı "çoklu hedefleme rağmen", bir proje aynı anda yalnızca bir çerçeve ve tek bir platform hedefleyebilirsiniz.  
  
 MSBuild hedefleme özelliklerinden bazıları şunlardır:  
  
-   .NET Framework, örneğin, sürüm 2.0, 3.5 ve 4'ün önceki bir sürümünü hedefleyen bir uygulama geliştirebilirsiniz.  
  
-   Örneğin, Silverlight Framework .NET Framework dışında bir çerçeve hedefleyebilirsiniz.  
  
-   Platformlarını hedefleyebilen bir *framework profili*, hangi hedef framework'ün önceden tanımlanmış bir alt kümesidir.  
  
-   Geçerli .NET Framework sürümü için bir hizmet paketi yayımlandığında bunu hedefleyebilirsiniz.  
  
-   MSBuild'ı hedefleyen bir uygulama yalnızca hedef framework ve platform kullanılabilir işlevleri kullanır garanti eder.  
  
## <a name="target-framework-and-platform"></a>Hedef Framework ve Platform  
 A *hedef Framework'ü* bir proje üzerinde çalıştırmak için yerleşik olan .NET Framework sürümü ve *hedef platform* projeyi çalıştırmak için yerleşik bir sistem platformudur.  Örneğin, 802 x 86 işlemci ailesini (x86) ile uyumlu bir 32 bit platformda çalıştırmak için bir .NET Framework 2.0 uygulama hedeflemek isteyebilirsiniz. Hedef Çerçeve ve hedef platform bileşimi olarak da bilinen *hedef bağlam*. Daha fazla bilgi için [hedef çerçevesi ve hedef platformu](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## <a name="toolset-toolsversion"></a>Araç Takımı (ToolsVersion)  
 Bir araç takımı, araçları, görevleri ve uygulama oluşturmak için kullanılan hedefleri araya toplar. Bir araç takımı csc.exe ve vbc.exe, ortak hedefler dosyası (microsoft.common.targets) gibi derleyicileri içerir ve ortak görevleri (microsoft.common.tasks) dosya. 4.5 araç takımı, hedef .NET Framework sürümleri 2.0, 3.0, 3.5, 4 ve 4.5 için kullanılabilir. Ancak, 2.0 araç takımını ve .NET Framework sürüm 2.0 hedeflemek için yalnızca kullanılabilir. Daha fazla bilgi için [araç takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## <a name="reference-assemblies"></a>Başvuru bütünleştirilmiş kodları  
 Araç kümesinde belirtilen başvuru bütünleştirilmiş kodları tasarım ve uygulama oluşturmanıza yardımcı olur. Bu başvuru bütünleştirilmiş kodları yalnızca belirli hedef derleme etkinleştirmek, ancak hedef ile uyumlu olan bu bileşenler ve özellikler Visual Studio IDE'de de kısıtlama. Daha fazla bilgi için [tasarım zamanında derlemeleri çözme](../msbuild/resolving-assemblies-at-design-time.md)  
  
## <a name="configuring-targets-and-tasks"></a>Hedefleri ve Görevleri Yapılandırma  
 MSBuild hedefleri ve görevleri çalıştırmak için yapılandırabilirsiniz giden işlem MSBuild ile böylece üzerinde çalışan fiyattan önemli ölçüde farklı Bağlamlar hedefleyebilirsiniz.  Örneğin, geliştirme bilgisayarında .NET Framework 4.5 ile bir 64-bit platformlarda çalışırken bir 32-bit, .NET Framework 2.0 uygulama hedefleyebilirsiniz. Daha fazla bilgi için [yapılandırma hedefleri ve görevleri](../msbuild/configuring-targets-and-tasks.md).  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Hedef bağlam parçası olmayan bir derleme başvurusu çalışırsanız hatalarla karşılaşabilirsiniz. Bu hataları ve bunlarla ilgili yapılması gerekenler hakkında daha fazla bilgi için bkz. [.NET Framework hedefleme hataları giderme](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).



