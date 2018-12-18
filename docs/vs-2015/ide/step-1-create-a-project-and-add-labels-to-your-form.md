---
title: '1. adım: Proje oluşturma ve formunuza etiketler ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6332659307f10b5cf7f4f224c8a99456de03d81a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207005"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>1. Adım: Proje Oluşturma ve Formunuza Etiketler Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sınavı geliştirmede ilk adım olarak projeyi oluşturun ve bir forma etiketler, bir düğme ve diğer denetimleri ekleyin. Ayrıca eklediğiniz her denetimin özelliklerini ayarlarsınız. Proje formu, denetimleri, içerir ve (öğreticide daha ilerideki) kodu. Etiketler sınav sorularını gösterir düğme sınavı başlatır ve diğer denerimler ise sınav yanıtlarını ve sınavı bitirmek için kalan süreyi gösterir.  
  
> [!NOTE]
>  Bu konu, temel kodlama kavramları hakkındaki bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: bir zaman aşımına matematik sınavı oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-create-a-project-and-set-properties-for-a-form"></a>Bir proje oluşturun ve bir formun özelliklerini ayarlamak için  
  
1.  Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2.  İçinde **yüklü şablonlar** listesinde **C#** veya **Visual Basic**.  
  
3.  Şablonlar listesinde seçin **Windows Forms uygulaması** şablon adlandırın **matematik sınavı**ve ardından **Tamam** düğmesi.  
  
     Adlı bir form **Form1.cs** veya **Form1.vb** , seçtiğiniz programlama diline bağlı olarak görünür.  
  
4.  Formu seçin ve ardından değiştirmek, **metin** özelliğini **matematik sınavı**.  
  
     **Özellikleri** penceresi formun özelliklerini içerir.  
  
5.  Formun boyutunu 500 piksel genişliğe ve 400 piksel uzunluğa ayarlayın değiştirin.  
  
     Form tümleşik geliştirme ortamı (IDE) sol alt köşesinde doğru boyutu görünene kadar kenarlarını sürükleyerek yeniden boyutlandırabilirsiniz. Alternatif olarak, değerlerini değiştirebilirsiniz **boyutu** özelliği.  
  
6.  Değiştirin **FormBorderStyle** özelliğini **Fixed3D**, ayarlayıp **MaximizeBox** özelliğini **False**.  
  
     Bu değerler, sınava girenlerin formu yeniden boyutlandırmasını engeller.  
  
### <a name="to-create-the-time-remaining-box"></a>Kalan zaman kutusunu oluşturma  
  
1.  Ekleme bir **etiket** denetimi araç kutusundan ve ardından değerini kendi **(ad)** özelliğini `timeLabel`.  
  
     Bu etiket, sağ üst köşedeki sınavda kalan saniye sayısını gösteren bir kutusu olacaktır.  
  
2.  Değişiklik **AutoSize** özelliğini **False** böylece kutuyu yeniden boyutlandırabilirsiniz.  
  
3.  Değişiklik **BorderStyle** özelliğini **FixedSingle** kutu çevresinde bir çizgi çizmek için.  
  
4.  Ayarlama **boyutu** özelliğini **200, 30**.  
  
5.  Etiketi, mavi aralık çizgilerinin görüneceği yeri formun sağ üst köşesine taşıyın.  
  
     Bu satırlar formdaki denetimleri hizalamanıza yardımcı olur.  
  
6.  İçinde **özellikleri** penceresinde seçin **metin** özelliği ve ardından değerini temizlemek için Geri Al tuşunu seçin.  
  
7.  Yanındaki artı işaretini (+) seçin **yazı tipi** özelliği ve değerini değiştirin **boyutu** özelliğini **15.75 olarak**.  
  
     Aşağıdaki resmin gösterdiği gibi birkaç yazıtipi özelliğini değiştirebilirsiniz.  
  
     ![Yazı tipi boyutunu gösteren Özellikler penceresi](../ide/media/express-setfontsize.png "Express_setFontSize")  
Yazı tipi boyutunu gösteren Özellikler penceresi  
  
8.  Başka bir **etiket** denetimi araç kutusundan ve ardından yazı tipi boyutunu ayarlayın **15.75 olarak**.  
  
9. Ayarlama **metin** özelliğini **kalan süre**.  
  
10. Etiket hemen soluna hizalanacağı şekilde taşıyın **timeLabel** etiketi.  
  
### <a name="to-add-controls-for-the-addition-problems"></a>Toplama problemleri için denetimler ekleme  
  
1.  Ekleme bir **etiket** denetimi araç kutusundan ve ardından kendi **metin** özelliğini **?** (soru işareti).  
  
2.  Ayarlama **AutoSize** özelliğini **False**.  
  
3.  Ayarlama **boyutu** özelliğini **60, 50**.  
  
4.  Yazı tipi boyutunu **18**.  
  
5.  Ayarlama **TextAlign** özelliğini **MiddleCenter**.  
  
6.  Ayarlama **konumu** özelliğini **50, 75** denetimin form üzerinde yerleştirmek için.  
  
7.  Ayarlama **(ad)** özelliğini **plusLeftLabel**.  
  
8.  Seçin **plusLeftLabel** etiketleyebilir ve Ctrl + C tuşlarını seçin veya **kopyalama** üzerinde **Düzenle** menüsü.  
  
