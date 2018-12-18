---
title: Sharepoint 2010 uygulamaları için birim testlerini yalıtmak üzere Öykünücüler kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b681164c-c87a-4bd7-be48-ed77e1578471
caps.latest.revision: 17
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4c2922d5be6c3326dac3b0c2667e5210ec908722
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915457"
---
# <a name="using-emulators-to-isolate-unit-tests-for-sharepoint-2010-applications"></a>Sharepoint 2010 uygulamaları için birim testlerini yalıtmak üzere öykünücüler kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft.SharePoint.Emulators paketi Microsoft SharePoint 2010 uygulamaları için ayrılmış birim testleri oluşturmanıza yardımcı olacak bir dizi sağlar. Öykünücü kullanmak [dolgular](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) gelen [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) en genel nesneleri ve SharePoint API yöntemlerini taklit eden hafif bellek içi nesneler oluşturmak için yalıtım çerçevesi. Bir SharePoint yöntemine öykünülmediğinde veya bir öykünücü'nın varsayılan davranışını değiştirmek istediğinizde istediğiniz sonuçları sağlamak için sahte dolgu verisi oluşturabilirsiniz.  
  
 Mevcut test yöntemleri ve sınıfları kolayca öykünücü bağlamında çalışacak şekilde dönüştürülebilir. Bu özellik çift kullanımlı testler oluşturmanıza olanak sağlar. Çift kullanımlı test, Öykünücüler kullanan yalıtılmış birim testleri gerçek SharePoint API karşı tümleştirme testleri arasında geçiş yapabilirsiniz.  
  
