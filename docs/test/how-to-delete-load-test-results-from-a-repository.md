---
title: 'Nasıl yapılır: Bir Depodan Yük Testi Sonuçlarını Silme'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, deleting results
- load test results, removing
- Load Test Results Repository
- load tests, removing results
- load test results, deleting
ms.assetid: c2afe36b-d061-4f0e-9580-c18569ec08f9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e2a7df778ff506c76513af6e6fe926a193f6a18e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065280"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Nasıl yapılır: bir depodan silme yük testi sonuçları

Bir yük testi çalıştırdığınızda, çalışma sırasında toplanan bilgiler yük testi sonuçları deposunda depolanır. Yük testi sonuçları deposu, performans sayacı verileri ve hatalar hakkında bilgi içerir. Daha fazla bilgi için [Yönet yük testi sonuçları yük testi sonuçları deposunda](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Kullanarak yük testi sonuçları Yük Testi Düzenleyicisi'nden yönetebilirsiniz **açık ve yük testi sonuçlarını yönetme** iletişim kutusu. Açın, içeri aktarma, dışarı aktarma ve yük testi sonuçları kaldırın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Depodan sonuçları silmek için

1.  Bir web performansı ve yük testi projesinden, bir yük testi açın.

2.  Gömülü araç çubuğunda **sonuçları Aç ve Yönet**.

     **Yönetme yük testi sonuçlarını Aç ve** iletişim kutusu görüntülenir.

3.  İçinde **yük testi sonuçlarını bulmak için bir denetleyici adı girin**, bir denetleyici seçin. Seçin  **\<yerel - denetleyici yok >** yerel olarak depolanmış sonuçlara ulaşmak için.

4.  İçinde **göstermek için aşağıdaki yükleme testi sonuçları**, yük testi sonuçları görüntülemek istediğinizi seçin. Seçin  **\<tüm testler için sonuçları Göster >** tüm testler için tüm sonuçları görmek için.

     Yük testi sonuçları kullanamıyorsanız, görünürler **yük testi sonuçları** listesi. Sütunların **zaman**, **süresi**, **kullanıcı**, **sonucu**, **Test**, ve  **Açıklama**. **Test** test adını içerir ve **açıklama** test çalıştırılmadan önce eklenir isteğe bağlı bir açıklama içerir. **Açıklama** sütunu içindeki girilen kısa açıklamaları görüntüler **analiz yorumları** bunun için test sonucu.

5.  İçinde **yük testi sonuçları** listesinde, bir sonuç seçin. Kullanabileceğiniz **Shift** anahtar **Ctrl** anahtar ya da her ikisini birden fazla sonuç seçin.

6.  Seçin **Kaldır**.

     Depodan sonuçları kaldırılır.

    > [!NOTE]
    > **Yönetme yük testi sonuçlarını Aç ve** sonuçları kaldırıldıktan sonra iletişim kutusu açık kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: bir depodan dışarı aktarma yük testi sonuçları](../test/how-to-export-load-test-results-from-a-repository.md)
- [Yük testi sonuçları deposu içindeki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılır: bir depoda alma yük testi sonuçları](../test/how-to-import-load-test-results-into-a-repository.md)