---
title: MSBuild görevleri belirli Visual C++ | Microsoft Docs
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
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1da9bdb5c181c9fd935987d629f08af1505f0501
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246161"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Visual C++'ye Özgü MSBuild Görevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Görevler, derleme işlemi sırasında çalışan kodu sağlar. Visual C++ yüklü olduğunda, aşağıdaki görevleri ile birlikte yüklenen listelenenlere kullanılabilir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Daha fazla bilgi için [MSBuild (Visual C++) genel bakış](http://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca).  
  
 Her görev için parametrelerin yanı sıra, her görev, ayrıca aşağıdaki parametrelere sahiptir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Condition`|İsteğe bağlı `String` parametresi.<br /><br /> A `Boolean` ifade eden [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] altyapısı bu görevi yürüten olup olmadığını belirlemek için kullanır. Tarafından desteklenen koşullar hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], bkz: [koşullar](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|İsteğe bağlı parametre. Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, sonraki görevlerinde [hedef](../msbuild/target-element-msbuild.md) öğesi ile derleme devam yürütülecek ve görevin tüm hataları uyarı olarak kabul edilir<br />-   **ErrorAndContinue**. Bir görev başarısız olduğunda, sonraki görevlerinde `Target` öğesi ile derleme devam yürütmek ve tüm hataları görev hata olarak kabul edilir.<br />-   **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, listesindeki kalan görevlere`Target` olmayan öğe ve derleme yürütülür ve tüm `Target` öğesi ve yapı başarısız olduğu değerlendirilir.<br /><br /> .NET Framework 4.5 yalnızca desteklenen önce sürümleri `true` ve `false` değerleri.<br /><br /> Daha fazla bilgi için [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[BscMake Görevi](../msbuild/bscmake-task.md)|Microsoft gözatma bilgisi bakım Yardımcısı Aracı (bscmake.exe) sarmalar.|  
|[CL Görevi](../msbuild/cl-task.md)|Visual C++ derleyicisi Aracı'nı (cl.exe) sarmalar.|  
|[CPPClean Görevi](../msbuild/cppclean-task.md)|MSBuild Visual C++ proje derlenirken oluşturan geçici dosyaları siler.|  
|[LIB Görevi](../msbuild/lib-task.md)|Microsoft 32-Bit Kitaplık Yöneticisi Aracı (lib.exe) sarmalar.|  
|[Link Görevi](../msbuild/link-task.md)|Visual C++ bağlayıcı Aracı'nı (link.exe) sarmalar.|  
|[MIDL Görevi](../msbuild/midl-task.md)|Microsoft arabirim tanımı dili (MIDL) derleyici Aracı'nı (midl.exe'yi) sarmalar.|  
|[MT Görevi](../msbuild/mt-task.md)|Microsoft bildirim Aracı (mt.exe) sarmalar.|  
|[RC Görevi](../msbuild/rc-task.md)|Microsoft Windows Kaynak Derleyicisi Aracı (rc.exe) sarmalar.|  
|[SetEnv Görevi](../msbuild/setenv-task.md)|Belirtilen ortam değişkeninin değerini siler veya ayarlar.|  
|[VCMessage Görevi](../msbuild/vcmessage-task.md)|Derleme sırasında iletileri ve hata iletilerini uyarı günlükleri.|  
|[XDCMake Görevi](../msbuild/xdcmake-task.md)|XML belge açıklaması (.xdc) dosyaları bir .xml dosyasına birleştirir XML belgelendirme Aracı (xdcmake.exe'yi) sarmalar.|  
|[XSD Görevi](../msbuild/xsd-task.md)|Bir kaynaktan şema ya da sınıf dosyaları oluşturur XML şema tanımı Aracı (XSD.exe'nin) sarmalar.|  
|[MSBuild Başvurusu](../msbuild/msbuild-reference.md)|MSBuild sistemi öğeleri açıklar.|  
|[Görevler](../msbuild/msbuild-tasks.md)|Bir yapı oluşturmak için birleştirilebilir kod birimleri olan görevleri açıklar.|  
|[Görev Yazma](../msbuild/task-writing.md)|Bir görevin nasıl oluşturulacağını açıklar.|



