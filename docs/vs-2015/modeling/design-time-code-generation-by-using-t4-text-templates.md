---
title: T4 metin şablonları kullanarak tasarım zamanı kodu oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
ms.assetid: 2774b83d-1adb-4c66-a607-746e019b80c0
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a302f2d4f96f7f110780feae3f76e08b440d037f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859284"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tasarım zamanı T4 metin şablonları, program kodu ve diğer dosyaları oluşturmanıza olanak tanır, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje. Genellikle, böylece verileri göre hazırlanmasının kod farklılık şablonları yazma bir *model*. Bir dosya veya uygulama gereksinimleri hakkında önemli bilgiler içeren veritabanı modelidir.  
  
 Örneğin, bir tablo veya diyagramını olarak bir iş akışını tanımlayan bir model olabilir. Modelden, iş akışı yürüten yazılım oluşturabilirsiniz. Kullanıcıların gereksinimleri değiştiğinde, kullanıcılar ile yeni bir iş akışı tartışmak kolay bir işlemdir. İş akışı kodu yeniden kodu el ile güncelleştirme değerinden daha güvenilir oldu.  
  
> [!NOTE]
>  A *modeli* uygulamanın belirli bir yönüyle açıklayan bir veri kaynağıdır. Dosyadan veya veritabanından herhangi bir türden herhangi formunun olabilir. Herhangi bir UML modeli veya etki alanına özgü dil modeli gibi belirli bir biçimde olmasını yok. Tablolar ya da XML dosyası biçiminde tipik modelleridir.  
  
 Büyük olasılıkla kod oluşturma ile ilgili bilgi sahibi olduğunuz. Kaynakları tanımladığınızda bir **.resx** dosyası, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümü, sınıflar ve yöntemler kümesi oluşturulduğunda otomatik olarak. Kaynaklar dosyası sınıflar ve yöntemler düzenlemek sahip olması durumuna göre çok daha kolay ve daha güvenilir düzenlemek için kaynaklar kolaylaştırır. Metin şablonları ile aynı şekilde kendi tasarımının bir kaynaktan kod oluşturabilirsiniz.  
  
 Bir metin şablonu oluşturmak istediğiniz metni ve değişken bölümlerini oluşturduğu program kodu bir karışımını içerir. Program kodu ve yineleyin veya koşullu olarak oluşturulan metin parçalarını atlamasını sağlar. Oluşturulan metin için kendisini uygulamanızın parçasını oluşturacak program kodu olabilir.  
  
## <a name="creating-a-design-time-t4-text-template"></a>Tasarım zamanı T4 metin şablonu oluşturma  
  
#### <a name="to-create-a-design-time-t4-template-in-visual-studio"></a>Visual Studio'da bir tasarım zamanı T4 şablonu oluşturmak için  
  
1.  Oluşturma bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projeye ya da mevcut bir açın.  
  
     Örneğin, **dosya** menüsünde seçin **yeni**, **proje**.  
  
2.  Bir metin şablonu dosyasını projenize ekleyin ve uzantısına sahip bir ad verin **.tt**.  
  
     Bunu yapmak için **Çözüm Gezgini**, projenizin kısayol menüsünde **Ekle**, **yeni öğe**. İçinde **Yeni Öğe Ekle** iletişim kutusu seç **metin şablonu** Orta bölmeden.  
  
     Dikkat **özel araç** dosyanın özelliği **TextTemplatingFileGenerator**.  
  
3.  Dosyasını açın. Ayrıca, aşağıdaki yönergeleri zaten içerecektir:  
  
    ```  
    <#@ template hostspecific="false" language="C#" #>  
    <#@ output extension=".txt" #>  
    ```  
  
     Şablona eklediyseniz bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projesi dil özniteliği olacaktır "`VB`".  
  
4.  Metin, dosyanın sonuna ekleyin. Örneğin:  
  
    ```  
    Hello, world!  
    ```  
  
5.  Dosyayı kaydedin.  
  
     Görebileceğiniz bir **Güvenlik Uyarısı** şablonu çalıştırmak istediğinizi onaylamanızı isteyen bir ileti kutusu. **Tamam**'ı tıklatın.  
  
