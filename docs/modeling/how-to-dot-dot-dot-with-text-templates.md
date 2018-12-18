---
title: Nasıl yapılır ... Metin Şablonları ile
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 20dbc5223ddb053355fa5e8076ae66badee688a4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883080"
---
# <a name="how-to--with-text-templates"></a>Nasıl yapılır ... Metin Şablonları ile
Visual Studio'da metin şablonları oluşturma metin herhangi bir türde kullanışlı bir yöntem sunar. Metin şablonları, uygulamanızın bir parçası olarak çalışma zamanında ve bazı proje kodunu oluşturmak için tasarım zamanında metin oluşturmak için kullanabilirsiniz. Bu konuda en sık özetlenmektedir sorulan "Nasıl... yapabilirim?" Sorular.

 Bu konu başlığında, madde işareti tarafından öncelenen birden çok yanıt alternatif önerilerdir.

 Metin şablonları için genel bir giriş için okuma [kod oluşturma ve T4 metin şablonları](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Nasıl Yapılır...

### <a name="generate-part-of-my-application-code"></a>Uygulama kodumda parçası oluşturma
 Bir yapılandırma sahibim veya *modeli* bir dosya veya bir veritabanı. Bir veya daha fazla bölümlerini kodum bu modeline bağlıdır.

-   Kodu dosyalarınızdaki dosyalardan bazıları, metin şablon oluşturma. Daha fazla bilgi için [T4 metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md) ve [şablon yazmaya başlamak için en iyi yolu nedir?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Çalışma zamanında veri şablona geçirme dosyaları oluştur
 Çalışma zamanında Uygulamam standart metin ve verileri bir karışımını içeren raporlar gibi metin dosyaları oluşturur. Yüzlerce yazılmasını engellemek istediğiniz `write` deyimleri.

-   Bir çalışma zamanı metin şablonu projenize ekleyin. Bu şablon örneğini ve metin oluşturmak için kullanın, kodunuzda bir sınıf oluşturur. Oluşturucu parametreler için veri geçirebilirsiniz. Daha fazla bilgi için [T4 metin şablonları ile çalışma süresi metni oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md).

-   Yalnızca çalışma zamanında kullanılabilir olan şablonlardan oluşturmak istiyorsanız, standart metin şablonları kullanabilirsiniz. Visual Studio uzantısı yazıyorsanız metin şablonu oluşturma hizmetini çağırabilirsiniz. Daha fazla bilgi için [bir VS uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md). Diğer bağlamlarda Bu, metin şablon oluşturma altyapısı kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Kullanım \<#@parameter#> parametreleri geçirmek için bu şablonları için yönergesi. Daha fazla bilgi için [T4 parametre yönergesi](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Bir şablondan başka bir proje dosyası okunamıyor
 Şablon olarak aynı Visual Studio projesinden bir dosyayı okumak için:

-   INSERT `hostSpecific="true"` içine `<#@template#>` yönergesi.

     Kodunuzda kullanmak `this.Host.ResolvePath(filename)` dosyasının tam yolunu elde edilir.

### <a name="invoke-methods-from-a-template"></a>Bir şablondan yöntemleri çağırma
 Yöntemleri, örneğin, standart zaten varsa [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sınıflar:

- Kullanma \<#@assembly#> bütünleştirilmiş kod yükleme ve kullanma yönergesi \<#@import#> ad alanı bağlamını ayarlamak için. Daha fazla bilgi için [T4 içe aktarma yönergesi](../modeling/t4-import-directive.md).

   Sık aynı derleme kullanan ve içeri aktarma yönergeleri, yönerge işlemcisi yazma göz önünde bulundurun. Her şablon, derlemeler ve model dosyaları yüklemek ve ad alanı bağlamını ayarlayın ve yönerge işlemcisinin çağırabilirsiniz. Daha fazla bilgi için [özel T4 metin şablonu yönerge işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md).

  Yöntemleri kendinize yazıyorsanız:

- Bir çalışma zamanı metin şablonu yazıyorsanız, çalışma zamanı metin şablonu ile aynı ada sahip bir kısmi sınıf tanımını yazın. Ek yöntemleri bu sınıfına ekleyin.

- Bir sınıf özelliği denetim bloğu yazma `<#+ ... #>` içinde yöntemler, özellikler ve özel sınıflar bildirebilirsiniz. Metin şablonu derlendiğinde, bir sınıfa dönüştürülür. Standart denetim blokları `<#...#>` metin için tek bir yöntem dönüştürülür ve sınıf özelliği bloklarını, ayrı üyeleri olarak eklenir. Daha fazla bilgi için [metin şablonu denetim blokları](../modeling/text-template-control-blocks.md).

   Sınıf özellikleri de katıştırılmış metin blokları içerebilir olarak tanımlanan yöntemleri.

   Sınıf özellikleri yapabileceğiniz ayrı bir dosyada yerleştirmeyi düşünün `<#@include#>` bir veya daha fazla şablon dosyalarına.

- Ayrı bir derlemede (sınıf kütüphanesi) yöntemleri yazmak ve bunları şablonunuzdan çağırın. Kullanım `<#@assembly#>` derlemeyi yüklemek için yönergesi ve `<#@import#>` ad alanı bağlamını ayarlamak için. Derleme, bu hata ayıklama sırasında yeniden için Visual Studio'yu yeniden başlatın ve durdurun gerekebilir olduğunu unutmayın. Daha fazla bilgi için [T4 metin şablonu yönergeleri](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Çok sayıda dosya bir model şemadan oluştur
 Dosyaları genellikle aynı XML veya veritabanı şeması modellerinden oluşturursanız:

-   Bir yönerge işlemcisi yazma göz önünde bulundurun. Bu, birden çok derleme deyimleriyle değiştirin ve içeri aktarma deyimleri her şablonda ile tek bir özel yönerge sağlar. Yönerge işlemcisini ayrıca yüklemek ve model dosyası ayrıştırılamıyor. Daha fazla bilgi için [özel T4 metin şablonu yönerge işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Karmaşık bir modelden dosyaları oluştur

-   Bir etki alanına özgü dil (DSL) temsil eden model oluşturmayı düşünün. Türleri ve model öğeleri adlarını yansıtan özellikleri kullandığından bu çok şablonları yazmak kolaylaştırır. Dosya ayrıştırma veya XML düğümüyle gidin gerekmez. Örneğin:

     `foreach (Book book in this.Library) { ... }`

     Daha fazla bilgi için [ile etki alanına özgü dillerle çalışmaya başlama](../modeling/getting-started-with-domain-specific-languages.md) ve [bir etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="get-data-from-visual-studio"></a>Visual Studio'dan veri alma
 Visual Studio'da kümesi tarafından sağlanan hizmetleri kullanmayı `hostSpecific` özniteliği ve yük `EnvDTE` derleme. Örneğin:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

### <a name="execute-text-templates-in-the-build-process"></a>Metin şablonları oluşturma işleminde yürütün

-   Daha fazla bilgi için [derleme sürecinde kod oluşturma](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Daha fazla genel sorular

### <a name="starting"></a> Metin şablonu yazma başlatmak için en iyi yolu nedir?

1.  Oluşturulan dosyanın belirli bir örneği yazın.

2.  Bir metin şablonuna ekleyerek etkinleştirmek `<#@template #>` yönergesi ve yönergeleri ve kod girdi dosyası veya model'ı yüklemek için gerekli.

3.  Aşamalı olarak dosyanın parçalarını kod blokları ifade ile değiştirin.

### <a name="what-is-a-model"></a>"Modeli" nedir?

-   Şablonunuz tarafından okunan giriş. Bir dosya veya bir veritabanı olabilir. XML veya bir Visio çizim veya bir etki alanına özgü dil (DSL) ya da bir UML modeli olabilir veya düz metin olabilir. Çeşitli dosyalar arasında yaymak. Genellikle birden fazla şablon bir model okur.

     Terim "modelin" olduğu çıkarımında iş oluşturulan program kodu veya diğer dosyaları daha fazla doğrudan bazı yönlerini temsil ettiğini ' dir. Örneğin, oluşturulan yazılım gözetmenlik bir iletişim ağı planını temsil edebilir.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Metin şablonlarını kullanmanın avantajı nedir?
 Genellikle, birden çok kod veya diğer dosyaları bir modelden oluşturun. Modeli oluşturulan kodun daha doğrudan gereksinimleri temsil eder. Bu uygulama ayrıntısı atlar ve kod yerine gereksinimleri açısından yazılmıştır. Normalde yaptığınız gibi - gereksinimleri - değiştiğinde modeli daha kolay ve program kodunu farklı bölümlerinin daha güvenilir bir şekilde güncelleştirebilirsiniz.

 Kod oluşturma bu nedenle Çevik Geliştirme yöntemleri açısından değerli bir araç olan.

### <a name="what-best-practices-are-there-for-text-templates"></a>Hangi "iyi" için metin şablonları vardır?

-   Daha fazla bilgi için [için T4 metin şablonları yazma yönergeleri](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>"T4" nedir?

-   Burada açıklanan Visual Studio Metin şablonu özellikleri için başka bir ad. Yayımlanmadı, önceki sürümü "Metin şablonu dönüştürme" kısaltması oluştu.
