---
title: Klavye ve Fare kısayolları için Sınıf Tasarımcısı
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87b447c3cf2fbba77584675edf3d34f44a98cb64
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848507"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Sınıf diyagramında ve sınıf Ayrıntıları penceresinde klavye ve Fare kısayolları

Klavye, fare yanı sıra gezinme eylemleri gerçekleştirmek için kullanabileceğiniz **Sınıf Tasarımcısı** ve **sınıf ayrıntıları** penceresi.

## <a name="use-the-mouse-in-class-designer"></a>Sınıf Tasarımcısı'nda fare kullanma

Sınıf diyagramları aşağıdaki fare eylemleri desteklenir:

|Fare birleşimi|Bağlam|Açıklama|
| - |-------------|-----------------|
|Çift tıklayın|Şekil öğeleri|Kod Düzenleyicisi açılır.|
|Çift tıklayın|Lolipop Bağlayıcısı|Genişlet/Daralt lollipop.|
|Çift tıklayın|Lolipop bağlayıcı etiketi|Çağıran **Göster arabirimi** komutu.|
|Fare tekerleği|Sınıf diyagramı|Dikey kaydırma.|
|**Shift** + fare tekerleği|Sınıf diyagramı|Yatay kaydırma.|
|**CTRL** + fare tekerleği|Sınıf diyagramı|Yakınlaştırma.|
|**CTRL**+**Shift** + tıklayın|Sınıf diyagramı|Yakınlaştırma.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde fare kullanma

Fareyi kullanarak görünümünü değiştirebilirsiniz **sınıf ayrıntıları** penceresi ve verileri aşağıdaki yollarla gösterir:

- Düzenlenebilir bir hücreye tıklayıp söz konusu hücrenin içeriğini düzenlemenize olanak tanır. Değişikliklerinizi veri depolanan veya görüntülenen tüm konumları yansıtılır dahil olmak üzere **özellikleri** penceresi ve kaynak kodu.

- Bir satırın herhangi bir hücreyi tıklatıldığında **özellikleri** satır tarafından temsil edilen öğeyi özelliklerini görüntülemek için pencere.

- Bir sütunun genişliğini değiştirmek için sütun genişliğini istediğiniz kadar sınır sütun başlığını sağ tarafında sürükleyin.

- Genişletme veya satır solundaki oka simgeleri tıklayarak bölme ya da özellik düğümleri Daralt.

- **Sınıf ayrıntıları** penceresi sunar yeni üyeler geçerli sınıftaki oluşturmak ve üyelerin bölmeler arasında gezinmek için çeşitli düğmeler **sınıf ayrıntıları** pencere kılavuzunun.

## <a name="use-the-keyboard-in-class-designer"></a>Sınıf Tasarımcısı'nda klavyeyi kullanma

Sınıf diyagramları aşağıdaki klavye eylemleri desteklenir:

|Anahtar|Bağlam|Açıklama|
|---------|-------------|-----------------|
|**Ok tuşları**|İç tür şekilleri|Şekil içeriği ağaç stili ezinti (Şekil çevresinde kaydırma desteklenir). Sol ve sağ tuşlarını Genişlet/geçerli öğe Genişletilebilir ise Daralt ve üst öğeye gidin değilse (ayrıntılı davranışı için ağaç görünümü Gezinti bakın).|
|**Ok tuşları**|Üst düzey şekiller|Şekilleri diyagram üzerinde taşınıyor.|
|**Shift**+**ok tuşları**|İç tür şekilleri|Şekil öğelerine üyeleri, iç içe geçmiş türler veya bölmeleri gibi oluşan yapı sürekli seçimi. Bu kısayollar çevresinde kaydırma desteklemez.|
|**Giriş**|İç tür şekilleri|Üst düzey şekli başlığı gidin.|
|**Giriş**|Üst düzey şekiller|Diyagram üzerinde ilk şekli gidin.|
|**Son**|İç tür şekilleri|Şekil içinde son görünür öğesine gidin.|
|**Son**|Üst düzey şekiller|Son şekli diyagram üzerinde gidin.|
|**Shift**+**giriş**|İç tür şeklini|Geçerli öğe ile başlayan ve aynı şekilde en üst öğede ile biten bir şeklin içindeki öğeleri seçer.|
|**Shift**+**bitiş**|İç tür şeklini|Aynı **Shift**+**giriş** yukarıdan aşağı yönde.|
|**Girin**|Tüm bağlamları|Ayrıca çift kullanılabilir olan şekil varsayılan eylemini çağırır. Çoğu durumda bu kodu görüntüle ancak bazı öğelerin farklı tanımlayın (elma şekerleri, bölme üstbilgileri, lollipop etiketlerini).|
|**+** ve **-**|Tüm bağlamları|O anda odaklanılan öğeyi Genişletilebilir ise, bu anahtarları genişletin veya öğe daraltın.|
|**>**|Tüm bağlamları|Daraltılmış ve ilk alt öğesine gider öğelerde alt öğe içeren bu öğe genişletir.|
|**<**|Tüm bağlamları|Üst öğesine gider.|
|**Alt**+**Shift**+**m**|Tür şekillerini içinde + tür şekilleri.|Varsa, şu anda Seçilen şekil lolipopa gider.|
|**Alt**+**Shift**+**B**|Tür şekillerini içinde + tür şekilleri.|Temel tür listesi tür şeklini gösterilir ve birden fazla öğe varsa, bu listenin (daraltma/genişletme) genişletme durumunu değiştirir.|
|**Delete**|Diyagramdaki şekilleri türü ve açıklama|Çağıran **diyagramdan Kaldır** komutu.|
|**Delete**|Diğer her şey üzerinde.|Çağıran **koddan Sil** komut (üyeleri, parametreleri, ilişkilendirmeler, devralma, lollipop etiketlerini).|
|**CTRL**+**Sil**|Tüm bağlamları|Çağıran **koddan Sil** seçimi komutu.|
|**sekmesi**|Tüm bağlamları|Sonraki alt (kaydırma destekler) aynı üst içinde gider.|
|**Shift**+**sekmesi**|Tüm bağlamları|Önceki alt (kaydırma destekler) aynı üst içinde gider.|
|**Ara çubuğu**|Tüm bağlamları|Seçim geçerli öğe yapar.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde klavye kullanın

