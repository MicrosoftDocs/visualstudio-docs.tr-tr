---
title: Kodlanmış UI testleri, kodlanmış UI Test düzenleyicisini kullanarak düzenleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.assetid: 76435c4b-593e-43a3-a9fe-709a7f9f5e0f
caps.latest.revision: 42
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1bf24c24a60a37fd8fc5859d216c34eaa2e9b4f8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951276"
---
# <a name="editing-coded-ui-tests-using-the-coded-ui-test-editor"></a>Kodlanmış UI Test Düzenleyicisi'ni Kullanarak Kodlanmış UI Testlerini Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI Test Düzenleyicisi'ni kullanarak kodlanmış UI testlerini kolayca değiştirmenize olanak tanır. Kodlanmış UI Test Düzenleyicisi'ni kullanarak bulun, görüntüleyin ve test yöntemlerinizi ve UI eylemlerini özelliklerini düzenleyin. Ayrıca, UI kontrol haritasını görüntülemek ve bunların ilgili denetimleri düzenlemek için kullanabilirsiniz.  
  
 **Gereksinimler**  
  
-   Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>Neden bunu yapmam gerekir?  
 Kodlanmış UI Test Düzenleyicisi'ni kullanarak daha hızlı ve kod düzenleyicisini kullanarak kodlanmış UI test yöntemlerinizde kod düzenleme daha etkilidir. Kodlanmış UI Test Düzenleyicisi ile araç ve kısayol menüleri hızla bulup UI eylemlerini ve denetimleri ile ilgili özellik değerlerini değiştirmek için kullanabilirsiniz. Örneğin, aşağıdakileri gerçekleştirmek için kodlanmış UI Test Düzenleyicisi araç kullanabilirsiniz:  
  
 ![UI Test Düzenleyicisi](../test/media/uitesteditor.png "UITestEditor")  
  
1.  [Bulma](../ide/finding-and-replacing-text.md) UI eylemlerini ve denetimlerini bulmanıza yardımcı olur.  
  
