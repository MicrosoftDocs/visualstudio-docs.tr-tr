---
title: '2. adım: rasgele nesne ve simge listesi ekleme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 84c9c837fdb812b18f72e768b8ee528118b28777
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746838"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>2. adım: rasgele nesne ve simge listesi ekleme
Bu adımda, oyun için bir grup eşleşen simge oluşturuyorsunuz. Her simge, form üzerindeki TableLayoutPanel denetiminde rasgele iki hücreye eklenir. Bunu yapmak için iki kullandığınız `new` deyimleri iki nesne oluşturma. İlki bir <xref:System.Random> gibi matematik testi oyunda kullanılan nesne. Bu koddaki kullanım amacıysa, TableLayoutPanel denetiminde rasgele hücre seçmektir. Size yeni olabilir, ikinci nesne bir <xref:System.Collections.Generic.List%601> rastgele seçilmiş simgeleri depolamak için kullanılan nesne.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>Rasgele nesne ve simge listesi ekleme

1.  İçinde **Çözüm Gezgini**, seçin *Form1.cs* Visual C# kullanıyorsanız veya *Form1.vb* Visual Basic kullanıyorsanız ve menü çubuğunda seçin **görünümü**   >  **Kod**. Alternatif olarak, seçtiğiniz **F7** anahtar veya çift **Form1** içinde **Çözüm Gezgini**.

     Böylece Form1'in arkasındaki kod modülü görüntülenir.

2.  Varolan kod içine aşağıdaki kodu ekleyin.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

     Visual C# kullanıyorsanız olması emin yerleştirdiğiniz kodu parantezinden ve sınıf bildiriminden hemen sonra (`public partial class Form1 : Form`). Visual Basic kullanıyorsanız, sonra sağ sınıf bildirimi kodu put (`Public Class Form1`).

3.  Liste nesnesi eklerken, **IntelliSense** açılır penceresi. Aşağıdaki bir Visual C# örneği olmakla birlikte, Visual Basic'te liste eklediğinizde de benzer bir metin görüntülenir.

     ![Özellikler penceresini tıklatın gösteren olay](../ide/media/express_listintellisense.png) IntelliSense penceresi

    > [!NOTE]
    >  Yalnızca kodu el ile girdiğinizde, IntelliSense penceresi görüntülenir. Kodu kopyalayıp yapıştırırsanız görünmez.

     Kodu (ve açıklamaları) küçük bölümler halinde incelerseniz anlaması daha kolay olur. Programlarınızı liste nesneleri farklı türlerde öğelerini izlemek için kullanabilirsiniz. Bir liste; sayıları, doğru/yanlış değerlerini, metinleri veya diğer nesneleri barındırabilir. Hatta diğer liste nesneleri içeren bir liste nesnesi olabilir. Bir listedeki öğeler öğe olarak adlandırılır ve her liste öğesi bir tür yalnızca tutar. Öyleyse, bir sayı listesi yalnızca sayıları tutabilir; bu listeye metin ekleyemezsiniz. Benzer şekilde, doğru/yanlış değerlerini içeren bir listeye sayı ekleyemezsiniz.

     Oluştururken bir `List` kullanarak nesne bir `new` deyimi içinde depolamak istediğiniz veri türünü belirtmeniz gerekir. İşte bu nedenle en üstündeki araç ipucu **IntelliSense** penceresi listedeki öğeleri türlerini gösterir. Ayrıca, nedir `List<string>` (Visual C#) ve `List(Of String)` (Visual Basic'te) anlamına gelir: Bu bir `List` öğelerini tutan nesnenin `string` veri türü. Programınızın metin depolamak için kullandığı bir dizedir hangi araç ipucunu sağa olduğu **IntelliSense** penceresi size bildiren.

4.  Visual Basic'te önce geçici bir dizin oluşturulması gerekmesine karşın, Visual C# ortamında listenin tek bir deyimle oluşturulabilmesinin nedenini bir düşünün. Bu Visual C# dili sahip olmasından *koleksiyon başlatıcıları*, liste değerleri kabul etmek için hazırlayın. Visual Basic'te bir koleksiyon başlatıcısı kullanabilirsiniz. Ancak, önceki Visual Basic sürümü ile uyumluluk açısından önceki kodu kullanmanızı öneririz.

     Koleksiyon Başlatıcısı ile kullandığınızda, bir `new` deyimi, yeni liste nesne oluşturulduktan sonra program doldurur, süslü ayraçlar içinde sağlanan verileri ile. Bu durumda, simgeler adlı dizelerinin listesini almak ve altı dizeleri içeren bu listeyi başlatıldı. Bu dizelerin her biri tek bir harftir ve bunların tümü etiketlerde yer alacak simgelere karşılık gelir. Dolayısıyla, oyunda bir çift ünlem işareti, bir çift büyük N harfi, bir çift virgül vs. olacaktır. (Bu karakterler Webdings yazı tipine ayarlandığında, otobüs, bisiklet, örümcek vb. simgeler olarak görünür.) Liste nesnesi bir TableLayoutPanel panelinde her hücre için tüm, altı dizeleri olacaktır.

    > [!NOTE]
    >  Visual Basic'te aynı sonucu elde ancak dizeler ardından bir liste nesnesine dönüştürülen geçici bir dizinin ilk şekilde yerleştirilir. Örneğin, dizilerin sabit boyutlu oluşturulması dışında, dizi bir listeye benzer. Listelerin gerektiğinde daralabilmesi ve genişleyebilmesi bu programda önem taşır.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Öğretici bir sonraki adıma dönmek için bkz: [3. adım: her etikete rasgele simge atama](../ide/step-3-assign-a-random-icon-to-each-label.md).

-   Eğitmen önceki adıma dönmek için bkz: [1. adım: Proje oluşturma ve formunuza tablo ekleme](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
