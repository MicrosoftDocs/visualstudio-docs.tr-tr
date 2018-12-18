---
title: Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
ms.assetid: 9fd0c9a2-d351-40c8-be88-0749788264bf
caps.latest.revision: 51
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: af5f34b307f94f1bae4c913421acbe0a934ed113
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743827"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod Haritaları, büyük kod tabanlarında, bilmediğiniz bir kodda veya eski kodda kafanız karışmadan önlemenize yardımcı olabilir. Örneğin, hata ayıklama işlemi yaparken birçok dosya ve proje arasında koda bakmanız gerekebilir. Kod parçaları gidin ve onlar arasındaki ilişkileri anlamak için kod haritalarını kullanma. Bu şekilde, bu kodu birikimine izlemek ya da ayrı bir şeklini çizmeniz gerekmez. Bu nedenle, çalışmanızı kesintiye uğradığında, bellek, üzerinde çalıştığınız kod hakkında Yardım yenileme kod eşlemeleri.  
  
 ![Kod Haritası &#45; koddaki ilişkileri eşleyin](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")  
  
 **İmleç Düzenleyicisi'nde göründüğü bir yeşil ok gösterir**  
  
 Komutlar ve kod haritaları ile çalışırken kullanabileceğiniz eylemler için bilgi [göz atma ve yeniden düzenleme kod eşlemeleri](../modeling/browse-and-rearrange-code-maps.md).  
  
## <a name="understand-the-problem"></a>Sorunu anlama  
 Üzerinde çalıştığınız bir çizim programında bir hata olduğunu varsayın. Hatayı yeniden oluşturmak için çözümü Visual Studio tuşuna açın ve **F5** hata ayıklama başlatılamıyor.  
  
 Ne zaman bir çizgi çizdiğinizde ve seçin **son vuruşumu Geri Al**, sonraki çizgiyi çizene kadar hiçbir şey olmaz.  
  
 ![Kod Haritası &#45; yineleme hata](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")  
  
 Arayarak incelemeye başlamak için `Undo` yöntemi. İçinde bulma `PaintCanvas` sınıfı.  
  
 ![Kod Haritası &#45; Bul kod](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")  
  
## <a name="start-mapping-the-code"></a>Kodu eşleştirmeyi başlat  
 Artık eşleştirmeyi Başlat `undo` yöntemi ve ilişkilerini. Kod Düzenleyicisi'nde, eklediğiniz `undo` yöntemini ve başvurduğu için yeni bir kod Haritası alanları. Yeni bir eşleme oluşturduğunuzda, kodun dizinini oluşturmak biraz zaman alabilir. Bu, sonraki işlemlerin daha hızlı çalışmasını sağlar.  
  
 ![Kod Haritası &#45; yöntemi ve ilgili alanları göster](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")  
  
> [!TIP]
>  Yeşil vurgu eşlemeye eklenen son öğeleri gösterir. Yeşil bir ok, imlecinizin koddaki konumunu gösterir. Öğeler arasındaki oklar farklı ilişkileri temsil eder. Harita üzerinde bunlar üzerinde fareyi hareket ve kendi araç ipuçlarını inceleyerek öğeler hakkında daha fazla bilgi alabilirsiniz.  
  
 ![Kod Haritası &#45; araç ipuçlarını göster](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")  
  
## <a name="navigate-and-examine-code-from-the-map"></a>Eşlemeden koda gitme ve kodu inceleme  
 Her alana ilişkin kod tanımını görmek için alana eşlemede çift tıklatın veya alanı seçip ENTER tuşuna **F12**. Yeşil ok eşlemedeki öğeler arasında hareket eder. Ayrıca kod düzenleyicisindeki imleciniz de otomatik olarak hareket eder.  
  
 ![Kod Haritası &#45; alan tanımı inceleyin](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")  
  
 ![Kod Haritası &#45; alan tanımı inceleyin](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")  
  
> [!TIP]
>  Kod düzenleyicisinde imleci hareket ettirerek yeşil oku eşlemede taşıyabilirsiniz.  
  
## <a name="understand-relationships-between-pieces-of-code"></a>Kod parçaları arasındaki ilişkileri anlama  
 Bilmek istediğiniz artık başka hangi kodun etkileşim `history` ve `paintObjects` alanları. Bu alanlara başvuran tüm yöntemleri eşlemeye ekleyebilirsiniz. Bunu eşlemeden veya kod düzenleyicisinden yapabilirsiniz.  
  
 ![Kod Haritası &#45; tüm başvuruları Bul](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")  
  
 ![Kod düzenleyiciden bir kod Haritası açın](../modeling/media/codemapstoryboardpaint6a.PNG "CodeMapStoryboardPaint6A")  
  
> [!NOTE]
>  Ardından Windows Phone veya Windows Store, gibi birden fazla uygulama arasında paylaşılan bir projeden öğeler eklediğinizde bu öğeler harita üzerinde şu anda etkin uygulama projesiyle olmadığını her zaman görünür. Harita üzerinde bağlamı için de değişir. daha sonra başka bir uygulama projesi bağlamı değiştirirseniz, bu nedenle, yeni öğeleri paylaşılan projeden eklenen tüm. Eşleme üzerinde bir öğeyle gerçekleştirdiğiniz işlemler, yalnızca aynı bağlamı paylaşılan öğeler için geçerlidir.  
  
 İlişkilerin akışını yeniden düzenlemek ve eşlemenin okunmasını kolaylaştırmak için düzeni değiştirin. Ayrıca, öğeleri sürükleyerek de eşleme etrafında taşıyabilirsiniz.  
  
 ![Kod Haritası &#45; düzenini değiştir](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")  
  
> [!TIP]
>  Varsayılan olarak, **artan düzen** açıktır. Yeni öğeler eklediğinizde, bu eşlemeyi mümkün olduğunca az yeniden düzenler. Yeni öğeler eklemek her zaman tüm eşlemeyi yeniden düzenlemek için devre dışı **artan düzen**.  
  
 ![Kod Haritası &#45; düzenini değiştir](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")  
  
 Bu yöntemleri inceleyelim. Harita üzerinde çift **PaintCanvas** yöntemi veya bu yöntemi seçip ENTER tuşuna **F12**. Bu yöntem oluşturduğunu öğrenin `history` ve `paintObjects` boş listeler olarak.  
  
 ![Kod Haritası &#45; yöntem tanımını incelemek](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")  
  
 Şimdi incelemek için aynı adımları tekrarlayarak `clear` yöntem tanımı. Öğrenirsiniz `clear` bazı görevleri gerçekleştiren `paintObjects` ve `history`. Ardından `Repaint` yöntemi.  
  
 ![Kod Haritası &#45; yöntem tanımını incelemek](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")  
  
 Şimdi `addPaintObject` yöntem tanımı. Ayrıca bazı görevleri gerçekleştiren `history` ve `paintObjects`. Aynı zamanda çağrı yaptığı `Repaint`.  
  
 ![Kod Haritası &#45; yöntem tanımını incelemek](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")  
  
## <a name="find-the-problem-by-examining-the-map"></a>Eşlemeyi inceleyerek sorunu bulma  
 Tüm yöntemleri değiştiren görünüyor `history` ve `paintObjects` çağrı `Repaint`. Henüz `undo` yöntemi çağırmaz `Repaint`rağmen `undo` aynı alanları değiştirir. Çağırarak bu sorunu düzeltebileceğinizi düşünüyorsunuz şekilde `Repaint` gelen `undo`.  
  
 ![Kod Haritası &#45; yöntemi çağrısı eksik Bul](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")  
  
 Size bu eksik çağrıyı gösteren bir eşlemeniz yoksa, özellikle de daha karmaşık kod söz konusu olduğunda bu sorunun bulunması daha zor olabilir.  
  
## <a name="share-your-discovery-and-next-steps"></a>Keşfinizi ve sonraki adımları paylaşma  
 Siz veya başka biri bu hatayı düzeltmeden önce, eşlemenin üzerine sorunla ve bu sorunun düzeltilmesiyle ilgili notlar ekleyebilirsiniz.  
  
 ![Kod Haritası &#45; izleme için yorum ve bayrağı öğeleri](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")  
  
 Örneğin, eşlemeye açıklamalar ekleyebilir ve renkler kullanarak öğeleri işaretleyebilirsiniz.  
  
 ![Kod Haritası &#45; açıklamalı ve işaretli öğeleri](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")  
  
 Microsoft Outlook yüklüyse, eşlemeyi başkalarına e-postayla gönderebilirsiniz. Eşlemeyi bir görüntü veya başka bir biçim olarak dışarı da aktarabilirsiniz.  
  
 ![Kod Haritası &#45; paylaşımı, dışarı aktarma, posta](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")  
  
## <a name="fix-the-problem-and-show-what-you-did"></a>Sorunu giderme ve ne yaptığınızı gösterme  
 Bu hatayı düzeltmek için arama için ekleme `Repaint` için `undo`.  
  
 ![Kod Haritası &#45; eksik yöntem çağrısını ekleyin](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")  
  
 Düzeltmenizi onaylamak için hata ayıklama oturumunu yeniden başlatır ve hatayı yeniden oluşturmaya çalışırsınız. Şimdi **son vuruşumu Geri Al** beklediğiniz gibi çalışır ve doğru düzeltmeyi yaptığınızı onaylar.  
  
 ![Kod Haritası &#45; Onayla kod düzeltme](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")  
  
 Eşlemeyi yaptığınız düzeltmeyi gösterecek şekilde güncelleştirebilirsiniz.  
  
 ![Kod Haritası &#45; yöntem çağrısı eksik olan güncelleştirme eşlemesi](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")  
  
 Haritanız artık arasında bir bağlantı gösterir **geri** ve **Repaint**.  
  
 ![Kod Haritası &#45; güncelleştirilmiş harita yöntemi çağrısıyla](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")  
  
> [!NOTE]
>  Eşlemeyi güncelleştirdiğinizde, eşlemeyi oluşturmak için kullanılan kod dizininin güncelleştirdiğini belirten bir ileti görebilirsiniz. Bu, birisinin kodu eşlemenizin geçerli kodla eşleşmemesine neden olacak şekilde değiştirdiği anlamına gelir. Bu sizi eşlemeyi güncelleştirmekten alıkoymaz, ancak kodla eşleştiğini doğrulamak için eşlemeyi yeniden oluşturmak zorunda kalabilirsiniz.  
  
 Artık araştırmanızı bitirdiniz. Kodu eşleştirerek sorunu başarıyla buldunuz ve giderdiniz. Ayrıca kodda gezinmeye ve öğrendiklerinizi hatırlamanıza yardımcı olan ve sorunu gidermek için attığınız adımları gösteren bir eşlemeniz de vardır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklarken çağrı yığınında yöntemler eşleştirme](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)   
 [Kodu görselleştirme](../modeling/visualize-code.md)



