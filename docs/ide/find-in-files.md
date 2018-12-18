---
title: Dosyalarda Bul
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e1470868e207687a7b35f46724b80b0da0a0e71c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946565"
---
# <a name="find-in-files"></a>Dosyalarda Bul

**Dosyalarda Bul** belirtilen birtakım dosyalarda aramanıza olanak sağlar. Eşleşme bulundu ve yapılan Eylemler listelenen **Bul sonuçları** penceresinde seçili **neden seçenekleri**.

Görüntülemek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz **dosyalarda Bul** içinde **bulma ve değiştirme** penceresi.

## <a name="to-display-find-in-files"></a>Dosyalarda Bul görüntülemek için

1. Menü çubuğunda seçin **Düzenle** > **bulma ve değiştirme**.

1. Seçin **dosyalarda Bul**.

Bulma işlemi iptal etmek için basın **Ctrl** + **sonu**.

> [!NOTE]
> Bul ve Değiştir aracı dizinleri aramaz `Hidden` veya `System` özniteliği.

## <a name="find-what"></a>Aranan

Yeni metin dizesi veya deyim için aramak için kutusunda belirtin. İçin en son'Aranan 20 dizelerden herhangi birinde aramak için açılır listeyi açın ve dize seçin. Bitişik seçin **ifade oluşturucusu** bir veya daha fazla normal ifadeler, arama dizesinde kullanmak istiyorsanız, düğme. Daha fazla bilgi için bkz: [Visual Studio'da normal ifadeler kullanarak](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> **İfade oluşturucusu** düğmesi, yalnızca seçtiyseniz etkinleştirilir **normal ifadeler kullanmanız** altında **bulma seçeneklerini**.

## <a name="look-in"></a>Bakılacak yer

Gelen seçilen seçeneği **konum** aşağı açılan liste belirler olup olmadığını **dosyalarda Bul** aramaları yalnızca şu anda etkin dosyalarında veya belirli klasörlerde depolanan tüm dosyalar. Listeden bir arama kapsamı seçin veya **Gözat (...)**  görüntülemek için düğmesini **Arama Klasörleri Seç** iletişim kutusu ve kendi dizinlerin girin. Doğrudan bir yol da yazabilirsiniz **konum** kutusu.

> [!WARNING]
> İle **çözümün tamamında** veya **geçerli projenin** seçenekleri, proje ve çözüm dosyaları değil aranır. Proje dosyaları aramak istiyorsanız, bir arama klasörü seçin.

> [!NOTE]
> Varsa **konum** seçeneğe kullanıma kaynak kodu denetiminden yalnızca yerel makinenize indirilen bu dosyanın sürümü aranır bir dosya aramak neden olur.

## <a name="include-subfolders"></a>Alt klasörleri dahil et

Belirtir, alt **konum** klasörü arama yapılır.

## <a name="find-options"></a>Bulma seçenekleri

Genişlet veya daralt **bulma seçeneklerini** bölümü. Aşağıdaki seçenekler seçilen veya temizlenmiş:

**Büyük küçük harf duyarlı**

Seçili olduğunda, bir **Bul sonuçları** arama büyük küçük harfe duyarlı olur

**Tam sözcükleri eşleştir**

Seçili olduğunda, **Bul sonuçları** windows yalnızca tam sözcük eşleşmeleri döndürür.

**Normal İfadeler Kullanma**

Bu onay kutusunu seçtiyseniz eşleştiği metnin desenlerini tanımlamak için özel gösterimler kullanabilirsiniz **Aranan** veya **yerine** metin kutuları. Bu gösterimler listesi için bkz: [Visual Studio'da normal ifadeler kullanarak](../ide/using-regular-expressions-in-visual-studio.md).

**Bu dosya türlerini arayın**

Bu liste içinde arama yapmak dosya türlerini gösterir **konum** dizinleri. Bu alan ise boş, tüm dosyaların **konum** dizinleri arama yapılır.

Herhangi bir öğeyi listeden, bu belirli türdeki dosyaları bulacağı önceden yapılandırılmış arama dizesini girmek için seçin.

## <a name="result-options"></a>Sonuç seçenekleri

Genişlet veya daralt **neden seçenekleri** bölümü. Aşağıdaki seçenekler seçilen veya temizlenmiş:

**Sonuçları 1 pencere Bul**

Seçili olduğunda, geçerli arama sonuçları içeriğinin yerine geçecek **Bul sonuçları 1** penceresi. Bu pencere arama sonuçlarınızı görüntülemesi için otomatik olarak açılır. Bu pencere el ile açın, seçin **diğer pencereler** gelen **Görünüm** menü ve seçin **Bul sonuçları 1**.

**Sonuçları 2 pencere Bul**

Seçili olduğunda, geçerli arama sonuçları içeriğinin yerine geçecek **Bul sonuçları 2** penceresi. Bu pencere arama sonuçlarınızı görüntülemesi için otomatik olarak açılır. Bu pencere el ile açın, seçin **diğer pencereler** gelen **Görünüm** menü ve seçin **Bul sonuçları 2**.

**Dosya adları yalnızca görüntüleme**

Arama görüntüleme kendilerini eşleşen yerine arama içeren dosyaların bir listesini görüntüler eşleşir.

**Sonuçları ekleme**

Önceki arama sonuçlarının arama sonuçları ekler.

## <a name="see-also"></a>Ayrıca bkz.

- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
- [Dosyalarda Değiştir](../ide/replace-in-files.md)
- [Visual Studio komutları](../ide/reference/visual-studio-commands.md)