---
title: '1. adım: bir Windows Forms uygulaması projesi oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dd6c7f5398575f70da4414cfd529dbd6a67f5c6f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292389"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>1. Adım: Windows Forms Uygulaması Projesi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Resim Görüntüleyici oluşturduğunuzda ilk adım bir Windows Forms Application projesi oluşturmaktır.  
  
 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo")bu konunun video sürümü için bkz: [öğretici 1: Visual Basic'te - Video 1 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205209) veya [öğretici 1: Resim Görüntüleyici C# ' - oluşturma 1 video](http://go.microsoft.com/fwlink/?LinkId=205199). Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır.  
  
### <a name="to-create-a-windows-forms-application-project"></a>Bir Windows Forms uygulaması projesi oluşturmak için  
  
1.  Menü çubuğunda, **dosya**, **yeni**, **proje**. İletişim kutusu şu şekilde görünmelidir.  
  
     ![Yeni Proje iletişim kutusu](../ide/media/newprojectdialogcallouts.png "NewProjectDialogCallouts")  
Yeni Proje iletişim kutusu  
  
2.  Seçin ya da **Visual C#** veya **Visual Basic** içinde **yüklü şablonlar** listesi.  
  
3.  Şablonlar listesinde **Windows Forms uygulaması** simgesi. Yeni form adı **pictureviewer olarak**ve ardından **Tamam** düğmesi.  
  
     Visual Studio, programınız için bir çözüm oluşturur. Bir çözüm için tüm projeleri ve dosyaları, programınızın gerek duyduğu bir kapsayıcı görevi görür. Bu kullanım koşullarını, bu öğreticinin ilerleyen bölümlerinde daha ayrıntılı olarak açıklanacaktır.  
  
4.  Artık Visual Studio arabiriminde görmeniz gereken aşağıda gösterilmiştir.  
  
    > [!NOTE]
    >  Pencere düzeniniz tam olarak bu çizim gibi görünmeyebilir. Kesin pencere düzeni, Visual Studio, kullandığınız programlama diline ve diğer etkenlere sürümüne bağlıdır. Ancak, tüm üç pencerenin de görüntülendiğini doğrulamanız gerekir.  
  
     ![IDE penceresi](../ide/media/express-ideoverview-visio.png "Express_IDEOverview_Visio")  
IDE penceresi  
  
     Arabirim üç pencere içerir: ana pencere, **Çözüm Gezgini**ve **özellikleri** penceresi.  
  
     Bu pencerelerden biri eksikse, menü çubuğundan seçerek varsayılan pencere düzenini geri **penceresi**, **pencere düzenini Sıfırla**. Windows, menü komutlarını kullanarak da görüntüleyebilirsiniz. Menü çubuğunda, **görünümü**, **Özellikler penceresi** veya **Çözüm Gezgini**. Başka bir pencere açıksa seçerek bunları kapatın **kapatmak** (x), sağ üst köşesinde düğmesini.  
  
5.  Çizim aşağıdaki pencereleri (sol üst köşeden saat yönünde Giden) göstermektedir:  
  
    -   **Ana pencere** Bu pencerede formlarla çalışma ve kod düzenleme gibi işin çoğunu gerçekleştirirsiniz. Çizimde, pencere, Form Düzenleyicisi'nde bir form gösterir. Pencerenin üst kısmındaki **başlangıç sayfası** sekmesi ve **Form1.cs [Design]** sekmesi görüntülenir. (Visual Basic'te, sekme adı .cs yerine .vb ile biter. cs.)  
  
    -   **Çözüm Gezgini penceresinde** Bu pencerede, görüntüleyebilir ve çözümünüzdeki tüm öğelerine gidin. Bir dosyanın içeriğini seçerseniz **özellikleri** penceresi değişiklikler. (Bu .cs Visual C# ve Visual Basic uzantısı .vb ile biten) bir kod dosyası açarsanız kod dosyası veya kod dosyası için bir tasarımcı görünür. Bir tasarımcı, düğmeler ve listeler gibi denetimler ileride ekleyebileceğiniz görsel bir yüzeydir. Visual Studio formları için tasarımcı Windows Form Tasarımcısı olarak adlandırılır.  
  
    -   **Özellikler penceresi** Bu pencerede diğer pencerelerde seçtiğiniz öğelerin özelliklerini değiştirebilirsiniz. Form1 seçerseniz, örneğin, alt başlık ayarlayarak değiştirebileceğiniz **metin** özelliğini değiştirebilirsiniz arka plan rengi ayarlayarak **Backcolor** özelliği.  
  
    > [!NOTE]
    >  Üst satırı **Çözüm Gezgini** gösterir **çözüm 'Pictureviewer olarak' (1 proje)**, Visual Studio çözüm için oluşturduğunuz anlamına gelir. Bir çözüm birden fazla proje içerebilir ancak şu an için yalnızca bir proje içeren çözümlerle çalışacaksınız.  
  
6.  Menü çubuğunda, **dosya**, **Tümünü Kaydet**.  
  
     Alternatif, **Tümünü Kaydet** aşağıdaki çizimin gösterdiği araç çubuğunda düğme.  
  
     ![Tüm araç çubuğu düğmesi Kaydet](../ide/media/express-iconsaveall.png "Express_IconSaveAll")  
Tüm araç çubuğu düğmesi Kaydet  
  
     Visual Studio klasör adını ve proje adını otomatik olarak doldurur ve daha sonra projeyi projeler klasörünüze kaydeder.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [2. adım: bilgisayarınızı Program Çalıştır](../ide/step-2-run-your-program.md).  
  
-   Genel Bakış konusuna dönmek için bkz: [öğretici 1: Resim Görüntüleyici oluşturma](../ide/tutorial-1-create-a-picture-viewer.md).



