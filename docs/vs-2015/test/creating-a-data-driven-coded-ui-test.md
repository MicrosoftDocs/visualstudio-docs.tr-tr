---
title: Kodlanmış UI testi oluşturma verilerle | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests, data-driven
ms.assetid: 5838f02d-001f-49ce-adce-c9ea1afaec2f
caps.latest.revision: 58
ms.author: gewarren
manager: douge
ms.openlocfilehash: d3674d6ccbda89a2a3ee1de551587ba034ba51c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932630"
---
# <a name="creating-a-data-driven-coded-ui-test"></a>Verilerle Çalışan Kodlanmış UI Testi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Farklı koşulları test etmeye yönelik farklı parametre değerleriniz ile birden çok kez testleri çalıştırabilirsiniz. Verilerle çalışan kodlanmış UI testleri bunu yapmak için uygun bir yoldur. Veri kaynağındaki her satır bir kodlanmış UI test yinelemesini olduğunu ve parametre değerlerini bir veri kaynağı tanımlayın. Genel sonuç testi sonucu yineleme için hesaplanır. Örneğin, bir test yineleme başarısız olursa, genel test sonucu başarısız olur.  
  
 **Gereksinimler**  
  
-   Visual Studio Enterprise  
  
## <a name="create-a-data-driven-coded-ui-test"></a>Verilerle çalışan kodlanmış UI testi oluşturma  
 Bu örnek, Windows hesaplayıcısı uygulaması üzerinde çalışan kodlanmış UI testi oluşturur. İki sayıyı toplar ve toplamı doğru olduğunu doğrulamak için bir onay kullanır. Ardından, onaylama işlemi ve parametre değerlerini iki sayı için veri odaklı ve depolanan bir virgülle ayrılmış değer (.csv) dosyasında olacak kodlanmıştır.  
  
#### <a name="step-1---create-a-coded-ui-test"></a>1. adım - kodlanmış UI testi oluşturma  
  
1.  Bir proje oluşturun.  
  
     ![Kodlanmış UI test projesi oluşturma](../test/media/cuit-datadriven.png "CUIT_dataDriven_")  
  
2.  Eylemleri kaydetmek bu seçeneği seçin.  
  
     ![Eylemleri kaydetmeyi](../test/media/cuit-datadriven-generatecodedialog.png "CUIT_dataDriven_GenerateCodeDialog")  
  
3.  Hesaplayıcı uygulamasını açın ve testi kaydetmeyi başlatın.  
  
     ![Eylemleri Kaydet](../test/media/cuit-datadriven-cuitbuilder.png "CUIT_dataDriven_CUITBuilder")  
  
4.  1 ve 2 ekleme, kaydedicisini durdurur ve test yöntemi oluşturun. Daha sonra veri dosyasındaki değerlerle Biz bu kullanıcı girişi değerleri değiştirirsiniz.  
  
     ![Test yöntemi Genetate](../test/media/cuit-datadriven-cuitbuildergencode.png "CUIT_dataDriven_CUITBuilderGenCode")  
  
     Test Oluşturucusu'nu kapatın. Yöntemi, teste eklenir:  
  
    ```csharp  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
  
    }  
    ```  
  
5.  Kullanım `AddNumbers()` test çalıştırdığını doğrulamak için yöntem. Yukarıda gösterilen test yönteminde imleci, bağlam menüsünü açın ve seçin **çalıştırmak testlerini**. (Klavye kısayolu: Ctrl + R, T).  
  
     Test sonucu geçti veya başarısız olan test Test Gezgini penceresinde gösterilip gösterilmediğini gösterir. Gelen Test Gezgini penceresi açmak için **TEST** menüsünde seçin **Windows** seçip **Test Gezgini**.  
  
6.  Bir veri kaynağı onaylama parametre değerleri için de kullanılabilir olduğundan — beklenen değerlerini doğrulamak için test tarafından kullanılır — iki sayının toplamını doğru olduğunu doğrulamak için onaylama ekleyelim. Yukarıda gösterilen test yönteminde imleci, bağlam menüsünü açın ve seçin **kodlanmış UI testi için kod üret**, ardından **kullanım kodlanmış UI Test Oluşturucusu**.  
  
     Toplamı görüntüleyen hesaplayıcı metin denetiminde eşleyin.  
  
     ![Harita UI metin denetimi](../test/media/cuit-datadriven-addassertion.png "CUIT_dataDriven_AddAssertion")  
  
