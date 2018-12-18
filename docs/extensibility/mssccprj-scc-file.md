---
title: MSSCCPRJ. SCC dosya | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc754437433124e033b0f0fb0feac79487664b51
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636077"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. SCC dosyası
Bir Visual Studio çözüm veya projeyi IDE'yi kullanarak kaynak denetimi altında koyun, IDE iki temel bilgi parçasını alır. Kaynak Denetimi Eklentisi dizeleri biçiminde bilgi gelir. "AuxPath" ve "ProjName" Bu dizeler IDE donuk, ancak bunlar eklenti tarafından sürüm denetimine çözüm veya projeyi bulmak için kullanılırlar. IDE genellikle bu dizeler ilk kez çağırarak alır [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ve ardından bunları gelecekteki çağrılar için çözüm veya proje dosyasında kaydeder [SccOpenProject](../extensibility/sccopenproject-function.md). Bir kullanıcı, çatallar, dallar veya sürüm denetimindeki çözüm ve proje dosyalarını kopyalar çözüm ve proje dosyalarında eklendiğinde, "AuxPath" ve "ProjName" dizeleri otomatik olarak güncelleştirilmez. Çözüm ve proje dosyaları sürüm denetiminde kendi doğru konuma işaret ettiğinden emin olmak için kullanıcıların el ile dizeler güncelleştirmeniz gerekir. Dizeleri donuk yöneliktir olduğundan, bu her zaman nasıl güncelleştirileceğini açık olmayabilir.  
  
 Kaynak Denetimi Eklentisi "AuxPath" ve "ProjName" dizeleri adlı özel bir dosyaya depolayarak bu sorunu önleyebilirsiniz *MSSCCPRJ.SCC* dosya. Bu sahibi olduğu ve eklenti tarafından tutulan yerel, istemci tarafı bir dosyadır. Bu dosya kaynak denetimi altında hiçbir zaman yerleştirilir ancak kaynak-denetimli dosyaları içeren her dizin eklentisi tarafından oluşturulur. Visual Studio çözüm ve proje dosyaları hangi dosyaların belirlemek için kaynak denetimi eklentisi bir standart veya kullanıcı tarafından sağlanan listesine karşı dosya uzantılarını karşılaştırabilirsiniz. IDE, algıladıktan sonra eklenti destekler *MSSCCPRJ.SCC* dosyası, çözüm ve proje dosyalarına "AuxPath" ve "ProjName" dizelerini katıştırma olmaktan çıkar ve bu dizelerden okuma *MSSCCPRJ.SCC*bunun yerine dosya.  
  
 Destekleyen bir kaynak denetimi eklentisi *MSSCCPRJ.SCC* dosya, aşağıdaki yönergelere uyması gerekir:  
  
-   Yalnızca bir olabilir *MSSCCPRJ.SCC* her dizin dosyası.  
  
-   Bir *MSSCCPRJ.SCC* dosya içerebilir "AuxPath" ve "ProjName" belirli bir dizinin içindeki kaynak denetimi altında olan birden çok dosya için.  
  
-   "AuxPath" dizesini tırnak işaretleri içine olmaması gerekir. Tırnak içine sınırlayıcı olarak sağlamak için kullanılabilir (örneğin, bir çift tırnak boş bir dize belirtmek için kullanılabilir). IDE alanından okurken "AuxPath" dizesi gelen tüm teklifler çıkartır *MSSCCPRJ.SCC* dosya.  
  
-   "ProjName" dizesi *MSSCCPRJ. SCC dosya* döndürülen dizenin tam olarak eşleşmelidir `SccGetProjPath` işlevi. İşlev tarafından döndürülen dize tırnak içine dizesinde varsa *MSSCCPRJ.SCC* dosya, tırnak işareti olmalıdır çevresinde ve bunun tersi de geçerlidir.  
  
-   Bir *MSSCCPRJ.SCC* dosya oluşturulduğunda veya bir dosya, kaynak denetimi altında yerleştirilmiş her güncelleştirildiğinde.  
  
-   Varsa bir *MSSCCPRJ.SCC* dosyası silindi, sağlayıcı bu dizine ilgili kaynak denetimi işlemi gerçekleştirir, sonraki açışınızda yeniden oluşturmalıdır.  
  
-   Bir *MSSCCPRJ.SCC* dosya kesin olarak tanımlanan biçime uymalıdır.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ gösterimi. SCC dosya biçimi  
 Bir örnek aşağıdadır *MSSCCPRJ.SCC* (satır numaralarını yalnızca bir kılavuz olarak sağlanır ve dosya gövdesinde dahil edilmemesi gereken) dosya biçimi:  
  
 [Satır 1] `SCC = This is a Source Code Control file`  
  
 [Satır 2]  
  
 [Satır 3] `[TestApp.sln]`  
  
 [Satır 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Satır 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Satır 6]  
  
 [Satır 7] `[TestApp.csproj]`  
  
 [Satır 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Satır 9] `SCC_Project_Name = "$/TestApp"`  
  
 İlk satır, dosyanın amacı bildiren ve bu türdeki tüm dosyalar için imza görevi görür. Bu satır, tam olarak bu tüm gibi görünmelidir *MSSCCPRJ.SCC* dosyaları:  
  
 `SCC = This is a Source Code Control file`  
  
 Aşağıdaki bölümde, dosya adı köşeli ayraç tarafından işaretlenen her bir dosya için ayarları ayrıntıları. Bu bölümde, izlenen her dosya için tekrarlanır. Bu satırı bir dosya adı, yani örneğidir `[TestApp.csproj]`. IDE, aşağıdaki iki satırı bekliyor. Ancak, tanımlanan değerlerden birisini stilini tanımlayın. Değişkenler `SCC_Aux_Path` ve `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Bu bölüm için hiçbir bitiş sınırlayıcısı yoktur. Dosyasında bulunan tüm sabit değerleri yanı sıra dosya adını scc.h üstbilgi dosyasında tanımlanmıştır. Daha fazla bilgi için [kaynak denetimi eklentisi bulmak için anahtar olarak kullanılan dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [Kaynak denetimi eklentisi bulmak için anahtar olarak kullanılan dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)