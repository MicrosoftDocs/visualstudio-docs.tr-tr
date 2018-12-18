---
title: '7. adım: Formunuza iletişim kutusu bileşenleri ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca17a6958a3c66054b89fc65c30bf397c4e6b821
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192952"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>7. Adım: Formunuza İletişim Kutusu Bileşenleri Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programınızın resim dosyalarınızı açmasını ve bu adımda, bir arka plan rengini seçin etkinleştirmek için bir **OpenFileDialog** bileşeni ve bir **ColorDialog** formunuza bileşen.  
  
 Bazı açılardan denetim gibi bir bileşenidir. Formunuza bir bileşen eklemek için araç kutusunu kullanın ve kullanarak onun özelliklerini ayarlarsınız **özellikleri** penceresi. Ancak denetimden farklı olarak formunuza bir bileşen eklemek, kullanıcının formda görebileceği görünür bir öğe eklemez. Bunun yerine, kod ile tetikleyebileceğiniz belirli davranışlar sağlar. Açılır bir bileşendir bir **açık dosya** iletişim kutusu.  
  
 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo")bu konunun video sürümü için bkz: [öğretici 1: Visual Basic'te - Video 3 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205213) veya [öğretici 1: Resim Görüntüleyici C# ' - oluşturma Video 3](http://go.microsoft.com/fwlink/?LinkId=205202). Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır.  
  
### <a name="to-add-dialog-components-to-your-form"></a>Formunuza iletişim kutusu bileşenleri eklemek için  
  
1.  Windows Form Tasarımcısı (Form1.cs [Design] veya Form1.vb [Design]) seçin ve ardından açın **iletişim kutuları** araç kutusu grubu.  
  
    > [!NOTE]
    >  **İletişim kutuları** araç grubunda açma ve dosyaları kaydetmek, klasörlere göz atma ve yazı tiplerini ve renkleri seçmek için kullanılabilecek pek çok yararlı iletişim kutuları, açılan bileşeni vardır. Bu projede iki iletişim kutusu bileşeni kullanırsınız: **OpenFileDialog** ve **ColorDialog**.  
  
2.  Adlı bir bileşen eklemek için **openFileDialog1** formunuza, çift **OpenFileDialog**. Adlı bir bileşen eklemek için **colorDialog1** formunuza, çift **ColorDialog** araç. (Bir sonraki Eğitmen adımında kullanın.) Windows Form Tasarımcısı (Resim Görüntüleyicisi formunun altında) aşağıdaki resimde gösterildiği gibi bir simge her biri, eklediğiniz iki iletişim kutusu bileşenleri için sahip alt kısmındaki bir alan görmelisiniz.  
  
     ![İletişim kutusu bileşenleri](../ide/media/express-dialogsadded.png "Express_DialogsAdded")  
İletişim kutusu bileşenleri  
  
3.  Seçin **openFileDialog1** Windows Form Tasarımcısı'nın atındaki simgesi. İki özellikleri ayarlayın:  
  
    -   Ayarlama **filtre** özelliğini aşağıdaki (kopyalayın ve yapıştırın):  
  
        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  
  
    -   Ayarlama **başlık** özelliğini aşağıdaki: **bir resim dosyası seçin**  
  
         **Filtre** özellik ayarları görüntülenecek dosya türlerinin çeşitlerini belirtir **Resim Seç** dosya iletişim kutusu.  
  
    > [!NOTE]
    >  Bir örnek görmek için **Dosya Aç** iletişim kutusu farklı bir uygulama Not Defteri'ni veya Paint'i açın ve menü çubuğunda, **dosya**, **açın**. Nasıl olduğuna dikkat edin bir **dosya türü** altındaki aşağı açılan listeden. Yalnızca kullanılan **filtre** özelliğinde **OpenFileDialog** kurmak için bileşen. Ayrıca, nasıl **başlık** ve **filtre** özellikleri kalın **özellikleri** penceresi. IDE, varsayılan değerleri değiştirilmiş özellikleri size göstermek için yapar.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [adım 8: bir resim düğme olayı işleyicisi Göster için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [6. adım: ad bilgisayarınızı düğme denetimleri](../ide/step-6-name-your-button-controls.md).



