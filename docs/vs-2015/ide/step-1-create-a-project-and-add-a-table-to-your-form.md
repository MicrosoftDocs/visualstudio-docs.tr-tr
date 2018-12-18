---
title: '1. adım: Proje oluşturma ve formunuza tablo ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c49a3e9ac7c4a37c1c030d631667d90b274143cf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934697"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>1. Adım: Proje Oluşturma ve Formunuza Tablo Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşleştirme oyunu hazırlarken ilk adım projeyi oluşturmak ve formunuza bir tablo eklemektir. Tablo, simgeleri 4x4'lük muntazam bir kılavuza hizalamaya yardımcı olur. Ayrıca, oyun tahtasının görünüşünü iyileştirmek için çeşitli özellikleri ayarlarsınız.  
  
### <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Bir proje oluşturmak ve formunuza bir tablo eklemek için  
  
1. Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2. Visual Studio Express kullanmıyorsanız, önce bir programlama dili seçmeniz gerekir. Gelen **yüklü şablonlar** listesinde **Visual C#** veya **Visual Basic**.  
  
3. Proje şablonları listesinde seçin **Windows Forms uygulaması**, projeyi adlandırın **oyunu**ve ardından **Tamam** düğmesi.  
  
4. İçinde **özellikleri** penceresinde aşağıdaki form özelliklerini ayarlayın.  
  
   1.  Formun değiştirme **metin** özelliğinden **Form1** için **eşleştirme oyunu**. Bu metin oyun penceresinin en üstünde görünür.  
  
   2.  Formun boyutunu 550 piksel genişliğe ve 550 piksel uzunluğa ayarlayın. Ayarlayarak ya da bunu yapabilirsiniz **boyutu** özelliğini **550, 550**, veya tümleşik geliştirme ortamı (sağ alt köşesinde doğru boyutu görünceye kadar formu köşesinden sürükleyerek IDE).  
  
5. Seçerek araç kutusunu görüntüleyin **araç kutusu** IDE'nin sol tarafındaki sekmesi.  
  
6. Sürükleme bir `TableLayoutPanel` denetimi **kapsayıcıları** Araç Kutusu'nda, kategori ve bunun için aşağıdaki özellikleri ayarlayın.  
  
   1. Ayarlama **BackColor** özelliğini **CornflowerBlue**. Bunu yapmak için açık **BackColor** yanındaki aşağı açılır oku seçerek iletişim kutusu **BackColor** özelliğinde **özellikleri** penceresi.  Ardından, **Web** sekmesinde **BackColor** iletişim kutusu, kullanılabilir renk adlarının bir listesini görüntülemek için.  
  
      > [!NOTE]
      >  Renkler alfabetik sırada değildir ve CornflowerBlue listenin sonuna yakın bir yerdedir.  
  
   2. Ayarlama **Dock** özelliğini **dolgu** özelliğin yanındaki açılan düğmeyi seçerek ve büyük Orta düğmeyi seçerek. Böylece tablo formun tamamını kaplayacak şekilde yayılır.  
  
   3. Ayarlama **CellBorderStyle** özelliğini **iç**. Böylece, tahta üzerindeki her bir hücre arasında görsel kenarlıklar olur.  
  
   4. TableLayoutPanel denetiminin sağ üst köşesindeki üçgen düğmesini seçerek ilgili görev menüsünü görüntüleyin.  
  
   5. Görev menüsünde **Satır Ekle** iki kez iki satır daha ekleyin ve ardından **Sütun Ekle** iki kez iki sütun daha eklemek için.  
  
   6. Görev menüsünde **satırları ve sütunları Düzenle** açmak için **sütun ve satır stilleri** penceresi. Her sütun seçin, **yüzde** seçenek düğmesini ve ardından her bir sütunun genişliğini toplam genişliğin yüzde 25 değerine ayarlayın. Ardından **satırları** açılır listeden kutusu penceresinin en üstünde ve her bir satırın yüksekliğini yüzde 25 değerine ayarlayın. İşiniz bittiğinde seçin **Tamam** düğmesi.  
  
      TableLayoutPanel denetiminiz şu anda, eşit boyutlu on altı kare hücre içeren 4x4'lük bir kılavuz halinde olmalıdır. Bu satırlar ve sütunlar, sonradan simge resimlerinin görüneceği yerlerdir.  
  
