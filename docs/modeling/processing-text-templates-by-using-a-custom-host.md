---
title: Bir Özel Konak kullanarak Metin Şablonlarını İşleme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 87d9f5f489bffcc624ff758c89e5d3a230a68d01
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859347"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Özel bir Konak kullanarak Metin Şablonlarını İşleme

*Metin şablonu dönüştürme* işlem alır bir *metin şablonu* dosyası olarak girdi ve çıktı olarak bir metin dosyası oluşturur. Metin dönüştürme motorunu, Visual Studio uzantısı, veya Visual Studio'nun yüklü olduğu bir makinede çalışan bir tek başına uygulamasından çağırabilirsiniz. Ancak, sağlamanız gereken bir *metin şablonu oluşturma barındırıcısı*. Bu sınıf, derlemeler ve ekleme dosyaları gibi kaynakları bularak ve çıktı ve hata iletilerini işleme alarak şablonu ortama bağlar.

> [!TIP]
> Bir paket ya da Visual Studio içinde çalışır uzantısı yazıyorsanız, kendi ana bilgisayarınızı yazmak yerine metin şablonu oluşturma hizmetini kullanarak göz önünde bulundurun. Daha fazla bilgi için [bir VS uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Metin şablonu dönüştürmelerinin sunucu uygulamalarında kullanılması önerilmez. Metin şablonu dönüştürmelerinin tek bir iş parçacığı dışında kullanılması önerilmez. Bunun nedeni, metin şablonu oluşturma motorunun şablonları çevirmek, derlemek ve yürütmek için tek bir AppDomain öğesini yeniden kullanmasıdır. Çevrilen kod, iş parçacığı açısından güvenli olmak üzere tasarlanmamıştır. Altyapı, bir Visual Studio projesinde tasarım zamanında olduğu gibi seri olarak, dosyalarını işlemek için tasarlanmıştır.
>
> Çalışma zamanı uygulamaları için önceden işlenmiş metin şablonlarını kullanmayı: bkz [T4 metin şablonları ile çalışma süresi metni oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md).

Uygulamanız, derleme zamanında sabitlenmiş bir grup şablon kullanıyorsa, Önceden İşlenmiş Metin Şablonlarının kullanılması daha kolaydır. Uygulamanızı Visual Studio'nun yüklü olduğu değil, bir makine üzerinde çalıştırılacaksa da bu yaklaşımı kullanabilirsiniz. Daha fazla bilgi için [T4 metin şablonları ile çalışma süresi metni oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Uygulamanızda metin şablonu yürütme

Bir metin şablonu yürütmek için ProcessTemplate yöntemini çağırırsınız <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Uygulamanızın şablonu bularak sağlaması ve çıktı ile işlem yapması gerekir. 

 İçinde `host` parametresi uygulayan bir sınıf sağlamanız gerekir <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Bu, Motor tarafından geri çağrılır.

 Ana bilgisayar hataları günlüğe kaydedebilmeli, derleme ve ekleme dosyalarına yapılan başvuruları çözümleyebilmeli, şablonun yürütülebileceği bir Uygulama Etki Alanı sağlayabilmeli ve her yönerge için uygun işlemciyi çağırabilmelidir.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> tanımlanan **Microsoft.VisualStudio.TextTemplating.\*. 0. dll**, ve <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> tanımlanan **Microsoft.VisualStudio.TextTemplating.Interfaces.\*. 0. dll**.

## <a name="in-this-section"></a>Bu Bölümde
 [İzlenecek yol: bir özel metin şablonu konağı oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md) Visual Studio'nun dışında metin şablon işlevini kullanılabilmesini özel metin şablonu konağı oluşturma işlemi gösterilmektedir.

## <a name="reference"></a>Başvuru
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>

## <a name="related-sections"></a>İlgili Bölümler

- [Metin şablonu dönüştürme süreci](../modeling/the-text-template-transformation-process.md) metin dönüştürmenin nasıl çalıştığını açıklar ve hangi kısımları özelleştirebilirsiniz.
- [Özel T4 metin şablonu yönerge işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md) şablonu yönerge işlemcileri metin genel bir bakış sağlar.