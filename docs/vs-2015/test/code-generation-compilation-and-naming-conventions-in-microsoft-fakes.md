---
title: Kod oluşturma, derleme ve Microsoft Fakes adlandırma kuralları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 20221de4-2a9e-4787-b99a-b5855bb90872
caps.latest.revision: 18
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1de284c8d4fdfe5cb84a474641b880590c2094aa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895333"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu Fakes kod oluşturma ve derleme seçeneklerini ve sorunlarını açıklar ve üretilen Fakes türleri, üyeler ve parametrelerini adlandırma kurallarını açıklar.  
  
 **Gereksinimler**  
  
-   Visual Studio Enterprise  
  
##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 [Kod oluşturma ve derleme](#BKMK_Code_generation_and_compilation)  
  
- [Koçanların kod oluşturma yapılandırma](#BKMK_Configuring_code_generation_of_stubs) • [tür filtreleme](#BKMK_Type_filtering) • [somut sınıflar ve sanal yöntemleri Koçan yapma](#BKMK_Stubbing_concrete_classes_and_virtual_methods) • [iç türleri](#BKMK_Internal_types) • [ Derleme sürelerini en iyi duruma getirme](#BKMK_Optimizing_build_times) • [derleme adı Çarpışmasından](#BKMK_Avoiding_assembly_name_clashing)  
  
  [Fakes adlandırma kuralları](#BKMK_Fakes_naming_conventions)  
  
- [Dolgu ve Koçan türleri adlandırma kuralları yazın](#BKMK_Shim_type_and_stub_type_naming_conventions) • [Shim temsilci özelliği veya stub temsilci alanı adlandırma kuralları](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions) • [parametre türü adlandırma kuralları](#BKMK_Parameter_type_naming_conventions) • [özyinelemeli kuralları](#BKMK_Recursive_rules)  
  
  [Dış Kaynaklar](#BKMK_External_resources)  
  
- [Kılavuz](#BKMK_Guidance)  
  
##  <a name="BKMK_Code_generation_and_compilation"></a> Kod oluşturma ve derleme  
  
###  <a name="BKMK_Configuring_code_generation_of_stubs"></a> Koçanların kod oluşturma yapılandırma  
 Koçan türler oluşturulmasını .fakes dosya uzantısına sahip bir XML dosyasında yapılandırılır. Fakes framework yapı işleminde özel MSBuild görevleri ile tümleştirir ve bu dosyaları derleme sırasında algılar. Fakes Kod Oluşturucusu bir derleme içine Koçan türleri derler ve projeye başvuruyu ekler.  
  
 Aşağıdaki örnekte, FileSystem.dll içinde tanımlanan Koçan türleri gösterilmektedir:  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
    <Assembly Name="FileSystem"/>  
</Fakes>  
  
```  
  
###  <a name="BKMK_Type_filtering"></a> Tür filtreleme  
 Filtreler heline getirilmesi gereken hangi türleri sınırlamak için .fakes dosyasında ayarlanabilir. Temizle, Ekle, Kaldır öğelerini seçili türlerinin listesini oluşturmak için StubGeneration öğesinin altındaki sınırsız sayıda ekleyebilirsiniz.  
  
 Örneğin, bu .fakes dosya türleri System ve System.IO ad alanları altında için saplamalar oluşturur, ancak System içinde "Handle" içeren her türü dışlar:  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
  <Assembly Name="mscorlib" />  
  <!-- user code -->  
  <StubGeneration>  
    <Clear />  
    <Add Namespace="System!" />  
    <Add Namespace="System.IO!"/>  
    <Remove TypeName="Handle" />  
  </StubGeneration>  
  <!-- /user code -->  
</Fakes>  
```  
  
 Filtre dizeleri nasıl yapılması gerektiğini tanımlamak için basit bir dil bilgisi kullanın:  
  
-   Filtreleri, varsayılan olarak büyük küçük harf duyarsız; eşleşen alt dizenin filtreleri uygulayın:  
  
     `el` "hello" ile eşleşir  
  
-   Ekleme `!` filtre sonuna kadar kesin bir büyük küçük harfe duyarlı eşleşme yapar:  
  
     `el!` "hello" ile eşleşmiyor  
  
     `hello!` "hello" ile eşleşir  
  
-   Ekleme `*` filtre sonuna kadar kolaylaştırır eşleşecek dize öneki:  
  
     `el*` "hello" ile eşleşmiyor  
  
     `he*` "hello" ile eşleşir  
  
-   Noktalı virgülle ayrılmış bir liste içinde birden çok filtre ayırım yaparak birleştirilebilir.  
  
     `el;wo` "hello" ve "world" ile eşleşir  
  
###  <a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a> Somut sınıflar ve sanal yöntemleri Koçan yapma  
 Varsayılan olarak, Koçan türleri korumalı olmayan tüm sınıflar için oluşturulur. .fakes yapılandırma dosyasıyla sınıflarının soyut Koçan türlerini kısıtlamak mümkündür:  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
  <Assembly Name="mscorlib" />  
  <!-- user code -->  
  <StubGeneration>  
    <Types>  
      <Clear />  
      <Add AbstractClasses="true"/>  
    </Types>  
  </StubGeneration>  
  <!-- /user code -->  
</Fakes>  
```  
  
###  <a name="BKMK_Internal_types"></a> Dahili türler  
 Fakes Kod Oluşturucusu Shim/dolgu türlerini oluşturmak ve saplama türleri için üretilen Fakes derlemeye görülebilen türler. Shimmed derleme dahili türlerini Fakes ve test derlemeniz görünür hale getirmek için ekleme <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini shimmed derleme kodu, oluşturulan Fakes derlemesine ve test derlemesine görünürlük sağlar. Örnek buradadır:  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes")]  
[assembly: InternalsVisibleTo("FileSystem.Tests")]  
```  
  
 **Kesin adlandırılmış derlemelerin iç türleri**  
  
 Shimmed derleme kesin şekilde adlandırıldığında ve derlemenin iç türlerine erişmek isterseniz:  
  
- Hem test derlemeniz hem de Fakes derlemeniz kesin adlandırılmış olmalıdır.  
  
- Test ve Fakes derlemesinin ortak anahtarlarını eklemelisiniz **Internalsvisibletoattribute** shimmed derlemelerdeki öznitelikleri. Shimmed derleme kesin şekilde adlandırıldığında dolgu kullanılan derleme koduna bizim örnek öznitelikleri nasıl görüneceğini aşağıda verilmiştir:  
  
  ```csharp  
  // FileSystem\AssemblyInfo.cs  
  [assembly: InternalsVisibleTo("FileSystem.Fakes",  
      PublicKey=<Fakes_assembly_public_key>)]  
  [assembly: InternalsVisibleTo("FileSystem.Tests",  
      PublicKey=<Test_assembly_public_key>)]  
  ```  
  
  Shimmed derleme güçlü adlandırılırsa Fakes framework otomatik olarak oluşturulan Fakes derlemeleri imzalar. Test derlemesi strong oturum gerekir. Bkz: [oluşturma ve kullanma tanımlayıcı adlandırılmış derlemeler](http://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).  
  
  Fakes çerçevesi, bu kod parçacığı eklemek için bir başlangıç noktası olarak kullanabilmeniz için oluşturulan tüm derlemeleri imzalamak için aynı anahtarı kullanır. **InternalsVisibleTo** özniteliğini shimmed derleme kodunuza fakes derlemesi.  
  
```csharp  
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]  
```  
  
 Fakes derlemesi için farklı bir ortak anahtar belirtebilirsiniz, bir anahtar gibi tam yolunu belirterek shimmed derleme için oluşturduğunuz **.snk** olarak alternatif anahtarı içeren dosyayı `KeyFile` özniteliği değeri `Fakes` \\ `Compilation` öğesinin **.fakes** dosya. Örneğin:  
  
```xml  
<-- FileSystem.Fakes.fakes -->  
<Fakes ...>  
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />  
</Fakes>  
  
```  
  
 Daha sonra diğer ortak anahtarını kullanmak zorunda **.snk** shimmed derleme kodunda Fakes derlemesinin Internalvisibleto özniteliğinin ikinci parametre olarak dosya:  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes",  
    PublicKey=<Alternate_public_key>)]  
[assembly: InternalsVisibleTo("FileSystem.Tests",  
    PublicKey=<Test_assembly_public_key>)]  
```  
  
 Yukarıdaki değerleri örnekte `Alternate_public_key` ve `Test_assembly_public_key` aynı olabilir.  
  
###  <a name="BKMK_Optimizing_build_times"></a> Derleme zamanlarını optimize etme  
 Fakes derlemelerinin derlemesi yapım sürenizi önemli ölçüde artırabilir. Ayrı merkezi bir proje içinde .NET System derlemeleri için Fakes derlemeleri ve üçüncü taraf derlemeler oluşturarak derleme zamanını en aza indirebilirsiniz. Bu tür derlemeler makinenizde nadiren değiştiğinden, oluşturulan Fakes derlemeleri diğer projelerde yeniden kullanabilirsiniz.  
  
 Birim test projelerinizden proje klasöründeki FakesAssemblies altında yerleştirilen derlenmiş Fakes derlemelerden açıkça başvuru basit sürebilir.  
  
1.  Test projelerinizle eşleşen .NET çalışma zamanı sürümünü ile yeni bir sınıf kitaplığı oluşturun. Şimdi fakes.prebuild diye çağıralım. Class1.cs dosyasını projeden gerekli kaldırın.  
  
2.  Tüm sistem başvuru ekleyin ve üçüncü taraf derlemeler için Fakes gerekir.  
  
3.  Her derleme için bir .fakes dosyası ekleyin ve oluşturun.  
  
4.  Test projenizden  
  
    -   Fakes çalışma zamanı DLL başvuru sahip olduğunuzdan emin olun:  
  
         C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll  
  
    -   İçin oluşturduğunuz her derleme için Fakes, projenizin Fakes.Prebuild\FakesAssemblies klasöründe karşılık gelen DLL dosyasına bir başvuru ekleyin.  
  
###  <a name="BKMK_Avoiding_assembly_name_clashing"></a> Derleme adı çarpışmasından  
 Bir ekip ortamında, tüm yapı çıkışları tek bir dizin içinde birleştirilir. Fakes kullanan birden fazla proje söz konusu olduğunda, farklı sürümden Fakes derlemeler birbirini geçersiz kılma meydana getirebilir. Örneğin, .NET Framework 2.0 mscorlib.dll TestProject1 fakes ve için .NET Framework 4 mscorlib.dll mscorlib olarak hem de verir TestProject2 fakes. Fakes.dll Fakes derlemesi.  
  
 Bu sorunu önlemek için Fakes, .fakes dosyaları eklerken proje-olmayan başvurular için sürüm nitelikli Fakes derleme adı otomatik olarak oluşturmalısınız. Fakes derleme adı oluştururken bir sürüm nitelikli Fakes derleme adı bir sürüm numarası gömer:  
  
 Bir derleme MyAssembly ve sürüm 1.2.3.4, Fakes derleme adı MyAssembly.1.2.3.4.fakes'dir.  
  
 .Fakes içindeki derleme öğesinin Version özniteliğini düzenleyerek bu sürümü kaldırın ya da değiştirin:  
  
```xml  
attribute of the Assembly element in the .fakes:  
<Fakes ...>  
  <Assembly Name="MyAssembly" Version="1.2.3.4" />  
  ...  
</Fakes>  
  
```  
  
##  <a name="BKMK_Fakes_naming_conventions"></a> Fakes adlandırma kuralları  
  
###  <a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a> Dolgu ve Koçan türleri adlandırma kuralları yazın  
 **Ad Alanları**  
  
- . Fakes sonekini ad alanına eklenir.  
  
   Örneğin, `System.Fakes` ad alanı System ad alanının Shim/dolgu türlerini içerir.  
  
- Global.Fakes boş ad alanını dolgu türünü içerir.  
  
  **Tür adları**  
  
- Dolgu/Shim öneki Dolgu türü adı yapılandırmak için tür adına eklenir.  
  
   Örneğin, ShimExample Example türünün shim türüdür.  
  
- Stub öneki stub türü adı yapılandırmak için tür adına eklenir.  
  
   Örneğin, Stubıexample IExample türünün stub türüdür.  
  
  **Tür argümanları ve iç içe tür yapıları**  
  
- Genel tür argümanları kopyalanır.  
  
- İç içe tür yapıları shim türleri için kopyalanır.  
  
###  <a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a> Adlandırma kuralları shim temsilci özelliği veya stub temsilci alanı  
 **Temel kurallar** alanının adlandırma, boş bir isimden başlama:  
  
- Yöntem adı eklenir.  
  
- Yöntem adı açık arabirim uygulaması ise noktalar kaldırılır.  
  
- Yöntem genelse, `Of` *n* nereden eklenir *n* genel yöntem bağımsız değişken sayısı.  
  
  **Özel yöntem adları** gibi özellik alıcı veya ayarlayıcılar aşağıdaki tabloda açıklandığı gibi kabul edilir.  
  
|Yöntem ise...|Örnek|Yöntem adı eklenmiş|  
|-------------------|-------------|--------------------------|  
|A **Oluşturucusu**|`.ctor`|`Constructor`|  
|Statik **Oluşturucusu**|`.cctor`|`StaticConstructor`|  
|Bir **erişimci** yöntemiyle iki kısımdan adı "_" (örneğin, özellik alıcıları) tarafından ayrılmış|*kind_name* (ortak büyük/küçük harf, ancak ECMA tarafından zorlanan değil)|*NameKind*, burada her iki parçayı büyük harfli takas ve|  
||Özelliğin alıcısı `Prop`|`PropGet`|  
||Özelliğin Ayarlayıcısı `Prop`|`PropSet`|  
||Olay ekleyici|`Add`|  
||Olay kaldırıcısı|`Remove`|  
|Bir **işleci** iki bölümden oluşur|`op_name`|`NameOp`|  
|Örneğin: + işleci|`op_Add`|`AddOp`|  
|İçin bir **dönüştürme işleci**, dönüş türü eklenir.|`T op_Implicit`|`ImplicitOpT`|  
  
 **Notlar**  
  
-   **Alıcılar ve ayarlayıcılar Dizin oluşturucuların** özelliğine benzer şekilde değerlendirilir. Bir dizin oluşturucu için varsayılan ad `Item`.  
  
-   **Parametre türü** adları dönüştürülür ve birleştirilir.  
  
-   **Dönüş türü** aşırı yükleme belirsizliği olmadıkça göz ardı edilir. Bu durumda, dönüş türü adının sonuna eklenir  
  
###  <a name="BKMK_Parameter_type_naming_conventions"></a> Parametre türü adlandırma kuralları  
  
|Verilen|Eklenen dizedir...|  
|-----------|-------------------------|  
|A **türü**`T`|T<br /><br /> Ad alanı, iç içe yapı ve genel tikler iptal bırakılır.|  
|Bir **çıkış parametresi**`out T`|`TOut`|  
|A **ref parametresi** `ref T`|`TRef`|  
|Bir **dizi türü**`T[]`|`TArray`|  
|A **çok boyutlu dizi** türü `T[ , , ]`|`T3`|  
|A **işaretçi** türü `T*`|`TPtr`|  
|A **genel tür**`T<R1, …>`|`TOfR1`|  
|A **genel tür bağımsız değişkeni** `!i` türü `C<TType>`|`Ti`|  
|A **genel metot argümanı** `!!i` yöntemi `M<MMethod>`|`Mi`|  
|A **iç içe türü**`N.T`|`N` , ardından eklenir `T`|  
  
###  <a name="BKMK_Recursive_rules"></a> Özyinelemeli kurallar  
 Aşağıdaki kurallar özyinelemeli olarak uygulanır şunlardır:  
  
-   Fakes C# kullandığı için Fakes derlemeleri oluşturmak için bir geçersiz C# simgesi üretecek karakterlerden kaçırılmışsa "_" (alt çizgi).  
  
-   Bildirim türü herhangi bir üyesi ile elde edilen adı çakışıyor, 01 ile başlayan iki basamaklı sayaç ekleyerek bir numaralandırma şeması kullanılır.  
  
##  <a name="BKMK_External_resources"></a> Dış Kaynaklar  
  
###  <a name="BKMK_Guidance"></a> Kılavuzu  
 [Visual Studio 2012 – bölüm 2 ile sürekli teslimat testi: birim testi: iç testler](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Microsoft Fakes ile Test Edilen Kodu Yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)



