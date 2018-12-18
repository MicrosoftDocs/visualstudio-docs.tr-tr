---
title: 'İzlenecek yol: Metin şablonları kullanarak kod oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
ms.assetid: 24602ade-baca-425e-a6ce-be09a2c7f7e1
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: bd360e07ca555bb7cb2c482970ab9a202f7bb630
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932559"
---
# <a name="walkthrough-generating-code-by-using-text-templates"></a>İzlenecek Yol: Metin Şablonları Kullanarak Kod Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod oluşturma, türü kesin olarak belirtilmiş kaynak modeli değiştiğinde henüz kolayca değiştirilebilir program kodunu oluşturmak sağlar. Bunu daha esnek bir yapılandırma dosyası, kabul eden tamamen genel bir program yazma Alternatif yöntem ile karşılaştırın ancak ne kodu sonuçlarında çok kolay okumak ve değiştirmek ya da bu tür iyi bir performans sahiptir. Bu yönerge, bu Avantajdan gösterir.  
  
## <a name="typed-code-for-reading-xml"></a>XML okuma için yazılan kod  
 System.Xml ad alanı bir XML belgesi yüklenirken ve bellekte serbestçe gezinme için kapsamlı araçlar sağlar. Ne yazık ki, tüm düğümlerin aynı XmlNode türü vardır. Bu nedenle, alt düğümü veya yanlış öznitelikleri yanlış türde bekleniyor gibi programlama hatalarını yapmak çok kolay.  
  
 Bu örnek proje, şablon bir örnek XML dosyasını okur ve her düğüm türü için karşılık gelen sınıflar oluşturur. El ile yazılmış kod içinde XML dosyasına gitmek için bu sınıfları kullanabilirsiniz. Uygulamanız üzerinde aynı düğüm türleri kullanan diğer dosyaları da çalıştırabilirsiniz. Örnek XML dosyası amacı uğraşmanız uygulamanızın istediğiniz tüm düğüm türleri sağlamaktır.  
  
