---
title: LIB görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), LIB task
- LIB task (MSBuild (Visual C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df6011cb1c706069135a133dd37a34e54203b22b
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079630"
---
# <a name="lib-task"></a>LIB görevi
Microsoft 32-Bit Kitaplık Yöneticisi aracını sarmalar *lib.exe*. Kitaplık Yöneticisi'ni oluşturur ve ortak nesne dosyası biçimi (COFF) nesne dosyası kitaplığı yönetir. Kitaplık Yöneticisi'ni de dışarı aktarma dosyaları oluşturabilir ve kitaplıkları dışarı başvuru tanımlarını içeri aktarma. Daha fazla bilgi için [LIB başvurusu](/cpp/build/reference/lib-reference) ve [çalıştıran LIB](/cpp/build/reference/running-lib).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır **LIB** görev. Çoğu görev parametreleri bir komut satırı seçeneğine karşılık gelir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**AdditionalDependencies**|İsteğe bağlı **String []** parametresi.<br /><br /> Komut satırına eklenecek ek öğeleri belirtir.|  
|**AdditionalLibraryDirectories**|İsteğe bağlı **String []** parametresi.<br /><br /> Kullanıcının ortam kitaplık yolunu geçersiz kılar. Bir dizin adı belirtin.<br /><br /> Daha fazla bilgi için [/Libpath (ek Libpath)](/cpp/build/reference/libpath-additional-libpath).|  
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Listesini *lib.exe* seçenekleri komut satırında belirtilen. Örneğin, /\<Seçenek1 > /\<Seçenek2 > /\<seçeneği #>. Belirtmek için bu parametreyi kullanın *lib.exe* diğer tarafından temsil edilmez seçenekleri **LIB** görev parametresi.<br /><br /> Daha fazla bilgi için [çalıştıran LIB](/cpp/build/reference/running-lib).|  
|**DisplayLibrary**|İsteğe bağlı **dize** parametresi.<br /><br /> Çıkış Kitaplığı hakkında bilgi görüntüler. Bilgiler bir dosyaya yeniden yönlendirmek için bir dosya adı belirtin. "Onayla" ya da nothing bilgileri konsola yeniden yönlendirmek için belirtin.<br /><br /> Bu parametre için karşılık gelen **/LIST** seçeneği *lib.exe*.|  
|**ErrorReporting**|İsteğe bağlı **dize** parametresi.<br /><br /> İç hata bilgilerini Microsoft'a göndermek nasıl belirtir *lib.exe* çalışma zamanında başarısız olur.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.<br /><br /> -   **NoErrorReport** -   **/errorreport: yok**<br />-   **PromptImmediately** - **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** - **okunmalı**<br /><br /> Daha fazla bilgi için **/errorreport** komut satırı seçeneği [çalıştıran LIB](/cpp/build/reference/running-lib).|  
|**ExportNamedFunctions**|İsteğe bağlı **String []** parametresi.<br /><br /> Dışarı aktarmak için bir veya daha fazla işlevi belirtir.<br /><br /> Bu parametre için karşılık gelen **/dışarı aktarma:** seçeneği *lib.exe*.|  
|**ForceSymbolReferences**|İsteğe bağlı **dize** parametresi.<br /><br /> Zorlar *lib.exe* belirtilen sembole bir başvuru eklenecek.<br /><br /> Bu parametre için karşılık gelen **/INCLUDE:** seçeneği *lib.exe*.|  
|**IgnoreAllDefaultLibraries**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tüm varsayılan kitaplıkları kitaplıklarına listeden kaldırır, *lib.exe* dış başvurular çözümlediğinde arar.<br /><br /> Bu parametre için parametresiz biçiminin karşılık gelen **/nodefaultlıb** seçeneği *lib.exe*.|  
|**IgnoreSpecificDefaultLibraries**|İsteğe bağlı **String []** parametresi.<br /><br /> Belirtilen kitaplıkları kitaplıklarına listeden kaldırır, *lib.exe* dış başvurular çözümlediğinde arar.<br /><br /> Bu parametre için karşılık gelen **/nodefaultlıb** seçeneği *lib.exe* almayan bir `library` bağımsız değişken.|  
|**LinkLibraryDependencies**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, proje bağımlılıklarının kitaplık çıkışları içinde otomatik olarak bağlandığını belirtir.|  
|**LinkTimeCodeGeneration**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, bağlama sırasında kod oluşturmayı belirtir.<br /><br /> Bu parametre için karşılık gelen **/LCTG** seçeneği *lib.exe*.|  
|**MinimumRequiredVersion**|İsteğe bağlı **dize** parametresi.<br /><br /> Alt sistemin gerekli en düşük sürümü belirtir. 0 ila 65.535 aralığındaki ondalık sayılar virgülle ayrılmış bir listesini belirtin.|  
|**ModuleDefinitionFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Modül tanım dosyasının adını belirtir (*.def*).<br /><br /> Bu parametre için karşılık gelen **/def** seçeneği *lib.exe* almayan bir `filename` bağımsız değişken.|  
|**Ad**|İsteğe bağlı **dize** parametresi.<br /><br /> İçeri aktarma kitaplığı oluşturulduğunda, içeri aktarma kitaplığını oluşturulmakta olan DLL'in adını belirtir.<br /><br /> Bu parametre için karşılık gelen **/NAME** seçeneği *lib.exe* almayan bir `filename` bağımsız değişken.|  
|**OutputFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Varsayılan adını ve program konumunu geçersiz kılar, *lib.exe* oluşturur.<br /><br /> Bu parametre için karşılık gelen **/OUT** seçeneği *lib.exe* almayan bir `filename` bağımsız değişken.|  
|**RemoveObjects**|İsteğe bağlı **String []** parametresi.<br /><br /> Belirtilen nesneyi çıkış kitaplığında atlar. *Lib.exe* tüm nesneleri (elinizin altında nesne dosyalarında veya kitaplıklarındaki) birleştirerek ve ardından bu seçeneği tarafından belirtilen nesneleri silerek bir çıkış kitaplığı oluşturur.<br /><br /> Bu parametre için karşılık gelen **/REMOVE** seçeneği *lib.exe* almayan bir `membername` bağımsız değişken.|  
|**Kaynakları**|Gerekli `ITaskItem[]` parametresi.<br /><br /> Kaynak dosyaları boşluklarla ayrılmış bir listesini belirtir.|  
|**Alt sistem**|İsteğe bağlı **dize** parametresi.<br /><br /> Yürütülebilir dosya için ortamı belirtir. Alt sistem seçimi giriş noktası sembolünü ya da giriş noktası işlevini etkiler.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.<br /><br /> -   **Konsol** -   **/Subsystem: Console**<br />-   **Windows** - **/SUBSYSTEM:WINDOWS**<br />-   **Yerel** - **natıve**<br />-   **EFI uygulaması** - **/SUBSYSTEM:EFI_APPLICATION**<br />-   **EFI Önyükleme servisi sürücüsü** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**<br />-   **EFI çalışma zamanı** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **Wındowsce** - **/SUBSYSTEM:WINDOWSCE**<br />-   **POSIX** - **/SUBSYSTEM:POSIX**<br /><br /> Daha fazla bilgi için [/Subsystem (alt belirtin)](/cpp/build/reference/subsystem-specify-subsystem).|  
|**SuppressStartupBanner**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.<br /><br /> Daha fazla bilgi için bkz. **/nologo** adresindeki seçeneği [çalıştıran LIB](/cpp/build/reference/running-lib).|  
|**TargetMachine**|İsteğe bağlı **dize** parametresi.<br /><br /> Program veya DLL için hedef platformu belirtir.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.<br /><br /> -   **MachineARM** - **/MACHINE:ARM**<br />-   **MachineEBC** - **/MACHINE:EBC**<br />-   **MachineIA64** - **/MACHINE:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** -**/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** - **/MACHINE:SH4**<br />-   **MachineTHUMB** - **/MACHINE:THUMB**<br />-   **MachineX64** - **/MACHINE:X 64**<br />-   **MachineX86** - **/MACHINE:X86**<br /><br /> Daha fazla bilgi için [/Machine (hedef platformu belirt)](/cpp/build/reference/machine-specify-target-platform).|  
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlüğü dizini belirtir.|  
|**TreatLibWarningAsErrors**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, neden **LIB** bir çıktı dosyası durumunda oluşturmamanız için görev *lib.exe* bir uyarı oluşturur. Varsa `false`, bir çıkış dosyası oluşturulur.<br /><br /> Daha fazla bilgi için bkz. **wx** adresindeki seçeneği [LIB çalıştırma](/cpp/build/reference/running-lib).|  
|**UseUnicodeResponseFiles**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, proje sisteminin kitaplıkçıyı üretildiğinde biçimli yanıt dosyaları oluşturmasını söyler. Belirtin `true` projedeki dosyaların UNICODE yolları olduğunda.|  
|**ayrıntılı**|İsteğe bağlı **Boole** parametresi.<br /><br /> Varsa `true`, oturumunun ilerleme durumu hakkında ayrıntıları görüntüler. Bu adları içeren *.obj* eklenmekte olan dosyalar. Bilgiler Standart çıkışa gönderilir ve bir dosyaya yönlendirilebilir.<br /><br /> Daha fazla bilgi için **/VERBOSE** seçeneğini [çalıştıran LIB](/cpp/build/reference/running-lib).|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)