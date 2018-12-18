---
title: Web sitesi destek öznitelikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 312d8a760cc7005afc4308b637b12a292bd20329
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756675"
---
# <a name="web-site-support-attributes"></a>Web Sitesi Destek Öznitelikleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Web sitesi projesi Web desteği sağlamak için programlama genişletilebilir. Dil kendisi ile kaydetmelisiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] böylece proje şablonları görünebilen **yeni Web sitesi** dil seçildiğinde iletişim kutusu.  
  
 IronPython Studio örnek web sitesi desteği içerir. İle bulabilirsiniz [VSSDK örnekleri](../../misc/vssdk-samples.md). Bu, IronPython, yeni Web projeleri için bir codebehind dili olarak kaydetmek için aşağıdaki öznitelik sınıfları içerir.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Bu öznitelik, dil projede yer alır. Web programlama dilleri listesini dili ekler **dil** listesinde **yeni Web sitesi** iletişim kutusu. Örneğin, aşağıdaki IronPython listeye ekler:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Bu öznitelik, ayrıca şablonları klasörüne işaret edecek şekilde şablonları yolunu ayarlar. Şablonları klasörünün konumu hakkında daha fazla bilgi için bkz. [Web sitesi destek şablonları](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Bu öznitelik, dil projede yer alır. Bir dosya türü (ilgili) içine yerleştirmek Web sitesi projesi başka bir dosya türü altında (birincil) verir **Çözüm Gezgini**.  
  
 Örneğin:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 bir .aspx dosyasına bir IronPython codebehind dosya ilgili olup olmadığını belirtir. Yeni bir .aspx Web sayfası bir IronPython Web sitesini çözümde oluşturulduğunda, yeni .py kaynak dosyası oluşturulur ve .aspx sayfasına bir alt düğüm olarak görünür.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Bu öznitelik dil proje pakete yerleştirildi. Bu dil için IntelliSense sağlayıcısı seçer.  
  
 Örneğin:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 belirten bir örneğini uygulayan PythonIntellisenseProvider <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, dil hizmetleri sağlamak amacıyla isteğe bağlı olarak oluşturulmalıdır.  
  
 IVsIntellisenseProject uygulama başvuruları işler ve bir Web sayfası koduna sahip istenen ancak önbelleğe alınmamış dil derleyicisini çağırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Sitesi Desteği](../../extensibility/internals/web-site-support.md)

