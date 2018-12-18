---
title: Etkinleştirme kodlanmış UI denetimlerinizin | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 24
ms.author: gewarren
manager: douge
ms.openlocfilehash: e5ab2ca3e0f7d8f7006177f89c6850ce9882681a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848546"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Denetimlerinizin Kodlanmış UI Testlerini Etkinleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI test çerçevesi için destek uygularsanız, denetim daha kolay test edilebilir. Artımlı olarak artan destek düzeyleri ekleyebilirsiniz. Kayıt ve kayıttan yürütme ve özellik doğrulama destekleyerek başlayabilirsiniz. Bu denetimin özel özellikler tanımak kodlanmış UI test Oluşturucusu izin verecek şekilde derleyebilir ve üretilen koddan özelliklere erişmek için özel sınıflar sağlar. Ayrıca, kodlanmış UI test Oluşturucusu'nu yakalama eylemlerini kaydedilen eylem amacı yakın bir şekilde yardımcı olabilir.  
  
 **Bu konuda:**  
  
1. [Erişilebilirlik uygulayarak kaydı ve kayıttan yürütme ve doğrulama özelliği desteği](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)  
  
2. [Bir özellik sağlayıcısı uygulayarak özel özellik doğrulama desteği](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)  
  
3. [Özel özelliklere erişmek için bir sınıf uygulayarak kod oluşturma desteği](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)  
  