6.  İçinde **Çözüm Gezgini**, şablon dosyası düğümünü genişletin ve uzantıya sahip bir dosyayı bulabilirsiniz **.txt**. Metin şablonundan oluşturulan bir dosya içerir.  
  
    > [!NOTE]
    >  Projenizi Visual Basic projesi ise,'a tıklamalıdır **tüm dosyaları göster** çıktı dosyasını görmek için.  
  
### <a name="regenerating-the-code"></a>Kod oluşturma işlemi sürüyor  
 Aşağıdaki durumlarda hiçbirinde paketinizle dosyası oluşturmanın bir şablon yürütülecek:  
  
- Şablonu düzenleyebilir ve ardından odak farklı bir değiştirme [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] penceresi.  
  
- Şablonu kaydedin.  
  
- Tıklayın **tüm Şablonları Dönüştür** içinde **derleme** menüsü. Bu tüm şablonlarda dönüştüren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözüm.  
  
- İçinde **Çözüm Gezgini**, kısayol menüsünden herhangi dosya öğesini **özel aracı Çalıştır**. Seçili şablonları kümesini dönüştürmek için bu yöntemi kullanın.  
  
  Ayrıca ayarlayabileceğiniz bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okurlar veri dosyalar değiştiğinde şablonları çalıştırılır, böylece proje. Daha fazla bilgi için [kodu otomatik olarak yeniden](#Regenerating).  
  
## <a name="generating-variable-text"></a>Değişken metin oluşturma  
 Metin şablonları oluşturulan dosyanın içeriğini değiştirmek için program kodu kullanmanıza izin verir.  
  
#### <a name="to-generate-text-by-using-program-code"></a>Program kodu kullanarak metin oluşturmak için  
  
1. İçeriğini değiştirme `.tt` dosyası:  
  
   ```csharp  
   <#@ template hostspecific="false" language="C#" #>  
   <#@ output extension=".txt" #>  
   <#int top = 10;  
  
   for (int i = 0; i<=top; i++)   
   { #>  
      The square of <#= i #> is <#= i*i #>  
   <# } #>  
   ```  
  
   ```vb  
   <#@ template hostspecific="false" language="VB" #>  
   <#@ output extension=".txt" #>  
   <#Dim top As Integer = 10  
  
   For i As Integer = 0 To top  
   #>  
       The square of <#= i #> is <#= i*i #>  
   <#  
   Next  
   #>  
  
   ```  
  
2. .Tt dosyasını kaydedin ve yeniden oluşturulmuş bir .txt dosyasını inceleyin. 0 sayıların 10 kareleri listeler.  
  
   Deyimleri içinde alındığına dikkat edin `<#...#>`ve tek bir ifade içinde `<#=...#>`. Daha fazla bilgi için [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).  
  
   Kod yazarsanız [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], `template` yönergesi içermelidir `language="VB"`. `"C#"` varsayılandır.  
  
## <a name="debugging-a-design-time-t4-text-template"></a>Tasarım zamanı T4 metin şablonuna ilişkin hata ayıklama  
 Bir metin şablonunda hata ayıklama için:  
  
- INSERT `debug="true"` içine `template` yönergesi. Örneğin:  
  
   `<#@ template debug="true" hostspecific="false" language="C#" #>`  
  
- Kesme noktaları şablonda, sıradan bir kod için yaptığınız şekilde ayarlayın.  
  
- Seçin **T4 şablonunda Hata Ayıkla** Çözüm Gezgini'ndeki metin şablonu dosyasının kısayol menüsünden.  
  
  Şablon çalıştırın ve kesme noktalarında durdurun. Değişkenleri incelemek ve her zamanki yolla kodda adım adım.  
  
> [!TIP]
>  `debug="true"` oluşturulan kodun daha doğru bir şekilde daha fazla satır yönergeleri oluşturulan koda numaralandırmasını ekleyerek metin şablonu için eşleme sağlar. Teslim değiştirmeden bırakırsanız, kesme noktaları durumu yanlış çalıştırmasında durabilir.  
>   
>  Ancak bile, değil hata ayıklaması yaparken şablon yönergesinde yan tümcesi bırakabilirsiniz. Bu performans çok küçük bir bırakma neden olur.  
  
## <a name="generating-code-or-resources-for-your-solution"></a>Koda veya kaynaklara çözümünüz için oluşturma  
 Bir modeline bağlı olarak farklılık gösterir. program dosyaları oluşturabilirsiniz. Bir model, bir veritabanı, yapılandırma dosyası, UML model, DSL model veya diğer kaynak gibi bir giriştir. Birkaç genellikle oluşturmak program dosyaları aynı modelden olan. Bunu başarmak için her oluşturulan program dosyası için bir şablon dosyası oluşturun ve tüm şablonları aynı modelin okuma.  
  
#### <a name="to-generate-program-code-or-resources"></a>Program kodu veya kaynakları oluşturmak için  
  
1.  Çıktı yönergesi .cs, .vb, .resx veya .xml gibi uygun türde bir dosya oluşturmak için değiştirin.  
  
2.  İstediğiniz çözümü kod üreten kodu ekleyin. Örneğin, bir sınıfta üç tamsayı alan bildirimleri oluşturmak istiyorsanız:  
  
    ```csharp  
  
              <#@ template debug="false" hostspecific="false" language="C#" #>  
    <#@ output extension=".cs" #>  
    <# var properties = new string [] {"P1", "P2", "P3"}; #>  
    // This is generated code:  
    class MyGeneratedClass {  
    <# // This code runs in the text template:  
      foreach (string propertyName in properties)  { #>  
      // Generated code:  
      private int <#= propertyName #> = 0;  
    <# } #>  
    }  
    ```  
  
    ```vb  
    <#@ template debug="false" hostspecific="false" language="VB" #>  
    <#@ output extension=".cs" #>  
    <# Dim properties = {"P1", "P2", "P3"} #>  
    class MyGeneratedClass {  
    <#   
       For Each propertyName As String In properties  
    #>  
      private int <#= propertyName #> = 0;  
    <#  
       Next  
    #>  
    }  
  
    ```  
  
3.  Dosyayı kaydedin ve artık aşağıdaki kodu içeren oluşturulan dosyasını inceleyin:  
  
    ```  
    class MyGeneratedClass {  
      private int P1 = 0;   
      private int P2 = 0;  
      private int P3 = 0;  
    }  
    ```  
  
### <a name="generating-code-and-generated-text"></a>Kod ve oluşturulan metin oluşturma  
 Program kodu oluştururken, şablonunuzda yürütülen kod ile çözümünüzün bir parçası haline gelir elde edilen oluşturulan kod karışmasını önlemek en önemlidir. İki dilden aynı olması gerekmez.  
  
 Önceki örnekte, iki sürümü vardır. Kod bir sürümde, C# dilinde olduğu. Diğer sürüm kod Visual Basic ' dir. Ancak her ikisini de tarafından oluşturulan metin aynıdır ve C# sınıfı olan.  
  
 Aynı şekilde kullanabileceğinizi bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] herhangi bir dilde kod oluşturmak için şablon. Oluşturulan metin herhangi belirli bir dilde olması gerekmez ve program kodu olması gerekmez.  
  
