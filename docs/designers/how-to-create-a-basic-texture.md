---
title: 'Nasıl Yapılır: Temel Doku Oluşturma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4bd1d34ef2dc31935038bb1be30d548c58208fd
ms.sourcegitcommit: 25fc9605ba673afb51a24ce587cf4304b06aa577
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028994"
---
# <a name="how-to-create-a-basic-texture"></a>Nasıl yapılır: temel doku oluşturma

Bu makalede şu etkinlikler de dahil olmak üzere, temel bir doku oluşturmak için görüntü Düzenleyicisi kullanma işlemini gösterir:

- Doku boyutunu ayarlama

- Ön ve arka plan renkleri ayarlama

- Alfa kanalını (saydam) kullanma

- Kullanarak **dolgu** ve **elipsin** araçları

- Aracı özelliklerini ayarlama

## <a name="create-a-basic-texture"></a>Temel doku oluşturma

Görüntüleri ve oyunlarda veya uygulamalarda ilişkin dokular oluşturmak ve değiştirmek için görüntü Düzenleyicisi'ni kullanabilirsiniz.

Aşağıdaki adımlar, bir "hedef merkezi" hedefi temsil eden bir doku oluşturmayı gösterir. İşlemi tamamladığınızda, doku aşağıdaki resimdeki gibi görünmelidir. Daha iyi dokudaki saydamlık göstermek için görüntü Düzenleyicisi göstermek için yeşil, Damalı düzeni kullanmak için yapılandırıldı.

!["Hedef merkezi" hedef saydamlığına yeşil renkte gösterilir](../designers/media/digit-bullseye-texture-in-editor.png)

Başlamadan önce emin **özellikleri** penceresi görüntülenir. Kullandığınız **özellikleri** penceresi görüntüyü boyutunu ayarlayın, aracı özelliklerini değiştirmek ve çalışırken renkleri belirtin.

### <a name="create-a-bullseye-target-texture"></a>Bir "hedef merkezi" hedef doku oluşturma

1. Birlikte çalışmak bir doku oluşturun. Projenize doku ekleme hakkında daha fazla bilgi için bkz: [Resim Düzenleyicisi](../designers/image-editor.md#get-started).

2. Görüntü boyutu 512 x 512 piksel olarak ayarlayın. İçinde **özellikleri** penceresinde değerlerini ayarlayın **genişliği** ve **yükseklik** özelliklerine `512`.

3. Görüntü Düzenleyicisi araç çubuğunda **dolgu** aracı. **Özellikleri** penceresi özelliklerini görüntüler **dolgu** aracından görüntü özelliklerini birlikte.

4. Ön plan rengini tamamen saydam siyah olarak ayarlar. İçinde **özellikleri** penceresi içinde **renkleri** özellik grubu, select **ön plan**. Değerlerini ayarlayın **R**, **G**, **B**, ve **A** yanındaki Renk Seçici için Özellikler `0`.

5. Görüntü Düzenleyicisi araç çubuğunda **dolgu** aracı tuşuna basın ve basılı tutun **Shift** anahtar ve herhangi bir noktaya görüntüyü seçin. Kullanarak **Shift** anahtar görüntüde rengini değiştirmek için dolgu rengi alfa değeri neden olur; Aksi takdirde, alfa değeri dolgu rengi renk görüntünün birlikte karıştırmak için kullanılır.

    > [!IMPORTANT]
    > Bu adımda, önceki adımda, renk seçimi ile birlikte, temel görüntü için çizim "hedef merkezi" hedef dokuyu hazırlanır sağlar. Resmin saydam siyah doldurulur olduğunda — ve hedef kenarlığını siyah olduğundan — yumuşatma yapıt hedefi geçici bir çözüm olacaktır.

6. Görüntü Düzenleyicisi araç çubuğunda **elipsin** aracı.

7. Ön plan rengi, tam olarak donuk siyah olarak ayarlar. Değerlerini ayarlayın **R**, **G**, ve **B** özelliklerine `0` değeri **A** özelliğini `255`.

8. Arka plan rengi ila tamamen opak beyaz olarak ayarlar. İçinde **özellikleri** penceresi içinde **renkleri** özellik grubu, select **arka plan**. Değerlerini ayarlayın **R**, **G**, **B**, ve **A** özelliklerine `255`.

9. Elipsin ana hattın genişliği ayarlayın. İçinde **özellikleri** penceresi içinde **Görünüm** özellik grubu ayarlayın **genişliği** özelliğini `8`.

10. Bu düzgünleştirme etkin olduğundan emin olun. İçinde **özellikleri** penceresi, **Görünüm** özelliği emin olun, grup **yumuşatma** özelliği ayarlanmış.

11. Kullanarak **elipsin** aracı, piksel Koordinattan bir daire çizin `(3, 3)` piksel koordinat için `(508, 508)`. Daire daha kolay çizmek için basın tutun ve **Shift** çizerken anahtar.

    > [!NOTE]
    > Geçerli işaretçisi konumunu piksel koordinatları Visual Studio durum çubuğunda görüntülenir.

12. Arka plan rengini değiştirin. Ayarlama **R** için `44`, **G** için `165`, **B** için `211`, ve **A** için `255`.

13. Piksel koordinat başka bir daire çizin `(64, 64)` piksel koordinat için `(448, 448)`.

14. Tam opak beyaz arka plan rengini değiştirin. Ayarlama **R**, **G**, **B**, ve **A** için `255`.

15. Piksel koordinat başka bir daire çizin `(128, 128)` piksel koordinat için `(384, 384)`.

16. Arka plan rengini değiştirin. Ayarlama **R** için `255`, **G** ve **B** için `64`, ve **A** için `255`.

17. Piksel koordinat başka bir daire çizin `(192, 192)` piksel koordinat için `(320, 320)`.

"Hedef merkezi" hedef dokuyu tamamlanmıştır. Saydamlık ile gösterilen son görüntü aşağıda verilmiştir.

![Hedef dokuyu tam hedef "Merkezi"](../designers/media/gfx_image_demo_bullseye.png)

Bir sonraki adım, bu dokunun MIP düzeyleri oluşturabilirsiniz. Bilgi için [nasıl yapılır: MIP düzeyleri oluşturma ve değiştirme](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görüntü Düzenleyicisi](../designers/image-editor.md)