> [!NOTE]
> Aşağıdaki anahtar bağlamaları için özel kod yazma deneyimi taklit edecek şekilde seçilmiştir.

Gitmek için aşağıdaki anahtarları kullanmak **sınıf ayrıntıları** penceresi:

|||
|-|-|
|Anahtar|Sonuç|
|**,** (virgül)|İmleç bir parametre satırındaki içinde ise, virgül yazma imleci sonraki parametre adı alanına taşır. İmleç bir yöntem içinde son parametre satırı varsa imleci hareket \<parametre Ekle > Yeni bir parametre oluşturmak için kullanabileceğiniz bir alan.<br /><br /> İmleç başka bir yerde ise **sınıf ayrıntıları** penceresinde virgül yazarak tam anlamıyla ekler virgül geçerli alanda.|
|**;**  (noktalı virgül) veya **)** (kapanış ayracı)|İmleci sonraki üye satırda adı alanına taşımak **sınıf ayrıntıları** pencere kılavuzunun.|
|**sekmesi**|İmleç ilk soldan sağa ve yukarıdan ardından üst taşıma sonraki alana taşır. İmleç metin içinde yazdığınız alandan taşıyorsanız **sınıf ayrıntıları** metni işleyen ve bir hata vermezse depolar.<br /><br /> İmleç bir boş alanı gibi olup olmadığını \<parametre Ekle >, sekme, sonraki satırda ilk alanına taşır.|
|**Ara çubuğu**|İmleç ilk soldan sağa ve yukarıdan ardından üst taşıma sonraki alana taşır. İmleç bir boş alanı gibi olup olmadığını \<parametre Ekle >, sonraki satırda ilk alanına taşır. Unutmayın \<alanı > hemen virgül göz ardı edilir sonra türü belirtilmiş.<br /><br /> İmleç Özet alanında ise, bir boşluk girerek bir boşluk karakteri ekler.<br /><br /> İmleci belirli bir satır Gizle sütununda ise, bir boşluk tuşlarına basarak Gizle onay kutusu değerini değiştirir.|
|**CTRL**+**sekmesi**|Başka bir belge penceresine geçiş yapar. Örneğin, geçiş **sınıf ayrıntıları** penceresi bir açık kod dosyası.|
|**ESC**|Bir alana metin yazmak başlamıştır, ESC tuşuna basarak alanın içeriğini önceki değerine dönüştürme, bir geri alma anahtar görevi görür. Sınıf Ayrıntıları penceresi genel odağa sahip, ancak belirli hiçbir hücre odaklanmış, ESC tuşuna basarak odağı UZAĞINIZDA taşır **sınıf ayrıntıları** penceresi.|
|**Yukarı ok** ve **aşağı ok**|Bu anahtarları satır satır içinde dikey imleç **sınıf ayrıntıları** pencere kılavuzunun.|
|**Sol Ok**|İmleç Ad sütununda ise (açıksa) sol ok tuşlarına hiyerarşideki geçerli düğüm daraltır.|
|**Sağ ok**|İmleç Ad sütununda ise (daraltılmışsa) basarak oka hiyerarşideki geçerli düğüm genişletir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Tür üyeleri oluşturma ve yapılandırma](creating-and-configuring-type-members.md)