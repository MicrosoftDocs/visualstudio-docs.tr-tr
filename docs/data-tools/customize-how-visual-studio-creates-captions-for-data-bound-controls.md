---
title: Açıklamalı alt yazılar verilere bağlı denetimler için özelleştirme
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 11f7249f30b1866ca7c4aea4bbefa850a5353c0f
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305591"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme

Öğeleri sürüklediğinizde [veri kaynakları penceresi](add-new-data-sources.md#data-sources-window) özel bir durum bir tasarımcının üzerine devreye: Başlık etiketindeki sütun adları daha okunabilir bir dizeye iki biçimlendirilen ya da daha fazla sözcük olarak bulunan birleştirilmesinden. Bu etiketleri oluşturulduğu, ayarlayarak şeklini özelleştirebilir **SmartCaptionExpression**, **SmartCaptionReplacement**, ve **SmartCaptionSuffix** değerler **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data tasarımcıları** kayıt defteri anahtarı.

> [!NOTE]
> Oluşturduğunuz kadar bu kayıt defteri anahtarı mevcut değil.

Akıllı Açıklamalı Altyazı değerini girilen normal ifade tarafından denetlenir **SmartCaptionExpression** değeri. Ekleme **veri tasarımcıları** kayıt defteri anahtarı başlık etiketindeki denetleyen varsayılan normal ifade geçersiz kılar. Normal ifadeler hakkında daha fazla bilgi için bkz. [Visual Studio'da normal ifadeler kullanarak](../ide/using-regular-expressions-in-visual-studio.md).

Aşağıdaki tabloda başlık etiketindeki denetleyen kayıt defteri değerleri açıklanmaktadır.

|Kayıt defteri öğesi|Açıklama|
|-------------------|-----------------|
|**SmartCaptionExpression**|Normal ifade, deseni eşleştirmesini için kullanın.|
|**SmartCaptionReplacement**|İçinde eşleşen herhangi bir gruba görüntülenecek biçimi **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Açıklamalı alt yazı sonuna eklenecek isteğe bağlı dize.|

Bu kayıt defteri değerleri için iç varsayılan ayarları aşağıdaki tabloda listelenmektedir.

|Kayıt defteri öğesi|Varsayılan değer|Açıklama|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll})(\\\p{Lu})&#124;_+**|Ardından bir büyük harf veya alt çizgi, küçük harfli bir karakterle eşleşir.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** ifadenin ilk parantez içinde eşleşen herhangi bir karakteri temsil eder ve **$2** ikinci parantez içinde eşleşen herhangi bir karakteri temsil eder. Değişiklik, ilk eşleşme, boşluk ve ikinci Eşleştir ' dir.|
|**SmartCaptionSuffix**|**:**|Döndürülen dize için eklenmiş bir karakteri temsil eder. Örneğin, açıklamalı alt yazı ise `Company Name`, sonek kolaylaştırır `Company Name:`|

> [!CAUTION]
> Kayıt Defteri Düzenleyicisi'nde her şeyi yaparken çok dikkatli olmanız gerekir. Düzenlemeden önce kayıt defterini yedekleyin. Kayıt Defteri Düzenleyicisi'ni yanlış kullanırsanız, işletim sistemini yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilir. Microsoft Kayıt Defteri Düzenleyicisi'ni kullanarak neden sorunları çözülebilir garanti etmez. Kayıt Defteri Düzenleyicisi'ni kullanım riski size aittir.
>
> Yedekleme, düzenleme ve kayıt defterini geri yüklemek için yönergeler aşağıdaki Bilgi Bankası makalesi içerir: [Microsoft Windows kayıt defterine açıklama](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us; 256986)

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Veri kaynakları penceresi akıllı açıklamalı alt yazı davranışını değiştirmek

1.  Bir komut penceresi açın **Başlat** ardından **çalıştırma**.

2.  Tür `regedit` içinde **çalıştırma** iletişim kutusu seçeneğine tıklayıp **Tamam**.

3.  Genişletin **HKEY_CURRENT_USER** > **yazılım** > **Microsoft** > **VisualStudio**düğümü.

4.  Sağ **15.0** düğümünü ve yeni bir **anahtarı** adlı `Data Designers`.

5.  Sağ **veri tasarımcıları** düğümü ve üç yeni dize değerlerini oluşturun:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Sağ **SmartCaptionExpression** değeri ve seçin **Değiştir**.

7. İstediğiniz normal ifade girin **veri kaynakları** penceresini kullanın.

8. Sağ **SmartCaptionReplacement** değeri ve seçin **Değiştir**.

9. Değiştirme girin, normal ifade ile eşleşen desenlerini görüntülemek istediğiniz şekilde biçimlendirilmiş bir dize.

10. Sağ **SmartCaptionSuffix** değeri ve seçin **Değiştir**.

11. Açıklamalı alt yazı sonunda görünmesini istediğiniz herhangi bir karakter girin.

    Sonraki öğeleri sürükleyin **veri kaynakları** penceresinde başlık etiketindeki sağlanan yeni kayıt defteri değerleri kullanılarak oluşturulur.

## <a name="turn-off-the-smart-captioning-feature"></a>Akıllı açıklamalı alt yazı özelliği devre dışı bırakmak

1.  Bir komut penceresi açın **Başlat** ardından **çalıştırma**.

2.  Tür `regedit` içinde **çalıştırma** iletişim kutusu seçeneğine tıklayıp **Tamam**.

3.  Genişletin **HKEY_CURRENT_USER** > **yazılım** > **Microsoft** > **VisualStudio**düğümü.

4.  Sağ **15.0** düğümünü ve yeni bir **anahtarı** adlı `Data Designers`.

5.  Sağ **veri tasarımcıları** düğümü ve üç yeni dize değerlerini oluşturun:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Sağ **SmartCaptionExpression** öğesi ekleyin ve seçin **Değiştir**.

7. Girin `(.*)` değeri. Bu, tüm dizeyi eşleştirir.

8. Sağ **SmartCaptionReplacement** öğesi ekleyin ve seçin **Değiştir**.

9. Girin `$1` değeri. Bu dizenin değişmeden kalır, böylece tüm dize olan eşleşen değerle değiştirir.

    Sonraki öğeleri sürükleyin **veri kaynakları** penceresinde başlık etiketindeki değiştirilmemiş açıklamalı alt yazılar ile oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)