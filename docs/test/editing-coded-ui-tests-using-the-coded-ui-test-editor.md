---
title: Kodlanmış UI testlerini düzenleme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6c45a8abceacb1d566ca5aba382e7955f1c2601e
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895567"
---
# <a name="edit-coded-ui-tests-using-the-coded-ui-test-editor"></a>Kodlanmış UI Test düzenleyicisini kullanarak kodlanmış UI testlerini düzenleme

Kodlanmış UI Test Düzenleyicisi'ni kullanarak kodlanmış UI testlerini kolayca değiştirmenize olanak tanır. Kodlanmış UI Test Düzenleyicisi'ni kullanarak bulun, görüntüleyin ve test yöntemlerinizi ve UI eylemlerini özelliklerini düzenleyin. Ayrıca, UI kontrol haritasını görüntülemek ve bunların ilgili denetimleri düzenlemek için kullanabilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

## <a name="features-of-the-coded-ui-test-editor"></a>Kodlanmış UI Test Düzenleyicisi'nin özellikleri

Kodlanmış UI Test Düzenleyicisi'ni kullanarak daha hızlı ve kod düzenleyicisini kullanarak kodlanmış UI test yöntemlerinizde kod düzenleme daha etkilidir. Kodlanmış UI Test Düzenleyicisi ile araç ve kısayol menüleri hızla bulup UI eylemlerini ve denetimleri ile ilgili özellik değerlerini değiştirmek için kullanabilirsiniz. Örneğin, aşağıdakileri gerçekleştirmek için kodlanmış UI Test Düzenleyicisi araç kullanabilirsiniz:

![UI Test Düzenleyicisi](../test/media/uitesteditor.png)

1. [Bulma](../ide/finding-and-replacing-text.md) UI eylemlerini ve denetimlerini bulmanıza yardımcı olur.

2. **Silme** istenmeyen UI eylemlerini kaldırır.

3. **Yeniden adlandırma** test yöntemleri ve denetimlerin adlarını değiştirir.

4. **Özellikleri** açılır **özellikleri** seçili öğe için bir pencere.

5. **Yeni bir yönteme Böl** UI eylemlerini modülerleştirmek olanak tanır.

6. **Kodu Taşı** özel kod test yöntemlerinizi ekler.

7. **Öncesine gecikme Ekle** milisaniye cinsinden belirtilen bir UI eyleminden önce bir duraklama ekler.

8. **UI denetimini Bul** testten geçirilen uygulamanın UI denetimi konumunu belirtir.

9. **Tümünü Bul** doğrulamaya yardımcı olur, özellik ve uygulama denetimleri yapılan önemli değişiklikler denetler.

Açtığınızda *UIMap.uitest* dosya bağlı olan kodlanmış UI testleri, kodlanmış UI test açılarak **kodlanmış UI Test Düzenleyicisi**. Aşağıdaki yordamlar nasıl daha sonra bulmak ve test yöntemleri ve özellikleri UI eylemlerini ve düzenleyici araç çubuğu ve kısayol menülerini kullanarak denetimleri için Düzen açıklar.

## <a name="open-a-coded-ui-test"></a>Kodlanmış UI testi Aç

Görüntüleyin ve düzenleyin, Visual C# ve Visual Basic tabanlı kodlanmış UI testi kullanarak **kodlanmış UI Test Düzenleyicisi**.

![Bağlam menüsü düzen ile kodlanmış UI Test Oluşturucusu](../test/media/editcodeduitest.png)

İçinde **Çözüm Gezgini**, kısayol menüsünü açın *UIMap.uitest* ve **açın**. Kodlanmış UI testi görüntülenen **kodlanmış UI Test Düzenleyicisi**. Şimdi, görüntüleyin ve kayıtlı yöntemleri, Eylemler ve karşılık gelen denetimlerinde kodlanmış UI testi düzenleyin.

