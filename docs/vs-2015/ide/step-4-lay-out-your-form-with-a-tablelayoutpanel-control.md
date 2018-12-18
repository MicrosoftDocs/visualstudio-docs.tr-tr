---
title: '4. adım: TableLayoutPanel denetimi ile formunuzu | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4a08359c11fa45c87c787a5a3a414eb8515e7473
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210105"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>4. Adım: TableLayoutPanel Denetimi ile Formunuzu Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu adımda eklediğiniz bir `TableLayoutPanel` form denetimi. TableLayoutPanel, özel olarak daha sonra ekleyeceksiniz formda denetimleri düzgün şekilde hizalamaya yardımcı olur.  
  
 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo")bu konunun video sürümü için bkz: [öğretici 1: Visual Basic'te - Video 2 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205211) veya [öğretici 1: Resim Görüntüleyici C# ' - oluşturma Videoyu 2](http://go.microsoft.com/fwlink/?LinkId=205200). Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır.  
  
### <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Formunuzu bir TableLayoutPanel denetimiyle düzenlemek için  
  
1.  Visual Studio IDE'nin sol tarafında bulun **araç kutusu** sekmesi. Seçin **araç kutusu** sekmesi ve araç kutusu görünür. (Veya menü çubuğunda, **görünümü**, **araç kutusu**.)  
  
2.  Yanındaki küçük üçgen sembolünü seçin **kapsayıcıları** grubu, aşağıdaki resimde gösterildiği gibi açın.  
  
     ![Kapsayıcılar grubu](../ide/media/express-toolbox.png "Express_Toolbox")  
Kapsayıcılar grubu  
  
3.  Formunuza düğmeler, onay kutuları ve etiketler gibi denetimler ekleyebilirsiniz. Çift `TableLayoutPanel` araç kutusu denetimi. (Ya da denetimi araç kutusundan forma sürükleyebilirsiniz.) Bunu yaptığınızda IDE ekler bir `TableLayoutPanel` aşağıdaki resimde gösterildiği gibi form denetimi.  
  
     ![TableLayoutPanel denetimi](../ide/media/express-formtablelayout.png "Express_FormTableLayout")  
TableLayoutPanel denetimi  
  
    > [!NOTE]
    >  Formunuza başlığıyla içinde bir pencere görünürse, TableLayoutPanel ekledikten sonra **TableLayoutPanel görevleri**, herhangi bir yeri kapatmak için form içinde seçin. Bu pencere hakkında daha fazla öğreticinin ilerleyen bölümlerinde öğreneceksiniz.  
  
     Nasıl araç kutusu sekmesini seçtiğinizde formunuzun kapsayacak şekilde genişler ve bunun dışında herhangi bir yeri seçtikten sonra kapatır dikkat edin. Bu IDE otomatik gizleme özelliğidir. Açıp pencereler için geçiş otomatik gizleme ve kilitleme penceresinin üst sağ üst köşedeki Raptiye simgesini seçerek açabilirsiniz. Raptiye simgesi aşağıdaki gibi görünür.  
  
     ![Raptiye simgesi](../ide/media/express-pushpintoolbox.png "Express_PushpinToolbox")  
Raptiye simgesi  
  
4.  Mutlaka **TableLayoutPanel** seçerek seçilir. Açılan listenin en üstündeki bakarak hangi denetimin seçili olduğunu doğrulayabilirsiniz **özellikleri** penceresinde, aşağıdaki resimde gösterildiği gibi.  
  
     ![TableLayoutPanel denetimini gösteren Özellikler penceresi](../ide/media/express-controlspropwin.png "Express_ControlsPropWin")  
TableLayoutPanel denetimini gösteren Özellikler penceresi  
  
5.  Seçin **alfabetik** araç çubuğunda düğme **özellikleri** penceresi. Bu özellikler listesinden neden **özellikleri** penceresi, bu öğreticide özellikleri bulmak daha kolay bulabilmesini sağlar alfabetik sırada görüntüleyin.  
  
6.  Aşağı açılan listesidir üst kısmındaki denetim seçiciyi **özellikleri** penceresi. Bu örnekte, bir denetim adlı gösterir `tableLayoutPanel1` seçilir. Windows Form Tasarımcısı'nda bir alan seçerek veya denetim seçiciden seçerek denetimleri seçebilirsiniz. Şimdi `TableLayoutPanel` olan seçili **Dock** özelliği ve **Dock**, ayarlanması **hiçbiri**. Bir açılan liste okunu değerin yanında görüntülendiğine dikkat edin. Oku seçin ve ardından **dolgu** düğmesini (ortadaki büyük düğme), aşağıdaki resimde gösterildiği gibi.  
  
     ![Doldur seçili Özellikler penceresi](../ide/media/express-docktable.png "Express_DockTable")  
