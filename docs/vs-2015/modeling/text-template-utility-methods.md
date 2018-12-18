---
title: Metin şablonu yardımcı program yöntemleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4a9c5a0b4b6c85a301c5d3a0e12ad3687f54aeb0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186309"
---
# <a name="text-template-utility-methods"></a>Metin Şablonu Yardımcı Program Yöntemleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod yazdığınızda, her zaman kullanabileceğiniz çeşitli yöntemler vardır bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metin şablonu. Bu yöntemler, şurada tanımlanan <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  Ayrıca, diğer yöntemler ve normal (değil önceden işlenmiş) metin şablonunda konak ortamı tarafından sağlanan hizmetleri de kullanabilirsiniz. Örneğin, dosya yollarını çözmek, oturum hataları ve tarafından sağlanan hizmetleri edinin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve tüm paketler yüklenir.  Daha fazla bilgi için [metin şablonunda Visual Studio'dan erişme](http://msdn.microsoft.com/en-us/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## <a name="write-methods"></a>Yöntemleri yazın  
 Kullanabileceğiniz `Write()` ve `WriteLine()` bir ifade kod bloğu kullanmak yerine standart bir kod bloğu içindeki metni eklenecek yöntemleri. Aşağıdaki iki kod blokları işlevsel olarak eşdeğerdir.  
  
##### <a name="code-block-with-an-expression-block"></a>Bir ifade bloğu ile kod bloğu  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>Kod bloğu WriteLine() kullanma  
  
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
 Yardımcı program yöntemleri hata ve uyarı iletilerini eklemek için kullanabileceğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata listesi. Örneğin, aşağıdaki kod bir hata iletisi hata listesine ekler.  
  
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
  
 Türünü `this.Host` şablon yürütüyordur ana bilgisayar türüne bağlıdır. Çalıştıran bir şablonda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], atayabilirsiniz `this.Host` için `IServiceProvider` IDE gibi hizmetlere erişim elde etmek için. Örneğin:  
  
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