> [!TIP]
> Bir yöntem içinde bulunan bir UI eyleminden seçtiğinizde **UI eylemlerini** karşılık gelen denetimin bölmesinde vurgulanır. UI eylemi veya denetim özelliklerini de değiştirebilirsiniz.

## <a name="modify-ui-action-and-control-properties"></a>UI eylemi ve denetim özelliklerini değiştirme

Kodlanmış UI Test Düzenleyicisi'ni kullanarak hızla bulun ve tüm UI eylemlerini test yöntemlerinizde görüntüleme. Düzenleyicide UI eylemini seçtiğinizde ilgili denetimin otomatik olarak vurgulanır. Benzer şekilde, bir denetimi seçtiğinizde, ilişkili UI eylemlerini vurgulanır. Bir UI eyleminden ya da bir denetimi seçtiğinizde, ardından kullanımı kolay olan **özellikleri** penceresi ile karşılık gelen özelliklerini değiştirmek için.

![UI eylem özelliklerini](../test/media/codeduiedituiaction.png)

Bir UI eylem özelliklerini değiştirmek için **UI eylemi** bölmesinde UI eylem özelliklerini yı düzenlemek istediğiniz bir UI eyleminden içeren test yöntemi genişletin ve ardından Özellikler penceresini kullanarak özelliklerini değiştirin.

Örneğin, bir sunucu kullanılamıyor ve web tarayıcınızı ile ilişkili bir kullanıcı Arabirimi eylemine sahip belirten **Web sayfasına gidin '<http://Contoso1/default.aspx>'**, URL'sine değişebilir `'http://Contoso2/default.aspx'`.

![Denetim Özellikleri](../test/media/codeduitestcontrolprop.png)

Bir denetimin özelliklerini değiştirme UI eylemlerini aynı şekilde gerçekleştirilir. İçinde **UI kontrol haritasını** bölmesinde, düzenleme ve kullanma özelliklerini değiştirmek istediğiniz denetimi seçin **özellikleri** penceresi.

Örneğin, bir geliştirici değişmiş olabilecek **(ID)** "idSubmit" "idLogin" test edilen uygulamanın kaynak kodunda bir düğme denetimi özelliği İle **(ID)** özellik, uygulama değişti, kodlanmış UI testi düğme denetimini bulmanız mümkün olmayacaktır ve başarısız olur. Bu durumda, test edicinin açabilirsiniz **arama özellikleri** toplama ve değişiklik **kimliği** Geliştirici uygulamada kullanılan yeni değerle eşleşecek şekilde özelliği. Test edicinin da değiştirebilir **kolay ad** özellik değerini "Login" için "Gönder" Bu değişikliği yaparak, ilişkili UI eylemi kodlanmış UI Test Düzenleyicisi'nde "Seç 'Gönder' düğmesinden" güncelleştirilir "Seç 'Login' düğmesini."

Değişikliklerinizi tamamladıktan sonra yapılan değişiklikleri kaydetmek *UIMap.Designer* seçerek dosya **Kaydet** Visual Studio araç.

### <a name="tips"></a>İpuçları

- Varsa **özellikleri** penceresi görüntülenmez, basılı **Alt** tuşuna sırada **Enter**, veya basın **F4**.

- Yaptığınız özellik değişiklikleri geri almak için seçin **geri** gelen **Düzenle** tuşuna basın veya menü **Ctrl**+**Z**.

- Kullanabileceğiniz **Bul** açmak için kodlanmış UI Test Düzenleyicisi araç çubuğu düğmesini **Bul ve Değiştir** Visual Studio'da araç. Ardından **bulmak** denetimi UI eylemini kodlanmış UI Test Düzenleyicisi'nde bulun. Örneğin, bulunacak deneyebilirsiniz "tıklayın 'Login' düğmesini." Bu, büyük testlerinde yararlı olabilir. Değiştir işlevselliği kullanamaz **Bul ve Değiştir** içinde kodlanmış UI Test Düzenleyicisi araç. Bul denetiminin daha fazla bilgi için bkz. [metin bulma ve değiştirme](../ide/finding-and-replacing-text.md).

