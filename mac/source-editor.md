---
title: Kaynak Düzenleyicisi
description: Mac için Visual Studio Kaynak Düzenleyicisi'ni kullanarak
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: b284cde511b17863861908d9967bbea7672e297b
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295702"
---
# <a name="source-editor"></a>Kaynak Düzenleyicisi

Güvenilir bir kaynak Düzenleyicisi kod temellerini ve verimli bir şekilde yazmak için gereklidir. Mac için Visual Studio IDE ile etkileşimlerinizde ortasına bir Gelişmiş kaynak Düzenleyicisi sağlar. Kaynak Düzenleyicisi beklediğiniz ve kolayca çalışmanızı yapmanız gereken özellikleri sağlar: temel tür kendi Roslyn derleyici tümleştirmesinin avantajları için söz dizimi vurgulama, kod parçacıkları ve kod katlamayı, tam olarak işlevsel IntelliSense gibi kod tamamlama.

Mac için Visual Studio kaynak düzenleyicisinde, yeniden düzenleme, hata ayıklama ve sürüm denetimi tümleştirmesi gibi IDE içindeki diğer tüm işlevlere sahip için benzersiz bir deneyim sağlar.

Bu makalede, bazı kaynak Düzenleyicisi anahtar özelliklerini tanıtır ve mümkün olduğunca fazla verimli olması için Mac için Visual Studio nasıl kullanabileceğinizi keşfediyor.

## <a name="the-source-editor-experience"></a>Kaynak Düzenleyicisi deneyimi

Görüntüleme ve verimli bir şekilde kodunuzda taşıma geliştirme iş akışı önemli bir parçasıdır. Tam olarak nasıl görüntülemek ve geliştiricilerin - ve genellikle projeler arasında değişen bir kişisel karar kod korumak karar.

Mac için Visual Studio'nun platformlar arası geliştirme erişilebilir ve kadar kullanışlı hale getirmek için çok sayıda güçlü özellikler sunar. Aşağıdaki bölümlerde, önemli noktalardan bazıları açıklanmaktadır.

## <a name="code-folding"></a>Kod Katlama

Kod katlamayı büyük kaynak kodu dosyaları göster veya gizle tam yönergeleri, ortak kod ve açıklamalar ve #region deyimleri kullanma gibi kod bölümlerini geliştiricilerin vererek yönetmenizi kolaylaştırır. Kod katlamayı Visual Studio'da varsayılan olarak Mac için devre dışı

Kod katlamayı üzerinde etkinleştirmek için gidin **Visual Studio > Tercihler > Metin Düzenleyicisi > Genel > kod Katlama**:

![Kod Katlama Seçenekleri](media/source-editor-image1.png)

Bu menü seçeneği #regions ve açıklamalar, kod yerine adlandırılmış bir ipucu görüntüleyen varsayılan olarak katlamak için de içerir.

Göstermek veya gizlemek bölümleri için satır numarası yanındaki açıklama pencere öğesini kullanın:

![Gösterme veya gizleme kod olarak bölümlerde](media/source-editor-image2.png)

Kullanarak büyük Katlama gizleme ve gösterilmesi arasında geçiş yapabilirsiniz **Görüntüle > Katlama > Aç/Kapat Katlama / tüm büyük Katlama geçiş** menü öğesi:

![Menü öğesi Katlama](media/source-editor-image19.png)

Bu menü öğesi, etkinleştirme veya devre dışı kod katlamayı de kullanılabilir.

## <a name="white-space"></a>Boşluk

Görünmez karakterler kaynak kodunda görüntülemeniz için gerekli olabilir. Kod standartlarımız, koda ve gereksiz yere değil yer harcama bağlılığı emin olmak için görünür bir yoludur. Ayrıca yazarken kullanışlıdır F#, kod değerlendirmek için tam olarak girintili satırlarına bağlıdır.

Boşluk giderek göstermek için seçenekleri ayarlayın **Visual Studio > Tercihler > Metin Düzenleyicisi > işaretleyiciler ve Cetveller**. Bu seçenek olanak ayarı _olduğunda_ görünmez karakterler gösterilir: hiçbir zaman seçimde veya her zaman:

![Görünmez karakterler seçeneklerini göster](media/source-editor-image3.png)

Sekmeler, boşluk ve satır sonlarını göstermek için bir seçenek de kullanılabilir:

![Sekmeler ve alanları göster](media/source-editor-image4.png)

Görünmez karakterler gri noktalar, aşağıdaki görüntüde gösterildiği gibi görüntülenir:

![Görüntülenen boşluk](media/source-editor-image22.png)

## <a name="ruler"></a>Cetvel

Sütun cetvelini özellikle satır uzunluğu yönergeleri içeren bir ekip çalışırken satır uzunluğu belirlemek için yararlıdır. Sütun cetvelini açıp giderek kapatılabilir **Visual Studio > Tercihler > Metin Düzenleyicisi > işaretleyiciler ve Cetveller** seçerek (veya seçimini) **Göster sütun cetvelini**de gösterildiği gibi Aşağıdaki görüntüde:

!["Show sütun cetvelini vurgulanmış" ile Tercihler iletişim kutusu](media/source-editor-image5.png)

 Bu, kaynak düzenleyicisinde dikey açık gri çizgi olarak görüntüler.

## <a name="highlight-identifier-references"></a>Tanımlayıcı başvurularını vurgulamak

Başvurularıyla"seçeneğinin etkin vurgulama tanımlayıcı", kaynak kodunda herhangi bir sembol seçebilirsiniz ve o dosyadaki tüm diğer başvurular için görsel bir kılavuz Kaynak Düzenleyicisi sağlar. Bu seçeneği etkinleştirmek için şuraya gidin: **Visual Studio > Tercihler > Metin Düzenleyicisi > işaretleyiciler ve Cetveller** seçip _tanımlayıcı başvurularını vurgulamak_aşağıdaki görüntüde gösterildiği gibi:

!["Vurgulanmış tanımlayıcı başvuruları Vurgula" ile Tercihler iletişim kutusu](media/source-editor-image6.png)

Vurgu rengi de bir atanan veya başvurulan belirten için yararlıdır. Bir şey atanırsa kırmızıyla vurgulanır. başvuru, mavi renkle vurgulanır:

![Örnek gösteren Vurgu rengi](media/source-editor-image7.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Düzenleyicisi'ni (Windows için Visual Studio) özellikleri](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Anahat oluşturma (Windows için Visual Studio)](/visualstudio/ide/outlining)