---
title: MSBuild komut satırı başvurusu | Microsoft Docs
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
- MSBuild, msbuild.exe
- MSBuild, command line reference
- msbuild.exe
ms.assetid: edaa65ec-ab8a-42a1-84cb-d76d5b2f4584
caps.latest.revision: 61
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a1827166829686801743ccc98156a0009e50dc3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245914"
---
# <a name="msbuild-command-line-reference"></a>MSBuild Komut Satırı Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir proje veya çözüm dosyası oluşturmak için MSBuild.exe kullandığınızda, işlem çeşitli yönlerini belirlemek için birkaç anahtar ekleyebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`ProjectFile`|Hedefler proje dosyasında belirttiğiniz oluşturur. MSBuild, proje dosyası belirtmezseniz, geçerli çalışma dizini "proj" sona erer ve bu dosyayı kullanan bir dosya adı uzantısı için arar. Bu bağımsız değişken için bir Visual Studio çözüm dosyası da belirtebilirsiniz.|  
  
## <a name="switches"></a>Anahtarlar  
  
|Anahtar|Kısa biçim|Açıklama|  
|------------|----------------|-----------------|  
|/help|/? veya/h|Kullanım bilgilerini görüntüler. Aşağıdaki komut bir örnektir:<br /><br /> `msbuild.exe /?`|  
|/detailedsummary|/DS|Yapı günlüğüne sonunda oluşturulmuş yapılandırmaları ve bunlar düğümlere nasıl zamanlanan hakkında ayrıntılı bilgileri gösterir.|  
|/ignoreprojectextensions: `extensions`|/ Yoksay: `extensions`|Belirtilen uzantılar oluşturmak için hangi proje dosyasına belirlerken yoksayın. Aşağıdaki örnekte gösterildiği gibi birden fazla uzantı ayırmak için noktalı virgül veya virgülle kullanın:<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/ maxcpucount [:`number`]|/m [:`number`]|Kullanılacak eş zamanlı işlemlerin en fazla sayısını belirtir. Bu anahtar eklemezseniz, varsayılan değer 1'dir. Bu anahtarı bir değer belirtmeden eklerseniz, MSBuild bilgisayardaki işlemci sayısını kadar kullanın. Daha fazla bilgi için [paralel birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Aşağıdaki örnek, aynı anda üç projeleri sağlayan üç MSBuild işlemleri kullanarak derlemek için MSBuild bildirir:<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/ noautoresponse|/noautorsp|MSBuild.rsp dosyaları otomatik olarak dahil değildir.|  
|/nodeReuse:`value`|/nr:`value`|Etkinleştirmek veya yeniden kullanma MSBuild düğümlerinin devre dışı. Aşağıdaki değerleri belirtebilirsiniz:<br /><br /> -   **True**. Ardışık derlemeler bunları (varsayılan) kullanabilmesi için derleme tamamlandıktan sonra düğümleri kalır.<br />-   **False**. Derleme tamamlandıktan sonra düğümleri kalır yok.<br /><br /> Bir düğüm yürüten bir projeye karşılık gelir. Eklerseniz **/maxcpucount** anahtar, birden fazla düğüme eşzamanlı olarak yürütebilir.|  
|/nologo||Başlangıç başlığını veya telif hakkı iletisini görüntülemez.|  
|/ önişle [:`filepath`]|/PP [:`filepath`]|Tarafından toplanan, tek proje dosyası oluşturma inlining'i tüm sınırlarının ile bir yapı sırasında alınmayacaktır dosyalar olarak işaretlenmiş. Hangi dosyaların içeri aktarılmakta olan daha kolay belirlemek için bu anahtarı kullanın, burada dosyaları içeri aktarılmakta olan ve bu dosyaları için derleme katkıda. Bu anahtar kullandığınızda, proje oluşturulan değil.<br /><br /> Belirtirseniz bir `filepath`, çıkış dosyasının toplu proje dosyasıdır. Aksi takdirde, çıktıyı konsol penceresinde görünür.<br /><br /> Nasıl kullanılacağı hakkında daha fazla bilgi için `Import` öğesinin başka bir proje dosyasına bir proje dosyası eklemek için [içeri aktarma öğesi (MSBuild)](../msbuild/import-element-msbuild.md) ve [nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|  
|/ Property:`name`=`value`|/ p:`name`=`value`|Ayarlayın veya geçersiz kılma belirtilen proje düzeyi özellikleri burada `name` özellik adı ve `value` özellik değeri. Ayrı ayrı her bir özellik belirtin veya aşağıdaki örnekte gösterildiği gibi birden çok özellik ayırmak için noktalı virgül veya virgülle kullanın:<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/ target:`targets`|/ t:`targets`|Proje belirtilen hedeflerin oluşturun. Ayrı ayrı her bir hedef belirtin veya aşağıdaki örnekte gösterildiği gibi birden çok hedef ayırmak için noktalı virgül veya virgülle kullanın:<br /><br /> `/target:Resources;Compile`<br /><br /> Bu anahtarı kullanarak tüm aracıların belirtirseniz, tüm hedeflerini yerine çalıştıkları `DefaultTargets` proje dosyasında özniteliği. Daha fazla bilgi için [hedef derleme sırası](../msbuild/target-build-order.md) ve [nasıl yapılır: belirtin, hedef yapı ilk](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Bir hedef görevler grubudur. Daha fazla bilgi için [hedefleri](../msbuild/msbuild-targets.md).|  
|/toolsversion:`version`|/TV:`version`|Aşağıdaki örnekte gösterildiği gibi projeyi oluşturmak için kullanılacak araç takımı sürümünü belirtir: `/toolsversion:3.5`<br /><br /> Bu anahtarı kullanarak bir projeyi oluşturun ve belirtilen sürümden farklı bir sürüm belirtin [proje öğesi (MSBuild)](../msbuild/project-element-msbuild.md). Daha fazla bilgi için [ToolsVersion ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).<br /><br /> MSBuild 4.5 için aşağıdaki değerleri belirtebilirsiniz `version`: 2.0, 3.5 ve 4.0. 4.0 belirtirseniz `VisualStudioVersion` yapı özelliği kullanmak için hangi alt araç belirtir. Daha fazla bilgi için alt araç takımları bölümüne bakın. [araç takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).<br /><br /> Bir araç takımı, görevler, hedefler ve bir uygulama oluşturmak için kullanılan araçları oluşur. Araçlar csc.exe ve vbc.exe gibi derleyicileri içerir. Araç takımları hakkında daha fazla bilgi için bkz: [araç takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [standart ve özel araç takımı yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md), ve [çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md). **Not:** araç takımının sürüm üzerinde bir proje oluşturulan çalıştırmak için .NET Framework sürümü hedef çerçeve ile aynı değildir. Daha fazla bilgi için [hedef çerçevesi ve hedef platformu](../msbuild/msbuild-target-framework-and-target-platform.md).|  
|/ validate: [`schema`]|/VAL [`schema`]|Proje dosyası doğrulamak ve doğrulama başarılı olursa, projeyi derleyin.<br /><br /> Belirtmezseniz `schema`, proje, varsayılan şemayla doğrulandı.<br /><br /> Belirtirseniz `schema`, proje, belirttiğiniz şemayla doğrulandı.<br /><br /> Aşağıdaki ayarı bir örnek verilmiştir: `/validate:MyExtendedBuildSchema.xsd`|  
|/verbosity:`level`|/v:`level`|Yapı günlüğünde görüntülenecek bilgi miktarını belirtir. Her bir Günlükçü bu Günlükçü için ayarladığınız ayrıntı düzeyini dayalı olarak olayları görüntüler.<br /><br /> Aşağıdaki ayrıntı düzeylerinden belirtebilirsiniz: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.<br /><br /> Aşağıdaki ayarı bir örnek verilmiştir: `/verbosity:quiet`|  
|/ VERSION|/ ver|Yalnızca sürüm bilgilerini görüntüleyin. Proje oluşturulan değil.|  
|@`file`||Bir metin dosyasından komut satırı anahtarları ekleyin. Birden çok dosyanız varsa, bunları ayrı ayrı belirtin. Daha fazla bilgi için [yanıt dosyaları](../msbuild/msbuild-response-files.md).|  
  
### <a name="switches-for-loggers"></a>Günlükçüler için anahtarlar  
  
|Anahtar|Kısa biçim|Açıklama|  
|------------|----------------|-----------------|  
|/consoleloggerparameters:<br /><br /> `parameters`|/clp:`parameters`|Derleme bilgileri konsol penceresinde görüntüler konsol günlüğe belirttiğiniz parametreleri geçirin. Aşağıdaki parametreleri belirtebilirsiniz:<br /><br /> -   **PerformanceSummary**. Görevler, hedefler ve projeleri harcanan zamanı gösterir.<br />-   **Özet**. Sonunda, hata ve uyarı özetini gösterir.<br />-   **NoSummary**. Hata ve uyarı özeti sonunda gösterme.<br />-   **ErrorsOnly**. Yalnızca hataları gösterir.<br />-   **WarningsOnly**. Yalnızca uyarıları göster.<br />-   **NoItemAndPropertyList**. Öğeleri ve ayrıntı düzeyini ayarlanırsa, her proje yapı başlangıcında görünür özellikler listesini gösterme `diagnostic`.<br />-   **ShowCommandLine**. Göster `TaskCommandLineEvent` iletileri.<br />-   **ShowTimestamp**. Herhangi bir ileti öneki olarak zaman damgasını gösterir.<br />-   **ShowEventId**. Olay kimliği için her bir olayı başlatıldı, tamamlanan olay ve ileti gösterin.<br />-   **ForceNoAlign**. Konsol arabellek boyutu metni hizalama yok.<br />-   **DisableConsoleColor**. Varsayılan konsol renkleri tüm günlük iletileri kullanın.<br />-   **DisableMPLogging**. Çok işlemcili günlük çıkış stili, çok işlemcili olmayan modda çalışırken devre dışı bırakın.<br />-   **EnableMPLogging**. Çok işlemcili günlük stili bile çok işlemcili olmayan modda çalışırken etkinleştirin. Bu günlük stili varsayılan olarak açıktır.<br />-   **Ayrıntı**. Geçersiz kılma **/verbosity** bu Günlükçü için ayarlama.<br /><br /> Aşağıdaki örnekte gösterildiği gibi birden çok parametre ayırmak için noktalı virgül veya virgülle kullanın:<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/distributedFileLogger|/dfl|Her MSBuild düğümün yapı çıkışını kendi dosyasına kaydedin. İlk konum: Bu dosyalar için geçerli bir dizindir. Varsayılan olarak, dosyalar adlandırılır "MSBuild*nodeId*.log". Kullanabileceğiniz **/fileLoggerParameters** dosyaları ve diğer parametreleri fileLogger konumunu belirtmek için anahtar.<br /><br /> Kullanarak bir günlük dosyası adında **/fileLoggerParameters** anahtarı, dağıtılmış Günlükçü kullanır, şablon olarak adlandırın ve her düğüm için bir günlük dosyası oluştururken bu ada düğüm kimliği ekleyin.|  
|/distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|/DL:`central logger`*`forwarding logger`|MSBuild, farklı bir Günlükçü örneği için her bir düğüm ekleme, olaylarından günlük. Birden çok günlükçüleri belirtmek için ayrı ayrı her bir Günlükçü belirtin.<br /><br /> Günlükçü söz dizimi bir Günlükçü belirtmek için kullanın. Günlükçü sözdizimi için bkz **/logger** aşağıdaki anahtar.<br /><br /> Aşağıdaki örnekler, bu anahtarı kullanın gösterilmektedir:<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/fileLogger<br /><br /> *[sayı]*|/fl [`number`]|Derleme çıktısında tek bir dosyayı geçerli dizinde oturum açın. Belirtmezseniz `number`, çıktı dosyası msbuild.log olarak adlandırılır. Belirtirseniz `number`, çıktı dosyası msbuild adlı`n`n .log `number`. `Number` 1'den 9 arası rakam olabilir.<br /><br /> Kullanabileceğiniz **/fileLoggerParameters** anahtarını dosyası ve diğer parametreleri fileLogger için konumu belirtin.|  
|/fileloggerparameters:[number]<br /><br /> `parameters`|/FLP: [ `number`] `parameters`|Dosya günlükçüsünün ve dağıtılmış dosya günlükçüsünün herhangi ek bir parametre belirtir. Bu anahtarın varlığı, gelir karşılık gelen /**filelogger [**`number`**]** anahtar. `Number` 1'den 9 arası rakam olabilir.<br /><br /> İçin listelenen tüm parametreleri kullanabilirsiniz **/consoleloggerparameters**. Ayrıca, bir veya daha fazla aşağıdaki parametreleri kullanabilirsiniz:<br /><br /> -   **Günlük dosyası**. Hangi derleme günlüğüne yazılan günlük dosyası yolu. Dağıtılmış dosya günlükçüsünün bu yolu, günlük dosyalarının adlarını ekler.<br />-   **Append**. Yapı günlüğüne günlük dosyasına eklenir veya onun üzerine yazar olup olmadığını belirler. Anahtar ayarladığınızda yapı günlüğüne günlük dosyasına eklenir. Anahtar mevcut olmadığında, var olan bir günlük dosyasının içeriğinin üzerine yazılır.<br />     Bunu true veya false, ayarlanmasına ne olursa olsun ekleme anahtar içeriyorsa, günlük eklenir. Append anahtar eklemezseniz, günlük üzerine yazılır.<br />     Bu durumda dosyanın üzerine yazılır: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     Bu durumda, dosyayı eklenir: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     Bu durumda, dosyayı eklenir: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Kodlama**. (Örneğin, UTF-8, Unicode ve ASCII) için dosya kodlamasını belirtir.<br /><br /> Aşağıdaki örnek, uyarılar ve hatalar için ayrı günlük dosyalarını oluşturur:<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> Aşağıdaki örneklerde, diğer olasılıklar gösterilmektedir:<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|/Logger:<br /><br /> `logger`|/ l:`logger`|Günlükçü MSBuild'den olayları günlüğe kaydetmek için belirtir. Birden çok günlükçüleri belirtmek için ayrı ayrı her bir Günlükçü belirtin.<br /><br /> İçin aşağıdaki sözdizimini kullanın `logger`: `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> İçin aşağıdaki sözdizimini kullanın `LoggerClass`: `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Derlemenin tam olarak bir Günlükçü içeriyorsa Günlükçü sınıfı belirtmeniz gerekmez.<br /><br /> İçin aşağıdaki sözdizimini kullanın `LoggerAssembly`: `{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> Günlükçü parametreler isteğe bağlıdır ve tam olarak onları girerken için Günlükçü geçirilir.<br /><br /> Aşağıdaki örneklerde **/logger** geçin.<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolelogger|/noconlog|Varsayılan konsol günlüğe devre dışı bırakın ve olayları konsolda oturum yok.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yapılar `rebuild` hedefinin `MyProject.proj` proje.  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>Örnek  
 MSBuild.exe daha karmaşık yapıları gerçekleştirmek için kullanabilirsiniz. Örneğin, belirli projelerin bir çözümde belirli hedefler oluşturmak için kullanabilirsiniz. Aşağıdaki örnek projeyi oluşturur `NotInSolutionFolder` ve proje temizler `InSolutionFolder`, içinde `NewFolder` Çözüm klasörü.  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Yaygın MSBuild Proje Özellikleri](../msbuild/common-msbuild-project-properties.md)



