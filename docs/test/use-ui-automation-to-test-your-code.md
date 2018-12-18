---
title: Otomatikleştirilmiş UI testleri
ms.date: 12/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codedUITest
- vs.codedUITest.recorder
- vs.codedUITest.testbuilder
- vs.codedUITest.addAssertions
- vs.codedUITest.createdialog
helpviewer_keywords:
- automated tests, testing UI interface
- coded UI test
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce10c81265ecfd95f43d62c73d69c902eda1a6c6
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896646"
---
# <a name="use-ui-automation-to-test-your-code"></a>UI otomasyonunu kullanarak kodunuzu test etme

Uygulamanızın kullanıcı arabirimi (UI) sürücü otomatik testler olarak bilinir *kodlanmış UI testleri* (CUITs) Visual Studio'da. Bu testler, işlevsel test kullanıcı Arabirimi denetimleri içerir. Bunlar, kullanıcı arabirimi de dahil olmak üzere tüm uygulamanın düzgün çalıştığını doğrulamak olanak tanır. Kodlanmış UI testleri doğrulama veya başka bir mantık kullanıcı arabiriminde, örneğin, bir web sayfasındaki olduğunda özellikle yararlıdır. Mevcut bir el ile testi otomatik hale getirmek için de sık kullanılır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Aşağıdaki çizimde gösterildiği gibi tipik geliştirme deneyimi biri, başlangıçta yalnızca uygulamanızı oluşturmak ve burada şeyler düzgün çalıştığını doğrulamak için kullanıcı Arabirimi denetimleri tıklatın olabilir. Ardından uygulamayı el ile test etmek devam gerekmez, otomatikleştirilmiş bir testi oluşturmaya karar verebilirsiniz. Uygulamanızda sınanan belirli işlevi bağlı olarak kullanıcı Arabirimi düzeyinde test içermeyebilir veya bir tümleştirme testini veya işlevsel bir testi için kod yazabilirsiniz. Bazı iş mantığı doğrudan erişmek istiyorsanız, bir birim testi kodu. Ancak, belirli koşullar altında çeşitli kullanıcı Arabirimi denetimleri, uygulamanızda test dahil etmek yararlı olabilir. Kodlanmış UI testi, kod karmaşası uygulamanızın işlevselliğini etkilemez doğrulayabilirsiniz.

![Uygulama geliştirme sırasında test etme](../test/media/cuit_overview.png)

Kodlanmış UI testi oluşturmak kolaydır. Yalnızca el ile çalışırken test gerçekleştirmek **kodlanmış UI Test Oluşturucusu** arka planda çalışır. Ayrıca, hangi belirli alanlarla değerleri görünmelidir belirtebilirsiniz. **Kodlanmış UI Testi Oluşturucusu** eylemlerinizi kaydeder ve bunları kod oluşturur. Test oluşturulduktan sonra bir dizi eylem değiştirmenize olanak tanıyan özelleştirilmiş bir düzenleyici düzenleyebilirsiniz.

Alternatif olarak, Microsoft Test Yöneticisi'nde kaydedildiği bir test çalışması'iniz varsa, kod üretebilirsiniz ekleyebilirsiniz. Daha fazla bilgi için [kayıt ve yürütme geri el ile testleri](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts).

Özelleştirilmiş **kodlanmış UI Test Oluşturucusu** bunu kolayca oluşturma ve düzenleme kodlanmış UI testleri, test yerine kodlama becerilerinizi ana yoğunlaşmıştır bile Düzenleyicisi yapın. Ancak, böylece kopyalayıp uyarlamak basit bir geliştirici ve test daha gelişmiş bir biçimde genişletmek istediğiniz kodu yapılandırılmıştır. Örneğin, bir Web sitesinden bir şey satın almak için bir testi kaydedin ve ardından öğe sayısını satın bir döngü eklemek için oluşturulan kodu düzenleyin.

**Gereksinimler**

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

