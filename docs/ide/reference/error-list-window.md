---
title: Hata Listesi Penceresi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 069f2a4957338ec3ab29855d9629712c7eb7cdcc
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389059"
---
# <a name="error-list-window"></a>Hata Listesi Penceresi

> [!NOTE]
> **Hata listesi** belirli bir hata iletisi hakkındaki bilgileri görüntüler. Hata numarasını veya hata dizesi metnini gelen kopyalayabilirsiniz **çıkış** penceresi. Görüntülenecek **çıkış** penceresinde, tuşuna **Ctrl**+**Alt**+**O**. Bkz: [çıkış penceresine](../../ide/reference/output-window.md).

**Hata listesi** penceresi, aşağıdaki görevleri gerçekleştirmenize olanak tanır:

-   Hatalar, uyarılar ve kod yazdığınız sırada üretilen iletileri görüntüleyin.

-   IntelliSense tarafından fark edilen sözdizimi hatalarını bulur.

-   Bulma dağıtım hatalarını, belirli statik analiz hatalarını ve kurumsal şablon ilkeleri uygulanırken saptanan hataları.

-   Burada sorun ortaya çıkar ve hata konumuna gitmek dosyayı açmak için hata iletisini çift tıklayın.

-   Hangi girişlerin görüntüleneceğini ve her giriş için hangi bilgi sütunlarını görünür filtreleyin.

-   Özel terimleri arayın ve yalnızca geçerli proje veya belgeyi aramayı kapsamına.

Görüntülenecek **hata listesi**, seçin **görünümü** > **hata listesi**, veya basın **Ctrl** + **\\** + **E**.

Seçebileceğiniz **hataları**, **uyarıları**, ve **iletileri** farklı düzeylerde bilgileri görmek için sekmeler.

Listeyi sıralamak için herhangi bir sütun başlığına tıklayın. Başka bir sütuna göre yeniden sıralamak için basılı **Shift** anahtar ve başka bir sütun başlığına tıklayın. Hangi sütunların görüntülenip hangilerinin gizlendiğini seçmek için seçin **sütunları göster** kısayol menüsünden. Sütunların görüntülenme sırasını değiştirmek için herhangi bir sütun başlığını sola veya sağa sürükleyin.

## <a name="error-list-filters"></a>Hata listesi filtreleri

Araç çubuğunun sağ tarafında biri diğeri araç çubuğunun solunda iki açılır liste kutusu filtrede iki tür vardır. Araç çubuğunun sol tarafta açılır listeden kullanılacak kod dosyalarını belirtir (**çözümün tamamında**, **açık belgeler**, **geçerli proje**,  **Geçerli belge**).

Analiz etmek ve hata grupları üzerinde hareket için arama kapsamını sınırlandırabilirsiniz. Örneğin, bir projenin derlenmesini önleyen çekirdek hatalarına odaklanmak isteyebilirsiniz. Kapsam belirleme seçenekleri şunlardır:

1.  **Belgeleri açma**: hatalar, uyarılar ve açık belgelerin iletileri göster.

2.  **Geçerli proje**: Göster hataları, uyarıları ve iletileri seçilmiş belgenin projesinden **Düzenleyicisi** veya seçilen projede **Çözüm Gezgini**.

    > [!NOTE]
    > Şu anda seçili olan belgenin projesi seçili projeden farklıysa, filtrelenmiş liste hataları, uyarıları ve iletileri değiştirecek **Çözüm Gezgini**.

3.  **Geçerli belge**: hatalar, uyarılar ve şu anda seçili belgedeki iletilerini göster **Düzenleyicisi** veya **Çözüm Gezgini**.

Bir filtre o anda arama sonucuna uygulanırsa, filtrenin adını görünür **hata listesi** başlık çubuğu. **Hataları**, **uyarıları**, ve **iletileri** düğmeleri sonra toplam öğe sayısının yanı sıra gösterilen filtrelenmiş öğe sayısını da görüntüler. Örneğin, düğme Göster "x / y hata". Hiçbir filtre uygulanmamışsa başlık çubuğunda yalnızca "hata listesi" yazar.

Araç çubuğunun sağ tarafındaki listenin (bir yapı işleminden kaynaklanan hatalar) derleme hatalarından gösterilip gösterilmeyeceğini belirtir veya IntelliSense (bir derleme çalıştırmadan önce algılanan hataları) veya her ikisi de.

## <a name="search"></a>Ara

Kullanım **arama hatası listesi** metin kutusunun sağ alt tarafında **hata listesi** hata Listesi'nde belirli hataları bulmak için araç çubuğu. Hata listesindeki görünen herhangi bir sütunda arama yapabilirsiniz ve arama sonuçları her zaman sorgu veya uygulanan filtre yerine sıralama önceliği olan sütun göre sıralanır. Seçerseniz **Esc** odak modundayken anahtar **hata listesi**, arama terimini temizleyebilir ve arama sonuçlarını filtrelersiniz. Ayrıca **X** temizleyin metin kutusunun sağ tarafındaki.

## <a name="save"></a>Kaydet

Hata listesini kopyalayabilir ve bir dosyaya kaydedin. Kopyala ve seçimi sağ tıklayın ve ardından bağlam menüsünde istediğiniz hataları seçin **kopyalama**. Ardından, hataları bir dosyaya yapıştırabilirsiniz. Hataları bir Excel elektronik tablosuna yapıştırırsanız, alanlar farklı sütunlar olarak görünür.

## <a name="ui-element-list"></a>UI öğe listesi

Önem Derecesi

Farklı türde görüntüler **hata listesi** giriş (**hata**, **ileti**, **uyarı**, **uyarı (etkin)**, **(Devre dışı) uyarı**.

Kod

Hata kodu görüntülenir.

Açıklama

Giriş metni görüntüler.

Proje

Geçerli projenin adını görüntüler.

Dosya

Dosya adını görüntüler.

Çizgi

Sorun oluştuğu satırı görüntüler.