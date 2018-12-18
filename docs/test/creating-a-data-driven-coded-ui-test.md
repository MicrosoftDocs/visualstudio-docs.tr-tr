---
title: Verilerle Çalışan Kodlanmış UI Testi Oluşturma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 92bbeb34733332b2bada3955dda2058d63460fec
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068493"
---
# <a name="create-a-data-driven-coded-ui-test"></a>Verilerle çalışan kodlanmış UI testi oluşturma

Farklı koşulları test etmeye yönelik farklı parametre değerleriniz ile birden çok kez testleri çalıştırabilirsiniz. Verilerle çalışan kodlanmış UI testleri bunu yapmak için uygun bir yoldur. Veri kaynağındaki her satır bir kodlanmış UI test yinelemesini olduğunu ve parametre değerlerini bir veri kaynağı tanımlayın. Genel sonuç testi sonucu yineleme için hesaplanır. Örneğin, bir test yineleme başarısız olursa, genel test sonucu başarısız olur.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

## <a name="create-a-test-project"></a>Bir test projesi oluşturma

Bu örnek, Windows hesaplayıcısı uygulaması üzerinde çalışan kodlanmış UI testi oluşturur. İki sayıyı toplar ve toplamı doğru olduğunu doğrulamak için bir onay kullanır. Ardından, onaylama işlemi ve iki sayı parametre değerlerini virgülle ayrılmış bir değeri depolanan ve veri odaklı olmak kodlanmıştır (*.csv*) dosyası.

### <a name="step-1---create-a-coded-ui-test"></a>1. adım - kodlanmış UI testi oluşturma