7. Form düzenleyicisinde TableLayoutPanel seçildiğinden emin olun. Bunu doğrulamak için görmelisiniz **tableLayoutPanel1** en üstündeki **özellikleri** penceresi. Seçilmezse, formda TableLayoutPanel öğesini seçin veya en üstündeki aşağı açılır denetimden seçin **özellikleri** penceresi.  
  
    TableLayoutPanel seçili durumdayken araç kutusunu açın ve eklemek bir **etiket** denetimi (bulunan **ortak denetimleri** kategorisi) TableLayoutPanel öğesinin sol üst hücresine. `Label` Denetim IDE'de artık seçilmelidir. Bu öğe için aşağıdaki özellikleri ayarlayın.  
  
   1.  Etiketin olduğundan emin olun **BackColor** özelliği **CornflowerBlue**.  
  
   2.  Ayarlama **AutoSize** özelliğini **False**.  
  
   3.  Ayarlama **Dock** özelliğini **dolgu**.  
  
   4.  Ayarlama **TextAlign** özelliğini **MiddleCenter** özelliğin yanındaki açılan düğmeyi seçerek ve ardından Orta düğmeyi seçerek. Böylece, simgenin hücrenin ortasında görünmesi sağlanır.  
  
   5.  Seçin **yazı tipi** özelliği. Üç nokta (…) düğmesi görünmelidir.  
  
   6.  Üç nokta düğmesini seçin ve ayarlayın **yazı tipi** değerini **Webdings**, **yazı tipi stili** için **kalın**ve **boyutu** için **72**.  
  
   7.  Ayarlama **metin** harf etiketi özelliği **c**.  
  
        TableLayoutPanel öğesinin sol üst hücresinde şimdi, mavi arka plan üzerinde ortalanmış bir siyah kutu yer alıyor olmalıdır.  
  
       > [!NOTE]
       >  Webdings yazı tipi, simgelerden oluşan bir yazı tipi olup Windows işletim sistemiyle birlikte gelir. Eşleştirme oyununuzda oyuncunun simge çiftlerini eşleştirmesi gerektiğinden, eşleştirilecek simgeleri göstermek için bu yazı tipini kullanıyorsunuz. Yerine **c** içinde **metin** özelliği, hangi simgelerin gösterildiğini görmek için farklı harfler girmeyi deneyin. Ünlem işareti bir örümcek, büyük N harfi bir göz ve virgül ise kırmızı biberdir.  
  
8. Etiket denetiminizi seçin ve TableLayoutPanel içinde sonraki hücreye kopyalayın. (Ctrl + C tuşlarına basın veya menü çubuğunda, **Düzenle**, **kopyalama**.) Sonra da yapıştırın. (Ctrl + V tuşlarına basın veya menü çubuğunda, **Düzenle**, **Yapıştır**.) TableLayoutPanel denetiminin ikinci hücresinde ilk etiketin bir kopyası görünür. Yeniden yapıştırdığınızda, üçüncü hücrede bir başka etiket görünür. Yapıştırmayı sürdürün `Label` hücrelerin tümü doluncaya kadar denetler.  
  
   > [!NOTE]
   >  Çok fazla kez yapıştırırsanız, yeni etiket denetiminizi ekleyecek bir yer olması için IDE TabloLayoutPanel öğesine yeni bir satır yapıştırır. Bunu geri alabilirsiniz. Yeni hücreyi kaldırmak için Ctrl + Z tuşlarına basın veya menü çubuğunda, **Düzenle**, **geri**.  
  
    Artık formunuz hazırdır. Aşağıdaki resimde olduğu gibi görünmesi gerekir.  
  
    ![İlk eşleştirme oyunu formu](../ide/media/express-tut4step1.png "Express_Tut4Step1")  
   İlk eşleştirme oyunu formu  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [2. adım: rasgele nesne ve a List of Icons ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
-   Genel Bakış konusuna dönmek için bkz: [Tutorial 3: Create a Matching Game](../ide/tutorial-3-create-a-matching-game.md).



