---
title: XDCMake görevi | Microsoft Docs
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
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: caf3803edff01e6ffe650f18aaccef99fc50728f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204886"
---
# <a name="xdcmake-task"></a>XDCMake Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML belge açıklaması (.xdc) dosyaları bir .xml dosyasına birleştirir XML belgelendirme Aracı (xdcmake.exe'yi) sarmalar.  
  
 .Xdc dosyasını kullanarak Visual C++ kaynak kod ve derleme belge açıklamaları sağlama oluşturulduğunda [/doc](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63) derleyici seçeneği. Daha fazla bilgi için [XDCMake başvurusu](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [XML belgesi oluşturma aracı özellik sayfaları](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)ve komut satırı Yardımı seçeneği (**/?**) xdcmake.exe'yi için.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, aracı xdcmake.exe'yi birkaç komut satırı seçeneklerini destekler. Ek seçenekler, belirttiğiniz zaman desteklenir **/eski** komut satırı seçeneği.  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır **XDCMake** görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|İsteğe bağlı **String []** parametresi.<br /><br /> Birleştirmek için bir veya daha fazla ek .xdc dosyalarının belirtir.<br /><br /> Daha fazla bilgi için **ek belge dosyaları** açıklamasında [XML belgesi oluşturma aracı özellik sayfaları](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0). Ayrıca bkz: **/eski** ve **/Fs** xdcmake.exe'yi için komut satırı seçenekleri.|  
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırında belirtilen seçeneklerin bir listesi. Örneğin, "*/option1 /option2 /option#*". Diğer tarafından temsil edilmez seçeneklerini belirtmek için bu parametreyi kullanın **XDCMake** görev parametresi.<br /><br /> Daha fazla bilgi için [XDCMake başvurusu](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [XML belgesi oluşturma aracı özellik sayfaları](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)ve komut satırı Yardımı (**/?**) xdcmake.exe'yi için.|  
|**DocumentLibraryDependencies**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true` ve geçerli proje çözümde bir statik kitaplık (.lib) proje üzerinde bağımlılık vardır, bu kitaplık projesi için .xdc dosyalarının geçerli proje için .xml dosyasını çıkış dahil.<br /><br /> Daha fazla bilgi için **belge kitaplığı bağımlılıkları** açıklamasında [XML belgesi oluşturma aracı özellik sayfaları](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0).|  
|**OutputFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Varsayılan çıkış dosyası adını geçersiz kılar. Varsayılan adı, işlenen ilk .xdc dosyasının adından türetilir.<br /><br /> Daha fazla bilgi için **/out:** `filename` seçeneğini [XDCMake başvurusu](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac). Ayrıca bkz: **/eski** ve **/Fo** xdcmake.exe'yi için komut satırı seçenekleri.|  
|**projectName**|İsteğe bağlı **dize** parametresi.<br /><br /> Geçerli projenin adı.|  
|**SlashOld**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, ek xdcmake.exe'yi seçeneklerini etkinleştirir.<br /><br /> Daha fazla bilgi için **/eski** xdcmake.exe'yi için komut satırı seçeneği.|  
|**Kaynakları**|Gerekli `ITaskItem[]` parametresi.<br /><br /> Tüketilen ve görevler tarafından yayılan MSBuild kaynak dosya öğeleri bir dizisi tanımlanmaktadır.|  
|**SuppressStartupBanner**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.<br /><br /> Daha fazla bilgi için **/nologo** seçeneğini [XDCMake başvurusu](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac).|  
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlüğü dizini belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



