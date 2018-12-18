---
title: Kodunuzu test etmek için UI otomasyonunu kullanma | Microsoft Docs
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
- vs.codedUITest
- vs.codedUITest.recorder
- vs.codedUITest.testbuilder
- vs.codedUITest.addAssertions
- vs.codedUITest.createdialog
helpviewer_keywords:
- automated tests, testing UI interface
- coded UI test
ms.assetid: ad9e3eaa-ab86-436e-95b8-dc20eb1f8b2a
caps.latest.revision: 87
ms.author: gewarren
manager: douge
ms.openlocfilehash: 251f6a99f64a191f1a5d957157c06c7e89147217
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812679"
---
# <a name="use-ui-automation-to-test-your-code"></a>Kodunuzu Test Etmek için UI Otomasyonunu Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızın kullanıcı arabirimi (UI) sürücü otomatik testler olarak bilinir *kodlanmış UI testleri* (CUITs). Bu testler, işlevsel test kullanıcı Arabirimi denetimleri içerir. Bunlar, kullanıcı arabirimi de dahil olmak üzere tüm uygulamanın düzgün çalıştığını doğrulamak olanak tanır. Kodlanmış UI testleri doğrulama veya başka bir mantık kullanıcı arabiriminde, örneğin, bir web sayfasındaki olduğunda özellikle yararlıdır. Mevcut bir el ile testi otomatik hale getirmek için de sık kullanılır.  
  
 Aşağıdaki çizimde gösterildiği gibi tipik geliştirme deneyimi biri, başlangıçta yalnızca uygulamanızı (F5) ve burada şeyler düzgün çalıştığını doğrulamak için kullanıcı Arabirimi denetimleri tıklatın olabilir. Uygulamayı el ile test etmek devam gerekmez Kodlanmış testi oluşturmaya karar verebilirsiniz. Uygulamanızda sınanan belirli işlevi bağlı olarak kullanıcı Arabirimi düzeyinde test içermeyebilir veya bir tümleştirme testini veya bir işlevsel test için kod yazabilirsiniz. Bazı iş mantığı doğrudan erişmek istiyorsanız, bir birim testi kodu. Ancak, belirli koşullar altında çeşitli kullanıcı Arabirimi denetimleri, uygulamanızda test dahil etmek yararlı olabilir. Kodlanmış UI testi ilk (F5), kod karmaşası uygulamanızın işlevselliğini etkilemez doğrulama senaryosu, otomatik hale getirebilirsiniz.  
  
 ![Uygulama geliştirme sırasında test](../test/media/cuit-overview.png "CUIT_Overview")  
  
 Kodlanmış UI testi oluşturmak kolaydır. CUIT Test Oluşturucusu'nu arka planda çalışırken, yalnızca testin el ile gerçekleştirin. Ayrıca, hangi belirli alanlarla değerleri görünmelidir belirtebilirsiniz. CUIT Test Oluşturucusu'nu eylemlerinizi kaydeder ve bunları kod oluşturur. Test oluşturulduktan sonra bir dizi eylem değiştirmenize olanak tanıyan özelleştirilmiş bir düzenleyici düzenleyebilirsiniz.  
  
 Alternatif olarak, Microsoft Test Yöneticisi'nde kaydedildiği bir test çalışması'iniz varsa, kod üretebilirsiniz ekleyebilirsiniz. Daha fazla bilgi için [kayıt ve yürütme geri el ile testleri](http://msdn.microsoft.com/library/9792e72f-600e-441f-9d4e-6510e5965665).  
  
 Özelleştirilmiş CUIT Test Oluşturucusu'nu ve düzenleyici, oluşturmak ve test yerine kodlama becerilerinizi ana yoğunlaşmıştır olsa bile, kodlanmış UI testleri düzenlemek kolaylaştırır. Ancak, böylece kopyalayıp uyarlamak basit bir geliştirici ve test daha gelişmiş bir biçimde genişletmek istediğiniz kodu yapılandırılmıştır. Örneğin, bir Web sitesinden bir şey satın almak için bir testi kaydedin ve ardından öğe sayısını satın bir döngü eklemek için oluşturulan kodu düzenleyin.  
  
 **Gereksinimler**  
  
- Visual Studio Enterprise  
  
  İlgili Platform ve yapılandırmaları desteklenir kodlanmış UI testleri tarafından daha fazla bilgi için bkz. [kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).  
  
  **Bu konudaki**  
  
- [Kodlanmış UI testleri oluşturma](#VerifyingCodeUsingCUITCreate)  
  
  -   [Main yordamı](#VerifyingCodeUsingCUITCreate)  
  
  -   [Başlatma ve durdurma uygulama](#starting)  
  
  -   [UI denetimlerinin özelliklerini doğrulama](#VerifyingCodeUsingCUITGenerateAssertions)  
  
- [Kodlanmış UI testleri özelleştirme](#VerifyingCodeCUITModify)  
  
  -   [Oluşturulan kod](#generatedCode)  
  
  -   [UI denetim eylemlerini ve özelliklerini kodlama](#actions)  
  
  -   [Hata Ayıklama](#debugging)  
  
- [Yenilikler](#VerifyCodeUsingCUITWhatsNext)  
  
##  <a name="VerifyingCodeUsingCUITCreate"></a> Kodlanmış UI testleri oluşturma  
  
1. **Kodlanmış UI testi projesi oluşturun.**  
  
    Kodlanmış UI testleri, kodlanmış UI test projesi içinde yer almalıdır. Kodlanmış UI test projesi yoksa bir tane oluşturun. İçinde **Çözüm Gezgini**, çözümün kısayol menüsünde **Ekle**, **yeni proje** seçip ya da **Visual Basic** veya **Visual C#**. Ardından, **Test**, **kodlanmış UI testi**.  
  
   - <em>Göremiyorum **kodlanmış UI testi</em>* proje şablonları.*  
  
      Visual Studio'nun kodlanmış UI testlerini desteklemeyen bir sürümünü kullanıyor olabilirsiniz. Kodlanmış UI testleri oluşturmak için Visual Studio Enterprise'ı kullanmanız gerekir.  
  
2. **Kodlanmış UI test dosyası ekleyin.**  
  
    Kodlanmış UI projesi oluşturduysanız, ilk CUIT dosyasını otomatik olarak eklenir. Başka bir test dosyası eklemek için kodlanmış UI test projesi kısayol menüsünü açın, işaret **Ekle**ve ardından **kodlanmış UI testi**.  
  
    ![Kodlanmış UI testi oluşturma](../test/media/codedui-create.png "CodedUI_Create")  
  
    İçinde **kodlanmış UI testi için kod üret** iletişim kutusunda **eylemleri Kaydet, UI haritasını Düzenle veya onaylama işlemleri Ekle**.  
  
    ![Kayıt eylemleri seçin](../test/media/codedui-codegendialogb.png "CodedUI_CodeGenDialogB")  
  
    Kodlanmış UI Test Oluşturucusu görünür ve Visual Studio en aza indirilir.  
  
    ![Kodlanmış UI Testi Oluşturucusu](../test/media/codedui-testbuilder.png "CodedUI_TestBuilder")  
  
3. **Bir dizi eylem kaydı**.  
  
    **Kaydı başlatmak için**, seçin **kayıt** simgesi. Gerekirse, uygulama başlatma da dahil olmak üzere, uygulamanızda test etmek istediğiniz eylemleri gerçekleştirin.  
  
    Örneğin, bir web uygulaması sınıyorsanız, bir tarayıcıyı başlatın, web sitesine gidin ve uygulamada oturum açın.  
  
    **Kaydı Duraklat için**, gelen e-posta ile uğraşmak zorunda kalırsanız örnek seçin için **duraklatmak**.  
  
   > [!WARNING]
   >  Masaüstü üzerinde gerçekleştirilen tüm eylemler kaydedilir. Hassas veriler kayda eklenmesini açabilir eylemleri gerçekleştiriyorsanız kaydı duraklatın.  
  
    **Eylemleri silmek** yanlışlıkla kaydettiğiniz öğesini **düzenleme eylemleri**.  
  
    **Kod üretmek için** , eylemlerinizi çoğaltmak, seçin **kod oluştur** simgesi ve türü bir ad ve açıklama için kodlanmış UI test metodu.  
  
4. **Metin kutuları gibi kullanıcı Arabirimi alanlarındaki değerleri doğrulayın**.  
  
    Seçin **onaylama Ekle** kodlanmış UI Test Oluşturucusu'nda çalışan uygulamanızda bir UI denetimini seçin. Görüntülenen özellikler listesinde, örneğin, bir özellik seçin **metin** metin kutusunda. Kısayol menüsünde **onaylama Ekle**. Karşılaştırma işleci, karşılaştırma değeri ve hata iletisi iletişim kutusunda seçin.  
  
    Onaylama işlemi pencereyi kapatın ve seçin **kod üret**.  
  
    ![Öğesini hedefleyen kodlanmış UI testi](../test/media/codedui-1.png "CodedUI_1")  
  
   > [!TIP]
   >  Eylemlerini kaydederek ve değerlerini doğrulama arasında geçiş yapar. Her bir dizi eylem veya doğrulamaları sonunda kod oluşturur. İsterseniz, daha sonra yeni eylemler ve Doğrulamalar eklemeniz mümkün olacaktır.  
  
    Daha fazla ayrıntı için [denetimleri, doğrulama özellikleri](#VerifyingCodeUsingCUITGenerateAssertions).  
  
5. **Oluşturulan test kodunu görüntüleme**.  
  
    Oluşturulan kodun görüntülemek için kullanıcı Arabirimi Test Oluşturucusu'nu penceresini kapatın. Kodda, her adımın verdiğiniz adları görebilirsiniz. Kod, oluşturduğunuz CUIT dosyasıdır:  
  
   ```csharp  
   [CodedUITest]  
   public class CodedUITest1  
   { ...  
     [TestMethod]  
     public void CodedUITestMethod1()  
     {  
         this.UIMap.AddTwoNumbers();  
         this.UIMap.VerifyResultValue();  
         // To generate more code for this test, select   
         // "Generate Code" from the shortcut menu.  
     }  
   }  
   ```  
  
6. **Daha fazla eylem ve Onaylamalar ekleme**.  
  
    Test yöntemi, uygun noktada imleci yerleştirin ve ardından kısayol menüsünden seçin **kodlanmış UI testi için kod üret**. Yeni kod bu noktada eklenir.  
  
7. **Test eylemlerini ve Onaylamalar ayrıntılarını Düzenle**.  
  
    UIMap.uitest açın. Bu dosya kodlanmış UI testi Burada, herhangi bir dizi kaydettiğiniz eylem düzenleme yapabilir onayları Düzenle Düzenleyicisi'nde açılır.  
  
    ![Kodlanmış UI Test Düzenleyicisi](../test/media/cuit-editor-edit.png "CUIT_Editor_edit")  
  
    Daha fazla bilgi için [düzenleme kodlanmış UI Test düzenleyicisini kullanarak kodlanmış UI testleri](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
8. **Test çalıştırması**.  
  
    Test Gezgini'ni kullanın veya test yönteminde kısayol menüsünü açın ve ardından **çalıştırmak testlerini**. Testlerin nasıl çalıştırılacağı hakkında daha fazla bilgi için bkz. [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md) ve *kodlanmış UI testleri çalıştırmak için ek seçenekler* içinde [sıradakiler?](#VerifyCodeUsingCUITWhatsNext) adresindeki bölüm Bu konunun sonuna.  
  
   Bu konuda geriye kalan bölümlerinde, bu yordamdaki adımları hakkında daha fazla ayrıntı sağlar.  
  
   Daha ayrıntılı bir örnek için bkz. [izlenecek yol: oluşturma, düzenleme ve bir kodlanmış UI testi koruma](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). İzlenecek yolda, oluşturmak, düzenlemek ve bir kodlanmış UI testinin nasıl yükleneceğini göstermek için basit bir Windows Presentation Foundation (WPF) uygulaması oluşturacaksınız. İzlenecek yol çeşitli zamanlama sorunları ve yeniden düzenlemeyi denetleme tarafından kırılan testleri düzeltmeye ilişkin çözümler sağlar.  
  
###  <a name="starting"></a> Başlatma ve durdurma test altındaki uygulama  
 *My application, tarayıcı veya veritabanı her test için ayrı ayrı durdurmak ve başlatmak istemiyorum. Bu nasıl kaçınabilirim?*  
  
-   ![Prerequsite](../test/media/prereq.png "önkoşul uyarılarını gözardı et") test altındaki uygulamanızı başlatmak için eylemleri kaydetmek istemiyorsanız, seçmeden önce uygulamanızı başlamalıdır **kayıt** simgesi.  
  
-   ![Prerequsite](../test/media/prereq.png "önkoşul uyarılarını gözardı et")test sonunda, testin çalıştığı işlem sonlandırıldı. Uygulamanızı test başlattıysanız, uygulama genellikle kapatır.  Çıktığında uygulamanız kapatmak için test istemiyorsanız kullanın ve çözüm bir .runsettings dosyası eklemelisiniz `KeepExecutorAliveAfterLegacyRun` seçeneği. Daha fazla bilgi için [bir .runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
-   ![Prerequsite](../test/media/prereq.png "önkoşul uyarılarını gözardı et") her test yönteminin başlangıcında kod çalıştıran bir [TestInitialize] özniteliği tarafından tanımlanan bir test başlatma yöntemi ekleyebilirsiniz. Örneğin, uygulama TestInitialize yöntemden başlatabilir.  
  
-   ![Prerequsite](../test/media/prereq.png "önkoşul uyarılarını gözardı et") kod her test yönteminin sonunda çalıştırılan bir [TestCleanup] özniteliği tarafından tanımlanan bir test temizleme yöntemi ekleyebilirsiniz. Örneğin, uygulamayı kapatmak için bu yöntem, TestCleanup yöntemi çağrılabilir.  
  
###  <a name="VerifyingCodeUsingCUITGenerateAssertions"></a> UI denetimlerinin özelliklerini doğrulama  
 Kullanabileceğiniz **kodlanmış UI Test Oluşturucusu** bir kullanıcı arabirimi (UI) denetimine eklemek için <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> test veya onaylama UI denetimini kullanan bir doğrulama yöntemi için kod oluşturmak için.  
  
 Onaylar için kullanıcı Arabirimi denetimleri oluşturmak için Seç **onaylama Ekle** doğrulamak istediğiniz test edilen uygulamada denetime doğru sürükleyin ve kodlanmış UI Test Oluşturucusu araç. Denetim kutusu özetlenmektedir, fare düğmesini bırakın. Denetimi sınıf kodunun hemen oluşturulur `UIMap.Designer.cs` dosya.  
  
 ![Öğesini hedefleyen kodlanmış UI testi](../test/media/codedui-1.png "CodedUI_1")  
  
 Bu denetimin özelliklerini artık listelenen **onaylama Ekle** iletişim kutusu.  
  
 Özel bir denetime gezinme bir başka yolu oku seçmektir **(<<)** görünümü için genişletmek için **UI kontrol haritasını**. Üst, eşdüzey veya alt denetim bulmak için haritada herhangi bir yere tıklayın ve ağaç taşımak için ok tuşlarını kullanın.  
  
 ![Kodlanmış UI test özelliklerini](../test/media/codedui-2.png "CodedUI_2")  
  
- *Uygulamamda bir denetimi seçeneğini veya UI kontrol haritasında denetiminde göremiyorum özeliklerini göremiyorum.*  
  
   Uygulama kodunda doğrulamak istediğiniz denetimin HTML kimliği öznitelik ya da WPF kullanıcı kimliği gibi benzersiz bir kimliği olması gerekir. Bu kimliği eklemek için uygulama kodu güncelleştirmeniz gerekebilir.  
  
  Ardından, özellikte doğrulayın ve sonra istediğiniz UI denetimi için kısayol menüsünü açın **onaylama Ekle**. İçinde **onaylama Ekle** iletişim kutusunda **karşılaştırıcı** örneğin değerinizi <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>, değerinizi içinde değeri yazın **karşılaştırma değeri**.  
  
  ![Kodlanmış UI testi onaylar](../test/media/codedui-3.png "CodedUI_3")  
  
  Testiniz için tüm onayları eklendiğinde seçin **Tamam**.  
  
  Onayları kodunu oluşturmak ve UI haritasına denetim eklemek için seçin **kod üret** simgesi. Kodlanmış UI test yönteminizde için bir ad ve yöntem için herhangi bir yorum olarak eklenir yöntemi için bir açıklama yazın. Seçin **Ekle ve Oluştur**. Ardından, **kapatmak** kapatmak için simge **kodlanmış UI Test Oluşturucusu**. Bu, aşağıdaki koda benzer bir kod oluşturur. Örneğin, girdiğiniz adı ise `AssertForAddTwoNumbers`, kodu şu örnekteki gibi görünecektir:  
  
- Test yöntemi, kodlanmış UI test dosyanızdaki AssertForAddTwoNumbers onay yöntemi çağrısı ekler:  
  
  ```  
  [TestMethod]  
  public void CodedUITestMethod1()  
  {  
      this.UIMap.AddTwoNumbers();  
      this.UIMap.AssertForAddTwoNumbers();  
  }  
  ```  
  
   Onaylar ve adımları sırasını değiştirmek için ya da yeni test metotları oluşturmak için bu dosyayı düzenleyebilirsiniz. Daha fazla kod eklemek için imleci test yönteminin ve kısayol menüsünde yer seçin **kodlanmış UI testi için kod üret**.  
  
- Adlı bir yöntem ekler `AssertForAddTwoNumbers` UI haritasına (UIMap.uitest). Bu dosya kodlanmış UI testi, onaylamalar düzenleyebileceğiniz Düzenleyicisi'nde açılır.  
  
   ![Düzenleme assert kodlanmış UI Test düzenleyicisini kullanarak](../test/media/cuit-editor-assert.png "CUIT_Editor_assert")  
  
   Daha fazla bilgi için [düzenleme kodlanmış UI Test düzenleyicisini kullanarak kodlanmış UI testleri](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
   UIMap.Designer.cs içinde onay yöntemi, oluşturulan kod da görüntüleyebilirsiniz. Ancak, bu dosyayı düzenlemeniz değil. Uyarlanmış bir kod sürümünü hale getirmek isterseniz, yöntemi UIMap.cs gibi başka bir dosyaya kopyalayın, yöntemleri yeniden adlandırın ve bunları düzenleyebilirsiniz.  
  
  ```  
  public void AssertForAddTwoNumbers()  
  {  
      ...  
  }  
  ```  
  
  *Seçmek istediğiniz denetim odağı kaybettiğinde ve kodlanmış UI Test Oluşturucusu ' onaylama Ekle aracı seçmek çalıştığınızda kaybolur. Denetimin nasıl seçilsin mi?*  
  **Klavyeyi kullanarak gizli bir denetimi seçme**  
  
  Bazen, [denetimleri ekleme ve bunların özelliklerini doğrulama](#VerifyingCodeUsingCUITGenerateAssertions), klavye kullanmanız gerekebilir. Örneğin, bir bağlam menü denetimini kullanan kodlanmış UI testi kaydetmeyi denediğinizde denetiminde menü öğelerini listesini odağı kaybeder ve kodlanmış UI Test Oluşturucusu onaylama Ekle aracı seçmek çalıştığınızda kaybolur. Bu, Internet Explorer'da bağlam menüsü burada ve odağı kaybeder onaylama Ekle aracıyla seçmek deneyin kaybolmasına aşağıdaki çizimde gösterilmiştir.  
  
  ![Sı Codeduıtest&#95;SelectControlKeyboard](../test/media/codeduitest-selectcontrolkeyboard.png "CodedUITest_SelectControlKeyboard")  
  
  UI denetimini seçmek için klavyeyi kullanmak için fareyi denetimin üzerine gelin. Ardından basılı **Ctrl** anahtarı ve **miyim** aynı zamanda anahtar. Anahtarları bırakın. Denetim kodlanmış UT Test Oluşturucusu tarafından kaydedilir.  
  
> [!WARNING]
>  Microsoft Lync kullanırsanız, kodlanmış UI Test Oluşturucusu başlamadan önce Lync kapatmanız gerekir. Microsoft Lync Engellemesi ile **Ctrl + ı** klavye kısayol.  
  
 *Bir bir denetimi fareyle üzerine gelindiğinde kaydedemiyorum. Bu geçici bir yolu var mı?*  
 **El ile kayıt fare geldiğinde**  
  
 Bazı durumlarda, kullanılan belirli bir denetim bir kodlanmış UI testi el ile kayıt fare vurgulu olayları için klavyeyi kullanma gerektirebilir. Örneğin, bir Windows Form veya bir Windows Presentation Foundation (WPF) uygulaması test ettiğinizde, olabilir özel kod. Veya, bir kullanıcı üzerine geldiğinde genişleterek bir ağaç düğümü gibi bir denetimin üzerine geldiği için tanımlanan özel davranış olabilir. Bu gibi durumlarda test etmek için el ile kodlanmış UI Test tuşlarına basarak denetimin üzerine geldiğinizde Oluşturucu klavye tuşlarını önceden tanımlanmış bildirim gerekir.  
  
 Kodlanmış UI testleri gerçekleştirdiğinizde, denetimin üzerine gelin. Tuşuna basın ve basılı Ctrl klavyenizde Shift ve R tuşlarını basılı tutarak. Anahtarları bırakın. Fareyi üzerine gelindiğinde kullanılacak olay kodlanmış UT Test Oluşturucusu tarafından kaydedilir.  
  
 ![Codeduı&#95;gelin](../test/media/codedui-hover.png "CodedUI_Hover")  
  
 Test yöntemi oluşturduktan sonra aşağıdaki örneğe benzer bir kod UIMap.Desinger.cs dosyasına eklenecek:  
  
```csharp  
// Mouse hover '1' label at (87, 9)  
Mouse.Hover(uIItem1Text, new Point(87, 9));  
  
```  
  
 *Fare vurgulu olaylarını yakalamak için anahtar atama başka bir yerde ortamım kullanılıyor. Varsayılan anahtar atama değiştirebilirim?*  
 **Fareyi üzerine gelindiğinde kullanılacak klavye atamalarını yapılandırma**  
  
 Gerekirse, Ctrl + Shift + fare vurgulama olayları kodlanmış UI testleri uygulamak için kullanılan R varsayılan klavye atamasını farklı anahtarları kullanacak şekilde yapılandırılabilir.  
  
> [!WARNING]
>  Normal koşullar altında fare vurgulu olayları için klavye atamaları değiştirmek sahip olmamalıdır. Klavye atama elemanına dikkatli olun. Seçtiğiniz zaten Visual Studio veya test edilen uygulamanın başka bir yere kapsamında kullanımda olabilir.  
  
 Klavye atamaları değiştirmek için aşağıdaki yapılandırma dosyasını değiştirmeniz gerekir:  
  
 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`  
  
 Yapılandırma dosyasında değerlerini değiştirmek `HoverKeyModifier` ve `HoverKey` anahtarları klavye atamaları değiştirmek için:  
  
```  
<!-- Begin : Background Recorder Settings -->  
<!-- HoverKey to use. -->  
<add key="HoverKeyModifier" value="Control, Shift"/>  
<add key="HoverKey" value="R"/>  
  
```  
  
 *Bir Web sitesinde fare eklenmemesi kaydetme konusunda sorun yaşıyorum. Bir düzeltme bunun için çok var mı?*  
 **Web tarayıcısı ayarını örtük fare geldiğinde**  
  
 Belirli bir denetimin üzerine geldiğinizde birçok Web sitesi, bu ek ayrıntıları göster genişletir. Genellikle, bu gibi Masaüstü uygulamaları menülerde arayın. Bu yaygın bir düzen olduğundan, Web'e göz atmak için örtük eklenmemesi kodlanmış UI testleri etkinleştirin. Örneğin, kayıt Internet Explorer'da getirirse, bir olay harekete geçirilir. Bu olaylar kaydediliyor yedekli eklenmemesi için yol açabilir. Bu nedenle, örtük eklenmemesi ile kaydedilen `ContinueOnError` kümesine `true` kullanıcı Arabirimi test yapılandırma dosyası. Bu, kayıttan yürütmenin vurgulu event başarısız olursa devam etmesini sağlar.  
  
 Bir Web tarayıcısında örtük eklenmemesi kaydını etkinleştirmek için yapılandırma dosyasını açın:  
  
 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`  
  
 Yapılandırma dosyası anahtar olduğunu doğrulayın `RecordImplicitiHovers` ayarlamak bir değerini `true` aşağıdaki örnekte gösterildiği gibi:  
  
```  
<!--Use this to enable/disable recording of implicit hovers.-->  
<add key="RecordImplicitHover" value="true"/>  
  
```  
  
##  <a name="VerifyingCodeCUITModify"></a> Kodlanmış UI testleri özelleştirme  
 Kodlanmış UI testi oluşturduktan sonra Visual Studio'da aşağıdaki araçlardan herhangi birini kullanarak düzenleyebilirsiniz:  
  
-   **Kodlanmış UI Test Oluşturucusu:** testlerinize ek denetimleri ve doğrulama eklemek için kodlanmış UI Test Oluşturucusu'nu kullanın. Bölümüne bakın [denetimleri ekleme ve bunların özelliklerini doğrulama](#VerifyingCodeUsingCUITGenerateAssertions) bu konuda.  
  
-   **Kodlanmış UI Test Düzenleyicisi:** kodlanmış UI Test Düzenleyicisi'ni kullanarak kodlanmış UI testlerini kolayca değiştirmenize olanak tanır. Kodlanmış UI Test Düzenleyicisi'ni kullanarak bulun, görüntüleyin ve test yöntemlerinizi düzenleyin. UI eylemlerini ve bunların ilişkili denetimleri UI kontrol haritasında de düzenleyebilirsiniz. Daha fazla bilgi için [düzenleme kodlanmış UI Test düzenleyicisini kullanarak kodlanmış UI testleri](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
-   **Kod Düzenleyicisi:**  
  
    -   Bölümünde anlatıldığı gibi denetimler için kodu testinizde el ile ekleyin [kodlama UI denetim eylemlerini ve özelliklerini](#VerifyingCodeCUITActionsandProperties) bölümüne bakın.  
  
    -   Kodlanmış UI testi oluşturduktan sonra veri odaklı olarak değiştirebilirsiniz. Daha fazla bilgi için [veri tabanlı kodlanmış bir UI testi oluşturma](../test/creating-a-data-driven-coded-ui-test.md).  
  
    -   Bir kodlanmış UI Testi kayıttan yürütmesinde kaybolur ve benzeri için ilerleme çubuğunu oluşmasına görünmesi için bir pencere gibi belirli olaylar için beklenecek test bildirebilirsiniz. Bunu yapmak için uygun UITestControl.WaitForControlXXX() yöntemini ekleyin. Kullanılabilir yöntemleri tam bir listesi için bkz. [yapmadan kodlanmış UI testleri beklemek için belirli olayları sırasında kayıttan yürütme](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Bir denetim WaitForControlEnabled yöntemi kullanarak etkin olmasını bekler, kodlanmış UI testi örneği için bkz [izlenecek yol: oluşturma, düzenleme ve bir kodlanmış UI testi koruma](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
    -   Kodlanmış UI testleri, Internet Explorer 9 ve Internet Explorer 10 HTML5 denetimleri bazıları için destek içerir. Daha fazla bilgi için [kodlanmış UI testlerinde HTML5 denetimleri kullanma](../test/using-html5-controls-in-coded-ui-tests.md).  
  
    -   **Kodlanmış UI testi kodlama Kılavuzu:**  
  
        -   [Kodlanmış UI Testinin Anatomisi](../test/anatomy-of-a-coded-ui-test.md)  
  
        -   [Kodlanmış UI Testleri için En İyi Yöntemler](../test/best-practices-for-coded-ui-tests.md)  
  
        -   [Birden Çok UI Eşlemesi Bulunan Büyük Uygulamaları Sınama](../test/testing-a-large-application-with-multiple-ui-maps.md)  
  
        -   [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)  
  
###  <a name="generatedCode"></a> Oluşturulan kod  
 Seçeneğini belirlediğinizde **kod üret**, bazı kod parçalarını oluşturulur:  
  
- **Bir test yönteminin satır.**  
  
  ```csharp  
  [CodedUITest]  
  public class CodedUITest1  
  { ...  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        this.UIMap.AddTwoNumbers();  
        // To generate more code for this test, select   
        // "Generate Code" from the shortcut menu.      }  
  }  
  ```  
  
   Daha fazla kayıtlı eylemleri ve Doğrulamalar eklemek için bu yöntemi, sağ tıklayabilirsiniz. Ayrıca, el ile genişletin veya kodu değiştirmek için de düzenleyebilirsiniz. Örneğin, bazı kodları bir döngüde içine.  
  
   Yeni test metotları eklemek ve aynı şekilde kod ekleyin. Her test yönteminin olmalıdır `[TestMethod]` özniteliği.  
  
- **Bir yöntem UIMap.uitest**  
  
   Bu yöntem, kaydettiğiniz eylemleri veya doğrulamanız yapıldı değeri ayrıntılarını içerir. Bu kod UIMap.uitest açıp düzenleyebilirsiniz. Bu, silebilir veya yeniden düzenleyin kayıtlı eylemleri bir özelleştirilmiş düzenleyicisinde açılır.  
  
   Kuşak UIMap.Designer.cs içinde de metodu oluşturuldu görüntüleyin. Bu yöntem test çalıştırdığınızda, kaydettiğiniz eylemleri gerçekleştirir.  
  
  ```csharp  
  // File: UIMap.Designer.cs  
  public partial class UIMap  
  {  
    /// <summary>  
    /// Add two numbers  
    /// </summary>  
    public void AddTwoNumbers()  
    { ...   }  
  }  
  ```  
  
  > [!WARNING]
  >  Daha fazla test oluşturduğunuzda, yeniden oluşturulacak çünkü bu dosyayı düzenlemeniz değil.  
  
   Bu yöntemlerin uyarlanmış sürümleri için UIMap.cs kopyalayarak yapabilirsiniz. Örneğin, bir test yöntemi çağırabilir parametreli bir sürüm yapabilirsiniz:  
  
  ```csharp  
  // File: UIMap.cs  
  public partial class UIMap // Same partial class  
  {  
    /// <summary>  
    /// Add two numbers – parameterized version  
    /// </summary>  
    public void AddTwoNumbers(int firstNumber, int secondNumber)  
    { ...   // Code modified to use parameters.  
    }  
  }  
  ```  
  
- **UIMap.uitest bildirimlerinde**  
  
   Bu bildirimleri test tarafından kullanılan UI denetimleri uygulamanın temsil eder. Denetimleri çalıştırmak ve bunların özelliklerine erişmek için oluşturulan kod tarafından kullanılırlar.  
  
   Kendi kodunuzu yazma varsa bunları da kullanabilirsiniz. Örneğin, bir Web uygulamasında bir köprünün seçin, bir metin kutusunda bir değer yazın veya dal ve alanda bir değere göre farklı test eylemleri kullanarak test yöntemi olabilir.  
  
   Birden çok kodlanmış UI testleri ve birden çok UI haritası nesneleri ve büyük uygulamaları sınama kolaylaştırmak için dosyaları ekleyebilirsiniz. Daha fazla bilgi için [birden çok UI eşlemesi bulunan büyük uygulamaları sınama](../test/testing-a-large-application-with-multiple-ui-maps.md).  
  
  Oluşturulan kod hakkında daha fazla bilgi için bkz: [kodlanmış UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md).  
  
###  <a name="actions"></a> UI denetim eylemlerini ve özelliklerini kodlama  
 UI test denetimleri ile çalışırken kodlanmış UI testleri, iki bölüme ayrılır: akce a vlastnosti.  
  
- İlk bölümü, kullanıcı Arabirimi test denetimleri üzerinde gerçekleştirebileceğiniz eylemler oluşur. Örneğin, kodlanmış UI testleri, kullanıcı Arabirimi test denetim üzerinde fare tıklamasına benzetimini yapmak veya klavye kullanıcı Arabirimi test denetimini etkilemek için yazılan anahtarları benzetimi.  
  
- İkinci bölümü, almak ve UI testi denetimde özellikleri ayarlamak etkinleştirilmesi oluşur. Örneğin, kodlanmış UI testleri öğe sayısını alabilirsiniz bir `ListBox`, veya bir `CheckBox` seçili duruma.  
  
  **UI Test denetimi eylemlerini erişme**  
  
  UI test denetimlerinde fare tıklamasına veya klavye eylemleri gibi eylemleri gerçekleştirmek için yöntemleri kullanın. <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> ve <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> sınıflar:  
  
- Bir fare tıklaması gibi bir kullanıcı Arabirimi test denetimde fare odaklı bir eylem gerçekleştirmek için kullandığınız <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>.  
  
   `Mouse.Click(buttonCancel);`  
  
- Bir düzenleme denetimine yazarak gibi bir klavye odaklı eylemi gerçekleştirmek için kullandığınız <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>.  
  
   `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`  
  
  **UI Test denetimin özelliklerine erişme**  
  
  Almak ve UI denetimini belirli özellik değerlerini ayarlamak için doğrudan alın veya değerleri bir denetimin özelliklerini ayarlayın veya kullanabileceğiniz <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> ve <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> yöntemleriyle almak veya ayarlamak istediğiniz belirli bir özelliğin adı.  
  
  <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> ardından uygun dönüştürülebilen bir nesne döndürür <xref:System.Type>. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> bir nesne için özellik değerini kabul eder.  
  
##### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Özellikleri almak veya kullanıcı Arabirimi test denetimlerinden doğrudan ayarlamak için  
  
-   T:Microsoft.VisualStudio.TestTools.UITesting.UITestControl, t:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList veya T: gibi türetilen denetimler ile Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox, alma ya da özellik değerlerine, doğrudan, aşağıdaki gibi ayarlayın:  
  
    ```  
    int i = myHtmlList.ItemCount;  
    myWinCheckBox.Checked = true;  
    ```  
  
##### <a name="to-get-properties-from-ui-test-controls"></a>UI test denetimlerden özellikleri almak için  
  
-   Bir özellik değeri bir denetiminden almak için kullanın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.  
  
-   Özelliği almak için denetimin belirtmek için uygun dize ile kullanmak `PropertyNames` sınıfı parametresi olarak her bir denetimde <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> uygun veri türü, ancak bu dönüş değeri olarak atandığında döndürür bir <xref:System.Object>. Dönüş <xref:System.Object> uygun türü olarak dönüştürülmelidir.  
  
     Örnek:  
  
     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`  
  
##### <a name="to-set-properties-for-ui-test-controls"></a>UI testi denetimlerin özelliklerini ayarlamak için  
  
-   Bir denetimde bir özelliği ayarlamak için kullanın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.  
  
-   Ayarlanacak denetim özelliği belirtmek için uygun dize ile kullanmak `PropertyNames` ilk parametre olarak sınıf <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, ikinci parametre olarak özellik değeri ile.  
  
     Örnek:  
  
     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`  
  
###  <a name="debugging"></a> Hata Ayıklama  
 Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini analiz edebilirsiniz. Kodlanmış UI test günlüklerini filtre ve kayıt kodlanmış UI testleri hakkında önemli bilgiler çalıştırır. Günlükleri biçimi sorunları hızla ayıklamanıza olanak tanır. Daha fazla bilgi için [çözümleme kodlanmış UI testleri kullanarak kodlanmış UI Test günlüklerini](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).  
  
##  <a name="VerifyCodeUsingCUITWhatsNext"></a> Sırada ne var?  
 **Kodlanmış UI testleri çalıştırmak için ek seçenekler:** kodlanmış UI testleri bu konunun önceki kısımlarında açıklandığı gibi doğrudan Visual Studio'dan çalıştırabilirsiniz. Ayrıca, otomatikleştirilmiş UI testleri çalıştırabilirsiniz [!INCLUDE[TCMext](../includes/tcmext-md.md)], veya [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]. Kodlanmış UI testlerini otomatik olduğunda, bunları diğer otomatik testler çalıştırdığınızda, masaüstü ile etkileşimine izin sahiptirler.  
  
- [Nasıl yapılır: Microsoft Visual Studio'dan testler çalıştırma](http://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)  
  
- [Otomatikleştirilmiş testleri Microsoft Test Yöneticisi'ni çalıştırma](http://msdn.microsoft.com/en-us/0632f265-63fe-4859-a413-9bb934c66835)  
  
- [Nasıl yapılır: yapılandırma ve uygulamanızı oluşturduktan sonra zamanlanmış testleri çalıştırma](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)  
  
- [Yapı işleminizdeki testleri çalıştırın](http://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)  
  
- [Komut satırından otomatikleştirilmiş testler çalıştırma](http://msdn.microsoft.com/library/f18179c6-b688-4e41-9898-8aca130c4fc3)  
  
- [Nasıl yapılır: Test aracınızı masaüstüyle etkileşim kuran testleri çalıştırmak için ayarlama](~/E:/Repos/visualstudio-docs-pr/docs/test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md)  
  
- [&#91;kullanımdan&#93; kullanarak kodlanmış UI testlerini yük testlerinde](http://msdn.microsoft.com/library/704339ff-7da7-4d5f-acb3-c3b23f4acb43)  
  
  **Özel denetimler için destek ekleme:** kodlanmış UI Test Çerçevesi olası her UI desteklemez ve test etmek istediğiniz kullanıcı Arabirimi desteklemiyor olabilir. Örneğin, hemen bir kodlanmış UI testi için UI oluşturamazsınız [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Ancak, özel bir denetim destekleyen kodlanmış UI Test Çerçevesi uzantısı oluşturabilirsiniz.  
  
- [Denetimlerinizin Kodlanmış UI Testlerini Etkinleştirme](../test/enable-coded-ui-testing-of-your-controls.md)  
  
- [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)  
  
  Kodlanmış UI testleri genellikle el ile testleri otomatik hale getirmek için kullanılır. Ek rehberlik için bkz. [Testing for Continuous Delivery ile Visual Studio 2012 – Chapter 5: otomatikleşen sistem testleri](http://go.microsoft.com/fwlink/?LinkID=255196). El ile testleri hakkında daha fazla bilgi için bkz. [ &#91;kullanımdan&#93; oluşturma el ile Test çalışmaları Microsoft Test Yöneticisini kullanarak](http://msdn.microsoft.com/library/9989e184-c8e4-444b-998d-a1a5ec94461e). Otomatik Sistem testleri hakkında daha fazla bilgi için bkz. [oluşturarak otomatikleştirilmiş testleri Microsoft Test Yöneticisini kullanarak](http://msdn.microsoft.com/en-us/7b5075ee-ddfe-411d-b1d4-94283550a5d0).  
  
## <a name="external-resources"></a>Dış Kaynaklar  
  
### <a name="guidance"></a>Kılavuz  
 [Visual Studio 2012 – bölüm 2 ile sürekli teslimat testi: birim testi: iç testler](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Bölüm 5 – Visual Studio 2012 ile sürekli teslimat testi: Sistem testlerini otomatikleştirme](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="faq"></a>SSS  
 [Kodlanmış UI testleri SSS - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Kodlanmış UI testleri SSS -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [(Visual Studio UI Otomasyon Codeduı dahil) test etme](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>   
 [Kod kalitesini geliştirme](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)   
 [İzlenecek yol: Oluşturma, düzenleme ve kodlanmış UI testi bakımını yapma](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)   
 [Kodlanmış UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)   
 [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)   
 [Birden çok UI eşlemesi bulunan büyük uygulamaları sınama](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Kodlanmış UI Test düzenleyicisini kullanarak kodlanmış UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)   
 [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Visual Studio 2010'dan kodlanmış UI testlerini yükseltme](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)   
 [Mevcut eylem kaydından bir kodlanmış UI testi oluşturma](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)



