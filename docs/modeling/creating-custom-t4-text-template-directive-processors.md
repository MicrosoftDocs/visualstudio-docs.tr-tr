---
title: Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0216fab44ddc52c2d01c27365449377fb899e1a6
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859659"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma

*Metin şablonu dönüştürme süreci* götüren bir *metin şablonu* dosyası olarak girdi ve çıktı olarak bir metin dosyası oluşturur. *Metin şablonu dönüştürme motoru* işlemi ve altyapısı bir metin şablonu dönüştürme ana bilgisayarı ve bir veya daha fazla metin şablonu ile etkileşime giren denetimleri *yönerge işlemcileri* tamamlamak için işlem. Daha fazla bilgi için [metin şablonu dönüştürme süreci](../modeling/the-text-template-transformation-process.md).

Özel bir yönerge işlemcisi oluşturmak için öğesinden devralınan bir sınıf oluşturun. <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> veya <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Bu ikisi arasındaki fark <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> kullanıcıdan parametreleri almak ve şablon çıktı dosyası üretir kodunu oluşturmak için gerekli olan minimum arabirimini uygular. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> uygulayan tasarım deseni gerektirir/sağlar. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> iki özel parametre işler `requires` ve `provides`.  Örneğin, özel bir yönerge işlemcisi bir dosya adı, açık şekilde kullanıcıdan kabul dosyayı okumak ve ardından dosyanın metin adlı bir değişkende depolayın `fileText`. Öğesinin <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> sınıfı sürebilir bir dosya adı kullanıcıdan değeri olarak `requires` parametresi ve metin değeri olarak depolamak için değişken adını `provides` parametresi. Bu işlemci açın ve dosyayı okuma ve metin dosyasının belirtilen bir değişkende depolayın.

Bir metin şablonundan Visual Studio'da özel bir yönerge işlemcisi çağırmadan önce kaydetmeniz gerekir.

Kayıt defteri anahtarı ekleme hakkında daha fazla bilgi için bkz. [özel yönerge işlemcisini dağıtma](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Özel yönergeleri

Özel bir yönerge şöyle görünür:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Özel yönerge işlemcisi, bir metin şablonundan dış veri ya da kaynaklara erişimi istediğiniz zaman kullanabilirsiniz.

Yönerge işlemcileri için yeniden kullanılması faktörü kod için bir yol sağlamak için farklı metin şablonlarını tek bir yönerge işlemcisi sağlayan işlevsellik paylaşabilirsiniz. Yerleşik `include` yönergesi benzerdir, çünkü kodu faktörü ve farklı metin şablonları arasında paylaşmak için kullanabilirsiniz. Fark herhangi bir işlevsellik olan, `include` yönergenin sağladığı sabittir ve sonraki parametre kabul etmiyor. Bir metin şablonu için ortak işlevselliği sağlar ve şablon parametreleri geçirmek izin vermek istiyorsanız özel bir yönerge işlemcisi oluşturmanız gerekir.

Özel yönerge işlemcilerinizi bazı örnekleri şunlardır:

-   Bir kullanıcı adı ve parola parametre olarak kabul eden bir veritabanındaki verileri döndürmek için bir yönerge işlemcisi.

-   Açıp, bir dosyayı okumak için bir yönerge işlemcisi dosyasının adı, parametre olarak kabul eder.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Özel yönerge işlemcisi sorumlusu bölümleri

Bir yönerge işlemcisi geliştirmek için öğesinden devralınan bir sınıf oluşturmanız gerekir <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> veya <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

En önemli `DirectiveProcessor` uygulamanız gereken yöntemler aşağıdaki gibidir.

-   `bool IsDirectiveSupported(string directiveName)` -Dönüş `true` yönerge işlemciniz adlandırılmış yönergesiyle giderebilirsiniz durumunda.

-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -Şablon altyapısı, şablon yönergesinde her oluşumu için bu yöntemi çağırır. İşlemci sonuçları kaydetmeniz gerekir.

Startprocessingrun() tüm çağrıları sonra şablon oluşturma altyapısı bu yöntemleri çağırır:

-   `string[] GetReferencesForProcessingRun()` -Şablon kodunu gerektiren derlemelerin adlarını döndürür.

-   `string[] GetImportsForProcessingRun()` -Kullanılabilir ad alanlarının, şablonu kodu döndürür.

-   `string GetClassCodeForProcessingRun()` -Yöntemler, özellikler ve şablon kodunu kullanabileceğiniz diğer bildirimleri kodunu döndürür. Bunu yapmanın en kolay yolu, C# veya Visual Basic kodunu içeren bir dize oluşturmaktır. Yönerge işlemciniz herhangi bir CLR dil kullanan bir şablondan çağrılan özellikli hale getirmek için ifadeleri bir CodeDom ağacını oluşturmak ve ardından şablon tarafından kullanılan dilde ağacı seri hale getirme sonucunu döndürür.

-   Daha fazla bilgi için [izlenecek yol: özel yönerge işlemcisi oluşturma](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel yönerge işlemcisi dağıtma](../modeling/deploying-a-custom-directive-processor.md) özel yönerge işlemcisi kaydetmek açıklanmaktadır.
- [İzlenecek yol: özel yönerge işlemcisi oluşturma](../modeling/walkthrough-creating-a-custom-directive-processor.md) özel yönerge işlemcisi oluşturma, kayıt ve yönerge işlemcisini sınamak ve HTML olarak çıkış dosyası biçimine açıklanmaktadır.