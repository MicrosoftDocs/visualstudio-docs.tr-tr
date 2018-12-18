---
title: '6. adım: Düğme denetimlerinizi adlandırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e02c240f8e4146ce1c87fd1d90c30eb7787cef5d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303790"
---
# <a name="step-6-name-your-button-controls"></a>6. Adım: Düğme Denetimlerinizi Adlandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Formunuzda tek bir PictureBox vardır. Onu eklediğinizde IDE otomatik olarak bunu adlı **pictureBox1**. Adlı tek bir CheckBox vardır **checkBox1**. Bir süre sonra biraz kod yazacaksınız ve bu kod CheckBox'a ve PictureBox'a başvuracaktır. Olmadığı için bu denetimlerin her birinden yalnızca biri gördüğünüzde ne anlama geldiğini bilirsiniz **pictureBox1** veya **checkBox1** kodunuzda.  
  
> [!NOTE]
>  Adları Visual Basic'te, herhangi bir denetim adının varsayılan ilk harfi ilk harf olduğundan **PictureBox1**, **CheckBox1**ve benzeri.  
  
 Formunuzda dört düğme vardır ve IDE bunları adlı **button1**, **button2**, **button3**, ve **button4**. Yalnızca geçerli adlarına bakarak hangi düğmesi olduğunu bilemezsiniz **Kapat** düğmesi ve hangisinin **resim Göster** düğmesi. İşte bu nedenle düğme denetimlerinize daha açıklayıcı adlar vermek yararlıdır.  
  
 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo")bu konunun video sürümü için bkz: [öğretici 1: Visual Basic'te - Video 3 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205213) veya [öğretici 1: Resim Görüntüleyici C# ' - oluşturma Video 3](http://go.microsoft.com/fwlink/?LinkId=205202). Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır.  
  
### <a name="to-name-your-button-controls"></a>Düğme denetimlerinizi adlandırmak için  
  
1.  Form üzerinde seçin **Kapat** düğmesi. (Tüm düğmeler seçiliyse hala varsa seçimini iptal etmek için ESC tuşuna basın.) Kaydırın **özellikleri** penceresini görene kadar **(ad)** özelliği. ( **(Ad)** özelliği, Özellikler alfabetik olduğunda en olan.) Adla değiştirin **closeButton**, aşağıdaki resimde gösterildiği gibi.  
  
     ![CloseButton adıyla Özellikler penceresi](../ide/media/express-setnameproperty.png "Express_SetNameProperty")  
CloseButton adıyla Özellikler penceresi  
  
    > [!NOTE]
    >  İçin düğmenizin adını değiştirmeyi denerseniz **closeButton**, Kapat ve düğme sözcükleri arasına bir boşluk koyun, IDE bir hata iletisi görüntüler: "özellik değeri geçerli değil." Denetim adlarında boşluklara (ve diğer birkaç karaktere) izin verilmez.  
  
2.  Diğer üç düğmeyi yeniden adlandır **Arkaplandüğmesi**, **Temizledüğmesi**, ve **showButton**. Denetim Seçici açılan listesini seçerek adları doğrulayabilirsiniz **özellikleri** penceresi. Yeni düğme adları görüntülenir.  
  
