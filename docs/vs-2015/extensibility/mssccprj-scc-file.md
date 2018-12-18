---
title: MSSCCPRJ. SCC dosya | Microsoft Docs
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
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a04429bafb7da0b3d4922905bd712e82ba16a4ba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736142"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ.SCC Dosyası
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Visual Studio çözüm veya projeyi IDE'yi kullanarak kaynak denetimi altında yerleştirildiğinde, IDE iki temel bilgi parçasını öğesinden kaynak denetimi eklentisi dizeleri biçiminde alır. Bu dizeler, "AuxPath" ve "ProjName" IDE'ye opak, ancak bunlar eklenti tarafından sürüm denetimine çözüm veya projeyi bulmak için kullanılır. IDE genellikle bu dizeler ilk kez çağırarak alır [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ve ardından bunları gelecekteki çağrılar için çözüm veya proje dosyasında kaydeder [SccOpenProject](../extensibility/sccopenproject-function.md). Bir kullanıcı, çatallar, dallar veya sürüm denetimindeki çözüm ve proje dosyalarını kopyalar çözüm ve proje dosyalarında eklendiğinde, "AuxPath" ve "ProjName" dizeleri otomatik olarak güncelleştirilmez. Çözüm ve proje dosyaları sürüm denetiminde kendi doğru konuma işaret ettiğinden emin olmak için kullanıcıların el ile dizeler güncelleştirmeniz gerekir. Dizeleri donuk yöneliktir olduğundan, bu her zaman nasıl güncelleştirileceğini açık olmayabilir.  
  
 Kaynak Denetimi Eklentisi "AuxPath" ve "ProjName" dizeleri MSSCCPRJ adlı özel bir dosyaya depolayarak, bu sorunu önleyebilirsiniz. SCC dosyası. Bu sahibi olduğu ve eklenti tarafından tutulan yerel, istemci tarafı bir dosyadır. Bu dosya kaynak denetimi altında hiçbir zaman yerleştirilir ancak kaynak-denetimli dosyaları içeren her dizin eklentisi tarafından oluşturulur. Visual Studio çözüm ve proje dosyaları hangi dosyaların belirlemek için kaynak denetimi eklentisi bir standart veya kullanıcı tarafından sağlanan listesine karşı dosya uzantılarını karşılaştırabilirsiniz. Bir eklenti MSSCCPRJ desteklediğini IDE algıladıktan sonra. SCC dosya, "AuxPath" ekleme olmaktan çıkar ve çözüm ve proje dosyaları ve "ProjName" dizelere Bu dizelerin MSSCCPRJ okur. SCC dosya yerine.  
  
 MSSCCPRJ destekleyen bir kaynak denetimi eklentisi. SCC dosya, aşağıdaki yönergelere uyması gerekir:  
  
-   Yalnızca bir MSSCCPRJ olabilir. Dizin başına SCC dosyası.  
  
-   Bir MSSCCPRJ. SCC dosyası, belirli bir dizinin içindeki kaynak denetimi altında olan birden çok dosya için "AuxPath" ve "ProjName" içerebilir.  
  
-   "AuxPath" dizesini tırnak işaretleri içine olmaması gerekir. Tırnak içine sınırlayıcı olarak sağlamak için kullanılabilir (örneğin, bir çift tırnak boş bir dize belirtmek için kullanılabilir). MSSCCPRJ okunduğunda IDE "AuxPath" dizesi gelen tüm teklifler çıkartır. SCC dosyası.  
  
-   MSSCCPRJ "ProjName" dizesi. SCC dosyası, döndürülen dizenin tam olarak eşleşmelidir `SccGetProjPath` işlevi. İşlev tarafından döndürülen dize tırnak içine MSSCCPRJ dizesinde varsa. SCC dosya, tırnak işareti olmalıdır çevresinde ve bunun tersi de geçerlidir.  
  
-   Bir MSSCCPRJ. SCC dosya oluşturulduğunda veya bir dosya, kaynak denetimi altında yerleştirilmiş her güncelleştirildiğinde.  
  
-   Eğer bir MSSCCPRJ. SCC dosya silindiğinde, sağlayıcı bu dizine ilgili kaynak denetimi işlemi gerçekleştiren bir sonraki açışınızda yeniden oluşturmalıdır.  
  
-   Bir MSSCCPRJ. SCC dosya kesin olarak tanımlı biçime uymalıdır.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ gösterimi. SCC dosya biçimi  
 MSSCCPRJ örneği aşağıda verilmiştir. SCC dosya biçimi (satır numaralarını yalnızca bir kılavuz olarak sağlanır ve dosya gövdesinde dahil edilmemesi gereken):  
  
 [Satır 1] `SCC = This is a Source Code Control file`  
  
 [Satır 2]  
  
 [Satır 3] `[TestApp.sln]`  
  
 [Satır 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Satır 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Satır 6]  
  
 [Satır 7] `[TestApp.csproj]`  
  
 [Satır 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Satır 9] `SCC_Project_Name = "$/TestApp"`  
  
 İlk satır, dosyanın amacı bildiren ve bu türdeki tüm dosyalar için imza görevi görür. Bu satır, tam olarak bu tüm MSSCCPRJ gibi görünmelidir. SCC dosyaları:  
  
 `SCC = This is a Source Code Control file`  
  
 Aşağıda bir dosya adı köşeli ayraç tarafından işaretlenen her bir dosya için ayarları bölümüdür. Bu bölümde, izlenen her dosya için tekrarlanır. Bu satırı bir dosya adı, yani örneğidir `[TestApp.csproj]`. IDE, aşağıdaki iki satırı bekliyor. Ancak, tanımlanan değerlerden birisini stilini tanımlayın. Değişkenler `SCC_Aux_Path` ve `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Bu bölüm için hiçbir bitiş sınırlayıcısı yoktur. Dosyasında bulunan tüm sabit değerleri yanı sıra dosya adını scc.h üstbilgi dosyasında tanımlanmıştır. Daha fazla bilgi için [dizeleri kullanılan bir kaynak denetimi eklentisi bulmak için anahtar olarak](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [Kaynak Denetimi Eklentisi Bulmak için Anahtar Olarak Kullanılan Dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