##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 [Gereksinimler](#BKMK_Requirements)  
  
 [AppointmentsWebPart örneği](#BKMK_The_AppointmentsWebPart_example)  
  
 [Varolan bir testi dönüştürme](#BKMK_Converting_an_existing_test)  
  
- [Öykünücüler paketini test projesine ekleme](#BKMK_Adding_the_Emulators_package_to_a_test_project)  
  
- [Bir test yöntemini öykünmeyle çalıştırma](#BKMK__Running_a_test_method_in_the_emulation_context)  
  
  [Çift kullanımlı sınıflar ve yöntemler oluşturma](#BKMK_Creating_dual_use_classes_and_methods)  
  
  [Çift kullanımlı oluşturmak için öznitelikleri test sınıfı TestInitialize ve TestCleanup kullanma](#BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class)  
  
  [Benzetilmemiş SharePoint yöntemlerinin yönetilmesi](#BKMK_Handling_non_emulated_SharePoint_methods)  
  
  [Karalama ve bir Özet yazma öykünmesi testleri](#BKMK_Writing_emulation_tests_from_scratch__and_a_summary)  
  
  [Örnek](#BKMK_Example)  
  
  [Benzetilmiş SharePoint türleri](#BKMK_Emulated_SharePoint_types)  
  
##  <a name="BKMK_Requirements"></a> Gereksinimleri  
  
- Microsoft SharePoint 2010 (SharePoint 2010 Server veya SharePoint 2010 Foundation)  
  
- Microsoft Visual Studio Enterprise  
  
- Microsoft SharePoint Öykünücüler NuGet paketi  
  
  Ayrıca sahibi olmalısınız [Visual Studio'da birim testinin temellerini](../test/unit-test-basics.md) ve biraz bilgi [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
##  <a name="BKMK_The_AppointmentsWebPart_example"></a> AppointmentsWebPart örneği  
 AppointmentsWebPart, randevularınızın SharePoint listesini yönetmek ve görüntülemek olanak tanır.  
  
 ![Randevular Web Bölümü](../test/media/ut-emulators-appointmentswebpart.png "UT_EMULATORS_AppointmentsWebPart")  
  
 Biz bu örnekte web bölümünün iki yöntemini test ediyoruz:  
  
- `ScheduleAppointment` Yöntemi yönteme geçirilen liste öğesi değerlerini doğrular ve belirtilen bir SharePoint web bir listede yeni bir giriş oluşturur.  
  
- `GetAppointmentsForToday` Yöntemi bugüne ait randevuların ayrıntılarını döndürür.  
  
  [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Converting_an_existing_test"></a> Varolan bir testi dönüştürme  
 Bir yöntemin bir SharePoint bileşeninde tipik bir test, test yöntemi SharePoint Foundation içinde geçici bir site oluşturur ve SharePoint bileşenlerini test gerekenleri altındaki kodun siteye ekler. Test yöntemi oluşturur ve bileşen örneği uygular. Testin sonunda site bozuk.  
  
 `ScheduleAppointment` Test altındaki Kodumuzun yöntemi büyük olasılıkla bileşen için yazılmış ilk yöntemlerden biri:  
  
```  
// method under test  
public bool ScheduleAppointment(SPWeb web, string listName, string name,   
    string phone, string email, string age, DateTime date, out string errorMsg)  
{  
    errorMsg = string.Empty;  
    var badFormat = this.checkInput(name, phone, email, age);  
    if (badFormat)  
    {  
        errorMsg = "Bad Format";  
        return false;  
    }  
    var exists = this.CheckDuplicate(listName, web, name, phone, email, age, date);  
    if (exists)  
    {  
        errorMsg = "Item already exists";  
        return false;  
    }  
    SPListItemCollection items = web.Lists[listName].Items;  
    // create item and populate fields  
    SPListItem item = items.Add();  
    item["Name"] = name;  
    item["Phone"] = phone;  
    item["Email"] = email;  
    item["Age"] = age;  
    item["Date"] = date.ToString("D");  
    item.Update();  
    return true;  
}  
  
```  
  
 İşlevselliğin ilk testi `ScheduleAppointment` yöntemi şöyle görünebilir:  
  
```csharp  
  
[TestMethod]  
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()  
{  
    using( var site = new SPSite("http://localhost"))  
    using (var webPart = new BookAnAppointmentWebPart())  
    {  
        // Arrange  
        string errorMsg = string.Empty;  
        DateTime date = DateTime.Now;  
        SPList list = AddListToSiteHelper(site);  
  
        // Act  
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,  
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,   
            out errorMsg);  
        list.Delete();  
  
        // Assert  
        Assert.IsTrue(success);  
    }  
}  
```  
  
 Bu test yöntemini doğrulamasına rağmen `ScheduleAppointment` yöntemi doğru bir şekilde yeni bir giriş listesine ekler, onu daha bir tümleştirme testini web bölümü bir test kodunuzun özel davranışına olmaktan çok. SharePoint ve SharePoint API için dış bağımlılıklar testin kullanıcı kodundan farklı nedenlerle başarısız olmasına neden olabilir `ScheduleAppointment` yöntemi. Oluşturma ve yok etme SharePoint sitesine ek yükü, testi kodlama işleminin normal bir parçası olarak çalıştırmak yavaş de yapabilirsiniz. Her test yöntemi için Kurulum ve site yok edilmesini gerçekleştirmek, sadece verimli Geliştirici birim testleri oluşturma sorununu compounds.  
  
 Microsoft SharePoint Öykünücüler, bir dizi nesnesi ve "en yaygın SharePoint API'leri davranışını taklit eden double" yöntemi sağlar. Öykünülmüş yöntemler SharePoint çalıştırılacak gerektirmeyen basit SharePoint API uygulamalarıdır. Yöntemi iki katına SharePoint Öykünücüleri SharePoint API çağrıları sapma Microsoft Fakes kullanarak testlerinizi yalıtırsınız ve istediğiniz kodu test ettiğinizden emin olun. Öykünülmemiş SharePoint yöntemlerini çağırdığınızda, Fakes doğrudan istenen davranışı oluşturmak için kullanabilirsiniz.  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Adding_the_Emulators_package_to_a_test_project"></a> Öykünücüler paketini test projesine ekleme  
 Bir test projesine SharePoint öykünücüleri eklemek için:  
  
1. Çözüm Gezgini'nde test projesini seçin.  
  
2. Seçin **NuGet paketlerini Yönet...**  kısayol menüsünde.  
  
3. Arama **çevrimiçi** kategorisi için `Microsoft.SharePoint.Emulators`ve ardından **yükleme**.  
  
   ![SharePoint Öykünücüler NuGet paketi](../test/media/ut-emulators-nuget.png "UT_EMULATORS_Nuget")  
  
   [Bu konudaki](#BKMK_In_this_topic)  
  
###  <a name="BKMK__Running_a_test_method_in_the_emulation_context"></a> Bir test yöntemini öykünmeyle çalıştırma  
 Paketin yüklenmesi projeleriniz için gerekli kitaplıklara başvurular ekler. Var olan bir test sınıfında öykünücüleri kullanmayı yapmak için ad alanları Ekle `Microsoft.SharePoint.Emulators` ve `Microsoft.QualityTools.Testing.Emulators`.  
  
 Test yöntemlerinizde Öykünmeyi etkinleştirmek için yöntemin gövdesinde kaydırma bir `using` oluşturan deyimi bir `SharePointEmulationScope` nesne. Örneğin:  
  
```csharp  
  
[TestMethod]  
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()  
{  
    // create the emulation scope with a using statement  
    using (new SharePointEmulationScope())  
    using( var site = new SPSite("http://localhost"))  
    using (var webPart = new BookAnAppointmentWebPart())  
    {  
        // Arrange  
        string errorMsg = string.Empty;  
        DateTime date = DateTime.Now;  
        SPList list = AddListToSiteHelper(site);  
  
        // Act  
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,  
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,   
            out errorMsg);  
        list.Delete();  
  
        // Assert  
        Assert.IsTrue(success);  
    }  
}  
  
```  
  
 Test yöntemi yürütüldüğünde, öykünücü çalışma zamanı Microsoft dinamik olarak kod içinde Microsoft.SharePoint.fakes.dll dosyasında bildirilen temsilcilere bu yöntemlere yapılan çağrılar yöneltmektir SharePoint yöntemlerde Fakes'i çağırır. Microsoft.SharePoint.Emulators.dll yakından gerçek SharePoint davranışını yakından taklit eden benzetilmiş yöntemler için temsilciler uygular. Test yöntemi veya test altındaki bileşen bir SharePoint yöntemi çağırması çıkan davranış öykünme olur.  
  
 ![Öykünücü yürütme akışı](../test/media/ut-emulators-flowchart.png "UT_EMULATORS_FlowChart")  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Creating_dual_use_classes_and_methods"></a> Çift kullanımlı sınıflar ve yöntemler oluşturma  
 Gerçek SharePoint API karşı tümleştirme testleri hem de ve Öykünücüler kullanan yalıtılmış birim testlerinde kullanılabilecek yöntemler oluşturmak için aşırı yüklenmiş oluşturucusunu kullanın. `SharePointEmulationScope(EmulationMode)` test yöntemi kodunuzu sarın için. İki değeri `EmulationMode` enum, kapsamın Öykünücüler kullanıp kullanmayacağını belirtin (`EmulationMode.Enabled`) veya SharePoint API kapsamı kullanıp kullanmadığını (`EmulationMode.Passthrough`).  
  
 Örneğin, işte önceki test ikili kullanım için nasıl değiştirebilirsiniz:  
  
```csharp  
  
// class level field specifies emulation mode  
private const EmulationMode emulatorMode = EmulationMode.Enabled;  
  
[TestMethod]  
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()  
{  
    // emulation scope determined by emulatorMode  
    using( SharePointEmulationScope(emulatorMode))  
    using( var site = new SPSite("http://localhost"))  
    using (var webPart = new BookAnAppointmentWebPart())  
    {  
        // Arrange  
        string errorMsg = string.Empty;  
        DateTime date = DateTime.Now;  
        SPList list = AddListToSiteHelper(site);  
  
        // Act  
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,  
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,   
            out errorMsg);  
        list.Delete();  
  
        // Assert  
        Assert.IsTrue(success);  
    }  
}  
```  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class"></a> Çift kullanımlı oluşturmak için öznitelikleri test sınıfı TestInitialize ve TestCleanup kullanma  
 Kullanarak sınıftaki tüm veya çoğu testi çalıştırırsanız `SharePointEmulationScope`, öykünme modu ayarlamak için sınıf düzeyi tekniklerinin yararlanabilir.  
  
- Test sınıfı yöntemleri ile oluşturulan <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> ve <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> oluşturabilir ve kapsamı yok.  
  
- Ayarı `EmulationMode` sınıf düzeyi arasında mod değişikliğini otomatikleştirmenize sağlayabilirsiniz `EmulationMode.Enabled` ve `EmulationMode.Passthrough`.  
  
  İle öznitelendirilen sınıf yöntemi `[TestInitialize]` ile öznitelendirilen bir yöntem ve her test yönteminin başlangıcında çalıştırılan `[TestCleanup]` her test yönteminin sonunda çalıştırır. İçin özel alan bildirebilir `SharePointEmulationScope` nesnesi sınıf düzeyinde, bunu başlatabilir `TestInitialize` öznitelikli yöntem ve sonra nesneyi elden `TestCleanup` öznitelikli yöntem.  
  
  Seçimini otomatikleştirmesi için seçtiğiniz herhangi bir yöntemi kullanabilirsiniz `EmulationMode`. Bir önişlemci yönergelerini kullanarak bir sembolün varlığını denetlemek için yoludur. Örneğin, Öykünücüler kullanan bir sınıf içinde test yöntemleri çalıştırmak için bir simge gibi tanımlayabileceğiniz `USE_EMULATION` test proje dosyası veya derleme komut satırı. Simge tanımlanmışsa bir sınıf seviyesi `EmulationMode` sabiti bildirilir ve kümesine `Enabled`. Aksi takdirde, sabiti ayarlanmış `Passthrough`.  
  
  Önişlemci yönergeleri kullanmayı gösteren test sınıfının bir örnek aşağıda verilmiştir ve `TestInitialize` ve `TestCleanup` öznitelikli yöntemlerinin öykünme modunu ayarlamak için.  
  
```csharp  
//namespace declarations  
...  
  
namspace MySPAppTests   
{  
    [TestClass]  
    public class BookAnAppointmentWebPartTests  
    {  
  
        // emulationScope is a class level field  
        private SharePointEmulationScope emulationScope;  
  
        // preprocessor directives determine the value of emulatorMode  
        #if USE_EMULATIONprivate const EmulationMode emulatorMode = EmulationMode.Enabled;#elseprivate const EmulationMode emulatorMode = EmulationMode.Passthrough;#endif  
  
        // InitializeTest sets the emulation scope at the beginning of each test method  
        [TestInitialize]public void InitializeTest(){this.emulationScope = new SharePointEmulationScope(emulatorMode);}  
  
        // CleanupTest disposes the emulation scope at the end of each test method  
        [TestCleanup]public void CleanupTest(){this.emulationScope.Dispose();}  
  
        [TestMethod]  
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()  
        {  
            // remove the SharePointEmulationScope using statement from the method  
            using( var site = new SPSite("http://localhost"))  
            using (var webPart = new BookAnAppointmentWebPart())  
            {  
                // Arrange  
                string errorMsg = string.Empty;  
                DateTime date = DateTime.Now;  
                SPList list = AddListToSiteHelper(site);  
  
                // Act  
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,  
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,   
                    out errorMsg);  
                list.Delete()  
  
                // Assert  
                Assert.IsTrue(success);  
            }  
        }  
  
        ...// More tests  
  
    }  
}  
  
```  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Handling_non_emulated_SharePoint_methods"></a> Benzetilmemiş SharePoint yöntemlerinin yönetilmesi  
 SharePoint türlerinin hepsi benzetilmiş değildir ve benzetilmiş bazı türlerdeki tüm yöntemleri benzetilmiş değildir. Test altındaki kodun benzetilmeyen bir SharePoint yöntemi çağırması durumunda çağırılıyorsa yöntem bir `NotSupportedException` özel durum. Bir özel durum oluştuğunda SharePoint yöntemine sahte dolgu ekleyin.  
  
 **SharePoint fakes kurma**  
  
 Microsoft Fakes dolgu verileri açıkça çağırmak için:  
  
1. Benzetilmemiş bir SharePoint sınıfını istiyorsanız, Microsoft.SharePoint.fakes dosyasını düzenleyin ve sınıfı sınıflar listesine ekleyin. Bkz: [saplamalar ve dolguların kod oluşturma yapılandırma](http://msdn.microsoft.com/library/hh708916.aspx#bkmk_configuring_code_generation_of_stubs) bölümünü [kod oluşturma, derleme ve adlandırma kuralları Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md).  
  
    ![Çözüm Gezgini'nde klasörü fakes](../test/media/ut-emulators-fakesfilefolder.png "UT_EMULATORS_FakesFileFolder")  
  
2. Test projesini en az bir kez Microsoft SharePoint Öykünücüler paketini yükledikten sonra ve Microsoft.SharePoint.Fakes dosyası düzenlediyseniz yeniden oluşturun. Proje derleme oluşturur ve doldurur bir **FakesAssembly** disk üzerinde proje kök klasörünüzde klasör.  
  
    ![FakesAssembly klasör](../test/media/ut-emulators-fakesassemblyfolder.png "UT_EMULATORS_FakesAssemblyFolder")  
  
3. Bir başvuru ekleyin **Microsoft.SharePoint.14.0.0.0.Fakes.dll** bulunan derleme **FakesAssembly** klasör.  
  
4. (İsteğe bağlı) Test sınıfı için bir ad alanı yönergesi için ekleme `Microsoft.QualityTools.Testing.Fakes`, `Microsoft.SharePoint.Fakes` ve tüm iç içe geçmiş ad alanı `Microsoft.SharePoint.Fakes`kullanmak istediğiniz.  
  
   **Bir SharePoint yöntemi için dolgu temsilcisi uygulama**  
  
   Bizim örnek projemizde `GetAppointmentsForToday` yöntem çağrılarını [SPList.getıtems(spquery)](http://msdn.microsoft.com/library/ms457534.aspx) SharePoint API yöntemini.  
  
```csharp  
// method under test  
public string GetAppointmentsForToday(string listName, SPWeb web)  
{  
    SPList list = web.Lists[listName];  
    DateTime today = DateTime.Now;  
    var listQuery = new SPQuery{Query = String.Format("<Where><Eq><FieldRef Name='Date'/>" +"<Value Type='Text'>{0}</Value>" +"</Eq></Where>", today.ToString("D"))};  
    var result = new System.Text.StringBuilder();  
    foreach (SPListItem item in list.GetItems(listQuery))  
    {  
        result.AppendFormat("Name: {0}, Phone: {1}, Email: {2}, Age: {3}, Date: {4}\n",   
            item["Name"], item["Phone"], item["Email"], item["Age"], item["Date"]);  
    }  
    return result.ToString();  
}  
  
```  
  
 `SPList.GetItems(SPQuery)` Aşırı yüklenen sürümü `GetItems` yöntemi yapılmaz. Bu nedenle, yalnızca sarmalama için varolan bir testi `GetAppointmentsForToday` içinde `SharePoint.Emulation.Scope` başarısız olur. Fakes temsilci bir uygulamasını yazmanız gereken bir çalışma testi oluşturmak için `ShimSPList.GetItemsSPQuery` karşı test etmek istediğiniz sonuçları döndürür.  
  
 Varolan bir test yöntemi, bir değişiklik işte `GetAppointmentsForTodayReturnsOnlyTodaysAppointments`, Fakes temsilci uygulayan. Gerekli değişiklikler açıklamalarda çağrılır:  
  
> [!IMPORTANT]
>  Açıkça Fakes dolgular throw oluşturma yöntemleri test bir `ShimNotSupported` test çalıştırdığınızda, özel durum `EmulationMode.Passthrough` bağlamı. Bu sorunu önlemek için ayarlamak için bir değişken kullanın `EmulationMode` değeri ve tüm Fakes kodlarını kaydırma bir `if` değeri test deyimi.  
  
```csharp  
// class level field to set emulation mode  
private const EmulationMode emulatorMode = EmulationMode.Enabled  
  
[TestMethod]  
public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()  
{  
  
    // create the emulation scope with a using statement  
    using (var emulationScope = new SharePointEmulationScope(emulatorMode))  
    using( var site = new SPSite("http://localhost"))  
    using (var webPart = new BookAnAppointmentWebPart())  
    {  
        // Arrange  
        DateTime date = DateTime.Now;  
        SPList list = AddListToSiteHelper(site);  
        // insert 2 items into list  
        AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",  
            "raisa@outlook.com", "55", date.ToString("D") });  
        AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",  
            "francis@contoso.com", "42", date.AddDays(1).ToString("D") });  
  
        // use Fakes shims only if emulation is enabled  
        if (emulatorMode == EmulationMode.Enabled){var sList = new ShimSPList(list);sList.GetItemsSPQuery = (query) =>{var shim = new ShimSPListItemCollection();shim.Bind(new[] { list.Items[0] });return shim.Instance;}}  
  
        // Act  
        string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);  
        list.Delete();  
  
        // Assert  
        Assert.IsTrue(result.Contains(String.Format(  
            "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +  
            "Age: 55, Date: {0}", date.ToString("D"))));  
        Assert.IsFalse(result.Contains("Name: Francis Totten"));  
    }  
}  
  
```  
  
 Bu yöntemde, önce öykünmenin etkin olup olmadığını test ederiz. İse, için Fakes dolgu nesnesi oluştururuz. bizim `SPList` listesi oluşturma ve bir yöntem oluşturarak kendi `GetItemsSPQuery` temsilci. Fakes temsilci kullanan `Bind` doğru liste öğesini eklemek için yöntemi `ShimSPListItemCollection` çağırana döndürülür.  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Writing_emulation_tests_from_scratch__and_a_summary"></a> Karalama ve bir Özet yazma öykünmesi testleri  
 Öykünme ve önceki bölümlerde açıklanan çift kullanımlı testler oluşturmak için tekniklerin, mevcut testleri dönüştürdüğünüzü varsaymasına rağmen teknikleri sıfırdan testler yazmak için kullanabilirsiniz. Aşağıdaki listede bu teknikler özetlenmektedir:  
  
- Sınama projesinde öykünücü kullanmak için Microsoft.SharePoint.Emulators NuGet paketini projeye ekleyin.  
  
- Sınama yönteminde öykünücü kullanmak için oluşturun bir `SharePointEmulationScope` yöntemin başında bir nesne. Kapsam atılana kadar tüm desteklenen SharePoint API'larının.  
  
- Test kodunuzu gerçek bir SharePoint API'si yazar gibi yazın. Öykünme bağlamı, SharePoint yöntemlerinin çağrıları otomatik olarak saptıran.  
  
- SharePoint nesnelerin hepsi benzetilmiş değildir ve benzetilmiş bazı nesnelerin tüm yöntemleri benzetilmiş değildir. A `NotSupportedException` benzetilmemiş nesne veya yöntem kullandığınızda özel durumu harekete geçirilir. Böyle bir durumda gerekli davranışın döndürülmesi için Fakes dolgu temsilcisi yönteminde açıkça oluşturun.  
  
- Çift kullanımlı testler oluşturmak için kullanın `SharePointEmulationScope(EmulationMode)` kullanarak öykünme kapsamı nesnesi oluşturmak için oluşturucu. `EmulationMode` SharePoint çağrıları öykünülmüş veya gerçek bir SharePoint sitesine karşı yürütülen değerini belirtir.  
  
- Tümünü veya bir test sınıfındaki test yöntemlerinizin çoğu öykünme bağlamında çalışırsa, bir sınıf seviyesi kullanabileceğiniz `TestInitialize` öznitelikli yöntemini `SharePointEmulationScope` nesnesi ve bir sınıf seviyesi alanını öykünme modunu ayarlamak için. Bu öykünme modunu değiştirmeyi otomatikleştirmenize yardımcı olur. Ardından bir `TestCleanup` öznitelikli kapsam nesnesini atmak için yöntem.  
  
  [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Example"></a> Örnek  
 Yukarıda açıklanan SharePoint öykünücüsü tekniklerini içeren son bir örnek aşağıda verilmiştir:  
  
```csharp  
using System;   
//other namespace declarations  
...   
// code under test  
using MySPApps;  
using Microsoft.SharePoint;  
// unit testing and emulators  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.QualityTools.Testing.Emulators;  
using Microsoft.SharePoint.Emulators;  
// explicit Fakes shims  
using Microsoft.QualityTools.Testing.Fakes;  
using Microsoft.SharePoint.Fakes  
  
namspace MySPAppTests   
{  
    [TestClass]  
    public class BookAnAppointmentWebPartTests  
    {  
  
        // emulationScope is a class level field  
        private SharePointEmulationScope emulationScope;  
  
        // preprocessor directives determine the value of emulatorMode  
        #if USE_EMULATION  
            private const EmulationMode emulatorMode = EmulationMode.Enabled;  
        #else  
            private const EmulationMode emulatorMode = EmulationMode.Passthrough;  
        #endif  
  
        // InitializeTest sets the emulation scope at the beginning of each test method  
        [TestInitialize]  
        public void InitializeTest()  
        {  
            this.emulationScope = new SharePointEmulationScope(emulatorMode);  
        }  
  
        // CleanupTest disposes the emulation scope at the end of each test method  
        [TestCleanup]  
        public void Cleanup()  
        {  
            this.emulationScope.Dispose();  
        }  
  
        [TestMethod]  
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()  
        {  
            // remove the SharePointEmulationScope using statement from the method  
            using( var site = new SPSite("http://localhost"))  
            using (var webPart = new BookAnAppointmentWebPart())  
            {  
                // Arrange  
                string errorMsg = string.Empty;  
                DateTime date = DateTime.Now;  
                SPList list = AddListToSiteHelper(site);  
  
                // Act  
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,  
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,   
                    out errorMsg);  
                list.Delete()  
  
                // Assert  
                Assert.IsTrue(success);  
            }  
        }  
  
        [TestMethod]  
        public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()  
        {  
  
            // remove the SharePointEmulationScope using statement from the method  
            using( var site = new SPSite("http://localhost"))  
            using (var webPart = new BookAnAppointmentWebPart())  
            {  
                // Arrange  
                DateTime date = DateTime.Now;  
                SPList list = AddListToSiteHelper(site);  
                // insert 2 items into list  
                AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",  
                    "raisa@outlook.com", "55", date.ToString("D") });  
                AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",  
                    "francis@contoso.com", "42", date.AddDays(1).ToString("D") });  
  
                // use Fakes shims only if emulation is enabled  
                if (emulatorMode == EmulationMode.Enabled)  
                {  
                    var sList = new ShimSPList(list);  
  
                    sList.GetItemsSPQuery = (query) =>  
                    {  
                        var shim = new ShimSPListItemCollection();  
                        shim.Bind(new[] { list.Items[0] });  
                        return shim.Instance;  
                    }  
                }  
  
                // Act  
                string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);  
                list.Delete();  
  
                // Assert  
                Assert.IsTrue(result.Contains(String.Format(  
                    "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +  
                    "Age: 55, Date: {0}", date.ToString("D"))));  
                Assert.IsFalse(result.Contains("Name: Francis Totten"));  
            }  
        }  
  
        ...// More tests  
  
    }  
}  
  
```  
  
##  <a name="BKMK_Emulated_SharePoint_types"></a> Benzetilmiş SharePoint türleri  
 [Microsoft.SharePoint.SPField](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPField)  
  
 [Microsoft.SharePoint.SPFieldIndex](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndex)  
  
 [Microsoft.SharePoint.SPFieldIndexCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndexCollection)  
  
 [Microsoft.SharePoint.SPFieldLink](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLink)  
  
 [Microsoft.SharePoint.SPFieldLinkCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLinkCollection)  
  
 [Microsoft.SharePoint.SPFieldUrlValue](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldUrlValue)  
  
 [Microsoft.SharePoint.SPFile](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFile)  
  
 [Microsoft.SharePoint.SPFileCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFileCollection)  
  
 [Microsoft.SharePoint.SPFolder](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolder)  
  
 [Microsoft.SharePoint.SPFolderCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolderCollection)  
  
 [Microsoft.SharePoint.SPItem](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItem)  
  
 [Microsoft.SharePoint.SPItemEventDataCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventDataCollection)  
  
 [Microsoft.SharePoint.SPItemEventProperties](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventProperties)  
  
 [Microsoft.SharePoint.SPList](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPList)  
  
 [Microsoft.SharePoint.SPListCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListCollection)  
  
 [Microsoft.SharePoint.SPListEventProperties](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListEventProperties)  
  
 [Microsoft.SharePoint.SPListItem](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItem)  
  
 [Microsoft.SharePoint.SPListItemCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItemCollection)  
  
 [Microsoft.SharePoint.SPQuery](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPQuery)  
  
 [Microsoft.SharePoint.SPRoleAssignment](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignment)  
  
 [Microsoft.SharePoint.SPRoleAssignmentCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignmentCollection)  
  
 [Microsoft.SharePoint.SPSecurableObject](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurableObject)  
  
 [Microsoft.SharePoint.SPSecurity](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity)  
  
 [Microsoft.SharePoint.SPSite](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite)  
  
 [Microsoft.SharePoint.SPUser](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPUser)  
  
 [Microsoft.SharePoint.SPUserCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPUserCollection)  
  
 [Microsoft.SharePoint.SPView](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPView)  
  
 [Microsoft.SharePoint.SPViewCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewCollection)  
  
 [Microsoft.SharePoint.SPViewContext](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewContext)  
  
 [Microsoft.SharePoint.SPWeb](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb)  
  
 [Microsoft.SharePoint.SPWebCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPWebCollection)  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuza birim testi](../test/unit-test-your-code.md)   
 [Kodlanmış UI testleriyle SharePoint 2010 uygulamalarını test etme](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)   
 [Web performansı ve yük SharePoint 2010 ve 2013 uygulamalarını test etme](http://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54)   
 [SharePoint Çözümleri Geliştirme](http://msdn.microsoft.com/library/059bce0f-c301-4234-a0b4-9c14b7cdfa3e)



