---
title: '3. adım: Form özelliklerinizi ayarlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 64e197e3f6f34cc46d91c330b4d5f80b3c6ce578
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848637"
---
# <a name="step-3-set-your-form-properties"></a>3. Adım: Form Özelliklerinizi Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ardından, kullandığınız **özellikleri** penceresini kullanarak formunuzun görünüşünü değiştirme.  
  
 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo")bu konunun video sürümü için bkz: [öğretici 1: Visual Basic'te - Video 1 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205209) veya [öğretici 1: Resim Görüntüleyici C# ' - oluşturma 1 video](http://go.microsoft.com/fwlink/?LinkId=205199). Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır.  
  
### <a name="to-set-your-form-properties"></a>Form özelliklerinizi ayarlamak için  
  
1. Windows Forms Designer'a baktığınızdan emin olun. Visual Studio tümleşik geliştirme ortamında (IDE) seçin **Form1.cs [Design]** sekme (veya **Form1.vb [Design]** Visual Basic sekmesini).  
  
2. Form içinde herhangi bir yeri seçin **Form1** seçin. Bakmak **özellikleri** şimdi form özelliklerini gösteren penceresinde. Formlar çeşitli özelliklere sahiptir. Örneğin, ön plan ve arka plan rengi, görünen başlık metnini ayarlayabileceğiniz formun üst kısmında, form ve diğer özellikleri boyutunu.  
  
   > [!NOTE]
   >  Varsa **özellikleri** penceresi görünmüyorsa, kare seçerek programınızı durdurmak **hata ayıklamayı Durdur** düğme araç çubuğundan veya pencereyi kapatmanız yeterlidir. Program durdurulursa ve hala görmüyorsanız **özellikleri** menü çubuğunda, pencere **görünümü**, **Özellikler penceresi**.  
  
3. Form seçildikten sonra bulma **metin** özelliğinde **özellikleri** penceresi. Listenin nasıl sıralandığına bağlı olarak aşağı kaydırmanız gerekebilir. Seçin **metin**, türü **resim görüntüleyici**ve ardından ENTER TUŞUNA basın.  Formunuzda şimdi metin olmalıdır **resim görüntüleyici** , başlık çubuğunda ve **özellikleri** penceresi aşağıdaki resme benzer görünmelidir.  
  
    ![Özellikler penceresi](../ide/media/express-edittextproperty.png "Express_EditTextProperty")  
   Özellik penceresi  
  
   > [!NOTE]
   >  Özellikler, kategorilere ayrılmış veya alfabetik görünüm ile sıralanabilir. Düğmeleri kullanarak bu iki görünüm arasında geçiş yapabilirsiniz **özellikleri** penceresi. Bu öğreticide, özellikleri alfabetik görünüm aracılığıyla bulmak daha kolay olur.  
  
4. Windows Forms Tasarımcısı'na geri dönün. Formun alt sağ altındaki küçük beyaz kare olan ve aşağıdaki gibi görünür, formun sağ alt sürükleme işleyicisini seçin.  
  
    ![Sürükleme tutamacı](../ide/media/express-bottomrt-drag.png "Express_BottomRT_Drag")  
   Sürükleme tutamacı  
  
    Böylece form daha geniş ve daha uzun formu yeniden boyutlandırmak için tutamacı sürükleyin.  
  
5. Bakmak **özellikleri** penceresinde dikkat **boyutu** özelliği değişti. **Boyutu** her zaman formun yeniden boyutlandırma özelliğini değiştirir. Bir form boyuta gören yaklaşık 550, yeniden boyutlandırmak için formun tutamacını sürüklemeyi deneyin 350 (tam olmasına gerek yoktur), bu proje için iyi çalışmalıdır. Alternatif olarak, doğrudan değerler girebilirsiniz **boyutu** özelliği ve ardından ENTER tuşuna basın.  
  
6. Programınızı tekrar çalıştırın. Unutmayın, programınızı çalıştırmak için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz.  
  
   - Seçin **F5** anahtarı.  
  
   - Menü çubuğunda, **hata ayıklama**, **hata ayıklamayı Başlat**.  
  
   - Araç çubuğunda **hata ayıklamayı Başlat** gibi görünen bir düğme.  
  
      ![Hata ayıklama araç çubuğu düğmesini Başlat](../ide/media/express-icondebug.png "Express_IconDebug")  
     Hata ayıklama araç çubuğu düğmesini Başlat  
  
     Tıpkı daha önce IDE oluşturur ve programınızı çalıştırır ve bir pencere görüntülenir.  
  
7. Sonraki adıma geçmeden önce programınızı durdurmak, IDE izin vermeyeceğinden çalışırken programınızı değiştirin. Unutmayın, programınızı durdurmak için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz.  
  
   -   Araç çubuğunda **hata ayıklamayı Durdur** düğmesi.  
  
   -   Menü çubuğunda, **hata ayıklama**, **hata ayıklamayı Durdur**.  
  
   -   Üst köşesinde X düğmesini **Form1** penceresi.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [4. adım: düzenleme kullanıma bilgisayarınızı Form bir TableLayoutPanel denetimiyle](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [2. adım: bilgisayarınızı Program Çalıştır](../ide/step-2-run-your-program.md).



