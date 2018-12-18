---
title: 'Hata: Web sunucusunda hata ayıklama başlatılamıyor | Microsoft Docs'
ms.custom: ''
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e58f8152d5c927271161bbf9615b1dfe3944e6dd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478258"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Hata: Web Sunucusunda Hata Ayıklama Başlatılamıyor

Bir Web sunucusu üzerinde çalışan bir ASP.NET uygulaması hata ayıklama çalıştığınızda, bu hata iletisini alabilirsiniz: `Unable to start debugging on the Web server`.

Bu hata genellikle, bir güncelleştirme, uygulama havuzları, bir IIS sıfırlama veya her ikisini de gerektiren bir hata veya yapılandırma değişikliği oluştu nedeniyle oluşur. Yükseltilmiş bir komut istemi'ni açıp yazarak IIS'yi sıfırlayın `iisreset`. 

## <a name="specificerrors"></a>Ayrıntılı hata iletisi nedir?

`Unable to start debugging on the Web server` İleti geneldir. Genellikle, daha belirli bir ileti hata dizesi içinde bulunur ve sorunu ya da daha kesin bir düzeltme için arama nedenini belirlemenize yardımcı olabilir. Birkaç ana hata iletisi eklenir daha sık karşılaşılan hata iletileri şunlardır:

