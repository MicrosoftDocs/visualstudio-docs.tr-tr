---
title: '11. adım: Programınızı çalıştırma ve diğer özellikleri deneyin | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a80a962017cc54e6ce7aae6201079f976dee9ab1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172282"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>11. Adım: Programınızı Çalıştırma ve Diğer Özellikleri Deneme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programınız bitti ve çalıştırılmaya hazır. Programınızı çalıştırabilir ve PictureBox arka plan rengini ayarlayın. Daha fazla bilgi için formun rengini değiştirerek, düğmeleri ve onay kutusunu özelleştirerek ve formun özelliklerini değiştirerek programı iyileştirmeyi deneyin.  
  
 Örnek tamamlanmış bir sürümünü indirmek için bkz [eksiksiz resim görüntüleyici Öğreticisi örneği](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).  
  
 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo")bu konunun video sürümü için bkz: [öğretici 1: Visual Basic'te - Video 5 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205216) veya [öğretici 1: Resim Görüntüleyici C# ' - oluşturma Video 5](http://go.microsoft.com/fwlink/?LinkId=205206). Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır.  
  
### <a name="to-run-your-program-and-set-the-background-color"></a>Programınızı çalıştırmak ve arka plan rengini ayarlamak için  
  
1.  F5'i seçin veya menü çubuğunda, **hata ayıklama**, **hata ayıklamayı Başlat**.  
  
2.  Bir resmi açmadan önce seçin **arka plan rengini ayarlamak** düğmesi. **Renk** iletişim kutusu açılır.  
  
     ![Renk iletişim kutusu](../ide/media/express-colordialog.png "Express_ColorDialog")  
Renk iletişim kutusu  
  
3.  PictureBox arka plan rengini ayarlamak için bir renk seçin. Yakından bakın `backgroundButton_Click()` nasıl çalıştığını anlamanız için yöntemi.  
  
    > [!NOTE]
    >  Resim URL'sini yapıştırarak Internet'ten yükünü **açık dosya** iletişim kutusu. Arka plan renkleriniz görünsün saydam bir arka plan görüntüsüne bulmaya çalışın.  
  
4.  Seçin **resmi Temizle** temizlendiğinden emin olmak için düğme. Sonra programdan çıkmak **Kapat** düğmesi.  
  
### <a name="to-try-other-features"></a>Diğer özellikleri denemek için  
  
-   Kullanarak form ve düğmelerin rengini değiştirmek **BackColor** özelliği.  
  
-   Düğmeleri ve onay kutusunu kullanarak özelleştirme **yazı tipi** ve **ForeColor** özellikleri.  
  
-   Formunuzun **FormBorderStyle** ve **ControlBox** özellikleri.  
  
-   Formunuzun kullanın **AcceptButton** ve **CancelButton** özellikleri düğmeler otomatik olarak seçilir, bu nedenle, kullanıcı ENTER veya ESC tuşuna seçer. Programa **Dosya Aç** kullanıcı girin ve kullanıcı ESC seçtiğinde kutuyu kapatın seçtiğinde bir iletişim kutusu.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Visual Studio'da programlama hakkında daha fazla bilgi için bkz. [programlama kavramları](http://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6).  
  
-   Visual Basic hakkında daha fazla bilgi için bkz: [Visual Basic ile uygulama geliştirme](http://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f).  
  
-   Visual C# hakkında bilgi edinmek için bkz. [C# dili ve .NET Framework Giriş](http://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081).  
  
-   Sonraki eğitime gitmek için bkz: [öğretici 2: bir zaman aşımına matematik sınavı oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [adım 10: ek düğmeler ve onay kutusu için kod yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).



