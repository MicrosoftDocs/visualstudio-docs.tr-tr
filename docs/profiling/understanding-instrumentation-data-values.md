---
title: İzleme veri değerlerini anlama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 524f6f575725fed754c3873af8a9ff62a3c3686f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477554"
---
# <a name="understand-instrumentation-data-values"></a>İzleme veri değerlerini anlama

*Araçları* ayrıntılı zamanlama bilgileri işlev çağrıları, satırları ve profili uygulama yönergeleri için profil oluşturma Visual Studio kayıtların yöntemi

İzleme yöntemi başında ve diğer işlevleri bu işlevler tarafından hedef işlevleri profili ikili ve önce ve sonra her çağrısı sonunu kod yerleştirir. Eklenen kod, aşağıdaki bilgileri kaydeder:

- Bu koleksiyon olay öncekinin arasındaki aralığı.

- İşletim sistemi bir işlem aralığı sırasında gerçekleştirilip. Örneğin, işletim sistemi okuma veya yazma disk veya anahtar hedef iş parçacığı ve başka bir işlem başka bir iş parçacığında arasında.

Her aralık için profil oluşturucu analiz Aralık sonunda yoktu çağrı yığını yeniden yapılandırır. Çağrı yığını zamanında bir noktada bir işlemci üzerinde etkin olan işlevler listesi verilmiştir. Yalnızca bir işlevi (geçerli işlevi) kod yürütüyor; Diğer (çağrı yığını) geçerli işlevi çağrısı ile sonuçlandı işlev çağrılarını zincirine işlevlerdir.

Aralık kaydedilirken çağrı yığınında her işlevi için profil oluşturucu analiz aralığı bir veya daha fazla işlev için dört veri değerlerini ekler. Analiz iki ölçütü temel alarak bir işlev için veri değeri aralığı ekler:

- Aralık kod işlevinin ya da buna oluşup oluşmadığını bir *alt işlevi* (işlev tarafından çağrıldı işlevi).

- Bir işletim sistemi olay aralığındaki oluşup oluşmadığını.

Bir aralık bir işlevi veya veri aralığı için veri değerleri adlı *geçen dahil*, *geçen özel*, *uygulama dahil*, ve  *Uygulama özel*:

- Bir işlevin tüm aralıkları geçen dahil veri değerine eklenir.

- Aralık kod işlevin yer alan ve alt işlevi oluştuysa, aralık işlevi geçen özel veri değeri eklenir.

- Bir işletim sistemi olay aralığında gerçekleşmedi aralığı uygulama dahil veri değerine eklenir.

- Bir işletim sistemi olay aralığında gerçekleşmedi ve işlev kodu doğrudan yürütme aralığı oluştu (diğer bir deyişle, bu alt işlevinde oluşmadı), uygulama özel veri değeri aralık eklenir.

Profil oluşturma araçları raporları profil oluşturma oturumu kendisini işlevlerde toplam değerlerini ve işlemler, iş parçacıkları ve oturum ikili dosyaları topla.

## <a name="elapsed-inclusive-values"></a>Geçen dahil değerleri

Bir işlev ve onun alt işlevleri yürütme harcanan toplam süre.

Geçen dahil değerler doğrudan işlev kodu ve hedef işlevi alt işlevlerini yürütme harcanan aralıkları yürütme harcanan aralıkları içerir. İşlevin veya işletim sistemi için bekleme içeren alt işlevleri aralıkları geçen dahil değerleri de dahil edilir.

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler

Alt işlevlerde geçen süre dışında bir işlev yürütülürken harcanan süre.

Geçen özel değerler, doğrudan bir işletim sistemi olay aralığındaki oluşup oluşmadığını bağımsız olarak işlev kodu yürütme harcanan aralıkları içerir. Tüm aralıkları hedef işlevi tarafından adı veriliyordu alt işlevleri harcadığı geçen özel değerler dahil edilmez.

## <a name="application-inclusive-values"></a>Uygulama (bunlar dahil) değerleri

Bir işlev ve işletim sistemi olayları harcanan zamanın hariç olmak üzere kendi alt işlevleri yürütme harcanan süre.

Uygulama (bunlar dahil) değerleri, işletim sistemi olayları içeren aralıkları dahil etmeyin. Uygulama dahil değerler işlevi kodu doğrudan yürütmesini aralığı olup harcandığını bağımsız olarak, bir işlev yürütülürken harcanan veya harcandığını tüm diğer aralıkları hedef işlevi alt işlevlerde içerir.

## <a name="application-exclusive-values"></a>Uygulama özel değerler

Alt işlevlerde geçen süre ve işletim sistemi olayları harcanan zamanın hariç, bir işlev yürütülürken harcanan süre.

Uygulama özel değerleri, işletim sistemi olayları içeren aralıkları veya işlev tarafından çağrılan işlevler yürütmek harcanan aralıkları dahil etmeyin. Uygulama özel değerler, doğrudan işlev kodu yürütme harcanan ve bir işletim sistemi olay içermiyordu yalnızca bu aralıkların içerir.

## <a name="elapsed-inclusive-percent"></a>Geçen dahil yüzde

Modül, iş parçacığı veya işlem işlevi geçen dahil değerleri olan toplam geçen dahil değerlerini profil oluşturma oturumu yüzdesi.

100 * işlevi geçen dahil / oturum geçen (bunlar dahil)

## <a name="elapsed-exclusive-percent"></a>Geçen özel yüzde

Modül, iş parçacığı veya işlem işlevi geçen özel değerleri olan toplam geçen dahil değerlerini profil oluşturma oturumu yüzdesi.

100 * geçen özel işlev / oturum geçen (bunlar dahil)

## <a name="application-inclusive-percent"></a>Uygulama dahil yüzde

İşlev, modül, iş parçacığı veya işlem uygulama dahil değerleri olan toplam uygulama dahil değerlerini profil oluşturma oturumu yüzdesi.

100 * işlev dahil uygulama / oturum uygulama (bunlar dahil)

## <a name="application-exclusive-percent"></a>Uygulama özel yüzde

Uygulama özel aralıklarına modülü, iş parçacığı veya işlem işlevi olan toplam uygulama dahil değerlerini profil oluşturma oturumu yüzdesi.

100 * işlev uygulama özel / oturum uygulama (bunlar dahil)

## <a name="see-also"></a>Ayrıca bkz.

[Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)  
[Nasıl yapılır: Toplama metotlarını seçme](../profiling/how-to-choose-collection-methods.md)