---
title: BscMake görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b93247fcce7502ce96a075dc5d297cd9c87fe640
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153195"
---
# <a name="bscmake-task"></a>BscMake görevi
> [!IMPORTANT]
>  BscMake artık Visual Studio IDE tarafından kullanılır. Visual Studio 2008'den itibaren gözatma bilgilerini otomatik olarak depolanan bir *.sdf* dosyası *çözüm* klasör.  
  
 Microsoft gözatma bilgisi bakım Yardımcısı aracı sarmalar (*bscmake.exe'yi*).  *Bscmake.exe'yi* aracı gözatma bilgisi dosyası oluşturur (*.bsc*) öğesinden kaynak tarayıcı dosyaları (*.sbr*) derleme sırasında oluşturulur. Kullanım **Nesne Tarayıcısı** görüntülemek için bir *.bsc* dosya. Daha fazla bilgi için [BSCMAKE başvurusu](/cpp/build/reference/bscmake-reference).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır **BscMake** görev. Çoğu görev parametreleri bir komut satırı seçeneğine karşılık gelir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırında belirtilen seçeneklerin bir listesi. Örneğin, /\<Seçenek1 > /\<Seçenek2 > /\<seçeneği #>. Diğer tarafından temsil edilmez seçeneklerini belirtmek için bu parametreyi kullanın **BscMake** görev parametresi.<br /><br /> Daha fazla bilgi için bkz. seçenekleri [BSCMAKE seçenekleri](/cpp/build/reference/bscmake-options).|  
|**OutputFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Varsayılan çıkış dosyası adını geçersiz kılan bir dosya adını belirtir.<br /><br /> Daha fazla bilgi için **/o** seçeneğini [BSCMAKE seçenekleri](/cpp/build/reference/bscmake-options).|  
|**PreserveSBR**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, artımlı olmayan bir derleme zorlar. Tam ve artımlı olmayan bir derleme olup olmamasına bakılmaksızın gerçekleşir bir *.bsc* dosyanın var olduğundan ve engeller *.sbr* kesilmesini dosyaları.<br /><br /> Daha fazla bilgi için **/n** seçeneğini [BSCMAKE seçenekleri](/cpp/build/reference/bscmake-options).|  
|**Kaynakları**|İsteğe bağlı **Itaskıtem []** parametresi.<br /><br /> Tüketilen ve görevler tarafından yayılan MSBuild kaynak dosya öğeleri bir dizisi tanımlanmaktadır.|  
|**SuppressStartupBanner**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.<br /><br /> Daha fazla bilgi için **/nologo** seçeneğini [BSCMAKE seçenekleri](/cpp/build/reference/bscmake-options).|  
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlüğü dizini belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)