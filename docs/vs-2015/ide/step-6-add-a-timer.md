---
title: '6. adım: Zamanlayıcı ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 577ef28c49d769bac8d979330f181c67b8d35687
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293390"
---
# <a name="step-6-add-a-timer"></a>6. Adım: Zamanlayıcı Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ardından, eklediğiniz bir **Zamanlayıcı** eşleştirme oyunu denetimi. Zamanlayıcı belirtilen milisaniye sayısı kadar bekler ve ardından olarak adlandırılan bir olayı tetikler bir *değer çizgisi*. Bu olay, bir eylemi başlatmak veya eylemi düzenli aralıklarla yinelemek için kullanışlıdır. Bu durumda, oyuncuların iki simge seçmesini sağlamak ve simgeler eşleşmez ise, kısa bir süre sonra bu iki simgeyi yeniden gizlemek için bir zamanlayıcı kullanacaksınız.  
  
### <a name="to-add-a-timer"></a>Zamanlayıcı eklemek için  
  
1.  Windows Form Tasarımcısı araç kutusundan seçin **Zamanlayıcı** (içinde **bileşenleri** kategori) ve ENTER tuşuna basın veya zamanlayıcıya forma bir zamanlayıcı denetimi eklemek için çift tıklayın. Adlı Zamanlayıcı simgesinin **Süreölçer1**, formun altındaki bir alanda aşağıdaki resimde gösterildiği gibi görünmesi gerekir.  
  
     ![Zamanlayıcı](../ide/media/express-timer.png "Express_Timer")  
Zamanlayıcı  
  
    > [!NOTE]
    >  Araç kutusu boş ise, araç kutusunu açmadan önce formun arkasındaki kodu değil de, form tasarımcısını seçtiğinizden emin olun.  
  
2.  Seçin **Süreölçer1** Zamanlayıcıyı seçmek için simge. İçinde **özellikleri** penceresi, Özellikler olayları görüntüleme alanından anahtar. Ardından Zamanlayıcının **aralığı** özelliğini **750**, ancak kendi **etkin** özelliğini **False**. **Aralığı** özelliği Zamanlayıcı arasında beklenecek süreyi belirten *ticks*, veya Tick olayını ne zaman tetikleyeceğini. 750 değeri zamanlayıcıya, Tick olayını tetiklemeden önce saniyenin dörtte üçü kadar (750 milisaniye) beklemesini bildirir. Sizi ararız `Start()` yalnızca oyuncu ikinci etiketi seçtikten sonra zamanlayıcıyı başlatmak için yöntemi.  
  
3.  Zamanlayıcıyı seçmek Windows Forms Tasarımcısı'nda denetimini ve ardından ENTER tuşuna basın veya boş eklemek için zamanlayıcıya çift tıklayarak **değer çizgisi** olay işleyicisi. Kodu aşağıdaki kodla değiştirin ya da aşağıdaki kodu olay işleyicisine el ile girin.  
  
     [!code-csharp[VbExpressTutorial4Step6#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial4Step6#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#7)]  
  
     Tick olayı işleyicisi üç şeyi yapar: ilk olarak, çağırarak Zamanlayıcının çalışmadığından emin olur `Stop()` yöntemi. İki başvuru değişkeni kullanıyorsa `firstClicked` ve `secondClicked`, oyuncunun seçtiği iki etiketin simgelerini yeniden görünmez yapmak için. Son olarak, sıfırlar `firstClicked` ve `secondClicked` başvuru değişkenlerini `null` Visual C# ve `Nothing` Visual Basic'te. Programın kendini sıfırlama şekli olması nedeniyle bu adım önemlidir. Bunu hiçbirini izlememektedir anda `Label` denetimleri ve oyuncunun yeniden bir etiket seçmesi için hazır.  
  
    > [!NOTE]
    >  A `Timer` nesnesinin bir `Start()` Zamanlayıcıyı başlatan bir yöntemi ve bir `Stop()` yöntemi. Zamanlayıcının ayarlandığında **etkin** özelliğini **True** içinde **özellikleri** penceresinde başladıktan program başlar başlamaz yolunda. Ancak çıktığınızda ayarlı olarak **False**, çağrılıncaya kadar işlemeye başlamaz kendi `Start()` yöntemi çağrılır. Normalde, bir Zamanlayıcının Tick olayını tekrar tekrar kullanarak tetiklemeden **aralığı** saat döngüleri arasında kaç milisaniye belirlemek için özellik. Fark etmiş olabilirsiniz nasıl Zamanlayıcının `Stop()` Tick olayı içinde yöntemi çağrılır. Zamanlayıcıyı koyar *tek sefer moduna*, yani `Start()` yöntemi çağrıldığında, belirtilen aralık kadar bekleyip, tek bir Tick olayını tetikler ve sonra durur.  
  
4.  Zamanlayıcıyı iş başında görmek için kod düzenleyicisine gidin ve üst ve alt için aşağıdaki kodu ekleyin `label_Click()` olay işleyicisi yöntemi. (Ekliyorsunuz bir `if` deyimi üst ve alt kısmına; üç deyimi yöntemin geri kalanı aynı kalır.)  
  
     [!code-csharp[VbExpressTutorial4Step6#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial4Step6#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#8)]  
  
     Yönteminin üst kısmına kodu değerini kontrol ederek Zamanlayıcının başlatılıp başlatılmadığını denetler **etkin** özelliği. Bu şekilde, varsa oyuncunun seçtiği ilk ve ikinci `Label` denetimleri ve ve Zamanlayıcı başlarsa, üçüncü bir etiket seçildiğinde hiçbir şey olmayacaktır.  
  
     Kod yöntemi ayarlar altındaki `secondClicked` ikinci izlemek için başvuru değişkenini `Label` oyuncunun seçtiği ve ardından bu etiketin simge rengini siyaha görünür yapmak için ayarlar denetimi. Daha sonra, 750 milisaniye bekler ve tek bir Tick olayı tetiklemesi için zamanlayıcıyı tek sefer modunda başlatır. Zamanlayıcının Tick olayı işleyicisi iki simgeyi de gizler ve sıfırlar `firstClicked` ve `secondClicked` başvuru değişkenlerini form oyuncunun başka bir simge çifti seçmesine hazır olması.  
  
5.  Programınızı kaydedin ve çalıştırın. Bir simge seçin; bu simge görünür duruma gelir.  
  
6.  Başka bir simge seçin. Kısa bir süre görünür ve sonra iki simge birden kaybolur. Bunu birçok kez tekrar edin. Form artık, seçtiğiniz birinci ve ikinci simgeleri takip ediyor ve simgelerin kaybolmasını sağlamadan önce duraklamak için zamanlayıcıyı kullanıyor.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [adım 7: Keep Pairs Visible](../ide/step-7-keep-pairs-visible.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [adım 5: Add Label References](../ide/step-5-add-label-references.md).



