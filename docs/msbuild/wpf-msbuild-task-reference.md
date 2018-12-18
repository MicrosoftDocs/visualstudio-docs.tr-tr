---
title: WPF MSBuild görev başvurusu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53f723644744001e39967186d0eeec74bf7d3bd7
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153806"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild görev başvurusu
Windows Presentation Foundation (WPF) derleme işlemi derleme görevleri işaretlemesi ve işlem kaynaklarını derlemek için görevleri de dahil olmak üzere, ek bir kümesi Microsoft build engine (MSBuild) genişletir.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Bir bütünleştirilmiş kod içine katıştırılmış olarak kaynak kaynak kümesini sınıflandırır. Bir kaynak yerelleştirilebilir değil ise, ana uygulama derlemesine eklenir; Aksi takdirde, bir uydu derlemeye eklenir.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 En az bir derleme oluşturur [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] projesinde sayfasına başvuruda o projede yerel olarak bildirilmiş bir tür. Oluşturulan derleme, derleme işlemi tamamlandıktan sonra veya derleme işlemi başarısız olursa kaldırılır.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Geçerli dizinin döndürür [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] çalışma zamanı.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Yerelleştirilemeyen dönüştürür [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] proje dosyaları için derlenmiş ikili biçimi.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 İkinci geçiş işaretlemesi derleme gerçekleştirir [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] başvuru türleri aynı projedeki dosyaları.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Yerelleştirme öznitelikleri ve yorumlar veya birden fazla birleştirir [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] tüm derleme için tek bir dosya halinde ikili biçimi dosyaları.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Bir veya daha fazla kaynak katıştırır (*.jpg*, *.ico*, *.bmp*, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ikili biçimi ve diğer uzantı türleri) içine bir *.resources*dosya.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Denetler, güncelleştirir veya tüm yerelleştirmek için benzersiz tanımlayıcıları (Uıd'leri) kaldırır [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] kaynakta bulunan öğeleri [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyaları.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Ekler  **\<HostInBrowser / >** öğe uygulama bildiriminin (*\<projectname >. exe.manifest*) olduğunda bir [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] Proje oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [MSBuild](../msbuild/msbuild.md)