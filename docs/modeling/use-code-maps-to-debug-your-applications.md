---
title: Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 838bf3cab092106140f3aeeaf33c74a13cd23b35
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859672"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma

Kod Haritaları, büyük kod tabanlarında, bilmediğiniz bir kodda veya eski kodda kafanız karışmadan önlemenize yardımcı olabilir. Örneğin, hata ayıklama işlemi yaparken birçok dosya ve proje arasında koda göz atmak zorunda kalabilirsiniz. Kod parçaları gidin ve onlar arasındaki ilişkileri anlamak için kod haritalarını kullanma. Bu şekilde, bu kodu birikimine izlemek ya da ayrı bir şeklini çizmeniz gerekmez. Bu nedenle, çalışmanızı kesintiye uğradığında, bellek, üzerinde çalıştığınız kod hakkında Yardım yenileme kod eşlemeleri.

![Kod Haritası &#45; koddaki ilişkileri eşleme](../modeling/media/codemapstoryboardpaint.png)

**İmleç Düzenleyicisi'nde göründüğü bir yeşil ok gösterir**

Komutlar ve kod haritaları ile çalışırken kullanabileceğiniz eylemler için bilgi [göz atma ve yeniden düzenleme kod eşlemeleri](../modeling/browse-and-rearrange-code-maps.md).

> [!NOTE]
> Oluşturma ve kod haritaları düzenlemek için Visual Studio Enterprise edition gerekiyor. Visual Studio Community ve Professional sürümleri için Enterprise sürümünde oluşturulan şemaları açabilir, ancak onları düzenleyemezsiniz.

## <a name="understand-the-problem"></a>Sorunu anlama
 Üzerinde çalıştığınız bir çizim programında bir hata olduğunu varsayın. Hatayı yeniden oluşturmak için çözümü Visual Studio tuşuna açın ve **F5** hata ayıklama başlatılamıyor.

 Ne zaman bir çizgi çizdiğinizde ve seçin **son vuruşumu Geri Al**, sonraki çizgiyi çizene kadar hiçbir şey olmaz.

 ![Kod Haritası &#45; yineleme hata](../modeling/media/codemapstoryboardpaint0.png)

 Arayarak incelemeye başlamak için `Undo` yöntemi. İçinde bulma `PaintCanvas` sınıfı.

 ![Kod Haritası &#45; kod bulma](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Kodu eşleştirmeyi başlat
 Artık eşleştirmeyi Başlat `undo` yöntemi ve ilişkilerini. Kod Düzenleyicisi'nde, eklediğiniz `undo` yöntemini ve başvurduğu için yeni bir kod Haritası alanları. Yeni bir eşleme oluşturduğunuzda, kodun dizinini oluşturmak biraz zaman alabilir. Bu, sonraki işlemlerin daha hızlı çalışmasını sağlar.

 ![Kod Haritası &#45; yöntemi ve ilgili alanları göster](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> Yeşil vurgu eşlemeye eklenen son öğeleri gösterir. Yeşil ok, imlecinizin koddaki konumunu gösterir. Öğeler arasındaki oklar farklı ilişkileri temsil eder. Harita üzerinde bunlar üzerinde fareyi hareket ve kendi araç ipuçlarını inceleyerek öğeler hakkında daha fazla bilgi alabilirsiniz.

 ![Kod Haritası &#45; araç ipuçlarını göster](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Eşlemeden koda gitme ve kodu inceleme
 Her alana ilişkin kod tanımını görmek için alana eşlemede çift tıklatın veya alanı seçip ENTER tuşuna **F12**. Yeşil ok eşlemedeki öğeler arasında hareket eder. Ayrıca kod düzenleyicisindeki imleciniz de otomatik olarak hareket eder.

 ![Kod Haritası &#45; alan tanımı inceleyin](../modeling/media/codemapstoryboardpaint5.png)

 ![Kod Haritası &#45; alan tanımı inceleyin](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> Kod düzenleyicisinde imleci hareket ettirerek yeşil oku eşlemede taşıyabilirsiniz.

## <a name="understand-relationships-between-pieces-of-code"></a>Kod parçaları arasındaki ilişkileri anlama
 Bilmek istediğiniz artık başka hangi kodun etkileşim `history` ve `paintObjects` alanları. Bu alanlara başvuran tüm yöntemleri eşlemeye ekleyebilirsiniz. Bunu eşlemeden veya kod düzenleyicisinden yapabilirsiniz.

 ![Kod Haritası &#45; tüm başvuruları Bul](../modeling/media/codemapstoryboardpaint6.png)

 ![Kod düzenleyiciden bir kod Haritası açın](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Ardından Windows Phone veya Windows Store, gibi birden fazla uygulama arasında paylaşılan bir projeden öğeler eklediğinizde bu öğeler harita üzerinde şu anda etkin uygulama projesiyle olmadığını her zaman görünür. Harita üzerinde bağlamı için de değişir. daha sonra başka bir uygulama projesi bağlamı değiştirirseniz, bu nedenle, yeni öğeleri paylaşılan projeden eklenen tüm. Eşleme üzerinde bir öğeyle gerçekleştirdiğiniz işlemler, yalnızca aynı bağlamı paylaşılan öğeler için geçerlidir.

 İlişkilerin akışını yeniden düzenlemek ve eşlemenin okunmasını kolaylaştırmak için düzeni değiştirin. Ayrıca, öğeleri sürükleyerek de eşleme etrafında taşıyabilirsiniz.

 ![Kod Haritası &#45; Düzeni Değiştir](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> Varsayılan olarak, **artan düzen** açıktır. Yeni öğeler eklediğinizde, bu eşlemeyi mümkün olduğunca az yeniden düzenler. Yeni öğeler eklemek her zaman tüm eşlemeyi yeniden düzenlemek için devre dışı **artan düzen**.

 ![Kod Haritası &#45; Düzeni Değiştir](../modeling/media/codemapstoryboardpaint7.png)

 Bu yöntemleri inceleyelim. Harita üzerinde çift **PaintCanvas** yöntemi veya bu yöntemi seçip ENTER tuşuna **F12**. Bu yöntem oluşturduğunu öğrenin `history` ve `paintObjects` boş listeler olarak.

 ![Kod Haritası &#45; yöntem tanımını inceleyin](../modeling/media/codemapstoryboardpaint8.png)

 Şimdi incelemek için aynı adımları tekrarlayarak `clear` yöntem tanımı. Öğrenirsiniz `clear` bazı görevleri gerçekleştiren `paintObjects` ve `history`. Ardından `Repaint` yöntemi.

 ![Kod Haritası &#45; yöntem tanımını inceleyin](../modeling/media/codemapstoryboardpaint9.png)

 Şimdi `addPaintObject` yöntem tanımı. Ayrıca bazı görevleri gerçekleştiren `history` ve `paintObjects`. Aynı zamanda çağrı yaptığı `Repaint`.

 ![Kod Haritası &#45; yöntem tanımını inceleyin](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Eşlemeyi inceleyerek sorunu bulma
 Tüm yöntemleri değiştiren görünüyor `history` ve `paintObjects` çağrı `Repaint`. Henüz `undo` yöntemi çağırmaz `Repaint`rağmen `undo` aynı alanları değiştirir. Çağırarak bu sorunu düzeltebileceğinizi düşünüyorsunuz şekilde `Repaint` gelen `undo`.

 ![Kod Haritası &#45; yöntemi çağrısı eksik Bul](../modeling/media/codemapstoryboardpaint11.png)

 Size bu eksik çağrıyı gösteren bir eşlemeniz yoksa, özellikle de daha karmaşık kod söz konusu olduğunda bu sorunun bulunması daha zor olabilir.

## <a name="share-your-discovery-and-next-steps"></a>Keşfinizi ve sonraki adımları paylaşma
 Siz veya başka biri bu hatayı düzeltmeden önce, eşlemenin üzerine sorunla ve bu sorunun düzeltilmesiyle ilgili notlar ekleyebilirsiniz.

 ![Kod Haritası &#45; yorum ve bayrağı öğelerini izleme](../modeling/media/codemapstoryboardpaint12.png)

 Örneğin, eşlemeye açıklamalar ekleyebilir ve renkler kullanarak öğeleri işaretleyebilirsiniz.

 ![Kod Haritası &#45; açıklamalı ve bayrak eklenen öğeler](../modeling/media/codemapstoryboardpaint12a.png)

 Microsoft Outlook yüklüyse, eşlemeyi başkalarına e-postayla gönderebilirsiniz. Eşlemeyi bir görüntü veya başka bir biçim olarak dışarı da aktarabilirsiniz.

 ![Kod Haritası &#45; paylaşımı, dışarı aktarma, posta](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Sorunu giderme ve ne yaptığınızı gösterme
 Bu hatayı düzeltmek için arama için ekleme `Repaint` için `undo`.

 ![Kod Haritası &#45; eksik yöntem çağrısını ekleyin](../modeling/media/codemapstoryboardpaint14.png)

 Düzeltmenizi onaylamak için hata ayıklama oturumunu yeniden başlatır ve hatayı yeniden oluşturmaya çalışırsınız. Şimdi **son vuruşumu Geri Al** beklediğiniz gibi çalışır ve doğru düzeltmeyi yaptığınızı onaylar.

 ![Kod Haritası &#45; Onayla kod düzeltmesi](../modeling/media/codemapstoryboardpaint15.png)

 Eşlemeyi yaptığınız düzeltmeyi gösterecek şekilde güncelleştirebilirsiniz.

 ![Kod Haritası &#45; yöntem çağrısı eksik olan güncelleştirme eşlemesi](../modeling/media/codemapstoryboardpaint16.png)

 Haritanız artık arasında bir bağlantı gösterir **geri** ve **Repaint**.

 ![Kod Haritası &#45; güncelleştirilmiş harita yöntemi çağrısı ile](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Eşlemeyi güncelleştirdiğinizde, eşlemeyi oluşturmak için kullanılan kod dizininin güncelleştirdiğini belirten bir ileti görebilirsiniz. Bu, birisinin kodu eşlemenizin geçerli kodla eşleşmemesine neden olacak şekilde değiştirdiği anlamına gelir. Bu sizi eşlemeyi güncelleştirmekten alıkoymaz, ancak kodla eşleştiğini doğrulamak için eşlemeyi yeniden oluşturmak zorunda kalabilirsiniz.

 Artık araştırmanızı bitirdiniz. Kodu eşleştirerek sorunu başarıyla buldunuz ve giderdiniz. Ayrıca kodda gezinmeye ve öğrendiklerinizi hatırlamanıza yardımcı olan ve sorunu gidermek için attığınız adımları gösteren bir eşlemeniz de vardır.

## <a name="see-also"></a>Ayrıca Bkz.

- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Kodu görselleştirme](../modeling/visualize-code.md)