4. [Bir eyleme eylem filtresi uygulayarak amaç duyarlı Eylemler desteği](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)  
  
   ![CUIT&#95;tam](../test/media/cuit-full.png "CUIT_Full")  
  
##  <a name="recordandplayback"></a> Erişilebilirlik uygulayarak kaydı ve kayıttan yürütme ve doğrulama özelliği desteği  
 Kodlanmış UI test oluşturucusu, kayıt sırasında karşılaştığı ve ardından bu oturumu yeniden Yürüt için kod oluşturur denetimleri hakkında bilgi yakalar. Denetiminiz erişilebilirlik desteklemiyorsa, kodlanmış UI test Oluşturucusu kullanarak ekran koordinatları (fare tıklamaları gibi) eylemleri yakalayın. Test yürütüldüğünde, oluşturulan kod bu fare tıklamaları aynı ekran koordinatlarında verecek. Test yürütüldüğünde denetim ekranda farklı bir yerde görünür, oluşturulan kod denetiminizi bu eylemi gerçekleştirmek başarısız olur. Test farklı ortamlarda veya kullanıcı Arabirimi düzeninde değişiklikler yapıldı sonra farklı bir ekrana yapılandırmada kayıttan yürütülebilir bu hatalarına neden olabilir.  
  
 ![CUIT&#95;RecordNoSupport](../test/media/cuit-recordnosupport.png "CUIT_RecordNoSupport")  
  
 Erişilebilirlik uygularsanız, ancak, kodlanmış UI test Oluşturucusu olan bir test kaydeder ve kod oluşturur, denetimi ile ilgili bilgileri yakalamak için kullanır. Ardından, test çalıştırdığınızda, kullanıcı arabiriminde başka bir yerde olsa bile, oluşturulan kod bu olaylara karşı denetiminiz tekrarlar. Test yazarları ayrıca oluşturabileceksiniz oluşturma denetiminiz temel özelliklerini kullanarak sağlayın.  
  
 ![CUIT&#95;kayıt](../test/media/cuit-record.png "CUIT_Record")  
  
### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Bir Windows Forms denetiminin kaydı ve kayıttan yürütme özelliği doğrulama ve gezinti desteklemek için  
 Aşağıdaki yordamda belirtildiği gibi denetiminiz için erişilebilirlik uygulamak ve ayrıntılı olarak açıklandığı <xref:System.Windows.Forms.AccessibleObject>.  
  
 ![CUIT&#95;erişilebilir](../test/media/cuit-accessible.png "CUIT_Accessible")  
  
1.  Türetilen bir sınıf uygulamak <xref:System.Windows.Forms.Control.ControlAccessibleObject>ve geçersiz kılma <xref:System.Windows.Forms.Control.AccessibilityObject%2A> sınıfınızın bir nesneyi döndürmek için özellik.  
  
    ```csharp  
    public partial class ChartControl : UserControl  
    {  
        // Overridden to return the custom AccessibleObject for the control.  
        protected override AccessibleObject CreateAccessibilityInstance()  
        {  
            return new ChartControlAccessibleObject(this);  
        }  
  
        // Inner class ChartControlAccessibleObject represents accessible information  
        // associated with the ChartControl and is used when recording tests.  
        public class ChartControlAccessibleObject : ControlAccessibleObject  
        {  
            ChartControl myControl;  
            public ChartControlAccessibleObject(ChartControl ctrl)  
                : base(ctrl)  
            {  
                myControl = ctrl;  
            }  
        }  
    }  
    ```  
  
2.  Erişilebilir nesnenin geçersiz kılma <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> ve <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> özellikleri ve yöntemleri.  
  
3.  Başka bir alt denetimin erişilebilirlik nesne uygulamak ve alt denetimin geçersiz kılma <xref:System.Windows.Forms.Control.AccessibilityObject%2A> bu erişilebilirlik nesneyi döndürmek için özellik.  
  
4.  Geçersiz kılma <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, ve <xref:System.Windows.Forms.AccessibleObject.Select%2A> alt denetimin erişilebilirlik nesne için özellikleri ve yöntemleri.  
  
> [!NOTE]
>  Bu konuda erişilebilirlik örnek başlayan <xref:System.Windows.Forms.AccessibleObject> Bu yordam ve ardından yapılarında kalan yordamları, şirket içinde. Erişilebilirlik örnek çalışan sürümü oluşturmak istiyorsanız, bir konsol uygulaması oluşturun ve ardından program.cs'deki kodu örnek kod ile değiştirin. Erişilebilirlik ve System.Drawing System.Windows.Forms başvurular eklemeniz gerekir. Değiştirmeniz **birlikte çalışma türlerini katıştır** erişilebilirlik için **False** bir yapı uyarısı ortadan kaldırmak için. Projenin çıktı türünden için değiştirebileceğiniz **konsol uygulaması** için **Windows uygulama** böylece bir konsol penceresi görünmez çalıştırdığınızda uygulama.  
  
##  <a name="customproprties"></a> Bir özellik sağlayıcısı uygulayarak özel özellik doğrulama desteği  
 Kayıt ve kayıttan yürütme ve özelliği doğrulama için temel destek uyguladık sonra denetiminizin özel özellikler kodlanmış UI testleri kullanılabilir uygulayarak yapabileceğiniz bir <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> eklenti. Örneğin, aşağıdaki yordam grafik denetiminin CurveLegend alt denetimlerin durumu özelliğine erişmek kodlanmış UI testleri sağlayan bir özellik sağlayıcısı oluşturur.  
  
 ![CUIT&#95;CustomProps](../test/media/cuit-customprops.png "CUIT_CustomProps")  
  
### <a name="to-support-custom-property-validation"></a>Özel özellik doğrulamasını desteklemek için  
 ![CUIT&#95;Özellikler](../test/media/cuit-props.png "CUIT_Props")  
  
1.  Eğri gösterge erişilebilir nesnenin geçersiz kılma <xref:System.Windows.Forms.AccessibleObject.Description%2A> özellik açıklama dizesi içinde zengin özellik değerlerini geçirmek için noktalı virgülle (;) ana açıklaması (ve diğer birden çok özellik uyguluyorsanız,) ayrılmış.  
  
    ```csharp  
    public class CurveLegendAccessibleObject : AccessibleObject  
    {  
        // add the state property value to the description  
        public override string Description  
        {  
            get  
            {  
                // Add “;” and the state value to the end  
                // of the curve legend’s description  
                return "CurveLegend; " + State.ToString();  
            }  
        }  
    }  
    ```  
  
2.  Bir sınıf kitaplığı projesi oluşturarak denetiminiz için bir UI testi uzantısı paketi oluşturma ve erişilebilirlik, Microsoft.VisualStudio.TestTools.UITesting Microsoft.VisualStudio.TestTools.UITest.Common, başvuruları ekleyin ve Microsoft.VisualStudio.TestTools.Extension. Değişiklik **birlikte çalışma türlerini katıştır** erişilebilirlik için **False**.  
  
3.  Türetilen bir özellik sağlayıcısı sınıfı Ekle <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using Accessibility;  
    using Microsoft.VisualStudio.TestTools.UITesting;  
    using Microsoft.VisualStudio.TestTools.UITest.Extension;  
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
    using Microsoft.VisualStudio.TestTools.UITest.Common;  
  
    namespace ChartControlExtensionPackage  
    {  
        public class ChartControlPropertyProvider : UITestPropertyProvider  
        {  
        }  
    }  
    ```  
  
4.  Özellik adlarını ve özellik tanımlayıcılar yerleştirerek özellik sağlayıcısı uygulayan bir <xref:System.Collections.Generic.Dictionary%602>.  
  
    ```csharp  
    // Define a map of property descriptors for CurveLegend  
    private static Dictionary<string, UITestPropertyDescriptor> curveLegendPropertiesMap = null;  
    private static Dictionary<string, UITestPropertyDescriptor> CurveLegendPropertiesMap  
    {  
        get  
        {  
            if (curveLegendPropertiesMap == null)  
            {  
                UITestPropertyAttributes read =  
                    UITestPropertyAttributes.Readable |  
                    UITestPropertyAttributes.DoNotGenerateProperties;  
                curveLegendPropertiesMap =  
                    new Dictionary<string, UITestPropertyDescriptor>  
                        (StringComparer.OrdinalIgnoreCase);  
                curveLegendPropertiesMap.Add("State",  
                    new UITestPropertyDescriptor(typeof(string), read));  
            }  
            return curveLegendPropertiesMap;  
        }  
    }  
  
    // return the property descriptor  
    public override UITestPropertyDescriptor GetPropertyDescriptor(UITestControl uiTestControl, string propertyName)  
    {  
        return CurveLegendPropertiesMap[propertyName];  
    }  
  
    // return the property names  
    public override ICollection<string> GetPropertyNames(UITestControl uiTestControl)  
    {  
        if (uiTestControl.ControlType.NameEquals("Chart") || uiTestControl.ControlType.NameEquals("Text"))  
        {  
            // the keys of the property map are the collection of property names  
            return CurveLegendPropertiesMap.Keys;  
        }  
  
        // this is not my control  
        throw new NotSupportedException();  
    }  
  
    // Get the property value by parsing the accessible description  
    public override object GetPropertyValue(UITestControl uiTestControl, string propertyName)  
    {  
        if (String.Equals(propertyName, "State", StringComparison.OrdinalIgnoreCase))  
        {  
            object[] native = uiTestControl.NativeElement as object[];  
            IAccessible acc = native[0] as IAccessible;  
  
            string[] descriptionTokens = acc.accDescription.Split(new char[] { ';' });  
            return descriptionTokens[1];  
        }  
  
        // this is not my control  
        throw new NotSupportedException();  
    }  
    ```  
  
5.  Geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> belirten derlemenizi denetiminizi ve alt öğeleri için özel denetim desteği sağlar.  
  
    ```csharp  
    public override int GetControlSupportLevel(UITestControl uiTestControl)  
    {  
        // For MSAA, check the control type  
        if (string.Equals(uiTestControl.TechnologyName, "MSAA",  
            StringComparison.OrdinalIgnoreCase) &&  
            (uiTestControl.ControlType == "Chart"||uiTestControl.ControlType == "Text"))  
        {  
            return (int)ControlSupport.ControlSpecificSupport;  
        }  
  
        // This is not my control, so return NoSupport  
        return (int)ControlSupport.NoSupport;  
    }  
    ```  
  
6.  Kalan soyut yöntemlerini geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.  
  
    ```csharp  
    public override string[] GetPredefinedSearchProperties(Type specializedClass)  
    {  
        throw new NotImplementedException();  
    }  
  
    public override Type GetSpecializedClass(UITestControl uiTestControl)  
    {  
        throw new NotImplementedException();  
    }  
  
    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)  
    {  
        throw new NotImplementedException();  
    }  
  
    public override void SetPropertyValue(UITestControl uiTestControl, string propertyName, object value)  
    {  
        throw new NotImplementedException();  
    }  
  
    public override string GetPropertyForAction(UITestControl uiTestControl, UITestAction action)  
    {  
        throw new NotImplementedException();  
    }  
  
    public override string[] GetPropertyForControlState(UITestControl uiTestControl, ControlStates uiState, out bool[] stateValues)  
    {  
        throw new NotImplementedException();  
    }  
  
    ```  
  
7.  Türetilen bir uzantı paketi sınıfı ekleyin <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
    ```csharp  
    using System;  
    using Microsoft.VisualStudio.TestTools.UITesting;  
    using Microsoft.VisualStudio.TestTools.UITest.Extension;  
    using Microsoft.VisualStudio.TestTools.UITest.Common;  
  
    namespace ChartControlExtensionPackage  
    {  
        internal class ChartControlExtensionPackage : UITestExtensionPackage  
        {  
        }  
    }  
    ```  
  
8.  Tanımlama `UITestExtensionPackage` derleme için özniteliği.  
  
    ```csharp  
    [assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
                    "ChartControlExtensionPackage",  
                    typeof(ChartControlExtensionPackage.ChartControlExtensionPackage))]  
    namespace ChartControlExtensionPackage  
    {  
       …  
    ```  
  
9. Uzantı paketi sınıfta geçersiz <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> özellik sağlayıcısı sınıfı bir özellik sağlayıcısı istendiğinde döndürmek için.  
  
    ```csharp  
    internal class ChartControlExtensionPackage : UITestExtensionPackage  
    {  
        public override object GetService(Type serviceType)  
        {  
            if (serviceType == typeof(UITestPropertyProvider))  
            {  
                if (propertyProvider == null)  
                {  
                    propertyProvider = new ChartControlPropertyProvider();  
                }  
                return propertyProvider;  
            }  
            return null;  
        }  
  
        private UITestPropertyProvider propertyProvider = null;  
    }  
    ```  
  
10. Kalan soyut yöntemlerini ve özelliklerini geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
    ```csharp  
  
    public override void Dispose() { }  
  
    public override string PackageDescription  
    {  
        get { return "Supports coded UI testing of ChartControl"; }  
    }  
  
    public override string PackageName  
    {  
        get { return "ChartControl Test Extension"; }  
    }  
  
    public override string PackageVendor  
    {  
        get { return "Microsoft (sample)"; }  
    }  
  
    public override Version PackageVersion  
    {  
        get { return new Version(1, 0); }  
    }  
  
    public override Version VSVersion  
    {  
        get { return new Version(10, 0); }  
    }  
    ```  
  
11. İkili dosyalarınızı oluşturmak ve kopyalamak için **%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.  
  
> [!NOTE]
>  Bu uzantı paketi "Metin" türünde herhangi bir denetimi için geçerlidir. Aynı türden birden çok denetim test ediyorsanız bunları ayrı ayrı test edin ve hangi uzantı paketleri testleri kaydettiğinizde dağıtılan yönetmek gerekir.  
  
##  <a name="codegeneration"></a> Özel özelliklere erişmek için bir sınıf uygulayarak kod oluşturma desteği  
 Kodlanmış UI test Oluşturucusu'nu oturumu kaydından kodu oluşturduğunda, kullandığı <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> denetimlerinizi erişmek için sınıf.  
  
```csharp  
  
      UITestControl uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;  
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.GetProperty("State").ToString());  
```  
  
 Denetimin özel özellikler erişim sağlamak için bir özellik sağlayıcısı uyguladık. böylece oluşturulan kodun Basitleştirilmiş özelliklere erişmek için kullanılan özel bir sınıf ekleyebilirsiniz.  
  
```csharp  
  
      ControlLegend uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;  
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.State);  
```  
  
### <a name="to-add-a-specialized-class-to-access-your-control"></a>Denetiminiz erişmek için özel bir sınıf eklemek için  
 ![CUIT&#95;CodeGen](../test/media/cuit-codegen.png "CUIT_CodeGen")  
  
1.  Türetilen bir sınıf uygulamak <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> ve arama özellikleri koleksiyona Oluşturucusu denetimin türü ekleyin.  
  
    ```csharp  
    public class CurveLegend:WinControl   
    {  
       public CurveLegend(UITestControl c) : base(c)   
       {  
          // The curve legend control is a “text” type of control  
          SearchProperties.Add(  
             UITestControl.PropertyNames.ControlType, "Text");  
       }  
    }  
    ```  
  
2.  Denetimin özel özellikler, sınıf özelliklerini uygulayın.  
  
    ```csharp  
    public virtual string State  
    {  
        get  
        {  
            return (string)GetProperty("State");  
        }  
    }  
    ```  
  
3.  Geçersiz kılma özelliği sağlayıcınızın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> gösterge alt denetimleri eğrinin için yeni bir sınıf türü döndürmek için yöntemi.  
  
    ```csharp  
    public override Type GetSpecializedClass(UITestControl uiTestControl)   
    {   
       if (uiTestControl.ControlType.NameEquals("Text"))   
       {   
          // This is text type of control. For my control,  
          // that means it’s a curve legend control.  
          return typeof(CurveLegend);   
       }   
  
       // this is not a curve legend control  
       return null;  
    }  
    ```  
  
4.  Geçersiz kılma özelliği sağlayıcınızın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> yeni sınıf PropertyNames yöntemi türü döndürmek için yöntemi.  
  
    ```csharp  
    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)  
    {  
        if (uiTestControl.ControlType.NameEquals("Text"))  
        {  
          // This is text type of control. For my control,  
          // that means it’s a curve legend control.  
            return typeof(CurveLegend.PropertyNames);  
        }  
  
        // this is not a curve legend control  
        return null;  
    }  
    ```  
  
##  <a name="intentawareactions"></a> Bir eyleme eylem filtresi uygulayarak amaç duyarlı Eylemler desteği  
 Visual Studio test düzenlediğinizde her fare ve klavye olay yakalar. Ancak, bazı durumlarda, fare ve klavye olaylarının serisinde eylemin amacı kaybedilebilir. Örneğin, otomatik tamamlama denetiminiz destekliyorsa, farklı bir ortamda test yürütüldüğünde fare ve klavye olaylarını aynı kümesini farklı bir değer sonuçlanabilir. Klavye ve fare olaylar dizisini tek bir eylem ile değiştiren bir eylem filtresi eklentisini ekleyebilirsiniz. Bu şekilde, bir değerin değeri ayarlar tek bir eylemle seçimdeki kaynaklanan fare ve klavye olaylarını dizi değiştirebilirsiniz. Böylece, kodlanmış UI testleri farklılıkları otomatik tamamlama bir ortamdan diğerine önler.  
  
### <a name="to-support-intent-aware-actions"></a>Amaç duyarlı Eylemler desteklemek için  
 ![CUIT&#95;eylemleri](../test/media/cuit-actions.png "CUIT_Actions")  
  
1.  Türetilen bir eylem filtresi sınıf uygulama <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, özelliklerini geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> ve <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.  
  
    ```csharp  
    internal class MyActionFilter : UITestActionFilter  
    {  
       // If the user actions we are aggregating exceeds the time allowed,  
       // this filter is not applied. (The timeout is configured when the  
       // test is run.)  
       public override bool ApplyTimeout  
       {  
          get { return true; }  
       }  
  
       // Gets the category of this filter. Categories of filters  
       // are applied in priority order.  
       public override UITestActionFilterCategory Category  
       {  
          get { return UITestActionFilterCategory.PostSimpleToCompoundActionConversion; }  
       }  
  
       public override bool Enabled  
       {  
          get { return true; }  
       }  
  
       public override UITestActionFilterType FilterType  
       {  
          // This action filter operates on a single action  
          get { return UITestActionFilterType.Unary; }  
       }  
  
       // Gets the name of the group to which this filter belongs.  
       // A group can be enabled/disabled using configuration file.  
       public override string Group  
       {  
          get { return "ChartControlActionFilters"; }  
       }  
  
       // Gets the name of this filter.  
       public override string Name  
       {  
          get { return "Convert Double-Click to Single-Click"; }  
       }  
    ```  
  
2.  Geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>. Örnek realpces bir çift tıklatma eylemi tek bir eylemi buraya tıklayın.  
  
    ```csharp  
    public override bool ProcessRule(IUITestActionStack actionStack)  
    {  
        if (actionStack.Count > 0)  
        {  
            MouseAction lastAction = actionStack.Peek() as MouseAction;  
            if (lastAction != null)  
            {  
                if (lastAction.UIElement.ControlTypeName.Equals(  
                     ControlType.Text.ToString(),  
                     StringComparison.OrdinalIgnoreCase))  
                {  
                    if(lastAction.ActionType == MouseActionType.DoubleClick)  
                    {  
                        // Convert to single click  
                        lastAction.ActionType = MouseActionType.Click;  
                    }  
                }  
            }  
        }  
        // Do not stop aggregation  
        return false;  
    }  
    ```  
  
3.  Eylem filtresine <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> uzantı paketinin yöntemi.  
  
    ```csharp  
    public override object GetService(Type serviceType)   
    {   
       if (serviceType == typeof(UITestPropertyProvider))   
       {   
          if (propertyProvider == null)  
          {  
             propertyProvider = new PropertyProvider();  
          }   
          return propertyProvider;  
       }   
       else if (serviceType == typeof(UITestActionFilter))   
       {   
          if (actionFilter == null)  
          {  
             actionFilter = new RadGridViewActionFilter();  
          }  
          return actionFilter;   
       }   
       return null;  
    }  
    ```  
  
4.  İkili dosyalarınızı oluşturun ve bunları %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages kopyalayın.  
  
> [!NOTE]
>  Eylem filtresi erişilebilirlik uygulamaları ya da özellik sağlayıcısı bağlı değildir.  
  
## <a name="debug-your-property-provider-or-action-filter"></a>Özellik sağlayıcısı veya eylem filtresi hata ayıklama  
 Özellik sağlayıcısı ve eylem filtresi, yüklenen ve uygulamanızdan ayrı bir işlemde kodlanmış UI test oluşturucusu tarafından çalıştırılan bir uzantı paketi uygulanır.  
  
#### <a name="to-debug-your-property-provider-or-action-filter"></a>Özellik sağlayıcısı veya eylem filtresi hata ayıklamak için  
  
1.  Uzantı paketi kopyanızı .dll hata ayıklama sürümünü ve %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages .pdb dosyalarını oluşturun.  
  
2.  Uygulamanızı (ayıklayıcıda değil) çalıştırın.  
  
3.  Kodlanmış UI test Oluşturucusu'nu çalıştırın.  
  
     `codedUITestBuilder.exe  /standalone`  
  
4.  Hata ayıklayıcı codedUITestBuilder işlemine iliştirin.  
  
5.  Kodunuzda kesme noktaları ayarlayın.  
  
6.  Kodlanmış UI test Oluşturucusu'nda oluşturma özelliğine sağlayıcınız çalışma ve eylem filtrelerinizi kullanmak için Eylemler kaydetmek için onaylar.  
  
## <a name="external-resources"></a>Dış kaynaklar  
  
### <a name="guidance"></a>Kılavuz  
 [Visual Studio 2012 – bölüm 2 ile sürekli teslimat testi: birim testi: iç testler](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.AccessibleObject>   
 [Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)