Doldur seçili Özellikler penceresi  
  
     *Yerleştirme* Visual Studio'da pencere başka bir pencereye veya alana IDE'de bağlı olduğu başvuruyor. Örneğin, Özellikler penceresinde – yani eklenmemiş ve Visual Studio – yerleştirilmemiş akıyor olabilir veya karşı yerleştirilmiş **Çözüm Gezgini**.  
  
7.  TableLayoutPanel ayarladıktan sonra **Dock** özelliğini **dolgu**, panel formun tamamını kaplar. Formu yeniden boyutlandırırsanız, TableLayoutPanel takılı kalır ve kendisini sığacak şekilde yeniden boyutlandırır.  
  
    > [!NOTE]
    >  TableLayoutPanel, Microsoft Office Word'ün bir tablo gibi çalışır: satırları ve sütunları vardır ve tek bir hücre birçok satırı ve sütunu kapsayabilir. Her hücre bir denetimi kontrol eder (düğme, onay kutusu veya etiket) barındırabilir. TableLayoutPanel denetiminiz olur bir `PictureBox` denetimi üst satırı, kapsayan bir `CheckBox` denetimi, sol alttaki hücreye ve dört `Button` kendi sağ alt hücresinde denetimleri.  
  
8.  Şu anda TableLayoutPanel, iki eşit boyutta satıra ve iki eşit boyutta sütuna sahiptir. Size en üst satır ve sağ sütun için bunları yeniden boyutlandırın gerekiyor. Windows Form Tasarımcısı'nda Tablelayoutpanel'i seçin. Sağ üst köşedeki gibi görünen bir küçük siyah üçgen düğme yoktur.  
  
     ![Üçgen düğme](../ide/media/express-iconblacktriangle.gif "Express_IconBlackTriangle")  
Üçgen düğme  
  
     Bu düğme denetimi yardımcı olan görevleri olduğunu gösterir özelliklerini otomatik olarak ayarlayın.  
  
9. Aşağıdaki resimde gösterildiği gibi denetim görev listesinde görüntülemek üzere üçgeni seçin.  
  
     ![TableLayoutPanel görevleri](../ide/media/express-tablepanel.png "Express_TablePanel")  
TableLayoutPanel görevleri  
  
10. Seçin **satırları ve sütunları Düzenle** görüntülenecek olan görevi **sütun ve satır stilleri** penceresi. Seçin **Column1**, emin olma yüzde 15 boyutunu ayarlayın **yüzde** düğmesi seçili olduğunu ve `15` içinde **yüzde** kutusu. (Bu bir `NumericUpDown` denetimi, bir sonraki öğreticide kullanacaksınız.) Seçin **Sütun2** ve yüzde 85 olarak ayarlayın. Seçmeyin **Tamam** pencere kapanacağından düğmesini henüz. (Ancak bunu yaparsanız, görev listesini kullanarak yeniden açabilirsiniz.)  
  
     ![TableLayoutPanel sütun ve satır stilleri](../ide/media/vs-tablelayoutpanel-setup.png "VS_TableLayoutPanel_Setup")  
TableLayoutPanel sütun ve satır stilleri  
  
11. Gelen **Göster** açılan pencerenin en üstünde **satırları**. Ayarlama **Satır1** yüzde 90 ve **satır2** yüzde 10.  
  
12. Seçin **Tamam** düğmesi. Tablelayoutpanel'inizin şimdi büyük bir üst satırı, küçük bir alt satırı, küçük bir sol sütunu ve büyük bir sağ sütunu olması gerekir. TableLayoutPanel sütun ve satırlar formdaki tableLayoutPanel1 seçerek ve ardından, satır ve sütun kenarlıklarını sürükleyerek yeniden boyutlandırabilirsiniz.  
  
     ![Yeniden boyutlandırılan TableLayoutPanel ile Form1](../ide/media/vs-formafterlayoutpanel.png "VS_FormAfterLayoutPanel")  
Yeniden boyutlandırılan TableLayoutPanel ile Form1  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [5. adım: bilgisayarınızı formu için denetimler Ekle](../ide/step-5-add-controls-to-your-form.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [3. adım: bilgisayarınızı Form özelliklerini ayarla](../ide/step-3-set-your-form-properties.md).



