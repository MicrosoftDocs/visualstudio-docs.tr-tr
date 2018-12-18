---
title: Testi birden çok UI eşlemesi bulunan büyük uygulamaları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dfc1cf44cb92ab58b50284f0398178c8f96f2a2e
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895138"
---
# <a name="test-a-large-application-with-multiple-ui-maps"></a>Birden çok UI eşlemesi bulunan büyük uygulamaları test etme

Bu konu, birden çok UI Haritası'nı kullanarak büyük bir uygulamayı test ettiğinizde, kodlanmış UI testleri kullanma işlemini açıklar.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise

Yeni kodlanmış UI testi oluşturduğunuzda, Visual Studio test çerçevesi varsayılan olarak testi için kod oluşturur bir <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> sınıfı. Kodlanmış UI testleri nasıl kaydedileceği hakkında daha fazla bilgi için bkz: [Oluştur kodlanmış UI testleri](../test/use-ui-automation-to-test-your-code.md) ve [kodlanmış UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md).

Oluşturulan kod için UI haritasında test ile etkileşime giren her nesne için bir sınıf içerir. Oluşturulan her bir yöntemi için Yöntem parametreleri için bir yardımcı sınıfı için özel olarak bu yöntem oluşturulur. UI haritasında, nesneleri, sayfalar ve formları ve denetimleri, uygulamanızda çok sayıda varsa, çok fazla büyüyebilir. Ayrıca, birkaç kişiye testleri üzerinde çalışıyorsanız ve o uygulama tek bir büyük UI haritası dosyasıyla hantal hale gelir.

Birden çok UI haritası dosyalarını kullanarak, aşağıdaki faydaları sağlayabilir:

- Her harita bir mantıksal uygulama alt kümesi ile ilişkili olabilir. Bu değişiklikleri yönetmeyi kolaylaştırır.

- Her test uygulamasının bir bölüm çalışabilir ve uygulamanın diğer bölümlerini üzerinde çalışan test edicileri ile engellemeden kodları denetleyin.

- Uygulama kullanıcı Arabirimi eklemeler, artımlı olarak arabiriminin diğer bölümleri için testleri üzerinde çok az etkisi olan ölçeklendirilebilir.

## <a name="do-you-need-multiple-ui-maps"></a>Birden çok UI haritası gerekiyor mu?
 Birden çok UI haritası, bu tür durumlarda her oluşturun:

-   Birlikte bir Web sitesinde bir kayıt sayfasına veya bir alışveriş sepeti satın alma sayfası gibi bir mantıksal işlemi gerçekleştiren bileşik UI denetimlerinin birçok karmaşık ayarlar.

-   Bağımsız bir uygulama işlemlerinin birden çok sayfa içeren bir sihirbaz gibi çeşitli noktalarından erişim denetimleri ayarlayın. Bir sihirbazın her sayfasındaki özellikle karmaşık ise, her sayfa için ayrı UI haritası oluşturabilirsiniz.

## <a name="add-multiple-ui-maps"></a>Birden çok UI Eşlemesi Ekle

### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>UI haritasında, kodlanmış UI test projesi eklemek için

1. İçinde **Çözüm Gezgini**UI haritası depolamak, kodlanmış UI testi proje dosyasını sağ tıklayın, fareyle için kodlanmış UI test projesi içinde bir klasör oluşturmak için **Ekle**ve ardından **Yeniklasör**. Örneğin, adlandırabilirsiniz `UIMaps`.

    Yeni klasör, kodlanmış UI test projesi altında görüntülenir.

2. Sağ `UIMaps` klasörünü **Ekle**ve ardından **yeni öğe**.

    **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

   > [!NOTE]
   > Yeni bir kodlanmış UI testi Haritası eklemek için kodlanmış UI test projesi içinde olmalıdır.

