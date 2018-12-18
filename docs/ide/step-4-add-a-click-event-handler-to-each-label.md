---
title: '4. adım: her etikete click olay işleyicisi ekleme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04054d353e0260e7a38a189fc6946aacd353b6c4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897959"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>4. adım: her etikete click olay işleyicisi ekleme

Eşleştirme oyunu aşağıdaki gibi çalışır:

1. Oyuncu gizli simge içeren karelerden birini seçtiğinde, program simge rengini siyaha dönüştürerek bu simgeyi oyuncuya gösterir.

2. Oyuncu daha sonra başka bir gizli simge seçer.

3. Simgeler eşleşirse görünür olarak kalırlar. Aksi takdirde iki simge de tekrar gizlenir.

   Programınızın bu şekilde çalışmasını sağlamak için eklediğiniz bir <xref:System.Windows.Forms.Control.Click> Seçilen etiketin rengini değiştiren olay işleyicisi.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Her etikete bir tıklama olayı işleyicisi eklemek için

1.  Formda açın **Windows Form Tasarımcısı**. İçinde **Çözüm Gezgini**, seçin *Form1.cs* veya *Form1.vb*. Menü çubuğunda, **görünümü** > **Tasarımcısı**.

2.  İlk etiket denetimini belirleyip seçin. Ardından, basılı **Ctrl** seçerken her biri diğer etiketlerin seçmek için anahtar. Her etiketin seçildiğinden emin olun.

3.  Seçin **olayları** araç çubuğunda düğme **özellikleri** penceresini görüntülemek için **olayları** sayfasını **özellikleri** penceresi. Ekranı aşağı kaydırarak **tıklayın** olay girin **label_Click** kutusunda, aşağıdaki resimde gösterildiği gibi.

     ![Tıklama olayını gösteren Özellikler penceresi](../ide/media/express_labelclick.png)

4.  Seçin **Enter** anahtarı. IDE ekler bir `Click` adlı olay işleyicisi `label_Click()` koda ve bunu formdaki etiketlerin her kancaları.

5.  Kodun geri kalanını aşağıdaki gibi doldurun:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

    > [!NOTE]
    > Kopyalar ve yapıştırırsanız `label_Click()` varolan değiştirdiğinizden emin kodu el ile girmek yerine kod bloğunu `label_Click()` kod. Aksi takdirde, yinelenen bir kod bloğu ile karşı karşıya kalırsınız.

    > [!NOTE]
    > Size tanıdık gelebilir `object sender` olarak kullanılan hizmet örneğiyle aynı olay işleyicisinin üst [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md) öğretici. Kancalandı tıklama olayları tek bir olay işleyicisi yöntemine farklı etiket denetimi, hangi etiketin ne olursa olsun, kullanıcının seçtiği aynı yöntem çağrılır. Olay işleyicisi yöntemi adı kullanması için hangi etiketin seçildiğini bilmesi gerekir `sender` etiket denetimini tanımlamak için. Yöntemin ilk satırında program, olmayan genel bir nesne, ancak özellikle bir etiket denetimi olduğunu ve adını kullandığını söyler `clickedLabel` etiketin özelliklerine ve yöntemlere erişmek için.

     Bu yöntem ilk denetler olmadığını `clickedLabel` başarıyla dönüştürüldü (bir nesneden bir etiket kontrolüne atama). Başarısız bir değeri olup olmadığını `null` (C#) veya `Nothing` (Visual Basic) ve yöntemde kodun geri kalanını yürütmek istemiyorsanız. Ardından, yöntem etiketin kullanarak seçilen etiketin metin rengini denetler **ForeColor** özelliği. Etiketin metin rengi siyah ise, simge zaten seçilmiş ve yöntem bitmiş demektir. (Budur `return` deyiminin yaptığı: programa yöntemi yürütmeyi durdurmasını söyler.) Aksi takdirde simge seçilmemiş demektir ve dolayısıyla program etiketin metin rengini siyah olarak değiştirir.

6.  Menü çubuğunda, **dosya** > **Tümünü Kaydet** ilerlemenizi kaydedin ve ardından menü çubuğunda, **hata ayıklama** > **Başlat Hata ayıklama** seçerek programınızı çalıştırın. Mavi arka planlı boş bir form görmeniz gerekir. Formdaki hücrelerden herhangi birini seçtiğinizde, simgelerden birinin görünür hale gelmesi gerekir. Formda farklı yerler seçmeye devam edin. Siz simgeleri seçtikçe görünmeleri gerekir.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Sonraki öğretici adımına gitmek için bkz: [5. adım: etiket başvuruları ekleme](../ide/step-5-add-label-references.md).

-   Önceki öğretici adımına dönmek için bkz: [3. adım: her etikete rasgele simge atama](../ide/step-3-assign-a-random-icon-to-each-label.md).