> [!NOTE]
>  Uygulama [XSD.exe'nin](http://go.microsoft.com/fwlink/?LinkId=178765), birlikte bulunan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], türü kesin belirlenmiş sınıf XML dosyaları oluşturabilirsiniz. Burada gösterilen şablonu, bir örnek olarak verilmiştir.  
  
 Örnek dosyası şu şekildedir:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<catalog>  
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">  
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>  
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>  
  </artist>  
  <artist id ="Euan%20Garden" name="Euan Garden">  
    <song id ="GardenScottishCountry">Scottish Country Garden</song>  
  </artist>  
</catalog>  
```  
  
 Bu izlenecek yolda oluşturur, aşağıdaki gibi bir kod yazabilirsiniz ve IntelliSense doğru özniteliği ve alt adlarla yazarken ister projesinde:  
  
```  
Catalog catalog = new Catalog(xmlDocument);  
foreach (Artist artist in catalog.Artist)  
{  
  Console.WriteLine(artist.name);  
  foreach (Song song in artist.Song)  
  {  
    Console.WriteLine("   " + song.Text);  
  }  
}  
```  
  
 Bu şablonu kullanmadan yazabilirsiniz yazılmamış kod ile karşılaştırın.  
  
```  
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");  
foreach (XmlNode artist in catalog.SelectNodes("artist"))  
{  
    Console.WriteLine(artist.Attributes["name"].Value);  
    foreach (XmlNode song in artist.SelectNodes("song"))  
    {  
         Console.WriteLine("   " + song.InnerText);  
     }  
}  
```  
  
 Kesin türü belirtilmiş sürümünde XML şeması bir değişiklik sınıfları değişikliklerle sonuçlanır. Derleyici, uygulama kodunun değiştirilmesi gerekmeden bölümleri vurgular. Genel XML kodu kullanan yazılmamış sürümde bu tür desteği yoktur.  
  
 Bu projede tek şablon dosyası türü belirtilmiş sürümünü mümkün kılan sınıflar oluşturmak için kullanılır.  
  
## <a name="setting-up-the-project"></a>Projeyi ayarlama  
  
### <a name="create-or-open-a-c-project"></a>Bir C# projesi oluşturun veya açın  
 Bu teknik, herhangi bir kod projesine uygulayabilirsiniz. Bu kılavuzda bir C# projesi kullanır ve bir konsol uygulaması Test amaçları için kullanırız.  
  
##### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Üzerinde **dosya** menüsünü tıklatın **yeni** ve ardından **proje**.  
  
2.  Tıklayın **Visual C#** düğümünü ve ardından **şablonları** bölmesinde tıklayın **konsol uygulaması.**  
  
### <a name="add-a-prototype-xml-file-to-the-project"></a>Bir prototip XML dosyası projeye ekleyin.  
 Bu dosyanın amacı, okuyabilir, uygulamanızın istediğiniz XML düğüm türleri örnekleri sağlamaktır. Uygulamanızı test etmek için kullanılacak bir dosya olabilir. Bu dosyadaki her düğüm türü için bir C# sınıf şablonu oluşturur.  
  
 Dosya, böylece şablon okuyabilir, ancak derlenmiş uygulamasına oluşturulmuyor projenin bir parçası olmalıdır.  
  
##### <a name="to-add-an-xml-file"></a>Bir XML dosyası eklemek için  
  
1. İçinde **Çözüm Gezgini**, projeye sağ tıklayın, **Ekle** ve ardından **yeni öğe**.  
  
2. İçinde **Yeni Öğe Ekle** iletişim kutusunda **XML dosyası** gelen **şablonları** bölmesi.  
  
3. Örnek içerik dosyasına ekleyin.  
  
4. Bu kılavuz için dosya adı `exampleXml.xml`. Önceki bölümde gösterilenle XML olarak dosyanın içeriği ayarlayın.  
  
   .  
  
### <a name="add-a-test-code-file"></a>Bir test kod dosyasına ekleyin  
 Projenize bir C# dosyası ekleyin ve içinde yazma yazabiliyor olmasını istediğiniz kod bir örnek. Örneğin:  
  
```  
using System;  
namespace MyProject  
{  
  class CodeGeneratorTest  
  {  
    public void TestMethod()  
    {  
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");  
      foreach (Artist artist in catalog.Artist)  
      {  
        Console.WriteLine(artist.name);  
        foreach (Song song in artist.Song)  
        {  
          Console.WriteLine("   " + song.Text);  
} } } } }  
```  
  
 Bu aşamada bu kodu derlemek başarısız olur. Şablon yazarken, başarılı olması izin sınıflar oluşturur.  
  
 Daha kapsamlı bir testi bu test işlevi karşı örnek XML dosyası bilinen içeriğini çıktısını denetleyebilirsiniz. Ancak test yönteminin derlediğinde bu kılavuzda, biz memnun olacaktır.  
  
### <a name="add-a-text-template-file"></a>Bir metin şablonu dosyasını ekleyin  
 Bir metin şablonu dosyasını ekleyin ve ".cs" çıkış uzantısına ayarlandı.  
  
##### <a name="to-add-a-text-template-file-to-your-project"></a>Bir metin şablonu dosyasını projenize eklemek için  
  
1. İçinde **Çözüm Gezgini**, projeye sağ tıklayın, **Ekle**ve ardından **yeni öğe**.  
  
2. İçinde **Yeni Öğe Ekle** iletişim kutusu seç **metin şablonu** gelen **şablonları** bölmesi.  
  
   > [!NOTE]
   >  Bir metin şablonu ve değil önceden işlenmiş metin şablonu eklediğinizden emin olun.  
  
3. Şablon yönergesinde dosyasını değiştirmek `hostspecific` özniteliğini `true`.  
  
    Bu değişiklik, erişim elde etmek şablon kodunu etkinleştirir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hizmetleri.  
  
4. Çıktı yönergesinde, uzantı özniteliğine ".cs" değiştirin, böylece şablon bir C# dosyası oluşturur. Bir Visual Basic projesinde ".vb" için değiştirirsiniz.  
  
5. Dosyayı kaydedin. Bu aşamada, metin şablonu dosyasını bu satırlar içermelidir:  
  
   ```  
   <#@ template debug="false" hostspecific="true" language="C#" #>  
   <#@ output extension=".cs" #>  
   ```  
  
   biçimindeki telefon numarasıdır.  
  
   Bir .cs dosyası Çözüm Gezgini'nde bir yan kuruluşu olan şablon dosyası göründüğüne dikkat edin. [+]'i tıklatarak şablon dosyasının adının yanında görebileceğiniz. Bu dosya, kaydedin veya şablon dosyası uzağa odağı Taşı şablon dosyasından oluşturulur. Oluşturulan dosyanın, projenizin bir parçası olarak derlenir.  
  
   Siz kolaylık sağlamak için şablon dosyası geliştirme, böylece bunları birbirinin yanına görebilirsiniz pencereleri şablon dosyası ve oluşturulan dosya. Bu çıkış şablonunuzun hemen görmenize olanak sağlar. Ayrıca, şablonunuzu geçersiz C# kodu oluşturduğunda, hatalar hata iletisi penceresinde görünür fark edeceksiniz.  
  
   Şablon dosyasını kaydettiğinizde doğrudan oluşturulan dosyada gerçekleştirdiğiniz düzenlemeler kaybedilir. Bu nedenle oluşturulan dosyayı düzenlemekten kaçının, veya yalnızca kısa denemeleri için düzenleyin. Bazen, IntelliSense işlemde olduğu dosyanın oluşturulan kodda kısa bir parçasını deneyin ve ardından şablon dosyasına kopyalama kullanışlıdır.  
  
## <a name="developing-the-text-template"></a>Metin şablonu geliştirme  
 En iyi öneri Çevik Geliştirme test kodu şekilde sıkışmalı ve kadar her artış hatalarını bazıları temizleme biz küçük adımlar, şablonda geliştireceksiniz.  
  
### <a name="prototype-the-code-to-be-generated"></a>Prototip kod oluşturulacak  
 Test kodu, dosyanın her düğüm için bir sınıf gerektirir. Bu nedenle, bazı derleme hataları şablona şu satırları ekleyin ve kaydedin yerine geçer:  
  
```  
class Catalog {}   
class Artist {}  
class Song {}  
```  
  
 Bu, gerekli olan görmenize yardımcı olur, ancak bildirimleri örnek XML dosyasında düğüm türlerinden oluşturulabilir. Bu Deneysel satırı şablondan silin.  
  
### <a name="generate-application-code-from-the-model-xml-file"></a>Model XML dosyasından uygulama kodu oluştur  
 XML dosyasını okuma ve sınıf bildirimleri oluşturmak için aşağıdaki şablon kodla içerik şablonu değiştirin:  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml"#>  
<#@ import namespace="System.Xml" #>  
<#  
 XmlDocument doc = new XmlDocument();  
 // Replace this file path with yours:  
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
#>  
  public partial class <#= node.Name #> {}  
<#  
 }  
#>  
```  
  
 Projeniz için doğru yol ile dosya yolunu değiştirin.  
  
 Kod bloğu sınırlayıcılar fark `<#...#>`. Bu sınırlayıcılar metin oluşturduğu program kodun bir parçasını ayraç içine alın. Deyim bloğu sınırlayıcılar `<#=...#>` köşeli ayraç string olarak değerlendirilen bir ifade.  
  
 Uygulamanız için kaynak kodu oluşturan bir şablonu yazarken, iki ayrı program metni ile çalışıyorsanız. Şablonu kaydedin veya başka bir pencereye odağı Taşı, program kod bloğu sınırlayıcıları içinde her zaman çalışır. Sınırlayıcılar dışında görünen, oluşturduğu metin için oluşturulan dosya kopyalanır ve uygulama kodunuzun bir parçası haline gelir.  
  
 `<#@assembly#>` Yönergesi davranacağını gibi derleme şablonu kod için kullanılabilir hale getirme, bir başvuru. Şablon tarafından görülen derlemelerin listesini uygulama projesi başvuruları listesinde ayrıdır.  
  
 `<#@import#>` Yönergesi çalışır gibi bir `using` deyimi, bunları içeri aktarılan ad alanındaki sınıflar kısa adları kullanabilirsiniz.  
  
 Ne yazık ki, bu şablon kodunu oluşturur ancak örnek XML dosyası kümedeki her düğüm için bir sınıf bildirimi ürettiği böylece birden çok örneği varsa `<song>` düğümü, sınıf şarkıyı birkaç bildirimlerini görünür.  
  
### <a name="read-the-model-file-then-generate-the-code"></a>Model dosyasını okuyun ve ardından kodu oluştur  
 Birçok metin şablonu şablon ilk bölümünü kaynak dosyasını okuyan deseni izler ve şablon ikinci bölümü oluşturur. Tüm örnek dosyasının içerdiği düğüm türleri özetlemek için okuma ve ardından sınıf bildirimleri oluşturmak ihtiyacımız var. Başka bir `<#@import#>` kullanabiliriz böylece gereklidir `Dictionary<>:`  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml"#>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.Collections.Generic" #>  
<#  
 // Read the model file  
 XmlDocument doc = new XmlDocument();  
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");  
 Dictionary <string, string> nodeTypes =   
        new Dictionary<string, string>();  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
   nodeTypes[node.Name] = "";  
 }  
 // Generate the code  
 foreach (string nodeName in nodeTypes.Keys)  
 {  
#>  
  public partial class <#= nodeName #> {}  
<#  
 }  
