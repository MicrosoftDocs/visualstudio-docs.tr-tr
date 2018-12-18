---
title: Kodlanmış UI testinin anatomisi | Microsoft Docs
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
- coded UI tests
ms.assetid: 9c5d82fc-3fb7-4bb1-a9ac-ac1fa3a4b500
caps.latest.revision: 25
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7595a967a6dae091da6c5a7613a27c602cc1381e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202754"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Kodlanmış UI Testinin Anatomisi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çeşitli dosyalar, bir kodlanmış UI testi kodlanmış UI testi projesi oluşturduğunuzda, çözümünüze eklenir. Bu konuda, bu dosyaları keşfetmek için kodlanmış UI testi örneği kullanacağız.  
  
 **Gereksinimler**  
  
-   Visual Studio Enterprise  
  
## <a name="contents-of-a-coded-ui-test"></a>Kodlanmış UI testi içeriği  
 Bir kodlanmış UI testi, oluşturduğunuzda **kodlanmış UI Test Oluşturucusu** test ve ayrıca test yöntemleri, parametreleri ve altındaki tüm testler için onaylar kullanıcı arabiriminin bir harita oluşturur. Ayrıca, her test için bir sınıf dosyası oluşturur.  
  
|Dosya|İçindekiler|Düzenlenebilir?|  
|----------|--------------|---------------|  
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Bildirimler bölümü](#UIMapDesignerFile)<br /><br /> [UIMap sınıfı](#UIMapClass) (kısmi, otomatik olarak oluşturulan)<br /><br /> [Yöntemler](#UIMapMethods)<br /><br /> [Özellikler](#UIMapProperties)|Hayır|  
|[UIMap.cs](#UIMapCS)|[UIMap sınıfı](#UIMapCS) (kısmi)|Evet|  
|[Codeduıtest1.cs](#CodedUITestCS)|[Codeduıtest1 sınıfı](#CodedUITestCS)<br /><br /> [Yöntemler](#CodedUITestMethods)<br /><br /> [Özellikler](#CodedUITestProperties)|Evet|  
|[UIMap.uitest](#UIMapuitest)|UI testi için XML eşleme.|Hayır|  
  
###  <a name="UIMapDesignerFile"></a> UIMap.Designer.cs  
 Bu dosya tarafından otomatik olarak oluşturulan kodu içeren **kodlanmış UI Test Oluşturucusu** bir testi oluşturulduğunda. Bu dosya bir dosya ekleyin veya kod değiştirme olmaması bir test değiştirir, her seferinde yeniden oluşturulur.  
  
#### <a name="declarations-section"></a>Bildirimler bölümü  
 Bu bölüm, bir Windows kullanıcı arabirimi aşağıdaki bildirimleri içerir.  
  
```csharp  
using System;  
using System.CodeDom.Compiler;  
using System.Collections.Generic;  
using System.Drawing;  
using System.Text.RegularExpressions;  
using System.Windows.Input;  
using Microsoft.VisualStudio.TestTools.UITest.Extension;  
using Microsoft.VisualStudio.TestTools.UITesting;  
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;  
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;  
using MouseButtons = System.Windows.Forms.MouseButtons;  
```  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> Bir Windows kullanıcı arabirimi (UI) ad alanı bulunur. Bir Web sayfası kullanıcı Arabirimi için bir ad alanı olacaktır <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>; bir Windows Presentation Foundation kullanıcı arabirimi, ad alanı olacaktır <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>.  
  
####  <a name="UIMapClass"></a> UIMap sınıfı  
 Sonraki bölüm dosyanın <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> sınıfı.  
  
```  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public partial class UIMap  
```  
  
 Sınıf kodu ile başlayan bir <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> kısmi bir sınıf olarak bildirilen sınıfa uygulanır. Bu dosyada bulunan her sınıf için öznitelik de geçerli fark edeceksiniz. Bu sınıf için daha fazla içerebilecek dosya `UIMap.cs`, hangi ele alınmıştır daha sonra.  
  
 Oluşturulan `UIMap` sınıfı, her yöntem zaman test kaydedildiği belirtilen için kod içerir.  
  
```  
public void LaunchCalculator()  
public void AddItems()  
public void VerifyTotal()  
public void CleanUp()  
```  
  
 Bu bölümü <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> sınıfı yöntemleri için gereken her bir özellik için oluşturulan kodu da içerir.  
  
```  
public virtual LaunchCalculatorParams LaunchCalculatorParams  
public virtual AddItemsParams AddItemsParams  
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues  
public virtual CalculateItemsParams CalculateItemsParams  
public virtual VerifyMathAppTotalExpectedValues   
    VerifyMathAppTotalExpectedValues  
public UIStartMenuWindow UIStartMenuWindow  
public UIRunWindow UIRunWindow  
public UICalculatorWindow UICalculatorWindow  
public UIStartWindow UIStartWindow  
public UIMathApplicationWindow UIMathApplicationWindow  
```  
  
#####  <a name="UIMapMethods"></a> UIMap yöntemi  
 Her yöntem benzer bir yapıya sahip `AddItems()` yöntemi. Bu, netlik eklemek için satır sonları ile birlikte sunulan kodu altında daha ayrıntılı açıklanmıştır.  
  
```  
/// <summary>  
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.  
/// </summary>  
public void AddItems()  
{  
    #region Variable Declarations  
    WinControl uICalculatorDialog =   
        this.UICalculatorWindow.UICalculatorDialog;  
    WinEdit uIItemEdit =   
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;  
    #endregion  
  
    // Type '{NumPad7}' in 'Calculator' Dialog  
    Keyboard.SendKeys(uICalculatorDialog,   
        this.AddItemsParams.UICalculatorDialogSendKeys,   
        ModifierKeys.None);  
  
    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    Keyboard.SendKeys(uIItemEdit,   
        this.AddItemsParams.UIItemEditSendKeys,   
        ModifierKeys.None);  
}  
```  
  
 Bu yöntem için parametre değerleri için kullanmak için hangi sınıfın her bir yöntemin tanımı için Özet açıklama söyler. Bu durumda `AddItemsParams` daha sonra tanımlanmış sınıf `UIMap.cs` dosya ve aynı zamanda tarafından döndürülen değer türü olan `AddItemsParams` özelliği.  
  
 Yöntemin en üstündeki kodu bir `Variable Declarations` yerel değişkenler için kullanıcı arabirimini tanımlar bölge nesneleri yöntemi tarafından kullanılır.  
  
 Bu yöntemde, her ikisi de `UIItemWindow` ve `UIItemEdit` kullanılarak erişilen özellikleri `UICalculatorWindow` daha sonra tanımlanmış sınıf `UIMap.cs` dosya.  
  
 Sonraki hesaplayıcı uygulamaya klavyeden özelliklerini kullanarak metin gönderen satırla `AddItemsParams` nesne.  
  
 `VerifyTotal()` Yöntemi çok benzer yapıya sahip ve aşağıdaki onay kodunu içerir.  
  
```  
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '  
Assert.AreEqual(  
    this.VerifyTotalExpectedValues.UIItemEditText,   
    uIItemEdit.Text);  
```  
  
 Windows hesap makinesi uygulama geliştiricisine genel kullanıma açık bir denetimin adı sağlamadığından, metin kutusu adı bilinmiyor olarak listelenir. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> Gerçek değeri testin başarısız olmasına neden olduğu beklenen değer için eşit olmadığı durumlarda yöntemi başarısız olur. Ayrıca, beklenen değerle ardından bir boşluk bir ondalık noktası içerdiğine dikkat edin. Bu belirli test işlevlerini değiştirmek amacıyla varsa, ondalık ve boşluğa izin vermeniz gerekir.  
  
#####  <a name="UIMapProperties"></a> UIMap özellikleri  
 Her bir özellik için kod da sınıfı çok standarttır. Aşağıdaki kod için `AddItemsParams` özelliği kullanılan `AddItems()` yöntemi.  
  
```  
public virtual AddItemsParams AddItemsParams  
{  
    get  
    {  
        if ((this.mAddItemsParams == null))  
        {  
            this.mAddItemsParams = new AddItemsParams();  
        }  
        return this.mAddItemsParams;  
    }  
}  
```  
  
 Özellik adında özel bir yerel değişken kullandığını bildirimi `mAddItemsParams` döndürmeden önce değerini tutacak. Özellik adı ve sınıf adını döndürür nesne için aynıdır. Sınıf daha sonra tanımlanır `UIMap.cs` dosya.  
  
 Bir özellik tarafından döndürülen her sınıf benzer şekilde yapılandırılmıştır. Aşağıdaki `AddItemsParams` sınıfı.  
  
```  
/// <summary>  
/// Parameters to be passed into 'AddItems'  
/// </summary>  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public class AddItemsParams  
{  
    #region Fields  
    /// <summary>  
    /// Type '{NumPad7}' in 'Calculator' Dialog  
    /// </summary>  
    public string UICalculatorDialogSendKeys = "{NumPad7}";  
  
    /// <summary>  
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    /// </summary>  
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";  
    #endregion  
}  
```  
  
 İçindeki tüm sınıflar ile `UIMap.cs` dosya, bu sınıf ile başlayan <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. Bu küçük bir sınıf içinde bir `Fields` parametreleri olarak kullanılmak üzere dize tanımlayan bölge <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> kullanılır yöntemi `UIMap.AddItems()` daha önce bahsedilen yöntemi. Bu parametreleri kullanılan yöntemi çağrılmadan önce bu dize alanları değiştirmek için kod yazabilirsiniz.  
  
###  <a name="UIMapCS"></a> UIMap.cs  
 Varsayılan olarak, bu dosya bir kısmi içerir `UIMap` yöntemleri veya özellikleri olmayan sınıf.  
  
#### <a name="uimap-class"></a>UIMap sınıfı  
 İşlevlerini genişletmek için özel kod oluşturabileceğiniz budur <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> sınıfı. Bu dosyada oluşturduğunuz kod tarafından oluşturulacak değil **kodlanmış UI Test Oluşturucusu** test değiştirilir her zaman.  
  
 Tüm parçaları <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> yöntemleri ve özellikleri, herhangi bir bölümünü kullanabilir <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> sınıfı.  
  
###  <a name="CodedUITestCS"></a> Codeduıtest1.cs  
 Bu dosya tarafından oluşturulan **kodlanmış UI Test Oluşturucusu**, ancak bu dosyadaki kodu değiştirebilmeniz test değiştirilir, her seferinde yeniden oluşturulmaz. Dosyanın adı oluşturduğunuzda test için belirttiğiniz adından oluşturulur.  
  
#### <a name="codeduitest1-class"></a>Codeduıtest1 sınıfı  
 Varsayılan olarak, bu dosya, yalnızca bir sınıf tanımı içerir.  
  
```  
[CodedUITest]  
public class CodedUITest1  
```  
  
 T:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute öğesi bir test uzantısı olarak tanınması test çerçevesi sağlar sınıfını otomatik olarak uygulanır. Ayrıca bu kısmi bir sınıf olmadığına dikkat edin. Tüm sınıf kodu bu dosyada yer alır.  
  
#####  <a name="CodedUITestProperties"></a> Codeduıtest1 özellikleri  
 Sınıfı dosyanın sonunda bulunan iki varsayılan özellikleri içerir. Bunlar değiştirilmemelidir.  
  
```  
/// <summary>  
/// Gets or sets the test context which provides  
/// information about and functionality for the current test run.  
///</summary>  
public TestContext TestContext  
public UIMap UIMap  
```  
  
#####  <a name="CodedUITestMethods"></a> Codeduıtest1 yöntemleri  
 Varsayılan olarak, yalnızca bir yöntem sınıfı içerir.  
  
```  
public void CodedUITestMethod1()  
```  
  
 Bu yöntem her çağırır `UIMap` bölümünde açıklanır testinizi kaydettiğiniz zaman belirttiğiniz yöntemi [UIMap sınıfı](#UIMapClass).  
  
 Adlandırılmış bir bölge `Additional test attributes`, kaldırılmamışsa, iki isteğe bağlı yöntemler içerir.  
  
```  
// Use TestInitialize to run code before running each test   
[TestInitialize()]  
public void MyTestInitialize()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.LaunchCalculator();  
}  
  
// Use TestCleanup to run code after each test has run  
[TestCleanup()]  
public void MyTestCleanup()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.CloseCalculator();  
}  
```  
  
 `MyTestInitialize()` Yöntemi olan <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> , uygulanan herhangi bir test yöntemleri önce bu yöntemi çağırmak için test çerçevesi söyler. Benzer şekilde, `MyTestCleanup()` yöntemi olan <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> uygulanmış, bu yöntem tüm diğer test yöntemlerini çağırmak için test çerçevesi söyleyen çağrıldı. Bu yöntemlerin kullanım isteğe bağlıdır. Bu test için `UIMap.LaunchCalculator()` yöntemi konumundan çağrılabilir `MyTestInitialize()` ve `UIMap.CloseCalculator()` yöntemi konumundan çağrılabilir `MyTestCleanup()` yerine gelen `CodedUITest1Method1()`.  
  
 Kullanarak daha fazla yöntem bu sınıfa eklerseniz <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>, test çerçevesi testin bir parçası her bir yöntemi çağırır.  
  
###  <a name="UIMapuitest"></a> UIMap.uitest  
 Bir XML dosyası temsil kaydı yapısı, kodlanmış UI testi ve tüm bölümleri budur. Bunlar, eylemleri ve sınıfları yöntemleri ve söz konusu sınıfın özelliklerine ek olarak içerir. [UIMap.Designer.cs](#UIMapDesignerFile) dosyası kodlanmış UI test yapısı oluşturmaya oluşturucusu tarafından oluşturulur ve test çerçevesi bağlantı sağlayan kodunu içerir.  
  
 `UIMap.uitest` Dosyası doğrudan düzenlenebilir değil. Ancak, otomatik olarak değiştirir testi değiştirmek için kodlanmış UI Oluşturucusu kullanabilirsiniz `UIMap.uitest` dosya ve [UIMap.Designer.cs](#UIMapDesignerFile) dosya.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>   
 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>   
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)   
 [Birden çok UI eşlemesi bulunan büyük uygulamaları sınama](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



