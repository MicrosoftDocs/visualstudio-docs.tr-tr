---
title: Denetimlerinizin Kodlanmış UI Testlerini Etkinleştirme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b9f9256407f854e5e7eefbca0cdd767679b9c88c
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895957"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Kodlanmış UI denetimlerinizin etkinleştir

Denetiminizi daha test edilebilir hale getirmek framework kodlanmış UI testi için destek uygular. Artımlı olarak artan destek düzeyleri ekleyebilirsiniz. Kayıt ve kayıttan yürütme ve özellik doğrulama destekleyerek başlatın. Ardından, denetimin özel özellikler tanımak kodlanmış UI test Oluşturucusu etkinleştirmek için oluşturun. Üretilen koddan özelliklere erişmek için özel sınıflar sağlar. Ayrıca, kodlanmış UI test Oluşturucusu'nu yakalama eylemlerini kaydedilen eylem amacı yakın bir şekilde yardımcı olabilir.

![CUIT&#95;tam](../test/media/cuit_full.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Erişilebilirlik uygulayarak kaydı ve kayıttan yürütme ve özellik doğrulama desteği

Kodlanmış UI test oluşturucusu, kayıt sırasında karşılaştığı ve ardından bu oturumu yeniden Yürüt için kod oluşturur denetimleri hakkında bilgi yakalar. Denetiminiz erişilebilirlik desteklemiyorsa, kodlanmış UI test Oluşturucusu kullanarak ekran koordinatları (fare tıklamaları gibi) eylemleri yakalar. Test yürütüldüğünde, oluşturulan kod aynı ekran koordinatlarında eylemleri verir. Test yürütüldüğünde denetim ekranda farklı bir yerde görünür, oluşturulan kod eylemi gerçekleştirmek başarısız olur. Denetiminiz için erişilebilirlik uygulanmamasının görebileceğiniz test hataları test farklı ortamlarda farklı ekran yapılandırmada kayıttan yürütülebilir veya UI düzeni değiştiğinde.

 ![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png)

 Erişilebilirlik uygularsanız, kodlanmış UI test Oluşturucusu olan bir test düzenlediğinizde, denetimi ile ilgili bilgileri yakalamak için kullanır. Ardından, test çalıştırdığınızda, kullanıcı arabiriminde başka bir yerde olsa bile, oluşturulan kod bu olaylara karşı denetiminiz tekrarlar. Test yazarlar da oluşturabilir, denetim temel özelliklerini kullanarak sağlayın.

 ![CUIT&#95;kaydı](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Destek kaydı ve kayıttan yürütme ve bir Windows Forms denetimi için gezinme özelliği doğrulama
 Aşağıdaki yordamda belirtildiği gibi denetiminiz için erişilebilirlik uygulamak ve ayrıntılı olarak açıklandığı <xref:System.Windows.Forms.AccessibleObject>.

 ![CUIT&#95;erişilebilir](../test/media/cuit_accessible.png)

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

3.  Başka bir alt denetimin erişilebilirlik nesne uygulamak ve alt denetimin geçersiz kılma <xref:System.Windows.Forms.Control.AccessibilityObject%2A> erişilebilirlik nesneyi döndürmek için özellik.

4.  Geçersiz kılma <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, ve <xref:System.Windows.Forms.AccessibleObject.Select%2A> alt denetimin erişilebilirlik nesne için özellikleri ve yöntemleri.

> [!NOTE]
> Bu konuda erişilebilirlik örnek başlayan <xref:System.Windows.Forms.AccessibleObject>ve sonra kalan yordamlarda Bu örneği oluşturur. Erişilebilirlik örnek çalışan sürümü oluşturmak istiyorsanız, bir konsol uygulaması oluşturun ve ardından değiştirin *Program.cs* örnek kod ile. Erişilebilirlik ve System.Drawing System.Windows.Forms başvurular ekleyin. Değişiklik **birlikte çalışma türlerini katıştır** erişilebilirlik için **False** bir yapı uyarısı ortadan kaldırmak için. Projenin çıktı türünden değiştirebilirsiniz **konsol uygulaması** için **Windows uygulama** böylece bir konsol penceresi görünmez çalıştırdığınızda uygulama.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Bir özellik sağlayıcısı uygulayarak özel özellik doğrulama desteği

Kayıt ve kayıttan yürütme ve özelliği doğrulama için temel destek uyguladıktan sonra denetimin özel özellikler kodlanmış UI testleri kullanılabilir uygulayarak yapabileceğiniz bir <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> eklenti. Örneğin, aşağıdaki yordam grafik denetiminin CurveLegend alt denetimlerin durumu özelliğine erişmek kodlanmış UI testleri sağlayan bir özellik sağlayıcısı oluşturur:

 ![CUIT&#95;CustomProps](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Özel özellik doğrulamasını desteklemek için

![CUIT&#95;Özellikler](../test/media/cuit_props.png)

1. Eğri gösterge erişilebilir nesnenin geçersiz kılma <xref:System.Windows.Forms.AccessibleObject.Description%2A> zengin özellik değerlerini açıklama dizesine geçmenizi özelliği. Birden çok değer noktalı virgülle (;) ayırın.

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add ";" and the state value to the end
                // of the curve legend's description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

1. Bir sınıf kitaplığı projesi oluşturarak denetiminiz için bir UI testi uzantısı paketi oluşturun. Erişilebilirlik, Microsoft.VisualStudio.TestTools.UITesting Microsoft.VisualStudio.TestTools.UITest.Common ve Microsoft.VisualStudio.TestTools.Extension başvurular ekleyin. Değişiklik **birlikte çalışma türlerini katıştır** erişilebilirlik için **False**.

1. Türetilen bir özellik sağlayıcısı sınıfı Ekle <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>:

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

1. Özellik adlarını ve özellik tanımlayıcılar yerleştirerek özellik sağlayıcısı uygulayan bir <xref:System.Collections.Generic.Dictionary%602>.

1. Geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> belirten derlemenizi denetiminizi ve alt öğeleri için özel denetim desteği sağlar.

1. Kalan soyut yöntemlerini geçersiz kılar <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Türetilen bir uzantı paketi sınıfı ekleyin <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Tanımlama `UITestExtensionPackage` derleme için özniteliği.

1. Uzantı paketi sınıfta geçersiz <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> özellik sağlayıcısı sınıfı bir özellik sağlayıcısı istendiğinde döndürmek için.

1. Kalan soyut yöntemlerini ve özelliklerini geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. İkili dosyalarınızı oluşturmak ve kopyalamak için *%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Bu uzantı paketi, "Metin" türünde herhangi bir denetime uygulanır. Aynı türde birden çok denetim test ediyorsanız hangi uzantı paketleri testleri kaydettiğinizde dağıtılan yönetebilirsiniz bunları ayrı ayrı test edin.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Özel özelliklerine erişmek için bir sınıf uygulayarak kod oluşturma desteği

Kodlanmış UI test Oluşturucusu'nu oturumu kaydından kodu oluşturduğunda, kullandığı <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> denetimlerinizi erişmek için sınıf.

Denetimin özel özellikler erişim sağlamak için bir özellik sağlayıcısı uyguladık özelliklere erişmek için kullanılan özel bir sınıf ekleyebilirsiniz. Özel sınıf ekleme oluşturulan kodu basitleştirir.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Denetiminiz erişmek için özel bir sınıf eklemek için

![CUIT&#95;CodeGen](../test/media/cuit_codegen.png)

1. Türetilen bir sınıf uygulamak <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> ve arama özellikleri koleksiyona Oluşturucusu denetimin türü ekleyin.

1. Denetimin özel özellikler, sınıf özelliklerini uygulayın.

1. Geçersiz kılma özelliği sağlayıcınızın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> gösterge alt denetimleri eğrinin için yeni bir sınıf türü döndürmek için yöntemi.

1. Geçersiz kılma özelliği sağlayıcınızın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> yeni sınıf PropertyNames yöntemi türü döndürmek için yöntemi.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Bir eyleme eylem filtresi uygulayarak amaç duyarlı Eylemler desteği

 Visual Studio test düzenlediğinizde her fare ve klavye olay yakalar. Ancak, bazı durumlarda, fare ve klavye olaylarının serisinde eylemin amacı kaybedilebilir. Örneğin, otomatik tamamlama denetiminiz destekliyorsa, farklı bir ortamda test yürütüldüğünde fare ve klavye olaylarını aynı kümesini farklı bir değer sonuçlanabilir. Klavye ve fare olaylar dizisini tek bir eylem ile değiştiren bir eylem filtresi eklentisini ekleyebilirsiniz. Bu şekilde, bir dizi değeri ayarlar tek bir eylemle bir değer seçin fare ve klavye olayı değiştirebilirsiniz. Böylece, kodlanmış UI testleri farklılıkları otomatik tamamlama bir ortamdan diğerine önler.

### <a name="to-support-intent-aware-actions"></a>Amaç duyarlı Eylemler desteklemek için

![CUIT&#95;eylemleri](../test/media/cuit_actions.png)

1. Türetilen bir eylem filtresi sınıf uygulama <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, özelliklerini geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> ve <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.

1. Geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>. Örnek bir tek tıklama eylemi ile bir çift tıklatma eylemi değiştirir.

1. Eylem filtresine <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> uzantı paketinin yöntemi.

1. İkili dosyalarınızı oluşturmak ve kopyalamak için *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Eylem filtresi erişilebilirlik uygulamaları ya da özellik sağlayıcısı bağlı değildir.

## <a name="debug-your-property-provider-or-action-filter"></a>Hata ayıklama özellik sağlayıcısı veya eylem filtresi

Özellik sağlayıcısı ve eylem filtresi bir uzantısı paketinde uygulanır. Test Oluşturucusu'nu uzantı paketi, uygulamanızdan ayrı bir işlemde çalıştırır.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Özellik sağlayıcısı veya eylem filtresi hata ayıklamak için

1.  Uzantı paketi kopyanızı hata ayıklama sürümünü derlemek *.dll* ve *.pdb* dosyaları *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

2.  Uygulamanızı (ayıklayıcıda değil) çalıştırın.

3.  Kodlanmış UI test Oluşturucusu'nu çalıştırın.

     `codedUITestBuilder.exe  /standalone`

4.  Hata ayıklayıcı codedUITestBuilder işlemine iliştirin.

5.  Kodunuzda kesme noktaları ayarlayın.

6.  Kodlanmış UI test Oluşturucusu'nda oluşturma özelliğine sağlayıcınız çalışma ve eylem filtrelerinizi kullanmak için Eylemler kaydetmek için onaylar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.AccessibleObject>
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)