1. Bir proje oluşturun.

    ![Kodlanmış UI test projesi oluşturma](../test/media/cuit_datadriven_.png)

   > [!NOTE]
   > Görmüyorsanız **kodlanmış UI Test projesi** şablon gereken [kodlanmış UI test bileşeni](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

2. Tercih **eylemlerini kaydedin**.

    ![Eylemleri kaydetmek seçin](../test/media/cuit_datadriven_generatecodedialog.png)

3. Hesaplayıcı uygulamasını açın ve testi kaydetmeyi başlatın.

    ![Kayıt eylemleri](../test/media/cuit_datadriven_cuitbuilder.png)

4. 1 ve 2 ekleme, kaydedicisini durdurur ve test yöntemi oluşturun. Daha sonra veri dosyasındaki değerlerle Biz bu kullanıcı girişi değerleri değiştirirsiniz.

    ![Genetate test yöntemi](../test/media/cuit_datadriven_cuitbuildergencode.png)

    Test Oluşturucusu'nu kapatın. Yöntemi, teste eklenir:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AddNumbers();
   }
   ```

5. Kullanım `AddNumbers()` test çalıştırdığını doğrulamak için yöntem. Yukarıda gösterilen test yönteminde imleci, bağlam menüsünü açın ve seçin **çalıştırmak testlerini**. (Klavye kısayolu: **Ctrl**+**R**,**T**).

    Test başarılı olup gösteren test sonucu görüntülenir **Test Gezgini** penceresi. Gelen Test Gezgini penceresi açmak için **Test** menüsünde seçin **Windows** seçip **Test Gezgini**.

6. Bir veri kaynağı onaylama parametre değerleri için de kullanılabilir olduğundan — beklenen değerlerini doğrulamak için test tarafından kullanılır — iki sayının toplamını doğru olduğunu doğrulamak için onaylama ekleyelim. Yukarıda gösterilen test yönteminde imleci, bağlam menüsünü açın ve seçin **kodlanmış UI testi için kod üret**, ardından **kullanım kodlanmış UI Test Oluşturucusu**.

    Toplamı görüntüleyen hesaplayıcı metin denetiminde eşleyin.

    ![Harita UI metin denetimi](../test/media/cuit_datadriven_addassertion.png)

7. Toplam değeri doğru olduğunu doğrulayan bir onay ekleyin. Seçin **görüntü metni** sahip özellik **3** seçip **onaylama Ekle**. Kullanım **AreEqual** karşılaştırıcı ve karşılaştırma değeri olduğundan emin olun **3**.

    ![Onaylama işlemi yapılandırma](../test/media/cuit_datadriven_builderaddassertion2.png)

8. Onaylama yapılandırdıktan sonra kodu yeniden Oluşturucu oluşturur. Bu, doğrulama için yeni bir yöntem oluşturur.

    ![Onaylama yöntemi](../test/media/cuit_datadriven_assertiongencode.png)

    Çünkü `ValidateSum` yöntemi doğrulama sonuçlarını `AddNumbers` yöntemi, kod bloğunun altına taşıyın.

   ```csharp
   public void CodedUITestMethod1()
   {
       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSum();
   }
   ```

9. Test kullanarak çalıştığını doğrulamak `ValidateSum()` yöntemi. Yukarıda gösterilen test yönteminde imleci, bağlam menüsünü açın ve seçin **çalıştırmak testlerini**. (Klavye kısayolu: **Ctrl**+**R**,**T**).

     Bu noktada, tüm parametre değerlerini kendi yöntemlerini sabiti olarak tanımlanır. Ardından, veri odaklı bizim test yapmak için bir veri kümesi oluşturalım.

### <a name="step-2---create-a-data-set"></a>2. adım - veri kümesi oluşturma

1.  Bir metin dosyası adlı dataDrivenSample projeye eklemek *data.csv*.

     ![Bir virgülle ayrılmış değer dosyası projeye ekleyin.](../test/media/cuit_datadriven_addcsvfile.png)

2.  Doldurma *.csv* aşağıdaki verilerle dosyası:

    |Num1|Num2|TOPLA|
    |-|-|-|
    |3|4|7|
    |5|6|11|
    |6|8|14|

     Veri ekledikten sonra dosyanın aşağıdaki gibi görünmelidir:

     ![.Csv dosyasını verilerle doldurma](../test/media/cuit_datadriven_adddatatocsvfile.png)

3.  Kaydetmeniz önemlidir *.csv* doğru kodlaması kullanarak dosya. Üzerinde **dosya** menüsünde seçin **Gelişmiş kaydetme seçenekleri** ve **Unicode (UTF-8 imza olmadan) - kod sayfası 65001** kodlama olarak.

4.  *.Csv* dosya, çıktı dizinine kopyalanmalıdır veya test çalıştırılamıyor. Kullanım **özellikleri** penceresini kopyalayın.

     ![.Csv dosyasını dağıtma](../test/media/cuit_datadriven_deploycsvfile.png)

     Şimdi oluşturulan veri kümesi sahibiz, test verilere bağlayın.

### <a name="step-3---add-data-source-binding"></a>3. adım - veri kaynağı bağlama ekleme

1.  Veri kaynağına bağlamak için ekleme bir `DataSource` görüntülenmesi için öznitelik `[TestMethod]` hemen test metodu özniteliği.

    ```csharp
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]
    public void CodedUITestMethod1()
    {
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();
    }
    ```

     Veri kaynağı artık bu test yöntemi, kullanabilmeniz için kullanılabilir.

    > [!TIP]
    > Bkz: [veri kaynağı özniteliği örnekleri](#CreateDataDrivenCUIT_QA_DataSourceAttributes) soru-cevap'ta XML, SQL Express ve Excel gibi diğer veri kaynağı türleri kullanma örnekleri için bir bölüm.

2.  Testi çalıştırın.

     Üç yineleme ile test çalışmaları dikkat edin. Veri kaynağına bağlanan üç veri satırı içerdiğinden budur. Ancak, test yine de sabit parametre değerlerini kullanıyor ve her zaman 1 + 2 3 toplamı ile ekliyor de görürsünüz.

     Ardından, veri kaynağı dosyasında değerleri kullanmak için test yapılandıracağız.

### <a name="step-4---use-the-data-in-the-coded-ui-test"></a>4. adım - veri kodlanmış UI testi kullanın

1.  Ekleme `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` üstüne *CodedUITest.cs* dosyası:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text.RegularExpressions;
    using System.Windows.Input;
    using System.Windows.Forms;
    using System.Drawing;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UnitTesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    ```

