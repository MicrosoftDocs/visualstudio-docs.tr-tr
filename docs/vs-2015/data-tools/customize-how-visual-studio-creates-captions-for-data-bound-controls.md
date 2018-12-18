---
title: Visual Studio 2015 açıklamalı alt yazılar verilere bağlı denetimler için nasıl oluşturduğunu özelleştirme | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 38d2e1241c3b16e5bb5cc66531515688d75d52d1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065386"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Öğeleri sürüklediğinizde [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) Windows Form Tasarımcısı, özel bir durum dönüştürülerek: Başlık etiketindeki sütun adları daha okunabilir bir dizeye iki biçimlendirilen ya da daha fazla sözcüklerdir. araya bulundu. Bu etiketleri oluşturulduğu, ayarlayarak şeklini özelleştirebilir **SmartCaptionExpression**, **SmartCaptionReplacement**, ve **SmartCaptionSuffix** değerler **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Data tasarımcıları** kayıt defteri anahtarı.

> [!NOTE]
>  Oluşturduğunuz kadar bu kayıt defteri anahtarı mevcut değil.

 Akıllı Açıklamalı Altyazı değerini girilen normal ifade tarafından denetlenir **SmartCaptionExpression** değeri. Ekleme **veri tasarımcıları** kayıt defteri anahtarı başlık etiketindeki denetleyen varsayılan normal ifade geçersiz kılar. Normal ifadeler hakkında daha fazla bilgi için bkz. [Visual Studio'da normal ifadeler kullanarak](../ide/using-regular-expressions-in-visual-studio.md).

 Aşağıdaki tabloda başlık etiketindeki denetleyen kayıt defteri değerleri açıklanmaktadır.

|Kayıt defteri öğesi|Açıklama|
|-------------------|-----------------|
|**SmartCaptionExpression**|Normal ifade desenleri, eşleştirmek için kullanılır.|
|**SmartCaptionReplacement**|İçinde eşleşen herhangi bir gruba görüntülenecek biçimi **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Açıklamalı alt yazı sonuna eklenecek isteğe bağlı dize.|

 Bu kayıt defteri değerleri için iç varsayılan ayarları aşağıdaki tabloda listelenmektedir.

|Kayıt defteri öğesi|Varsayılan değer|Açıklama|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu})&#124;_ +|Ardından bir büyük harf veya alt çizgi, küçük harfli bir karakterle eşleşir.|
|**SmartCaptionReplacement**|$1 $2|$1 ifadenin ilk parantez içinde eşleşen herhangi bir karakter ve $2 ikinci parantez içinde eşleşen herhangi bir karakteri temsil eder. Değişiklik, ilk eşleşme, boşluk ve ikinci Eşleştir ' dir.|
|**SmartCaptionSuffix**|:|Döndürülen dize için eklenmiş bir karakteri temsil eder. Örneğin, açıklamalı alt yazı ise `Company Name`, sonek kolaylaştırır `Company Name:`|

> [!CAUTION]
>  Kayıt Defteri Düzenleyicisi'nde her şeyi yaparken çok dikkatli olmanız gerekir. Düzenlemeden önce kayıt defterini yedekleyin. Kayıt Defteri Düzenleyicisi'ni yanlış kullanırsanız, işletim sistemini yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilir. Microsoft Kayıt Defteri Düzenleyicisi'ni kullanarak neden sorunları çözülebilir garanti etmez. Kayıt Defteri Düzenleyicisi'ni kullanım riski size aittir.
>
>  Yedekleme, düzenleme ve kayıt defterini geri yüklemek için yönergeler aşağıdaki Bilgi Bankası makalesi içerir: [Microsoft Windows kayıt defterine açıklama](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us; 256986)

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Veri kaynakları penceresi akıllı açıklamalı alt yazı davranışını değiştirmek için

1.  Bir komut penceresi açın **Başlat** ardından **çalıştırma**.

2.  Tür `regedit` içinde **çalıştırma** iletişim kutusu seçeneğine tıklayıp **Tamam**.

3.  Genişletin **HKEY_CURRENT_USER** düğümü.

4.  Genişletin **yazılım** düğümü.

5.  Genişletin **Microsoft** düğümü.

6.  Genişletin **VisualStudio** düğümü.

7.  Sağ **10.0** düğümünü ve yeni bir **anahtarı** adlı `Data Designers`.

8.  Sağ **veri tasarımcıları** düğümünü ve yeni bir **dize değeri** adlı `SmartCaptionExpression`.

9. Sağ **veri tasarımcıları** düğümünü ve yeni bir **dize değeri** adlı `SmartCaptionReplacement`.

10. Sağ **veri tasarımcıları** düğümünü ve yeni bir **dize değeri** adlı `SmartCaptionSuffix`.

11. Sağ **SmartCaptionExpression** öğesi ekleyin ve seçin **Değiştir**.

12. İstediğiniz normal ifade girin **veri kaynakları** penceresini kullanın.

13. Sağ **SmartCaptionReplacement** öğesi ekleyin ve seçin **Değiştir**.

14. Değiştirme girin, normal ifade ile eşleşen desenlerini görüntülemek istediğiniz şekilde biçimlendirilmiş bir dize.

15. Sağ **SmartCaptionSuffix** öğesi ekleyin ve seçin **Değiştir**.

16. Açıklamalı alt yazı sonunda görünmesini istediğiniz herhangi bir karakter girin.

     Sonraki öğeleri sürükleyin **veri kaynakları** penceresinde başlık etiketindeki sağlanan yeni kayıt defteri değerleri kullanılarak oluşturulur.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Akıllı açıklamalı alt yazı özelliği devre dışı bırakmak için

1.  Bir komut penceresi açın **Başlat** ardından **çalıştırma**.

2.  Tür `regedit` içinde **çalıştırma** iletişim kutusu seçeneğine tıklayıp **Tamam**.

3.  Genişletin **HKEY_CURRENT_USER** düğümü.

4.  Genişletin **yazılım** düğümü.

5.  Genişletin **Microsoft** düğümü.

6.  Genişletin **VisualStudio** düğümü.

7.  Sağ **10.0** düğümünü ve yeni bir **anahtarı** adlı `Data Designers`.

8.  Sağ **veri tasarımcıları** düğümünü ve yeni bir **dize değeri** adlı `SmartCaptionExpression`.

9. Sağ **veri tasarımcıları** düğümünü ve yeni bir **dize değeri** adlı `SmartCaptionReplacement`.

10. Sağ **veri tasarımcıları** düğümünü ve yeni bir **dize değeri** adlı `SmartCaptionSuffix`.

11. Sağ **SmartCaptionExpression** öğesi ekleyin ve seçin **Değiştir**.

12. Girin `(.*)` değeri. Bu, tüm dizeyi eşleştirir.

13. Sağ **SmartCaptionReplacement** öğesi ekleyin ve seçin **Değiştir**.

14. Girin `$1` değeri. Bu dizenin değişmeden kalır, böylece tüm dize olan eşleşen değerle değiştirir.

     Sonraki öğeleri sürükleyin **veri kaynakları** penceresinde başlık etiketindeki değiştirilmemiş açıklamalı alt yazılar ile oluşturulur.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
