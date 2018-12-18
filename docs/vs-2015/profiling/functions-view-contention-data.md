---
title: İşlevler görünümü - çakışma verileri | Microsoft Docs
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
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ada92736312501d05504cf7b69ad07b549f31df
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765263"
---
# <a name="functions-view---contention-data"></a>İşlevler Görünümü - Çakışma Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İşlevleri raporu engellenen profil oluşturma çalıştırmasını profil oluşturma çalışması sırasında yürütme içinde işlevler Çekişme veri listesini görüntüleyin.  
  
 Eşzamanlılık metodu kullanarak toplandığı bir profil oluşturma veri dosyasını işlevler görünümünde görüntülenen değerleri aşağıdaki tabloda açıklanmaktadır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı engellenme süresi**|İşlev gövdesinde kod yürütürken gelen bu işlev boyunca engellenmiş olan süre miktarı. İşlev tarafından çağrılan işlevler engellenme süresi dahil değildir.|  
|**Dışlamalı engellenme süresi yüzdesi**|Bu işlevin dışlamalı engellenme süresi olan profil oluşturma çalışması içindeki tüm engellenme süresi yüzdesi.|  
|**Dışlamalı Çekişmeler**|Bu işlev, işlev gövdesinde kod yürütürken gelen engellendi sayısı. İşlev tarafından çağrılan işlevler çakışması dahil edilmez.|  
|**Dışlamalı Çekişme yüzdesi**|Profil oluşturma çalıştırmasını içindeki tüm çekişmelerin yüzdesi, bu işlevin dışlamalı çekişmeler yoktu.|  
|**İşlev adresi**|İşlevin adresi.|  
|**İşlev adı**|İşlev tam adı.|  
|**Kapsamlı engellenme süresi**|Bu işlev veya bu işlev tarafından çağrılan bir işlevin yürütülmesini engellendiği zaman.|  
|**Kapsamlı engellenme süresi yüzdesi**|Bu işlev veya modül, kapsamlı engellenme süresi olan profil oluşturma çalışması içindeki tüm engellenme süresinin yüzdesi.|  
|**Kapsamlı Çekişmeler**|Bu işlev veya bu işlev tarafından çağrılan bir işlevin yürütülmesini engellendi sayısı.|  
|**Kapsamlı Çekişme yüzdesi**|Profil çalıştıran tüm çekişmelerin yüzdesi bu işlev veya modül kapsamlı çakışmaları oldu.|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**Modül adı**|İşlevi içeren modül adı.|  
|**Modül yolu**|İşlevi içeren modül yolu.|  
|**İşlem kimliği**|İşlevi, yürütülmekte olan işlemin işlem kimliği (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Kaynak dosyası**|Bu işlevin tanımını içeren kaynak dosya.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [İşlevler görünümü](../profiling/functions-view.md)   
 [İşlevler görünümü - izleme](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [İşlevler görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [İşlevler görünümü](../profiling/functions-view-instrumentation-data.md)   
 [İşlevler Görünümü](../profiling/functions-view-sampling-data.md)



