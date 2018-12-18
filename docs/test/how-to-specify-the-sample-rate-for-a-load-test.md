---
title: 'Nasıl yapılır: Yük Testi Çalışma Ayarı için Örnek Hızı Belirtme'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: b022b4648931bf0e403df589d37cb086fb2a9c2c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053055"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Nasıl yapılır: yük testi çalışma ayarı için örnek hızı belirtme

İle yükleme testinizi oluşturduktan sonra **Yeni Yük Testi Sihirbazı**, kullanabileceğiniz **Yük Testi Düzenleyicisi** test ihtiyaçlarınızı ve hedeflerinizi karşılayacak şekilde özelliklerini değiştirmek için.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Kullanarak **Yük Testi Düzenleyicisi**, bir çalışma ayarının düzenleyebileceğiniz **örnek hızı** özellik değerine **özellikleri** penceresi. Çalıştırma ayarları özellikleri ve açıklamalarının tam listesi için bkz: [yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).

Uygun bir değer seçin **örnek hızı** yük testi çalışma ayarı için özellik tabanlı yükleme testinizin uzunluğuna. Varsayılan değer olarak beş saniye gibi küçük bir örnekleme hızı yükleme testi sonuçları veritabanı daha fazla alan gerektirir. Daha uzun yük testleri için örnek hızı artırmak topladığınız veri miktarını azaltır. Daha fazla bilgi için [nasıl yapılır: yük testi çalışma ayarı için örnek hızı belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Örnek hızlara ait bazı Kılavuzlar şunlardır:

|Yük testi süresi|Önerilen örnek hız|
|-|-----------------------------|
|\< 1 saat|5 saniye|
|1 - 8 saat|15 saniye|
|8 - 24 saat|30 saniye|
|> 24 saat|60 saniye|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Bir çalışma ayarında performans sayacı örnekleme oranı belirtmek için

1.  Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görünür. Yük testi ağacında görüntülenir.

2.  Ağaç, yük test **çalıştırma ayarları** klasörü için örnek hızı belirtme istediğiniz çalışma ayarı seçin.

3.  Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Özellikleri görüntülenir ve kategorileri yük çalışma ayarı kullanıcının **özellikleri** penceresi.

4.  İçinde **örnek hızı** özelliği, yük testi performans sayacı verilerini toplayacak sıklığını belirten bir zaman değeri girin.

5.  Özelliği değiştirmeyi bitirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Daha sonra yeni kullanarak yük testlerini çalıştırabilirsiniz **örnek hızı** değeri.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)