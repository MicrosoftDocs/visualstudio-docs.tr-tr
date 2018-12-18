---
title: '5. adım: formunuza denetimler ekleme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7a0167d4d5af125e706350002ccf8a17e459414
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748562"
---
# <a name="step-5-add-controls-to-your-form"></a>5. adım: formunuza denetimler ekleme
Bu adımda, denetimleri gibi eklediğiniz bir <xref:System.Windows.Forms.PictureBox> denetim ve <xref:System.Windows.Forms.CheckBox> Formunuza denetim. Ardından ekleyin <xref:System.Windows.Forms.Button> formunuza denetimler.

 ![video bağlantı](../data-tools/media/playvideo.gif)bu konuda video sürümü için bkz: [Öğreticisi 1: Visual Basic'te - Video 2 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205211) veya [Eğitmen 1: Resim Görüntüleyici C# ' - Video 2 oluşturma](http://go.microsoft.com/fwlink/?LinkId=205200). Bazı menü komutları ve diğer kullanıcı arabirimi öğeleri küçük farklar olduklarından bu videolar Visual Studio'nun önceki bir sürümünü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde geçerli sürümünde Visual Studio çalışır.

## <a name="to-add-controls-to-your-form"></a>Formunuza denetimler ekleme

1.  Git **araç** (Visual Studio IDE sol tarafta bulunan) sekmesinden ve genişletin **ortak denetimler** grubu. Bu, en yaygın denetimleri formlarında gördüğünüz gösterir.

2.  Seçin **TableLayoutPanel** form üzerinde denetim. TableLayoutPanel seçildiğini doğrulamak için adının en üstündeki açılır liste kutusunda gösterildiğinden emin olun **özellikleri** penceresi. En üstte açılır liste kutusunu kullanarak form denetimlerini seçebilirsiniz **özellikleri** penceresi. Bir denetim seçme bu şekilde genellikle fare küçük bir denetimle seçme daha kolay olabilir.

3.  Çift **PictureBox** formunuza PictureBox denetimi eklenecek öğe. TableLayoutPanel formunuz doldurmak için yerleşik olduğundan, IDE PictureBox denetimi ilk boş hücreye (sol üst köşesinde) ekler.

4.  Yeni seçin **PictureBox** seçmek üzere denetlemek ve ardından aşağıdaki resimde gösterildiği gibi görev listesini görüntülemek için yeni PictureBox denetiminde siyah üçgen seçin.

     ![PictureBox görevleri](../ide/media/express_pictureboxtasks.png)
**PictureBox** görevleri

    > [!NOTE]
    >  TableLayoutPanel denetimi yanlış türde yanlışlıkla eklerseniz, silebilirsiniz. Denetimin sağ tıklayın ve ardından **silmek** bağlam menüsünde. Menü Çubuğu'nu kullanarak formdan denetimleri de kaldırabilirsiniz. Menü çubuğunda seçin **Düzenle** > **geri**, veya **Düzenle** > **silmek**.

5.  Seçin **Ana kapsayıcıda yerleştir** bağlantı. Bu otomatik olarak PictureBox ayarlar **yerleştirme** özelliğine **doldurun**. Bu görmek için seçin **PictureBox** gidin seçmek için Denetim **özellikleri** penceresinde ve emin olun, **yerleştirme** özelliği ayarlanmış **doldurun**.

6.  Her iki sütuna değiştirerek yayılan PictureBox olun kendi **ColumnSpan** özelliği. Seçin **PictureBox** denetleyin ve ayarlayın, **ColumnSpan** özelliğine **2**. Ayrıca, PictureBox boş olduğunda, boş bir çerçeve göstermek istiyorsunuz. Ayarlama, **kenarlık stili** özelliğine **Fixed3D**.

    > [!NOTE]
    >  Görmüyorsanız, bir **ColumnSpan** , PictureBox, ardından özelliğidir PictureBox TableLayoutPanel yerine formun eklendiğini büyük olasılıkla. Bu sorunu gidermek için tercih **PictureBox**, silmek, seçin **TableLayoutPanel**, ve ardından yeni PictureBox ekleyin.

7.  Seçin **TableLayoutPanel** formdaki ve sonra forma bir onay kutusu denetimi ekleyin. Çift **onay kutusunu** öğesi **araç** tablonuz sonraki boş hücreye yeni bir onay kutusu denetimi eklemek için. Bir PictureBox TableLayoutPanel ilk iki hücrelere yukarı aldığından, onay kutusu denetimi için sol alt hücre eklenir. Seçin **metin** özelliği ve Word türü **Esnetme**, aşağıdaki resimde gösterildiği gibi.

     ![TextBox denetimi Stretch özelliği ile](../ide/media/express_pictureviewercheckbox.png)
**TextBox** ile kontrol **Esnetme** özelliği

8.  Seçin **TableLayoutPanel** form ve gidin **kapsayıcıları** grubu **araç** (burada aldığınız TableLayoutPanel denetimi) ve çift tıklatın **FlowLayoutPanel** (sağ alt) PictureBox son hücreye öğesi yeni bir denetim eklemek için. TableLayoutPanel içinde FlowLayoutPanel yerleştirme (seçerek **Ana kapsayıcıda yerleştir** FlowLayoutPanel'ın siyah üçgen görev listesi veya FlowLayoutPanel's ayarlayarak **yerleştirme** özelliğine **doldurun**).

    > [!NOTE]
    >  A <xref:System.Windows.Forms.FlowLayoutPanel> diğer denetimlerini sırayla masaüstünüzdeki satırlardaki düzenler bir kapsayıcıdır. Tüm denetimlerindeki tek bir satırı düzenlemek için yer varsa bir FlowLayoutPanel boyutlandırdığınızda, yapar. Aksi takdirde, bunları birbirinin satırlarındaki düzenler. FlowLayoutPanel dört düğme tutmak için kullanır. Düğmeleri biri üzerinde Yerleştir başka eklendiğinde top, FlowLayoutPanel düğmeleri eklemeden önce seçili olduğundan emin olun. Daha önce her bir hücre yalnızca bir denetim tutabilir belirtmiştik rağmen TableLayoutPanel sağ alt hücrenin dört düğmesi denetimleri vardır. Bir denetim diğer denetimleri tutan bir hücreye koyabilirsiniz olmasıdır. Bu tür denetimi bir kapsayıcı adı verilir ve FlowLayoutPanel bir kapsayıcıdır.

## <a name="to-add-buttons"></a>Düğmeler ekleme

1.  Eklediğiniz yeni FlowLayoutPanel seçin. Git **ortak denetimler** içinde **araç** çift tıklayın ve **düğmesini** adlı bir düğme denetim eklemek için öğeyi **button1** için FlowLayoutPanel. Başka bir düğme eklemek için yineleyin. Zaten var olduğu adlı bir düğme IDE belirler **button1** ve bir sonraki çağırır **button2**.

2.  Genellikle, kullanarak başka bir düğme ekleme **araç**. Bu saati seçin **button2**ve ardından menü çubuğunda, **Düzenle** > **kopya** (veya basın **Ctrl** + **C**). Menü çubuğunda seçin **Düzenle** > **Yapıştır** (veya basın **Ctrl**+**V**), düğmesinin bir kopyasını yapıştırmak için. Şimdi yeniden yapıştırın. IDE şimdi eklendi **button3** ve **button4** FlowLayoutPanel için.

    > [!NOTE]
    >  Kopyalayın ve hiçbir denetim yapıştırın. IDE adları ve yeni denetimleri mantıksal bir şekilde yerleştirir. Bir kapsayıcıya bir denetim yapıştırırsanız, IDE yerleştirme için sonraki mantıksal alan seçer.

3.  İlk düğmesini seçin ve ayarlayın, **metin** özelliğine **resim Göster**. Ardından **metin** sonraki üç düğmelere özelliklerini **resmi temizleyin**, **arka plan rengini ayarlama**, ve **Kapat**.

4.  Düğmeleri boyut ve bölmenin sağ tarafındaki hizalamak için bunları düzenlemek için sonraki adım olacaktır. Seçin **FlowLayoutPanel** ve bakmak kendi **FlowDirection** özelliği. Ayarlanmış şekilde değiştirme **RightToLeft**. Bunu hemen düğmeleri kendilerini hücrenin sağ tarafındaki align ve bunların sırası ters şekilde **resim Göster** düğmesi olan sağ taraftaki.

    > [!NOTE]
    >  Düğmeleri hala yanlış sırayla varsa, bunları herhangi bir sırada yeniden düzenlemek için FlowLayoutPanel çevresindeki düğmeler sürükleyebilirsiniz. Bir düğme seçin ve sola veya sağa sürükleyin.

5.  Seçin **Kapat** düğmesini seçin. Basılı **Ctrl** anahtarı ve böylece tüm seçilir diğer üç düğme seçin. Tüm düğmeleri seçili durumdayken Git **özellikleri** penceresini açın ve kaydırma kadar **AutoSize** özelliği. Bu özellik otomatik olarak kendisini tüm kendi metnin sığması için yeniden boyutlandırmak için düğmesini söyler. Ayarlamak **doğru**. Düğmeleri şimdi düzgün şekilde boyutlandırılmalıdır ve doğru sırada olmalıdır. (Tüm dört düğmeleri seçili olduğu sürece, tüm dört değiştirebilirsiniz **AutoSize** özellikleri aynı anda.) Aşağıdaki resimde, dört düğme gösterilmektedir.

     ![Resim Görüntüleyici dört düğmeleriyle](../ide/media/express_autosize.png)
**resim görüntüleyici** dört düğmeleri

6.  Şimdi yeniden kullanıma yeni laid formunuz görmek için programı çalıştırın. Düğmeler ve onay kutusunu seçerek herhangi bir şey henüz yapmaz, ancak en kısa sürede çalışır.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Öğretici bir sonraki adıma dönmek için bkz: [6. adım: düğme denetimlerinizi adlandırma](../ide/step-6-name-your-button-controls.md).

-   Eğitmen önceki adıma dönmek için bkz: [4. adım: bir TableLayoutPanel denetimi ile formunuzu düzenleme](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).
