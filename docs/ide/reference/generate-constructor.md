---
title: Bir Oluşturucu Hızlı Eylem oluştur
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c6b267bee0c78de19ffa0d443f515375eeae949a
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295832"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Visual Studio'da bir oluşturucu üret

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** hemen bir sınıf üzerinde yeni bir oluşturucu için kod oluşturmanıza olanak tanır.

**Ne zaman:** yeni oluşturucusu ve düzgün bir şekilde otomatik olarak bildirmek istiyorsanız tanıtmak veya var olan bir oluşturucu değiştirin.

**Neden:** ancak bu özellik, uygun parametrelerle birlikte otomatik olarak oluşturur, kullanmadan önce Oluşturucu bildirebilirsiniz. Ayrıca, mevcut bir oluşturucu değiştirme otomatik olarak güncelleştirmek için bu özelliği kullanmadığınız sürece tüm callsites güncelleştirilmesini gerektirir.

**Nasıl:** bir oluşturucu oluşturmak için birkaç yolu vardır:

   - [Oluşturucu Oluşturma ve üyeleri seçin](#pick)
   - [Seçili alanları oluşturucusunu üret](#selection)
   - [Yeni kullanımdan oluşturucusunu üret](#usage)
   - [Mevcut oluşturucusuna parametre Ekle](#addparameter)
   - [Oluştur ve alan/özellik bir oluşturucu parametreden Başlat](#create)

## <a id = "pick"></a> Oluşturucu Oluşturma ve üyeleri (C# yalnızca) seçin

1. Bir sınıftaki herhangi bir boş satırında imleci yerleştirin:

   ![İmleç boş satır](media/constructor1-highlight-cs.png)

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+**.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
   - **Fare**
      - Sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
      - &nbsp; ![Ampul](media/bulb-cs.png) boş bir satıra sınıfında metin imleci ise sol kenar boşluğunda görünür simge.

   ![Oluşturucu Önizleme oluşturma](media/constructor1-preview-cs.png)

1. Seçin **Oluştur Oluşturucusu** aşağı açılan menüden.

   **Üyeleri çekme** iletişim kutusu açılır.

1. Oluşturucu parametresi olarak dahil etmek istediğiniz üyeleri seçin. Yukarı kullanarak bunları sıralayın ve aşağı okları. Seçin **Tamam**.

   ![Seçim üyeleri iletişim](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Denetleyebilirsiniz **null denetimleri Ekle** , oluşturucu parametresi için null denetimlerinin otomatik olarak oluşturmak için onay kutusu.

   Oluşturucu, belirtilen parametrelerle oluşturulur.

   ![Oluşturucu sonuç oluştur](media/constructor1-result-cs.png)

## <a id="selection"></a> Seçili alanları (yalnızca C#) oluşturucusunu üret

1. Oluşturulan, oluşturucuda olmasını istediğiniz üyeleri seçin:

   ![Üyeleri seçin](media/constructor2-highlight-cs.png)

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+**.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
   - **Fare**
      - Sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
      - &nbsp; ![Ampul](media/bulb-cs.png) Seçimi içeren satırda metin imleci ise sol kenar boşluğunda görünür simge.

      ![Oluşturucu Önizleme oluşturma](media/constructor2-preview-cs.png)

1. Seçin **'TypeName(...)' Generate Oluşturucusu**  aşağı açılan menüden.

   Oluşturucu seçili parametrelerle oluşturulur.

   ![Oluşturucu sonuç oluştur](media/constructor2-result-cs.png)

## <a id="usage"></a> Oluşturucu Oluşturma yeni kullanımından (C# ve Visual Basic)

1. İmlecinizi satıra Yerleştir kırmızı dalgalı olduğu. Kırmızı dalgalı çizgi henüz mevcut olmayan bir oluşturucu için bir çağrı gösterir.

   - C# İÇİN:

       ![Vurgulanmış kodu C#](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanmış kodu VB](media/constructor-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+**.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
   - **Fare**
      - Sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
      - Kırmızı dalgalı çizgi gelin ve tıklayın ![Ampul](media/bulb-cs.png) Bu simge görünür.
      - &nbsp; ![Ampul](media/bulb-cs.png) kırmızı dalgalı çizgi içeren satırda metin imleci ise sol kenar boşluğunda görünür simge.

      ![Oluşturucu Önizleme oluşturma](media/constructor-preview-cs.png)

3. Seçin **içinde Oluşturucu Üret '*TypeName*'** aşağı açılan menüden.

   > [!TIP]
   > Kullanım **değişiklik önizlemesi** Önizleme pencerenin alt kısmındaki bağlantı [tüm değişiklikleri görmek için](../../ide/preview-changes.md) , oluşturulacak, seçim yapmadan önce.

   Oluşturucu, kullanımdan çıkarılan herhangi bir parametre ile oluşturulur.

   - C# İÇİN:

       ![Yöntem sonuç C# oluştur](media/constructor-result-cs.png)

   - Visual Basic:

       ![Yöntem sonuç VB oluştur](media/constructor-result-vb.png)

## <a id="addparameter"></a> Oluşturucuya varolan (yalnızca C#) parametre Ekle

1. Var olan bir oluşturucu çağrısı için bir parametre ekleyin.

2. İmlecinizi satıra Yerleştir henüz mevcut olmayan bir oluşturucu kullanılan belirten bir kırmızı dalgalı olduğu.

    ![Oluşturucu vurgulama oluştur](media/constructor4-highlight-cs.png)

3. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+**.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
   - **Fare**
      - Sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
      - Kırmızı dalgalı çizgi gelin ve tıklayın ![Ampul](media/bulb-cs.png) Bu simge görünür.
      - &nbsp; ![Ampul](media/bulb-cs.png) kırmızı dalgalı çizgi içeren satırda metin imleci ise sol kenar boşluğunda görünür simge.

      ![Oluşturucu Önizleme oluşturma](media/constructor4-preview-cs.png)

4. Seçin **'TypeName(...)' için parametre Ekle**  aşağı açılan menüden.

   Oluşturucuya, kullanımdan çıkarılan türü ile parametresi eklendi.

   ![Oluşturucu sonuç oluştur](media/constructor4-result-cs.png)

Varolan bir yöntem için parametre de ekleyebilirsiniz. Daha fazla bilgi için [bir yönteme parametre eklemek](add-parameter.md).

## <a id="create"></a> Oluştur ve bir alan veya özellik (yalnızca C#) bir oluşturucu parametreden Başlat

1. Var olan bir oluşturucu bulmak ve bir parametre ekleyin:

   ![Oluşturucu vurgulama oluştur](media/constructor5-highlight-cs.png)

1. İmlecinizi yeni eklenen parametresi içinde yerleştirin.

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+**.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
   - **Fare**
      - Sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
      - &nbsp; ![Ampul](media/bulb-cs.png) eklenen parametresiyle satırındaki metin imleci ise sol kenar boşluğunda görünür simge.

   ![Oluşturucu Önizleme oluşturma](media/constructor5-preview-cs.png)

1. Seçin **oluşturma ve başlatma özelliği** veya **oluşturma ve başlatma alan** aşağı açılan menüden.

   Alan veya özellik türlerinizi eşleşecek şekilde otomatik olarak adlandırılan ve bildirilen. Bir kod satırı alanı veya özelliği Oluşturucu gövdesinde başlatmak için de eklenir.

   ![Oluşturucu sonuç oluştur](media/constructor5-result-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)