### <a name="structuring-text-templates"></a>Metin şablonları yapılandırma  
 Birkaç iyi uygulama, biz şablon kodunu iki bölüme ayırın eğilimi gösterir:  
  
- Bir yapılandırma veya değişkenleri değerleri ayarlar, ancak metin blokları içermiyor veri toplama bölümü. Önceki örnekte, bu başlatma parçasıdır `properties`.  
  
   Mağaza modeli oluşturur ve genellikle bir model dosyasını okuyan buna bazen "modeli" bölümünde verilir.  
  
- Metin oluşturma bölümü (`foreach(...){...}` örnekte), değişkenlerin değerleri kullanır.  
  
  Bu gerekli bir ayrım değildir, ancak şablon metni içeren bölümü karmaşıklığını azaltmayı tarafından okunacak kolaylaştıran bir stili.  
  
## <a name="reading-files-or-other-sources"></a>Okuma dosyaları veya diğer kaynaklar  
 Bir model dosyası veya veritabanına erişmek için şablon kodunuz derlemeleri System.XML gibi kullanabilirsiniz. Bu derlemeler erişim kazanmak için şunlar gibi yönergeleri eklemeniz gerekir:  
  
```  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.IO" #>  
```  
  
 `assembly` Yönergesi kullanımınıza belirtilen derleme şablon kodunuz için başvurular bölümünü aynı şekilde bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje. Otomatik olarak başvurulan System.dll bir başvuru eklemek gerekmez. `import` Yönergesi ile aynı şekilde bunların tam nitelikli adlarını kullanarak olmadan türlerini kullanmanıza imkan tanır `using` yönergesi sıradan program dosyasındaki.  
  
 Örneğin, içeri aktardıktan sonra **System.IO**, şunu yazabilirsiniz:  
  
