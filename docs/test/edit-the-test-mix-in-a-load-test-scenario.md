---
title: Bir yük testi senaryosunun test karışımı
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, adding tests
- test mix
- load tests, test mix
- load tests, removing tests
ms.assetid: 303e1d70-5d98-424a-b51e-e0898e16d3f8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3b3bd0ae4df657d7234a77413003b18d5db86138
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895996"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Hangi web performansı, birim ve kodlanmış UI testleri yük testi senaryosunda içerecek şekilde belirlemek için test karışımını düzenle

*Test karışımı* bir senaryo seçimini web senaryosu ve bu testlerin dağıtımını içeren senaryoda bulunan başarım ve birim testlerini birleşimidir. Dağıtım için belirli bir testin bir yük testi çalışması sırasında sanal bir kullanıcı tarafından seçilir olasılık belirtebileceğiniz bir ayardır.

Bir yük testi için test kümesini ekledikten sonra *test karışımı* karıştırmak seçenekleri diğer gibi çalışır. Sanal kullanıcı test karışımında belirtilen olasılığını göre rastgele seçer. Örneğin, iki testler, her yüzde 50 karışımında varsa, ilk yaklaşık yarım saat test yeni bir sanal kullanıcı seçer. Bir 50/50 karışımında bir test uzun ve diğeri kısaysa, uzun test çalıştırmasından daha fazla yük gelir.

Testler için karışımı ekledikten sonra bunları kaldırabilirsiniz. Ayrıca, dağıtım, test karışımını karıştırma denetimini kullanarak değiştirebilirsiniz. Karıştırma denetimini senaryosunda testlerin dağıtımını kolayca ayarlamanıza olanak tanır.

> [!NOTE]
> Dağıtım, belirli bir testin bir yük testi çalışması sırasında sanal bir kullanıcı tarafından seçilir olasılık ölçüsüdür. Dağıtım bir yüzdesi olarak ifade edilir. Bu nedenle, bir senaryoda bulunan tüm testler için dağıtım sayıların toplamını 100'dür. Örneğin, bir senaryo sadece bir test içeriyorsa, dağıtım için test yüzde 100 ' dir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Varolan bir senaryoyu test karışımında yeni testler ekleyin

Kullanarak yeni bir senaryo oluşturduğunuzda **Yeni Yük Testi Sihirbazı**, yeni senaryo test karışımını eklemek için web performansı ve birim testleri belirtebilirsiniz.

Senaryo metin karışımını kullanarak daha fazla web başarım ve birim testleri ekleyebilirsiniz **Yük Testi Düzenleyicisi**.

![Varolan yük testi için test ekleme](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Daha fazla test için varolan bir senaryoyu eklemek için

1.  Bir yük testi açın.

2.  İçinde **Yük Testi Düzenleyicisi**, varolan bir senaryoyu sağ tıklayın ve ardından **Test Ekle**.

     **Test Ekle** iletişim kutusu görüntülenir. Tüm web performansı, birim ve çözümünüzü senaryonuzda olmayan kodlanmış UI testlerini senaryoya eklemek kullanılabilir.

3.  İçinde **kullanılabilir testler** bölmesinde, web performansı, birim ve eklemek istediğiniz kodlanmış UI testleri seçin. Testler eklemek için sağ oku seçerek **Seçili testler** bölmesi.

4.  Testleri eklemeyi bitirdiğinizde seçin **Tamam**.

     Testleri test karışımına eklenir. Yeni dağıtım, test karışımını testler için otomatik olarak atanır.

5.  (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın. Daha fazla bilgi için [karışımı denetimi ile ilgili](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

##  <a name="remove-tests-from-a-scenario"></a>Testleri bir senaryodan Kaldır
 ![Varolan bir yük testi bir test kaldırılıyor](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Testleri bir senaryodan kaldırmak için

1.  Bir yük testi açın.

2.  İçinde **Yük Testi Düzenleyicisi**, ağaç yük testi, test ve select kaldırmak istediğiniz senaryoyu **Test Karışımını Düzenle**. **Test Karışımını Düzenle** iletişim kutusu görüntülenir.

3.  Kılavuzda web performansı, birim ve kodlanmış UI testi seçin ve sonra **Kaldır**.

    > [!NOTE]
    > Test kaldırdıktan sonra test karışımını, tercih edilen dağıtım için ayarlayın.

4.  Testleri kaldırmayı bitirdiğinizde seçin **Tamam**.

##  <a name="EditingTestMixAboutMixControl"></a> Karışım denetimi hakkında
 Karıştırma denetimini testleri, tarayıcı türleri veya bir yük testi senaryosuna ağ türleri arasında dağıtılmış yük yüzdesi ayarlamanızı sağlar. Yüzde değerleri kaydırıcılar hareket ettirilerek ayarlanır. Testler için karışımı ayarlamak, bir sanal kullanıcının bir yük testi senaryosunda belirli bir testi çalıştırma olasılığını belirtir.

 Bir kaydırıcı taşıdığınızda, tüm kullanılabilir öğeleri yüzde değerlerini değiştirin. İkiden fazla öğe varsa, ekleme veya kaldırma miktarı diğer öğeler arasında eşit olarak dağıtılır. Bu davranışı geçersiz kılmak mümkündür. Belirli bir öğe için kilit sütunundaki onay kutusunu seçerseniz, o öğe için belirtilen yüzde değerini kilitlersiniz. Ardından, bir kaydırıcıyı taşıdığınızda, ekleme veya kaldırma miktarı yalnızca kilidi kalan tüm öğeleri uygulanır.

 **Dağıt** düğmesi yüzdeyi tüm öğeler arasında eşit olarak ayırmak için kullanılır. Örneğin, üç öğeye sahipseniz seçme **Dağıt** yüzde değerlerini 34, 33 ve 33 olarak ayarlar.

> [!WARNING]
> **Dağıt** düğmesi kilitli olan öğeleri geçersiz kılar.


 Yüzde değerlerini doğrudan yazmak mümkündür **%** Kaydırıcıları kullanmak yerine sütun. Bir yüzde değeri doğrudan giriyorsanız, diğer öğeler otomatik olarak ayarlar değil.

> [!NOTE]
> Toplam % 100 eklemez veya girilen yüzde değerleri kaydırıcılar devre dışı **%** ondalıksa sütun.


 Yüzde değerlerini el ile girdiğinizde, tüm öğelerin toplamının %100 olduğundan emin olmanız gerekir. Bir karışımı kaydettiğinizde, toplam %100 değilse, yüzde değerlerini oldukları gibi kabul etmeniz veya geri gidip onları ayarlamanız istenir. Oldukları gibi bunları kabul etmeyi seçerseniz, % 100 olarak dağıtılır.  Örneğin, iki öğeniz varsa ve el ile bunları %80 ve % 40 olarak ayarlarsanız, ilk öğeye (120 bölünmüş 80) % 66.67 ayarlayın ve ikinci öğe %33.33 (40 120 bölünmüş) ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)