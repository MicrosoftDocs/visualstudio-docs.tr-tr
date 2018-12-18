---
title: 'Nasıl yapılır: profil oluşturma araçları çağrı izleme raporu oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a363554dfab8463ed91a82ffae9dea4f52d435d4
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815736"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Nasıl yapılır: profil oluşturma araçları çağrı izleme raporu oluşturma
*Çağrı izleme raporu* için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma araçları her giriş ve çıkış noktası, uygulamanızın işlevlere ve diğer işlevleri işlevinizi tarafından her çağrı için zamanlama bilgilerini listeler. Çağrı izleme raporları yalnızca araçları yöntemi ile toplanan, profil oluşturma verilerini için kullanılabilir.  
  
> [!NOTE]
>  Çağrı izleme raporlarında görüntüleyemiyor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Kullanmalısınız **VSPerfReport** virgülle ayrılmış bir değer üretmek için komut satırı aracı (. *CSV*) veya. *xml* dosya. Bu araç hakkında daha fazla bilgi için bkz: [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Çağrı izleme raporu oluşturmak için  
  
1.  Açık bir **komut istemi** penceresi.  
  
2.  Komut satırında, aşağıdaki komutu yazın:  
  
     *ToolsPath* **VSPerfReport** *VSPFile***/CallTrace [/ XML]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Profil oluşturma araçları komut satırı araçları yolu. Daha fazla bilgi için bkz: [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Profil oluşturma verileri (. *Vsp* veya. *vsps*) dosyası. Tam ve kısmi yollar kabul edilir.|  
    |Xml|Biçimlendirilmiş XML raporunu oluşturur.|  

  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: olay izleme için Windows (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Profil Araçları API'leri](../profiling/profiling-tools-apis.md)
