---
title: MSBuild görevleri | Microsoft Docs
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
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dff7c0ce45c71340f3b931e32843adb6a90ea075
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176713"
---
# <a name="msbuild-tasks"></a>MSBuild Görevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir yapı platformunu herhangi bir sayıda eylemleri derleme işlemi sırasında yürütme yeteneği gerekir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] kullanan *görevleri* bu eylemleri gerçekleştirmek için. Bir görev tarafından kullanılan yürütülebilir kod birimidir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] CAN atomik yapı işlemleri gerçekleştirmek için.  
  
## <a name="task-logic"></a>Görev mantığı  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] XML proje dosyası biçimi, proje dosyasının bunu kendi, görev mantıksal işlemleri uygulanan derleme tam olarak yürütülemiyor.  
  
 Bir görevin yürütülme mantığı uygulayan bir .NET sınıfı uygulanır <xref:Microsoft.Build.Framework.ITask> tanımlanan arabirimi <xref:Microsoft.Build.Framework> ad alanı.  
  
 Görev sınıfı proje dosyasında görev ayrıca giriş ve çıkış parametrelerini tanımlar. Görev sınıfı tarafından kullanıma sunulan tüm genel ayarlanabilir statik olmayan soyut olmayan özellikler üzerinde aynı ada sahip karşılık gelen bir öznitelik yerleştirerek proje dosyasında erişilebilir [görev](../msbuild/task-element-msbuild.md) öğesi.  
  
 Yazma uygulayan yönetilen bir sınıf tarafından kendi görevinizi yazabilirsiniz <xref:Microsoft.Build.Framework.ITask> arabirimi. Daha fazla bilgi için [görev yazma](../msbuild/task-writing.md).  
  
## <a name="executing-a-task-from-a-project-file"></a>Proje dosyasından bir görevi yürütülüyor  
 Proje dosyanızda bir görev yürütülmeden önce görev adı ile görevi uygulayan derlemedeki tür ilk eşlenmelidir [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi. Böylece [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyanızda bulduğunda, görevin yürütülme mantığı için aranacağı bildirin.  
  
 Bir görev olarak çalıştırmak için bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyası, bir alt öğesi olarak görev adı ile bir öğe oluşturmaya bir `Target` öğesi. Görev parametreleri kabul ediyorsa, bu öğenin öznitelikleri geçirilir.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] öğe listeleri ve özellikleri parametre olarak kullanılabilir. Örneğin, aşağıdaki çağrıları kod `MakeDir` görev ve değerini ayarlar `Directories` özelliği `MakeDir` nesne değerine eşit `BuildDir` özelliği, önceki örnekte bildirilen.  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Görevler, ayrıca öğeleri ya da daha sonra kullanmak için özellikler depolanabilir proje dosyasına bilgi döndürebilir. Örneğin, aşağıdaki çağrıları kod `Copy` bilgileri depolar ve görev `CopiedFiles` çıkış özelliğinde `SuccessfullyCopiedFiles` öğe listesi.  
  
```  
<Target Name="CopyFiles">  
    <Copy  
        SourceFiles="@(MySourceFiles)"  
        DestinationFolder="@(MyDestFolder)">  
        <Output  
            TaskParameter="CopiedFiles"  
            ItemName="SuccessfullyCopiedFiles"/>  
     </Copy>  
</Target>  
```  
  
## <a name="included-tasks"></a>Dahil edilen görevler  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] gibi birçok görevi ile birlikte gelen [kopyalama](../msbuild/copy-task.md), dosyaları kopyalayan [MakeDir](../msbuild/makedir-task.md), dizinler oluşturan ve [Csc](../msbuild/csc-task.md), hangi derler [!INCLUDE[csprcs](../includes/csprcs-md.md)] kaynak kodu dosyaları. Kullanılabilir görevlerin ve kullanım bilgilerinin tam listesi için bkz: [görev başvurusu](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Geçersiz kılınan görevleri  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Görevler çeşitli konumlarda arar. İlk konum uzantılı dosyaları alıyor. .NET Framework dizinlerinde depolanan OverrideTasks. Bu dosyalar, görevler proje dosyasına görevler de dahil olmak üzere aynı ada sahip herhangi bir görevi geçersiz kılar. İkinci konum uzantılı dosyaları alıyor. .NET Framework dizinlerde görevler. Görev bu konumlardan birini bulunamazsa, görev proje dosyasında kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [MSBuild](msbuild.md)   
 [Görev yazma](../msbuild/task-writing.md)   
 [Satır İçi Görevleri](../msbuild/msbuild-inline-tasks.md)


