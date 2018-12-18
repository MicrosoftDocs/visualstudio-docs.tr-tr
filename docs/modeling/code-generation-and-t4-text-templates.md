---
title: Kod Oluşturma ve T4 Metin Şablonları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a273e6a82bbf99d1a3d57f3759504fedaa5532e6
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176287"
---
# <a name="code-generation-and-t4-text-templates"></a>Kod Oluşturma ve T4 Metin Şablonları

Visual Studio'da bir *T4 metin şablonu* metin blokları ve bir metin dosyası oluşturabilir Denetim mantığı bir karışımını olduğu. Denetim mantığı program kodu içinde parçalarını olarak yazılır [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veya [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Visual Studio 2015 güncelleştirme 2 ve sonraki sürümlerinde, C# sürüm 6.0 özellikleri T4 şablonları yönergeleri kullanabilirsiniz. Oluşturulan dosyanın metin bir web sayfası veya kaynak dosya veya program herhangi bir dilde kaynak kodu gibi herhangi bir türde olabilir.

T4 metin şablonları iki tür vardır: zamanı hem tasarım zamanı'nı çalıştırın.

## <a name="run-time-t4-text-templates"></a>Çalıştırma zamanı T4 metin şablonları

Olarak da bilinir, metin dizelerinin çıktısını bir parçası olarak genellikle üretmek için uygulamanızdaki zamanı şablonları Çalıştır 'önceden işlenmiş' şablonları yürütülür. Örneğin, bir HTML sayfası tanımlamak için bir şablon oluşturabilirsiniz:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Şablonu oluşturulan çıktı benzer olduğuna dikkat edin. Elde edilen çıkış şablona benzerliğini değiştirmek istediğinizde hataları önlemeye yardımcı olur.

Ayrıca, bu şablon, program kodu parçalarını içerir. Koşullu bölümler ve uygulamanızın verilerini gösterecek biçimde metnin bölümlerini yinelemek için bu parçaları kullanabilirsiniz.

Çıktı üretmek için uygulamanızı şablon tarafından oluşturulan bir işlevi çağırır. Örneğin:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

Uygulamanızı Visual Studio yüklü olmayan bir bilgisayarda çalıştırabilirsiniz.

Bir çalışma zamanı şablonu oluşturmak için bir **önceden işlenmiş metin şablonu** projenize bir dosya. Alternatif olarak, bir düz metin dosyası ekleyin ve ayarlamak kendi **özel araç** özelliğini **TextTemplatingFilePreprocessor**.

Daha fazla bilgi için [T4 metin şablonları ile çalışma süresi metni oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md). Şablonları sözdizimi hakkında daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Tasarım zamanı T4 metin şablonları

Tasarım zamanı şablonları, kaynak kodunun bir parçası ve uygulamanızın diğer kaynakları tanımlayın. Genellikle, bir tek bir girdi dosyası veya veritabanı verileri okumak çeşitli şablonları kullanın ve bazılarını oluşturun, *.cs*, *.vb*, ya da diğer kaynak dosyası. Her şablon, bir dosya oluşturur. Bunlar, Visual Studio veya MSBuild içinde yürütülür.

Örneğin, giriş verileriniz, yapılandırma verilerini bir XML dosyası olabilir. Metin şablonlarını, geliştirme sırasında XML dosyasını düzenlediğinizde, uygulama kodunun bir parçası yeniden oluşturun. Şablonlardan birini, aşağıdaki örneğe benzer:

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

Oluşturulan XML dosyasında değerleri bağlı olarak *.cs* dosya aşağıdaki benzemesi:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Başka bir örnek olarak, bir iş akışı diyagramı iş etkinliğinde giriş olabilir. Kullanıcılar kendi iş akışı değiştirdiğinizde veya farklı bir iş akışı yeni kullanıcılar ile iş başlattığınızda, yeni modeline uyacak şekilde kodu yeniden oluşturmak kolaydır.

Tasarım zamanı şablonları, daha hızlı ve gereklilikler değiştiğinde yapılandırmasını değiştirmek için daha güvenilir hale getirir. Genellikle iş akışı örnekte olduğu gibi iş gereksinimleri açısından giriş tanımlanır. Bu, Kullanıcılarınızla değişiklikleri tartışmak kolaylaştırır. Tasarım zamanı şablonları, bu nedenle bir Çevik Geliştirme sürecinde kullanışlı bir araç olan.

Tasarım zamanı şablonu oluşturmak için bir **metin şablonu** projenize bir dosya. Alternatif olarak, bir düz metin dosyası ekleyin ve ayarlamak kendi **özel araç** özelliğini **TextTemplatingFileGenerator**.

Daha fazla bilgi için [T4 metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Şablonları sözdizimi hakkında daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Terim *modeli* bazen bir veya daha fazla şablonları tarafından okunan veriler tanımlamak için kullanılır. Modeli, herhangi bir dosyadan veya veritabanından herhangi bir biçimdeki olabilir. Bir UML modeli veya bir etki alanına özgü dil modeli yok. 'Model' yalnızca veri kod benzeyen yerine iş kavramlarını bağlamında tanımlanabilir gösterir.

Metin şablonu dönüştürme özelliği adlı *T4*.

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
