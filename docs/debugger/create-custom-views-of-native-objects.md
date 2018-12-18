---
title: Yerel nesnelerin özel görünümlerini oluşturma
description: Visual Studio hata ayıklayıcıda yerel türleri görüntüleme biçimini özelleştirmek için Natvis çerçevesini kullanın
ms.custom: ''
ms.date: 10/31/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 937692f11cbd642da823d6f7d13bcd90de59b388
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000867"
---
# <a name="create-custom-views-of-native-objects-in-the-debugger"></a>Hata ayıklayıcıda yerel nesnelerin özel görünümlerini oluşturma

Visual Studio *Natvis* framework özelleştirir yerel türler hata ayıklayıcı değişken pencerelerinde gibi görünecek şekilde **Yereller** ve **Watch** windows ve **DataTips**. Natvis görselleştirmeler, hata ayıklama sırasında daha görünür oluşturma türleri yararlanmanıza yardımcı olabilir. 

Natvis değiştirir *autoexp.dat* dosya Visual Studio'nun önceki sürümlerinde XML sözdizimi, daha iyi tanılama, sürüm oluşturma ve birden çok dosya desteği.  

Natvis için geçerli değildir:

- C++ Windows Masaüstü projeleri ile **hata ayıklayıcı türü** kümesine **karma** altında **yapılandırma özellikleri** > **hata ayıklama**. 
- [Karışık mod hata ayıklama](how-to-debug-in-mixed-mode.md) yönetilen uyumluluk modu Windows Masaüstü uygulamaları için (**Araçları** > **seçenekleri** > **hataayıklama**  >  **Genel** > **yönetilen Uyumluluk modunu kullan**).

## <a name="BKMK_Why_create_visualizations_"></a>Natvis görselleştirmeler

Böylece geliştiriciler daha kolay hata ayıklama sırasında görebileceği türleri için görselleştirme kuralları oluşturduğunuz oluşturmak için Natvis çerçevesini kullanın.  

Örneğin, aşağıdaki çizimde türünde bir değişken gösterir [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) herhangi bir özel görselleştirme olmadan hata ayıklayıcı penceresindeki.  

![TextBox varsayılan görselleştirme](../debugger/media/dbg_natvis_textbox_default.png "TextBox varsayılan Görselleştirme")  

Vurgulanmış satıra gösterir `Text` özelliği `TextBox` sınıfı. Karmaşık sınıf hiyerarşisi bu özelliği bulunamadı zorlaştırır. Hata ayıklayıcı textbox içinde tutulan dizeyi görememiz özel bir dize türünü, nasıl yorumlayacağını bilmez.  

Aynı `TextBox` Natvis özel Görselleştirici kuralları uygulandığında değişken penceresinde çok daha kolay görünüyor. Sınıfın önemli üyeleri birlikte görünür ve hata ayıklayıcı özel dize türünün temel dize değerini gösterir.  

![Metin veri Görselleştirici kullanarak](../debugger/media/dbg_natvis_textbox_visualizer.png "metin veri Görselleştirici kullanma")  

##  <a name="BKMK_Using_Natvis_files"></a>C++ projelerinde .natvis dosyaları kullan  

Natvis kullanan *.natvis* görselleştirme kuralları belirtmek için dosyaları. A *.natvis* dosyasıdır içeren bir XML dosyası bir *.natvis* uzantısı. Natvis şema tanımlanan *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.  

Temel yapısı bir *.natvis* dosyasıdır bir veya daha fazla `Type` görselleştirme girişleri temsil eden öğe. Her tam adına `Type` öğesi belirtilen kendi `Name` özniteliği.  

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

Visual Studio bazı sağlar *.natvis* dosyalar *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* klasör. Bu dosyalar birçok ortak tür için görselleştirme kuralları olan ve yeni türler için görselleştirmeler yazmak için örnek olarak hizmet verebilen.  

### <a name="add-a-natvis-file-to-a-c-project"></a>Bir C++ projesine bir .natvis dosyası ekleme  

Ekleyebileceğiniz bir *.natvis* herhangi bir C++ projesine dosya.  

**Yeni bir *.natvis* dosyası:**

1. C++ proje düğümünde seçin **Çözüm Gezgini**seçip **proje** > **Yeni Öğe Ekle**, veya projeye sağ tıklayıp seçin **Ekle**   >  **Yeni öğe**.
   
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **Visual C++** > **yardımcı programı** > **hata ayıklayıcı görselleştirme dosyası (.natvis)**. 
   
