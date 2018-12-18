---
title: WPF MSBuild görev başvurusu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5266b5b6274eb9a39f6603598b90cd551f25caef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185477"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild Görev Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Windows Presentation Foundation (WPF) derleme işlemi derleme görevleri işaretlemesi ve işlem kaynaklarını derlemek için görevleri de dahil olmak üzere, ek bir kümesi Microsoft build engine (MSBuild) genişletir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Bir bütünleştirilmiş kod içine katıştırılmış olarak kaynak kaynak kümesini sınıflandırır. Bir kaynak yerelleştirilebilir değil ise, ana uygulama derlemesine eklenir; Aksi takdirde, bir uydu derlemeye eklenir.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 En az bir derleme oluşturur [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] projesinde sayfasına başvuruda o projede yerel olarak bildirilmiş bir tür. Oluşturulan derleme, derleme işlemi tamamlandıktan sonra veya derleme işlemi başarısız olursa kaldırılır.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Geçerli dizinin döndürür [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] çalışma zamanı.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Yerelleştirilemeyen dönüştürür [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] proje dosyaları için derlenmiş ikili biçimi.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 İkinci geçiş işaretlemesi derleme gerçekleştirir [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] başvuru türleri aynı projedeki dosyaları.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Yerelleştirme öznitelikleri ve yorumlar veya birden fazla birleştirir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] tüm derleme için tek bir dosya halinde ikili biçimi dosyaları.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Bir veya daha fazla kaynak katıştırır (.jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçimi ve diğer uzantı türleri) bir .resources dosyasına.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Denetler, güncelleştirir veya tüm yerelleştirmek için benzersiz tanımlayıcıları (Uıd'leri) kaldırır [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] kaynakta bulunan öğeleri [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyaları.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Ekler  **\<HostInBrowser / >** öğe uygulama bildiriminin (*projectname*. exe.manifest) olduğunda bir [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] Proje oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)



