---
title: Bir özel konak kullanarak metin şablonlarını işleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5fa54f6b7ea57b6374e8fef291c64f0e5369ffea
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303465"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Bir Özel Konak kullanarak Metin Şablonlarını İşleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Metin şablonu dönüştürme* işlem alır bir *metin şablonu* dosyası olarak girdi ve çıktı olarak bir metin dosyası oluşturur. Metin dönüştürme altyapısı çağırabilirsiniz bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı, veya bir makine üzerinde çalışan bir tek başına uygulamasından [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklenir. Ancak, sağlamanız gereken bir *metin şablonu oluşturma barındırıcısı*. Bu sınıf, derlemeler ve ekleme dosyaları gibi kaynakları bularak ve çıktı ve hata iletilerini işleme alarak şablonu ortama bağlar.  
  
> [!TIP]
>  Bir paket ya da içinde çalışacak uzantısı yazıyorsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], kendi ana bilgisayarınızı yazmak yerine metin şablonu oluşturma hizmetini kullanmayı düşünün. Daha fazla bilgi için [bir VS uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
>  Metin şablonu dönüştürmelerinin sunucu uygulamalarında kullanılması önerilmez. Metin şablonu dönüştürmelerinin tek bir iş parçacığı dışında kullanılması önerilmez. Bunun nedeni, metin şablonu oluşturma motorunun şablonları çevirmek, derlemek ve yürütmek için tek bir AppDomain öğesini yeniden kullanmasıdır. Çevrilen kod, iş parçacığı açısından güvenli olmak üzere tasarlanmamıştır. Altyapı olduğu gibi seri olarak, dosyalarını işlemek için tasarlanmış bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projesinde tasarım zamanında.  
>   
>  Çalışma zamanı uygulamaları için önceden işlenmiş metin şablonlarını kullanmayı: bkz [T4 metin şablonları ile çalışma süresi metni oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Uygulamanız, derleme zamanında sabitlenmiş bir grup şablon kullanıyorsa, Önceden İşlenmiş Metin Şablonlarının kullanılması daha kolaydır. Uygulamanızı bir makine üzerinde çalıştırılacaksa da bu yaklaşımı kullanabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklü değil. Daha fazla bilgi için [T4 metin şablonları ile çalışma süresi metni oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="executing-a-text-template-in-your-application"></a>Uygulamanızda Metin Şablonu Yürütme  
 Bir metin şablonu yürütmek için ProcessTemplate yöntemini çağırırsınız <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:  
  
```  
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
 [İzlenecek yol: Özel Metin Şablonu Konağı Oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Metin şablonu işlevi dışında kullanılabilir hale getiren bir özel metin şablonu konağı oluşturma işlemi gösterilmektedir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Metin Şablonu Dönüştürme Süreci](../modeling/the-text-template-transformation-process.md)  
 Metin dönüştürmenin nasıl çalıştığını ve hangi kısımları özelleştirebileceğinizi açıklar.  
  
 [Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Metin şablonu yönerge işlemcilerine genel bakış sağlar.