```csharp  
  
      <# var properties = File.ReadLines("C:\\propertyList.txt");#>  
...  
<# foreach (string propertyName in properties) { #>  
...  
```  
  
```vb  
<# For Each propertyName As String In   
             File.ReadLines("C:\\propertyList.txt")  
#>  
  
```  
  
### <a name="opening-a-file-with-a-relative-pathname"></a>Göreli bir yol adına sahip bir dosyayı açma  
 Metin şablonu göreli bir konumdan bir dosya yüklemek için kullanabileceğiniz `this.Host.ResolvePath()`. Bunu kullanmak için. Konak, ayarlamalısınız `hostspecific="true"` içinde `template`:  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
  
```  
  
 Ardından, örneğin yazabilirsiniz:  
  
```csharp  
<# string fileName = this.Host.ResolvePath("filename.txt");  
  string [] properties = File.ReadLines(filename);  
#>  
...  
<#  foreach (string propertyName in properties { #>  
...  
  
```  
  
```vb  
<# Dim fileName = Me.Host.ResolvePath("propertyList.txt")  
   Dim properties = File.ReadLines(filename)  
#>  
...  
<#   For Each propertyName As String In properties  
...  
#>  
  
```  
  
 Ayrıca `this.Host.TemplateFile`, geçerli şablon dosyasına adını tanımlar.  
  
 Türünü `this.Host` (vb'de, `Me.Host`) olan `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`.  
  
### <a name="getting-data-from-includevsprvsincludesvsprvs-mdmd"></a>İçinden verileri alma [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
 Sağlanan hizmetleri kullanmayı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ayarlayın `hostSpecific` özniteliği ve yük `EnvDTE` derleme. Ardından IServiceProvider.GetCOMService() DTE ve diğer hizmetlere erişmek için de kullanabilirsiniz. Örneğin:  
  
```scr  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
> [!TIP]
>  Bir metin şablonu, kendi uygulama etki alanında çalışan ve Hizmetleri hazırlama tarafından erişilir. Bu durumda GetCOMService() GetService() daha büyük/küçük harf güvenilirdir.  
  
##  <a name="Regenerating"></a> Kodu otomatik olarak yeniden oluşturuluyor  
 Genellikle, birkaç dosya içinde bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözüm, bir giriş modeliyle oluşturulur. Her dosya, kendi şablon, ancak tüm aynı modele başvurur şablonları oluşturulur.  
  
 Kaynak modeli değişirse, Çözümdeki tüm şablonları yeniden çalıştırmanız gerekir. Bunu el ile yapmak için **tüm Şablonları Dönüştür** üzerinde **derleme** menüsü.  
  
 Yüklediyseniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Görselleştirme ve modelleme SDK'sı, bir derleme yaptığınızda otomatik olarak dönüştürülen tüm şablonları olabilir. Bunu yapmak için proje dosyanıza (.csproj veya .vbproj) bir metin düzenleyicisinde düzenleyin ve sonra diğer dosyanın sonuna aşağıdaki satırları ekleyin `<import>` ifadeleri:  
  
