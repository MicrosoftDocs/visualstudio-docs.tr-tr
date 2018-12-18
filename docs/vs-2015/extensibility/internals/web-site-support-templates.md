---
title: Web sitesi destek şablonları | Microsoft Docs
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
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eebacb3006826a90320cbc61edf7d56467e688ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760227"
---
# <a name="web-site-support-templates"></a>Web Sitesi Destek Şablonları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Web sitesi proje ve öğe şablonları, yeni Web sitesi projeleri ve öğeleri sıfırdan oluşturma gereksinimini ortadan kaldırarak geliştirme sürecini hızlandırmak Web sitesini yeniden kullanılabilir ve özelleştirilebilir proje ve öğe saptamalar sağlar. Daha fazla bilgi için [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] şablonları, [oluşturma proje ve öğe şablonları](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Proje şablonu klasörü  
 Web projesi şablonu şablonları genellikle yüklenen [*Visual Studio yükleme yolu*] \Common7\IDE\ProjectTemplates\Web\\, her programlama dilinde web sonra adlı bir alt klasör.  
  
## <a name="project-file"></a>Proje Dosyası  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tümleşik geliştirme ortamı (IDE) doğru proje türü için bir şablon bir yolu olarak bir proje dosyasının uzantısına gerektirir. Web projeleri bir proje dosyası olmadığından işlevsiz proje dosya uzantısı .webproj Bunu desteklemek için kaydedilir.  
  
 İsteğe bağlı olarak, bir dil adı dizesi Web Proje sisteminin dil varsayılan kümesinde etkinleştirmek için şablon eklenebilir **Yeni Öğe Ekle** iletişim kutusu öğeleri için şablona dayalı. Dize, dosyanın ilk satırı olmalıdır ve hem IntelliSense altyapısı kaydında AddItemLanguageName altında kayıtlı adı hem de proje Subtype(VsTemplate) altında kayıtlı adı ile eşleşmelidir. Daha fazla bilgi için [Web sitesi destek öznitelikleri](../../extensibility/internals/web-site-support-attributes.md).  
  
 Dize mevcut değilse Web Proje sistemi proje şablonu şablon tarafından Web projesine eklediğiniz sayfaları dil özniteliği ve dosya uzantıları temel varsayılan dili belirlemeye çalışır.  
  
## <a name="project-templates"></a>Proje şablonları  
 Yanıt olarak yeni Web siteleri oluşturmak için kullanılan Web sitesi projesi şablonları **yeni Web sitesi** komutunu **dosya** menüsü. Şu anda desteklenen üç Web sitesi projesi türleri:  
  
-   Boş Web sitesi projeleri  
  
-   Web sitesi projeleri  
  
-   Web hizmeti projelerini Microsoft Azure  
  
### <a name="empty-web-site-projects"></a>Boş Web sitesi projeleri  
 Bu dosyalar, yanıt olarak yeni bir boş Web sitesi oluşturma **boş Web sitesi** işaret sonra kullanılabilir olan komut **yeni Web sitesi** üzerinde **dosya** menüsü:  
  
-   EmptyWeb.vstemplate  
  
     Yeni bir boş Web sitesi oluşturmayı kılavuzları şablon dosyası.  
  
-   EmptyWeb.webproj  
  
     Bu dosya, proje şablonu sisteminin bir yapıdır. Bu proje dosyası başvurusu EmptyWeb.vstemplate dosyasındaki karşılar.  
  
### <a name="web-site-projects"></a>Web sitesi projeleri  
 Bu dosyalar, yanıt olarak yeni bir Web sitesi oluşturma **ASP.NET Web sitesi** işaret sonra kullanılabilir olan komut **yeni Web sitesi** üzerinde **dosya** menüsü:  
  
-   Default.aspx  
  
     Yeni Web sitesi için varsayılan giriş sayfası. Language özniteliği codebehind dilini belirtir ve bu sayfayla ilişkili codebehind kodu içeren bağımlı dosya CodeFile özniteliği belirtir.  
  
-   Default.aspx. *uzantısı*  
  
     Bağımlı dosya varsayılan giriş sayfasını codebehind kodunu içerir. Codebehind dili belirler *uzantısı* bu dosyanın.  
  
-   Web.config  
  
     Kök web.site yapılandırma dosyası.  
  
-   WebApplication.vstemplate  
  
     Web sitesi çözüm içeriğini belirler ve App_Data klasöründe oluşturulmasını zorlar şablon dosyası.  
  
-   WebApplication.webproj  
  
     Bu dosya, proje şablonu sisteminin bir yapıdır. Bu proje dosyası başvurusu WebApplication.vstemplate dosyasındaki karşılar.  
  
### <a name="web-service-projects"></a>Web hizmeti projelerini Microsoft Azure  
 Bu dosyalar, yanıt olarak yeni bir Web sitesi oluşturma **ASP.NET Web hizmeti** işaret sonra kullanılabilir olan komut **yeni Web sitesi** üzerinde **dosya** menüsü:  
  
-   QuoteService.asmx'e değiştirin  
  
     Yeni bir Web hizmeti için HTML sayfası. Language özniteliği codebehind dilini belirtir ve bu hizmetle ilişkili codebehind kodu içeren bağımlı dosya CodeBehind özniteliğinin belirtir.  
  
-   Hizmeti. *Uzantı*  
  
     Bağımlı dosya hizmet sınıfını uygular. Codebehind dili belirler *uzantısı* bu dosyanın.  
  
-   Web.config  
  
-   Kök web.site yapılandırma dosyası.  
  