3.  Çift **resim Göster** formundaki düğmesi. Alternatif, **resim Göster** formda düğmesine ve ardından ENTER tuşuna basın. Bunu yaptığınızda, IDE adlı ana penceresinde bir ek sekme açar **Form1.cs** (**Form1.vb** Visual Basic kullanılıyorsa). Bu sekme aşağıdaki resimde gösterildiği gibi formun arkasındaki kod dosyasını gösterir.  
  
     ![Visual C Form1.cs sekmesi&#35; kod](../ide/media/express-showbuttoncode.png "Express_ShowButtonCode")  
Visual C# koduyla Form1.cs sekmesi  
  
4.  Bu kod parçası üzerinde odaklanın. (Seçin **VB** aşağıda Visual Basic kullanıyorsanız kod Visual Basic sürümünü görüntülemek için sekmesinde.)  
  
     [!code-csharp[VbExpressTutorial1Step6#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial1Step6#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#1)]  
  
     Kodun adı aradığınız `showButton_Click()`. İçin kod dosyasını açtığınızda IDE bunu formun koduna eklemiştir **showButton** düğmesi. Bir formda bir denetim için kod dosyasını açtığınızda, tasarım zamanında, zaten mevcut değilse denetim için kod oluşturulur. Olarak da bilinen bu kod, bir *yöntemi*, programınızı çalıştırıp denetimi - bu durumda, seçin çalışır **resim Göster** düğmesi.  
  
    > [!NOTE]
    >  Bu öğreticide, otomatik olarak oluşturulan Visual Basic kodu parantez () arasındaki her şey kaldırılarak basitleştirilmiştir. Bu her gerçekleştiğinde, aynı kodu kaldırabilirsiniz. Programınız her iki şekilde çalışır. Öğreticiler kalanı için otomatik olarak oluşturulan herhangi bir kod mümkün olduğunda basitleştirilecektir.  
  
5.  Windows Form Tasarımcısı sekmesini tekrar seçin (**Form1.cs [Design]** Visual C# içinde **Form1.vb [Design]** Visual Basic'te) ve kod dosyası açın **resmi Temizle** Formun koduna bunun için bir yöntem oluşturmak için düğme. Bu, kalan iki düğme için yineleyin. Her defasında IDE formun kod dosyasına yeni bir yöntem ekler.  
  
6.  Birden fazla yöntem eklemek için onay kutusu denetimi için kod dosyasını ekleyin için Windows Form Tasarımcısı'nda açın bir `checkBox1_CheckedChanged()` yöntemi. Bu yöntem, her kullanıcı seçer veya temizler onay kutusunu çağrılır.  
  
    > [!NOTE]
    >  Bir programda çalışırken, Kod Düzenleyicisi'ni ve Windows Form Tasarımcısı arasında genellikle taşıyın. IDE, projenizde gezinmeyi kolaylaştırır. Kullanım **Çözüm Gezgini** çift tıklayarak Windows Form Tasarımcısı açmak için **Form1.cs** Visual C# veya **Form1.vb** Visual Basic veya menü çubuğunda, seçin**Görünümü**, **Tasarımcısı**.  
  
     Aşağıdaki yeni kod, Kod düzenleyicisinde gördüğünüz gösterir.  
  
     [!code-csharp[VbExpressTutorial1Step6#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step6#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#2)]  
  
     Eklediğiniz beş yönteme adlı *olay işleyicileri*, (örneğin, bir kullanıcı bir düğmeyi veya bir kutuyu seçmesi) bir olay gerçekleştiğinde programınız onları çağırır.  
  
     Tasarım zamanında IDE'de bir denetimin kodunu görüntülediğinizde, yoksak Visual Studio denetim için olay işleyicisi yöntemi ekler. Örneğin, bir düğmeye çift tıkladığınızda, IDE, bunun tıklama olayı (kullanıcı bir düğme seçtiği) için bir olay işleyicisi ekler. Bir onay kutusunu çift tıkladığınızda, IDE CheckedChanged olayı (kullanıcı seçerse ya da kutuyu her adlandırılan) için bir olay işleyicisi ekler.  
  
     Bir denetim için bir olay işleyici ekledikten sonra ona dilediğiniz zaman Windows Forms Tasarımcısı'ndan denetimi çift tıklayarak veya menü çubuğundan seçme dönebilirsiniz **görünümü**, **kod**.  
  
     Programları derleme ve yöntemler (olay işleyicileri dahil), istediğiniz herhangi bir ad olabilir adları önemlidir. IDE ile bir olay işleyicisi eklediğinizde, denetimin adını ve işlenen olayı temel alan bir ad oluşturur. Örneğin, adlı bir düğme için tıklama olayı **showButton** çağrılır `showButton_Click()` olay işleyicisi yöntemi. Ayrıca, açma ve Kapama parantezleri () genellikle yöntemleri ele belirtmek üzere yöntem adından sonra eklenir. İstediğiniz bir kod değişkeni adını değiştirmeye karar verirseniz, kod içindeki değişkene sağ tıklayın ve ardından **yeniden düzenleme**, **Yeniden Adlandır**. Koddaki bu değişkenin tüm örnekleri yeniden adlandırılır. Bkz: [düzenlemeyi yeniden adlandırma (C#)](../csharp-ide/rename-refactoring-csharp.md) veya [yeniden düzenleme ve yeniden adlandır iletişim kutusu](http://msdn.microsoft.com/library/001d2d81-9bb6-4e8e-ae3a-20c0daaa3959) daha fazla bilgi için.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [7. adım: bilgisayarınızı forma Ekle iletişim kutusu bileşenleri](../ide/step-7-add-dialog-components-to-your-form.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [5. adım: bilgisayarınızı formu için denetimler Ekle](../ide/step-5-add-controls-to-your-form.md).



