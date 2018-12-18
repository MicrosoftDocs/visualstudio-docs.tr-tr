---
title: Konu (Yardım Görüntüleyicisi) arama
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e50a2ecb302461db6454632e6c9702cff98c711
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378160"
---
# <a name="how-to-search-for-topics"></a>Nasıl Yapılır: Konu arayın

Belirli bir sözcüğün içeren tüm konuları bulmak için tam metin arama özelliğini kullanabilirsiniz. Ayrıca, iyileştirmek ve joker karakter ifadeler, mantıksal işleçler ve Gelişmiş arama işleçlerini kullanarak aramanızı özelleştirin.

Açmak için **arama** sekmesini, **arama** sekmesinde **Yardım Görüntüleyici** penceresinde veya klavye kullanıcısıysanız seçin **Ctrl** + **E**.

## <a name="to-perform-a-full-text-search"></a>Tam metin araması gerçekleştirmek için

1.  Arama kutusuna bulmak istediğiniz sözcüğü yazın.

2.  Arama sorgusunda, varsa hangi mantıksal ve Gelişmiş arama işleçleri, aramayı uygulamak için belirtin. Tüm kullanılabilir Yardım aranacak işleçleri kullanmayın.

    > [!NOTE]
    > İçinde **Görüntüleyici seçenekleri** iletişim kutusu, bir saat ve birincil yerel ayarınız İngilizce değilse, İngilizce içeriği dahil edilip edilmeyeceğini görüntülemek için arama sonuçlarının maksimum sayısı gibi ek tercihleri belirtebilirsiniz.

3.  Seçin **Enter** anahtarı.

     Bir arama varsayılan olarak en fazla 200 isabetli okuma sayısının döndürür ve bunları arama sonuçlarını alanında görüntüler. Her sonuç için ek sürüm bilgileri, içeriğe bağlı olarak görüntülenebilir.

4.  Bir konu görüntülemek için sonuçlar listesinden başlığını seçin.

## <a name="full-text-search-tips"></a>Tam metin arama ipuçları

Söz dizimi sorgunuzu etkilemesi anlarsanız, sizi ilgilendiren konular döndüren daha hedeflenen aramaları oluşturabilirsiniz. Sözdizimi, özel karakterler, ayrılmış sözcükleri ve filtreleri içerir. Bu konu, sorgularınızı ipuçları, yordamlar ve kolaylaştırıyor daha iyi yardımcı olacak ayrıntılı sözdizimi bilgiler sağlar.

### <a name="general-guidelines"></a>Genel yönergeler

Aşağıdaki tabloda, bazı temel kurallara ve arama sorguları Yardımı'nda geliştirmeye yönelik yönergeleri içerir.

|Sözdizimi|Açıklama|
|------------|-----------------|
|Büyük/küçük harfe duyarlılık|Aramalar büyük küçük harfe duyarlı değildir. Büyük veya küçük harf karakterler kullanarak arama ölçütlerinizi geliştirin. Örneğin, "OLE" ve "ole" aynı sonuçları döndürür.|
|Karakter birleşimleri|Yalnızca bireysel harfler için (a-z) arama yapılamıyor veya sayılar (0-9). Aktarmaya çalışırsanız arama belirli gibi "ve", "Kimden" sözcükler ayrılmıştır ve "ile", bunlar yoksayılır. Daha fazla bilgi için [sözcük aramalarına göz ardı](#stopwords) bu konunun devamındaki.|
|Değerlendirme sırası|Arama sorguları soldan sağa doğru değerlendirilir.|

### <a name="search-syntax"></a>Arama söz dizimi

Bu dize, "sözcük1 sözcük2" gibi birden çok sözcük içeren bir arama dizesi belirtirseniz yazmakla eşdeğerdir: "sözcük1 sözcük2 ve", tüm arama dizesindeki kelimeler içeren konuların döndürür.

> [!IMPORTANT]
> - Deyim aramaları desteklenmiyor. Arama dizesinde birden fazla belirtmeniz durumunda döndürülen konuları tüm belirttiğiniz sözcükleri ancak mutlaka belirttiğiniz terimin içerir.
> - Mantıksal işleçler, Boole sözcükler arasındaki ilişki belirtmek için kullanın. AND, OR, NOT, gibi mantıksal işleçler içerir ve yakında, daha fazla için aramanızı daraltın. Örneğin, "UNION bildirmek için" arama yaparsanız, arama sonuçlarını sözcükler "bildirim" ve "birleşim" en fazla birkaç sözcük birbirlerinden içeren konuları içerir. Daha fazla bilgi için [arama ifadelerindeki mantıksal işleçler](../help-viewer/logical-operators-search-expressions.md).

### <a name="filters"></a>FilTReleri

Gelişmiş arama işleçleri kullanarak, arama sonuçlarını daha fazla kısıtlayabilirsiniz. Yardımı, tam metin arama sonuçlarını filtrelemek için kullanabileceğiniz üç kategorileri içerir: Başlık, kod ve anahtar sözcüğü.

### <a name="ranking-of-search-results"></a>Arama Sonuçları sıralama

Arama algoritması derece yardımcı olmak için belirli ölçütleri geçerli arama sonuçları daha yüksek veya düşük sonuçlar listesinde. Genel olarak:

1.  Başlık arama sözcükleri içeren içerikleri olmayan içerik daha yüksek önem derecesi.

2.  Arama sözcükleri yakınında içeren içerik olmayan içerik daha yüksek önem derecesi.

3.  Daha yüksek yoğunlukta arama sözcükleri içeren içeriği daha düşük bir arama sözcükleri yoğunluğu olan içeriği, daha yüksek önem derecesi.

### <a name="stopwords"> Sözcük aramaları (durdurma sözcükleri) yoksayıldı </a>

Yaygın olarak karşılaşılan bir sözcük veya durdurma sözcükleri bazen verilen sayılar, otomatik olarak bir tam metin araması sırasında yok sayılır. İfade "geçiş" için arama yaparsanız, örneğin, arama sonuçlarını "geçiş" sözcüğünü içeren konuların değil "ile ancak" görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal ve Gelişmiş işleçler](../help-viewer/logical-operators-search-expressions.md)
- [Nasıl yapılır: Dizinde konu Bul](../help-viewer/find-topics-index.md)
- [Nasıl yapılır: TOC içinde konuları bulun](../help-viewer/find-topics-toc.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)