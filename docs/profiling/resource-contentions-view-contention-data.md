---
title: Kaynak çekişmeleri görünümü - Çekişme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e33a27d5f2b14effc9d8a90e903b34822d81edfb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31584145"
---
# <a name="resource-contentions-view---contention-data"></a>Kaynak çekişmeleri görünümü - çakışma verileri
Kaynak çakışması görünümü Çekişme olayları kaynağı olan kaynakları için Çekişme verileri listeler. Kaynağa erişim için başka bir iş parçacığı işlevinde kaynağa özel erişim aldığından beklenecek bir iş parçacığı işlevinde zorlandığında Çekişme olayı oluşur. Her kaynak Çekişme olayları sonuçlandı işlevi yürütme yollarını görüntüler bir çağrı ağacı kök düğümü değil.  
  
## <a name="data-values"></a>Veri değerleri  
  
### <a name="resource-values"></a>Kaynak değerleri  
 Kaynak satırı verileri kaynağa erişimi engellenen toplam zaman profil oluşturma verileri ve bu kaynağa erişim çakışması nedeniyle ortaya Çekişme olayları toplam sayısını görüntüler. (Bunlar dahil) ve özel bir kaynak için her zaman aynı değerlerdir.  
  
### <a name="function-values"></a>İşlev değerleri  
 İşlev değerleri çağrısı ağacında temsil yürütme yolu oluştu işlevi örneklerini dayanır.  
  
-   Özel değerler işlev ifadeleri, işlev gövdesi yürütülmekte olan oluştu olayları temel alır. İşlevin adı veriliyordu işlevlerinde oluşan olaylarla özel değerler dahil edilmez.  
  
-   Kapsayıcı değerler işlev veya işlev tarafından çağrılan işlev yürütülürken zaman oluşan olaylarla temel alır.  
  
### <a name="percentage-values"></a>Yüzde değerleri  
 Yüzde değerleri profil oluşturma verileri toplam süre veya Çekişme olayları temel alır. Rapor veya Çalıştır profili oluşturma görünümü filtre durumunda yalnızca engellenen zaman ve filtrelenmiş veri çekişmeleri toplam değeri olarak kullanılır.  
  
## <a name="navigating-the-resource-allocation-view"></a>Kaynak ayırma görünümü gezinme  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|Kaynak veya işlev adı.|  
|**Özel engellenen süresi**|-İçin bir kaynak, toplam süre bu kaynağa erişim engellendi ve beklemek için bir iş parçacığı neden oldu.<br />-Bir işlev için bu örnekler işlevinin işlev kodu işlev gövdesine yürütülmekte olan üst kaynak erişmesini engellendi zaman. İşlevin adı veriliyordu işlevlerinde engellenen süresi dahil değildir.|  
|**Özel engellenen süresi %**|-Engellendi profil oluşturma veri tüm engellenen zamanın yüzde olarak bir kaynak için bu kaynak süresi<br />-İçin bir işlev, bu işlevi örneklerinin özel engellenen süresi profil oluşturma veri tüm engellenen zamanı yüzdesi.|  
|**Özel çekişmeleri**|-Bir kaynak için kaynağa erişim toplam sayısı engellenen ve beklemek için bir iş parçacığı neden oldu.<br />-Bir işlev için bu örnekler işlevinin işlev kodu işlev gövdesine yürütülmekte olan üst kaynak erişmesini engellendi sayısı. İşlevin adı veriliyordu işlevlerinde engelleme olayları dahil edilmez.|  
|**Özel çekişmeleri %**|-Bir kaynak için bu kaynağa erişim için Çekişme olayları olan profil oluşturma veri tüm Çekişme olayları yüzdesi.<br />-Bir işlev için özel Çekişme olayları üst kaynak için bu işlevi örnekleri olan profil oluşturma veri tüm Çekişme olayları yüzdesi.|  
|**Dahil engellenen süre**|-İçin bir kaynak, toplam süre bu kaynağa erişim engellendi ve beklemek için bir iş parçacığı neden oldu.<br />-Bir işlev için bu örneğini işlev veya tüm işlevler örnekleri tarafından çağrılan zaman işlevi kod işlev gövdesine yürütülmekte olan üst kaynak erişmesini engellendi.|  
|**Kapsayıcı engellenen süresi %**|-Engellendi profil oluşturma veri tüm engellenen zamanın yüzde olarak bir kaynak için bu kaynak süresi<br />-Bir işlev için (bunlar dahil) engellenen süresi Bu işlevi örneklerinin çalışmasını profil tüm engellenen zamanın yüzde olarak oldu.|  
|**Kapsayıcı çekişmeleri**|-Bir kaynak için kaynağa erişim toplam sayısı engellenen ve beklemek için bir iş parçacığı neden oldu.<br />-Bir işlev için profil çalıştıran tüm Çekişme olayları yüzdesi (bunlar dahil) Çekişme olayları üst kaynak için bu işlevi örneklerinin yoktu.|  
|**Kapsayıcı çekişmeleri %**|-Bir kaynak için profil çalıştıran tüm Çekişme olayları yüzdesi bu kaynağa erişim için Çekişme olayları yoktu.<br />-Bir işlev için bu örnekler işlevinin işlev kodu işlev gövdesine yürütülmekte olan üst kaynak erişmesini engellendi sayısı. İşlevin adı veriliyordu işlevlerinde engelleme olayları dahil edilmez.|  
|**düzeyi**|Bu işlev çağrısı ağacında derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**Modül adı**|İşlevi içeren modülü adı.|  
|**Modül yolu**|İşlevi içeren modülü yolu.|  
|**İşlem kimliği**|İşlev yürütülmekte olan işlemin işlem kimliği (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Kaynak dosya**|Bu işlev için tanım içeriyor kaynak dosya.|