---
title: İzleme veri değerlerini anlama | Microsoft Docs
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
- Profiling Tools,instrumentation
- instrumentation profiling method
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aaa94700c22858be5b6a739034715d1bc926eaf9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787945"
---
# <a name="understanding-instrumentation-data-values"></a>İzleme Veri Değerlerini Anlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*İzleme* yöntemi profil oluşturma [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ayrıntılı zamanlama bilgileri işlev çağrıları, satırlar ve profili oluşturulan uygulama yönergeleri için kaydeder  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Araçlar yöntemini başlangıç ve son işlevlerin hedef profili oluşturulan ikili ve önceki ve sonraki her çağrının diğer işlevlere bu işlevleri tarafından kodu ekler. Eklenen kodu aşağıdaki kaydeder:  
  
- Bu koleksiyon olay ve önceki bir zaman aralığıdır.  
  
- Olup bir işletim sistemi aralığı sırasında bir işlem gerçekleştirdi. Örneğin, işletim sistemi okuma veya yazma disk veya anahtar hedef iş parçacığı ve başka bir işlem başka bir iş parçacığı arasında.  
  
  **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Her aralık için profil oluşturucu analiz aralığın sonunda mevcut çağırma yığınını yeniden oluşturur. Çağrı yığını, zaman içinde bir noktadaki bir işlemci üzerinde etkin olan işlevlerin listesidir. Yalnızca bir işlev (geçerli işlev) kodu yürütülüyor; diğer işlevler (çağrı yığınını) geçerli işlev çağrısında sonuçlanan işlev çağrıları zinciri içindedir.  
  
  Aralık kaydedildiği çağrı yığınında her işlev için profil oluşturucu analiz aralığı bir veya daha fazla işlev için dört veri değerlerinin ekler. Analiz iki ölçütleri temel alarak bir işlev için bir veri değer aralığı ekler:  
  
- Aralık kodu işlevin veya olup oluştu bir *alt işlevi* (işlev tarafından çağrılan bir işlev).  
  
- Olup bir işletim sistemi olay aralığındaki oluştu.  
  
  Bir işlev veya veri aralığı zaman aralığı için veri değerleri adlı *geçen kapsamlı*, *geçen dışlamalı*, *uygulama kapsamlı*, ve  *Uygulama özel*:  
  
- Bir işlevin tüm aralıkları geçen kapsamlı veri değerine eklenir.  
  
- Aralık işlevinin kodundaki ve bir alt işlevindeki oluştuysa, aralığı işlevi geçen özel veri değerine eklenir.  
  
- Bir işletim sistemi olay aralığında gerçekleşmedi aralığı uygulama kapsamlı veri değerine eklenir.  
  
- Bir işletim sistemi olay aralığında gerçekleşmedi ve doğrudan işlev kodunuzun yürütülmesine aralık oluştu (diğer bir deyişle, bir alt işlevde gerçekleşmedi), uygulama özel veri değerine aralık eklenir.  
  
  Profil oluşturma araçları raporları profil oluşturma oturumu kendisini işlevlerin toplam değerleri ve işlemler, iş parçacıkları ve oturumun ikili dosyaları toplama.  
  
## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerleri  
 Bir işlev ve alt işlevleri yürütülürken harcanan toplam süre.  
  
 Geçen kapsamlı değerler, işlev kodunu ve hedef işlevi alt işlevlerini yürütülürken harcanan aralıkları doğrudan yürütülürken harcanan aralıklarını içerir. Geçen kapsamlı değerleri, işlev veya işletim sistemi için bekleme içeren alt işlevleri de dahil edilir.  
  
## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerleri  
 Alt işlevlerde geçen zaman dışında bir işlev yürütülürken harcanan süre.  
  
 Geçen dışlamalı değerler doğrudan olup bir işletim sistemi aralığında olay bağımsız olarak işlev kod yürütülürken harcanan aralıklarını içerir. Geçen dışlamalı değerleri hedef işlev tarafından çağrılan alt işlevler harcanan tüm aralıkları dahil edilmez.  
  
## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerlerini  
 Bir işlev ve alt işlevleri işletim sistemi olayları harcanan zaman hariç, yürütülürken harcanan süre.  
  
 Uygulama kapsamlı değerlerini, işletim sistemi olaylarını içeriyor aralıkları içermez. Uygulama kapsamlı değerlerini doğrudan işlev kodu yürütme aralığı olup harcandığını bakılmaksızın, bir işlev yürütülürken harcanan veya harcandığını diğer tüm aralıkları hedef işlevin alt işlevleri içerir.  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Alt işlevlerde harcanan zaman ve işletim sistemi olayları harcanan zamanı hariç, bir işlev yürütülürken harcanan süre.  
  
 Uygulama özel değerlerini, işletim sistemi olaylarını içeriyor aralıkları veya işlev tarafından çağrılan işlevler yürütülürken harcanan aralıkları içermez. Uygulama özel değerleri olan doğrudan işlev kod yürütülürken harcanan ve bir işletim sistemi olay içermiyordu yalnızca bu aralıkları içerir.  
  
## <a name="elapsed-inclusive-percent"></a>Geçen kapsamlı yüzde  
 Geçen kapsamlı değeri işlevi, modülün, iş parçacığı veya işlem toplam geçen kapsamlı değerleri profil oluşturma oturumunun yüzdesi.  
  
 100 * işlevi geçen kapsamlı / oturum geçen kapsamlı  
  
## <a name="elapsed-exclusive-percent"></a>Geçen dışlamalı yüzde  
 İşlevi, modül, iş parçacığı ve işlem geçen özel değerleri olan toplam geçen kapsamlı değerleri profil oluşturma oturumunun yüzdesi.  
  
 100 * geçen özel işlev / oturum geçen kapsamlı  
  
## <a name="application-inclusive-percent"></a>Uygulama kapsamlı yüzde  
 İşlevi, modül, iş parçacığı ve işlem uygulama kapsamlı değerleri olan toplam uygulama kapsamlı değerleri profil oluşturma oturumunun yüzdesi.  
  
 100 * işlev uygulama kapsamlı / oturum uygulama kapsamlı  
  
## <a name="application-exclusive-percent"></a>Uygulama özel yüzde  
 İşlevi, modül, iş parçacığı ve işlem uygulaması özel aralıkları olan toplam uygulama kapsamlı değerleri profil oluşturma oturumunun yüzdesi.  
  
 100 * işlev uygulamasını özel / oturum uygulama kapsamlı  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Araçları performansını analiz etme](../profiling/analyzing-performance-tools-data.md)   
 [Nasıl Yapılır: Toplama Metotlarını Seçme](../profiling/how-to-choose-collection-methods.md)



