---
title: '4. adım: bir TableLayoutPanel denetimi ile formunuzu düzenleme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 164b0974d751dcfd164efab765432c1f9c23458c
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748302"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>4. adım: bir TableLayoutPanel denetimi ile formunuzu düzenleme
Bu adımda eklediğiniz bir <xref:System.Windows.Forms.TableLayoutPanel> Formunuza denetim. TableLayoutPanel daha sonra eklersiniz formdaki denetimlerin düzgün şekilde hizalayın yardımcı olur.

 ![video bağlantı](../data-tools/media/playvideo.gif)bu konuda video sürümü için bkz: [Öğreticisi 1: Visual Basic'te - Video 2 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205211) veya [Eğitmen 1: Resim Görüntüleyici C# ' - Video 2 oluşturma](http://go.microsoft.com/fwlink/?LinkId=205200). Bazı menü komutları ve diğer kullanıcı arabirimi öğeleri küçük farklar olduklarından bu videolar Visual Studio'nun önceki bir sürümünü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde geçerli sürümünde Visual Studio çalışır.

## <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>TableLayoutPanel denetimi ile formunuzu düzenleme

1.  Visual Studio IDE sol tarafında bulun **araç** sekmesi. Seçin **araç** sekmesinde ve **araç** görüntülenir. (Veya menü çubuğunda seçin **Görünüm** > **araç**.)

2.  Küçük bir üçgen simgesiyle seçin **kapsayıcıları** , aşağıdaki resimde gösterildiği gibi açmak için Grup.

     ![Kapsayıcılar grubu](../ide/media/express_toolbox.png)
**kapsayıcıları** grubu

3.  Formunuza denetimler düğmeleri, onay kutularını ve etiketler gibi ekleyebilirsiniz. TableLayoutPanel denetiminde çift **araç**. (Veya araç forma denetim sürükleyebilirsiniz.) Bunu yaptığınızda aşağıdaki resimde gösterildiği gibi IDE TableLayoutPanel denetimi formunuza ekler.

     ![TableLayoutPanel denetimi](../ide/media/express_formtablelayout.png)
**TableLayoutPanel** denetimi

    > [!NOTE]
    >  Bir pencere formunuz başlıkla içinde görünürse, TableLayoutPanel ekledikten sonra **TableLayoutPanel görevleri**, herhangi bir yere kapatmak için formun içine seçin. Bu pencere hakkında daha fazla daha sonra öğreticide öğreneceksiniz.

     Bildirim nasıl **araç** kendi sekmesini seçtiğinizde formunuz kapsayacak şekilde genişletir ve dışında herhangi bir yere seçtikten sonra kapatır. IDE otomatik gizleme özelliğini olmasıdır. Açmak veya kapatmak için herhangi bir windows otomatik gizleme değiştirme ve yerinde kilitlemek için pencerenin sağ üst köşesindeki Raptiye simgesini seçerek açabilirsiniz. Raptiye simgesinin aşağıdaki gibi görünür.

     ![Raptiye simgesinin](../ide/media/express_pushpintoolbox.png)
**Raptiye** simgesi

4.  TableLayoutPanel seçim yaparak seçili olduğundan emin olun. Açılan listenin en üstündeki bakarak hangi denetim seçilen doğrulayabilirsiniz **özellikleri** penceresinde, aşağıdaki resimde gösterildiği gibi.

     ![TableLayoutPanel denetimi gösteren Özellikler penceresi](../ide/media/express_controlspropwin.png)
**özellikleri** gösteren penceresi **TableLayoutPanel** denetimi

5.  Seçin **alfabetik** araç çubuğunda **özellikleri** penceresi. Bu özellikler listesini neden **özellikleri** Bu öğreticide özellikleri bulmak daha kolay hale getirir alfabetik sırada görüntülemek için penceresi.

6.  Denetim Seçici açılan en üstündeki listesidir **özellikleri** penceresi. Bu örnekte, bir denetim adlı gösterir `tableLayoutPanel1` seçilir. Ya da bir alana göre seçme denetimleri seçebileceğiniz **Windows Form Tasarımcısı** veya denetim seçicisini seçerek. TableLayoutPanel seçili, bulma **yerleştirme** özelliği ve **yerleştirme**, hangi ayarlanmalıdır **hiçbiri**. Aşağı açılan okunu değerin yanındaki görüntülendiğine dikkat edin. Oku seçin ve ardından **doldurun** düğmesini (büyük düğmesi ortasında), aşağıdaki resimde gösterildiği gibi.

     ![Özellikleri penceresinde seçili dolgulu](../ide/media/express_docktable.png)
**özellikleri** penceresiyle **doldurun** seçili

     *Yerleştirme* Visual Studio'da bir pencere başka bir pencere veya IDE alanına bağlı olduğunda başvuruyor. Örneğin, **özellikleri** penceresi - diğer bir deyişle, eklenmemiş ve Visual Studio içinde-serbest kaydırılan veya takılmamış karşı yerleşik **Çözüm Gezgini**.

7.  TableLayoutPanel ayarladıktan sonra **yerleştirme** özelliğine **doldurun**, formun tamamı paneli doldurur. Formu yeniden boyutlandırmak yeniden TableLayoutPanel yerleşik kalır ve kendisini uyacak şekilde yeniden boyutlandırır.

    > [!NOTE]
    >  Microsoft Office Word tablosunda gibi bir TableLayoutPanel çalışır: satırları ve sütunları olan ve tek bir hücre birden çok satır ve sütunları yayılabilir. Her bir hücre (düğme, onay kutusu veya bir etiket gibi) bir denetim basılı tutabilirsiniz. TableLayoutPanel olacaktır bir <xref:System.Windows.Forms.PictureBox> , tüm üst satırda kapsayıcı denetimi bir <xref:System.Windows.Forms.CheckBox> sol alt hücresini ve dört denetimi <xref:System.Windows.Forms.Button> sağ alt hücresini denetimlerinde.

8.  Şu anda, TableLayoutPanel iki eşit büyüklükteki satır ve iki eşit büyüklükteki sütun yok. Üst satırda ve sağ sütun hem; bu nedenle bunları yeniden boyutlandırmak çok büyük gerekir. İçinde **Windows Form Tasarımcısı**, TableLayoutPanel seçin. Sağ üst köşesinde şu şekilde görünen bir küçük siyah üçgen düğme vardır.

     ![Üçgen düğme](../ide/media/express_iconblacktriangle.gif)
**üçgen** düğmesi

     Bu düğme denetimi yardımcı görevleri sahip olduğunu gösterir özelliklerini otomatik olarak ayarlayın.

9. Aşağıdaki resimde gösterildiği gibi üçgen denetimin görev listesini görüntülemek için seçin.

     ![TableLayoutPanel görevleri](../ide/media/express_tablepanel.png)
**TableLayoutPanel** görevleri

10. Seçin **Düzenle satırları ve sütunları** görüntülemek için görev **sütun ve satır stilleri** penceresi. Seçin **Column1**ve boyutuna yüzde 15 emin olarak ayarlanıyor **yüzde** düğmesi seçilen ve girme **15** içinde **yüzde** kutusu. (Bu bir <xref:System.Windows.Forms.NumericUpDown> bir sonraki öğreticide kullanacaksınız denetimi.) Seçin **Column2** ve yüzde 85'e ayarlayın. Seçmeyin **Tamam** pencere kapanacaktır çünkü henüz düğmesine tıklayın. (Ancak bunu yaparsanız, bu görev listesini kullanarak yeniden açabilirsiniz.)

     ![TableLayoutPanel sütun ve satır stilleri](../ide/media/vs_tablelayoutpanel_setup.png)
**TableLayoutPanel** sütun ve satır stilleri

11. Gelen **Göster** aşağı açılan liste penceresinin en üstünde seçin **satırları**. Ayarlama **Row1** yüzde 90'e ve **satırı 2** yüzde 10 için.

12. Seçin **Tamam** düğmesi. TableLayoutPanel şimdi büyük üst satır, bir küçük alt satır, küçük bir sol sütunda ve büyük sağ sütun olmalıdır. TableLayoutPanel sütunları ve satırları seçerek boyutlandırabilirsiniz **tableLayoutPanel1** formun ve satır ve sütun kenarlıkları sürükleyerek.

     ![Yeniden boyutlandırılan TableLayoutPanel ile Form1](../ide/media/vs_formafterlayoutpanel.png)
**Form1** ile yeniden boyutlandırılabilir **TableLayoutPanel**

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Öğretici bir sonraki adıma dönmek için bkz: [5. adım: formunuza denetimler ekleme](../ide/step-5-add-controls-to-your-form.md).

-   Eğitmen önceki adıma dönmek için bkz: [3. adım: form özelliklerinizi ayarlama](../ide/step-3-set-your-form-properties.md).
