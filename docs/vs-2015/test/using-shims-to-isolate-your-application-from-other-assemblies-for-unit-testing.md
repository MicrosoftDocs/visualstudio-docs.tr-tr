---
title: Uygulamanızı birim testi için diğer derlemelerden yalıtmak üzere dolgular kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2a34de2-6527-4c21-8b93-2f268ee894b7
caps.latest.revision: 14
ms.author: gewarren
manager: douge
ms.openlocfilehash: a6cd7efa12fc87c5de4bd82bcfb789d50193dbe7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904423"
---
# <a name="using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Birim testi için uygulamanızı diğer derlemelerden yalıtmak üzere dolgular kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dolgu türleri ** test ortamı'ndan kolayca yalıtmak bileşenleri bildirmek için Microsoft Fakes çerçevesi kullanan iki teknoloji biridir. Dolgular çağrıları belirli metotlar için testinizi bir parçası olarak yazdığınız kod yöneltmektir. Birçok yöntem dış koşullar bağımlı farklı sonuçlar döndürebilir, ancak dolgu testinizin denetiminde ve her çağrıda tutarlı sonuçlar döndürebilir. Bu testleri yazmak çok daha kolay hale getirir.  
  
 Kodunuzu çözümünüzün bir parçası olmayan derlemelerden yalıtmak üzere dolgular kullanma. Bileşenleri çözümünüzün birbirinden yalıtmak üzere saplamalar kullanmanızı öneririz.  
  
 Kılavuzu genel bakış ve hızlı başlangıç için bkz: [yalıtma kod altında Microsoft Fakes ile Test](../test/isolating-code-under-test-with-microsoft-fakes.md)  
  
 **Gereksinimler**  
  
