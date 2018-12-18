---
title: 'Nasıl yapılır: komut satırından raporları filtreleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c173fb5cdea4c18f3d470bd1e92bd7f9b68a62e
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814573"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Nasıl yapılır: komut satırından raporları filtreleme
Seçeneklerini kullanarak **VSPerfReport** komut, filtre belirli zaman diliminin profil oluşturma veri dosyası, raporları veya verileri bir veya daha fazla işlemler veya iş parçacığı kısıtlamak. Bu komut hakkında daha fazla bilgi için bkz: [VSPerfReport](../profiling/vsperfreport.md).  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**StartTime:**[*değeri*]|Yalnızca değerden (milisaniye cinsinden.) toplanan verileri göster|  
|**EndTime:**[*değeri*]|Yalnızca değeri (milisaniye cinsinden.) önce toplanan verileri göster|  
|**FilterFile:** `VSPFFile`|Öğesinden oluşturulan bir filtre dosyasının konumunu belirtir **Visual Studio performans raporu** penceresi.|  
|**MsFilter:**[*StartTime, süre*]|Yalnızca verileri gösterir `StartTime` uzunluğu kadar `Duration` (milisaniye cinsinden.)|  
|**İşlem:**[*PID*]|Yalnızca belirtilen işlem verilerini gösterir.|  
|**İş parçacığı:**[*ThreadID*]|Yalnızca belirtilen iş parçacığı verileri gösterir.|  
|**İş parçacığı:**[*ThreadID, ProcessId*]|Yalnızca belirtilen işlemle ilişkili belirtilen iş parçacığı verileri gösterir.|