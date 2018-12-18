---
title: Using Microsoft.VisualStudio.TestTools.UnitTesting Members in Unit Tests | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 8
ms.author: gewarren
manager: douge
ms.openlocfilehash: 691b1e46f7657eb027fa48b31f31119cae0c7451
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216662"
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Birim Testlerinde Microsoft.VisualStudio.TestTools.UnitTesting Üyelerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Birim test, birim testi çerçevesi destekler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sınıfları ve üyeleri kullanan <xref:Microsoft.VisualStudio.TestTools.UnitTesting> birim testlerini kod yazıyor olun, ad alanı. Birim test ettiğiniz koddan oluşturulan bir birim testi iyileştirme veya sıfırdan test yazdığınızda, bunları kullanabilirsiniz.

## <a name="groups-of-elements"></a>Öğe grupları
 Birim testi çerçevesi daha net bir genel bakış sağlamak için bu bölümde UnitTesting ad öğelerini ilgili işlevlerin gruplar halinde düzenler.

> [!NOTE]
> Adları dize özniteliği sonlandırma, öznitelik öğeleri ile ya da dize özniteliği olmadan kullanılabilir. Örneğin, aşağıdaki iki kod örnekleri aynı şekilde işlev:
>
>  `[TestClass()]`
>
>  `[TestClassAttribute()]`

### <a name="elements-used-for-data-driven-testing"></a>Veri tabanlı test için kullanılan öğeleri
 Veri temelli birim testleri ayarlamak için aşağıdaki öğeleri kullanın. Daha fazla bilgi için [nasıl yapılır: veri temelli birim testi oluşturma](../test/how-to-create-a-data-driven-unit-test.md) ve [izlenecek yol: bir veri kaynağı tanımlamak için bir yapılandırma dosyası kullanarak](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Bir arama sıralamayı oluşturmak için kullanılan öznitelikler
 Aşağıdaki özniteliklerden birini ile donatılmış bir kod öğesi belirttiğiniz şu anda çağrılır. Daha fazla bilgi için [birim testinin anatomisi](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="for-assemblies"></a>Derlemeler için
 Derlemenizi kaldırılmadan önce Assemblyınitialize ve AssemblyCleanup derlemenizi yüklendikten sonra sağ ve sağ verilir.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="for-classes"></a>Sınıflar için
 Sınıfınıza kaldırılmadan önce Classınitialize ve ClassCleanup sınıfınıza yüklendikten sonra sağ ve sağ verilir.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="for-test-methods"></a>Test yöntemleri

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Test sınıfları ve yöntemleri tanımlamak için kullanılan öznitelikleri
 Her test sınıfı TestClass özniteliği olmalıdır ve her test yönteminin TestMethod özniteliği olmalıdır. Daha fazla bilgi için [birim testinin anatomisi](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Sınıflar ve ilgili özel durum onaylama
 Birim testleri tarafından onay deyimleri, özel durumlar ve öznitelikleri çeşitli kullanımları belirli uygulama davranışı doğrulayabilirsiniz. Daha fazla bilgi için [onay sınıfları](../test/using-the-assert-classes.md).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>TestContext sınıfı
 Aşağıdaki öznitelikler ve değerler atanmış görünür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] belirli test yöntemi için Özellikler penceresi. Bu öznitelikler, birim testinin kodu erişilebilir değildir. Çalıştırın, IDE'yi aracılığıyla sizin tarafınızdan veya birim testi kullanılan yolu etkiledikleri bunun yerine, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ya da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] test altyapısı. Örneğin, bazı bu öznitelikleri Test Yöneticisi ve bunları Grup ve sıralama testleri kullanın ve test sonuçları olan Test Sonuçları penceresinde sütunlar olarak görünür. Tek bir özniteliğe rastgele meta verileri için birim testleri eklemek için kullandığınız TestPropertyAttribute ' dir. Birim testi ile işaretleme tarafından bu test kapsayan bir test geçişi adını depolamak için örneğin, kullanabilirsiniz `[TestProperty("TestPass", "Accessibility")]`. Veya bu test türü göstergesi depolamak için kullanabilirsiniz: `[TestProperty("TestKind", "Localization")]`. Bu öznitelik ve atadığınız özellik değeri'ı kullanarak oluşturduğunuz özelliği, hem de görüntülenen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlığı altındaki Özellikler penceresi **Test özel**.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Test yapılandırma sınıfları

-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-for-generating-reports"></a>Rapor oluşturma için kullanılan öznitelikler
 Bu bölümdeki öznitelikleri, proje hiyerarşisi varlıklara süslemek test yöntemi ilişkili bir [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] takım projesi.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Özel erişimciler ile kullanılan sınıflar
 Bölümünde anlatıldığı gibi [Private erişimci oluşturmaya yarayan kullanarak duyurun](http://msdn.microsoft.com/en-us/2056c6a7-6672-42a7-8f53-fead33c56deb), birim testi için özel bir yöntem oluşturabilirsiniz. Bu oluşturma PrivateObject sınıfın bir nesnesi örnekleyen bir özel erişimci sınıfında oluşturur. PrivateObject sınıfı yansıma özel erişimci işleminin bir parçası kullanan bir sarmalayıcı sınıftır. PrivateType sınıfı benzer, ancak özel örnek yöntemleri çağırmak yerine özel statik yöntemleri çağırmak için kullanılır.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>