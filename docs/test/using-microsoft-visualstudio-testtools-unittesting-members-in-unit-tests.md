---
title: Birim Testlerinde Microsoft.VisualStudio.TestTools.UnitTesting Üyelerini Kullanma
ms.date: 03/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: bad6f01a49856e44120c0dc121ee262d9d26506c
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295611"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>MSTest framework birim testleri kullanın

[MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) framework Visual Studio'da birim testinin destekler. Sınıfları ve üyeleri kullanan <xref:Microsoft.VisualStudio.TestTools.UnitTesting> birim testlerini kod yazıyor olun, ad alanı. Koddan oluşturulan bir birim testi geliştirirken, ayrıca bunları kullanabilirsiniz.

## <a name="framework-members"></a>Framework üyeleri

Birim testi çerçevesi daha net bir genel bakış sağlamak için bu bölümde, üyelerinin düzenler <xref:Microsoft.VisualStudio.TestTools.UnitTesting> ilgili işlevleri gruplar halinde ad alanı.

> [!NOTE]
> Öznitelik öğeleri, adları "Özniteliği" ile bitemez, veya bilginiz olmaksızın "Özniteliği" son kullanılabilir. Örneğin, aşağıdaki iki kod örnekleri aynı şekilde işlev:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Veri tabanlı test için kullanılan üyeler

Veri temelli birim testleri ayarlamak için aşağıdaki öğeleri kullanın. Daha fazla bilgi için [veri temelli birim testi oluşturma](../test/how-to-create-a-data-driven-unit-test.md) ve [bir veri kaynağı tanımlamak için bir yapılandırma dosyası kullanın](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Çağıran bir sıralamayı oluşturmak için kullanılan öznitelikler

Aşağıdaki özniteliklerden birini ile donatılmış bir kod öğesi belirttiğiniz şu anda çağrılır. Daha fazla bilgi için [birim testinin anatomisi](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="attributes-for-assemblies"></a>Derlemeler için öznitelikler

Derlemenizi kaldırılmadan önce Assemblyınitialize ve AssemblyCleanup derlemenizi yüklendikten sonra sağ ve sağ verilir.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Öznitelikleri için sınıflar

Sınıfınıza kaldırılmadan önce Classınitialize ve ClassCleanup sınıfınıza yüklendikten sonra sağ ve sağ verilir.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Test yöntemleri için öznitelikler

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Test sınıfları ve yöntemleri tanımlamak için kullanılan öznitelikleri

Her test sınıfı olmalıdır `TestClass` özniteliği ve her test yönteminin olmalıdır `TestMethod` özniteliği. Daha fazla bilgi için [birim testinin anatomisi](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Sınıflar ve ilgili özel durum onaylama

Birim testleri, onaylar, özel durumlar ve öznitelikleri çeşitli kullanımları tarafından belirli bir uygulama davranışı doğrulayabilirsiniz. Daha fazla bilgi için [onay sınıfları kullanma](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>TestContext sınıfı

Aşağıdaki öznitelikler ve atanmış değerleri belirli test yöntemi için Visual Studio Özellikler penceresinde görünür. Bu öznitelikler, birim testinin kodu erişilebilir değildir. Bunun yerine, birim testi kullanılan veya IDE, Visual Studio aracılığıyla sizin tarafınızdan veya Visual Studio test altyapısı çalıştırma yolu etkiledikleri. Örneğin, bu öznitelikler bazı sütunlar halinde görünür **Test Yöneticisi** penceresi ve **Test sonuçları** bunları Grup ve sıralama testleri kullanın ve test sonuçları penceresi. Böyle bir öznitelik <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>, rastgele meta verileri için birim testleri eklemek için kullanın. Birim testi ile işaretleme tarafından bu test kapsayan bir test geçişi adını depolamak için örneğin, kullanabilirsiniz `[TestProperty("TestPass", "Accessibility")]`. Veya bir göstergesi olduğu ile test türünü depolamak için kullanabilirsiniz `[TestProperty("TestKind", "Localization")]`. Bu öznitelik, atama, özellik değerini kullanarak, oluşturduğunuz özelliği hem de görüntülenir Visual Studio'da **özellikleri** pencere başlığı altında **Test özel**.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Test yapılandırma sınıfları

- <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Raporlar üretmek için kullanılan öznitelikler

Bu bölümdeki öznitelikleri, Team Foundation Server takım projesinin proje hiyerarşisinde varlıklara süslemek test yöntemi ilgilidir.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Özel erişimciler ile kullanılan sınıflar

Birim testi için özel bir yöntem oluşturabilirsiniz. Bir nesnenin örneğini oluşturur, bir özel erişimci sınıfında, bu nesil oluşturur <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> sınıfı. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> Yansıma özel erişimci işleminin bir parçası kullanan bir sarmalayıcı sınıfı. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> Sınıfı benzer, ancak özel örnek yöntemleri çağırmak yerine özel statik yöntemleri çağırmak için kullanılır.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Başvuru belgeleri