9. Ctrl + V tuşlarını seçerek etiketi üç kez yapıştırın veya **Yapıştır** üzerinde **Düzenle** menüsü.  
  
10. Böylece bir satır sağında bulunan üç yeni etiket düzenleyin **plusLeftLabel** etiketi.  
  
     Boşluk satırlarını aralarında boşluk ve satır yukarı kullanabilirsiniz.  
  
11. İkinci etiketin değerini **metin** özelliğini **+** (artı).  
  
12. Üçüncü etiketin değerini **(ad)** özelliğini **plusRightLabel**.  
  
13. Dördüncü etiketin değerini **metin** özelliğini **=** (eşittir işareti).  
  
14. Ekleme bir **NumericUpDown** denetimi araç kutusundan, yazı tipi boyutunu ayarlayın **18**ve genişliğini ayarlayın **100**.  
  
     Bu bir sonraki denetim türü hakkında daha fazla öğreneceksiniz.  
  
15. Yukarı Hizala **NumericUpDown** denetimini ek sorunun etiket denetimleri ile.  
  
16. Değiştirin **(ad)** özelliği **NumericUpDown** denetimini **toplam**.  
  
     Aşağıdaki resmin gösterdiği gibi ilk satırı oluşturdunuz.  
  
     ![Matematik sınavının ilk satırı](../ide/media/express-firstrow.png "Express_firstRow")  
Matematik sınavının ilk satırı  
  
### <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Çıkarma, çarpma ve bölme problemleri için denetimler ekleme  
  
1.  Beş denetimin tümünü (dört Label denetimi ve NumericUpDown denetimi) ek sorun için kopyalayın ve ardından bunları yapıştırın.  
  
     Form, hala seçili olan beş yeni denetimler içerir.  
  
2.  Ek denetimler altında hizaya gelecek şekilde tüm denetimleri yere taşıyın.  
  
     Boşluk satırlarını iki satır arasında yeterli uzaklık vermek için kullanabilirsiniz.  
  
3.  Değiştirin **metin** İkinci etiketin özelliği **–** (eksi işareti).  
  
4.  İlk soru işareti etiketini ad **minusLeftLabel**.  
  
5.  İkinci soru işareti etiketini ad **minusRightLabel**.  
  
6.  Adı **NumericUpDown** denetimi **fark**.  
  
7.  Beş denetimi iki kez yapıştırın.  
  
8.  Üçüncü satırda ilk etiketi adı **timesLeftLabel**, İkinci etiketin değiştirme **metin** özelliğini **×** üçüncüetiketiolarakadlandırın(çarpıişareti)**timesRightLabel**ve NumericUpDown denetimini **ürün**.  
  
9. Dördüncü satır için ilk etiketin adını **dividedLeftLabel**, İkinci etiketin değiştirme **metin** özelliğini **bölü;** (bölme oturum) üçüncü etiketi adı  **dividedRightLabel**ve NumericUpDown denetimini **bölümü**.  
  
    > [!NOTE]
    >  Bu öğreticide çarpı işareti × ve bölme oturum bölü; kopyalayın ve bunları form üzerine yapıştırın.  
  
### <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Bir başlatma düğmesi ekleme ve sekme indisi sırasını ayarlama  
  
1.  Ekleme bir **düğmesi** denetimi araç kutusundan ve ardından kendi **(ad)** özelliğini **startButton**.  
  
2.  Ayarlama **metin** özelliğini **sınavın başlaması**.  
  
3.  Yazı tipi boyutunu **14**.  
  
4.  Ayarlama **AutoSize** özelliğini **True**, düğme metin sığdırmak için otomatik olarak yeniden boyutlandırmak neden olur.  
  
5.  Düğmeyi formun altına yakın ortalayın.  
  
6.  Değerini **TabIndex** özelliği **startButton** denetimini **1**.  
  
    > [!NOTE]
    >  **TabIndex** özelliği, sınava giren Tab tuşunu seçtiğinde denetimlerin sırasını ayarlar. Nasıl çalıştığını görmek için herhangi bir iletişim kutusunu açın (örneğin, menü çubuğunda, **dosya**, **açın**) ve ardından Tab tuşuna birkaç kez basın. Nasıl imlecinizin denetimden denetime her zaman, SEKME tuşuna hareket ettiğini izleyin. Programcı sipariş oluşturan oluştururken verdi.  
  
7.  Değerini **TabIndex** özelliğinin değerini NumericUpDown toplam denetimi için için **2**, fark denetimi için **3**, ürün denetimi için **4**ve bölüm denetimi için **5**.  
  
     Form aşağıdaki gibi görünmelidir.  
  
     ![İlk matematik sınavı formu](../ide/media/express-formlaidout.png "Express_FormLaidOut")  
İlk matematik sınavı formu  
  
8.  Doğrulamak için olup olmadığını **TabIndex** beklediğiniz, kaydedin ve F5 tuşunu veya seçerek programınızı çalıştırma özelliği çalışır **hata ayıklama**, **hata ayıklamayı Başlat** menü çubuğunda, ' i tıklatın ve ardından Tab tuşuna birkaç kez basın.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [2. adım: rasgele bir toplama problemi oluşturma](../ide/step-2-create-a-random-addition-problem.md).  
  
-   Genel Bakış konusuna dönmek için bkz: [öğretici 2: bir zaman aşımına matematik sınavı oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).



