---
title: Yerel nesnelerin özel görünümlerini oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- natvis
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff03e5e07c07b4516009c7606f8a8ea183c57298
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732491"
---
# <a name="create-custom-views-of-native-objects"></a>Yerel nesnelerin özel görünümlerini oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Natvis çerçevesi Visual Studio hata ayıklayıcı değişken pencerelerinde yerel türleri görüntülenme şeklini özelleştirmenizi sağlar (örneğin, **Watch**, **Yereller**, ve **veriipuçları** windows.  

 Natvis yerini **autoexp.dat** Visual Studio ve teklifler XML sözdizimi, daha iyi tanılama, sürüm oluşturma ve birden çok dosya desteği önceki sürümlerinde kullanılan dosya.  

> [!NOTE]
>  Natvis çerçevesi için görselleştirmeler kullanılamaz olduğunda:  
> 
> - Hata ayıklayıcı türü ayarlanan bir C++ Windows Masaüstü proje hata ayıklama **karma**.  
>   -   Windows masaüstü uygulamasında yönetilen uyumluluk modu karışık modda hata ayıklama yapıyorsunuz (**Araçlar / Seçenekler / hata ayıklama / genel / yönetilen Uyumluluk modunu kullan**).  
>   -   Yerel uyumluluk modunda bir Windows masaüstü uygulamasında hata ayıklama (**Araçlar / Seçenekler / hata ayıklama / genel / yerel Uyumluluk modunu kullan**).  

##  <a name="BKMK_Why_create_visualizations_"></a> Neden Natvis görsel oluşturulsun mu?  
 Natvis çerçevesi, geliştiricilerin bunları kolayca hata ayıklama sırasında görebilmek için oluşturduğunuz, türleri için görselleştirme kuralları oluşturmak için kullanabilirsiniz.  

 Örneğin, aşağıdaki görüntüde türünde bir değişken gösterilmektedir [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) görüntülenen hata ayıklayıcıda uygulanan özel görselleştirmeler.  

 ![TextBox varsayılan görselleştirme](../debugger/media/dbg-natvis-textbox-default.png "DBG_NATVIS_TextBox_Default")  

 Vurgulanmış satıra gösterir `Text` özelliği `TextBox` sınıfı. Karmaşık sınıf hiyerarşisi bu değeri bulmak zor hale getirir; Üstelik, hata ayıklayıcı textbox içinde tutulan dizeyi görememiz nesne tarafından kullanılan özel bir dize türünü nasıl yorumlayacağını bilmez.  

 Aynı `TextBox` özel görselleştirme kuralları uygulandığında çok daha basit n değişken penceresinde görünür. Sınıfın önemli üyeleri birlikte görüntülenebilir ve hata ayıklayıcı özel dize türünün temel dize değerini gösterir.  

 ![Metin veri Görselleştirici kullanarak](../debugger/media/dbg-natvis-textbox-visualizer.png "DBG_NATVIS_TextBox_Visualizer")  

##  <a name="BKMK_Using_Natvis_files"></a> Natvis dosyalarını kullanma  
 .natvis dosyaları, .natvis uzantılı XML dosyalarıdır. Şema tanımlanan **%VSINSTALLDIR%\Xml\Schemas\natvis.xsd**.  

 .Natvis dosyasının temel yapısı bir veya daha fazla `Type` öğeleri, burada her `Type` öğesi tam adı belirtilen bir tür için bir görselleştirme girdisini temsil eder `Name` özniteliği.  

```xml  

<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
  <Type Name="MyNamespace::CFoo">  
    .  
    .  
  </Type>  

  <Type Name="...">  
    .  
    .  
  </Type>  
</AutoVisualizer>  
```  

 Visual Studio sağlayan birkaç .natvis dosyası **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers** klasör. Bu dosyalar birçok ortak tür için görselleştirme kuralları içerir ve yeni türleri için görsel öğeler yazarken örnek olarak hizmet verebilir.  

## <a name="adding-natvis-files-to-your-projects"></a>.Natvis dosyası, projelere ekleme  
 .Natvis dosyaları herhangi bir C++ projesine ekleyebilirsiniz.  

 Açık bir C++ projesi ile yeni bir .natvis dosyası eklemek için proje düğümünü seçin. **Çözüm Gezgini**, tıklatıp **Ekle / yeni öğe / Visual C++ / yardımcı programı / hata ayıklayıcı görselleştirme dosyası (.natvis)**. Hata ayıklayıcı Natvis dosyalarını C++ projeleri otomatik olarak yüklenecektir. Varsayılan olarak, proje tarafından oluşturulan .pdb dosyasına Natvis dosyaları projenize eklenir. Bu, bu proje tarafından oluşturulan ikili hatalarını ayıklıyorsanız, açık proje yoksa bile hata ayıklayıcı Natvis dosyası .pdb yüklendiğini anlamına gelir. .Natvis dosyasında .pdb dahil edilecek .natvis dosyası istemiyorsanız sağ **Çözüm Gezgini**ve **yapılandırma özellikleri** penceresi kümesi **yapı tarafından çıkarıldı**  için **Evet**.  

 Natvis dosyalarını kullanarak Visual Studio yapılan değişiklikler dosyayı kaydettiğinizde etkili otomatik olarak hata ayıklama sırasında yaptığınız düzenleme önerilir. Geliştirilmiş bir düzenleme deneyimi de IntelliSense'de alın.  

 Bir .pdb yüklenen Natvis dosyaları yalnızca pdb başvurduğu modüldeki türler için geçerlidir. Örneğin, adlı bir tür için bir giriş Module1.pdb tanımlar `Test`, yalnızca uygulanan bu giriş **Test** Module1.dll sınıfta. Başka bir modül adlı bir sınıf tanımlıyorsa **Test**, Module1.pdb'ın natvis girişi için uygulanmaz.  