2.  Ekleme `TestContext.DataRow[]` içinde `CodedUITestMethod1()` yöntemi değerleri veri kaynağından uygulanır. Veri kaynağı değerleri denetimlerini kullanarak UIMap denetimlerine atanan sabitleri geçersiz kılma `SearchProperties`:

    ```csharp
    public void CodedUITestMethod1()
    {
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();this.UIMap.UICalculatorWindow.UIItemWindow21.UIItem2Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num2"].ToString();
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSumExpectedValues.UIItem2TextDisplayText = TestContext.DataRow["Sum"].ToString();
        this.UIMap.ValidateSum();
    }
    ```

     Verileri kodlamak için hangi arama özelliklerinin ekleyeceğimi için kodlanmış UI Test Düzenleyicisi'ni kullanın.

    -   Açık *UIMap.uitest* dosya.

         ![Kodlanmış UI Test Düzenleyicisi'ni açın](../test/media/cuit_datadriven_opentesteditor.png)

    -   UI eylemi seçin ve karşılık gelen UI denetim eşlemesi gözlemleyin. Nasıl eşleme kod, örneğin, karşılık gelen fark `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`.

         ![Kod ile yardımcı olması için kodlanmış UI Test Düzenleyicisi'ni kullanın](../test/media/cuit_datadriven_testeditor.png)

    -   İçinde **özellikleri** penceresinde açık **arama özellikleri**. Arama özellikleri **adı** değerdir veri kaynağını kullanma kodda neler değiştirildiği. Örneğin, `SearchProperties` her veri satırının ilk sütununu değerler atanır: `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`. Bu test için üç yineleme, değişir **adı** 3, sonra 5 ve 6 son arama özelliği için değer.

         ![Kodlama yardımcı olmak için arama özelliklerini kullanın](../test/media/cuit_datadriven_searchproperties.png)

3.  Çözümünüzü kaydedin.

### <a name="step-5---run-the-data-driven-test"></a>Adım 5 - veri tabanlı test çalıştırma

1.  Test şimdi testi yeniden çalıştırarak veri odaklı olduğunu doğrulayın.

     Test çalıştırması değerleri üç yineleme aracılığıyla görmelisiniz *.csv* dosya. Doğrulama de çalışması gerekir ve test, Test Gezgini'nde geçti olarak görüntülenmelidir.

## <a name="q--a"></a>Soru - Yanıt

###  <a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a> SQL Express veya XML gibi diğer veri kaynağı türleri için veri kaynağı öznitelikleri nelerdir?

Kodunuza kopyalayarak ve gereken özelleştirmeleri yaparak, aşağıdaki tabloda örnek veri kaynağı dizeleri kullanabilirsiniz.

**Veri kaynağı türleri ve öznitelikleri**

-   CSV

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`

-   Excel

     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`

-   Team Foundation Server test çalışmasında

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`

-   XML

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`

-   SQL Express

     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>UIMap.Designer dosyasındaki kodu neden değiştiremiyorum?

**Y:** herhangi bir kod, yaptığınız değişiklikler *UIMapDesigner.cs* UIMap - Kodlanmış UI Test Oluşturucusu kullanarak kodu üretmek her zaman dosya yazılır. Bu örnekte ve çoğu durumda, bir veri kaynağını kullanmak bir test etkinleştirmek için gereken kod değişikliği testin kaynak kod dosyasına yapılabilir (diğer bir deyişle, *Codeduıtest1.cs*).

Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, kendisine kopyalamalısınız *UIMap.cs* dosya ve yeniden adlandırın. *UIMap.cs* dosya, yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir *UIMapDesigner.cs* dosya. Orijinal yönteme başvuruyu içinde kodlanmış kaldırmalısınız *UITest.cs* dosya ve adlandırılan yöntem adıyla değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)