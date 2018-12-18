---
title: VSPerfMon | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c9abe6af1a775ad995fccbb6b67e1498224925a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721311"
---
# <a name="vsperfmon"></a>VSPerfMon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir uygulama için performans verilerini toplamak için VSPerfMon Aracı'nı kullanabilirsiniz; Genellikle bu araç, VSPerfCmd.exe tarafından başlatılır. VSPerfMon görüntüler işlem hakkında ek bilgi ekleme veya ayırma, VSPerfCmd aracı kullanarak mevcut değil. Bu bilgileri görüntülemek için ayrı bir pencerede VSPerfMon başlatın. VSPerfMon çağırmak için aşağıdaki sözdizimini kullanın:  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 VSPerfMon aracı seçenekleri aşağıdaki tabloda açıklanmaktadır:  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**U**|Yeniden yönlendirilmiş konsol Çıkışı Unicode olarak yazılır.  Bu, belirtilen ilk seçenek olması gerekir.|  
|**Çıkış:** `<` *dosya adı* `>`|Belirtilen dosya adı için çıkış yeniden yönlendirir.|  
|**İZLEME**|İzleme eklenmiş profil oluşturma için Performans İzleyicisi'ni başlatır.|  
|**ÖRNEK**|Örnekleme profil oluşturma için Performans İzleyicisi'ni başlatır.|  
|**KAPSAMI**|Kod kapsamı koleksiyonu için Performans İzleyicisi'ni başlatır.|  
|**EŞZAMANLILIK**|Kaynak Çekişme profil oluşturma için Performans İzleyicisi'ni başlatır.|  
|**Kullanıcı:** `[` *etki alanı* `\]` *kullanıcı adı*|İstemci erişimi için Performans İzleyicisi'ni belirtilen hesaptan sağlar.|  
|**CROSSSESSION**|Çapraz oturum profil oluşturmayı etkinleştirir.|  
|**SAYAÇ** `:cfg`|İzleme profili oluşturma metodu (İzleme) kullanıldığında, her bir izleme noktasına toplanacak CPU sayaç belirtir. Birden fazla sayaç seçenekleri belirterek, birden fazla sayaç verileri toplayabilirsiniz.<br /><br /> Sayaç belirtmek için aşağıdaki sözdizimini kullanın (*cfg*) veri:<br /><br /> **CounterName** [**, yeniden**[,**FriendlyName**]]<br /><br /> -   **CounterName** VSPerfCmd/querycounters komutu tarafından döndürülen bir sayaç adıdır.<br />-   **Reload** sayacı olay örnekleme aralığı. Kullanmayın *yeniden* araç haline getirme yöntemi ile.<br />-Belirtilen zaman **FriendlyName** değiştirir **CounterName** profil oluşturma araçları rapor sütun adları.|  
|**WINCOUNTER** `:path`|İşareti verilerle dahil etmek için bir Windows performans sayacı belirtir. `path` bir Windows performans sayacı PDH sayacı yol biçiminde dizedir. Örneğin:<br /><br /> \Processor(0)\\% işlemci zamanı<br /><br /> \System\Context anahtarlar/sn|  
|**OTOMATİK İŞARET** `:n`|/WINCOUNTER kullandığınız kullanıldığında otomatik işaretler arasındaki zaman aralığını (milisaniye cinsinden) belirtir. Yuvarlatılmış en yakın 500ms kadar.<br /><br /> Otomatik işaretleri devre dışı bırakmak için 0 kullanın. (varsayılan = 500ms belirtilmezse)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Vsınstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Performans Raporu Görünümleri](../profiling/performance-report-views.md)