##  <a name="BKMK_natvis_location"></a> .Natvis dosyaları dağıtma  
 .natvis dosyası yalnızca bir Visual Studio projesinde oluşturduğunuz türleri için geçerliyse, herhangi bir şey gerekmez; .natvis .pdb dahildir. Birden çok projeye uygulamak istediğiniz, ancak .natvis dosyaları, kullanıcı dizininizin veya sistem dizini ekleyin olabilir.  

 İçinde hangi .natvis dosyaları değerlendirilme sırasını aşağıdaki gibidir:  

1.  (yüklü bir proje içinde aynı adda bir dosya mevcut değilse) hata ayıklaması yaptığınız bir .pdb katıştırılmış .natvis dosyaları  

2.  yüklenen bir C++ projeleri veya bir üst düzey çözüm öğesi bir parçası olan .natvis dosyaları. Bu sınıf kitaplıkları dahil olmak üzere tüm yüklenmiş C++ projeleri içerir, ancak diğer diller projelerin içermez (örneğin, bir .natvis dosyası bir C# projesi yüklenemiyor). Yürütülebilir projeleri için kullanılabilir hiç C++ projesi olduğundan, bir .pdb mevcut olmayan herhangi bir .natvis dosyalarını barındırmak için çözüm öğeleri kullanmanız gerekir.  

3.  Kullanıcıya özgü natvis dizini (**%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers**  

4.  Sistem genelinde Natvis dizini (**%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers**). Visual Studio ile yüklenen .natvis dosyaları burada kopyalanır budur. Yönetici izinleriniz varsa, bu dizin için diğer dosyaları ekleyebilirsiniz.  

## <a name="modifying-natvis-files-while-debugging"></a>Hata ayıklama sırasında .natvis dosyasının değiştirilmesini  
 IDE'de bir .natvis dosyası dahil olduğu projenin hata ayıklama sırasında değiştirebilirsiniz. (İle hata ayıklama Visual Studio'nun aynı örneği kullanarak) IDE içindeki dosyasını açın, değiştirin ve dosyayı kaydedin. Dosyanın kaydedilmiş hemen sonra **Watch** ve **Yereller** windows değişikliği yansıtacak şekilde güncelleştirilmesi. .Natvis dosyası IDE dışında değiştirirseniz, değişiklikler otomatik olarak etkili olmaz. Windows'u güncelleştirmek için değerlendirebilirsiniz **.natvisreload** komutunu **Watch** penceresi. Bu değişikliklerin etkili hata ayıklama oturumu başlatmadan neden olur.  

 Ayrıca ekleme veya silme .natvis dosyaları bir çözüme hata ayıklaması yaptığınız ve Visual Studio ekleyebilir veya ilgili görselleştirmeler kaldırın.  

 İçinde bir .pdb katıştırılır, hata ayıklarken bir .natvis dosyası değiştirilemiyor.  

 Kullanım **.natvisreload** natvis dosyası (örneğin, kaynak denetimine iade edildi ve o birisi başka dosyada yapılan son değişikliklerini çekmek istediğiniz varsa) daha yeni bir sürümüne yükselttiğiniz sırada komutu. Visual Studio xml Düzenleyicisi'ni kullanarak natvis dosyalarını Düzenle önerilir.  

##  <a name="BKMK_Expressions_and_formatting"></a> İfadeler ve biçimlendirmeler  
 Natvis görselleştirmeler, görüntülenecek veri öğelerini belirtmek için C++ ifadeler kullanın. Geliştirmeleri ve şurada açıklanan hata ayıklayıcısındaki C++ ifadelerinin sınırlamalarına ek [bağlam işleci (C++)](../debugger/context-operator-cpp.md), aşağıdaki farklılıklara olmalıdır:  

- Natvis ifadeler, görselleştirilmekte olan nesnedeki değil geçerli yığın çerçevesi bağlamında değerlendirilir. Örneğin kullanırsanız `x` Natvis ifadesinde, bu adlı alanı ifade eder `x` adlı değil yerel bir değişkene görselleştirilen nesne içinde `x` şu anda yürütülen işlevdeki. Genel değişkenlere erişebilirsiniz ancak Natvis ifadeleri içindeki yerel değişkenler erişemez.  

- Natvis ifadeler İşlev değerlendirmesi veya yan efektlere izin vermez. Bu işlev çağrılarının ve atama işleçlerinin yoksayıldığı anlamına gelir. Çünkü [hata ayıklayıcı iç işlevleri](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) ücretsiz, bunlar serbestçe çağrılabilir herhangi bir Natvis ifadesinden diğer işlev çağrılarına izin verilmese yan etkisi olan.  

  Bir ifade bir değişken penceresinde nasıl görüntüleneceğini denetlemek için açıklanan biçim belirleyicilerinin herhangi kullanabilirsiniz [biçim belirticileri](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) bölümünü [C++ içindeki Biçim belirticileri](../debugger/format-specifiers-in-cpp.md) konu. Sanallaştırma girişi dahili olarak Natvis tarafından gibi kullanıldığında biçim belirticileri göz ardı edilir Not `Size` Arrayıtems genişletme ifade.  

## <a name="natvis-views"></a>Natvis görünümleri  
 Natvis görünümleri herhangi bir türü birden fazla yolla görmenize olanak sağlar. Örneğin, adlı bir görünüm tanımlayabilirsiniz **basit** , bir tür basitleştirilmiş bir görünümünü sağlar. Örneğin, bir görselleştirme işte `std::vector`:  

```xml  
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  

 `DisplayString` Ve `ArrayItems` öğeleri, varsayılan ve basit görünümlerinde kullanılır ancak `[size]` ve `[capacity]` öğeleri basit görünümden hariç tutulur. Kullanabileceğiniz **, Görünüm** biçim belirticisi diğer bir görünümünü belirtmek için. İçinde **Watch** penceresinde belirttiğiniz basit görünüm olarak **vec,view(simple)**:  

 ![Basit Görünüm ile İzleme penceresi](../debugger/media/watch-simpleview.png "SimpleView izleyin")  

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis hataları tanılama  
 Natvis Tanılama, sözdizimi ve ayrıştırma hataları için kullanabilirsiniz. Hata ayıklayıcısı bir görselleştirme girişinde hatalarla karşılaştığında, hataları ve görüntüler türü ham biçimiyle göz ardı eder veya başka bir uygun görselleştirme seçer. Belirli bir görselleştirme girişinin neden yoksayıldığını anlamak ve arka plandaki hataların neler olduğunu görmek için Natvis tanılamayı etkinleştirebilirsiniz **Araçlar / Seçenekler / hata ayıklama / çıkış penceresi / Natvis tanılama iletileri (yalnızca C++)** seçeneği. Hataları görüntülenebilir **çıkış** penceresi.  

##  <a name="BKMK_Syntax_reference"></a> Natvis söz dizimi başvurusu  

###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer öğesi  
 `AutoVisualizer` Öğesi .natvis dosyasının kök düğümüdür ve ad alanını içeren `xmlns:` özniteliği.  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

###  <a name="BKMK_Type"></a> Type öğesi  
 Bir temel tür şöyle görünür:  

```xml  
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  

```  

 Bu belirtir:  

1. Bu görselleştirme hangi tür için kullanılmalıdır ( `Type Name` özniteliği).  

2. Bu türdeki bir nesnenin değeri aşağıdaki gibi görünmelidir ( `DisplayString` öğesi).  

3. Türün üyeleri, kullanıcı, bir değişken penceresinde genişletir gibi görünmelidir ( `Expand` düğümü).  

   **Şablonlu sınıflar** `Name` özniteliği `Type` öğe kabul ettiği bir yıldız işareti `*` şablonlu sınıf adları için kullanılabilecek bir joker karakter olarak:  

```xml  
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  

```  

 Bu örnekte, nesnenin olup aynı görselleştirmeyi kullanılacak bir `CAtlArray<int>` veya `CAtlArray<float>`. İçin bir özel görselleştirme girdisi varsa bir `CAtlArray<float>` genel olana kıyasla öncelik kazanır.  

 Şablon parametreleri makroları $t1, $t2, kullanarak görselleştirme girişinde başvurulabilir vb. olduğunu unutmayın. Bu makroların örneklerini bulmak için Visual Studio ile birlikte gelen .natvis dosyalarına bakın.  

####  <a name="BKMK_Visualizer_type_matching"></a> Görselleştirici türü eşleşmesi  
 Daha sonra doğrulamak bir görselleştirme girdisi başarısız olursa, bir sonraki kullanılabilir görselleştirme kullanılır.  

#### <a name="inheritable-attribute"></a>Devralınabilir özniteliği  
 Bir görselleştirme yalnızca bir taban türü veya bir taban türü ve isteğe bağlı tüm türetilmiş türleri için geçerli olup olmadığını belirtebilirsiniz `Inheritable` özniteliği. Aşağıda, görselleştirme yalnızca geçerli `BaseClass` türü:  

```xml  
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

 Varsayılan değer olan `Inheritable` olduğu `true`.  

#### <a name="priority-attribute"></a>Öznitelik önceliği  
 `Priority` Özniteliği içinde alternatif tanımları ayrıştırmak bir tanımı başarısız olursa sırayla kullanılacağını belirtir. Olası değerleri `Priority` şunlardır: `Low`, `MediumLow`,`Medium`, `MediumHigh`, ve `High`, ve varsayılan değer `Medium`.  

 Öncelik özniteliğine yalnızca farklı dosya arasında değil aynı .natvis dosyası içindeki öncelikler ayırt etmek için kullanılmalıdır.  

 Aşağıdaki örnekte, biz öncelikle bir 2015 STL eşleşen girdiyi ayrıştırır ve ayrıştırmak başarısız olursa, diğer giriş STL 2013 sürümü için kullanacağız:  

```xml  
<!-- VC 2013 -->  
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">  
     <DisplayString>{_Callee}</DisplayString>  
    <Expand>  
        <ExpandedItem>_Callee</ExpandedItem>  
    </Expand>  
</Type>  

<!-- VC 2015 -->  
<Type Name="std::reference_wrapper&lt;*&gt;">  
    <DisplayString>{*_Ptr}</DisplayString>  
    <Expand>  
        <Item Name="[ptr]">_Ptr</Item>  
    </Expand>  
</Type>  
```  

####  <a name="BKMK_Versioning"></a> Sürüm öğesi  
 Kullanım `Version` kapsam görselleştirmeleri belirli modüller ve ad çakışmalarının sürümlerine öğesine indirilebilmesi ve farklı görselleştirme türleri farklı sürümleri için kullanılabilir. Örneğin:  

```xml  
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

 Bu örnekte, görselleştirme için yalnızca geçerli `DirectUI::Border` türü bulundu `Windows.UI.Xaml.dll` sürüm 1.5 1.0. Ne zaman uygulanmamış sürüm öğeleri eklenirken görselleştirme girişini belirli modülü ve sürüme kapsamları ve yanlışlıkla uyuşmazlıkları azaltır, ancak bir tür farklı modüller tarafından kullanılan ortak bir üstbilgi dosyasında tanımlandıysa sürümü tutulan görselleştirmenin olduğunu unutmayın. türü Belirtilen modül içinde değil.  

#### <a name="optional-attribute"></a>İsteğe bağlı öznitelik  
 `Optional` Öznitelik herhangi bir düğümde görünebilir. Ayrıştırmak isteğe bağlı bir düğüm içindeki herhangi bir alt ifade başarısız olursa, o düğümde göz ardı edilir, ancak geri kalan'Type öğesinin hala geçerli olduğunu. Aşağıdaki türde `[State]` olmayan-isteğe bağlıdır, ancak `[Exception]` isteğe bağlıdır.  Olması durumunda başka bir deyişle `MyNamespace::MyClass` _ adlı bir alan içeren`M_exceptionHolder`, yine de her ikisi de olur `[State]` düğüm ve `[Exception]` düğümü, ancak `_M_exceptionHolder` , yalnızca göreceksiniz eksik `[State]` düğüm.  

```xml  
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

###  <a name="BKMK_Condition_attribute"></a> Koşul özniteliği  
 İsteğe bağlı `Condition` özniteliği birçok görsel öğeler için kullanılabilir ve görselleştirme kuralının ne zaman kullanılması gerektiğini belirtir. Koşul özniteliği içindeki ifade halinde `false`, sonra da öğesi tarafından belirtilen görselleştirme kuralı uygulanmaz. True olarak değerlendirilirse veya yoksa hiçbir `Condition` özniteliği türe görselleştirme kuralı uygulanır. Bu öznitelik için kullanabileceğiniz `if-else` görselleştirme girişlerinde mantığı. Örneğin, aşağıdaki görselleştirme iki içeren `DisplayString` akıllı işaretçi türünüz için öğeleri:  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 Zaman `_Myptr` üyesidir `null`, ilk koşul `DisplayString` öğesi çözümler için `true`, böylece form görüntülenir. Zaman `_Myptr` üye değil `null`, koşul olmaması `false`ve ikinci `DisplayString` öğe görüntülenir.  

### <a name="includeview-and-excludeview-attributes"></a>IncludeView ve ExcludeView öznitelikleri  
 Bu öznitelikler görüntülenen ya da farklı görünümleri gösterilmiyorsa öğeleri belirtin. Örneğin, Natvis belirtimi verilen `std::vector`:  

```xml  
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  

 Basit Görünüm [boyutu] görüntülemez ve Basit Görünüm [kapasite] öğeleri. Biz kullanmışsınız `IncludeView="simple"` yerine `ExcludeView`, `[size]` ve `[capacity]` öğeleri getirirseniz, Basit Görünüm yerine varsayılan görünüm.  

 Kullanabileceğiniz `IncludeView` ve `ExcludeView` öznitelikleri ayrı ayrı üyeleri yanı sıra türleri.  

###  <a name="BKMK_DisplayString"></a> DisplayString  
 A `DisplayString` öğesi, değişkenin değeri olarak gösterilecek dizeyi belirtir. Bu ifadelerle karışan rasgele dizeleri kabul eder. Küme ayracı içindeki her şey bir ifade olarak yorumlanır. Örneğin, bir `DisplayString` bu gibi giriş:  

```xml  
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  

```  

 Yol türü bu değişkenler `CPoint` şöyle görüntülenir:  

 ![DisplayString öğesini kullanarak](../debugger/media/dbg-natvis-cpoint-displaystring.png "DBG_NATVIS_CPoint_DisplayString")  

 İçinde `DisplayString` ifade `x` ve `y`, üyeleri `CPoint`, kaşlı ayraçlar içinde olduğundan ve bunların değerleri değerlendirilir. İfade ayrıca çift kaşlı ayraçlar kullanarak bir küme ayracından nasıl kaçış gösterir ( `{{` veya `}}` ).  

> [!NOTE]
>  `DisplayString` Rastgele dize ve küme ayracı sözdizimi kabul eden tek öğe bir öğedir. Diğer tüm görselleştirme öğeleri yalnızca hata ayıklayıcı tarafından değerlendirilen ifadeleri kabul eder.  

###  <a name="BKMK_StringView"></a> StringView  
 `StringView` Öğe değeri yerleşik metin görselleştiriciye gönderilecek giden ifade tanımlar. Örneğin, aşağıdaki görselleştirme için sahip olduğumuz varsayalım `ATL::CStringT` türü:  

```xml  
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>  

```  

 `CStringT` Nesnesi şöyle:  

 ![CStringT DisplayString öğesi](../debugger/media/dbg-natvis-displaystring-cstringt.png "DBG_NATVIS_DisplayString_CStringT")  

 Görselleştirme görüntüler bir `CStringT` nesnesini şunun gibi bir değişken penceresinde:  

 Ekleme bir `StringView` öğesi, hata ayıklayıcı için bu değer bir metin görselleştirmesi ile görüntülenebilir gösterecektir:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

 Büyüteç simgesinin aşağıdaki değerin yanında gösterildiğine dikkat edin. Simge seçildiğinde dizeyi görüntüleyecek metin görselleştiricisi başlatılır, `m_pszData` işaret eder.  

 ![CStringT verilerle StringView Görselleştirici](../debugger/media/dbg-natvis-stringview-cstringt.png "DBG_NATVIS_StringView_CStringT")  

> [!NOTE]
>  Unutmayın ifade `{m_pszData,su}` C++ biçim belirticisini içerir `su` değeri bir Unicode dize görüntülemek için. Bkz: [C++ içindeki Biçim belirticileri](../debugger/format-specifiers-in-cpp.md) daha fazla bilgi için.  

###  <a name="BKMK_Expand"></a> Genişletin  
 `Expand` Düğümü, kullanıcı, değişken pencerelerinde genişlettiğinde görselleştirilen türün alt öğeleri özelleştirmek için kullanılır. Bu, alt öğeleri tanımlayan alt düğümlerin listesini kabul eder.  

 `Expand` Düğümüdür isteğe bağlı.  

-   Varsa bir `Expand` düğümü belirtilmezse görselleştirme girdisinde, Visual Studio'nun varsayılan genişletme kuralları kullanılır.  

-   Varsa bir `Expand` düğümü belirtilirse, altında alt düğümler olmadan tür genişletilemez hata ayıklayıcı pencerelerinde.  

####  <a name="BKMK_Item_expansion"></a> Öğe genişletme  
 `Item` Öğedir en temel ve en sık kullanılan öğe kullanılmak üzere bir `Expand` düğümü. `Item` tek bir alt öğe tanımlar. Örneğin, sahip olduğunuzu varsayalım. bir `CRect` sınıfıyla `top`, `left`, `right`, ve `bottom` alanlarından ve şu görselleştirme girdiniz:  

```xml  
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  

```  

 `CRect` Türü şu şekilde görünür:  

 ![CRect öğesi öğesi genişletmesi ile](../debugger/media/dbg-natvis-expand-item-crect1.png "DBG_NATVIS_Expand_Item_CRect1")  

 Belirtilen ifadeler `Width` ve `Height` öğeler değerlendirilir ve değer sütununda gösterilir. `[Raw View]` Özel genişletme kullanılan her durumda düğüm hata ayıklayıcı tarafından otomatik olarak oluşturulur. Bunu nasıl nesnenin ham görünümünün kendi görselleştirmesinden farklı olduğunu göstermek için yukarıdaki ekran görüntüsünde genişletilmiştir. Visual Studio varsayılan genişletmesi, temel sınıfın bir alt ağacını oluşturur ve tüm veri üyeleri temel sınıfın alt öğeleri olarak listeler.  

> [!NOTE]
>  Öğenin ifadesi karmaşık bir türü işaret ediyorsa `Item` düğümü genişletilebilir.  

####  <a name="BKMK_ArrayItems_expansion"></a> Arrayıtems genişletme  
 Kullanım `ArrayItems` düğümünü türü bir dizi olarak yorumlamasını ve tek tek öğelerini görüntülemek ve Visual Studio hata. Görselliğini `std::vector` iyi bir örnektir:  

```xml  
<Type Name="std::vector&lt;*&gt;">  
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mylast - _Myfirst</Item>  
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>  
    <ArrayItems>  
      <Size>_Mylast - _Myfirst</Size>  
      <ValuePointer>_Myfirst</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  

```  

 A `std::vector` değişken penceresinde genişletildiğinde bireysel öğelerini gösterir:  

 ![Arrayıtems genişletme kullanarak std::vector](../debugger/media/dbg-natvis-expand-arrayitems-stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  

 En azından `ArrayItems` düğümünde şunun olması gerekir:  

1. A `Size` (bir tamsayı olarak değerlendirilmelidir) ifadesi hata ayıklayıcının dizinin uzunluğunun anlamak  

2. A `ValuePointer` birinci öğeyi işaret etmelidir ifade (olmayan bir öğe türünün işaretçisi olmalıdır `void*`).  

   Dizi alt sınırı varsayılan değeri 0'dır. Değeri kullanılarak geçersiz kılınabilir bir `LowerBound` (örnekler bulunabilir Visual Studio ile birlikte gelen .natvis dosyalarında) öğesi.  

   Artık `[]` işleciyle bir `ArrayItems` genişletme, örneğin `vector[i]`. [] İşleci kullanan bir tek boyutlu dizi herhangi bir görselleştirme ile kullanılabilir `ArrayItems` veya `IndexListItems`bile türü bu işleci izin vermez (örneğin `CATLArray`).  

   Çok boyutlu diziler de belirtilebilir. Hata ayıklayıcı düzgün şekilde alt öğeleri bu durumda görüntülemek için yalnızca biraz daha fazla bilgiye gerek duyar:  

```xml  
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Direction>Forward</Direction>  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  

```  

 `Direction` Dizinin satır ağırlıklı mı sütun ağırlıklı mı sıralama olduğunu belirtir. `Rank` dizi boyut sayısını belirtir. `Size` Öğe kabul ettiği örtük `$i` parametresini bu boyuttaki dizinin uzunluğunu bulmak için boyut dizini ile değiştirir. Örneğin, önceki örnekte, ifade yukarıda `_M_extent.M_base[0]` sondan 0 boyutun uzunluğunu vermelidir `_M_extent._M_base[1]` 1 ve benzeri.  

 İşte iki nasıl boyutlu `Concurrency::array` nesne, hata ayıklayıcısı'nda görünür:  

 ![Arrayıtems genişletme ile iki boyutlu bir dizi](../debugger/media/dbg-natvis-expand-arrayitems-2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  

####  <a name="BKMK_IndexListItems_expansion"></a> Indexlistıtems genişletme  
 Kullanabileceğiniz `ArrayItems` yalnızca dizi öğelerinin bellekte bitişik, genişletme. Hata ayıklayıcı, işaretçisini geçerli öğeye artırılarak sonraki öğeye alır. Dizini değer düğümüne işlemek gereken çalışmaları desteklemek için `IndexListItems` düğümleri kullanılabilir. Bir görselleştirme aşağıda verilmiştir kullanarak `IndexListItems` düğüm:  

```xml  
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">  
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_M_vector._M_index</Item>  
    <IndexListItems>  
      <Size>_M_vector._M_index</Size>  
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>  
    </IndexListItems>  
  </Expand>  
</Type>  

```  

 Artık `[]` işleciyle bir `IndexListItems` genişletme, örneğin `vector[i]`. `[]` Operatörü kullanan bir tek boyutlu dizi herhangi bir görselleştirme ile kullanılabilir `ArrayItems` veya `IndexListItems`bile türü bu işleci izin vermez (örneğin `CATLArray`).  

 Arasındaki tek fark `ArrayItems` ve `IndexListItems` olan `ValueNode` tam ifadeyi bekliyor<sup>th</sup> örtük öğeyle `$i` parametresi.  

####  <a name="BKMK_LinkedListItems_expansion"></a> Linkedlistıtems genişletme  
 Görselleştirilmiş tür bağlı bir listeyi temsil ediyorsa, hata ayıklayıcı alt öğelerini kullanarak görüntüleyebilirsiniz bir `LinkedListItems` düğümü. Görselleştirme için `CAtlList` bu özelliği kullanarak yazın:  

```xml  
<Type Name="ATL::CAtlList&lt;*,*&gt;">  
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
  <Expand>  
    <Item Name="Count">m_nElements</Item>  
    <LinkedListItems>  
      <Size>m_nElements</Size>  
      <HeadPointer>m_pHead</HeadPointer>  
      <NextPointer>m_pNext</NextPointer>  
      <ValueNode>m_element</ValueNode>  
    </LinkedListItems>  
  </Expand>  
</Type>  

```  

 `Size` Öğesi listenin uzunluğunu gösterir. `HeadPointer` ilk öğesine işaret `NextPointer` sonraki öğeye başvuruyor ve `ValueNode` öğesinin değerine başvurur.  

-   `NextPointer` Ve `ValueNode` ifadeleri, üst liste türü ve bağlantılı liste düğümü öğesi bağlamında değerlendirilir. Yukarıdaki örnekte `CAtlList` sahip bir `CNode` sınıfı (bulunan `atlcoll.h`), bağlantılı listenin bir düğümünü temsil eder. `m_pNext` ve `m_element` alanları `CNode` sınıfı değil, `CAtlList` sınıfı.  

-   `ValueNode` Boş bırakılabilir veya sahip `this` bağlantılı liste düğümüne başvurmak için.  

#### <a name="customlistitems-expansion"></a>CustomListItems genişletme  
 `CustomListItems` Genişletme, bir karma tablo gibi bir veri yapısına geçmek için özel mantığı yazmak olanak sağlar. Kullanmanız gereken `CustomListItems` verileri görselleştirmek için hangi ihtiyacınız olan her şey değerlendirilecek yapıları C++ ifadeleri ifade olmakla birlikte kalıbına için oldukça uygun olmayan `ArrayItems`, `TreeItems`, veya `LinkedListItems.`  

 Görselleştirici CAtlMap için mükemmel örneğidir burada `CustomListItems` uygundur.  

```xml  
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">  
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>  
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>  
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
    <Expand>  
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">  
        <Variable Name="iBucket" InitialValue="-1" />  
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />  
        <Variable Name="iBucketIncrement" InitialValue="-1" />  

        <Size>m_nElements</Size>  
        <Exec>pBucket = nullptr</Exec>  
        <Loop>  
          <If Condition="pBucket == nullptr">  
            <Exec>iBucket++</Exec>  
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>  
            <Break Condition="iBucketIncrement == -1" />  
            <Exec>iBucket += iBucketIncrement</Exec>  
            <Exec>pBucket = m_ppBins[iBucket]</Exec>  
          </If>  
          <Item>pBucket,na</Item>  
          <Exec>pBucket = pBucket->m_pNext</Exec>  
        </Loop>  
      </CustomListItems>  
    </Expand>  
</Type>  
```  

####  <a name="BKMK_TreeItems_expansion"></a> Treeıtems genişletme  
 Görselleştirilmiş tür bir ağacı temsil ediyorsa, hata ayıklayıcı ağaçta yürüyebilir ve kullanabilirsiniz kullanarak kendi alt öğelerini görüntüleyebilir bir `TreeItems` düğümü. Görselleştirme için `std::map` bu özelliği kullanarak yazın:  

```xml  
<Type Name="std::map&lt;*&gt;">  
  <DisplayString>{{size = {_Mysize}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mysize</Item>  
    <Item Name="[comp]">comp</Item>  
    <TreeItems>  
      <Size>_Mysize</Size>  
      <HeadPointer>_Myhead->_Parent</HeadPointer>  
      <LeftPointer>_Left</LeftPointer>  
      <RightPointer>_Right</RightPointer>  
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>  
    </TreeItems>  
  </Expand>  
</Type>  

```  

 Çok benzer bir sözdizimidir `LinkedListItems` düğümü. `LeftPointer`, `RightPointer`, ve `ValueNode` ağaç düğümü sınıfı bağlamında değerlendirilir ve `ValueNode` boş bırakılabilir veya sahip `this` için ağaç düğümüne başvurmalıdır.  

####  <a name="BKMK_ExpandedItem_expansion"></a> Expandedıtem genişletme  
 `ExpandedItem` Öğesi, temel sınıflar veya veri üyelerinin özelliklerini görselleştirilen türün alt değilmiş gibi görüntüleyerek toplanmış alt görünüm oluşturmak için kullanılabilir. Belirtilen ifade değerlendirilir ve sonucun alt düğümleri görselleştirilen türün alt öğe listesine eklenir. Örneğin, bir akıllı işaretçi türüne sahip olduğumuz varsayalım `auto_ptr<vector<int>>` genellikle görüntüleneceği olarak:  

 ![Otomatik&#95;ptr&#60;vektör&#60;int&#62; &#62; varsayılan genişletme](../debugger/media/dbg-natvis-expand-expandeditem-default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  

 Vektörün değerlerini görmek için _Myptr üyesinden geçen değişken penceresinde iki düzey detaya gerekir. Ekleyerek bir `ExpandedItem` öğesini ortadan kaldırabilir `_Myptr` değişkeni bu hiyerarşisinden ve doğrudan vektör öğelerini görüntüleyebilirsiniz:  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 ![Otomatik&#95;ptr&#60;vektör&#60;int&#62; &#62; Expandedıtem genişletme](../debugger/media/dbg-natvis-expand-expandeditem-visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  

 Aşağıdaki örnek, temel sınıftan türetilen bir sınıfta özellikleri toplama gösterilmektedir. Varsayalım `CPanel` sınıf türetilir `CFrameworkElement`. Temel gelen özelliklerin yinelenmesi yerine `CFrameworkElement` sınıfı `ExpandedItem` düğümü, özelliklere, alt listesine eklenmesini sağlar `CPanel` sınıfı. **Nd** biçim belirticisi bu burada gereklidir türetilmiş sınıf için görselleştirme eşleştirmesini devre dışı bırakır. Aksi takdirde, ifade `*(CFrameworkElement*)this` açacak `CPanel` çünkü varsayılan görselleştirme türü eşleştirme kuralları yeniden uygulanması için görselleştirme, en uygun olanı düşünün. Kullanarak **nd** biçim belirticisi hata ayıklayıcının bir görselleştirme taban sınıfı yoksa, temel sınıf görselleştirmesini veya temel sınıf varsayılan genişletmesini kullanmasını söyler.  

```xml  
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  

```  

####  <a name="BKMK_Synthetic_Item_expansion"></a> Sentetik öğesi genişletmesi  
 Burada `ExpandedItem` öğesi hiyerarşileri ortadan kaldırarak verilerin daha düz bir görünümünü sağlar `Synthetic` düğüm yapar. (Diğer bir deyişle, bir ifadenin sonucu olmayan bir alt öğesi) bir yapay alt öğe oluşturmanızı sağlar. Bu alt öğe kendi alt öğelerini içerebilir. Aşağıdaki örnekte, görselleştirme için `Concurrency::array` türü kullanan bir `Synthetic` tanılama iletisini kullanıcıya göstermek için düğüm:  

```xml  
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">  
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>  
    </Synthetic>  
  </Expand>  
</Type>  

```  

 ![CONCURRENCY::Array Sythentic öğesi expansio ile](../debugger/media/dbg-natvis-expand-synthetic.png "DBG_NATVIS_Expand_Synthetic")  

###  <a name="BKMK_HResult"></a> HResult  
 `HResult` Öğesi, hata ayıklayıcı pencerelerinde HRESULT için görüntülenen bilgileri özelleştirmenize olanak sağlar. `HRValue` Öğesi, özelleştirilecek HRESULT 32-bit değeri içermelidir. `HRDescription` Öğesi hata ayıklayıcıda gösterilen bilgileri içerir.  

```  

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

###  <a name="BKMK_UIVisualizer"></a> Uıvisualizer  
 A `UIVisualizer` öğesi, hata ayıklayıcı ile grafiksel Görselleştirici eklentisini kaydeder. Bir grafik Görselleştirici eklentisi, bir iletişim kutusu veya bir değişkeni veya nesneyi, veri türüne uygun bir şekilde görüntülemek için başka bir arabirim oluşturur. Görselleştirici eklentisinin olarak yazılması bir [VSPackage](../extensibility/internals/vspackages.md) ve hata ayıklayıcı tarafından tüketilebilecek bir hizmeti göstermesi gerekir. .Natvis dosyası adı, sunulan hizmet GUID'si ve ayrıca görselleştirebileceği türler gibi eklenti için kayıt bilgileri içerir.  

 Uıvisualizer öğesinin bir örnek aşağıda verilmiştir:  

```xml  

<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="1" MenuName="Vector Visualizer"/>  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="2" MenuName="List Visualizer"/>  
.  
.  
</AutoVisualizer>  
```  

 A `UIVisualizer` tarafından tanımlanan bir `ServiceId`  -  `Id` öznitelik çifti. `ServiceId` Görselleştirici paket tarafından sunulan hizmet GUID'i `Id` bir hizmet birden fazla Görselleştirici sağlıyorsa, görselleştiricileri ayırt etmek için kullanılan benzersiz bir tanımlayıcıdır. Yukarıdaki örnekte, aynı Görselleştirici hizmeti iki Görselleştirici sağlıyor.  

 `MenuName` Özniteliktir Büyüteç simgesinin yanındaki açılır menüyü hata ayıklayıcı değişken pencerelerinde örneğin açtıklarında Görselleştirici adı olarak gördükleri:  

 ![Uıvisualizer menü kısayol menüsünü](../debugger/media/dbg-natvis-vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  

 .Natvis dosyasında tanımlanan her tür, onları görüntüleyebilen UI görselleştiricilerini açıkça listelemelidir. Hata ayıklayıcı türleri kayıtlı görselleştiricilerle eşleşecek şekilde tür girişlerindeki Görselleştirici başvurularını eşleştirir. Örneğin, şu tür girdisi `std::vector` yukarıdaki örneğimizde Uıvisualizer'a başvurur.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Bellek içi bit eşlemler görüntülemek için kullanılan görüntü Watch uzantısı Uıvisualizer'a örneği görebilirsiniz: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  

### <a name="customvisualizer-element"></a>CustomVisualizer öğesi  
 `CustomVisualizer` Visual Studio'da çalışan kod görselleştirmede denetlemek için yazabileceğiniz bir VSIX uzantısı belirten bir genişletilebilirlik noktası niteliğindedir. VSIX uzantılarını yazma hakkında daha fazla bilgi için bkz. [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Özel Görselleştirici yazma natvis XML tanımını yazmaya daha çok daha fazla iş olmakla birlikte, hangi natvis desteklediği veya desteklemediği hakkında kısıtlamalardan ücretsizdir. Özel görselleştiriciler sorgulayabilir ve hata ayıklanan işlemin değiştirmek veya Visual Studio'nun diğer bölümleriyle iletişim kurmak için kullanılan API'ler, hata ayıklayıcı genişletilebilirliği tam kümesini erişebilir.  

 Kullanabileceğiniz `Condition`, `IncludeView`, ve `ExcludeView` CustomVisualizer öğelerde öznitelikler.



