---
title: RC görevi | Microsoft Docs
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
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04bd592f919ab3ced11b36dceba7ce4178927884
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259356"
---
# <a name="rc-task"></a>RC Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sarmalar Microsoft Windows Kaynak Derleyicisi aracı RC.exe'yi. **RC** görev imleçler, simgeler, bit eşlemler, iletişim kutuları ve yazı tipleri gibi kaynakları bir kaynak (.res) dosyasına derler. Daha fazla bilgi için "Kaynak derleyicisi" bakın [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda RCtask parametrelerini açıklar. Çoğu görev parametreleri ve parametrelerin birkaç kümeleri bir komut satırı seçeneğine karşılık gelir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|İsteğe bağlı **String []** parametresi.<br /><br /> Bir dizin dahil etme dosyaları için Aranan dizinleri listesine ekler.<br /><br /> Daha fazla bilgi için **/I** seçeneğini [RC kullanma (RC komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730) MSDN Web sitesinde.|  
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırı optionsor örnek listesini **"**_/option1 /option2 /option#_". Diğer tarafından temsil edilmez komut satırı seçeneklerini belirtmek için bu parametreyi kullanın **RC** görev parametresi.<br /><br /> Seçenekler, daha fazla bilgi için bkz. [RC kullanma (RC komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730) MSDN Web sitesinde.|  
|**Kültür**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaynaklarda kullanılan kültürü temsil eden bir yerel ayar Kimliğini belirtir.<br /><br /> Daha fazla bilgi için **/l** seçeneğini [RC kullanma (RC komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730) MSDN Web sitesinde.|  
|**IgnoreStandardIncludePath**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, kaynak derleyicisi, üst bilgi veya kaynak dosyalar için aradığında, INCLUDE ortam değişkeni iade etmesini engeller.<br /><br /> Daha fazla bilgi için **/x** seçeneğini [RC kullanma (RC komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730) MSDN Web sitesinde.|  
|**NullTerminateStrings**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, tüm dizeler dize tablosu boş sonlandırır.<br /><br /> Daha fazla bilgi için **/n** seçeneğini [RC kullanma (RC komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730) MSDN Web sitesinde.|  
|**PreprocessorDefinitions**|İsteğe bağlı **String []** parametresi.<br /><br /> Kaynak derleyicisi için bir veya daha çok önişlemci sembolleri tanımlayın. Makro sembolleri bir listesini belirtin.<br /><br /> Daha fazla bilgi için **/d** seçeneğini [RC kullanma (RC komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730) MSDN Web sitesinde. Ayrıca bkz: **UndefinePreprocessorDefinitions** bu tablodaki.|  
|**ResourceOutputFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaynak dosyasının adını belirtir. Bir kaynak dosya adı belirtin.<br /><br /> Daha fazla bilgi için **/fo** seçeneğini [RC kullanma (RC komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730) MSDN Web sitesinde.|  
|**ShowProgress**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, derleyici, ilerleme üzerinde rapor iletilerini görüntüler.<br /><br /> Daha fazla bilgi için **/v** seçeneğini [RC kullanma (RC komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730) MSDN Web sitesinde.|  
|**Kaynak**|Gerekli `ITaskItem[]` parametresi.<br /><br /> Tüketilen ve görevler tarafından yayılan MSBuild kaynak dosya öğeleri bir dizisi tanımlanmaktadır.|  
|**SuppressStartupBanner**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.<br /><br /> Daha fazla bilgi için **/?** komut satırı seçeneğini ve ardından bakın **/nologo** seçeneği.|  
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleme günlüğü dizini belirtir.|  
|**UndefinePreprocessorDefinitions**|Önişlemci simge tanımlarını Kaldır.<br /><br /> Daha fazla bilgi için **/u** seçeneğini [RC kullanma (RC komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730) MSDN Web sitesinde. Ayrıca bkz: **PreprocessorDefinitions** bu tablodaki.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