7.  Toplam değeri doğru olduğunu doğrulayan bir onay ekleyin. Seçin **görüntü metni** sahip özellik **3** seçip **onaylama Ekle**. Kullanım **AreEqual** karşılaştırıcı ve karşılaştırma değeri olduğundan emin olun **3**.  
  
     ![Onay yapılandırma](../test/media/cuit-datadriven-builderaddassertion2.png "CUIT_dataDriven_BuilderAddAssertion2")  
  
8.  Onaylama yapılandırdıktan sonra kodu yeniden Oluşturucu oluşturur. Bu, doğrulama için yeni bir yöntem oluşturur.  
  
     ![Onaylama işlemi metodunu üret](../test/media/cuit-datadriven-assertiongencode.png "CUIT_dataDriven_AssertionGenCode")  
  
     Çünkü `ValidateSum` yöntemi doğrulama sonuçlarını `AddNumbers` yöntemi, kod bloğunun altına taşıyın.  
  
    ```csharp  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSum();  
  
    }  
    ```  
  
9. Test kullanarak çalıştığını doğrulamak `ValidateSum()` yöntemi. Yukarıda gösterilen test yönteminde imleci, bağlam menüsünü açın ve seçin **çalıştırmak testlerini**. (Kısayol: Ctrl + R, T klavye).  
  
     Bu noktada, tüm parametre değerlerini kendi yöntemlerini sabiti olarak tanımlanır. Ardından, veri odaklı bizim test yapmak için bir veri kümesi oluşturalım.  
  
#### <a name="step-2---create-a-data-set"></a>2. adım - veri kümesi oluşturma  
  
1.  Bir metin dosyası adlı dataDrivenSample projeye eklemek `data.csv`.  
  
     ![Bir virgülle ayrılmış değer dosyası projeye eklemek](../test/media/cuit-datadriven-addcsvfile.png "CUIT_dataDriven_AddCSVFile")  
  
2.  .Csv dosyasında aşağıdaki verilerle doldurur:  
  
    |Num1|Num2|TOPLA|  
    |----------|----------|---------|  
    |3|4|7|  
    |5|6|11|  
    |6|8|14|  
  
     Veri ekledikten sonra dosyanın aşağıdaki gibi görünmelidir:  
  
     ![Doldurun. Veri içeren CSV dosyası](../test/media/cuit-datadriven-adddatatocsvfile.png "CUIT_dataDriven_AddDataToCSVFile")  
  
3.  Doğru kodlama kullanılarak .csv dosyasını kaydetmek önemlidir. Üzerinde **dosya** menüsünde seçin **Gelişmiş kaydetme seçenekleri** ve **Unicode (UTF-8 imza olmadan) – kod sayfası 65001** kodlama olarak.  
  
4.  Çıkış dizinine .csv dosyasını kopyaladığınız veya test çalıştırılamıyor. Kopyalamak için Özellikler penceresini kullanın.  
  
     ![Dağıtın. CSV dosyası](../test/media/cuit-datadriven-deploycsvfile.png "CUIT_dataDriven_DeployCSVFile")  
  
     Şimdi oluşturulan veri kümesi sahibiz, test verilere bağlayın.  
  
#### <a name="step-3--add-data-source-binding"></a>3. adım – veri kaynağına bağlama Ekle  
  
