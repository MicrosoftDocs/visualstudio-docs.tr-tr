---
title: Hata ayıklayıcıda değişkenler için belleği görüntüleme | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdf8e5fc5ee0ac34b4c295f6cc593e0a93b548ae
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257270"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio hata ayıklayıcısında bellek windows kullanın (C#, C++, Visual Basic F#)

Hata ayıklama sırasında **bellek** penceresi uygulamanızı kullanarak bellek alanını gösterir. 

Hata ayıklayıcısı pencereleri gibi **Watch**, **Otolar**, **Yereller**ve **QuickWatch** iletişim belirli depolanan değişkenleri Göster Bellekteki konumu. **Bellek** penceresi genel resmi gösterir. Bellek görünümü, büyük (arabellek veya örneğin, büyük dizelerin) de diğer pencerelerinde görüntüleme veri parçaları incelemek için uygundur. 

**Bellek** penceresi verileri görüntülemek için sınırlı değildir. Bu her şeyi veriler, kod ve çöp rastgele bitlerini atanmamış bellekte dahil bellek alanını görüntüler.  

**Bellek** penceresi değildir komut dosyası veya SQL hata ayıklama için kullanılabilir. Bu diller bellek kavramını tanımıyoruz.  
  
## <a name="open-a-memory-window"></a>Bellek penceresi açın  
  
Diğer hata ayıklayıcı pencereleri gibi **bellek** windows yalnızca hata ayıklama oturumu sırasında kullanılabilir. 

>[!IMPORTANT]
>Etkinleştirmek için **bellek** windows **adres seviyesinde hata ayıklamayı** seçilmelidir **Araçları** > **seçenekleri** (veya **Hata ayıklama** > **seçenekleri**) > **hata ayıklama** > **genel**. 

**Bellek penceresi açmak için**
  
1. Emin **adres seviyesinde hata ayıklamayı** seçili **Araçları** > **seçenekleri** (veya **hata ayıklama**  >  **Seçenekleri**) > **hata ayıklama** > **genel**. 
   
1. Yeşil bir ok seçerek hata ayıklamayı Başlat tuşuna basarak **F5**, veya seçerek **hata ayıklama** > **hata ayıklamayı Başlat**.  
   
2. Altında **hata ayıklama** > **Windows** > **bellek**seçin **bellek 1**, **bellek2**, **Bellek 3**, veya **bellek 4**. (Bazı sürümlerinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yalnızca bir teklif **bellek** penceresi.)  

## <a name="move-around-in-the-memory-window"></a>Bellek penceresinde gezinme  

Bir bilgisayarın adres alanı büyük ve kaydırma tarafından yerinizi kolayca kaybedebilir **bellek** penceresi. 

Daha yüksek bellek adresleri penceresinin altında görünür. Daha yüksek bir adresi görüntülemek için aşağı kaydırın. Daha düşük bir adresini görüntülemek üzere yukarı doğru ilerleyin.  

Belirtilen bir adrese anında gidebilirsiniz **bellek** penceresi sürükle ve bırak özelliğini kullanarak veya adresini girerek **adresi** alan. **Adresi** alan alfasayısal adresleri ve adreslerine gibi değerlendirilen ifadeleri kabul `e.User.NonroamableId`. 

İçindeki ifadenin hemen yeniden değerlendirmeyi zorlamak için **adresi** yuvarlatılmış oku seçin, alan **otomatik olarak yeniden değerlendir** simgesi. 

Varsayılan olarak, **bellek** penceresi işler **adresi** ifadeleri uygulama çalışırken tekrar değerlendirilir Canlı ifadeleri olarak. Örneğin, Canlı ifadeler tarafından işaretçi değişkeninin dokunulan bellek görüntülemek için yararlı olabilir.  

**Sürükle ve bırak bir bellek konumuna taşımak için için:**  
   
1. Hata ayıklayıcı penceresinde herhangi bir bellek adresi ya da bir bellek adresi içeren bir işaretçi değişkeni seçin.  
   
2. Adres veya işaretçiyi sürükleyip **bellek** penceresi. Bu adres sonra görünür **adresi** alan ve **bellek** penceresini ayarlar bu adrese üstünde görüntülenecek. 
  
**Adres alanında girerek bir bellek konumuna taşımak için:**
  
- Adres veya ifadenin yapıştırın veya yazın **adresi** alan ve ENTER tuşuna **Enter**, veya açılır menüden arasından **adresi** alan. **Bellek** penceresini ayarlar bu adrese üstünde görüntülenecek.
  
## <a name="customize-the-memory-window"></a>Bellek penceresini özelleştirme 

Varsayılan olarak, bellek içeriğini 1 baytlık tamsayı olarak onaltılık biçimde görünür ve sütunların gösterilen penceresi genişliğini belirler. Şeklini özelleştirebilir **bellek** penceresi bellek içeriğini gösterir.  
  
**Bellek içeriği biçimini değiştirmek için:**  
  
-  Sağ **bellek** penceresinde ve bağlam menüsünden istediğiniz biçimleri seçin.  
  
**Bellek penceresi sütun sayısını değiştirmek için:**
  
- Açılan menü okunu seçin **sütunları** alan ve görüntülemek veya seçmek için sütun sayısını seçin **otomatik** penceresi genişliği üzerinde göre otomatik ayarlama.  
  
İçeriğini istemiyorsanız **bellek** uygulamanızı değiştirmek için pencere çalıştırır, Canlı ifade değerlendirmesi kapatabilirsiniz. 

**Canlı değerlendirme açıp kapatmak için:**  
  
- Sağ **bellek** penceresi ve select **otomatik olarak yeniden değerlendir** bağlam menüsünde. 

  >[!NOTE]
  >Canlı ifade değerlendirme bir geçiş olduğunu ve varsayılan olarak, bu nedenle seçerek **otomatik olarak yeniden değerlendir** devre dışı bırakır. Seçme **otomatik olarak yeniden değerlendir** yeniden açar yeniden açın. 
  
Gizleme veya en üstündeki araç çubuğunu görüntüleme **bellek** penceresi. İçin erişebilir değil **adresi** alan veya araç gizlenen diğer araçlar.  
  
**Araç çubuğunun görünümünü açıp kapatmak için:**  
  
- Sağ **bellek** penceresi ve select **araç çubuğunu göster** bağlam menüsünde. Araç çubuğu, önceki durumuna bağlı olarak kaybolur ya da görünür.  
  
## <a name="follow-a-pointer-through-memory"></a>Bellek işaretçiyle izleyin  

Yerel kod uygulamalarda live ifadeleri yazmaç adlarını kullanabilirsiniz. Örneğin, yığın işaretçisi, yığın izlemek için kullanabilirsiniz.  
  
**Bellek işaretçiyle izlemek için:**
  
1. İçinde **bellek** penceresi **adresi** geçerli kapsamda olan bir işaretçi ifadesi girin. Dile bağlı olarak, bu başvuru gerekebilir.  
  
2. Tuşuna **girin**.  
   
   Kullanırken bir hata ayıklama komutu gibi **adım**, görüntülenen bellek adresi **adresi** alan ve en üstündeki **bellek** penceresi otomatik olarak bir işaretçi olarak değiştirir değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklayıcı görünümü verileri](../debugger/viewing-data-in-the-debugger.md)