1. Dosya adı ve seçin **Ekle**.
   
   Yeni dosya eklenir **Çözüm Gezgini**ve Visual Studio belge Bölmesi'nde açılır. 

Visual Studio hata ayıklayıcısını yükler *.natvis* C++ projelerinde dosyaları otomatik olarak ve varsayılan olarak, aynı zamanda içerir bunları *.pdb* dosya projeyi oluşturduğunda. Yerleşik uygulama hatalarını ayıklıyorsanız, hata ayıklayıcısını yükler *.natvis* dosya *.pdb* Proje Aç olmasa bile, dosya. İstemiyorsanız *.natvis* dahil dosya *.pdb*, yerleşik hariç tutabilirsiniz *.pdb* dosya.

**Dışlanacak bir *.natvis* dosyasını bir *.pdb*:**

1. Seçin *.natvis* dosyası **Çözüm Gezgini**seçip **özellikleri** simgesini veya dosyaya sağ tıklayın ve seçin **özellikleri**.
   
1. Aşağı ok yanındaki açılan **yapıdan hariç** seçip **Evet**ve ardından **Tamam**.  

>[!NOTE]
>Yürütülebilir projelerinde hata ayıklarken, tüm eklemek için çözüm öğeleri kullanın *.natvis* içinde olmayan dosyalar *.pdb*, kullanılabilir hiç C++ projesi olduğundan.  

>[!NOTE]
>Natvis kuralları yüklendi gelen bir *.pdb* modülleri türlerinde yalnızca uygulamak, *.pdb* ifade eder. Örneğin, varsa *Module1.pdb* sahip adlı bir tür için bir Natvis girişi `Test`, yalnızca geçerli `Test` sınıfını *Module1.dll*. Başka bir modül adlı bir sınıf tanımlıyorsa `Test`, *Module1.pdb* Natvis girişi için uygulanmaz.  

### <a name="BKMK_natvis_location"></a> Natvis dosyası konumları  

Ekleyebileceğiniz *.natvis* dosyaları kullanıcı dizininize veya bir sistem dizini için birden çok projeye uygulamak istiyorsanız.  

*.Natvis* dosyalarını aşağıdaki sırayla değerlendirilir:  

1. Tüm *.natvis* gömülü dosyaları bir *.pdb* yüklenen projede aynı adda bir dosya mevcut değilse, hata ayıklama.  

1. Tüm *.natvis* yüklenmiş C++ proje veya üst düzey çözüm dosyaları. Bu grup, diğer dillerde sınıf kitaplıkları, ancak değil projeleri dahil olmak üzere tüm yüklenmiş C++ projeleri içerir. 

1.  Kullanıcıya özgü Natvis dizin (örneğin, *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).  

