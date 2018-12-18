---
title: VSPerfMon | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9754d4f324c178c117e14ff5949bd6c8ef352e9
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254816"
---
# <a name="vsperfmon"></a>VSPerfMon
VSPerfMon aracı, bir uygulama için performans verilerini toplamak için kullanabilirsiniz; Bu aracı tarafından başlatılan genellikle *VSPerfCmd.exe*. VSPerfMon görüntüler işlem hakkında ek bilgi eklemek veya VSPerfCmd aracı kullanarak mevcut olmayan ayırma. Bu bilgileri görüntülemek için ayrı bir pencerede VSPerfMon başlatın. VSPerfMon çağırmak için aşağıdaki sözdizimini kullanın:  
  
```cmd  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 VSPerfMon aracı seçenekleri aşağıdaki tabloda açıklanmaktadır:  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**U**|Yeniden yönlendirilen konsol çıktısı Unicode olarak yazılır.  Bu, belirtilen ilk seçenek olmalıdır.|  
|**Çıkış:** `<` *dosya adı* `>`|Belirtilen dosya adına çıkış yeniden yönlendirir.|  
|**İZLEME**|İzleme eklenmiş profil oluşturma için Performans İzleyicisi'ni başlatır.|  
|**ÖRNEK**|Örnekleme profili oluşturma için Performans İzleyicisi'ni başlatır.|  
|**KAPSAMI**|Kod kapsamı koleksiyonu için Performans İzleyicisi'ni başlatır.|  
|**EŞZAMANLILIK**|Kaynak çakışması profil oluşturma için Performans İzleyicisi'ni başlatır.|  
|**Kullanıcı:** `[` *etki alanı* `\]` *kullanıcı adı*|İstemci erişimi için Performans İzleyicisi'ni belirtilen hesabından sağlar.|  
|**CROSSSESSION**|Profil oluşturma oturumu arası sağlar.|  
|**SAYAÇ** `:cfg`|İzleme profili oluşturma yöntemi (İzleme) kullanıldığında, her izleme noktada toplanacak CPU sayaç belirtir. Birden fazla sayaç seçenekleri belirterek birden fazla sayaç verileri toplayabilir.<br /><br /> Sayaç belirtmek için aşağıdaki sözdizimini kullanın (*cfg*) verileri:<br /><br /> **CounterName** [**, yeniden yükleme**[,**FriendlyName**]]<br /><br /> -   **CounterName** VSPerfCmd /QueryCounters komutu tarafından döndürülen bir sayaç adı.<br />-   **Yeniden yükleme** sayacı olay örnekleme aralığı. Kullanmayın *yeniden* izleme yöntemi ile.<br />-Belirtilen zaman **FriendlyName** değiştirir **CounterName** profil oluşturma araçları rapor sütun adları.|  
|**WINCOUNTER** `:path`|İşareti verilerle dahil etmek için bir Windows performans sayacı belirtir. `path` Windows performans sayacı biçiminde bir dize olarak PDH sayaç yolu değil. Örneğin:<br /><br /> \Processor(0)\\% işlemci zamanı<br /><br /> \System\Context/sn|  
|**OTOMATİK İŞARET** `:n`|/WINCOUNTER kullandığınızda otomatik işaretleri arasında zaman aralığı (milisaniye cinsinden) belirtir. En yakın 500ms kadar yuvarlanmış.<br /><br /> Otomatik işaretleri devre dışı bırakmak için 0 kullanın. (varsayılan belirtilmezse 500ms =)|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Vsınstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Performans rapor görünümleri](../profiling/performance-report-views.md)