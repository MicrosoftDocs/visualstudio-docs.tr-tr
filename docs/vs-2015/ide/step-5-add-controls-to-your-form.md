---
title: '5. adım: Formunuza denetimler ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f7c65577a08b9aa9d6750b857e2c38939031f38
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257029"
---
# <a name="step-5-add-controls-to-your-form"></a>5. Adım: Formunuza Denetimler Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu adımda, denetimleri gibi eklediğiniz bir `PictureBox` denetimi ve bir `CheckBox` form denetimi. Ardından formunuza düğmeler ekleyin.  
  
 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo")bu konunun video sürümü için bkz: [öğretici 1: Visual Basic'te - Video 2 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205211) veya [öğretici 1: Resim Görüntüleyici C# ' - oluşturma Videoyu 2](http://go.microsoft.com/fwlink/?LinkId=205200). Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır.  
  
### <a name="to-add-controls-to-your-form"></a>Formunuza denetimler ekleme  
  
1.  Araç Kutusu sekmesine (Visual Studio IDE solunda bulunur) gidin ve genişletin **ortak denetimleri** grubu. Bu formlarda gördüğünüz ortak denetimleri gösterir.  
  
2.  Form üzerindeki TableLayoutPanel denetimini seçin. TableLayoutPanel seçili olduğunu doğrulamak için adının en üstündeki açılan liste kutusunda göründüğünden emin olun **özellikleri** penceresi. En üstündeki açılan liste kutusunu kullanarak form denetimleri seçebilirsiniz **özellikleri** penceresi. Bir denetimi bu şekilde genellikle daha küçük bir denetimi fareyle seçme daha kolay olabilir.  
  
3.  Çift **PictureBox** formunuza PictureBox denetimi eklemek için öğesi. TableLayoutPanel, formunuzu doldurmak üzere sabitlendiğinden IDE ilk boş hücreye (sol üst köşe) PictureBox denetimi ekler.  
  
4.  Seçmek için yeni PictureBox denetimini seçin ve ardından aşağıdaki resimde gösterildiği gibi görev listesini görüntülemek için yeni PictureBox denetiminde siyah üçgeni seçin.  
  
     ![PictureBox görevleri](../ide/media/express-pictureboxtasks.png "Express_PictureBoxTasks")  
PictureBox görevleri  
  
    > [!NOTE]
    >  Yanlışlıkla yanlış tür denetimi Tablelayoutpanel'e eklerseniz bunu silebilirsiniz. Denetime sağ tıklayın ve ardından **Sil** kendi bağlam menüsünde. Ayrıca, menü çubuğunu kullanarak denetimleri formdan kaldırabilirsiniz. Menü çubuğunda, **Düzenle**, **geri**, veya **Düzenle**, **Sil**.  
  
5.  Seçin **üst kapsayıcıya Yerleştir** bağlantı. Bu, PictureBox'ın ayarlar otomatik olarak **Dock** özelliğini **dolgu**. Bu, seçmek amacıyla PictureBox denetimini seçin görmek için Git **özellikleri** penceresinde emin olun **Dock** özelliği **dolgu**.  
  
6.  Değiştirerek her iki sütuna yayılmış PictureBox olun, **ColumnSpan** özelliği. PictureBox denetimini seçin ve ayarlayın, **ColumnSpan** özelliğini **2**. Ayrıca PictureBox boş iken boş bir çerçeve göstermek istersiniz. Ayarlama, **BorderStyle** özelliğini **Fixed3D**.  
  
    > [!NOTE]
    >  Görmüyorsanız, bir **ColumnSpan** PictureBox, ardından özelliği büyük olasılıkla PictureBox TableLayoutPanel yerine forma eklenmiş olan. Bu sorunu gidermek için PictureBox'ı seçin, silin, TableLayoutPanel öğesini seçin ve ardından yeni bir PictureBox ekleyin.  
  
7.  Formda TableLayoutPanel öğesini seçin ve ardından bir **onay kutusu** forma. Çift **onay kutusu** tablonuzdaki sonraki boş hücreye yeni bir CheckBox denetimi eklemek için araç kutusu öğesi. Bir PictureBox, TableLayoutPanel içindeki ilk iki hücreyi kurmak alacağından CheckBox denetimi sol alttaki hücreye eklenir. Seçin **metin** özelliği ve sözcüğünü yazın **Esnetme**, aşağıdaki resimde gösterildiği gibi.  
  
     ![Uzat özelliği olan TextBox denetimi](../ide/media/express-pictureviewercheckbox.png "Express_PictureViewerCheckbox")  
Uzat özelliği olan TextBox denetimi  
  
