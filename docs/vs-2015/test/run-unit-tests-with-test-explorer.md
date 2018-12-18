---
title: Test Gezgini ile birim testleri çalıştırma | Microsoft Docs
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
- vs.unittesting.testexplorer.overview
ms.assetid: 91b167a3-280a-498b-8fc2-f67859a2c64e
caps.latest.revision: 29
ms.author: gewarren
manager: douge
ms.openlocfilehash: f4c5a8a4d090a7603f83f6fb3c3d9deb0c67d5f8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846843"
---
# <a name="run-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testleri çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Test Gezgini, Visual Studio veya üçüncü taraf birim testi projelerini birim testleri çalıştırmak, testleri kategoriler halinde gruplandırmak, test listesini filtrelemek ve oluşturmak, kaydetmek ve test çalma listeleri çalıştırmak için kullanın. Ayrıca, Testlerde Hata Ayıkla ve test, performans ve kod kapsamını analiz edin.  
  
##  <a name="BKMK_Contents"></a> İçeriği  
 [Birim test çerçeveler ve test projeleri](#BKMK_Unit_test_frameworks_and_test_projects)  
  
 [Testleri Test Gezgini'nde çalıştırma](#BKMK_Run_tests_in_Test_Explorer)  
  
 [Test sonuçlarını görüntüle](#BKMK_View_test_results)  
  
 [Grup ve test listesini Filtrele](#BKMK_Group_and_filter_the_test_list)  
  
 [Özel çalma listeleri oluşturma](#BKMK_Create_custom_playlists)  
  
 [Hata ayıklama ve birim testlerini çözümleme](#BKMK_Debug_and_analyze_unit_tests)  
  
 [Dış Kaynaklar](#BKMK_External_resources)  
  
##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Birim test çerçeveler ve test projeleri  
 Visual Studio, hem yönetilen hem de yerel kod için Microsoft birim testi çerçevelerini içerir. Ancak, Test Gezgini Test Gezgini bağdaştırıcısı uygulayan test çerçevesi da herhangi bir birimi çalıştırabilirsiniz. Üçüncü taraf birim test çerçeveleri yükleme hakkında daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçevelerini yükleme](../test/install-third-party-unit-test-frameworks.md)  
  
 Test Gezgini, bir çözümde birden çok test projesini ve üretim kodu projelerin bir parçası olan test sınıflarından testleri çalıştırabilirsiniz. Test projeleri farklı birim test çerçeveleri kullanabilir. Test altındaki kod .NET Framework için yazıldığında, test projesi, ayrıca hedef kodun dili ne olursa olsun .NET Framework hedefleyen herhangi bir dilde yazılabilir. Yerel C/C++ kod projeleri, bir C++ birim test çerçevesi kullanılarak test edilmelidir.  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Run_tests_in_Test_Explorer"></a> Testleri Test Gezgini'nde çalıştırma  
 [Testler](#BKMK_Run_tests) **&#124;** [her derleme sonrasında Testleri Çalıştır](#BKMK_Run_tests_after_every_build)  
  
 Test projesi oluşturduğunuzda, testler Test Gezgini'nde görünür. Test Gezgini görünür değilse seçin **Test** Visual Studio menüsünde **Windows**ve ardından **Test Gezgini**.  
  
 ![Birim Test Gezgini](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  
  
 Çalıştırma, yazma ve testlerinizi yeniden çalıştırın, Test Gezgini sonuçları varsayılan gruplarında görüntüler **başarısız testler**, **başarılı testler**, **Atlanan testler** ve  **Testleri Çalıştır**. Test Gezgini'nin testlerinizi gruplandırma şeklini değiştirebilirsiniz.  
  
 Bulma, düzenleme ve Test Gezgini araç çubuğundan testleri çalıştırmak, işin çoğunu gerçekleştirebilirsiniz.  
  
 ![Test Gezgini araç çubuğundan testleri](../test/media/ute-toolbar.png "UTE_ToolBar")  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
###  <a name="BKMK_Run_tests"></a> Testleri çalıştırın  
 Tüm testler, Çözümdeki tüm testleri bir grup veya seçtiğiniz test kümesini çalıştırabilirsiniz. Aşağıdakilerden birini yapın:  
  
- Bir çözümdeki tüm testleri çalıştırmak için tercih **tümünü Çalıştır**.  
  
- Varsayılan bir grupta tüm testleri çalıştırmak için tercih **Çalıştır...**  ve sonra menüde grubu seçin.  
  
- Seçilmiş test için bağlam menüsünü açın ve ardından çalıştırmak istediğiniz testleri tek tek seçin **seçili Testleri Çalıştır**.  
  
- Paralel test yürütme ile bireysel testler herhangi bir sırada çalıştırılan engelleyen bağımlılık varsa, açma ![ALIŞTIR&#95;parallelicon&#45;küçük](../test/media/ute-parallelicon-small.png "UTE_parallelicon küçük") araç çubuğundaki iki durumlu düğme. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.  
  
  Testler çalışırken Test Gezgini penceresinin en üstündeki geçer/başarısız çubuğunda animasyon görünür. Tüm testler başarılı ya da herhangi bir test başarısız olursa kırmızıya döner test çalışması kılavuzumuzun geçer/başarısız çubuğu yeşile döner.  
  
  ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
###  <a name="BKMK_Run_tests_after_every_build"></a> Her derleme sonrasında Testleri Çalıştır  
  
> [!WARNING]
>  Her yapı Visual Studio Enterprise'da desteklendikten sonra birim testleri çalıştırma.  
  
|||  
|-|-|  
|![Yapıdan sonra çalıştırmak](../test/media/ute-runafterbuild-btn.png "UTE_RunAfterBuild_btn")|Her bir yerel oluşturmadan sonra birim testlerinizi çalıştırmak için tercih **Test** standart menüde seçip **oluşturmadan sonra Testleri Çalıştır** Test Gezgini araç çubuğundaki.|  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_View_test_results"></a> Test sonuçlarını görüntüle  
 [Test ayrıntılarını görüntüleme](#BKMK_View_test_details) **&#124;** [test yönteminin kaynak kodunu görüntüleme](#BKMK_View_the_source_code_of_a_test_method)  
  
 Test Gezgini çalıştırma, yazma ve testlerinizi yeniden çalıştırın gibi sonuçları gruplarında görüntüler. **başarısız testler**, **başarılı testler**, **Atlanan testler** ve **çalıştırma Testleri**. Test Gezgini görüntüler altındaki ayrıntılar bölmesi test özeti çalıştırın.  
  
###  <a name="BKMK_View_test_details"></a> Test ayrıntılarını görüntüleme  
 Tek bir testin ayrıntılarını görüntülemek için testi seçin.  
  
 ![Test yürütme ayrıntıları](../test/media/ute-testdetails.png "UTE_TestDetails")  
  
 Test ayrıntıları bölmesinde aşağıdaki bilgileri görüntüler:  
  
- Kaynak dosya adı ve test yönteminin satır sayısı.  
  
- Testin durumu.  
  
- Test yöntemini çalıştırmak için geçen geçen süre.  
  
  Test başarısız olursa, Ayrıntılar bölmesinde de görüntüler:  
  
- Test için birim test çerçevesi tarafından döndürülen ileti.  
  
- Yığın izleme zaman test başarısız oldu.  
  
  ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
###  <a name="BKMK_View_the_source_code_of_a_test_method"></a> Test yönteminin kaynak kodunu görüntüleme  
 Visual Studio düzenleyicisinde bir test yöntemi için kaynak kodunu görüntülemek için testi seçin ve ardından **testi Aç** bağlam menüsünde (klavye: F12).  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Group_and_filter_the_test_list"></a> Grup ve test listesini Filtrele  
 [Test listesini gruplandırma](#BKMK_Grouping_the_test_list) **&#124;** [nitelikler grupla](#BKMK_Group_by_traits) **&#124;** [arama ve filtre test listesi](#BKMK_Search_and_filter_the_test_list)  
  
 Test Gezgini, testlerinizi önceden tanımlanmış kategoriler halinde gruplamanızı sağlar. Test Gezgini izin verir, çalışan çoğu test çerçeveleri, kendi kategorileri ve testlerinizi gruplamak için kategori/değer çiftlerini tanımlayın. Ayrıca test özelliklerine karşı dizeleri eşleştirerek test listesine filtre uygulayabilirsiniz.  
  
###  <a name="BKMK_Grouping_the_test_list"></a> Test listesini gruplandırma  
 Testlerin düzenlenme şeklini değiştirmek için aşağı yanındaki oku seçin **Group By** düğmesi ![Test Gezgini Grup düğmesi](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn") ve yeni bir gruplandırma seçin ölçütleri.  
  
 ![Testleri Test Gezgini'nde kategoriye göre grup](../test/media/ute-groupbycategory.png "UTE_GroupByCategory")  
  
### <a name="test-explorer-groups"></a>Test Gezgini grupları  
  
|Grup|Açıklama|  
|-----------|-----------------|  
|**Süresi**|Yürütme süresine göre testi gruplandırır: **hızlı**, **orta**, ve **yavaş**.|  
|**Sonucu**|Yürütme sonuçlarına göre testleri gruplandırır: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|  
|**Nitelikler**|Tanımladığınız kategori/değer çiftlerine göre testi gruplandırır. Nitelik kategorileri ve değerlerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanır.|  
|**Project**|Projelerin adına göre testi gruplandırır.|  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
###  <a name="BKMK_Group_by_traits"></a> Niteliklere göre gruplandırma  
 Ayırt edici nitelik genellikle bir kategori ad/değer çifti olan, ancak tek bir kategori de olabilir. Nitelikler, birim test çerçevesi tarafından bir test yöntemi olarak tanımlanan yöntemlere atanabilir. Bir birim test çerçevesi, ayırt edici nitelik kategorilerini tanımlayabilir. Kendi kategori ad/değer çiftlerinizi tanımlamak için ayırdedici nitelik kategorilerine değerler ekleyebilirsiniz. Nitelik kategorileri ve değerlerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanır.  
  
 **Microsoft birim testi için yönetilen kod çerçevesi içindeki nitelikler**  
  
 Yönetilen uygulamalar için Microsoft birim test çerçevesi, ayırt edici nitelik adını tanımlamak / değer çiftinin bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> özniteliği. Test çerçevesi, önceden tanımlanmış bu nitelikleri de içerir:  
  
|Nitelik|Açıklama|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Sahip kategorisi birim test çerçevesi tarafından tanımlanır ve sahibin bir dize değerini vermenizi gerektirir.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Öncelik kategorisi birim test çerçevesi tarafından tanımlanır ve bir tamsayı öncelik değeri vermenizi gerektirir.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|TestCategory özniteliği bir değer olmadan bir kategori girmenize olanak tanır. TestCategory özniteliği tarafından tanımlanan bir kategori, TestProperty özniteliği kategorisi de olabilir.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|TestProperty özniteliği ayırdedici nitelik kategorisi/değer çifti tanımlamanızı sağlar.|  
  
 **Microsoft birim testi çerçevesi için C++ içindeki nitelikler**  
  
 Ayırt edici nitelik tanımlamak için `TEST_METHOD_ATTRIBUTE` makrosu. Örneğin, adlı bir ayırt edici nitelik tanımlamak için `TEST_MY_TRAIT`:  
  
```cpp  
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)  
```  
  
 Tanımlanan niteliği birim testlerinizde kullanmak için:  
  
```  
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)  
    TEST_OWNER(L"OwnerName")  
    TEST_PRIORITY(1)  
    TEST_MY_TRAIT(L"thisTraitValue")  
END_TEST_METHOD_ATTRIBUTE()  
  
TEST_METHOD(Method1)  
{     
    Logger::WriteMessage("In Method1");  
    Assert::AreEqual(0, 0);  
}  
```  
  
### <a name="c-trait-attribute-macros"></a>C++ ayırt edici öznitelik makroları  
  
|Makrosu|Açıklama|  
|-----------|-----------------|  
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Ayırt edici nitelik tanımlamak için test_method_attrıbute makrosunu kullanın.|  
|`TEST_OWNER(ownerAlias)`|Test yönteminin sahibini belirtmek için önceden tanımlanmış sahip ayırt edici niteliğini kullanın.|  
|`TEST_PRIORITY(priority)`|Test yöntemlerinize göreli öncelikler atamak için önceden tanımlanmış öncelik ayırt edici niteliğini kullanın.|  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
###  <a name="BKMK_Search_and_filter_the_test_list"></a> Arama ve test listesini Filtrele  
 Projelerinizde görüntüleyip çalıştırabileceğiniz, test yöntemlerini sınırlamak için Test Gezgini filtreleri kullanabilirsiniz.  
  
 Bir dizeyi Test Gezgini arama kutusuna yazın ve ENTER TUŞUNA basın, test listesi yalnızca tam olarak belirtilen adları dizeyi içeren testleri görüntüleyecek şekilde filtrelenmiştir.  
  
 Farklı ölçütlere göre filtrelemek için:  
  
1. Arama kutusunun sağındaki açılan listeyi açın.  
  
2. Yeni bir ölçüt seçin.  
  
3. Filtre değeri tırnak işaretleri arasında girin.  
  
   ![Test Gezgini testleri filtrelemek](../test/media/ute-filtertestlist.png "UTE_FilterTestList")  
  
> [!NOTE]
>  Arama büyük/küçük harfe duyarsızdır ve belirtilen dizeyi ölçüt değeri herhangi bir bölümü eşleştir.  
  
|Niteleyicisi|Açıklama|  
|---------------|-----------------|  
|**Nitelik**|Hem ayırdedici nitelik kategorisini hem de değer eşleşmelerini arar. Nitelik kategorileri ve değerlerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanır.|  
|**Project**|Test proje adı eşleşmeleri arar.|  
|**Hata iletisi**|Arama tarafından döndürülen başarısız kullanıcı tanımlı hata iletileri için eşleşme onaylar.|  
|**Dosya yolu**|Test kaynak dosyaları tam olarak nitelenmiş dosya adını eşleşmelerini arar.|  
|**Tam adı**|Test ad alanları, sınıflar ve yöntemler tam olarak nitelenmiş dosya adını eşleşmelerini arar.|  
|**Output**|Standart çıkış (stdout) veya standart hata (stderr) yazılmış kullanıcı tanımlı hata iletileri arar. Çıktı iletilerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanmıştır.|  
|**Sonucu**|Eşleşmeleri için Test Gezgini kategori adlarını arar: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|  
  
 Bir alt kümesini bir filtre sonuçlarını tutmak için aşağıdaki sözdizimini kullanın:  
  
```  
FilterName:"Criteria" -FilterName:"SubsetCriteria"  
```  
  
 Örneğin,  
  
```  
FullName:"MyClass" - FullName:"PerfTest"  
```  
  
 "adında PerfTest" adında de bu testlerin dışında adında "Sınıfım" içeren tüm testleri döndürür.  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Create_custom_playlists"></a> Özel çalma listeleri oluşturma  
 Oluşturun ve çalıştırın veya bir grup olarak görüntülemek istediğiniz testlerin listesini kaydedin. Çalma listesi seçtiğinizde listedeki testler görüntülenen Test Gezgini. Bir testi birden fazla çalma listesine ekleyebilirsiniz ve varsayılan seçtiğinizde projenizdeki tüm testler kullanılabilir **tüm testleri** çalma listesi.  
  
 ![Bir çalma listesi Seç](../test/media/ute-playlist.png "UTE_Playlist")  
  
 **Bir çalma listesi oluşturmak için**, Test Gezgini'nde bir veya birden çok test seçin. Bağlam menüsünde **çalma listesine Ekle**, **NewPlaylist**. Dosya adı ve belirttiğiniz konuma kaydetmek **yeni çalma listesi oluştur** iletişim kutusu.  
  
 **Bir çalma listesine testler eklemek için**, Test Gezgini'nde bir veya birden çok test seçin. Bağlam menüsünde **çalma listesine Ekle**, testleri eklemek istediğiniz çalma listesini seçin.  
  
 **Bir çalma listesini açmak için**, Test, Visual Studio menüsünden, çalma Listesi'ni seçin ve son kullanılan çalma listesinden seçin veya çalma listesi konumunu ve adını belirtmek için çalma listesi Aç'ı seçin.  
  
 Paralel test yürütme ile bireysel testler herhangi bir sırada çalıştırılan engelleyen bağımlılık varsa, açma ![ALIŞTIR&#95;parallelicon&#45;küçük](../test/media/ute-parallelicon-small.png "UTE_parallelicon küçük") araç çubuğundaki iki durumlu düğme. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Debug_and_analyze_unit_tests"></a> Hata ayıklama ve birim testlerini çözümleme  
 [Birim testlerinin hatalarını ayıklama](#BKMK_Debug_unit_tests) **&#124;** [Tanıla test yöntemi performans sorunlarını](#BKMK_Diagnose_test_method_performance_issues) **&#124;** [birim testi kod kapsamını analiz etme](#BKMK_Analyzeunit_test_code_coverage)  
  
###  <a name="BKMK_Debug_unit_tests"></a> Birim testlerinin hatalarını ayıklama  
 Test Gezgini, testleriniz için hata ayıklama oturumu başlatmak için kullanabilirsiniz. Kodunuzu Visual Studio hata ayıklayıcısı ile sorunsuz bir şekilde Adımlama, İleri ve geri birim testleri ve test altındaki projeye arasında sürer. Hata ayıklamayı başlatmak için:  
  
1. Visual Studio düzenleyicisinde, hatalarını ayıklamak istediğiniz bir veya daha fazla test yöntemlerinde kesme noktası ayarlayın.  
  
   > [!NOTE]
   >  Test yöntemleri herhangi bir sırada çalışabileceğinden, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktalarını ayarlayın.  
  
2. Test Gezgini'nde test yöntemlerini seçin ve ardından **seçilen Testlerde Hata Ayıkla** bağlam menüsünde.  
  
   Hata ayıklayıcısı hakkında daha fazla bilgi için bkz. [Visual Studio'da hata ayıklama](../debugger/debugging-in-visual-studio.md).  
  
   ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
###  <a name="BKMK_Diagnose_test_method_performance_issues"></a> Test yöntemi performans sorunlarını tanılama  
 Neden bir test yöntemi, çok fazla zaman aldığını tanılamak için yöntemi Test Gezgini'nde seçin ve ardından bağlam menüsünde profilini seçin. Bkz: [performans Gezgini](../profiling/performance-explorer.md).  
  
###  <a name="BKMK_Analyzeunit_test_code_coverage"></a> Birim testi kod kapsamını analiz etme  
  
> [!NOTE]
>  Birim testi kod kapsamı yalnızca Visual Studio Enterprise'da kullanılabilir.  
  
 Visual Studio kod kapsamı Aracı'nı kullanarak birim testleriniz tarafından gerçekten edildiğini, ürün kodu miktarını belirleyebilirsiniz. Kod kapsamı Seçili testler ya da bir çözümdeki tüm testleri çalıştırabilirsiniz.  
  
 Bir çözümde test yöntemleri için kod kapsamını çalıştırmak için:  
  
1. Seçin **testleri** Visual Studio menüsünde seçip **kod kapsamını analiz etme**.  
  
2. Alt menüden olarak aşağıdaki komutlardan birini seçin:  
  
   -   **Seçili testler** Test Gezgini'nde seçtiğiniz test yöntemlerini çalıştırır.  
  
   -   **Tüm testler** Çözümdeki tüm test yöntemlerini çalıştırır.  
  
   Kod Kapsamı Sonuçları penceresi satır, işlevi, sınıf, ad alanı ve modül tarafından uygulanan ürünün kodu bloklarının yüzdesini görüntüler.  
  
   Daha fazla bilgi için [kullanarak kod kapsamı için belirlemek ne kadar kodun test](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
   ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_External_resources"></a> Dış Kaynaklar  
  
###  <a name="BKMK_Guidance"></a> Kılavuzu  
 [Visual Studio 2012 – bölüm 2 ile sürekli teslimat testi: birim testi: iç testler](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuza birim testi](../test/unit-test-your-code.md)   
 [64 bitlik bir işlem olarak birim testi çalıştırma](../test/run-a-unit-test-as-a-64-bit-process.md)



