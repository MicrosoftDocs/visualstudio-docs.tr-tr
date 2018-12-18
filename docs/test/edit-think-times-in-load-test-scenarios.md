---
title: Yük testi için düşünme sürelerini
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 236b6dffa3885928b48b7d6ea044f2494e7d7b28
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895918"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Yük testleri senaryolarında Web sitesi insan etkileşimi gecikmelerini benzetmek için Düşünme zamanlarını düzenleme

Düşünme süreleri, insanların bir Web sitesiyle etkileşimleri ile arasında beklemesine neden olan insan davranışını benzetmekte kullanılır. Düşünme süreleri, bir web performans testindeki istekleri ve bir yük testi senaryosunda test tekrarları arasında oluşur. Bir yük testinde Düşünme süreleri kullanarak daha kesin yükleme benzetimleri oluşturmak yararlı olabilir. Düşünme süreleri kullanılan veya yükleme testlerinde kullanılıp değiştirebilirsiniz. Düşünme süreleri Yükleme kullanılan içinde testleri karar **Yük Testi Düzenleyicisi**.

*Düşünme profili* bir yük testi senaryosunda uygulandığı bir ayardır. Düşünme sürelerinin kaydedilip kaydedilmediğini tek tek web performansı testleri yük testi sırasında kullanılan ayarı belirler. Kullanmak istediğiniz Düşünme süreleri bazı web performans testlerinde ancak bazı durumlarda, bunları farklı senaryolarda yerleştirmelisiniz. Senaryoları hakkında daha fazla bilgi için bkz. [yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md).

Başlangıçta kullanarak yük testi oluşturduğunuzda yük testlerinizi Düşünme süreleri kullanıp kullanmayacağınızı ayarlarsınız **Yeni Yük Testi Sihirbazı**. Daha fazla bilgi için [yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md).

**Düşünme profili** seçenekleri, aşağıdaki listede açıklanmıştır:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Kapalı**

Düşünme süreleri göz ardı edilir. Yoğun web sunucunuza stres testi uygulamak için en fazla yüklemeyi oluşturmak istiyorsanız bu ayarı kullanın. Bir web sunucusu ile daha gerçekçi Kullanıcı etkileşimlerine çalışılırken kullanmayın.

**üzerinde**

Web performans testinde tam olarak kaydedilmiş Düşünme süreleri kullanılır. Tam olarak kayıtlı web performans testlerini çalıştırma birden çok kullanıcının benzetimini yapar. Bir yük testi benzetimini yapar çünkü aynı kullanarak birden çok kullanıcı zaman bir istemeyiz yük düzeni eşitlenmiş sanal kullanıcı oluşturabilir düşünün.

**Normal dağıtım**

Düşünme süreleri kullanılır, ancak normal bir eğri üzerinde değişir. Daha gerçekçi bir benzetimi sanal kullanıcı istekleri arasında düşünme sürelerini biraz değiştirerek sağlar.

> [!NOTE]
> Yük testi senaryosu özelliklerini ve açıklamalarının tam listesi için bkz: [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Düşünme Profili Değiştir

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Bir yük testi senaryosunda bir Düşünme profili değiştirmek için

1.  Web performansı ve yük testi projesinden, bir yük testi açın.

2.  İçinde **Yük Testi Düzenleyicisi**, değiştirmek istediğiniz senaryoyu düğümü seçin **Düşünme profili**. **Düşünme profili** görüntülenen **özellikleri** penceresi. Tuşuna **F4** görüntülenecek **özellikleri** penceresi.

3.  Değişiklik **Düşünme profili** özelliğinde **özellikleri** penceresi.

4.  Özelliklerini değiştirme işlemini tamamladıktan sonra seçin **Kaydet** üzerinde **dosya** menüsü. Bu gibi durumlarda, Yük testiniz daha sonra yeni bir Düşünme profili ile çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)