```  
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v11.0\TextTemplating\Microsoft.TextTemplating.targets" />  
<PropertyGroup>  
   <TransformOnBuild>true</TransformOnBuild>  
   <!-- Other properties can be inserted here -->  
</PropertyGroup>  
```  
  
 Daha fazla bilgi için [derleme sürecinde kod oluşturma](../modeling/code-generation-in-a-build-process.md).  
  
## <a name="error-reporting"></a>Hata Raporlama  
 Hata ve uyarı iletilerini yerleştirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata penceresinde, bu yöntemleri kullanabilirsiniz:  
  
```  
Error("An error message");  
Warning("A warning message");  
```  
  
##  <a name="Converting"></a> Bir şablon için mevcut bir dosyayı dönüştürme  
 Bunlar çok bunlar birlikte bazı eklenen program kodu üretir dosyaları gibi göründüğünü yer şablonları yararlı bir özelliğidir. Bu şablon oluşturma, kullanışlı bir yöntem önerir. Sıradan bir dosyası gibi bir prototip oluşturmanız bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] dosya ve sonuçta elde edilen dosyanın değişen kod kademeli olarak tanıtır.  
  
#### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Var olan bir dosya için bir tasarım zamanı şablonu dönüştürmek için  
  
1.  İçin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gibi oluşturmak istediğiniz türde bir dosya eklemek, proje bir `.cs`, `.vb`, veya `.resx` dosya.  
  
2.  Yeni dosyanın çalıştığından emin olmak için test edin.  
  
3.  Çözüm Gezgini'nde dosya adı uzantısı için değiştirme **.tt**.  
  
4.  Aşağıdaki özelliklerini doğrulamanızı **.tt** dosyası:  
  
    |||  
    |-|-|  
    |**Özel araç =**|**TextTemplatingFileGenerator**|  
    |**Build Action =**|**Yok**|  
  
5.  Dosyanın başına aşağıdaki satırları ekleyin:  
  
    ```  
    <#@ template debug="false" hostspecific="false" language="C#" #>  
    <#@ output extension=".cs" #>  
    ```  
  
     Şablonunuzda oluşturma kodunu yazmak isterseniz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]ayarlayın `language` özniteliğini `"VB"` yerine `"C#"`.  
  
     Ayarlama `extension` , örneğin oluşturmak istediğiniz dosya türünü dosya adı uzantısı özniteliği `.cs`, `.resx`, veya `.xml`.  
  
6.  Dosyayı kaydedin.  
  
     Belirtilen uzantı ile paketinizle bir dosya oluşturulur. Özellikleri, dosya türü için doğrudur. Örneğin, **derleme eylemi** .cs dosyası özelliğini olacak **derleme**.  
  
     Oluşturulan dosyanın özgün dosyayla aynı içerik içerdiğini doğrulayın.  
  
7.  Değiştirmek için istediğiniz dosya belirleyin. Örneğin, yalnızca belirli koşullar altında görünür bir bölümü veya bir bölümü, yinelenen veya belirli değerlerin nereden değişir. Oluşturma kodunu ekleyin. Dosyayı kaydedin ve dosyası doğru şekilde oluşturulduğunu doğrulayın. Bu adımı yineleyin.  
  
## <a name="guidelines-for-code-generation"></a>Kod oluşturma için yönergeler  
 Lütfen [için T4 metin şablonları yazma yönergeleri](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
## <a name="next-steps"></a>Sonraki adımlar  
  
|Sonraki adım|Konu|  
|---------------|-----------|  
|Yardımcı işlevleri, dahil edilen dosyalar ve dış veri kullanan kod ile daha gelişmiş bir metin şablonunda hata ayıklama ve yazabilirsiniz.|[T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)|  
|Belgelere, çalışma zamanında şablon oluşturma.|[T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md)|  
|Metin oluşturma dışında çalıştırmak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[TextTransform Yardımcı Programı ile Dosya Oluşturma](../modeling/generating-files-with-the-texttransform-utility.md)|  
|Bir etki alanına özgü dil biçiminde verilerinizi dönüştürün.|[Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Kendi veri kaynaklarınızı dönüştürmek için yönerge işlemcileri yazın.|[T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [T4 Metin Şablonları Yazma Yönergeleri](../modeling/guidelines-for-writing-t4-text-templates.md)