#>  
```  
  
### <a name="add-an-auxiliary-method"></a>Bir yardımcı yöntemi ekleyin  
 Bir sınıf özelliği denetim bloğu olan bir blok içinde tanımlayabilirsiniz yardımcı yöntemler. Blok tarafından ayrılmış `<#+...#>` ve son blok dosya olarak görünmesi gerekir.  
  
 Sınıf adları büyük harfle başlamak için tercih ederseniz, aşağıdaki şablon kodla şablonu son kısmını değiştirebilirsiniz:  
  
```  
// Generate the code  
 foreach (string nodeName in nodeTypes.Keys)  
 {  
#>  
  public partial class <#= UpperInitial(nodeName) #> {}  
<#  
 }  
#>  
<#+  
 private string UpperInitial(string name)  
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }  
#>  
```  
  
 Bu aşamada, aşağıdaki bildirimleri oluşturulan .cs dosyası içerir:  
  
```  
public partial class Catalog {}  
public partial class Artist {}  
public partial class Song {}  
```  
  
 Alt düğümler, öznitelikleri ve iç metin özellikleri gibi başka ayrıntılar, aynı yaklaşımı kullanarak eklenebilir.  
  
### <a name="accessing-the-visual-studio-api"></a>Visual Studio API erişme  
 Ayarı `hostspecific` özniteliği `<#@template#>` erişim sağlamak şablon yönergesi verir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API. Şablon Şablon kodda bir mutlak dosya yolunu kullanarak önlemek için proje dosyalarının konumunu almak için bunu kullanabilirsiniz.  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
