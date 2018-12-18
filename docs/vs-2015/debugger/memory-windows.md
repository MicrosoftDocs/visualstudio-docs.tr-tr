---
title: Bellek Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.memory
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 704c0ff20dbd11b4640b2d81670a4cdeaf3f1ea0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724249"
---
# <a name="memory-windows"></a>Bellek Pencereleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Bellek** penceresi, uygulamanız tarafından kullanılan bellek alanını bir görünüm sağlar. **Watch** penceresinde **QuickWatch** iletişim kutusu, **Otolar** penceresinde ve **Yereller** penceresi olan değişken içeriğini göster bellekte belirli konumlara depolanır. Ancak **bellek** penceresi büyük ölçekli resmi gösterir. Bu görünüm, büyük (arabellek veya örneğin, büyük dizelerin) de diğer pencerelerinde görüntüleme veri parçaları incelemek için kullanışlı olabilir. Ancak, **bellek** penceresi verileri görüntülemek için sınırlı değildir. İçerik verileri, kod veya Çöp rastgele bitlerini atanmamış bellek olup olmadığını her şeyi bellek alanı görüntüler.  
  
 **Bellek** pencere, yalnızca adres seviyesinde hata ayıklamayı etkin değilse kullanılabilir **seçenekleri** iletişim kutusu,**hata ayıklama** düğümü. **Bellek** penceresini komut dosyası veya SQL, bellek kavramını tanımaz diller için kullanılabilir değil.  
  
## <a name="opening-a-memory-window"></a>Bir bellek penceresini açma  
  
#### <a name="to-open-a-memory-window"></a>Bellek penceresi açmak için  
  
1.  Değil zaten hata ayıklama modunda iseniz hata ayıklamayı başlatın.  
  
2.  İçinde **hata ayıklama** menüsünde **Windows**. Ardından, fareyle **bellek** ve ardından **bellek 1**, **bellek 2**, **bellek 3**, veya **bellek 4**. (Alt düzey sürümleri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yalnızca tek bir **bellek** penceresi. Bu sürümlerinden birini kullanıyorsanız, tıklamanız **bellek**.)  
  
## <a name="paging-in-the-memory-window"></a>Bellek penceresi disk belleği  
 **Bellek** penceresine standart olmayan bir şekilde çalışır. dikey bir kaydırma çubuğuna sahip. Çok büyük modern bir bilgisayarın adres alanı ve, kolayca kaydırma çubuğunun Kaydırma kutusu yazılımdır ve rastgele bir konuma sürükleyerek kayıp. Bu nedenle thumb "üzerinde" ve her zaman kaydırma çubuğunu Merkezi'nde kalır. Yerel kod uygulamalarında yukarı veya aşağı sayfa ancak hakkında ücretsiz kaydırma yapılamıyor.  
  
 Daha yüksek bellek adresleri penceresinin altında görünür. Daha yüksek bir adresi görüntülemek için en fazla değil kaydırın.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Yukarı veya aşağı bellekte sayfa için  
  
1.  Dikey kaydırma çubuğu'nda thumb altında page DOWN (daha yüksek bir bellek adresi taşıma) için tıklayın.  
  
2.  (Daha düşük bir bellek adresi taşıma) ayarlama sayfası için thumb dikey kaydırma çubuğu'a tıklayın.  
  
## <a name="selecting-a-memory-location"></a>Bellek konumu seçme  
 Anında bellekte seçili bir konuma taşımak istiyorsanız, bir Sürükle ve bırak işlemi kullanarak veya değer düzenleyerek bunu yapabilirsiniz **adresi** kutusu. **Adresi** kutusu yalnızca sayısal değerler aynı zamanda adreslere değerlendirilen ifadeleri kabul eder. Varsayılan olarak, **bellek** penceresi değerlendirir bir **adresi** ifade olarak değerlendirilir, program yürütme sırasında dinamik bir ifade. Dinamik ifadeler çok kullanışlı olabilir. Örneğin, bir işaretçi tarafından dokunulan bellek görüntülemek için bunları kullanabilirsiniz.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Sürükleme ve bırakma bellek konumu seçmek için  
  
1.  Herhangi bir pencerede bir bellek adresi içeren bir bellek adresi ya da işaretçi değişkeni seçin.  
  
2.  Adres veya işaretçi sürükleyin **bellek** penceresi.  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Düzenleyerek bir bellek konumu seçmek için  
  
1.  İçinde **bellek** penceresinde **adresi** kutusu.  
  
2.  Ardından basın ve istediğiniz adresini yazın veya yapıştırın **ENTER**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Bilgileri bellek penceresini görüntüler biçimini değiştirme  
 Şeklini özelleştirebilir **bellek** penceresi bellek içeriğini gösterir. Varsayılan olarak, bellek içeriğini tek baytlık tamsayı olarak onaltılık biçimde görünür ve sütun sayısı geçerli pencerenin genişliğini tarafından otomatik olarak belirlenir.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Bellek içeriği biçimini değiştirmek için  
  
1.  Sağ **bellek** penceresi.  
  
2.  İstediğiniz biçimi seçin.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Bellek penceresi sütun sayısını değiştirmek için  
  
1. Üst kısmındaki araç çubuğunda **bellek** penceresinde bulun **sütunları** listesi.  
  
2. İçinde **sütunları** listesinde, görüntülemek veya seçmek istediğiniz sütun sayısını seçin **otomatik** penceresi genişliğine sığacak şekilde otomatik ayarlama.  
  
   İçeriğini istemiyorsanız **bellek** programınızı değiştirmek için pencere yürütür, Canlı ifade değerlendirmesi kapatabilirsiniz.  
  
#### <a name="to-toggle-live-evaluation"></a>Canlı değerlendirme açıp kapatmak için  
  
1. Sağ **bellek** penceresi.  
  
2. Kısayol menüsünde **otomatik olarak yeniden değerlendir**.  
  
    Canlı değerlendirme açıksa, seçeneğini seçtiyseniz ve tıklayarak Canlı değerlendirmeyi devre dışı bırakır. Canlı değerlendirme devre dışıysa seçeneği seçili değilse ve canlı değerlendirmeye tıklayarak kapatır.  
  
   Gizleme veya en üstündeki araç çubuğunu görüntüleme **bellek** penceresi. Araç çubuğu gizli sürece kutusu veya diğer araçları yönelik erişim sahip.  
  
#### <a name="to-toggle-the-toolbar"></a>Araç çubuğunu değiştirme  
  
1.  Sağ bir **bellek** penceresi.  
  
2.  Kısayol menüsünde **araç çubuğunu göster**.  
  
     Araç çubuğu, önceki durumuna bağlı olarak kaybolur ya da görünür.  
  
## <a name="following-a-pointer-through-memory"></a>Bellek işaretçiyle aşağıdaki  
 Yerel kod uygulamalarda live ifadeleri yazmaç adlarını kullanabilirsiniz. Örneğin, yığın işaretçisi, yığın izlemek için kullanabilirsiniz.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Bellek işaretçiyle izlemek için  
  
1.  İçinde **bellek** penceresi **adresi** bir işaretçi ifadesi yazın. İşaretçi değişkeninin geçerli kapsamda olmalıdır. Dile bağlı olarak, bu başvuru gerekebilir.  
  
2.  Tuşuna **ENTER**.  
  
     Şimdi, kullanırken bir yürütme komutu gibi **adım**, görüntülenen adres bellek işaretçi değiştikçe otomatik olarak değiştirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)