-   WebService.vstemplate  
  
     Web sitesi çözüm içeriğini belirler ve App_Data ve App_Code klasörleri oluşturulmasını zorlar şablon dosyası. Hizmet. *uzantısı* dosya, App_Code klasörüne kopyalanır.  
  
-   WebService.webproj  
  
     Bu dosya, proje şablonu sisteminin bir yapıdır. Bu proje dosyası başvurusu WebService.vstemplate dosyasındaki karşılar.  
  
## <a name="project-item-template-folder"></a>Proje öğesi şablon klasörü  
 Web proje öğesi şablonu şablonları genellikle yüklenen [*Visual Studio yükleme yolu*] \Common7\IDE\ItemTemplates\Web\\, her programlama dilinde kendi web sonra adlı bir alt klasör.  
  
## <a name="project-item-templates"></a>Proje öğesi şablonları  
 Yeni Web sayfaları yanıt olarak bir Web sitesi eklemek için kullanılan Web sitesi proje öğesi şablonları **varolan öğeyi Ekle** komutu. Şu anda, bu tür bir Web sayfaları desteklenmektedir:  
  
-   Yeni sınıfı  
  
-   Yeni HTML sayfası  
  
-   Yeni Web formu  
  
-   Yeni ana sayfası  
  
### <a name="new-class"></a>Yeni sınıfı  
 Bu şablon, yanıt olarak boş bir sınıf tanımlayan yeni bir kaynak dosyası oluşturur. **yeni sınıf Ekle** komutu.  
  
-   sınıf. *Uzantı*  
  
     Boş sınıf uygulayan kaynak dosyası. Codebehind dili belirler *uzantısı* bu dosyanın.  
  
-   Class.vstemplate  
  
     Kaynak dosyası oluşturur ve içeriğini belirleyen şablon dosyası.  
  
### <a name="new-html-page"></a>Yeni HTML sayfası  
 Bu şablon, yanıt olarak yeni bir Web sayfası oluşturur. **yeni HTML sayfası Ekle** komutu.  
  
-   HTMLPage.htm  
  
     Başlangıç Web sayfası içeriği. Bu Web sayfası, genellikle hiçbir ilişkili codebehind bağımlı dosya vardır. Akıllı bir sayfa ile ilişkili bir dosyası oluşturmak için Web formu şablonu kullanın.  
  
-   HTMLPage.vstemplate  
  
     Web sayfası oluşturur ve içeriğini belirleyen şablon dosyası.  
  
### <a name="new-webform"></a>Yeni Web formu  
 Bu şablon, yanıt olarak yeni bir akıllı Web sayfası oluşturur. **yeni Web formu ekleyin** komutu.  
  
 Bağımlı bir kaynak dosyası oluşturmak için Seç **kod ayrı dosyaya Yerleştir**. Aksi takdirde tek bir Web sayfası boş bir komut dosyası bloğu ve Hayır sahip oluşturulur \<% sayfa % > bağımlı bir dosyanın yeteneklerinizi yönergeleri.  
  
 Seçilen ana sayfa için içerik sayfası oluşturmak için Seç **Select ana sayfa**.  
  
-   WebForm.aspx  
  
     Başlangıç Web sayfası içeriği. Bu Web sayfası hiçbir ilişkili codebehind bağımlı dosya vardır.  
  
-   WebForm_cb.aspx  
  
     Başlangıç Web sayfası içeriği. Bu Web sayfasında ilişkili codebehind bağımlı dosya vardır.  
  
-   Codebehind. *Uzantı*  
  
     Bağımlı dosya webform sınıfı uygular. Codebehind dili belirler *uzantısı* bu dosyanın.  
  
-   ContentPage.aspx  
  
     İçerik sayfası olarak Web sayfasının başlangıç içeriği. Bu Web sayfası hiçbir ilişkili codebehind bağımlı dosya vardır.  
  
-   ContentPage_cb.aspx  
  
     İçerik sayfası olarak Web sayfasının başlangıç içeriği. Bu Web sayfasında ilişkili codebehind bağımlı dosya vardır.  
  
-   WebForm.vstemplate  
  
     Varsa yeni web sayfası ve onun bağımlı dosya içeriğini belirleyen şablon dosyası.  
  
### <a name="new-master-page"></a>Yeni ana sayfası  
 Bu şablon, yanıt olarak yeni bir ana sayfası oluşturur. **yeni ana sayfa Ekle** komutu.  
  
 Bağımlı bir kaynak dosyası oluşturmak için Seç **kod ayrı dosyaya Yerleştir**. Aksi takdirde tek bir Web sayfası boş bir komut dosyası bloğu ve Hayır sahip oluşturulur \<% sayfa % > bağımlı bir dosyanın yeteneklerinizi yönergeleri.  
  
-   MasterPage.master  
  
     Ana sayfaya başlangıç içeriği. Bu ana sayfası hiçbir ilişkili codebehind bağımlı dosya vardır.  
  
-   MasterPage_cb.master  
  
     Ana sayfaya başlangıç içeriği. Bu ana sayfanın ilişkili codebehind bağımlı dosya vardır.  
  
-   Codebehind. *uzantısı*  
  
     Ana sayfa sınıfın uyguladığı bağımlı dosya. Codebehind dili belirler *uzantısı* bu dosyanın.  
  
-   MasterPage.vstemplate  
  
     Varsa yeni bir ana sayfa ve onun bağımlı dosya içeriğini belirleyen şablon dosyası.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Sitesi Desteği](../../extensibility/internals/web-site-support.md)

