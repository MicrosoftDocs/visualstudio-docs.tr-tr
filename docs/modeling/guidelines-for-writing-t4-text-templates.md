---
title: T4 Metin Şablonları Yazma Yönergeleri
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 09ed896c85807da5a65084360fa62e24c3cca141
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896217"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>T4 Metin Şablonları Yazma Yönergeleri
Aşağıdaki genel yönergeleri program kodu veya diğer uygulama kaynakları Visual Studio'da oluşturmak istediğinizde yararlı olabilir. Kuralları sabit değil.

## <a name="guidelines-for-design-time-t4-templates"></a>Tasarım zamanı T4 şablonları için yönergeler
 Tasarım zamanı T4 şablonları, Visual Studio projesinde tasarım zamanında kod üreten şablonlardır. Daha fazla bilgi için [T4 metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Değişken yönlerini uygulama oluşturun.
Kod oluşturma sırasında proje değişebilir veya uygulamanın farklı sürümleri arasında değişir uygulama yönlerini için kullanışlıdır. Oluşturulacak ne olduğunu daha kolay belirleyebilir, değişken bu görünüşler daha sabit yönleri ayırın. Örneğin, uygulamanız bir Web sitesi sağlıyorsa, başka bir sayfadan Gezinti yolları tanımlar mantıksal işlevleri sunan standart sayfa ayırın.

 Bir veya daha fazla kaynak modeli değişken yönlerine kodlayın.
Bir dosya veya değişken oluşturulması gereken kod bölümlerini belirli değerlerini almak için her şablon okuyan veritabanı modelidir. Modelleri, veritabanlarını, XML dosyaları tasarım, diyagram veya etki alanına özgü diller olabilir. Genellikle, bir model, çok sayıda dosya içinde bir Visual Studio projesi oluşturmak için kullanılır. Her dosyayı ayrı bir şablondan oluşturulur.

 Bir projede birden fazla model kullanabilirsiniz. Örneğin, web sayfalarını ve sayfa düzeni için ayrı bir model arasında gezinme için bir model tanımlayabilir.

 Model, kullanıcıların ihtiyaçları ve sözlük, uygulamanız üzerinde odaklanın.
Örneğin, bir Web uygulamasında web sayfaları ve köprüler başvurmak için model beklenir.

 İdeal olarak, bir modeli temsil eden bilgi türünü uygun sunu biçimi seçin. Örneğin, bir modeli bir Web sitesi aracılığıyla gezinti yollarının bir diyagram kutuları ve okları olabilir.

 Oluşturulan kodu test edin.
El ile veya otomatik test sonuç kodunu girmesini gibi çalıştığını doğrulamak için kullanın. Kod oluşturulduğu aynı modelden testler oluşturma kaçının.

 Bazı durumlarda, model üzerinde doğrudan genel testleri gerçekleştirilebilir. Örneğin, Web sitesinin her sayfa gezinti bölmesinden başka tarafından erişilebildiğini sağlayan bir test yazabilirsiniz.

 İzin vermek için özel kod: Kısmi sınıflar oluşturun.
El ile ayrıca için oluşturulan kodu yazdığınız kodu için izin verin. Ortaya çıkabilecek tüm olası farklılıklara hesap bir kod oluşturma düzeni için olağandışıdır. Bu nedenle, ekleme veya bazı oluşturulan kod geçersiz kılmak beklemeniz gerekir. Oluşturulan malzemenin olduğu bir .NET dilinde gibi [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veya [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], iki stratejileri özellikle kullanışlıdır:

- Oluşturulan sınıflar, kısmi olmalıdır. Bu içerik için oluşturulan kod eklemenize olanak sağlar.

- Çiftler, biri diğerinden devralma sınıfları yeniden oluşturulması gerekir. Oluşturulan yöntemler ve Özellikler taban sınıf içermelidir ve yalnızca oluşturucuları türetilmiş bir sınıf içermelidir. Bu, elle yazılmış kodunuzu oluşturulan yöntemleri geçersiz kılmak sağlar.

  XML gibi diğer oluşturulan dillerde, kullanın `<#@include#>` elle yazılmış ve oluşturulan içerik basit birleşimlerini yapmak yönergesi. Daha karmaşık durumlarda elle yazılmış dosyalarla birlikte oluşturulan dosyanın birleştiren bir sonradan işleme adımı yazmak zorunda kalabilirsiniz.

  Ortak malzeme içerme dosyasına taşıma veya benzer metin ve birden fazla şablon içinde kod bloklarını yinelemekten kaçınmak için çalışma zamanı şablonları kullanın `<#@ include #>` yönergesi. Daha fazla bilgi için [T4 dahil yönergesi](../modeling/t4-include-directive.md).

  Ayrıca ayrı proje çalışma zamanı metin şablonları oluşturun ve ardından bunları tasarım zamanı şablonu çağırmak. Bunu yapmak için `<#@ assembly #>` ayrı proje erişmeye yönergesi. Örnekler için bkz ["Devralma içinde metin şablonlarında" Gareth Jones'un Blogundaki](http://go.microsoft.com/fwlink/?LinkId=208373).

  Büyük kod bloklarının ayrı bir derleme içine taşımayı düşünün.
  Büyük kod blokları ve sınıf özelliği bloklarını varsa, bu kod bazıları ayrı bir projede derleme yöntemlerde taşımak kullanışlı olabilir. Kullanabileceğiniz `<#@ assembly #>` yönergesi şablonu kodda erişmek için. Daha fazla bilgi için [T4 derleme yönergesi](../modeling/t4-assembly-directive.md).

  Şablon devralabilir soyut bir sınıf yöntemleri koyabilirsiniz. Soyut sınıf devralmalıdır <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Daha fazla bilgi için [T4 şablon yönergesi](../modeling/t4-template-directive.md).

  Bir yapılandırma dosyası kabul eden genel program kodu yazmak için bir değişken uygulama yazma yapılandırma dosyaları bir yöntem değil, kod oluşturur. Bu şekilde yazılmış bir uygulama, çok esnektir ve iş gereksinimleri değiştiğinde uygulama derlenmeden yapılandırılabilen. Ancak, bu yaklaşımın bir dezavantajı, uygulama daha belirli bir uygulamadan daha az iyi gerçekleştirir olur. Ayrıca, kısmen her zaman en genel türlerle dağıtılacak olduğundan, program kodu okuma ve bakımı daha zor olacaktır.

  Bunun aksine, değişken olan bölümleri derleme önce oluşturulan uygulama türü kesin belirlenmiş. Bu yazılım çok daha kolay ve daha güvenilir bir elle yazılmış kod yazma ve oluşturulan ile tümleştirmek için bölümleri sağlar.

  Kod oluşturma tüm avantajlarını elde etmek için program kodu yerine yapılandırma dosyalarını oluşturmak deneyin.

  Oluşturulan kod klasörü şablonları ve oluşturulan dosyalar adlı bir proje klasörüne yerleştirin kullanım **oluşturulan kodu**, bunu yapmak için bunları doğrudan düzenlenemez dosyaların olmadığını temizleyin. Oluşturulan sınıfları eklemek veya geçersiz kılmak için özel kod oluşturursanız, bu sınıflar adlı bir klasöre yerleştirin **özel kod**. Tipik bir proje yapısını şöyle görünür:

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs
```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Çalışma zamanı (önceden işlenmiş) T4 şablonları için yönergeler
 Ortak malzeme taşıma devralınan şablonlara miras yöntemleri ve T4 metin şablonları arasında metin blokları paylaşmak için kullanabilirsiniz. Daha fazla bilgi için [T4 şablon yönergesi](../modeling/t4-template-directive.md).

 Ayrıca çalışma zamanı şablonları sahip dosyaları içerir.

 Kodun büyük gövdeleri bir kısmi sınıfın içine taşıyın.
Her çalışma zamanı şablonu şablon olarak aynı ada sahip bir kısmi sınıf tanımı oluşturur. Aynı sınıfın başka bir kısmi tanımını içeren bir kod dosyası yazabilirsiniz. Bu şekilde sınıfı yöntemleri, alanları ve oluşturucular ekleyebilirsiniz. Bu üyeleri, şablon kod bloklarında gelen çağrılabilir.

 Bunu yapmanın avantajı IntelliSense kullanılabilir olduğu için kod yazmak daha kolay olmasıdır. Ayrıca, sunu ve temel mantığını arasında daha iyi bir ayrım elde edebilirsiniz.

 Örneğin, **MyReportText.tt**:

 `The total is: <#= ComputeTotal() #>`

 İçinde **MyReportText Methods.cs**:

 `private string ComputeTotal() { ... }`

 İzin vermek için özel kod: uzantı noktaları göz önünde bulundurun oluşturma sanal yöntemler sağlamak \<#+ sınıf özelliği engeller #>. Bu değişiklik gerektirmeden çoğu bağlamlarda kullanılacak tek bir şablon sağlar. Şablonu değiştirmek yerine, en düşük ek mantık sağlayan türetilmiş bir sınıf oluşturabilirsiniz. Türetilmiş sınıf, normal ya da kodu veya bir çalışma zamanı şablon olabilir.

 Örneğin, MyStandardRunTimeTemplate.tt içinde:

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

 Uygulama kodunda:

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();
```

## <a name="guidelines-for-all-t4-templates"></a>Tüm T4 şablonlarını için yönergeler
 Metin oluşturma alanından ayrı veri toplama deneyin hesaplama ve metin blokları karıştırmaktan kaçının. Her metin şablonunda, ilk kullanmak \<# kodunu engeller #> değişkenlerini ayarladıktan ve karmaşık hesaplamalar gerçekleştirmek için. İlk metin bloğundan şablonu veya ilk sonuna kadar \<#+ sınıf özelliği block #> uzun ifadeleri önlemek ve döngüler ve dallanmayı metin blokları içerdikleri yapmaktan kaçının. Bu uygulama şablonu okunması ve düzenlenmesi daha kolay hale getirir.

 Kullanmayın `.tt` gibi farklı dosya adı uzantısı için dahil etme dosyaları kullanın `.ttinclude` dosyaları. Kullanım `.tt` olmasını istediğiniz dosyaları işlenen olarak çalışma zamanı veya tasarım zamanı metin şablonları için yalnızca. Bazı durumlarda, Visual Studio tanır `.tt` dosyaları ve işleme özelliklerini otomatik olarak ayarlar.

 Her şablon sabit bir prototip başlatın.
Bir örnek oluşturur ve doğru olduğundan emin olun, istediğiniz kod veya metin yazın. Ardından uzantısı için .tt değiştirin ve içerik modeli okuyarak değiştiren kodun artımlı olarak ekleyin.

 Türü belirlenmiş modeller kullanmayı düşünün.
Bir XML veya veritabanı şeması için Modellerinizi oluşturmanıza karşın, bir etki alanına özgü dil (DSL) oluşturmak yararlı olabilir. Bir DSL her düğüm şema ve öznitelikleri temsil etmek için özellikleri temsil etmek için bir sınıf oluşturur avantajına sahiptir. Bu, iş modeli açısından programlayabileceğiniz anlamına gelir. Örneğin:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Modellerinizi için diyagramları kullanmayı düşünün.
Çok sayıda model en etkili bir şekilde sunulan ve özellikle çok büyük olduğu durumlarda yalnızca metin tablo olarak yönetilebilir.

 Ancak, bazı tür iş gereksinimlerini, karmaşık ilişkileri ve iş akışları kümesi açıklamak önemlidir ve diyagram en uygun Orta olan. Bir diyagram avantajı kullanıcılar ve diğer proje katılımcıları ile tartışmak kolay olmasıdır. Gereksinimleri değiştiğinde iş gereksinimlerini düzeyinde modelden kod oluşturarak, kodunuzu daha esnek yapmanızı ister.

 Bir etki alanına özgü dil (DSL) diyagramı kendi türünü de tasarlayabilirsiniz. Kod, UML hem DSL'ler oluşturulabilir. Daha fazla bilgi için [çözümleme ve mimari modelleme](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md)