2.  [Silme](#CodedUITestEditor_DeleteUIActions) istenmeyen UI eylemlerini kaldırır.  
  
3.  **Yeniden adlandırma** test yöntemleri ve denetimlerin adlarını değiştirir.  
  
4.  **Özellikleri** seçili öğe için Özellikler penceresi açılır.  
  
5.  [Yeni bir yönteme Böl](#CodedUITestEditor_SplitMethods) UI eylemlerini modülerleştirmek olanak tanır.  
  
6.  [Kodu Taşı](#CodedUITestEditor_MoveMethods) özel kod test yöntemlerinizi ekler.  
  
7.  [Öncesine gecikme Ekle](#CodedUITestEditor_InsertDelay) milisaniye cinsinden belirtilen bir UI eyleminden önce bir duraklama ekler.  
  
8.  [UI denetimini Bul](#CodedUITestEditor_LocateUIControl) testten geçirilen uygulamanın UI denetimi konumunu belirtir.  
  
9. [Tümünü Bul](#CodedUITestEditor_LocateDecendants) doğrulamaya yardımcı olur, özellik ve uygulama denetimleri yapılan önemli değişiklikler denetler.  
  
## <a name="how-do-i-do-this"></a>Bunu nasıl yapmalıyım?  
 İçinde [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], kodlanmış UI testleri, kodlanmış UI test projesi içinde ilişkide UIMap.uitest dosyayı açmayı otomatik olarak görüntüler kodlanmış UI testi kodlanmış UI Test Düzenleyicisi'nde. Aşağıdaki yordamlar nasıl daha sonra bulmak ve test yöntemleri ve özellikleri UI eylemlerini ve düzenleyici araç çubuğu ve kısayol menülerini kullanarak denetimleri için Düzen açıklar.  
  
## <a name="open-a-coded-ui-test"></a>Kodlanmış UI testi Aç  
 Görüntüleme ve düzenleme, Visual C# ve Visual Basic tabanlı kodlanmış UI testi kodlanmış UI Test Düzenleyicisi'ni kullanarak.  
  
 ![Bağlam menüsü düzen ile kodlanmış UI Test Oluşturucusu](../test/media/editcodeduitest.png "EditCodedUITest")  
  
 Çözüm Gezgini içinde kısayol menüsünü açın **UIMap.uitest** ve **açın**. Kodlanmış UI testi kodlanmış UI Test Düzenleyicisi'nde görüntülenir. Şimdi, görüntüleyin ve kayıtlı yöntemleri, Eylemler ve karşılık gelen denetimlerinde kodlanmış UI testi düzenleyin.  
  
> [!TIP]
>  Bir yöntem içinde bulunan bir UI eyleminden seçtiğinizde **UI eylemlerini** karşılık gelen denetimin bölmesinde vurgulanır. UI eylemi veya denetim özelliklerini de değiştirebilirsiniz.  
  
 *Göremiyorum* kodlanmış UI Test Düzenleyicisi.  
 2012'den önceki Visual Studio Enterprise sürümü kullanıyor olabilirsiniz. Kodlanmış UI Test Düzenleyicisi, aynı zamanda bir MSDN aboneliği ile Visual Studio 2010 Özellik Paketi 2'de kullanılabilir. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Microsoft Visual Studio 2010 Özellik Paketi 2](http://go.microsoft.com/fwlink/?LinkID=204119).  
  
##  <a name="CodedUITestEditor_EditActionAndControlProperties"></a> UI eylem özelliklerini ve bunların karşılık gelen denetimin özelliklerini değiştirme  
 Kodlanmış UI Test Düzenleyicisi'ni kullanarak hızla bulun ve tüm UI eylemlerini test yöntemlerinizde görüntüleme. Düzenleyicide UI eylemini seçtiğinizde ilgili denetimin otomatik olarak vurgulanır. Benzer şekilde, bir denetimi seçtiğinizde, ilişkili UI eylemlerini vurgulanır. Bir UI eyleminden ya da bir denetimi seçtiğinizde, sonra kendisiyle karşılık gelen özelliklerini değiştirmek için Özellikler penceresini kullanın çok kolaydır.  
  
 ![UI eylem özelliklerini](../test/media/codeduiedituiaction.png "CodedUIEditUIAction")  
UI eylem özelliklerini düzenleme  
  
 Bir UI eylem özelliklerini değiştirmek için **UI eylemi** bölmesinde UI eylem özelliklerini yı düzenlemek istediğiniz bir UI eyleminden içeren test yöntemi genişletin ve ardından Özellikler penceresini kullanarak özelliklerini değiştirin.  
  
 Örneğin, bir sunucu kullanılamıyor ve Web tarayıcınızı ile ilişkili bir kullanıcı Arabirimi eylemine sahip belirten **Web sayfasına gidin '<http://Contoso1/default.aspx’>**, URL'sine değişebilir `‘http://Contoso2/default.aspx’`.  
  
 ![Denetim Özellikleri](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp")  
Denetim özelliklerini düzenleme  
  
 Bir denetimin özelliklerini değiştirme UI eylemlerini aynı şekilde gerçekleştirilir. İçinde **UI kontrol haritasını** bölmesinde düzenlemek ve Özellikler penceresini kullanarak onun özelliklerini değiştirmek istediğiniz denetimi seçin.  
  
 Örneğin, bir geliştirici değişmiş olabilecek **(ID)** "idSubmit" "idLogin" test edilen uygulamanın kaynak kodunda bir düğme denetimi özelliği İle **(ID)** özellik, uygulama değişti, kodlanmış UI testi düğme denetimini bulmanız mümkün olmayacaktır ve başarısız olur. Bu durumda, test edicinin açabilirsiniz **arama özellikleri** toplama ve değişiklik **kimliği** Geliştirici uygulamada kullanılan yeni değerle eşleşecek şekilde özelliği. Test edicinin da değiştirebilir **kolay ad** özellik değerini "Login" için "Gönder" Bu değişikliği yaparak, ilişkili UI eylemi kodlanmış UI Test Düzenleyicisi'nde "Seç 'Gönder' düğmesinden" güncelleştirilir "Seç 'Login' düğmesini."  
  
 Değişikliklerinizi tamamladıktan sonra UIMap.Designer dosyasındaki değişiklikleri seçerek kaydedin **Kaydet** üzerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] araç çubuğu.  
  
 *Başka neleri bilmeliyim?*  
 **İpuçları**  
  
-   ![İpucu](../test/media/tip.png "İpucu") Özellikler penceresi görüntülenmiyorsa, basılı **Alt** tuşuna sırada **Enter**, veya alternatif olarak basın **F4**.  
  
-   ![İpucu](../test/media/tip.png "İpucu") yaptığınız özellik değişiklikleri geri almak için seçin **geri** gelen **Düzenle** menüsünden veya Ctrl + Z tuşuna basın.  
  
-   ![İpucu](../test/media/tip.png "İpucu") kullanabileceğiniz **Bul** Bul ve Değiştir araç Visual Studio'da açmak için kodlanmış UI Test Düzenleyicisi araç çubuğu düğmesi. Bul denetiminin sonra kodlanmış UI Test Düzenleyicisi'nde bir UI eyleminden bulmak için de kullanabilirsiniz. Örneğin, bulunacak deneyebilirsiniz "tıklayın 'Login' düğmesini." Bu, büyük testlerinde yararlı olabilir. Bul ve Değiştir aracında kodlanmış UI Test Düzenleyicisi'nde değiştir işlevselliği kullanamazsınız unutmayın. Bul denetiminin daha fazla bilgi için bkz. [bulma ve değiştirme metnini](../ide/finding-and-replacing-text.md).  
  
-   ![İpucu](../test/media/tip.png "İpucu") bazen bu görselleştirme denetimleri testten geçirilen uygulamanın kullanıcı Arabiriminde nerede bulunur zor olabilir. Kodlanmış UI Test Düzenleyicisi özelliklerini UI denetim eşleminde listelenen bir denetim seçin ve test edilen uygulamada konumunu görüntülemek biridir. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Test edilen uygulamada bir kullanıcı Arabirimi denetim konumlandırılıyor](#CodedUITestEditor_LocateUIControl) bulunduğu daha aşağıda bu konuda.  
  
-   ![İpucu](../test/media/tip.png "İpucu") düzenlemek istediğiniz denetimi içeren bir kapsayıcı denetimi genişletmek gerekli olabilir. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Denetim ve alt öğelerini konumlandırma](#CodedUITestEditor_LocateDecendants) bulunduğu daha aşağıda bu konuda.  
  
##  <a name="CodedUITestEditor_DeleteUIActions"></a> İstenmeyen UI eylemlerini silme  
 Kodlanmış UI testinize istenmeyen UI eylemlerini kolayca kaldırabilirsiniz.  
  
 ![UI eylemi Sil](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")  
  
 İçinde **UI eylemi** bölmesinde, silmek istediğiniz UI eylemi içeren test yöntemi genişletin. UI eylemi için kısayol menüsünü açın ve seçin **Sil**.  
  
##  <a name="CodedUITestEditor_SplitMethods"></a> İki ayrı yöntemleri bir test metodu bölme  
 Bir test yöntemine iyileştirmek için veya UI eylemlerini modülarize etmek için bölebilirsiniz. Örneğin, testinizi iki kapsayıcı denetimleri UI eylemleri olan tek test yöntemi olabilir. UI eylemlerini daha iyi bir kapsayıcı karşılık gelen iki yöntem de modularized olabilir.  
  
 ![Bir test yöntemi Splt](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")  
  
 ![İki yöntem test](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")  
  
 İçinde **UI eylemi** bölmesinde iki ayrı yöntemleri bölme ve başlamak için yeni bir test yöntemi, istediğiniz UI eylemi seçmek için istediğiniz test yöntemini genişletin. Ya da UI eylemi için kısayol menüsünü açın ve ardından **yeni bir yönteme Böl**, ya da seçin **yeni bir yönteme Böl** kodlanmış UI Test Düzenleyicisi araç çubuğu düğmesi. Yeni bir test yöntemi, UI Eylemler bölmesinde görünür. Bu eylem bölme burada belirttiğiniz Başlangıç UI eylemlerini içerir.  
  
 Bitirdikten sonra bir metodu bölme Kaydet değişiklikleri UIMap.Designer dosyasına seçerek **Kaydet** üzerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] araç çubuğu.  
  
 *Başka neleri bilmeliyim?*  
 **Önemli sorunlar**  
  
- ![Uyarı simgesi](../test/media/caution.gif "uyarı") **uyarısı:** bir metodu bölme, ayrıca bu UI hala istiyorsanız oluşturmak üzere olduğunuz yeni yöntem çağırmak için varolan bir yöntem çağırır herhangi bir kodu değiştirmeniz gerekir Eylemler dahildir. Bir metodu bölme, Microsoft Visual Studio iletişim kutusu görüntülenir. Varolan bir yöntem oluşturmak üzere olduğunuz yeni yöntemi de çağrılacak çağıran herhangi bir kodu değiştirmeniz gerekir sizi uyarır. Seçin **Evet**.  
  
  **İpuçları**  
  
- ![İpucu](../test/media/tip.png "İpucu") bölme geri seçin **geri** gelen **Düzenle** menüsünden veya Ctrl + Z tuşuna basın.  
  
- ![İpucu](../test/media/tip.png "İpucu") yeni yöntem yeniden adlandırabilirsiniz. UI Eylemler bölmesinde seçin ve seçin **Yeniden Adlandır** kodlanmış UI Test Düzenleyicisi araç çubuğu düğmesi.  
  
   veya  
  
   Yeni test yöntemi ve seçin, kısayol menüsünü açın **Yeniden Adlandır**.  
  
   Microsoft Visual Studio iletişim kutusu görüntülenir. Bu yöntemin başvurduğu herhangi bir kodu değiştirmeniz gerekir sizi uyarır. Seçin **Evet**.  
  
##  <a name="CodedUITestEditor_MoveMethods"></a> UIMap dosyaya özelleştirmeyi kolaylaştırmak için bir test yöntemi Taşı  
 Test yöntemleri birinin karar verirseniz kodlanmış UI test özel kod gerektirir, UIMap.cs veya UIMap.vb dosyasına taşımanız gerekir. Aksi takdirde, kodlanmış UI testi derlenmiştir her kodunuzu üzerine yazılır. Yöntem taşımayın, özel kodunuz testi derlenmiştir her seferinde üzerine yazılır.  
  
 İçinde **UI eylemi** bölmesinde, ne zaman üzerine olmayacaktır yazılmayacak kod işlevselliğini UIMap.cs veya UIMap.vb dosyasına test kodu taşımak istediğiniz test yöntemini yeniden seçin. Ardından, **kodu Taşı** kodlanmış UI Test Düzenleyicisi araç çubuğunda düğme veya test yöntemi için kısayol menüsünü açın ve seçin **kodu Taşı**. Test yöntemi UIMap.uitest dosyasından kaldırılır ve artık UI Eylemler bölmesinde görüntülenmez. Taşınan test dosyasını düzenlemek için Çözüm Gezgini'nden UIMap.cs veya UIMap.vb dosyasına'ı açın.  
  
 Bitirdikten sonra yöntemi taşıma Kaydet değişiklikleri UIMap.Designer dosyasına seçerek **Kaydet** üzerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] araç çubuğu.  
  
 *Başka neleri bilmeliyim?*  
 **Önemli sorunlar**  
  
- ![Uyarı simgesi](../test/media/caution.gif "uyarı") **uyarısı:** bir yöntemi taşıdığınızda, artık kodlanmış UI Test düzenleyicisini kullanarak düzenleyebilirsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız. Yöntemi taşıdığınızda, Microsoft Visual Studio iletişim kutusu görüntülenir. Bu, yöntem UIMap.uitest dosyasından UIMap.cs için taşınır veya UIMap.vb dosyasını, kodlanmış UI Test Düzenleyicisi'ni kullanarak yöntemi düzenlemenin mümkün olmayacak sizi uyarır. Seçin **Evet**.  
  
  **İpuçları**  
  
- ![İpucu](../test/media/tip.png "İpucu") taşıma geri seçin **geri** gelen **Düzenle** menüsünden veya Ctrl + Z tuşuna basın. Ancak, daha sonra el ile kod UIMap.cs veya UIMap.vb dosyasından kaldırmanız gerekir.  
  
##  <a name="CodedUITestEditor_LocateUIControl"></a> Test edilen uygulamada bir UI denetimine bulma  
 Bazen görselleştirme denetimleri testten geçirilen uygulamanın kullanıcı Arabiriminde nerede bulunur zor olabilir. Kodlanmış UI Test Düzenleyicisi özelliklerini UI denetim eşleminde listelenen bir denetim seçin ve test edilen uygulamada konumunu görüntülemek biridir. Kullanarak **UI denetimini Bul** test edilen uygulamada özelliği de kullanılabilir bir denetime yaptığınız arama özellik değişiklikleri doğrulamak için.  
  
 ![UI denetimini Bul](../test/media/codeduilocatecontrol.png "CodedUILocateControl")  
  
 ![Testten geçirilen uygulamanın bulunan denetim](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")  
  
 İçinde **UI kontrol haritasını** uygulama içinde bulmak istediğiniz denetimi, test ile ilişkili bölmesinde seçin. Ardından, denetimi için kısayol menüsünü açın ve ardından **UI denetimini Bul**. Test edilen uygulamada denetimi mavi bir kenarlık ile atanmış.  
  
 *Başka neleri bilmeliyim?*  
 **Önemli sorunlar**  
  
- ![Uyarı simgesi](../test/media/caution.gif "uyarı") **uyarısı:** bir UI denetimini Bul önce test ile ilişkili uygulamanın çalıştığını doğrulayın.  
  
  **İpuçları**  
  
- ![İpucu](../test/media/tip.png "İpucu") alternatif olarak, **bulun tüm** kapsayıcı altındaki tüm denetimleri bulunduğu doğru olduğunu doğrulamak için seçeneği. Bu seçenek, sonraki bölümde açıklanmıştır.  
  
##  <a name="CodedUITestEditor_LocateDecendants"></a> Denetim ve alt öğelerini konumlandırma  
 Bir kapsayıcı altındaki tüm denetimleri test edilen uygulamanın kullanıcı arabiriminde doğru konumlandırılabilir doğrulayabilirsiniz. Bu, kapsayıcı üzerinde yapılan arama özellik değişiklikleri doğrulamaya yardımcı olabilir. Ayrıca, olduğunda önemli değişiklikler test edilen uygulamanın kullanıcı arabiriminde, var olan denetim arama özellikleri yine de doğru olduğunu doğrulayabilirsiniz.  
  
 ![Tüm alt denetimler bulun](../test/media/codeduilocateall.png "CodedUILocateAll")  
  
 ![Bulunan tüm denetimleri](../test/media/codeduilocateall2.png "CodedUILocateAll2")  
  
 İçinde **UI kontrol haritasını** bölmesinde bulmak ve görüntülemek için tüm alt öğeleri için istediğiniz kapsayıcı denetimi seçin. Ardından, denetimi için kısayol menüsünü açın ve seçin **bulun tüm**. Kapsayıcı denetimi ve tüm alt denetimlerini kodlanmış UI Test Düzenleyicisi'nde yeşil bir onay işareti ya da 'X' kırmızı ile işaretlenmiştir. Bu işaretler denetimleri test edilen uygulamada başarıyla bulunan, size sağlar.  
  
 *Başka neleri bilmeliyim?*  
 **Önemli sorunlar**  
  
-   ![Uyarı simgesi](../test/media/caution.gif "uyarı") **uyarısı:** UI denetimleri konumlandırma önce test ile ilişkili uygulama çalıştığını doğrulayın.  
  
##  <a name="CodedUITestEditor_InsertDelay"></a> Bir UI eyleminden önce gecikme ekleme  
 Bazı durumlarda, oluşmasına, ilerleme çubuğu kaybolur için görüntülenen bir pencere gibi belirli olaylar için bekleyin ve test yapmak isteyebilirsiniz. Kodlanmış UI Test Düzenleyicisi'ni kullanarak, bunu bir UI eyleminden önce gecikme ekleyerek gerçekleştirebilirsiniz. Gecikme olmasını istediğiniz saniye sayısını belirtebilirsiniz.  
  
 ![Bir UI eyleminden önce gecikme Ekle](../test/media/codeduidelay.png "CodedUIDelay")  
  
 ![5 saniye ile eklenen gecikme](../test/media/codeduidealy2.png "CodedUIDealy2")  
  
 İçinde **UI eylemi** bölmesinde bir gecikme eklemek istediğiniz UI eylemi içeren test yöntemi genişletin. UI eylemi seçin. Ardından, UI eylemi için kısayol menüsünü açın ve seçin **önce gecikme Ekle**. Bir gecikme eklenen ve seçili UI eylemi aşağıdaki metinle önünde vurgulanan: **Eylemler arasındaki kullanıcı gecikmesini 1 saniye bekleyin**. Özellikler penceresinde değerini değiştirin **gecikme** özelliğini istenen milisaniye sayısı.  
  
 Bitirdikten sonra gecikme ekleme Kaydet değişiklikleri UIMap.Designer dosyasına seçerek **Kaydet** üzerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] araç çubuğu.  
  
 *Başka neleri bilmeliyim?*  
 **Notlar**  
  
- ![Prerequsite](../test/media/prereq.png "önkoşul uyarılarını gözardı et") belirli bir denetime bir UI eyleminden önce kullanılabilir olmasını sağlamak ihtiyacınız varsa, test yönteminizde uygun UITestControl.WaitForControlXXX() kullanarak özel kod eklemeyi düşünmelidir yöntem. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Kodlanmış UI yapma, kayıttan yürütme sırasında belirli olaylar için bekleme testleri](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).  
  
  **İpuçları**  
  
- ![İpucu](../test/media/tip.png "İpucu") Özellikler penceresi görüntülenmiyorsa, tuşunu Enter tuşuna basın veya alternatif olarak, F4 tuşuna basılı tutarak Alt.  
  
## <a name="external-resources"></a>Dış kaynaklar  
  
### <a name="guidance"></a>Kılavuz  
 [Visual Studio 2012 – bölüm 2 ile sürekli teslimat testi: birim testi: iç testler](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="faq"></a>SSS  
 [Kodlanmış UI testleri SSS - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Kodlanmış UI testleri SSS -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [(Visual Studio UI Otomasyon Codeduı dahil) test etme](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Kodlanmış UI testi verilerle oluşturma](../test/creating-a-data-driven-coded-ui-test.md)   
 [Mevcut eylem kaydından bir kodlanmış UI testi oluşturma](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)   
 [İzlenecek yol: Kodlanmış Bir UI Testi Oluşturmak Düzenlemek ve Sürdürmek](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)