8.  Formda TableLayoutPanel öğesini seçin ve ardından Git **kapsayıcıları** çift tıklayın ve Grup (burada aldığınız TableLayoutPanel denetiminizin) araç kutusunda **FlowLayoutPanel** öğe yeni bir denetim eklemek için (sağ alt) picturebox'taki son hücreye için. Ardından, Flowlayoutpanel'i Tablelayoutpanel'e yerleştirme (seçerek **üst kapsayıcıya Yerleştir** Flowlayoutpanel'in siyah renkli üçgen görev listesi veya Flowlayoutpanel'in ayarlayarak **Dock** özelliğini **dolgu**).  
  
    > [!NOTE]
    >  FlowLayoutPanel sırasıyla düzenli satırlardaki diğer denetimleri düzenler bir kapsayıcıdır. Flowlayoutpanel'i yeniden boyutlandırdığınızda, tüm denetimlerinden tek satıra yerleştirecek kadar yeri varsa bunu yapar. Aksi takdirde, bunları satırlarında, biri diğerinin en üstünde düzenler. Dört düğmeyi barındırması için bir FlowLayoutPanel kullanacaksınız. Düğmeleri geliyorsa eklendiğinde diğerinin üstüne, düğme eklemeden önce FlowLayoutPanel seçildiğinden emin olun. Her hücrenin yalnızca bir denetimi tutabileceği önceden belirtmiştik rağmen TableLayoutPanel öğesinin alt sağ hücresi dört düğme denetimine sahiptir. Diğer denetimleri içeren bir hücreye bir denetim koyabilirsiniz olmasıdır. Bu tür bir denetime kapsayıcı adı verilir ve FlowLayoutPanel bir kapsayıcıdır.  
  
### <a name="to-add-buttons"></a>Düğme eklemek için  
  
1.  Eklediğiniz yeni Flowlayoutpanel'i seçin. Git **ortak denetimleri** araç ve çift **düğmesi** adındaki bir düğme denetimini eklemek için ürün **button1** Flowlayoutpanel'e için. Başka bir düğme eklemek için yineleyin. IDE olduğunu zaten adlı bir düğme belirler **button1** ve bir Sonrakini **button2**.  
  
2.  Genellikle, diğer düğmeleri araç kutusunu kullanarak ekleyin. Bu süre seçin **button2**ve ardından menü çubuğunda, **Düzenle**, **kopyalama** (veya Ctrl + C tuşlarına basın). Menü çubuğunda, **Düzenle**, **yapıştırın** (veya Ctrl + V tuşlarına basın) düğmenizin bir kopyasını yapıştırmak için. Şimdi yeniden yapıştırın. IDE şimdi eklendi **button3** ve **button4** flowlayoutpanel'e.  
  
    > [!NOTE]
    >  Herhangi bir denetime kopyalayıp. IDE adları ve yeni denetimleri mantıksal bir şekilde yerleştirir. Bir denetimi kapsayıcının içine yapıştırırsanız, IDE yerleştirme için bir sonraki mantıksal alanı seçer.  
  
3.  İlk düğmeyi seçin ve ayarlayın, **metin** özelliğini **resim Göster**. Ardından **metin** için sonraki üç düğmenin özelliklerini **resmi Temizle**, **arka plan rengini ayarlamak**, ve **Kapat**.  
  
4.  Sonraki adımda, düğmelerin boyutları ayarlanmakta ve bunlar panelin sağ tarafına hizalanacak sağlamaktır. Flowlayoutpanel'i seçin ve bakmak kendi **FlowDirection** özelliği. Ayarlanmış şekilde değiştirmesini **RightToLeft**. Bunu hemen sonra düğmeler kendilerini hücrenin sağ tarafına Hizala ve gerekir sıralarını tersine böylece **resim Göster** sağ tarafta düğmesidir.  
  
    > [!NOTE]
    >  Düğmeler hala yanlış sırada varsa, bunları herhangi bir sırada yeniden düzenlemek için bir FlowLayoutPanel etrafına sürükleyebilirsiniz. Bir düğme seçip sola veya sağa sürükleyebilirsiniz.  
  
5.  Seçin **Kapat** düğmesini seçin. CTRL tuşunu basılı tutun ve diğer üç düğmeyi seçin, böylece tümü seçilir. Tüm düğmeleri seçili durumdayken, Git **özellikleri** penceresi ve sayfayı yukarı kaydırın **AutoSize** özelliği. Bu özellik düğmeye kendisini tüm metni sığacak şekilde otomatik olarak yeniden boyutlandırmak için söyler. Ayarlayın **true**. Düğmelerinizi şimdi doğru boyutlandırılmalı ve doğru sırada olmalıdır. (Dört düğme seçili olduğu sürece, tüm dört değiştirebilirsiniz **AutoSize** özellikleri aynı anda.) Aşağıdaki resimde dört düğme gösterilmektedir.  
  
     ![Resim Görüntüleyici ile dört düğme](../ide/media/express-autosize.png "Express_AutoSize")  
Dört düğmeli Resim Görüntüleyici  
  
6.  Artık, kullanıma yeni laid formunuzu yeniden görmek için programınızı çalıştırın. Düğmeleri ve onay kutularını seçmek henüz bir işe yaramaz, ancak kısa süre içinde çalışır.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [6. adım: ad bilgisayarınızı düğme denetimleri](../ide/step-6-name-your-button-controls.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [4. adım: düzenleme kullanıma bilgisayarınızı Form bir TableLayoutPanel denetimiyle](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).