...  
<#@ assembly name="EnvDTE" #>  
...  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
// Open the prototype document.  
XmlDocument doc = new XmlDocument();  
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));  
```  
  
## <a name="completing-the-text-template"></a>Metin şablonu Tamamlanıyor  
 Aşağıdaki şablon içeriği veren test kodu derlemek ve çalıştırmak kod oluşturur.  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.Collections.Generic" #>  
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{  
<#  
 // Map node name --> child name --> child node type  
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();  
  
 // The Visual Studio host, to get the local file path.  
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
 // Open the prototype document.  
 XmlDocument doc = new XmlDocument();  
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));  
 // Inspect all the nodes in the document.  
 // The example might contain many nodes of the same type,   
 // so make a dictionary of node types and their children.  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
   Dictionary<string, XmlNodeType> subs = null;  
   if (!nodeTypes.TryGetValue(node.Name, out subs))  
   {  
     subs = new Dictionary<string, XmlNodeType>();  
     nodeTypes.Add(node.Name, subs);  
   }  
   foreach (XmlNode child in node.ChildNodes)  
   {  
     subs[child.Name] = child.NodeType;  
   }   
   foreach (XmlNode child in node.Attributes)  
   {  
     subs[child.Name] = child.NodeType;  
   }  
 }  
 // Generate a class for each node type.  
 foreach (string className in nodeTypes.Keys)  
 {  
    // Capitalize the first character of the name.  
#>  
    partial class <#= UpperInitial(className) #>  
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }  
  
<#  
    // Generate a property for each child.  
    foreach (string childName in nodeTypes[className].Keys)  
    {  
      // Allow for different types of child.  
      switch (nodeTypes[className][childName])  
      {  
         // Child nodes:  
         case XmlNodeType.Element:  
#>  
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }  
<#  
         break;  
         // Child attributes:  
         case XmlNodeType.Attribute:  
#>  
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }  
<#  
         break;  
         // Plain text:  
         case XmlNodeType.Text:  
#>  
      public string Text  { get { return thisNode.InnerText; } }  
<#  
         break;  
       } // switch  
     } // foreach class child  
  // End of the generated class:  
#>  
   }   
<#  
 } // foreach class  
  
   // Add a constructor for the root class   
   // that accepts an XML filename.  
   string rootClassName = doc.SelectSingleNode("*").Name;  
#>  
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}  
<#+  
   private string UpperInitial(string name)  
   {  
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);  
   }  
#>  
```  
  