İlgili Platform ve yapılandırmaları desteklenir kodlanmış UI testleri tarafından daha fazla bilgi için bkz. [desteklenen platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

## <a name="install-the-coded-ui-test-component"></a>Kodlanmış UI test bileşenini yükleyin

Kodlanmış UI test araçları ve şablonları erişmek için yükleme **kodlanmış UI testi** Visual Studio 2017'in bileşeni.

1. Başlatma **Visual Studio yükleyicisi** seçerek **Araçları** > **araçları ve özellikleri Al**.

1. İçinde **Visual Studio yükleyicisi**, seçin **tek tek bileşenler** sekmesine ve ardından aşağı kaydırarak **hata ayıklama ve test** bölümü. Seçin **kodlanmış UI testi** bileşeni.

   ![Kodlanmış UI test bileşeni](media/coded-ui-test-component.png)

1. Seçin **değiştirme**.

## <a name="create-a-coded-ui-test"></a>Kodlanmış UI testi oluşturma

1. Kodlanmış UI testi projesi oluşturun.

   Kodlanmış UI testleri, kodlanmış UI test projesi içinde yer almalıdır. Kodlanmış UI test projesi yoksa bir tane oluşturun. Seçin **dosya** > **yeni** > **proje** açmak için **yeni proje** iletişim kutusu. Kategorileri soldaki bölmesinde **yüklü** > **Visual Basic** *veya* **Visual C#**  >   **Test**. Seçin **kodlanmış UI Test projesi** şablonu seçip **Tamam**.

   ![Kodlanmış UI testi proje şablonunu yeni proje iletişim kutusunda](media/coded-ui-test-project-template.png)

   > [!NOTE]
   > Görmüyorsanız **kodlanmış UI Test projesi** şablon gereken [kodlanmış UI test bileşeni](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

2. Kodlanmış UI test dosyası ekleyin.

     Kodlanmış UI projesi oluşturduysanız, ilk CUIT dosyasını otomatik olarak eklenir. Başka bir test dosyası eklemek için kodlanmış UI test projesi içinde kısayol menüsünde açın **Çözüm Gezgini**ve ardından **Ekle** > **kodlanmış UI testi**.

     İçinde **kodlanmış UI testi için kod üret** iletişim kutusunda **eylemleri Kaydet** > **UI haritasını Düzenle veya onaylama işlemleri Ekle**.

     ![Kodlanmış UI testi iletişim kutusu için kod oluşturma](media/generate-code-for-coded-ui-test.png)

     **Kodlanmış UI Test Oluşturucusu** görünür.

     ![Kodlanmış UI Test Oluşturucusu](../test/media/codedui_testbuilder.png)

3. Bir dizi eylem kaydı.

     **Kaydı başlatmak için**, seçin **kayıt** simgesi. Gerekirse, uygulama başlatma da dahil olmak üzere, uygulamanızda test etmek istediğiniz eylemleri gerçekleştirin. Örneğin, bir web uygulaması sınıyorsanız, bir tarayıcıyı başlatın, Web sitesine gidin ve uygulamada oturum açın.

     **Kaydı Duraklat için**, gelen e-posta ile uğraşmak zorunda kalırsanız örnek seçin için **duraklatmak**.

    > [!WARNING]
    > Masaüstü üzerinde gerçekleştirilen tüm eylemler kaydedilir. Hassas veriler kayda eklenmesini açabilir eylemleri gerçekleştiriyorsanız kaydı duraklatın.

     **Eylemleri silmek** yanlışlıkla kaydettiğiniz öğesini **düzenleme adımları**.

     **Kod üretmek için** , eylemlerinizi çoğaltmak, seçin **kod oluştur** simgesi ve türü bir ad ve açıklama için kodlanmış UI test metodu.

4. Metin kutuları gibi kullanıcı Arabirimi alanlarındaki değerleri doğrulayın.

     Seçin **onaylama Ekle** içinde **kodlanmış UI Test Oluşturucusu**, çalışan uygulamanızda bir UI denetimini seçin. Görüntülenen özellikler listesinde, örneğin, bir özellik seçin **metin** metin kutusunda. Kısayol menüsünde **onaylama Ekle**. Karşılaştırma işleci, karşılaştırma değeri ve hata iletisi iletişim kutusunda seçin.

     Onaylama işlemi pencereyi kapatın ve seçin **kod üret**.

     ![Kodlanmış UI test hedefleme öğesi](../test/media/codedui_1.png)

    > [!TIP]
    > Eylemlerini kaydederek ve değerlerini doğrulama arasında geçiş yapar. Her bir dizi eylem veya doğrulamaları sonunda kod oluşturur. İsterseniz, daha sonra yeni eylemler ve Doğrulamalar eklemeniz mümkün olacaktır.

     Daha fazla ayrıntı için [denetimlerin özelliklerini doğrulama](#validate-the-properties-of-ui-controls).

5. Oluşturulan test kodu görüntüleyin.

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

6. Daha fazla eylem ve Onaylamalar ekleme.

   Test yöntemi, uygun noktada imleci yerleştirin ve ardından kısayol menüsünden seçin **kodlanmış UI testi için kod üret**. Yeni kod bu noktada eklenir.

7. Test eylemlerini ve Onaylamalar ayrıntılarını düzenleyin.

     Açık *UIMap.uitest*. Bu dosya açılır **kodlanmış UI Test Düzenleyicisi**, burada, herhangi bir dizi kaydettiğiniz eylem düzenleme yapabilir onayları düzenleyin.

     ![Kodlanmış UI Test Düzenleyicisi](../test/media/cuit_editor_edit.png)

     Daha fazla bilgi için [düzenleme kodlanmış UI testleri, kodlanmış UI test düzenleyicisini kullanarak](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. Testi çalıştırın.

   Test Gezgini'ni kullanın veya test yönteminde kısayol menüsünü açın ve ardından **çalıştırmak testlerini**. Testlerin nasıl çalıştırılacağı hakkında daha fazla bilgi için bkz. [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md) ve *kodlanmış UI testleri çalıştırmak için ek seçenekler* içinde [sıradakiler?](#what's-next?) adresindeki bölüm Bu konunun sonuna.

Bu konuda geriye kalan bölümlerinde, bu yordamdaki adımları hakkında daha fazla ayrıntı sağlar.

Daha ayrıntılı bir örnek için bkz. [izlenecek yol: oluşturma, düzenleme ve kodlanmış UI testi koruma](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). İzlenecek yolda, oluşturmak, düzenlemek ve bir kodlanmış UI testinin nasıl yükleneceğini göstermek için basit bir Windows Presentation Foundation (WPF) uygulaması oluşturacaksınız. İzlenecek yol çeşitli zamanlama sorunları ve yeniden düzenlemeyi denetleme tarafından kırılan testleri düzeltmeye ilişkin çözümler sağlar.

## <a name="start-and-stop-the-application-under-test"></a>Testten geçirilen uygulamanın başlatıp

Uygulama, tarayıcı veya veritabanı her test için ayrı ayrı durdurmak ve başlatmak istemiyorsanız, aşağıdakilerden birini yapın:

- Test altındaki uygulamanızı başlatmak için eylemleri kaydetmek istemiyorsanız, seçmeden önce uygulamanızı başlamalıdır **kayıt** simgesi.

- Bir test sonunda, testin çalıştığı işlem sonlandırıldı. Uygulamanızı test başlattıysanız, uygulama genellikle kapatır.  Test çıktığında uygulamanız kapatmak için eklemek istemiyorsanız bir *.runsettings* dosya çözümünüze ve kullanma `KeepExecutorAliveAfterLegacyRun` seçeneği. Daha fazla bilgi için [bir .runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- Tarafından tanımlanan bir test başlatma yöntemi ekleme bir `[TestInitialize]` özniteliği, her test yönteminin başlangıcında kodu çalıştırır. Örneğin, uygulama TestInitialize yöntemden başlatabilir.

- Tarafından tanımlanan bir test temizleme yöntemi ekleme bir `[TestCleanup]` kod her test yönteminin sonunda çalıştırılan özniteliği. Örneğin, uygulamayı kapatmak için bu yöntem, TestCleanup yöntemi çağrılabilir.

## <a name="validate-the-properties-of-ui-controls"></a>UI denetimlerinin özelliklerini doğrulama

Kullanabileceğiniz **kodlanmış UI Test Oluşturucusu** bir kullanıcı arabirimi (UI) denetimine eklemek için <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> test veya onaylama UI denetimini kullanan bir doğrulama yöntemi için kod oluşturmak için.

Onaylar için kullanıcı Arabirimi denetimleri oluşturmak için Seç **onaylama Ekle** aracına **kodlanmış UI Test Oluşturucusu** ve doğrulamak istediğiniz test edilen uygulamada denetime doğru sürükleyin. Denetim kutusu özetlenmektedir, fare düğmesini bırakın. Denetimi sınıf kodunun hemen oluşturulur *UIMap.Designer.cs* dosya.

![Kodlanmış UI test hedefleme öğesi](../test/media/codedui_1.png)

Bu denetimin özelliklerini artık listelenen **onaylama Ekle** iletişim kutusu.

Özel bir denetime gezinme bir başka yolu oku seçmektir **(<<)** görünümü için genişletmek için **UI kontrol haritasını**. Üst, eşdüzey veya alt denetim bulmak için haritada herhangi bir yere tıklayın ve ağaç taşımak için ok tuşlarını kullanın.

![Kodlanmış UI test özelliklerini](../test/media/codedui_2.png)

> [!TIP]
> Uygulamanızda bir denetim seçin veya UI kontrol haritasında denetiminde görmüyor özeliklerini görmüyorsanız, denetimin uygulama kodunda benzersiz bir kimliği olduğunu doğrulayın. Benzersiz kimliği, bir HTML kimliği öznitelik veya bir WPF UId olabilir.

Ardından, özellikte doğrulayın ve sonra istediğiniz UI denetimi için kısayol menüsünü açın **onaylama Ekle**. İçinde **onaylama Ekle** iletişim kutusunda **karşılaştırıcı** örneğin değerinizi <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>, değerinizi içinde değeri yazın **karşılaştırma değeri**.

![Kodlanmış UI test onaylar](../test/media/codedui_3.png)

Testiniz için tüm onayları eklendiğinde seçin **Tamam**.

Onayları kodunu oluşturmak ve UI haritasına denetim eklemek için seçin **kod üret** simgesi. Kodlanmış UI test yönteminizde için bir ad ve yöntem için herhangi bir yorum olarak eklenir yöntemi için bir açıklama yazın. Seçin **Ekle ve Oluştur**. Ardından, **kapatmak** kapatmak için simge **kodlanmış UI Test Oluşturucusu**. Bu, aşağıdaki koda benzer bir kod oluşturur. Örneğin, girdiğiniz adı ise `AssertForAddTwoNumbers`, kodu şu örnekteki gibi görünecektir:

- Test yöntemi, kodlanmış UI test dosyanızdaki AssertForAddTwoNumbers onay yöntemi çağrısı ekler:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     Onaylar ve adımları sırasını değiştirmek için ya da yeni test metotları oluşturmak için bu dosyayı düzenleyebilirsiniz. Daha fazla kod eklemek için imleci test yönteminin ve kısayol menüsünde yer seçin **kodlanmış UI testi için kod üret**.

- Adlı bir yöntem ekler `AssertForAddTwoNumbers` UI eşlemenize (*UIMap.uitest*). Bu dosya açılır **kodlanmış UI Test Düzenleyicisi**, burada bir onayları düzenleyebilirsiniz.

     ![Düzenleme assert kodlanmış UI Test düzenleyicisini kullanarak](../test/media/cuit_editor_assert.png)

     Daha fazla bilgi için [düzenleme kodlanmış UI testleri, kodlanmış UI test düzenleyicisini kullanarak](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

     Oluşturulan kodun onaylama yöntemin de görüntüleyebilirsiniz *UIMap.Designer.cs*. Ancak, bu dosyayı düzenlemeniz değil. Uyarlanmış bir kod sürümünü hale getirmek isterseniz, yöntemler başka bir dosyaya gibi kopyalayın *UIMap.cs*yöntemleri yeniden adlandırın ve bunları düzenleyebilirsiniz.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>Klavyeyi kullanarak gizli bir denetim seçin

Seçmek istediğiniz denetim odağı kaybettiğinde ve seçtiğinizde kaybolur **onaylama Ekle** gelen aracı **kodlanmış UI Test Oluşturucusu**:

Bazı durumlarda, denetimleri eklediğiniz ve bunların özelliklerini doğrulayın, klavyeyi kullanmak gerekebilir. Örneğin, bir bağlam menü denetimini kullanan kodlanmış UI testi kaydetmeyi denediğinizde listesi denetiminde menü öğelerini odağı kaybeder ve seçmek çalıştığınızda kaybolur **onaylama Ekle** gelen aracı **kodlanmış UI testi Oluşturucu**. Bu bağlam menüsü Internet Explorer'da burada odağından ve ile seçmek çalışırsanız kaybolur aşağıdaki çizimde gösterilmiştir **onaylama Ekle** aracı.

![Sı Codeduıtest&#95;SelectControlKeyboard](../test/media/codeduitest_selectcontrolkeyboard.png)

UI denetimini seçmek için klavyeyi kullanmak için fareyi denetimin üzerine gelin. Ardından basılı **Ctrl** anahtarı ve **miyim** aynı zamanda anahtar. Anahtarları bırakın. Denetim tarafından kaydedilen **kodlanmış UI Test Oluşturucusu**.

#### <a name="manually-record-mouse-hovers"></a>El ile kayıt fare geldiğinde

Bir bir denetimi fareyle üzerine gelindiğinde kaydedemezsiniz varsa:

Bazı durumlarda, kullanılan belirli bir denetim bir kodlanmış UI testi el ile kayıt fare vurgulu olayları için klavyeyi kullanma gerektirebilir. Örneğin, bir Windows Form veya bir Windows Presentation Foundation (WPF) uygulaması test ettiğinizde, olabilir özel kod. Veya, bir kullanıcı üzerine geldiğinde genişleterek bir ağaç düğümü gibi bir denetimin üzerine geldiği için tanımlanan özel davranış olabilir. Bu gibi durumlarda test etmek için el ile bildir sahip **kodlanmış UI Test Oluşturucusu** klavye tuşlarını tuşlarına basarak denetimin üzerine geldiğinizde önceden tanımlanmış.

Kodlanmış UI testleri gerçekleştirdiğinizde, denetimin üzerine gelin. Tuşuna basın ve basılı **Ctrl**, basılı durumdayken **Shift** ve **R** klavyenizde anahtarları. Anahtarları bırakın. Fareyi üzerine gelindiğinde kullanılacak olay tarafından kaydedilen **kodlanmış UI Test Oluşturucusu**.

![Codeduı&#95;getirin](../test/media/codedui_hover.png)

Test yöntemi oluşturduktan sonra aşağıdaki örneğe benzer bir kod eklenecek *UIMap.Designer.cs* dosyası:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>Fareyle üzerine gelindiğinde klavye atamalarını yapılandırma

Fare vurgulu olaylarını yakalamak için anahtar atama başka bir yerde my ortamda kullanılıp kullanılmadığını:

Gerekirse, varsayılan atamasını klavye varsa **Ctrl**+**Shift**+**R** , kodlanmış UI testlerinde fare vurgulu olayları uygulamak için kullanılır farklı anahtarları kullanacak şekilde yapılandırılabilir.

> [!WARNING]
> Normal koşullar altında fare vurgulu olayları için klavye atamaları değiştirmek sahip olmamalıdır. Klavye atama elemanına dikkatli olun. Seçtiğiniz zaten Visual Studio veya test edilen uygulamanın başka bir yere kapsamında kullanımda olabilir.

Klavye atamaları değiştirmek için aşağıdaki yapılandırma dosyasını değiştirin:

*% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Yapılandırma dosyasında değerlerini değiştirmek `HoverKeyModifier` ve `HoverKey` anahtarları klavye atamaları değiştirmek için:

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Web tarayıcısı eklenmemesi örtük fare ayarlayın

Kayıt sorunları yaşıyorsanız, fare bir Web sitesinde gezinen:

Belirli bir denetimin üzerine geldiğinizde birçok Web sitesi, bu ek ayrıntıları göster genişletir. Genellikle, bu gibi Masaüstü uygulamaları menülerde arayın. Bu yaygın bir düzen olduğundan, Web'e göz atmak için örtük eklenmemesi kodlanmış UI testleri etkinleştirin. Örneğin, kayıt Internet Explorer'da getirirse, bir olay harekete geçirilir. Bu olaylar kaydediliyor yedekli eklenmemesi için yol açabilir. Bu nedenle, örtük eklenmemesi ile kaydedilen `ContinueOnError` kümesine `true` kullanıcı Arabirimi test yapılandırma dosyası. Bu, kayıttan yürütmenin vurgulu event başarısız olursa devam etmesini sağlar.

Bir web tarayıcısında örtük eklenmemesi kaydını etkinleştirmek için yapılandırma dosyasını açın:

*% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Yapılandırma dosyası anahtar olduğunu doğrulayın `RecordImplicitiHovers` ayarlamak bir değerini `true` aşağıdaki örnekte gösterildiği gibi:

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Kodlanmış UI testi özelleştirme

Kodlanmış UI testi oluşturduktan sonra Visual Studio'da aşağıdaki araçlardan herhangi birini kullanarak düzenleyebilirsiniz:

- Kullanım **kodlanmış UI Test Oluşturucusu** testlerinize ek denetimleri ve doğrulama eklemek için. Bölümüne bakın [denetimleri ve bunların özelliklerini doğrulama](#validate-the-properties-of-ui-controls) bu konuda.

- **Kodlanmış UI Test Düzenleyicisi** kolayca kodlanmış UI testleri değiştirmenize olanak tanır. Kullanarak **kodlanmış UI Test Düzenleyicisi**, bulmak, görüntülemek ve test yöntemlerinizi düzenleyin. UI eylemlerini ve bunların ilişkili denetimleri UI kontrol haritasında de düzenleyebilirsiniz. Daha fazla bilgi için [düzenleme kodlanmış UI testleri, kodlanmış UI test düzenleyicisini kullanarak](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Kod Düzenleyicisi:**

    - Bölümünde anlatıldığı gibi denetimler için kodu testinizde el ile ekleyin [kodlanmış UI denetim eylemlerini ve özelliklerini](#coded-ui-control-actions-and-properties) bölümüne bakın.

    - Kodlanmış UI testi oluşturduktan sonra veri odaklı olarak değiştirebilirsiniz. Daha fazla bilgi için [verilerle çalışan kodlanmış UI testi oluşturma](../test/creating-a-data-driven-coded-ui-test.md).

    - Bir kodlanmış UI Testi kayıttan yürütmesinde kaybolur ve benzeri için ilerleme çubuğunu oluşmasına görünmesi için bir pencere gibi belirli olaylar için beklenecek test bildirebilirsiniz. Bunu yapmak için uygun UITestControl.WaitForControlXXX() yöntemini ekleyin. Kullanılabilir yöntemleri tam listesi için bkz [olun kodlanmış UI testleri, kayıttan yürütme sırasında belirli olaylar için bekleyin](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Bir denetim WaitForControlEnabled yöntemi kullanarak etkin olmasını bekler, kodlanmış UI testi örneği için bkz [izlenecek yol: oluşturma, düzenleme ve kodlanmış UI testi koruma](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

    - Kodlanmış UI testleri, Internet Explorer 9 ve Internet Explorer 10 HTML5 denetimleri bazıları için destek içerir. Daha fazla bilgi için [kullanarak HTML5 denetimleri kodlanmış UI testlerinde](../test/using-html5-controls-in-coded-ui-tests.md).

    - Kodlanmış UI testi kodlama Kılavuzu:

       - [Kodlanmış UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)

       - [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)

       - [Birden çok UI eşlemesi bulunan büyük uygulamaları test etme](../test/testing-a-large-application-with-multiple-ui-maps.md)

       - [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>Oluşturulan kod

Seçeneğini belirlediğinizde **kod üret**, bazı kod parçalarını oluşturulur:

- Bir test yönteminin satır.

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

- Bir yöntemde *UIMap.uitest*.

     Bu yöntem, kaydettiğiniz eylemleri veya doğrulamanız yapıldı değeri ayrıntılarını içerir. Bu kod açarak düzenleyebileceğiniz *UIMap.uitest*. Bu, silebilir veya yeniden düzenleyin kayıtlı eylemleri bir özelleştirilmiş düzenleyicisinde açılır.

     Oluşturulan yöntemi de görüntüleyebilirsiniz *UIMap.Designer.cs*. Bu yöntem test çalıştırdığınızda, kaydettiğiniz eylemleri gerçekleştirir.

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
    > Daha fazla test oluşturduğunuzda, yeniden oluşturulacak çünkü bu dosyayı düzenlemeniz değil.

     Bu yöntemlerin uyarlanmış sürümleri için kopyalayarak yapabileceğiniz *UIMap.cs*. Örneğin, bir test yöntemi çağırabilir parametreli bir sürüm yapabilirsiniz:

    ```csharp
    // File: UIMap.cs
    public partial class UIMap // Same partial class
    {
      /// <summary>
      /// Add two numbers - parameterized version
      /// </summary>
      public void AddTwoNumbers(int firstNumber, int secondNumber)
      { ...   // Code modified to use parameters.
      }
    }
    ```

- Bildirimlerinde *UIMap.uitest*.

    Bu bildirimleri test tarafından kullanılan UI denetimleri uygulamanın temsil eder. Denetimleri çalıştırmak ve bunların özelliklerine erişmek için oluşturulan kod tarafından kullanılırlar.

    Kendi kodunuzu yazma varsa bunları da kullanabilirsiniz. Örneğin, bir web uygulamasında bir köprünün seçin, bir metin kutusunda bir değer yazın veya dal ve alanda bir değere göre farklı test eylemleri kullanarak test yöntemi olabilir.

    Birden çok kodlanmış UI testleri ve birden çok UI haritası nesneleri ve büyük uygulamaları sınama kolaylaştırmak için dosyaları ekleyebilirsiniz. Daha fazla bilgi için [birden çok UI eşlemesi bulunan büyük uygulamaları Test](../test/testing-a-large-application-with-multiple-ui-maps.md).

Oluşturulan kod hakkında daha fazla bilgi için bkz: [kodlanmış UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md).

## <a name="coded-ui-control-actions-and-properties"></a>Kodlanmış UI denetim eylemlerini ve özellikleri

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

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Özellikleri almak veya kullanıcı Arabirimi test denetimlerinden doğrudan ayarlamak için

Öğesinden türetilen denetimlerle <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>, gibi [HTML liste](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) veya [WinComboBox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox), alma veya doğrudan özellik değerlerine ayarlayın. Aşağıdaki kod, bazı örnekler gösterilmektedir:

 ```csharp
 int i = myHtmlList.ItemCount;
 myWinCheckBox.Checked = true;
 ```

### <a name="to-get-properties-from-ui-test-controls"></a>UI test denetimlerden özellikleri almak için

- Bir özellik değeri bir denetiminden almak için kullanın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- Özelliği almak için denetimin belirtmek için uygun dize ile kullanmak `PropertyNames` sınıfı parametresi olarak her bir denetimde <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> uygun veri türü, ancak bu dönüş değeri olarak atandığında döndürür bir <xref:System.Object>. Dönüş <xref:System.Object> uygun türü olarak dönüştürülmelidir.

     Örnek:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>UI testi denetimlerin özelliklerini ayarlamak için

- Bir denetimde bir özelliği ayarlamak için kullanın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.

- Ayarlanacak denetim özelliği belirtmek için uygun dize ile kullanmak `PropertyNames` ilk parametre olarak sınıf <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, ikinci parametre olarak özellik değeri ile.

     Örnek:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>Hata ayıklama

Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini analiz edebilirsiniz. Kodlanmış UI test günlüklerini filtre ve kayıt kodlanmış UI testleri hakkında önemli bilgiler çalıştırır. Günlükleri biçimi sorunları hızla ayıklamanıza olanak tanır. Daha fazla bilgi için [Çözümle kodlanmış UI testleri, kodlanmış UI test günlüklerini kullanarak](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="whats-next"></a>Sırada ne var?

**Kodlanmış UI testleri çalıştırmak için ek seçenekler:** kodlanmış UI testleri bu konunun önceki kısımlarında açıklandığı gibi doğrudan Visual Studio'dan çalıştırabilirsiniz. Ayrıca, Microsoft Test Yöneticisi veya Azure komut zincirlerini kullanarak otomatikleştirilmiş UI testleri çalıştırabilirsiniz. Kodlanmış UI testlerini otomatik olduğunda, bunları diğer otomatik testler çalıştırdığınızda, masaüstü ile etkileşimine izin sahiptirler.

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)

- [Yapı işleminizdeki testleri çalıştırın](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)

- [Nasıl yapılır: test aracınızı masaüstüyle etkileşim kuran testleri çalıştırmak için ayarlama](https://msdn.microsoft.com/Library/3a94dd07-6d17-402c-ae8f-7947143755c9)

**Özel denetimler için destek ekleme:** kodlanmış UI Test Çerçevesi olası her UI desteklemez ve test etmek istediğiniz kullanıcı Arabirimi desteklemiyor olabilir. Örneğin, Microsoft Excel için kodlanmış UI testi kullanıcı arabiriminin hemen oluşturulamıyor. Ancak, özel bir denetim destekleyen kodlanmış UI Test Çerçevesi uzantısı oluşturabilirsiniz.

- [Kodlanmış UI denetimlerinizin etkinleştir](../test/enable-coded-ui-testing-of-your-controls.md)

- [Kodlanmış UI testleri ve eylem kayıtları genişletin](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Kodlanmış UI testleri genellikle el ile testleri otomatik hale getirmek için kullanılır. El ile testleri hakkında daha fazla bilgi için bkz. [Microsoft Test Yöneticisi ile el ile testler](/azure/devops/test/mtm/run-manual-tests-with-microsoft-test-manager?view=vsts). Otomatikleştirilmiş testleri hakkında daha fazla bilgi için bkz: [Visual Studio'daki Test Araçları](../test/improve-code-quality.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [İzlenecek yol: Oluşturma, düzenleme ve bir kodlanmış UI testinin](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Kodlanmış UI testi için test UWP uygulaması oluşturma](test-uwp-app-with-coded-ui-test.md)
- [Kodlanmış UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)
- [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)
- [Birden çok UI eşlemesi bulunan büyük uygulamaları test etme](../test/testing-a-large-application-with-multiple-ui-maps.md)
