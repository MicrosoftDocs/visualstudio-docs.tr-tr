---
title: Yük testi için tarayıcı test karışımı
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c9cf19ad65131976ea5603ef5af49e8dd3ba555d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049334"
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Bir yük testi senaryosuna hangi web tarayıcısı türlerini belirtmek için test karışımını düzenleyin

*Tarayıcı karışımı* yük testi senaryosunda daha gerçekçi yükleme benzetimi yapmak için bir yol sağlar. Yükleme yerine tek tek web tarayıcısı heterojen bir web tarayıcı karışımını kullanarak oluşturulur. Uygulamalarınızla kullanılacak web tarayıcıları daha yakın bir yaklaşığını oluşturursunuz.

Tarayıcı karışımı, bir yük testi senaryosunda belirli bir web tarayıcı türü çalıştıran sanal kullanıcının olasılığını belirtir. Bir yük testi oluşturduğunuzda, yükü birden fazla web tarayıcısı üzerinden oluşturulur benzetimini yapmak isteyebilirsiniz. Sağlanan web tarayıcıları kümesinden Karışıma bir web tarayıcısı türü eklediğinizde, bir web performans testi tarafından gönderilen her HTTP isteği için seçilen web tarayıcısı ilişkili üstbilgileri kümesi eklenir.

Tarayıcı karışımı diğer karışımı seçenekleri gibi çalışır. Bir web tarayıcı türü, tarayıcı karışımını tabanlı bir sanal kullanıcı rastgele ilişkilidir. Bu kullanıcının karışımında belirtilen olasılığa dayalı belirli bir web tarayıcısında, testler.

Tarayıcı karışımı belirttikten sonra daha sonra ekleyebilir ve web tarayıcı türleri Karışıma kaldırın. Tarayıcı karışımı dağıtımını karıştırma denetimini kullanarak da değiştirebilirsiniz. Karıştırma denetimini bir senaryo tarayıcılarda dağıtımını kolayca ayarlamanıza olanak tanır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-browsers-to-a-scenario"></a>Bir senaryo için yeni tarayıcı ekleme

### <a name="to-add-new-browsers-to-a-scenario"></a>Yeni tarayıcılar bir senaryoya eklemek için

1.  Belirtme işleminde bir senaryo için tarayıcı karışımını seçerken **Ekle**.

     Yeni bir tarayıcı giriş kılavuza eklenir.

    > [!NOTE]
    > Görüntülenecek **Tarayıcı Karışımını Düzenle** iletişim kutusu, varolan bir senaryoyu sağ tıklayın ve ardından **Tarayıcı Karışımını Düzenle**.

2.  İçinde **tarayıcı türü** sütununda yeni giriş için oku seçin ve istenen tarayıcı türü seçin.

3.  (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın.

4.  Tarayıcılar eklemeyi tamamladığınızda, seçin **Tamam**.

##  <a name="remove-browsers-from-a-scenario"></a>Tarayıcılar senaryodan Kaldır

### <a name="to-remove-browsers-from-a-scenario"></a>Tarayıcılar senaryodan kaldırmak için

1.  Bir yük testi açın.

2.  Bir tarayıcı kaldırın ve ardından istediğiniz senaryoyu **Tarayıcı Karışımını Düzenle**.

     **Tarayıcı Karışımını Düzenle** iletişim kutusu görüntülenir.

3.  Kılavuzda tarayıcı seçin ve sonra **Kaldır**.

4.  (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın.

5.  Tarayıcıları kaldırma işlemini tamamladığınızda, seçin **Tamam**.

## <a name="about-the-mix-control"></a>Karışım denetimi hakkında

 Karıştırma denetimini testleri, tarayıcı türleri veya bir yük testi senaryosuna ağ türleri arasında dağıtılmış yük yüzdesi ayarlamanızı sağlar. Yüzde değerleri kaydırıcılar hareket ettirilerek ayarlanır. Tarayıcı türleri için karışımı ayarlamak, bir yük testi senaryosunda belirli tarayıcı türü çalıştıran sanal kullanıcının olasılığını belirtir.

 Bir kaydırıcı taşıdığınızda, tüm kullanılabilir öğeleri yüzde değerlerini değiştirin. İkiden fazla öğe varsa, ekleme veya kaldırma miktarı diğer öğeler arasında eşit olarak dağıtılır. Bu davranışı geçersiz kılmak mümkündür. Belirli bir öğe için kilit sütunundaki onay kutusunu seçerseniz, o öğe için belirtilen yüzde değerini kilitlersiniz. Ardından, bir kaydırıcıyı taşıdığınızda, ekleme veya kaldırma miktarı yalnızca kilidi kalan tüm öğeleri uygulanır.

 **Dağıt** düğmesi tüm öğeler arasında eşit yüzde değerlerini ayırmak için kullanılır. Örneğin, üç öğeye sahipseniz seçme **Dağıt** yüzde değerlerini 34, 33 ve 33 olarak ayarlar.

> [!WARNING]
> **Dağıt** düğmesi kilitli olan öğeleri geçersiz kılar.

 Yüzde değerlerini doğrudan yazmak mümkündür **%** Kaydırıcıları kullanmak yerine sütun. Bir yüzde değeri doğrudan giriyorsanız, diğer öğeler otomatik olarak ayarlar değil.

> [!NOTE]
> Toplam % 100 eklemez veya girilen yüzde değerleri kaydırıcılar devre dışı **%** ondalıksa sütun.

 Yüzde değerlerini el ile girdiğinizde, tüm öğelerin toplamının %100 olduğundan emin olmanız gerekir. Bir karışımı kaydettiğinizde, toplam %100 değilse, yüzde değerlerini oldukları gibi kabul etmeniz veya geri gidip onları ayarlamanız istenir. Oldukları gibi bunları kabul etmeyi seçerseniz, % 100 olarak dağıtılır.  Örneğin, iki öğeniz varsa ve el ile bunları %80 ve % 40 olarak ayarlarsanız, ilk öğeye (120 bölünmüş 80) % 66.67 ayarlayın ve ikinci öğe %33.33 (40 120 bölünmüş) ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)