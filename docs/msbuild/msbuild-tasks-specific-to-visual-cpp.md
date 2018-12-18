---
title: MSBuild görevleri belirli Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 06/27/2018
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 2caacec2412ea0c188d9b987ae8a6e52a89fbe9b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906760"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Visual C++'ye özgü MSBuild görevleri
Görevler, derleme işlemi sırasında çalışan kodu sağlar. Visual C++ yüklü olduğunda, aşağıdaki görevleri ile birlikte yüklenen listelenenlere kullanılabilir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Daha fazla bilgi için [MSBuild (Visual C++) genel bakış](/cpp/build/msbuild-visual-cpp-overview).  

 Her görev için parametrelerin yanı sıra, her görev, ayrıca aşağıdaki parametrelere sahiptir.  


| Parametre | Açıklama |
|-------------------| - |
| `Condition` | İsteğe bağlı `String` parametresi.<br /><br /> A `Boolean` ifade eden [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] altyapısı bu görevi yürüten olup olmadığını belirlemek için kullanır. Tarafından desteklenen koşullar hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], bkz: [koşullar](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | İsteğe bağlı parametre. Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, sonraki görevlerinde [hedef](../msbuild/target-element-msbuild.md) öğesi ile derleme devam yürütülecek ve görevin tüm hataları uyarı olarak kabul edilir<br />-   **ErrorAndContinue**. Bir görev başarısız olduğunda, sonraki görevlerinde `Target` öğesi ile derleme devam yürütmek ve tüm hataları görev hata olarak kabul edilir.<br />-   **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, listesindeki kalan görevlere`Target` olmayan öğe ve derleme yürütülür ve tüm `Target` öğesi ve yapı başarısız olduğu değerlendirilir.<br /><br /> .NET Framework 4.5 yalnızca desteklenen önce sürümleri `true` ve `false` değerleri.<br /><br /> Daha fazla bilgi için [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>İlgili konular  

|Başlık|Açıklama|  
|-----------|-----------------|  
|[BscMake görevi](../msbuild/bscmake-task.md)|Microsoft gözatma bilgisi bakım Yardımcısı aracı sarmalar (*bscmake.exe'yi*).|  
|[CL görevi](../msbuild/cl-task.md)|Visual C++ Derleyici aracı sarmalar (*cl.exe*).|  
|[CPPClean görevi](../msbuild/cppclean-task.md)|MSBuild Visual C++ proje derlenirken oluşturan geçici dosyaları siler.|  
|[LIB görevi](../msbuild/lib-task.md)|Microsoft 32-Bit Kitaplık Yöneticisi aracını sarmalar (*lib.exe*).|  
|[Bağlantı görevi](../msbuild/link-task.md)|Visual C++ bağlayıcı aracı sarmalar (*link.exe*).|  
|[MIDL görevi](../msbuild/midl-task.md)|Microsoft arabirim tanımı dili (MIDL) derleyici aracı sarmalar (*midl.exe'yi*).|  
|[MT görevi](../msbuild/mt-task.md)|Microsoft bildirim aracı sarmalar (*mt.exe*).|  
|[RC görevi](../msbuild/rc-task.md)|Microsoft Windows Kaynak Derleyicisi aracı sarmalar (*rc.exe*).|  
|[SetEnv görevi](../msbuild/setenv-task.md)|Belirtilen ortam değişkeninin değerini siler veya ayarlar.|  
|[VCMessage görevi](../msbuild/vcmessage-task.md)|Derleme sırasında iletileri ve hata iletilerini uyarı günlükleri. (Genişletilebilir değildir. Yalnızca iç kullanım.)|  
|[XDCMake görevi](../msbuild/xdcmake-task.md)|XML belgelendirme aracı sarmalar (*xdcmake.exe'yi*), XML belgesi açıklaması birleştirir (*.xdc*) dosyalarınızı bir *.xml* dosya.|  
|[XSD görevi](../msbuild/xsd-task.md)|XML şema tanımı aracı sarmalar (*XSD.exe'nin*), bir kaynaktan şema ya da sınıf dosyaları oluşturur. *Aşağıdaki nota bakın.*|  
|[MSBuild başvurusu](../msbuild/msbuild-reference.md)|MSBuild sistemi öğeleri açıklar.|  
|[Görevler](../msbuild/msbuild-tasks.md)|Bir yapı oluşturmak için birleştirilebilir kod birimleri olan görevleri açıklar.|  
|[Görev yazma](../msbuild/task-writing.md)|Bir görevin nasıl oluşturulacağını açıklar.|

> [!NOTE]
> Visual Studio 2017'de C++ proje desteği *XSD.exe'nin* kullanım dışı bırakılmıştır. Kullanmaya devam edebilirsiniz **Microsoft.VisualC.CppCodeProvider** el ile ekleyerek API'leri *CppCodeProvider.dll* GAC'ye.