- Bazen görselleştirme denetimleri testten geçirilen uygulamanın kullanıcı Arabiriminde nerede bulunur zor olabilir. Kodlanmış UI Test Düzenleyicisi özelliklerini UI denetim eşleminde listelenen bir denetim seçin ve test edilen uygulamada konumunu görüntülemek biridir. Daha fazla bilgi için [test edilen uygulamada bir UI denetimini Bul](#locate-a-ui-control-in-the-application-under-test) bulunduğu daha aşağıda bu makaledeki.

- Düzenlemek istediğiniz denetimi içeren bir kapsayıcı denetimi genişletmek gerekli olabilir. Daha fazla bilgi için [denetim ve alt öğelerini bulun](#locate-a-control-and-its-descendants) bulunduğu daha aşağıda bu makaledeki.

## <a name="delete-unwanted-ui-actions"></a>İstenmeyen UI eylemlerini silme

Kodlanmış UI testinize istenmeyen UI eylemlerini kolayca kaldırabilirsiniz.

![UI eylemi Sil](../test/media/codeduideleteuiaction.png)

İçinde **UI eylemi** bölmesinde, silmek istediğiniz UI eylemi içeren test yöntemi genişletin. UI eylemi için kısayol menüsünü açın ve seçin **Sil**.

## <a name="split-a-test-method-into-two-separate-methods"></a>İki ayrı yöntemleri bir test metodu bölme

Bir test yöntemine iyileştirmek için veya UI eylemlerini modülarize etmek için bölebilirsiniz. Örneğin, testinizi iki kapsayıcı denetimleri UI eylemleri olan tek test yöntemi olabilir. UI eylemlerini daha iyi bir kapsayıcı karşılık gelen iki yöntem de modularized olabilir.

![Bir test metodu bölme](../test/media/codeduitestsplitmethod1.png)

![İki test yöntemleri](../test/media/codeduitestsplitmethod2.png)

İçinde **UI eylemi** bölmesinde iki ayrı yöntemleri bölme ve başlamak için yeni bir test yöntemi, istediğiniz UI eylemi seçmek için istediğiniz test yöntemini genişletin. Ya da UI eylemi için kısayol menüsünü açın ve ardından **yeni bir yönteme Böl**, ya da seçin **yeni bir yönteme Böl** kodlanmış UI Test Düzenleyicisi araç çubuğu düğmesi. Yeni bir test yöntemi görünür **UI eylemlerini** bölmesi. Bu eylem bölme burada belirttiğiniz Başlangıç UI eylemlerini içerir.

Bitirdikten sonra yapılan değişiklikleri kaydetmek metodu bölme *UIMap.Designer* seçerek dosya **Kaydet** Visual Studio araç çubuğunda.

> [!WARNING]
> Bir metodu bölme, varolan bir yöntem de dahil bu UI eylemlerini hala istiyorsanız oluşturmak üzere olduğunuz yeni yöntem çağırmak için çağıran herhangi bir kodu değiştirmeniz gerekir. Bir metodu bölme, Microsoft Visual Studio iletişim kutusu görüntülenir. Varolan bir yöntem oluşturmak üzere olduğunuz yeni yöntemi de çağrılacak çağıran herhangi bir kodu değiştirmeniz gerekir sizi uyarır. Seçin **Evet**.

### <a name="tips"></a>İpuçları

- Bölme geri seçin **geri** gelen **Düzenle** tuşuna basın veya menü **Ctrl**+**Z**.

- Yeni yöntem yeniden adlandırabilirsiniz. Seçim **UI eylemlerini** bölmesinde seçin **Yeniden Adlandır** kodlanmış UI Test Düzenleyicisi araç çubuğu düğmesi.

   veya

   Yeni test yöntemi ve seçin, kısayol menüsünü açın **Yeniden Adlandır**.

   Microsoft Visual Studio iletişim kutusu görüntülenir. Bu yöntemin başvurduğu herhangi bir kodu değiştirmeniz gerekir sizi uyarır. Seçin **Evet**.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Bir test yöntemi özelleştirmeyi kolaylaştırmak için UIMap dosyaya Taşı

Test yöntemlerinizi birinin karar verirseniz içinde kodlanmış UI test özel kod gerektirir, bu da taşımanız *UIMap.cs* veya *UIMap.vb* dosya. Aksi takdirde, kodlanmış UI testi derlenmiştir her kodunuzu üzerine yazılır. Yöntem taşımayın, özel kodunuz testi derlenmiştir her seferinde üzerine yazılır.

İçinde **UI eylemi** bölmesinde, taşımak istediğiniz test yöntemini seçin *UIMap.cs* veya *UIMap.vb* üzerine olmaz yazılmayacak kod işlevselliğini dosyaya ne zaman test kod derlenir. Ardından, **kodu Taşı** kodlanmış UI Test Düzenleyicisi araç çubuğunda düğme veya test yöntemi için kısayol menüsünü açın ve seçin **kodu Taşı**. Test yöntemi kaldırılır *UIMap.uitest* dosya ve artık görüntülenen **UI eylemlerini** bölmesi. Taşınan test dosyasını düzenlemek için açın *UIMap.cs* veya *UIMap.vb* dosya **Çözüm Gezgini**.

Bitirdikten sonra yapılan değişiklikleri kaydetmek yöntemi taşıma *UIMap.Designer* seçerek dosya **Kaydet** Visual Studio araç çubuğunda.

> [!WARNING]
> Yöntemi taşıdığınızda kodlanmış UI Test Düzenleyicisi'ni kullanarak artık düzenleyebilirsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız. Yöntemi taşıdığınızda, Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntem öğesinden taşınacak sizi uyarır *UIMap.uitest* dosyasını *UIMap.cs* veya *UIMap.vb* dosya ve, bundan böyle yöntemi kullanarak düzenlemeniz mümkün olacağını Kodlanmış UI Test Düzenleyicisi. Seçin **Evet**.

### <a name="tips"></a>İpuçları

Taşıma geri seçin **geri** gelen **Düzenle** tuşuna basın veya menü **Ctrl**+**Z**. Ancak, daha sonra el ile koddan kaldırmalısınız *UIMap.cs* veya *UIMap.vb* dosya.

## <a name="locate-a-ui-control-in-the-application-under-test"></a>Test edilen uygulamada bir UI denetimini Bul

Bazen görselleştirme denetimleri testten geçirilen uygulamanın kullanıcı Arabiriminde nerede bulunur zor olabilir. Kodlanmış UI Test Düzenleyicisi özelliklerini UI denetim eşleminde listelenen bir denetim seçin ve test edilen uygulamada konumunu görüntülemek biridir. Kullanarak **UI denetimini Bul** test edilen uygulamada özelliği de kullanılabilir bir denetime yaptığınız arama özellik değişiklikleri doğrulamak için.

![UI denetimini Bul](../test/media/codeduilocatecontrol.png)

![Test edilen uygulamada bulunan denetim](../test/media/codeduilocatecontrol2.png)

İçinde **UI kontrol haritasını** uygulama içinde bulmak istediğiniz denetimi, test ile ilişkili bölmesinde seçin. Ardından, denetimi için kısayol menüsünü açın ve ardından **UI denetimini Bul**. Test edilen uygulamada denetimi mavi bir kenarlık ile atanmış.

> [!NOTE]
> Bir UI denetimini Bul önce test ile ilişkili uygulamanın çalıştığını doğrulayın.

### <a name="tips"></a>İpuçları

Kullanabileceğiniz **bulun tüm** kapsayıcı altındaki tüm denetimleri bulunduğu doğru olduğunu doğrulamak için seçeneği. Bu seçenek, sonraki bölümde açıklanmıştır.

## <a name="locate-a-control-and-its-descendants"></a>Denetim ve alt öğeleri bulun

Bir kapsayıcı altındaki tüm denetimleri test edilen uygulamanın kullanıcı arabiriminde doğru konumlandırılabilir doğrulayabilirsiniz. Bu, kapsayıcı üzerinde yapılan arama özellik değişiklikleri doğrulamaya yardımcı olabilir. Ayrıca, olduğunda önemli değişiklikler test edilen uygulamanın kullanıcı arabiriminde, var olan denetim arama özellikleri yine de doğru olduğunu doğrulayabilirsiniz.

![Tüm alt denetimler bulun](../test/media/codeduilocateall.png)

![Bulunan tüm denetimleri](../test/media/codeduilocateall2.png)

İçinde **UI kontrol haritasını** bölmesinde bulmak ve görüntülemek için tüm alt öğeleri için istediğiniz kapsayıcı denetimi seçin. Ardından, denetimi için kısayol menüsünü açın ve seçin **bulun tüm**. Kapsayıcı denetimi ve tüm alt denetimlerini kodlanmış UI Test Düzenleyicisi'nde yeşil bir onay işareti ya da 'X' kırmızı ile işaretlenmiştir. Bu işaretler denetimleri test edilen uygulamada başarıyla bulunan, size sağlar.

> [!NOTE]
> UI denetimleri konumlandırma önce test ile ilişkili uygulama çalıştığını doğrulayın.

## <a name="insert-a-delay-before-a-ui-action"></a>Bir UI eyleminden önce gecikme Ekle

Bazı durumlarda, oluşmasına, ilerleme çubuğu kaybolur için görüntülenen bir pencere gibi belirli olaylar için bekleyin ve test yapmak isteyebilirsiniz. Kodlanmış UI Test Düzenleyicisi'ni kullanarak, bunu bir UI eyleminden önce gecikme ekleyerek gerçekleştirebilirsiniz. Gecikme olmasını istediğiniz saniye sayısını belirtebilirsiniz.

![Bir UI eyleminden önce gecikme Ekle](../test/media/codeduidelay.png)

![5 saniye ile eklenen gecikmesi](../test/media/codeduidealy2.png)

İçinde **UI eylemi** bölmesinde bir gecikme eklemek istediğiniz UI eylemi içeren test yöntemi genişletin. UI eylemi seçin. Ardından, UI eylemi için kısayol menüsünü açın ve seçin **önce gecikme Ekle**. Bir gecikme eklenen ve seçili UI eylemi aşağıdaki metinle önünde vurgulanan: **Eylemler arasındaki kullanıcı gecikmesini 1 saniye bekleyin**. İçinde **özellikleri** penceresinde değerini **gecikme** özelliğini istenen milisaniye sayısını.

Bitirdikten sonra yapılan değişiklikleri kaydetme gecikme ekleme *UIMap.Designer* seçerek dosya **Kaydet** Visual Studio araç.

Belirli bir denetime bir UI eyleminden önce kullanılabilir olmasını sağlamak için ihtiyacınız varsa, uygun UITestControl.WaitForControlXXX() yöntemi kullanarak, test yöntemine özel kod ekleme düşünmelisiniz. Daha fazla bilgi için [yapma kodlanmış UI testlerini bekletme belirli olaylar için kayıttan yürütme sırasında](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="see-also"></a>Ayrıca bkz.

- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Verilerle çalışan kodlanmış UI testi oluşturma](../test/creating-a-data-driven-coded-ui-test.md)
- [İzlenecek yol: Oluşturma, düzenleme ve bakımı kodlanmış UI testi](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)