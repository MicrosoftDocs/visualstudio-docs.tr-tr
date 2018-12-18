---
title: Metin Şablonu Yardımcı Program Yöntemleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8d8101b3cd88b4cfa81e6d32327581de5336dcd1
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966521"
---
# <a name="text-template-utility-methods"></a>Metin Şablonu Yardımcı Program Yöntemleri

Visual Studio metin şablonunda kod yazdığınızda, her zaman kullanabileceğiniz çeşitli yöntemler vardır. Bu yöntemler, şurada tanımlanan <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

> [!TIP]
> Ayrıca, diğer yöntemler ve normal (değil önceden işlenmiş) metin şablonunda konak ortamı tarafından sağlanan hizmetleri de kullanabilirsiniz. Örneğin, dosya yollarını çözmek, oturum hataları ve Visual Studio ve tüm tarafından sağlanan hizmetleri edinin yüklenen paketler. Daha fazla bilgi için [metin şablonunda Visual Studio'dan erişme](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Yöntemleri yazın

Kullanabileceğiniz `Write()` ve `WriteLine()` bir ifade kod bloğu kullanmak yerine standart bir kod bloğu içindeki metni eklenecek yöntemleri. Aşağıdaki iki kod blokları işlevsel olarak eşdeğerdir.

### <a name="code-block-with-an-expression-block"></a>Bir ifade bloğu ile kod bloğu

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Kod bloğu WriteLine() kullanma

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Bu yardımcı program yöntemleri yerine iç içe geçmiş denetim yapıları ile uzun kod bloğu içinde bir ifade bloğu birini daha yararlı olabilir.

`Write()` Ve `WriteLine()` yöntemleri iki aşırı yükleme varsa, bir bileşik biçimlendirme dizesi artı dizesinde eklenecek nesneleri dizisi alır, tek bir dize parametresi ve bir alan (gibi `Console.WriteLine()` yöntemi). Aşağıdaki iki kullanımlarını `WriteLine()` işlevsel olarak eşdeğerdir:

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>Girinti yöntemleri

Girinti yöntemleri, metin şablonunuzu çıkışını biçimlendirmek için kullanabilirsiniz. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> Sınıfında bir `CurrentIndent` dizesi geçerli girinti metin şablonunda gösteren özelliğinin ve bir `indentLengths` diğer bir deyişle eklenmiş olan girintileri listesini alan. Bir girintilemeli ekleyebilirsiniz `PushIndent()` yöntemi ve bir girintilemeli çıkarmayı `PopIndent()` yöntemi. Tüm girintileri kaldırmak istediğiniz kullanırsanız `ClearIndent()` yöntemi. Aşağıdaki kod bloğu, bu yöntemlerin kullanımını gösterir:

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

Bu kod bloğunu aşağıdaki çıktıyı üretir:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Hata ve uyarı yöntemleri

İleti Visual Studio hata listesine eklemek için hata ve uyarı yardımcı program yöntemleri kullanabilirsiniz. Örneğin, aşağıdaki kod bir hata iletisi hata listesine ekler.

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>Ana bilgisayar ve hizmet sağlayıcısı erişimi

Özellik `this.Host` şablonunun yürütülmesinin ana bilgisayar tarafından kullanıma sunulan özellikler erişim sağlayabilir. Kullanılacak `this.Host`, ayarlamalısınız `hostspecific` özniteliğini `<@template#>` yönergesi:

`<#@template ... hostspecific="true" #>`

Türünü `this.Host` şablon yürütüyordur ana bilgisayar türüne bağlıdır. Visual Studio'da çalışan bir şablonda verdiğiniz `this.Host` için `IServiceProvider` IDE gibi hizmetlere erişim elde etmek için. Örneğin:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Farklı bir yardımcı program yöntemleri kümesini kullanma

Metin oluşturma işleminin bir parçası olarak, her zaman adlı bir sınıf içinde şablon dosyanızın dönüştürülür `GeneratedTextTransformation`ve devralınan <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Farklı bir kullanmak istiyorsanız bunun yerine, yöntemlerinin ayarlayın, kendi sınıfınızı yazabilir ve şablon yönergesinde belirtin. Sınıfınıza devralmalıdır <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

```
<#@ template inherits="MyUtilityClass" #>
```

Kullanım `assembly` derlenmiş sınıfı burada bulunabilir derlemeye başvuru yönergesi.