- [IIS başlatma eşleşen bir Web sitesi listesinde değil URL'si](#IISlist)
- [Web sunucusu doğru yapılandırılmamış](#web_server_config)
- [Web sunucusu için bağlantı kurulamıyor](#unabletoconnect)
- [Web sunucu zamanında yanıt vermedi](#webservertimeout)
- [Microsoft visual studio uzaktan hata ayıklama monitor(msvsmon.exe) uzak bilgisayar üzerinde çalışıyor görünmüyor](#msvsmon)
- [Uzak sunucu bir hata döndürdü](#server_error)
- [ASP.NET hata ayıklama başlatılamıyor](#aspnet)
- [Hata ayıklayıcıyı uzak bilgisayara bağlanamıyor](#cannot_connect)
- [Bkz. ortak yapılandırma hataları için Yardım. Web sayfası hata ayıklayıcı dışında çalışan daha fazla bilgi sağlayabilir.](#see_help)

## <a name="IISlist"></a> IIS başlatma eşleşen bir Web sitesi listesinde değil URL'si

- Yönetici olarak Visual Studio'yu yeniden başlatın ve hata ayıklama yeniden deneyin. (Bazı ASP.NET hata ayıklama senaryoları yükseltilmiş ayrıcalıklar gerektirir.)

    Her zaman Visual Studio kısayol simgesini sağ tıklayarak bir yönetici olarak çalıştırmak için Visual Studio yapılandırabilirsiniz seçme **Özellikler > Gelişmiş**ve her zaman bir yönetici olarak çalıştır seçeneğini belirleyin.

## <a name="web_server_config"></a> Web sunucusu doğru yapılandırılmamış

- Bkz: [hata: web sunucusu doğru yapılandırılmamış](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a> Web sunucusu için bağlantı kurulamıyor

- Visual Studio ile Web sunucusu aynı makine üzerinde çalışan ve kullanarak hata ayıklama olduğunuz **F5** (yerine **ekleme işlemi için**)? Proje özelliklerini açın ve proje doğru Web sunucusuna bağlanmak ve URL başlatmak için yapılandırıldığından emin olun. (Açık **Özellikler > Web > sunucuları** veya **Özellikler > hata ayıklama** proje türüne bağlı olarak. Web Forms projesi için açık **özellik sayfaları > Başlangıç Seçenekleri > sunucu**.)

- Aksi takdirde, uygulama havuzunu yeniden başlatın ve IIS'yi sıfırlayın. Daha fazla bilgi için bkz: [IIS yapılandırmanızı denetleyin](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a> Web sunucu zamanında yanıt vermedi

- IIS'yi sıfırlayın ve hata ayıklama yeniden deneyin. Hata ayıklayıcı birden çok IIS işlemine bağlı; sıfırlama bunları sonlandırır. Daha fazla bilgi için bkz: [IIS yapılandırmanızı denetleyin](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a> Microsoft visual studio uzaktan hata ayıklama monitor(msvsmon.exe) uzak bilgisayar üzerinde çalışıyor görünmüyor

- Uzak makinede ayıkladığınız durumunda olduğundan emin olun [yüklenir ve uzaktan hata ayıklayıcı çalıştıran](../debugger/remote-debugging.md). İleti bir güvenlik duvarı değinmektedir emin olun [düzeltmek güvenlik duvarı bağlantı noktaları](../debugger/remote-debugger-port-assignments.md) özellikle bir üçüncü taraf güvenlik duvarı kullanıyorsanız, açıktır.
- HOSTS dosyasını kullanıyorsanız, doğru bir şekilde yapılandırıldığından emin olun. Örneğin, kullanarak hata ayıklama **F5** (yerine **ekleme işlemi için**), ana proje özelliklerinizi olduğu gibi aynı proje URL'sini içermesi gerekir dosya **Özellikler > Web > sunucuları**  veya **Özellikler > hata ayıklama**proje türüne bağlı olarak.

## <a name="server_error"></a> Uzak sunucu bir hata döndürdü

Denetleyin, [IIS günlük dosyasına](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) hata kodlarını ve ek bilgiler ve bu IIS 7 için [blog gönderisi](https://blogs.iis.net/tomkmvp/troubleshoot-a-403).

Ayrıca, yaygın hata kodları ve bazı öneriler şunlardır.
- (403) Yasak. Bu hatanın birçok olası nedenleri vardır, günlük dosyası ve web sitesi için IIS güvenlik ayarlarını kontrol edin. Sunucunun web.config içerdiğinden emin olun `debug=true` derleme öğesindeki. Web uygulaması klasörünüze doğru izinlere sahip olduğunu ve uygulama havuzu yapılandırması (parola değişmiş olabilir) doğru olduğundan emin olun. Bkz: [IIS yapılandırmanızı denetleyin](#vxtbshttpservererrorsthingstocheck). Bu ayarları zaten doğru olduğundan ve yerel olarak hata ayıklama yaptığınız, ayrıca doğru sunucu türünü ve URL bağlanan doğrulayın (içinde **Özellikler > Web > sunucuları** veya **Özellikler > hata ayıklama**, proje türüne bağlı olarak).
- (503) sunucu kullanılamıyor. Uygulama havuzu bir hata veya yapılandırma değişikliği nedeniyle durdurulmuş. Uygulama havuzunu yeniden başlatın.
- (404) bulunamadı. Uygulama havuzu ASP.NET doğru sürümü için yapılandırıldığından emin olun.

## <a name="aspnet"></a> ASP.NET hata ayıklama başlatılamıyor

- Uygulama havuzunu yeniden başlatın ve IIS'yi sıfırlayın. Daha fazla bilgi için bkz: [IIS yapılandırmanızı denetleyin](#vxtbshttpservererrorsthingstocheck).
- URL yeniden yazdırmaya yapıyorsanız, bir URL yeniden yazdırmaya ile temel bir web.config sınayın. Bkz: **Not** hakkında URL yeniden yazma modülünde [IIS yapılandırmanızı denetleyin](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a> Hata ayıklayıcıyı uzak bilgisayara bağlanamıyor

Yerel olarak hata ayıklama yaptığınız, Visual Studio uzaktan hata ayıklayıcı 64-bit sürümü 64-bit uygulamalar hata ayıklamak için kullanan 32 bit bir uygulama olduğundan bu hata oluşabilir. Proje özelliklerini açın ve proje doğru Web sunucusu ve URL bağlanmak için yapılandırıldığından emin olun. (Açık **Özellikler > Web > sunucuları** veya **Özellikler > hata ayıklama** proje türüne bağlı olarak.)

Ayrıca, bir ana bilgisayar dosyası kullanıyorsanız, doğru bir şekilde yapılandırıldığından emin olun. Örneğin, ana proje özelliklerinizi olduğu gibi aynı proje URL'sini içermesi gerekir dosya **Özellikler > Web > sunucuları** veya **Özellikler > hata ayıklama**proje türüne bağlı olarak.

## <a name="see_help"></a> Bkz. ortak yapılandırma hataları için Yardım. Web sayfası hata ayıklayıcı dışında çalışan daha fazla bilgi sağlayabilir.

- Visual Studio ile Web sunucusu aynı makinede çalışan? Proje özelliklerini açın ve proje doğru Web sunucusuna bağlanmak ve URL başlatmak için yapılandırıldığından emin olun. (Açık **Özellikler > Web > sunucuları** veya **Özellikler > hata ayıklama** proje türüne bağlı olarak.)

- İşe veya uzaktan hata ayıklama yaptığınız, izleyeceğiniz adımlar [IIS yapılandırmanızı denetleyin](#vxtbshttpservererrorsthingstocheck).

##  <a name="vxtbshttpservererrorsthingstocheck"></a> IIS yapılandırmanızı denetleyin

Burada sorunu gidermek için ayrıntılı adımlar aldıktan sonra ve hata ayıklamak yeniden denemeden önce IIS sıfırlamanız gerekebilir. Yükseltilmiş bir komut istemi'ni açıp yazarak bunu, `iisreset`. 

* Durdur ve IIS uygulama havuzlarını yeniden başlatın ve sonra yeniden deneyin. 

    Uygulama havuzu bir hata nedeniyle durdurulmuş. Veya, yaptığınız başka bir yapılandırma değişikliği durdurun ve uygulama havuzunu yeniden başlatın.
    
    > [!NOTE]
    > Uygulama havuzu durdurma tutar, Denetim Masası'ndan URL yeniden yazma modülü kaldırmanız gerekebilir. Web Platformu Yükleyicisi (Webpı) kullanarak yeniden yükleyebilirsiniz. Bu sorun, önemli sistem yükseltmeden sonra ortaya çıkabilir.

* Uygulama havuzu yapılandırmanızı denetleyin, gerekiyorsa düzeltin ve sonra yeniden deneyin.

    Uygulama havuzu, Visual Studio projesi eşleşmiyor ASP.NET sürümü için yapılandırılabilir. Uygulama havuzundaki ASP.NET sürümünü güncelleştirin ve yeniden başlatın. Ayrıntılı bilgi için bkz: [IIS 8.0 kullanarak ASP.NET 3.5 ve ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Ayrıca, parola kimlik bilgileri değiştiyse, uygulama havuzu veya Web sitesi güncelleştirme gerekebilir.  Uygulama havuzu kimlik bilgilerini güncelleştirin **Gelişmiş Ayarlar > işlem modeli > kimlik**. Web sitesi için kimlik bilgilerini güncelleştirin **temel ayarlar > Farklı Bağlan...** . Uygulama havuzunu yeniden başlatın.
    
* Web uygulaması klasörünüze doğru izinlere sahip olup olmadığını denetleyin.

    IIS_IUSRS, IUSR, size veya özel kullanıcı ilişkili olduğundan emin olun [uygulama havuzu](/iis/manage/configuring-security/application-pool-identities) okuma ve yürütme hakları Web uygulama klasörü için. Sorunu düzeltin ve uygulama havuzunu yeniden başlatın.

* IIS üzerinde ASP.NET doğru sürümünün yüklü olduğundan emin olun.

    ASP.NET IIS ve Visual Studio projenizi uyumsuz sürümlerini bu soruna neden olabilir. Web.config dosyasında framework sürümü ayarlamanız gerekebilir. IIS üzerinde ASP.NET yüklemek için kullandığınız [Web Platformu Yükleyicisi (Webpı)](https://www.microsoft.com/web/downloads/platform.aspx). Ayrıca bkz [IIS 8.0 kullanarak ASP.NET 3.5 ve ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) veya ASP.NET Core [IIS ile Windows konakta](https://docs.asp.net/en/latest/publishing/iis.html).
  
* Yalnızca IP adresi kullanıyorsanız, kimlik doğrulama hatalarını çözümleme

     Varsayılan olarak, IP adresleri Internet bir parçası olarak kabul edilir ve Internet üzerinden NTLM kimlik doğrulaması yapılmadı. Web sitenizi IIS kimlik doğrulaması gerektirecek şekilde yapılandırılmışsa, bu kimlik doğrulama başarısız olur. Bu sorunu düzeltmek için uzak bilgisayarın IP adresi yerine adını belirtebilirsiniz.
     
## <a name="other-causes"></a>Diğer nedenler

IIS yapılandırmasını soruna neden değil, aşağıdaki adımları deneyin:

- Yönetici ayrıcalıklarıyla Visual Studio'yu yeniden başlatın ve yeniden deneyin.

    Web dağıtımı kullanarak gibi bazı ASP.NET hata ayıklama senaryoları için Visual Studio yükseltilmiş ayrıcalıklar gerektirir.
    
- Visual Studio birden çok örneğini çalıştırıyorsanız, Visual Studio'nun bir örneği (yönetici ayrıcalıklarıyla) projenizde yeniden açın ve yeniden deneyin.

- HOSTS dosyasını ile yerel adresler kullanıyorsanız, geri döngü adres makinenin IP adresi yerine kullanmayı deneyin.

    Yerel adresler kullanmıyorsanız, HOSTS dosyasını proje özelliklerinizi olduğu gibi aynı proje URL'sini içerdiğinden emin olun **Özellikler > Web > sunucuları** veya **Özellikler > hata ayıklama**bağlı olarak, Proje türü seçin.

## <a name="more-troubleshooting-steps"></a>Daha fazla sorun giderme adımları

* Sunucu üzerindeki tarayıcıda localhost sayfasını duruma getirin.

     IIS düzgün yüklü değilse, yazarken hataları almalısınız `http://localhost` bir tarayıcıda.
     
     IIS dağıtma hakkında daha fazla bilgi için bkz: [IIS 8.0 kullanarak ASP.NET 3.5 ve ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ve ASP.NET Core [IIS ile Windows konakta](https://docs.asp.net/en/latest/publishing/iis.html).

* Sunucuda temel bir ASP.NET uygulaması oluşturun (veya bir temel web.config dosyası kullanın).

    Hata ayıklayıcı ile çalışmak için uygulamanızı alınamıyor, temel bir ASP.NET uygulama sunucusunda yerel olarak oluşturma deneyin ve temel uygulama hata ayıklamak deneyin. (Varsayılan ASP.NET MVC şablonu kullanmak isteyebilirsiniz.) Temel bir uygulama hata ayıklama, iki yapılandırması arasında farklı nedir belirlemenize yardımcı olabilir. URL yeniden yazma kuralları gibi ayarları farklılıkları web.config dosyasına bakın.

## <a name="see-also"></a>Ayrıca Bkz.  
 [Web uygulamalarında hata ayıklama: Hatalar ve sorun giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)