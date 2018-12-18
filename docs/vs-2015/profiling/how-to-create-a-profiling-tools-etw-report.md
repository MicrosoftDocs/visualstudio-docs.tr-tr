---
title: 'Nasıl yapılır: profil oluşturma araçları ETW raporu oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1901cf0800483ee4ce8ba0bce26fe3cf7ac073e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761596"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Nasıl yapılır: Profil Oluşturma Araçları ETW Raporu Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir performans oturumu içinde kaydedilen ETW olayları için olay izleme Windows (ETW) raporu listeler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] profil oluşturma araçları. ETW verilerini bir ikili (.etl) dosyasında toplanır. Bu rapor hakkında daha fazla bilgi için bkz. [olay izleme için Windows (ETW) raporu](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  Arabirimdeki ETW raporları görüntüleyemez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Arabirimi kullanarak ETW veri toplama hakkında bilgi için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bkz: [nasıl yapılır: veri toplamak için olay izleme Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Bir komut istemi'nden ETW veri toplama hakkında daha fazla bilgi için bkz: [VSPerfCmd](../profiling/vsperfcmd.md) ve [olayları](../profiling/events-vsperfcmd.md).  
  
  Kullanarak ETW raporu oluşturma **VSReport / summary: etw** komutu. ETW verilerini içeren .etl, profil oluşturma veri (.vsp veya .vsps) dosyası olarak aynı dizinde olmalıdır. Varsayılan olarak, bir virgülle ayrılmış değer (.csv) dosyası olarak rapor oluşturulur. Daha fazla bilgi için [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>ETW raporu oluşturmak için  
  
-   İçinde bir **komut istemi** penceresinde aşağıdaki komutu yazın:  
  
     *ToolsPath* **VSPerfReport** *VSPFile***/Summary:ETW [/ XML]**   
  
    |||  
    |-|-|  
    |*ToolsPath*|Profil oluşturma araçları yardımcı program yolu. Daha fazla bilgi için [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Profil oluşturma veri (.vsp veya .vsps) dosyası. Tam ve kısmi yollar kabul edilir.|  
    |Xml|XML'de biçimlendirilmiş bir rapor oluşturur.|



