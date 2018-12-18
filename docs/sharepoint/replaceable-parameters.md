---
title: Değiştirilebilir parametreler | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload: office
ms.openlocfilehash: e79442ea42583f326f9cb59360777269c399b7a0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879304"
---
# <a name="replaceable-parameters"></a>Değiştirilebilir parametreler
  Değiştirilebilir parametreler veya *belirteçleri*, gerçek değerleri, tasarım zamanında bilinen olmayan SharePoint çözüm öğeleri için değerler sağlamak için proje dosyaları içinde kullanılabilir. Bunlar standart işlevinde benzer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] şablon belirteçleri. Daha fazla bilgi için [şablon parametreleri](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Belirteci biçimi
 Belirteçleri başlayıp dolar işareti ($) karakterini ile bitmelidir. Bir projeyi bir SharePoint çözüm paketini paketlendiğinde, dağıtımda kullanılan herhangi bir belirtece gerçek değerlerle değiştirilir (*.wsp* dosyası). Örneğin, belirteç **$SharePoint.Package.Name$** "Test SharePoint paketi" dizeye çözebilir.  
  
## <a name="token-rules"></a>Belirteç kuralları
 Belirteçleri aşağıdaki kurallar geçerlidir:  
  
- Belirteçleri, bir satırda herhangi bir yere belirtilebilir.  
  
- Belirteçleri, çok satırlı yayılamaz.  
  
- Aynı belirteci ile aynı satırda ve aynı dosyanın birden çok kez belirtilebilir.  
  
- Aynı satırda farklı belirteçleri belirtilebilir.  
  
  Bu kurallar izlemeyin belirteçleri göz ardı edilir ve bir uyarı veya hata neden değil.  
  
  Dize değerleri tarafından belirteçlerin değiştirme hemen sonra bildirim dönüştürme yapılır. Bu değişiklik, kullanıcının belirteçleriyle bildirim şablonları düzenlemenize olanak sağlar.  
  
### <a name="token-name-resolution"></a>Belirteç ad çözümlemesi
 Çoğu durumda, belirli bir değerin bulunduğu bağımsız olarak bir belirteç çözümler. Ancak, belirtecin bir paket veya özellik ile ilişkili ise, belirtecin değeri, bulunduğu üzerinde bağlıdır. Bir özellik ise bir, ardından belirteci Örneğin, paket `$SharePoint.Package.Name$` "Paket A." değerine çözümler Aynı özellik paketi B ardından olup olmadığını `$SharePoint.Package.Name$` "Paket b" çözümler  
  
## <a name="tokens-list"></a>Belirteçlerin listesi
 Aşağıdaki tabloda, kullanılabilir belirteçler listeler.  
  
|Ad|Açıklama|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Adı içeren proje dosyası, gibi *NewProj.csproj*.|  
|$SharePoint.Project.FileNameWithoutExtension$|Dosya adı uzantısı olmadan içeren proje dosyasının adı. Örneğin, "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Derleme çıkışını içeren proje (tanımlayıcı ad) görünen adı.|  
|$SharePoint.Project.AssemblyFileName$|Derleme çıkışını içeren projenin adı.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Dosya adı uzantısı olmadan, derleme çıkışını içeren projenin adı.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Ortak anahtar belirteci içeren proje çıkış bütünleştirilmiş koduna bir dizeye dönüştürülür. ("x2" 16 karakter on altılık biçimde.)|  
|$SharePoint.Package.Name$|İçeren paketin adı.|  
|$SharePoint.Package.FileName$|İçeren paket tanım dosyası adı.|  
|$SharePoint.Package.FileNameWithoutExtension$|İçeren paket tanım dosyası adı (uzantısı olmadan).|  
|$SharePoint.Package.Id$|İçeren paketin SharePoint kimliği. Bir özelliği birden fazla pakette kullandıysanız, bu değeri değiştirin.|  
|$SharePoint.Feature.FileName$|Tanım dosyasının içeren özellik adı, gibi *Feature1.feature*.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Dosya adı uzantısı olmadan Özellik tanım dosyasının adı.|  
|$SharePoint.Feature.DeploymentPath$|Paket özelliği içeren klasörün adı. Bu belirteç, özellik Tasarımcısı'nda "Dağıtım yolu" özelliğine karşılık gelir. Örnek değer olduğundan, "Project1_Feature1".|  
|$SharePoint.Feature.Id$|İçeren özelliğin SharePoint kimliği. Bu belirteç tüm özellik düzeyinde belirteçleri ile yalnızca bir özelliği aracılığıyla bir pakette bulunan dosyalar tarafından kullanılan bir özellik dışında bir paket için doğrudan eklenmedi.|  
|$SharePoint.ProjectItem.Name$|Öğesinden alınan olarak (kendi dosya adı değil), proje öğesinin adını **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. AssemblyQualifiedName$|Türü eşleşen derleme nitelenmiş adı [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] belirtecin. Biçimi [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] küçük harf ve Guid.ToString("D") biçimine karşılık gelir (yani xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
|$SharePoint.Type. \<GUID >. FullName$|Belirteçteki GUID eşleşen türü tam adı. GUID biçimi küçük harf ve Guid.ToString("D") biçimine karşılık gelir (yani xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Belirteç değiştirme dosya uzantıları listesi için uzantılar ekleme
 Belirteçleri teorik olarak bir SharePoint proje öğesi, varsayılan olarak, pakete ait olduğu herhangi bir dosyayı tarafından kullanılabilmesine rağmen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] belirteçleri yalnızca şu uzantılara sahip dosyalar paket dosyalarını ve bildirim dosyaları arar:  
  
- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
- ASCX  
  
- ASPX  
  
- Web Bölümü  
  
- DWP  
  
  Bu uzantılar tarafından tanımlanan `<TokenReplacementFileExtensions>` Microsoft.VisualStudio.SharePoint.targets dosyasında bulunan öğe... \\< program dosyaları\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools klasör.  
  
  Ancak, ek dosya uzantıları listesine ekleyebilirsiniz. Ekleme bir `<TokenReplacementFileExtensions>` önce tanımlanan tüm PropertyGroup SharePoint proje dosyasında öğesine \<alma > SharePoint hedefler dosyasının.  
  
> [!NOTE]  
>  Proje derlendikten sonra belirteç değiştirme oluştuğu için aşağıdaki gibi derlenen dosya türleri için dosya uzantıları eklememelisiniz *.cs*, *.vb* veya *.resx*. Belirteçleri değil derlenen dosyalarında değiştirilir.  
  
 Örneğin, dosya adı uzantısı eklemek için (*.myextension* ve *.yourextension*) belirteç değiştirme dosya adı uzantıları listesine bir projeye aşağıdaki eklersiniz (*.csproj* ) dosyası:  
  
```xml  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Uzantı hedeflerini ekleyebilirsiniz (*.targets*) dosyası. Ancak, uzantı değiştiren yerel sistemde paketlenen tüm SharePoint projeleri için Uzantılar listesi ekleme, yalnızca değil, kendi. Bu uzantı, sistemdeki tek Geliştirici olduğunuzda ya da projelerinizi çoğunu gerekiyorsa uygun olabilir. Ancak, sisteme özgü olduğundan, bu yaklaşım taşınabilir değildir ve bu nedenle önerilir, herhangi bir uzantısı proje dosyasına bunun yerine ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)  
  