1.  Veri kaynağına bağlamak için ekleme bir `DataSource` görüntülenmesi için öznitelik `[TestMethod]` hemen test metodu özniteliği.  
  
    ```  
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
    >  Bkz: [veri kaynağı özniteliği örnekleri](#CreateDataDrivenCUIT_QA_DataSourceAttributes) soru-cevap'ta XML, SQL Express ve Excel gibi diğer veri kaynağı türleri kullanma örnekleri için bir bölüm.  
  
2.  Testi çalıştırın.  
  
     Üç yineleme ile test çalışmaları dikkat edin. Veri kaynağına bağlanan üç veri satırı içerdiğinden budur. Ancak, test yine de sabit parametre değerlerini kullanıyor ve her zaman 1 + 2 3 toplamı ile ekliyor de görürsünüz.  
  
     Ardından, veri kaynağı dosyasında değerleri kullanmak için test yapılandıracağız.  
  
#### <a name="step-4--use-the-data-in-the-coded-ui-test"></a>4. adım – kodlanmış UI testi verileri kullanma  
  
1.  Ekleme `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` CodedUITest.cs dosyanın en üstüne:  
  
    ```  
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
  
    ```  
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
  
    -   UIMap.uitest dosyasını açın.  
  
         ![Kodlanmış UI Test Düzenleyicisi'ni açma](../test/media/cuit-datadriven-opentesteditor.png "CUIT_dataDriven_OpenTestEditor")  
  
    -   UI eylemi seçin ve karşılık gelen UI denetim eşlemesi gözlemleyin. Nasıl eşleme kod, örneğin, karşılık gelen fark `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`.  
  
         ![Kod ile yardımcı olması için kodlanmış UI Test Düzenleyicisi'ni kullanın](../test/media/cuit-datadriven-testeditor.png "CUIT_dataDriven_TestEditor")  
  
    -   Özellikler penceresinde açın **arama özellikleri**. Arama özellikleri **adı** değerdir veri kaynağını kullanma kodda neler değiştirildiği. Örneğin, `SearchProperties` her veri satırının ilk sütununu değerler atanır: `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`. Bu test için üç yineleme, değişir **adı** 3, sonra 5 ve 6 son arama özelliği için değer.  
  
         ![Kodlama yardımcı olmak için arama özelliklerini kullanın](../test/media/cuit-datadriven-searchproperties.png "CUIT_dataDriven_SearchProperties")  
  
3.  Çözümünüzü kaydedin.  
  
#### <a name="step-5--run-the-data-driven-test"></a>Adım 5-veri tabanlı test çalıştırma  
  
1. Test şimdi testi yeniden çalıştırarak veri odaklı olduğunu doğrulayın.  
  
    .Csv dosyasında değerleri kullanarak üç yineleme aracılığıyla testi görmeniz gerekir. Doğrulama de çalışması gerekir ve test, Test Gezgini'nde geçti olarak görüntülenmelidir.  
  
   **Kılavuz**  
  
   Ek bilgi için bkz: [Visual Studio 2012 – bölüm 2 ile sürekli teslimat testi: birim testi: iç testler](http://go.microsoft.com/fwlink/?LinkID=255188) ve [Visual Studio 2012 – Chapter 5 ile sürekli teslimat testi: Sistem testlerini otomatikleştirme](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
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
  
### <a name="q-can-i-use-data-driven-tests-on-my-windows-phone-app"></a>Windows Phone uygulamamı veri tabanlı testler kullanabilir miyim?  
 **Y:** Evet. Windows Phone için verilerle çalışan kodlanmış UI testleri bir test yönteminde DataRow özniteliği kullanılarak tanımlanır. Aşağıdaki örnek, x ve y ilk yineleme ve -1 -2 için ikinci bir test yinelemesini için 1 ve 2 değerlerini kullanın.  
  
```  
[DataRow(1, 2, DisplayName = "Add positive numbers")]  
[DataRow(-1, -2, DisplayName = "Add negative numbers")]  
[TestMethod]  
public void DataDrivingDemo_MyTestMethod(int x, int y)  
  
```  
  
### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>UIMap.Designer dosyasındaki kodu neden değiştiremiyorum?  
 **Y:** UIMap - Kodlanmış UI Test Oluşturucusu kullanarak kodu üretmek her zaman UIMapDesigner.cs dosyasında yaptığınız herhangi bir kod değişikliği üzerine yazılır. Bu örnekte ve çoğu durumda, bir veri kaynağını kullanmak bir test etkinleştirmek için gereken kod değişikliği testin kaynak kod dosyasına (diğer bir deyişle, Codeduıtest1.cs) yapılabilir.  
  
 Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, yöntemi UIMap.cs dosyasına kopyalayıp yeniden adlandırmanız gerekir. UIMap.cs dosyası, UIMapDesigner.cs dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış UITest.cs dosyasındaki orijinal yönteme başvuruyu kaldırıp yeniden adlandırılan yöntem adıyla değiştirmelisiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>   
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)   
 [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



