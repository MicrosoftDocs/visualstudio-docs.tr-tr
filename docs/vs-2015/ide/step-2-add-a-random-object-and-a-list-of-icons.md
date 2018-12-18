---
title: '2. adım: rasgele nesne ve simge listesi ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2740e61de964f3b0c72f44e9a5c11018894c4fe0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226661"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>2. Adım: Rasgele Nesne ve Simge Listesi Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu adımda, oyun için bir grup eşleşen simge oluşturuyorsunuz. Her simge, form üzerindeki TableLayoutPanel denetiminde rasgele iki hücreye eklenir. Bunu yapmak için iki kullandığınız `new` deyimleri iki nesne oluşturmak için. İlki bir `Random` matematik sınavı oyununda kullanılan gibi bir nesne. Bu koddaki kullanım amacıysa, TableLayoutPanel denetiminde rasgele hücre seçmektir. İçin yeni olabilecek ikinci nesne bir `List` rasgele seçilen simgeleri depolamak için kullanılan nesne.  
  
### <a name="to-add-a-random-object-and-a-list-of-icons"></a>Rasgele nesne ve bir simge listesi eklemek için  
  
1.  İçinde **Çözüm Gezgini**, seçin **Form1.cs** Visual C# kullanıyorsanız veya **Form1.vb** Visual Basic kullanıyorsanız ve menü çubuğunda, ardından **görüntüle** , **Kod**. Alternatif olarak, seçtiğiniz **F7** anahtar veya çift **Form1** içinde **Çözüm Gezgini**.  
  
     Böylece Form1'in arkasındaki kod modülü görüntülenir.  
  
2.  Varolan kod içine aşağıdaki kodu ekleyin.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#1)]  
  
     Visual C# kullanıyorsanız olması emin yerleştirdiğiniz kodu açılış kaşlı ayracından sonra ve yalnızca sınıf bildiriminden sonra (`public partial class Form1 : Form`). Visual Basic kullanıyorsanız sınıf bildiriminden hemen sonra kod yerleştirin (`Public Class Form1`).  
  
3.  Eklerken `List` nesne, fark **IntelliSense** açılır pencere. Aşağıdaki bir Visual C# örneği olmakla birlikte, Visual Basic'te liste eklediğinizde de benzer bir metin görüntülenir.  
  
     ![Click gösteren Özellikler penceresi olay](../ide/media/express-listintellisense.png "Express_ListIntellisense")  
IntelliSense penceresi  
  
    > [!NOTE]
    >  IntelliSense penceresi yalnızca kodu el ile girdiğinizde görünür. Kodu kopyalayıp yapıştırırsanız görünmez.  
  
     Kodu (ve açıklamaları) küçük bölümler halinde incelerseniz anlaması daha kolay olur. Programlarınız `List` farklı türlerde öğeler izlemek için nesneleri. Bir liste; sayıları, doğru/yanlış değerlerini, metinleri veya diğer nesneleri barındırabilir. Bile olabilir bir `List` diğer tutan nesne `List` nesneleri. Bir listedeki öğeler adlı *öğeleri*, ve her liste yalnızca öğesi bir tür tutar. Öyleyse, bir sayı listesi yalnızca sayıları tutabilir; bu listeye metin ekleyemezsiniz. Benzer şekilde, doğru/yanlış değerlerini içeren bir listeye sayı ekleyemezsiniz.  
  
     Oluştururken bir `List` kullanarak nesne bir `new` deyimi içinde depolamak istediğiniz veri türünü belirtmeniz gerekir. İşte bu nedenle en üstündeki araç ipucu **IntelliSense** penceresi listesinde öğelerin türlerini gösterir. Ayrıca, budur `List<string>` (Visual C#) ve `List(Of String)` (Visual Basic'te) anlamına gelir: Bu bir `List` öğelerini tutan nesne `string` veri türü. Programınızın metin depolamak için kullandığı bir dizedir hangi sağındaki araç ipucu olduğu **IntelliSense** penceresi, unsurdur.  
  
4.  Visual Basic'te önce geçici bir dizin oluşturulması gerekmesine karşın, Visual C# ortamında listenin tek bir deyimle oluşturulabilmesinin nedenini bir düşünün. Visual C# diline sahip olmasıdır *koleksiyon başlatıcıları*, liste değerleri kabul etmek için hazırlayın. Visual Basic'te bir koleksiyon başlatıcısı kullanabilirsiniz. Ancak, önceki Visual Basic sürümü ile uyumluluk açısından önceki kodu kullanmanızı öneririz.  
  
     Bir koleksiyon Başlatıcısı kullandığınızda bir `new` ifade, sonra yeni `List` nesnesi oluşturulur, program, kaşlı ayraçlar içinde sağladığınız verilerle doldurur. Bu durumda, adlı dize listesi elde **simgeler**, ve bu liste on altı dize içeren başlatılır. Bu dizelerin her biri tek bir harftir ve bunların tümü etiketlerde yer alacak simgelere karşılık gelir. Dolayısıyla, oyunda bir çift ünlem işareti, bir çift büyük N harfi, bir çift virgül vs. olacaktır. (Bu karakterler Webdings yazı tipine ayarlandığında, otobüs, bisiklet, örümcek vb. simgeler olarak görünür.) `List` Nesne TableLayoutPanel panelindeki her hücreye tüm, on altı dize olacaktır.  
  
    > [!NOTE]
    >  Visual Basic'te, aynı sonucu elde etmek, ancak dizeler ardından dönüştürülür geçici bir dizinin ilk şekilde yerleştirilir bir `List` nesne. Örneğin, dizilerin sabit boyutlu oluşturulması dışında, dizi bir listeye benzer. Listelerin gerektiğinde daralabilmesi ve genişleyebilmesi bu programda önem taşır.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [3. adım: her etikete rasgele simge atama](../ide/step-3-assign-a-random-icon-to-each-label.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [1. adım: Proje oluşturma ve tablo bilgisayarınızı formuna ekleme](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).



