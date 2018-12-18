---
title: Web sitesi desteği şablonları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af8e0d845157b475e4a5527443f55286828023cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147134"
---
# <a name="web-site-support-templates"></a>Web sitesi şablonları destekler
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Web sitesi proje ve öğe şablonları, yeni Web sitesi projeler ve öğeler sıfırdan oluşturma gereksinimini ortadan kaldırarak geliştirme işlemi hızlandırmak yeniden kullanılabilir ve özelleştirilebilir Web sitesi proje ve öğe saplamalar sağlar. Daha fazla bilgi için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] şablonları için bkz: [oluşturma proje ve öğe şablonlarını](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Proje şablonu klasörü
 Web projesi şablonları genellikle yüklenen [*Visual Studio yükleme yolu*] \Common7\IDE\ProjectTemplates\Web\\, her programlama dili web sonra adlı bir alt klasörü.

## <a name="project-file"></a>Proje Dosyası
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı (IDE) doğru proje türü için bir şablon eşleştirmek için bir yol olarak proje dosya uzantısının gerektirir. Web projeleri bir proje dosyası olmadığından kukla proje dosya uzantısı .webproj Şablonu proje türüyle eşleştirmek için kaydedilir.

 Bir dil adı dizesini dil varsayılan ayarlamak Web projesi sistemi etkinleştirmek için şablon, isteğe bağlı olarak eklenebilir **Yeni Öğe Ekle** öğeleri için iletişim kutusu şablona dayalı. Dize dosyasının ilk satırı olmalıdır. IntelliSense altyapısı kaydında altında AddItemLanguageName kayıtlı adı hem proje Subtype(VsTemplate) altında kayıtlı adı eşleşmelidir. Daha fazla bilgi için bkz: [Web sitesi desteği öznitelikleri](../../extensibility/internals/web-site-support-attributes.md).

 Dize mevcut değilse, Web projesi sistemi proje şablonu tarafından Web projesine eklendi sayfaları dil özniteliği ve dosya uzantıları göre varsayılan dili belirlemeye çalışır.

## <a name="project-templates"></a>Proje şablonları
 Yanıt olarak yeni Web siteleri oluşturmak için kullanılan Web sitesini proje şablonları **yeni Web sitesi** komutunu **dosya** menüsü. Şu anda desteklenen üç Web sitesi proje türleri:

-   Boş Web sitesi projeleri

-   Web sitesi projeleri

-   Web hizmeti projeleri

### <a name="empty-web-site-projects"></a>Boş Web sitesi projeleri
 Bu dosyaları yanıt olarak yeni ve boş bir Web sitesi oluşturmak **boş Web sitesi** seçtikten sonra kullanılabilir komut **dosya** > **yeni Web sitesi**:

-   EmptyWeb.vstemplate

     Yeni boş Web sitesi oluşturma sırasında size kılavuzluk eder şablon dosyası.

-   EmptyWeb.webproj

     Proje şablonu sisteminin bir yapı dosyasıdır. Proje dosyası başvurusu EmptyWeb.vstemplate dosyasında karşılar.

### <a name="web-site-projects"></a>Web sitesi projeleri
 Bu dosyaları yanıt olarak yeni bir Web sitesi oluşturmak **ASP.NET Web sitesi** seçtikten sonra kullanılabilir komut **dosya** > **yeni Web sitesi**:

-   Default.aspx

     Yeni Web sitesi için varsayılan giriş sayfası. Language özniteliği arkasındaki koda dilini belirtir ve bu sayfayla ilişkili arkasındaki koda kodunu içerir bağımlı dosya CodeFile özniteliği belirtir.

-   Default.aspx. *uzantısı*

     Varsayılan giriş sayfası arkasındaki koda kodunu içerir bağımlı dosya. Arkasındaki koda dilini belirler *uzantısı* bu dosyanın.

-   Web.config

     Kök web.site yapılandırma dosyası.

-   WebApplication.vstemplate

     Web sitesi çözümü içeriğini belirler ve App_Data klasöründe oluşturulmasını zorlar şablon dosyası.

-   WebApplication.webproj

     Proje şablonu sisteminin bir yapı dosyasıdır. Proje dosyası başvurusu WebApplication.vstemplate dosyasında karşılar.

### <a name="web-service-projects"></a>Web hizmeti projeleri
 Bu dosyaları yanıt olarak yeni bir Web sitesi oluşturmak **ASP.NET Web hizmeti** seçtikten sonra kullanılabilir komut **dosya** > **yeni Web sitesi**:

-   QuoteService.asmx'e değiştirin

     Yeni Web hizmeti için HTML sayfası. Language özniteliği arkasındaki koda dilini belirler ve bu hizmetle ilişkilendirilen arkasındaki koda kodunu içerir bağımlı dosyayı arkasındaki koda özniteliği belirtir.

-   Hizmet. *Uzantısı*

     Hizmet sınıfı uygulayan bağımlı dosya. Arkasındaki koda dilini belirler *uzantısı* bu dosyanın.

-   Web.config

-   Kök web.site yapılandırma dosyası.

-   WebService.vstemplate

     Web sitesi çözümü içeriğini belirler ve App_Data ve App_Code klasörleri oluşturmaya zorlar şablon dosyası. Hizmet. *uzantısı* dosyasının App_Code klasörüne kopyalanır.

-   WebService.webproj

     Proje şablonu sisteminin bir yapı dosyasıdır. Proje dosyası başvurusu WebService.vstemplate dosyasında karşılar.

## <a name="project-item-template-folder"></a>Proje öğesi şablonu klasörü
 Web proje öğesi şablonları içinde yüklü genellikle [*Visual Studio yükleme yolu*] \Common7\IDE\ItemTemplates\Web\\, her programlama dili kendi web sonra adlı bir alt klasörü.

## <a name="project-item-templates"></a>Proje öğesi şablonları
 Bir Web sitesine yanıt olarak yeni Web sayfaları eklemek için kullanılan Web sitesini proje öğesi şablonları **varolan öğeyi Ekle** komutu. Bu tür Web sayfalarının şu anda desteklenir:

-   Yeni bir sınıf

-   Yeni HTML sayfası

-   Yeni bir Web formu

-   Yeni ana sayfa

### <a name="new-class"></a>Yeni bir sınıf
 Bu şablon yanıt olarak boş bir sınıf tanımlayan yeni bir kaynak dosyası oluşturur **yeni sınıf Ekle** komutu.

-   Sınıf. *Uzantısı*

     Boş sınıfı uygulayan kaynak dosya. Arkasındaki koda dilini belirler *uzantısı* bu dosyanın.

-   Class.vstemplate

     Kaynak dosyası oluşturur ve içeriği belirleyen şablon dosyası.

### <a name="new-html-page"></a>Yeni HTML sayfası
 Bu şablon, yanıt olarak yeni bir Web sayfası oluşturur. **yeni HTML sayfası Ekle** komutu.

-   HTMLPage.htm

     Web sayfasının başlangıç içeriği. Bu Web sayfası genellikle herhangi bir ilişkili arkasındaki koda bağımlı dosyası vardır. Bir akıllı sayfası ile ilişkili arkadaki kod dosyası oluşturmak için Web Form şablonunu kullanın.

-   HTMLPage.vstemplate

     Web sayfası oluşturur ve içeriği belirleyen şablon dosyası.

### <a name="new-webform"></a>Yeni Web formu
 Bu şablon, yanıt olarak yeni bir akıllı Web sayfası oluşturur. **ekleme yeni bir Web formu** komutu.

 Bağımlı arkasındaki koda kaynak dosyası oluşturmak için seçin **kod ayrı bir dosyaya yerleştirin**. Aksi takdirde, tek bir Web sayfası boş bir betik bloğu ve Hayır sahip oluşturulur \<% sayfa % > yönergeleri bağımlı dosyasını yedekleyin bağlayın.

 Seçili ana sayfa için bir içerik sayfasını oluşturmak için seçin **Select ana sayfa**.

-   WebForm.aspx

     Web sayfasının başlangıç içeriği. Bu Web sayfası hiçbir ilişkili arkasındaki koda bağımlı dosya vardır.

-   WebForm_cb.aspx

     Web sayfasının başlangıç içeriği. Bu Web sayfasında ilişkili arkasındaki koda bağımlı dosya vardır.

-   Arkasındaki koda. *Uzantısı*

     Webform sınıfı uygulayan bağımlı dosya. Arkasındaki koda dilini belirler *uzantısı* bu dosyanın.

-   ContentPage.aspx

     Web sayfası bir içerik sayfasını olarak başlangıç içeriği. Bu Web sayfası hiçbir ilişkili arkasındaki koda bağımlı dosya vardır.

-   ContentPage_cb.aspx

     Web sayfası bir içerik sayfasını olarak başlangıç içeriği. Bu Web sayfasında ilişkili arkasındaki koda bağımlı dosya vardır.

-   WebForm.vstemplate

     Yeni web sayfası ve onun bağımlı dosya içeriğini miktarı belirler şablon dosyası.

### <a name="new-master-page"></a>Yeni ana sayfa
 Bu şablon, yanıt olarak yeni bir ana sayfa oluşturur **ekleme yeni ana sayfa** komutu.

 Bağımlı arkasındaki koda kaynak dosyası oluşturmak için seçin **kod ayrı bir dosyaya yerleştirin**. Tek bir Web sayfası boş bir betik bloğu ve Hayır sahip Aksi takdirde oluşturulan \<% sayfa % > yönergeleri bağımlı dosyasını yedekleyin bağlayın.

-   MasterPage.master

     Ana sayfaya başlangıç içeriği. Bu ana sayfa hiçbir ilişkili arkasındaki koda bağımlı dosya vardır.

-   MasterPage_cb.master

     Ana sayfaya başlangıç içeriği. Bu ana sayfa ilişkili arkasındaki koda bağımlı dosya vardır.

-   Arkasındaki koda. *uzantısı*

     Ana sayfa sınıfı uygulayan bağımlı dosya. Arkasındaki koda dilini belirler *uzantısı* bu dosyanın.

-   MasterPage.vstemplate

     Yeni ana sayfa ve onun bağımlı dosya içeriğini miktarı belirler şablon dosyası.

## <a name="see-also"></a>Ayrıca Bkz.
 [Web Sitesi Desteği](../../extensibility/internals/web-site-support.md)