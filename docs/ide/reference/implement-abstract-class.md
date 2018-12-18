---
title: Bir soyut sınıf uygulama
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: dfa2c6692ddcef9e41454bf902580f354c32f861
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53047609"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Visual Studio'da bir soyut sınıf uygulama

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** hemen soyut bir sınıf uygulamak için gereken kodu oluşturmanıza olanak tanır.

**Ne zaman:** soyut bir sınıftan istiyorsunuz.

**Neden:** bu özellik otomatik olarak tüm yöntem imzaları oluşturur ancak tüm soyut üyelerini birer birer el ile uygulayabilirsiniz.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. İmlecinizi satıra Yerleştir soyut bir sınıftan devralınan, ancak gerekli tüm üyeleri uygulanmadı belirten bir kırmızı dalgalı olduğu.

   - C# İÇİN:

       ![Vurgulanmış kodu C#](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanmış kodu VB](media/abstract-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+**.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
   - **Fare**
      - Sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
      - Kırmızı dalgalı çizgi gelin ve tıklayın ![Ampul](media/bulb-cs.png) Bu simge görünür.
      - &nbsp; ![Ampul](media/bulb-cs.png) kırmızı dalgalı çizgi içeren satırda metin imleci ise sol kenar boşluğunda görünür simge.

   ![Uygulama sınıfı Önizleme](media/abstract-preview-cs.png)

3. Seçin **soyut sınıf Uygula** aşağı açılan menüden.

   > [!TIP]
   > - Kullanım **değişiklik önizlemesi** Önizleme pencerenin alt kısmındaki bağlantı [tüm değişiklikleri görmek için](../../ide/preview-changes.md) , oluşturulacak, seçim yapmadan önce.
   > - Kullanım **belge**, **proje**, ve **çözüm** devralacak doğru yöntem imzaları arasında birden çok sınıf oluşturmak için önizleme penceresi altındaki bağlantıları soyut sınıf.

   Soyut yöntem imzaları oluşturulur ve uygulanması hazırsınız.

   - C# İÇİN:

       ![Uygulama sınıfı sonucuC#](media/abstract-result-cs.png)

   - Visual Basic:

       ![VB sınıf sonucu uygulayın](media/abstract-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)