3. Seçin **kodlanmış UI testi Haritası** listeden.

    İçinde **adı** kutusunda, yeni UI eşlemesi için bir ad girin. Bileşen veya eşleme, örneğin, temsil edecek bir sayfa adını kullanmak `HomePageMap`.

4. Seçin **ekleme**.

    Visual Studio penceresi simge durumuna küçültür ve **kodlanmış UI Test Oluşturucusu** iletişim kutusu görüntülenir.

5. İlk yöntem için eylemlerini kaydedin ve seçin **kod üret**.

6. Kayıtlı tüm eylem ve ilk bileşen veya sayfa için onaylar ve yöntemlere gruplanmış sonra kapatın **kodlanmış UI Test Oluşturucusu** iletişim kutusu.

7. UI haritası oluşturmaya devam edin. Eylemler ve Onaylamalar kaydedin, her bileşen için yöntemlerde gruplamak ve ardından kodu oluşturun.

   Çoğu durumda, uygulamanızın en üst düzey penceresi tüm sihirbazları, formlar ve sayfalar için sabittir. Üst düzey bir pencere için bir sınıf her UI eşlemesine sahip olsa da, tüm eşlemeler büyük olasılıkla çalıştırın, uygulamanızın tüm bileşenlerin aynı üst düzey pencereye başvuruyordur. Üst düzey penceresinden başlayarak kodlanmış UI testleri arama denetimlerin hiyerarşik olarak yukarıdan aşağıya doğru böylece her UI haritasında gerçek üst düzey bir pencere karmaşık bir uygulamada yinelenen. Gerçek üst düzey bir pencere yineleniyorsa, o pencereyi değişirse, birden fazla değişiklik neden olur. UI haritası arasında geçiş yaptığınızda bu performans sorunlarına neden olabilir.

   Bu etkiyi en aza indirmek için kullanabileceğiniz `CopyFrom()` yöntemi üst düzey yeni pencerede, UI haritasını ana üst düzey pencere aynı olduğundan emin olun.

## <a name="example"></a>Örnek

Aşağıdaki örnek, her bileşen ve çeşitli kullanıcı Arabirimi haritaları'nda oluşturulan sınıflar tarafından temsil edilen alt denetimlerini erişim sağlayan bir yardımcı program sınıfı bir parçasıdır.

Bu örnekte, bir web uygulaması adlı `Contoso` giriş sayfası, bir ürün sayfası ve bir alışveriş sepeti sayfası vardır. Bu sayfaların her biri, tarayıcı penceresi ortak bir üst düzey pencere paylaşır. UI haritasında her sayfa için yoktur ve aşağıdakine benzer bir kod yardımcı program sınıfı vardır:

```csharp
using ContosoProject.UIMaps;
using ContosoProject.UIMaps.HomePageClasses;
using ContosoProject.UIMaps.ProductPageClasses;
using ContosoProject.UIMaps.ShoppingCartClasses;

namespace ContosoProject
{
    public class TestRunUtility
    {
        // Private fields for the properties
        private HomePage homePage = null;
        private ProductPage productPage = null;
        private ShoppingCart shoppingCart = null;

        public TestRunUtility()
        {
            homePage = new HomePage();
        }

        // Properties that get each UI Map
        public HomePage HomePage
        {
            get { return homePage; }
            set { homePage = value; }
        }

        // Gets the ProductPage from the ProductPageMap.
        public ProductPage ProductPageObject
        {
            get
            {
                if (productPage == null)
                {
                    // Instantiate a new page from the UI Map classes
                    productPage = new ProductPage();

                    // Since the Product Page and Home Page both use
                    // the same browser page as the top level window,
                    // get the top level window properties from the
                    // Home Page.
                    productPage.UIContosoFinalizeWindow.CopyFrom(
                        HomePage.UIContosoWindowsIWindow);
                }
                return productPage;
            }
        }

    // Continue to create properties for each page, getting the
    // page object from the corresponding UI Map and copying the
    // top level window properties from the Home Page.
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)
