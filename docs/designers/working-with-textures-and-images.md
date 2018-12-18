---
title: Dokularla ve Görüntülerle Çalışma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb7cc97a797d02bd8353cbcfb19af6b8f9edf674
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079666"
---
# <a name="work-with-textures-and-images"></a>Dokularla ve görüntülerle çalışma

Dokuları ve görüntüleri oluşturmak ve değiştirmek için Visual Studio görüntü Düzenleyicisi kullanabilirsiniz. Resim Düzenleyicisi, DirectX uygulaması geliştirmede kullanılan olanlar gibi zengin doku ve resim biçimleri destekler.

> [!NOTE]
> Resim Düzenleyicisi simgeleri veya işaretçiler gibi düşük Renk görüntülerini desteklemiyor. Oluşturun veya bu tür görüntülerini değiştirmek için kullanın [(C++) simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons).

## <a name="textures-and-images"></a>Dokularla ve görüntülerle

Dokularla ve görüntülerle, temel düzeyde, yalnızca tablolar Grafik uygulamalarında visual ayrıntı sağlamak için kullanılan veri var. Nasıl kullanıldığına bağlı bir dokuyu veya görüntü sağlayan ayrıntı türüne bağlıdır, ancak rengi örnekleri, alfa (saydam) değerlerini, yüzey için normal değerler ve yükseklik değerlerini ortak örnek verilebilir. Bir doku şekli gösterimi ile birlikte kullanılmak üzere tasarlanmıştır doku ve resim arasındaki birincil fark olduğu — genellikle bir 3B modeli — tam bir nesneyi veya Sahneyi, ancak görüntü ifade etmek için genellikle bir tek başına bir nesneyi veya Sahneyi gösterimidir.

Herhangi bir dokuya kodlanmış ve işlenemez veya bir doku tutan bir veri türü dikgen çeşitli yollarla veya doku "şekline" sıkıştırılmış. Ancak farklı kodlama ve sıkıştırma yöntemleri farklı türde veriler için daha iyi sonuçlar verecek.

Dokuları ve resimleri diğer görüntü Düzenleyicisi benzer şekilde oluşturma ve değiştirme için görüntü Düzenleyicisi'ni kullanabilirsiniz. Resim Düzenleyicisi'ni de 3B grafik ile kullanım için mipmap oluşturma ve diğer özellikleri sağlar ve DirectX destekleyen yüksek oranda sıkıştırılmış, Donanım hızlandırmalı doku biçimlerini çoğunu destekler.

Ortak tür dokular şunlardır:

### <a name="texture-maps"></a>Doku eşlemi

Doku eşlemelerine bir bir, iki veya üç boyutlu bir matris düzenlenmiştir renk değerleri içerir. Etkilenen nesne üzerinde renk ayrıntısını sağlamak için kullanılır. Renkler (kırmızı, yeşil, mavi) RGB renk kanallarını kullanarak yaygın olarak kodlanır ve dördüncü içerebilir saydamlık temsil eden kanal, alfa,. Daha az yaygın olarak, renkler başka bir renk düzeninde kodlanmış veya dördüncü kanal alfa dışındaki veriler içerebilir — Örneğin, yükseklik.

### <a name="normal-maps"></a>Normal haritalar

Normal haritalar yüzeyi için normal değerler içerir. Etkilenen nesne üzerinde aydınlatma ayrıntı sağlamak için kullanılır. İçin normal değerler, x, y ve z boyutları vektör depolamak için kırmızı, yeşil ve mavi renk bileşenlerine kullanılarak yaygın olarak kodlanır. Ancak, diğer kodlamaları vardır — örneğin, Kutupsal koordinatlarına göre Kodlamalar.

### <a name="height-maps"></a>Yükseklik eşlemeleri

Yükseklik haritalar yükseklik alanı verileri içerir. Etkilenen nesne üzerinde bir form geometrik ayrıntı sağlamak için kullanılan — istenen efekti için gölgelendirici kodu kullanarak — veya Arazi oluşturma gibi kullanımlar için veri noktaları sağlamak için. Yükseklik değerlerini, dokudaki bir kanalı kullanılarak yaygın olarak kodlanır.

### <a name="cube-maps"></a>Küp eşler

Küp eşlemlerinin farklı veri türleri içerebilir — Örneğin, renkleri veya normal değerler — ancak bir küp yüzleri altı doku düzenlenir. Bu nedenle, doku koordinatları sağlanarak küp eşlemlerinin örneklenen değil, ancak bir vektör sağlanarak, Kaynak küpü merkezidir; Örnek vektör küp kesiştiği noktada alınır. Küp eşlemlerinin yansımaları hesaplamak için kullanılan ortam yaklaşık sağlamak için kullanılır; bu olarak bilinir *ortam eşleme*— veya küresel nesnelere doku temel, daha az bozulma sağlamak için iki boyutlu dokuları sağlayabilir.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Görüntü Düzenleyicisi](../designers/image-editor.md)|Dokularla ve görüntülerle çalışma için görüntü Düzenleyicisi'ni kullanmayı açıklar.|
|[Görüntü Düzenleyicisi örnekleri](../designers/image-editor-examples.md)|Resim Düzenleyicisi ortak görüntü işleme görevlerini gerçekleştirmek için nasıl kullanılacağını gösteren konulara bağlantılar sağlar.|