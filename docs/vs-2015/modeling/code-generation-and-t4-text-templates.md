---
title: Kod oluşturma ve T4 metin şablonları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 84
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d1310d08138e4df172a5dc9f390d0407a68fe769
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229833"
---
# <a name="code-generation-and-t4-text-templates"></a>Kod Oluşturma ve T4 Metin Şablonları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], *T4 metin şablonu* metin blokları ve bir metin dosyası oluşturabilir Denetim mantığı bir karışımını olduğu. Denetim mantığı program kodu içinde parçalarını olarak yazılır [!INCLUDE[csprcs](../includes/csprcs-md.md)] veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Visual Studio 2015 güncelleştirme 2 ve sonraki sürümlerinde, C# sürüm 6.0 özellikleri T4 şablonları yönergeleri kullanabilirsiniz. Oluşturulan dosyanın metin bir Web sayfası veya kaynak dosya veya program herhangi bir dilde kaynak kodu gibi herhangi bir türde olabilir.  
  
 T4 metin şablonları iki tür vardır:  
  
 **Çalıştırma zamanı T4 metin şablonları** ('önceden işlenmiş Şablonları'), metin dizelerinin çıktısını bir parçası olarak genellikle üretmek için uygulamanızdaki yürütülür.  
 Örneğin, bir HTML sayfası tanımlamak için bir şablon oluşturabilirsiniz:  
  
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
  
 Uygulamanızı sahip olmadığı bir bilgisayarda çalıştırabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklü.  
  
 Bir çalışma zamanı şablonu oluşturmak için bir **önceden işlenmiş metin şablonu** projenize bir dosya. Alternatif olarak, bir düz metin dosyası ekleyin ve ayarlamak kendi **özel araç** özelliğini **TextTemplatingFilePreprocessor**.  
  
 Daha fazla bilgi için [T4 metin şablonları ile çalışma süresi metni oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md). Şablonları sözdizimi hakkında daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).  
  
 **Tasarım zamanı T4 metin şablonları** yürütülür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kaynak kodunun bir parçası ve uygulamanızın diğer kaynakları tanımlamak için.  
 Genellikle, verileri tek bir girdi dosyası veya veritabanı okumak çeşitli şablonlar kullanın ve bazılarını oluşturun, `.cs`, `.vb`, ya da diğer kaynak dosyası. Her şablon, bir dosya oluşturur. İçinde yürütülen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veya [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 Örneğin, giriş verileriniz, yapılandırma verilerini bir XML dosyası olabilir. Metin şablonlarını, geliştirme sırasında XML dosyasını düzenlediğinizde, uygulama kodunun bir parçası yeniden. Şablonlardan birini, aşağıdaki örneğe benzer:  
  
```  
<#@ output extension=".txt" #>  
<#@ assembly name="System.Xml" #>  
<#  
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.  
#>  
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>  
{  
  ... // More code here.   
}  
  
```  
  
 Oluşturulan XML dosyasında değerleri bağımlı `.cs` dosya aşağıdaki benzemesi:  
  
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
>  Terim *modeli* bazen bir veya daha fazla şablonları tarafından okunan veriler tanımlamak için kullanılır. Modeli, herhangi bir dosyadan veya veritabanından herhangi bir biçimdeki olabilir. Bir UML modeli veya bir etki alanına özgü dil modeli yok. 'Model' yalnızca veri kod benzeyen yerine iş kavramlarını bağlamında tanımlanabilir gösterir.  
  
 Metin şablonu dönüştürme özelliği adlı *T4*.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md)  
 Metin dosyaları oluşturur herhangi bir uygulama, önceden derlenmiş metin şablonlarını metin tanımlamanın kolay ve güvenilir bir yöntemdir. Ancak, bu yöntem, çalışma zamanında değiştirme metin şablonları için kullanılamaz.  
  
 [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
 Kod ve diğer kaynakları bir modelde oluşturma modelini güncelleştirerek uygulamanızı güncelleştirmenize olanak tanır.  
  
 [Derleme Sürecinde Kod Oluşturma](../modeling/code-generation-in-a-build-process.md)  
 Yüklediyseniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Görselleştirme ve modelleme SDK'sı, sağlamak oluşturulan yazılım tutar değişiklikler ile güncel modelde.  
  
 [T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)  
 Bir metin şablonu dosyasının söz dizimi.  
  
 [İzlenecek Yol: Metin Şablonları Kullanarak Kod Oluşturma](../modeling/walkthrough-generating-code-by-using-text-templates.md)  
 Kod oluşturmayı kullan yollarından biri Tanıtımı.  
  
 [Bir T4 Metin Şablonuna İlişkin Hata Ayıklama](../modeling/debugging-a-t4-text-template.md)  
 Metin şablonları ve bazı ortak metin şablonu hataları ayıklanacak nasıl.  
  
 [TextTransform Yardımcı Programı ile Dosya Oluşturma](../modeling/generating-files-with-the-texttransform-utility.md)  
 Metin şablonu dönüştürmelerinin çalıştırmak için kullanabileceğiniz komut satırı aracı.  
  
 [T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)  
 Yazma yönerge işlemcileri ve kendi veri kaynakları için özel şablon oluşturma konakları öğreneceksiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir UML modelinden dosyalar oluşturma](../modeling/generate-files-from-a-uml-model.md)   
 [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)