1.  Sistem genelinde Natvis dizini (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Bu dizine sahip *.natvis* Visual Studio ile yüklenen dosyalar. Yönetici izinleriniz varsa, bu dizine dosyaları ekleyebilirsiniz.  

## <a name="modify-natvis-files-while-debugging"></a>.Natvis dosyalarında hata ayıklama sırasında değişiklik  

Değiştirebileceğiniz bir *.natvis* IDE, proje hata ayıklama sırasında dosya. Visual Studio ile hata ayıklama aynı örneğinde dosyasını açın, değiştirin ve dosyayı kaydedin. Dosyanın kaydedilmiş hemen sonra **Watch** ve **Yereller** windows update değişimi yansıtmak için. 

Siz de ekleyebilir veya silebilirsiniz *.natvis* dosyalarında hata ayıklama ve Visual Studio ekler veya kaldırır ve ilgili görselleştirmeleri bir çözüm.  

Update yapılamıyor *.natvis* gömülü dosyaları *.pdb* hata ayıklarken dosyaları.  

Değiştirirseniz *.natvis* dosyasını Visual Studio'nun dışında değişikliklerin otomatik olarak etkili değildir. Hata ayıklayıcı pencereleri güncelleştirilecek, değerlendirene **.natvisreload** komutunu **Watch** penceresi. Hata ayıklama oturumunu yeniden başlatmadan sonra değişiklikler geçerli olacaktır.  

Ayrıca **.natvisreload** yükseltmek için komut *.natvis* dosya daha yeni bir sürüme. Örneğin, *.natvis* dosya kaynak denetimine iade ve son değişikliklerini başka yapılan yazdıramadığının çekmek istediğiniz. 

##  <a name="BKMK_Expressions_and_formatting"></a> İfadeler ve biçimlendirmeler  
Natvis görselleştirmeler, görüntülenecek veri öğelerini belirtmek için C++ ifadeler kullanın. Geliştirmeleri ve hata ayıklayıcısındaki C++ ifadelerinin sınırlamalarına ek olarak, hangi açıklanmıştır [bağlam işleci (C++)](../debugger/context-operator-cpp.md), şunlara dikkat edin:  

- Natvis ifadeler, görselleştirilmekte olan nesnedeki değil geçerli yığın çerçevesi bağlamında değerlendirilir. Örneğin, `x` adlı alanı ifade içinde bir Natvis başvuruyor **x** adlı değil yerel bir değişkene görselleştirilen nesne içinde **x** geçerli işlev. Genel değişkenlere erişebilirsiniz ancak Natvis ifadeleri içindeki yerel değişkenler erişemez.  

- Natvis ifadeler İşlev değerlendirmesi veya yan efektlere izin vermez. İşlev çağrılarının ve atama işleçleri göz ardı edilir. Çünkü [hata ayıklayıcı iç işlevleri](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) ücretsiz, bunlar serbestçe çağrılabilir herhangi bir Natvis ifadesinden diğer işlev çağrılarına izin verilmese yan etkisi olan.  

- Bir ifade nasıl görüntülediğini denetlemek için açıklanan biçim belirleyicilerinin herhangi kullanabilirsiniz [biçim belirleyiciler c++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Giriş dahili olarak Natvis tarafından gibi kullanıldığında biçim belirticileri göz ardı `Size` ifadesinde bir [Arrayıtems genişletme](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).  

## <a name="natvis-views"></a>Natvis görünümleri  

Türleri farklı şekillerde göstermek için farklı Natvis görünümleri tanımlayabilirsiniz. Örneğin, bir görselleştirme işte `std::vector` adlı basitleştirilmiş bir görünümü tanımlayan `simple`. `DisplayString` Ve `ArrayItems` öğeleri göster varsayılan görünümü'nde ve `simple` görünümü sırada `[size]` ve `[capacity]` öğeleri gösterme `simple` görünümü. 

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


İçinde **Watch** penceresinde kullanım **, Görünüm** biçim belirticisi diğer bir görünümünü belirtmek için. Basit Görünüm olarak görünür **vec,view(simple)**:  

![Basit Görünüm ile İzleme penceresi](../debugger/media/watch-simpleview.png "basit görünümü ile İzleme penceresi")  

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis hataları  

Hata ayıklayıcısı bir görselleştirme girişinde hatalarla karşılaştığında, bunları yoksayar. Bu türü ham biçimiyle görüntüler veya başka bir uygun görselleştirme seçer. Natvis Tanılama, hata ayıklayıcısı bir görselleştirme girişinin neden göz ardı anlamak ve alttaki sözdizimini görebilir ve ayrıştırma hataları için kullanabilirsiniz. 

**Natvis tanılama üzerinde etkinleştirmek için:**

- Altında **Araçları** > **seçenekleri** (veya **hata ayıklama** > **seçenekleri**) > **hataayıklama**  >  **Çıkış penceresine**ayarlayın **Natvis tanılama iletileri (yalnızca C++)** için **hata**, **uyarı**, veya  **Ayrıntılı**ve ardından **Tamam**. 

Hataları görünür **çıkış** penceresi.  

##  <a name="BKMK_Syntax_reference"></a> Natvis söz dizimi başvurusu  

###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer öğesi  
`AutoVisualizer` Öğedir kök düğümü *.natvis* dosya ve ad alanını içeren `xmlns:` özniteliği. 

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

`AutoVisualizer` Öğesi olabilir [türü](#BKMK_Type), [HResult](#BKMK_HResult), [Uıvisualizer'a](#BKMK_UIVisualizer), ve [CustomVisualizer](#BKMK_CustomVisualizer) alt öğeleri. 

###  <a name="BKMK_Type"></a> Type öğesi  

Temel bir `Type` Bu örnek gibi görünür:  

```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  

 `Type` Öğesi belirtir:  

1. Ne tür bir görselleştirme için kullanılmalıdır ( `Name` özniteliği).  
   
2. Bu türdeki bir nesnenin değeri aşağıdaki gibi görünmelidir ( `DisplayString` öğesi).  
   
3. Türün üyeleri kullanıcı türü bir değişken penceresinde zaman genişletir gibi görünmelidir ( `Expand` düğümü).  
   
#### <a name="templated-classes"></a>Şablonlu sınıflar
`Name` Özniteliği `Type` öğe kabul ettiği bir yıldız işareti `*` şablonlu sınıf adları için kullanılabilecek bir joker karakter olarak.  

Aşağıdaki örnekte, aynı görselleştirme kullanılır, bu nesnenin olup bir `CAtlArray<int>` veya `CAtlArray<float>`. İçin bir özel görselleştirme girdisi varsa bir `CAtlArray<float>`, genel olana kıyasla öncelik kazanır.  

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

Şablon parametreleri görselleştirme girişinde makroları $t1, $t2, kullanarak başvuru ve VS. Bu makroların örneklerini bulmak için bkz: *.natvis* dosyaları, Visual Studio ile birlikte gönderilir.  

####  <a name="BKMK_Visualizer_type_matching"></a> Görselleştirici türü eşleşmesi  
Doğrulamak bir görselleştirme girdisi başarısız olursa, bir sonraki kullanılabilir görselleştirme kullanılır.  

#### <a name="inheritable-attribute"></a>Devralınabilir özniteliği  
İsteğe bağlı `Inheritable` öznitelik, bir görselleştirme yalnızca bir temel türü için geçerlidir veya bir taban türü ve tüm türetilmiş türleri olup olmadığını belirtir. Varsayılan değer olan `Inheritable` olduğu `true`.  

Aşağıdaki örnekte, görselleştirme yalnızca geçerli `BaseClass` türü:  

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

#### <a name="priority-attribute"></a>Öznitelik önceliği  

İsteğe bağlı `Priority` özniteliği ayrıştırmak bir tanımı başarısız olursa alternatif tanımları kullanılacak sırayı belirtir. Olası değerleri `Priority` şunlardır: `Low`, `MediumLow`,`Medium`, `MediumHigh`, ve `High`. Varsayılan değer `Medium` şeklindedir. `Priority` Özniteliği ayıran yalnızca aynı içindeki öncelikler arasında *.natvis* dosya.  

Aşağıdaki örnekte, önce bir 2015 STL eşleşen girdiyi ayrıştırır. Ayrıştırılacak başarısız olursa, diğer giriş STL 2013 sürümü için kullanır:  

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

### <a name="optional-attribute"></a>İsteğe bağlı öznitelik  
Koyabilirsiniz bir `Optional` herhangi bir düğümde öznitelik. Ayrıştırmak bir alt ifade isteğe bağlı bir düğüm içindeki başarısız olursa, hata ayıklayıcı düğüm yok sayar, ancak kalan geçerlidir `Type` kuralları. Aşağıdaki türde `[State]` olmayan-isteğe bağlıdır, ancak `[Exception]` isteğe bağlıdır.  Varsa `MyNamespace::MyClass` _ adında bir alana sahiptir`M_exceptionHolder`hem `[State]` düğüm ve `[Exception]` olup olmadığını ancak düğümünün görünen hiçbir `_M_exceptionHolder` alan, yalnızca `[State]` düğümü görüntülenir.

```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

###  <a name="BKMK_Condition_attribute"></a> Koşul özniteliği  

İsteğe bağlı `Condition` özniteliği birçok görsel öğeler için kullanılabilir ve görselleştirme kuralının ne zaman kullanılacağı belirtir. Koşul özniteliği içindeki ifade halinde `false`, görselleştirme kuralı uygulanmaz. Değerlendirilirse `true`, ya da hiçbir `Condition` görselleştirmeyi özniteliğini uygular. Görselleştirme girişlerinde if-else mantığı için bu özniteliği kullanabilirsiniz. 

Örneğin, aşağıdaki görselleştirme iki içeren `DisplayString` akıllı işaretçi türünüz için öğeleri. Zaman `_Myptr` üye boş olduğundan, ilk koşul `DisplayString` öğesi çözümler için `true`, bu form görüntüler. Zaman `_Myptr` üye boş değil, bir koşul olmaması `false`ve ikinci `DisplayString` öğesi görüntüler.  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

### <a name="includeview-and-excludeview-attributes"></a>IncludeView ve ExcludeView öznitelikleri  

`IncludeView` Ve `ExcludeView` özniteliklerini görüntülemek veya belirli görünümlerinde görüntülenmemesi için öğelerin belirtin. Örneğin, aşağıdaki Natvis belirtimi içinde `std::vector`, `simple` değil Görünüm `[size]` ve `[capacity]` öğeleri.

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

Kullanabileceğiniz `IncludeView` ve `ExcludeView` türleri ve üyeleri tek tek öznitelikler.  

###  <a name="BKMK_Versioning"></a> Sürüm öğesi  
`Version` Öğesi, bir görselleştirme girişini belirli modülü ve sürüme kapsamlar. `Version` Öğe ad çakışmalarını önlemeye yardımcı olur, yanlışlıkla uyuşmazlıkları azaltır ve farklı tür sürümleri için farklı görsel öğeler sağlar.  

Bir tür farklı modüller tarafından kullanılan ortak bir üstbilgi dosyasında tanımlıyorsa, yalnızca türü belirtilen Modül sürümü olduğunda sürümü tutulan görselleştirmenin görünür.  

Aşağıdaki örnekte, görselleştirme için yalnızca geçerli `DirectUI::Border` türü bulundu `Windows.UI.Xaml.dll` sürüm 1.5 1.0. 

```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

###  <a name="BKMK_DisplayString"></a> DisplayString öğesi 
`DisplayString` Öğesi bir değişkenin değeri gösterilecek bir dize belirtir. Bu ifadelerle karışan rasgele dizeleri kabul eder. Küme ayracı içindeki her şey bir ifade olarak yorumlanır. Örneğin, aşağıdaki `DisplayString` girişi:  

```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
```  

Anlamına gelir, türü değişkenlerindeki `CPoint` Bu resimde olduğu gibi görüntüleyin:  

 ![DisplayString bir öğesinin kullanımına](../debugger/media/dbg_natvis_cpoint_displaystring.png "DisplayString öğesi kullanma")  

İçinde `DisplayString` ifade `x` ve `y`, üyeleri `CPoint`, kaşlı ayraçlar içinde olduğundan değerleri değerlendirilir. Örnek ayrıca çift kaşlı ayraçlar kullanarak bir küme ayracından nasıl kaçış gösterir ( `{{` veya `}}` ).  

> [!NOTE]
> `DisplayString` Rastgele dize ve küme ayracı sözdizimi kabul eden tek öğe bir öğedir. Diğer tüm görselleştirme öğeleri yalnızca hata ayıklayıcı değerlendirebilirsiniz ifadeleri kabul edin.  

###  <a name="BKMK_StringView"></a> StringView öğesi 

`StringView` Öğesi, hata ayıklayıcı yerleşik metin görselleştiriciye göndermek için bir değer tanımlar. Örneğin, aşağıdaki görselleştirme için verilen `ATL::CStringT` türü:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  

`CStringT` Nesne görüntüler şu örnekteki gibi bir değişken penceresinde:   

![CStringT DisplayString öğesi](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT DisplayString öğesi")  

Ekleme bir `StringView` öğe değeri bir metin görselleştirmesi görüntüleyebilir hata ayıklayıcı söyler.  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

Hata ayıklama sırasında Büyüteç simgesinin yanındaki değişken seçebilir ve ardından **metin görselleştiricisi** dizesini görüntülemek için **m_pszData** işaret eder.  

 ![CStringT verilerle StringView Görselleştirici](../debugger/media/dbg_natvis_stringview_cstringt.png "CStringT verilerle StringView görselleştiricisi")  

İfade `{m_pszData,su}` C++ biçim belirticisini içerir **su**değeri bir Unicode dize olarak görüntülemek için. Daha fazla bilgi için [biçim belirleyiciler c++](../debugger/format-specifiers-in-cpp.md).  

###  <a name="BKMK_Expand"></a> Öğe genişletme 

İsteğe bağlı `Expand` düğüm türü bir değişken penceresinde genişlettiğinizde bir görselleştirilen türün alt özelleştirir. `Expand` Düğümünün alt öğeleri tanımlayan alt düğümlerin listesini kabul eder.  

- Varsa bir `Expand` düğüm, alt varsayılan genişletme kuralları kullanan bir görselleştirme girişinde belirtilmediyse.  
  
- Varsa bir `Expand` düğümü türü değil Genişletilebilir hata ayıklayıcı pencerelerinde, altında alt düğümler olmadan belirtilirse.  

####  <a name="BKMK_Item_expansion"></a> Öğe genişletme  

 `Item` En temel ve ortak öğesinde öğedir bir `Expand` düğümü. `Item` tek bir alt öğe tanımlar. Örneğin, bir `CRect` alan sınıfıyla `top`, `left`, `right`, ve `bottom` aşağıdaki görselleştirme girişinin vardır:  

```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
```  

Hata ayıklayıcı penceresinde `CRect` türü şu örnekteki gibi görünür:  

![CRect öğesi öğesi genişletmesi ile](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect ile öğesi öğesi genişletmesi")  

Hata ayıklayıcı belirtilen ifadeler değerlendirilir `Width` ve `Height` öğeleri ve değerleri gösteriyor **değer** değişken penceresinde sütunu. 

Hata ayıklayıcıyı otomatik olarak oluşturur **[ham görüntü]** her özel genişletme için düğüm. Önceki ekran görüntüler **[ham görüntü]** genişletilmiş düğüm varsayılan nesnenin ham görünümünün kendi Natvis görselleştirmeden farkı göstermek için. Varsayılan genişletmesi, temel sınıfın bir alt ağacını oluşturur ve tüm veri üyeleri temel sınıfın alt öğeleri olarak listeler.  

> [!NOTE]
> Öğenin ifadesi karmaşık bir türü işaret ediyorsa **öğesi** düğümü genişletilebilir.  

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

![Arrayıtems genişletme kullanarak std::vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector Arrayıtems genişletme kullanma")  

`ArrayItems` Düğümünde şunun olması gerekir:  

- A `Size` (bir tamsayı olarak değerlendirilmelidir) ifadesi hata ayıklayıcının dizinin uzunluğunun anlamak.  
- A `ValuePointer` ilk öğesine işaret eden bir ifade (olmayan bir öğe türünün işaretçisi olmalıdır `void*`).  

Dizi alt sınırı varsayılan değeri 0'dır. Geçersiz kılma değeri için kullanmak bir `LowerBound` öğesi. *.Natvis* dosyalarının Visual Studio ile birlikte gelen örnekler vardır.  

>[!NOTE]
>Kullanabileceğiniz `[]` işleci, örneğin `vector[i]`, kullanan herhangi bir tek boyutlu dizi görselleştirme ile `ArrayItems`bile türü (örneğin `CATLArray`) bu işleci izin vermiyor.  

Çok boyutlu diziler de belirtebilirsiniz. Bu durumda, hata ayıklayıcı, alt öğelerin düzgün görüntülenmesi için biraz daha fazla bilgi gerekiyor:  

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

- `Direction` Dizinin satır ağırlıklı mı sütun ağırlıklı sırayla olup olmadığını belirtir. 
- `Rank` dizi boyut sayısını belirtir. 
- `Size` Öğe kabul ettiği örtük `$i` parametresini bu boyuttaki dizinin uzunluğunu bulmak için boyut dizini ile değiştirir. Önceki örnekte, ifade `_M_extent.M_base[0]` sondan 0 boyutun uzunluğunu vermelidir `_M_extent._M_base[1]` 1 ve benzeri.  

Bir iki boyutlu nasıl işte `Concurrency::array` nesne hata ayıklayıcı penceresinde görünür:  

![Arrayıtems genişletme ile iki boyutlu dizi](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Arrayıtems genişletme ile iki boyutlu dizi")  

####  <a name="BKMK_IndexListItems_expansion"></a> Indexlistıtems genişletme  

Kullanabileceğiniz `ArrayItems` yalnızca dizi öğelerinin bellekte bitişik, genişletme. Hata ayıklayıcı, işaretçisini artırılarak sonraki öğeye alır. Dizini değer düğümüne yönetmek ihtiyacınız varsa `IndexListItems` düğümleri. Bir görselleştirme ile İşte bir `IndexListItems` düğüm:  

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

Arasındaki tek fark `ArrayItems` ve `IndexListItems` olduğu `ValueNode`, tam ifadeyi bekliyor<sup>th</sup> örtük öğeyle `$i` parametresi.  

>[!NOTE]
>Kullanabileceğiniz `[]` işleci, örneğin `vector[i]`, kullanan herhangi bir tek boyutlu dizi görselleştirme ile `IndexListItems`bile türü (örneğin `CATLArray`) bu işleci izin vermiyor.  

####  <a name="BKMK_LinkedListItems_expansion"></a> Linkedlistıtems genişletme  

Görselleştirilmiş tür bağlı bir listeyi temsil ediyorsa, hata ayıklayıcı alt öğelerini kullanarak görüntüleyebilirsiniz bir `LinkedListItems` düğümü. İçin aşağıdaki görselleştirme `CAtlList` yazın kullandığı `LinkedListItems`:  

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

Hata ayıklayıcı değerlendirir `NextPointer` ve `ValueNode` bağlamında ifadeleri `LinkedListItems` düğüm öğesi, üst liste türü değil. Önceki örnekte `CAtlList` sahip bir `CNode` sınıfı (bulunan `atlcoll.h`) diğer bir deyişle bir bağlantılı liste düğümü. `m_pNext` ve `m_element` alanları `CNode` sınıfı değil `CAtlList` sınıfı.  

`ValueNode` boş bırakılabilir veya kullanın `this` başvurmak için `LinkedListItems` düğümünün kendisini.  

#### <a name="customlistitems-expansion"></a>CustomListItems genişletme  
`CustomListItems` Genişletme, bir karma tablo gibi bir veri yapısına geçmek için özel mantığı yazmak olanak sağlar. Kullanma `CustomListItems` kalıbına için C++ ifadeler Değerlendirmeli ancak henüz yoksa için gereksinim duyduğunuz her şey için kullanabileceğiniz veri yapılarını görselleştirmek için uygun `ArrayItems`, `IndexListItems`, veya `LinkedListItems`.  

İçin aşağıdaki Görselleştirici `CAtlMap` mükemmel bir örnek burada `CustomListItems` uygundur.  

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

Kullanabileceğiniz `Exec` içine kod yürütmek için bir `CustomListItems` genişletme, genişletme içinde tanımlanan nesneler ve değişkenler kullanarak. Mantıksal işleçler, aritmetik işleçler ve atama işleçleri ile kullanabileceğiniz `Exec`. Kullanamazsınız `Exec` işlevleri değerlendirilecek.

`CustomListItems` aşağıdaki iç işlevleri destekler:

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

####  <a name="BKMK_TreeItems_expansion"></a> Treeıtems genişletme  
 Görselleştirilmiş tür bir ağacı temsil ediyorsa, hata ayıklayıcı ağaçta yürüyebilir ve kullanabilirsiniz kullanarak kendi alt öğelerini görüntüleyebilir bir `TreeItems` düğümü. Görselleştirme için `std::map` kullanarak yazın bir `TreeItems` düğüm:  

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

Sözdizimi benzer `LinkedListItems` düğümü. `LeftPointer`, `RightPointer`, ve `ValueNode` ağaç düğümü sınıfı bağlamında değerlendirilir. `ValueNode` boş bırakılabilir veya kullanın `this` başvurmak için `TreeItems` düğümünün kendisini.  

####  <a name="BKMK_ExpandedItem_expansion"></a> Expandedıtem genişletme  
 `ExpandedItem` Öğesi temel sınıflar veya veri üyelerinin özelliklerini görselleştirilen türün alt değilmiş gibi görüntüleyerek toplanmış alt görünüm oluşturur. Hata ayıklayıcı belirtilen ifadeyi değerlendirir ve sonucun alt düğümleri görselleştirilen türün alt öğe listesine ekler. 

Örneğin, akıllı işaretçi türü `auto_ptr<vector<int>>` genellikle görüntüler:  

 ![Otomatik&#95;ptr&#60;vektör&#60;int&#62; &#62; varsayılan genişletme](../debugger/media/dbg_natvis_expand_expandeditem_default.png "varsayılan genişletme")  

 Vektörün değerlerini görmek için üzerinden geçen değişken penceresinde iki düzey detaya sahip `_Myptr` üyesi. Ekleyerek bir `ExpandedItem` öğesini ortadan kaldırabilir `_Myptr` değişkeni bu hiyerarşisinden ve doğrudan vektör öğelerini görüntüleyebilirsiniz:  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

 ![Otomatik&#95;ptr&#60;vektör&#60;int&#62; &#62; Expandedıtem genişletme](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Expandedıtem genişletme")  

Aşağıdaki örnek, türetilen bir sınıfta temel sınıftan özellikleri toplama gösterilmektedir. Varsayalım `CPanel` sınıf türetilir `CFrameworkElement`. Temel gelen özelliklerin yinelenmesi yerine `CFrameworkElement` sınıfı `ExpandedItem` düğüm görselleştirme özelliklere alt listesine ekler `CPanel` sınıfı. 

```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  

**Nd** türetilmiş sınıf için görselleştirme kapatır, biçim belirticisi, gerekli burada. Aksi takdirde, ifade `*(CFrameworkElement*)this` neden `CPanel` çünkü varsayılan görselleştirme türü eşleştirme kuralları yeniden uygulanması için görselleştirme, en uygun olanı düşünün. Kullanma **nd** biçim belirticisi, hata ayıklayıcının hiçbir görselleştirme temel sınıf varsa temel sınıf görselleştirmesini veya sınıf varsayılan genişletmesini kullanmasını istemek için.  

####  <a name="BKMK_Synthetic_Item_expansion"></a> Sentetik öğesi genişletmesi  
 Sırada `ExpandedItem` öğesi hiyerarşileri ortadan kaldırarak verilerin daha düz bir görünümünü sağlar `Synthetic` düğüm yapar. Bir ifadenin sonucu olmayan bir yapay alt öğe oluşturmanızı sağlar. Yapay öğesi, kendi alt öğeleri olabilir. Aşağıdaki örnekte, görselleştirme için `Concurrency::array` türü kullanan bir `Synthetic` tanılama iletisini kullanıcıya göstermek için düğüm:  

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

 ![Sentetik öğesi genişletmesi ile CONCURRENCY::Array](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency::Array ile Sentetik öğesi genişletmesi")  

###  <a name="BKMK_HResult"></a> HResult öğesi 
 `HResult` Öğe için gösterilen bilgileri özelleştirmenize olanak sağlar bir **HRESULT** hata ayıklayıcı pencerelerinde. `HRValue` Öğesi, 32-bit değeri içermelidir **HRESULT** özelleştirilecek olmasıdır. `HRDescription` Öğesi hata ayıklayıcı penceresinde göstermek için bilgileri içerir.  

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

###  <a name="BKMK_UIVisualizer"></a> Uıvisualizer öğesi 
A `UIVisualizer` öğesi, hata ayıklayıcı ile grafiksel Görselleştirici eklentisini kaydeder. Bir grafik Görselleştirici iletişim kutusu veya bir değişkeni veya nesneyi bir biçimde kendi veri türü ile tutarlı gösteren diğer arabirim oluşturur. Görselleştirici eklentisinin olarak yazılması bir [VSPackage](../extensibility/internals/vspackages.md)ve hata ayıklayıcı tüketebileceği bir hizmeti göstermesi gerekir. *.Natvis* dosyası gibi eklenti için adını, kullanıma sunulan hizmet ve görselleştirme türlerini GUID kayıt bilgileri içerir.  

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

- A `ServiceId`  -  `Id` öznitelik çifti tanımlayan bir `UIVisualizer`. `ServiceId` Görselleştirici hizmeti paketi kullanıma sunan GUID'idir. `Id` bir hizmet birden fazla sağlıyorsa, görselleştiriciler, ayırır bir benzersiz tanımlayıcısıdır. Önceki örnekte, aynı Görselleştirici hizmeti iki Görselleştirici sağlıyor.  
  
- `MenuName` Özniteliği, hata ayıklayıcı Büyüteç simgesinin yanındaki açılır görüntülenecek Görselleştirici adı tanımlar. Örneğin:  

  ![Uıvisualizer menü kısayol menüsünü](../debugger/media/dbg_natvis_vectorvisualizer.png "Uıvisualizer'a menü kısayol menüsü")  

Tanımlanan her tür *.natvis* dosyayı görüntülemek için herhangi bir UI görselleştiricilerini açıkça listelemek gerekir. Hata ayıklayıcı kayıtlı görselleştiricilerle tür girişlerindeki Görselleştirici başvurularını eşleştirir. Örneğin, şu tür girdisi `std::vector` başvuruları `UIVisualizer` önceki örnekte.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Bir örneğini görmek bir `UIVisualizer` içinde [görüntü Watch](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) bellek içi bit eşlemler görüntülemek için kullanılan bir uzantı. 

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer öğesi  
 `CustomVisualizer` Visual Studio code'da görselleştirmeler denetlemek için yazdığınız bir VSIX uzantısı belirten bir genişletilebilirlik noktası niteliğindedir. VSIX uzantılarını yazma hakkında daha fazla bilgi için bkz. [Visual Studio SDK](../extensibility/visual-studio-sdk.md). 

Natvis XML tanımını daha özel Görselleştirici yazma için çok daha fazla iş olduğunu, ancak ücretsiz kısıtlamalardan hakkında ne Natvis vermez veya desteklemiyor. Özel görselleştiriciler hata ayıklayıcı genişletilebilirliği sorgulayabilir ve hata ayıklanan işlemin değiştirmek veya Visual Studio'nun diğer bölümleriyle iletişim kurmak, API kümesini erişebilir.  

 Kullanabileceğiniz `Condition`, `IncludeView`, ve `ExcludeView` üzerinde öznitelikleri `CustomVisualizer` öğeleri.