- Visual Studio Enterprise  
  
  Bkz: [Video (1 saat 16): Visual Studio 2012'de beklemediğiniz test edilebilir kod Fakes ile test etme](http://go.microsoft.com/fwlink/?LinkId=261837)  
  
## <a name="in-this-topic"></a>Bu konuda  
 İşte bu konudaki bilgi edineceksiniz:  
  
 [Örnek: Y2K hata](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Example__The_Y2K_bug)  
  
 [Dolgular kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Fakes_requirements)  
  
- [Fakes derlemeleri ekleyin](#AddFakes)  
  
- [ShimsContext kullanın](#ShimsContext)  
  
- [Dolgular ile testleri yazma](#WriteTests)  
  
  [Farklı türlerde yöntemleri için dolgular](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Shim_basics)  
  
- [Statik yöntemler](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_methods)  
  
- [(Tüm örnekler için) örnek yöntemleri](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_all_instances_)  
  
- [Örnek yöntemler (örneğin bir çalışma zamanı)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_one_instance_)  
  
- [Oluşturucular](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Constructors)  
  
- [Temel üyeler](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Base_members)  
  
- [Statik oluşturucular](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_constructors)  
  
- [Sonlandırıcılar](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Finalizers)  
  
- [Özel yöntemler](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Private_methods)  
  
- [Bağlama arabirimleri](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Binding_interfaces)  
  
  [Varsayılan davranışını değiştirme](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Changing_the_default_behavior)  
  
  [Algılama ortam erişir](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Detecting_environment_accesses)  
  
  [Eşzamanlılık](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Concurrency)  
  
  [Dolgu yöntemden asıl yöntemi çağırma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Calling_the_original_method_from_the_shim_method)  
  
  [Sınırlamalar](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Limitations)  
  
##  <a name="BKMK_Example__The_Y2K_bug"></a> Örnek: Y2K hata  
 1 Ocak 2000'in üzerinde özel durum oluşturan bir yöntem düşünelim:  
  
```csharp  
// code under test  
public static class Y2KChecker {  
    public static void Check() {  
        if (DateTime.Now == new DateTime(2000, 1, 1))  
            throw new ApplicationException("y2kbug!");  
    }  
}  
  
```  
  
 Bu yöntem test özellikle sorunlu programa bağımlı olduğundan dolayı `DateTime.Now`, bilgisayara bağlı bir yöntem kullanıcının saat, bir ortam bağımlı belirleyici yöntemi. Ayrıca, `DateTime.Now` statik bir özellik olduğundan bir saplama türü burada kullanılamaz. Bu sorun, birim testi yalıtımı sorunun belirtisi: ortamda bunların mantığına bağlı olduğundan, doğrudan veritabanına API çağrısı, web Hizmetleri ile iletişim kurmak ve benzeri programlar birim testi için sabit.  
  
 Burada Shim/dolgu türlerini kullanılması gereken budur. Shim/dolgu türlerini tüm .NET metotlarını bir kullanıcı tanımlı temsilciye sapma bir mekanizma sağlar. Kod tarafından oluşturulan Fakes oluşturucusu tarafından Shim/dolgu türlerini ve Shim/dolgu türlerini diyoruz, temsilciler, bunlar yeni yöntem uygulamaları belirtmek için kullanın.  
  
 Şu test Dolgu türü kullanma işlemini gösterir `ShimDateTime`DateTime.Now özel bir uygulamasını sağlamak için:  
  
```csharp  
//unit test code  
// create a ShimsContext cleans up shims   
using (ShimsContext.Create()  
    // hook delegate to the shim method to redirect DateTime.Now  
    // to return January 1st of 2000  
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);  
    Y2KChecker.Check();  
}  
  
```  
  
##  <a name="BKMK_Fakes_requirements"></a> Dolgular kullanma  
  
###  <a name="AddFakes"></a> Fakes derlemeleri ekleyin  
  
1.  Çözüm Gezgini'nde birim test projesinin genişletin **başvuruları**.  
  
    -   Visual Basic'te çalışıyorsanız, seçmelisiniz **tüm dosyaları göster** başvuru listesini görmek için Çözüm Gezgini araç.  
  
2.  Dolgular oluşturmak istediğiniz sınıf tanımlarını içeren derlemeyi seçin. DateTime dolgu oluşturmak istiyorsanız, örneğin System.dll seçin  
  
3.  Kısayol menüsünde **Fakes derlemesi Ekle**.  
  
###  <a name="ShimsContext"></a> ShimsContext kullanın  
 Shim/dolgu türlerini birim test çerçevesinde bulunmayan kullanırken, test kodu içindedir sarmalamanız gerekir bir `ShimsContext` , dolgular ömrünü denetlemek için. Biz bu yaramadı gerekiyorsa, dolgular AppDomain kapatılmasını en son. Oluşturmanın en kolay yolu bir `ShimsContext` statik kullanarak `Create()` aşağıdaki kodda gösterildiği gibi yöntemi:  
  
```csharp  
//unit test code  
[Test]  
public void Y2kCheckerTest() {  
  using(ShimsContext.Create()) {  
    ...  
  } // clear all shims  
}  
  
```  
  
 Her dolgu bağlamı düzgün bir şekilde silmek için önemlidir. Bir kural karşısında, her zaman çağrı `ShimsContext.Create` içine bir `using` kayıtlı dolgular, uygun temizleme emin olmak için deyimi. Örneğin, yerini alan bir test yöntemi için dolgu kaydetme `DateTime.Now` yöntemi her zaman döndüren bir temsilci ile ilk'ın Ocak 2000. Test yönteminde kayıtlı dolgu temizlemek unutursanız, test çalıştırmasının geri kalan her zaman döndürecekti ilk, Ocak 2000 DateTime.Now olarak değeri. Bu, suprising ve kafa karıştırıcı olabilir.  
  
###  <a name="WriteShims"></a> Dolgular ile bir test yazma  
 Test kodunuzda bir *sapma* sahtesini oluşturmak istediğiniz yöntem için. Örneğin:  
  
```csharp  
[TestClass]  
public class TestClass1  
{   
        [TestMethod]  
        public void TestCurrentYear()  
        {  
            int fixedYear = 2000;  
  
            using (ShimsContext.Create())  
            {  
              // Arrange:  
                // Detour DateTime.Now to return a fixed date:  
                System.Fakes.ShimDateTime.NowGet =   
                () =>  
                { return new DateTime(fixedYear, 1, 1); };  
  
                // Instantiate the component under test:  
                var componentUnderTest = new MyComponent();  
  
              // Act:  
                int year = componentUnderTest.GetTheCurrentYear();  
  
              // Assert:   
                // This will always be true if the component is working:  
                Assert.AreEqual(fixedYear, year);  
            }  
        }  
}  
  
```  
  
```vb  
<TestClass()> _  
Public Class TestClass1  
    <TestMethod()> _  
    Public Sub TestCurrentYear()  
        Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()  
            Dim fixedYear As Integer = 2000  
            ' Arrange:  
            ' Detour DateTime.Now to return a fixed date:  
            System.Fakes.ShimDateTime.NowGet = _  
                Function() As DateTime  
                    Return New DateTime(fixedYear, 1, 1)  
                End Function  
  
            ' Instantiate the component under test:  
            Dim componentUnderTest = New MyComponent()  
            ' Act:  
            Dim year As Integer = componentUnderTest.GetTheCurrentYear  
            ' Assert:   
            ' This will always be true if the component is working:  
            Assert.AreEqual(fixedYear, year)  
        End Using  
    End Sub  
End Class  
```  
  
 Dolgu sınıfı adları eklenmesiyle `Fakes.Shim` orijinal tür adının.  
  
 Dolgu iş ekleyerek *sapmalar* test altındaki uygulama koduna. Orijinal yönteme bir çağrı ortaya her yerde, Fakes sistem gerçek yöntemi çağırmak yerine dolgu kodunuzu adlı bir sapma gerçekleştirir.  
  
 Sapmalar oluşturulur ve çalışma zamanında silinmiş dikkat edin. Her zaman bir sapma içinde ömrünü oluşturmalısınız bir `ShimsContext`. Silindiğinde, etkin olduğu sırada oluşturduğunuz herhangi bir dolgu verileri kaldırılır. Bunu yapmanın en iyi yolu içinde olan bir `using` deyimi.  
  
 Fakes ad alanı var olmadığını belirten bir derleme hatası görebilirsiniz. Bu hata, bazen diğer derleme hataları olduğunda görüntülenir. Diğer hataları giderin ve onu kaybolur.  
  
##  <a name="BKMK_Shim_basics"></a> Farklı türlerde yöntemleri için dolgular  
 Shim/dolgu türlerini statik yöntemler veya kendi temsilcileri ile sanal olmayan yöntemler de dahil olmak üzere, herhangi bir .NET yöntemi değiştirmenizi sağlar.  
  
###  <a name="BKMK_Static_methods"></a> Statik yöntemler  
 Dolgular için statik yöntemler eklemek için özellikler bir dolgu türü yerleştirilir. Hedef yöntemin bir temsilciyi bağlamak için kullanılan bir ayarlayıcı her bir özellik vardır. Örneğin, bir sınıf verilen `MyClass` statik bir yöntem `MyMethod`:  
  
```csharp  
//code under test  
public static class MyClass {  
    public static int MyMethod() {  
        ...  
    }  
}  
```  
  
 Biz için dolgu ekleyebilirsiniz `MyMethod` her zaman 5 döndürür:  
  
```csharp  
// unit test code  
ShimMyClass.MyMethod = () =>5;  
```  
  
###  <a name="BKMK_Instance_methods__for_all_instances_"></a> (Tüm örnekler için) örnek yöntemleri  
 Benzer şekilde statik yöntemler için örnek yöntemler için tüm örnekleri için dolgu. Bu dolgular eklemek için özellikler, Karışıklığı önlemek için AllInstances adlı iç içe geçmiş bir tür içinde yerleştirilir. Örneğin, bir sınıf verilen `MyClass` bir örnek yöntemi ile `MyMethod`:  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 İçin dolgu ekleyebilirsiniz `MyMethod` 5, örnek bağımsız olarak her zaman döndürür:  
  
```csharp  
// unit test code  
ShimMyClass.AllInstances.MyMethod = () => 5;  
```  
  
 ShimMyClass oluşturulan tür yapısı şu kod gibi görünür:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public static class AllInstances {  
        public static Func<MyClass, int>MyMethod {  
            set {  
                ...  
            }  
        }  
    }  
}  
```  
  
 Fakes dikkat edin, çalışma zamanı örneği bu durumda temsilci ilk bağımsız değişkeni geçirir.  
  
###  <a name="BKMK_Instance_methods__for_one_instance_"></a> Örnek yöntemler (örneğin bir çalışma zamanı)  
 Örnek yöntemleri için çağrı alıcıda göre farklı temsilcileri tarafından da dolgu. Bu türün örneğini başına farklı davranışları sağlamak aynı örnek yöntemi sağlar. Bu dolgular ayarlanacak özellikler Dolgu türü örneği yöntemlerdir. Her örneklenen Dolgu türü, bir ham dolgulu türün örneğini ile de ilişkilidir.  
  
 Örneğin, bir sınıf verilen `MyClass` bir örnek yöntemi ile `MyMethod`:  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Dolgu MyMethod iki ilk her zaman 5 döndürür ve her zaman ikinci 10 döndürür ayarlayabilirsiniz:  
  
```csharp  
// unit test code  
var myClass1 = new ShimMyClass()  
{  
    MyMethod = () => 5  
};  
var myClass2 = new ShimMyClass { MyMethod = () => 10 };  
```  
  
 ShimMyClass oluşturulan tür yapısı şu kod gibi görünür:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public Func<int> MyMethod {  
        set {  
            ...  
        }  
    }  
    public MyClass Instance {  
        get {  
            ...  
        }  
    }  
}  
```  
  
 Gerçek dolgulu türün örneğini örnek özelliği erişilebilir:  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
var instance = shim.Instance;  
```  
  
 Genellikle yalnızca Dolgu türü olduğu gibi kullanabilmeniz için Dolgu türü ayrıca dolgulu türün örtük dönüştürmeleri vardır:  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
MyClass instance = shim; // implicit cast retrieves the runtime  
                         // instance  
```  
  
###  <a name="BKMK_Constructors"></a> Oluşturucular  
 Oluşturucular için gelecekteki nesnelere Shim/dolgu türlerini iliştirmek için de dolgu. Her Oluşturucu Dolgu türü statik yöntemde Oluşturucu olarak gösterilir. Örneğin, bir sınıf verilen `MyClass` tamsayı alan bir Oluşturucu ile:  
  
```csharp  
// code under test  
public class MyClass {  
    public MyClass(int value) {  
        this.Value = value;  
    }  
    ...  
}  
```  
  
 Değer alıcı çağrıldığında oluşturucuda değerinden bağımsız olarak her gelecekteki örnek -5 döndürür. böylece biz oluşturucunun Dolgu türü ayarlayın:  
  
```csharp  
// unit test code  
ShimMyClass.ConstructorInt32 = (@this, value) => {  
    var shim = new ShimMyClass(@this) {  
        ValueGet = () => -5  
    };  
};  
```  
  
 Her bir dolgu türü iki Oluşturucu sunan unutmayın. Varsayılan Oluşturucu, yeni bir örneğinde, bağımsız değişken yalnızca Oluşturucu dolgular içinde kullanılması gereken şekilde, bir dolgu örneğini alan oluşturucu sırasında gerekli olduğunda kullanılmalıdır:  
  
```csharp  
// unit test code  
public ShimMyClass() { }  
public ShimMyClass(MyClass instance) : base(instance) { }  
```  
  
 ShimMyClass oluşturulan tür yapısını followoing koda benzer:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass>  
{  
    public static Action<MyClass, int> ConstructorInt32 {  
        set {  
            ...  
        }  
    }  
  
    public ShimMyClass() { }  
    public ShimMyClass(MyClass instance) : base(instance) { }  
    ...  
}  
```  
  
###  <a name="BKMK_Base_members"></a> Temel üyeler  
 Temel üyeler dolgu özelliklerini temel türü için dolgu oluşturarak ve alt örneği temel dolgu sınıf oluşturucusuna bir parametre olarak geçirerek erişilebilir.  
  
 Örneğin, bir sınıf verilen `MyBase` bir örnek yöntemi ile `MyMethod` ve alt `MyChild`:  
  
```csharp  
public abstract class MyBase {  
    public int MyMethod() {  
        ...  
    }  
}  
  
public class MyChild : MyBase {  
}  
  
```  
  
 Dolgu ayarladık `MyBase` yeni bir oluşturarak `ShimMyBase` dolgu:  
  
```csharp  
// unit test code  
var child = new ShimMyChild();  
new ShimMyBase(child) { MyMethod = () => 5 };  
```  
  
 Alt Dolgu türü temel dolgu oluşturucusuna bir parametre olarak geçirildiğinde alt örneğine örtük olarak dönüştürülür unutmayın.  
  
 Oluşturulan tür yapısını ShimMyChild ve ShimMyBase aşağıdaki koda benzer:  
  
```csharp  
// Fakes generated code  
public class ShimMyChild : ShimBase<MyChild> {  
    public ShimMyChild() { }  
    public ShimMyChild(Child child)  
        : base(child) { }  
}  
public class ShimMyBase : ShimBase<MyBase> {  
    public ShimMyBase(Base target) { }  
    public Func<int> MyMethod  
    { set { ... } }  
}  
```  
  
###  <a name="BKMK_Static_constructors"></a> Statik oluşturucular  
 Shim/dolgu türlerini statik bir yöntemi açığa `StaticConstructor` bir türün statik Oluşturucu dolguya yeniden. Statik oluşturucular çalıştırıldığından emin olmak gereken yalnızca bir kez Dolgu türü herhangi bir üyesi erişmeden önce yapılandırılır.  
  
###  <a name="BKMK_Finalizers"></a> Sonlandırıcılar  
 Sonlandırıcılar Fakes içinde desteklenmez.  
  
###  <a name="BKMK_Private_methods"></a> Özel yöntemler  
 Fakes Kod Oluşturucusu yalnızca görünebilir türler imzası, yani parametre türleri ve dönüş türü görünür olan özel yöntem için dolgu özellikleri oluşturur.  
  
###  <a name="BKMK_Binding_interfaces"></a> Bağlama arabirimleri  
 Dolgulu türün bir arabirim uygular, Kod Oluşturucu tüm üyeleri aynı anda arabirimden bağlama izin veren bir yöntem yayar.  
  
 Örneğin, bir sınıf verilen `MyClass` uygulayan `IEnumerable<int>`:  
  
```csharp  
public class MyClass : IEnumerable<int> {  
    public IEnumerator<int> GetEnumerator() {  
        ...  
    }  
    ...  
}  
  
```  
  
 Biz uygulamaları dolgu `IEnumerable<int>` bağlama yöntemini çağırarak MyClass içinde:  
  
```csharp  
// unit test code  
var shimMyClass = new ShimMyClass();  
shimMyClass.Bind(new List<int> { 1, 2, 3 });  
  
```  
  
 ShimMyClass oluşturulan tür yapısı aşağıdaki koda benzer:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public ShimMyClass Bind(IEnumerable<int> target) {  
        ...  
    }  
}  
  
```  
  
##  <a name="BKMK_Changing_the_default_behavior"></a> Varsayılan davranışını değiştirme  
 Her bir üretilen Dolgu türü bir örneğini tutan `IShimBehavior` arabirimi aracılığıyla `ShimBase<T>.InstanceBehavior` özelliği. Bir istemci değil açıkça dolgu bir örnek üyesi çağırdığında davranışı kullanılır.  
  
 Davranışı açıkça ayarlı değil, özelliğinden döndürülen statik örneği kullanacak `ShimsBehaviors.Current` özelliği. Varsayılan olarak, bu özellik atan bir davranış döndürür. bir `NotImplementedException` özel durum.  
  
 Bu davranış ayarlayarak herhangi bir zamanda değiştirilebilir `InstanceBehavior` herhangi bir dolgu örneğini özelliği. Örneğin, aşağıdaki kod parçacığı dolgu, hiçbir şey yapmaz veya dönüş türünün varsayılan değerini döndüren bir davranış değişiklikleri — diğer bir deyişle, default(T):  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
//return default(T) or do nothing  
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;  
  
```  
  
 Davranış da genel olarak shimmed tüm örnekleri için değiştirilebilir `InstanceBehavior` özelliği açıkça ayarlanmamış statik ayarlayarak `ShimsBehaviors.Current` özelliği:  
  
```csharp  
// unit test code  
// change default shim for all shim instances  
// where the behavior has not been set  
ShimsBehaviors.Current =   
    ShimsBehaviors.DefaultValue;  
  
```  
  
##  <a name="BKMK_Detecting_environment_accesses"></a> Algılama ortam erişir  
 Belirli bir türün atayarak statik yöntemleri dahil olmak üzere tüm üyeleri bir davranış eklemek mümkündür `ShimsBehaviors.NotImplemented` statik özelliği için davranış `Behavior` karşılık gelen Dolgu türü:  
  
```csharp  
// unit test code  
// assigning the not implemented behavior  
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;  
// shorthand  
ShimMyClass.BehaveAsNotImplemented();  
  
```  
  
##  <a name="BKMK_Concurrency"></a> Eşzamanlılık  
 Shim/dolgu türlerini AppDomain tüm iş parçacıklarının uygulamak ve iş parçacığı benzeşimini yok. Eşzamanlılık destekleyen bir test Çalıştırıcısı'nı kullanmayı planlıyorsanız önemli bir olgu budur: Shim/dolgu türlerini içeren testler aynı anda çalıştırılamaz. Bu özellik, Fakes çalışma zamanı tarafından enfored değildir.  
  
##  <a name="BKMK_Calling_the_original_method_from_the_shim_method"></a> Dolgu yöntemden asıl yöntemi çağırma  
 Biz aslında yönteme geçirilen dosya adı doğrulama sonra metni dosya sistemine yazmak istediğinizi düşünelim. Bu durumda, biz dolgu yöntemi ortasında özgün yöntemini çağırmak istersiniz.  
  
 Bu sorunu çözmek için bir ilk yaklaşım bir temsilci kullanarak orijinal yönteme bir çağrı sarmaktır ve `ShimsContext.ExecuteWithoutShims()` şu kod gibi:  
  
```csharp  
// unit test code  
ShimFile.WriteAllTextStringString = (fileName, content) => {  
  ShimsContext.ExecuteWithoutShims(() => {  
  
      Console.WriteLine("enter");  
      File.WriteAllText(fileName, content);  
      Console.WriteLine("leave");  
  });  
};  
  
```  
  
 Başka bir yaklaşım, null, özgün yöntemini çağırın ve dolgu geri dolgu ayarlamaktır.  
  
```csharp  
// unit test code  
ShimsDelegates.Action<string, string> shim = null;  
shim = (fileName, content) => {  
  try {  
    Console.WriteLine("enter”);  
    // remove shim in order to call original method  
    ShimFile.WriteAllTextStringString = null;  
    File.WriteAllText(fileName, content);  
  }  
  finally  
  {  
    // restore shim  
    ShimFile.WriteAllTextStringString = shim;  
    Console.WriteLine("leave");  
  }  
};  
// initialize the shim  
ShimFile.WriteAllTextStringString = shim;  
  
```  
  
##  <a name="BKMK_Limitations"></a> Sınırlamaları  
 Dolgular, .NET temel sınıf kitaplığı'ndan tüm türlerde kullanılamaz **mscorlib** ve **sistem**.  
  
## <a name="external-resources"></a>Dış kaynaklar  
  
### <a name="guidance"></a>Kılavuz  
 [Visual Studio 2012 – bölüm 2 ile sürekli teslimat testi: birim testi: iç testler](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Microsoft Fakes ile Test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)   
 [Peter Provost'ın blog: Visual Studio 2012 dolgular](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)   
 [Video (1 saat 16): Visual Studio 2012'de beklemediğiniz test edilebilir kod Fakes ile test etme](http://go.microsoft.com/fwlink/?LinkId=261837)