### <a name="running-the-test-program"></a>Test programı çalıştırma  
 Konsol uygulamasının ana, aşağıdaki satırları test metodunu çalıştırır. Programın hata ayıklama modunda çalıştırmak için F5 tuşuna basın:  
  
```  
using System;  
namespace MyProject  
{ class Program  
  { static void Main(string[] args)  
    { new CodeGeneratorTest().TestMethod();  
      // Allow user to see the output:  
      Console.ReadLine();  
} } }  
```  
  
### <a name="writing-and-updating-the-application"></a>Yazma ve uygulamayı güncelleştirme  
 Uygulama artık genel XML kodunu kullanmak yerine üretilen sınıfları kullanarak, kesin türü belirtilmiş stilinde yazılabilir.  
  
 XML Şeması değiştiğinde yeni sınıflar kolayca oluşturulabilir. Derleyici, uygulama kodunun nereye güncelleştirilmelidir Geliştirici bildirir.  
  
 Örnek XML dosyası değiştirildiğinde sınıfları yeniden üret için tıklatın **tüm Şablonları Dönüştür** Çözüm Gezgini araç.  
  
## <a name="conclusion"></a>Sonuç  
 Bu izlenecek yol çeşitli teknikler ve kod oluşturma avantajlarını göstermektedir:  
  
- *Kod oluşturma* oluşturulmasını uygulamanızdan kaynak kodunun bir parçası olan bir *model*. Model, uygulama etki alanı için uygun bir biçimde bilgileri içerir ve uygulama ömrü boyunca değişebilir.  
  
- Güçlü bir kod avantajdır. Model bilgileri kullanıcıya daha uygun bir biçimde temsil ederken, oluşturulan kod bilgilerle türleri kümesi kullanarak çıkılacağını uygulamanın diğer bölümlerini sağlar.  
  
- IntelliSense ve derleyicinin yeni kod yazdığınızda hem şemayı güncelleştirildiğinde modelinin şemasıyla uyumluysa kod oluşturmanıza yardımcı olur.  
  
- Bir tek eylemlerin şablon dosyası bir projeye eklenmesi, bu avantajlar sağlayabilir.  
  
- Bir metin şablonu geliştirilen ve hızlı bir şekilde ve artımlı olarak test.  
  
  Bu izlenecek yolda, program kodu modeli, temsili bir örnek uygulamanın işlem XML dosyalarının bir örnekten gerçekten oluşturulur. Daha resmi bir yaklaşım, XML şeması .xsd dosyasını veya etki alanına özgü dil tanımıma biçiminde şablonu girişi olacaktır. Bu yaklaşım, bir ilişkinin çoğulluk gibi özellikleri belirlemek şablon kolaylaştırmak.  
  
## <a name="troubleshooting-the-text-template"></a>Metin şablonu sorunlarını giderme  
 Şablonu dönüştürme veya derleme hatalarıyla gördüyseniz **hata listesi**, veya çıktı dosyası doğru şekilde oluşturulmadı, açıklanan olan tekniklerle metin şablonunun giderebilirsiniz [oluşturma TextTransform yardımcı programı ile dosya](../modeling/generating-files-with-the-texttransform-utility.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [T4 metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)



