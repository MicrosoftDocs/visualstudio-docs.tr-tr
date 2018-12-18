---
title: Sunucu ve istemci yapılandırma sorunları ClickOnce Dağıtımları içinde | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 8cf7a6db209bb6bbed1d8044bbdc3ed106e64836
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948947"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce Dağıtımlarında Sunucu ve İstemci Yapılandırma Sorunları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Server Internet Information Services (IIS) kullanın ve dağıtımınız Windows tanımadığı bir dosya içeriyorsa, bir Microsoft Word dosyası gibi dosya aktarmak IIS reddeder ve dağıtımınızın başarılı olmaz.  
  
 Ayrıca, bazı Web sunucuları ve uygulama yazılımı gibi Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], dosyaların listesini içeren ve dosya karşıdan yükleyemiyor türleri. Örneğin, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] tüm Web.config dosyalarını indirilmesini engeller. Bu dosyalar, kullanıcı adları ve parolalar gibi hassas bilgiler içerebilir.  
  
 Bu kısıtlama çekirdek bir soruna neden olmaz ancak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bildirimleri ve derlemeler gibi dosyaları, bu kısıtlama engelleyebilir parçası olarak dahil edilen veri dosyaları indirmesini, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama. İçinde [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], IIS Yapılandırma Yöneticisi'nden tür dosyaların karşıdan yüklenmesini yasaklar işleyici kaldırarak bu hatayı çözebilirsiniz. Ek ayrıntılar için IIS sunucusu belgelerine bakın.  
  
 Bazı Web sunucuları gibi .mdf .dll ve .config uzantılı dosyaları engelleyebilir. Windows tabanlı uygulamaları genellikle bazı uzantılara sahip dosyaları içerir. Bir kullanıcı çalıştırmayı denerse bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] erişen bir Web sunucusunda engellenen bir dosya uygulama hataya neden olur. Tüm dosya uzantıları, kaldırma yerine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ".deploy" dosya uzantısına sahip her bir uygulama dosyası varsayılan olarak yayımlar. Bu nedenle, yöneticinin yalnızca aşağıdaki üç dosya uzantılarını engelini kaldırmak için Web sunucusunu yapılandırma gerekir:  
  
- .Application  
  
- .manifest  
  
- .deploy  
  
  Ancak, bu seçeneğin işaretini kaldırarak devre dışı bırakabilirsiniz **".deploy" dosya uzantısı** seçeneğini [Yayımlama Seçenekleri iletişim kutusu](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), bu durumda, tüm dosya uzantılarını engelini kaldırmak için Web sunucusu yapılandırmanız gerekir uygulamada kullanılır.  
  
  IIS olmayan yüklü kullanıyorsanız .manifest ve .application .deploy, örneğin, yapılandırma gerekecektir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], veya başka bir Web sunucusu (örn. Apache) kullanıyorsanız.  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce ve Güvenli Yuva Katmanı (SSL)  
 A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama düzgün çalışır, SSL üzerinden SSL sertifikası hakkında bir istem zaman Internet Explorer görüntülemesi dışında. Bir zaman site adları eşleşmiyor gibi sertifika veya sertifika ile bu sorun süresi dolmuş olduğunda istemi yükseltilebilir. Yapmak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir SSL bağlantısı üzerinden çalışma, sertifikanın güncel olduğunu ve site verileri eşleşen sertifika veri emin olun.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce ve Ara sunucu kimlik doğrulaması  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .NET Framework 3. 5 ' başlayarak Windows tümleşik Ara sunucu kimlik doğrulaması için destek sağlar. Özel machine.config yönergeleri gereklidir. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Temel veya Özet gibi diğer kimlik doğrulama protokolleri için destek sağlamaz.  
  
 Bu özelliği etkinleştirmek için .NET Framework 2.0 için bir düzeltme de uygulayabilirsiniz. Daha fazla bilgi için bkz. http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Daha fazla bilgi için [ \<defaultProxy > öğesi (ağ ayarları)](http://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce ve Web tarayıcı uyumluluğu  
 Şu anda [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] yüklemeler yalnızca dağıtım bildirimini URL, Internet Explorer'ı kullanarak açıldığında başlatılır. Yalnızca Internet Explorer varsayılan Web tarayıcısı ayarlanırsa URL'si Microsoft Office Outlook gibi başka bir uygulamadan başlatılan bir dağıtım başarılı bir şekilde başlatılır.  
  
> [!NOTE]
>  Mozilla Firefox, dağıtım sağlayıcısı boş veya Microsoft .NET Framework Assistant uzantı yüklü değilse desteklenir. Bu uzantı, .NET Framework 3.5 SP1 ile paketlenmiştir. XBAP desteği NPWPF eklentisi gerektiğinde etkinleştirilir.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>ClickOnce uygulamalarını tarayıcı betikler aracılığıyla etkinleştirme  
 Geliştirilmiş başlatan özel bir Web sayfası, bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] etkin komut dosyası kullanarak uygulamanın uygulama bazı makinelerde başlatmaz bulabilirsiniz. Internet Explorer olarak adlandırılan bir ayar içeriyor **Dosya indirmeleri için otomatik olarak sor**, bu davranışı etkiler. Bu ayar, üzerinde kullanılabilir **güvenlik** sekmesinde kendi **seçenekleri** bu davranışı etkiler menüsü. Çağrıldığı **Dosya indirmeleri için otomatik olarak sor**, ve altında listelenen **indirir** kategorisi. Özellik kümesine **etkinleştirme** intranet Web sayfaları ve için varsayılan **devre dışı** Internet Web sayfaları için varsayılan olarak. Bu ayar ayarlandığında **devre dışı**, yapmaya etkinleştirmek bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama program aracılığıyla (örneğin, gerçekleşen tarafından `document.location` özelliği) engellenir. Bu durumda, kullanıcıların yalnızca kullanıcı tarafından başlatılan bir indirme aracılığıyla uygulamaları gibi uygulamanın URL'sine ayarlayın bir köprüyü tıklatarak başlatabilirsiniz.  
  
## <a name="additional-server-configuration-issues"></a>Ek sunucu yapılandırma sorunları  
  
##### <a name="administrator-permissions-required"></a>Yönetici izinleri gerekir  
 HTTP ile yayımlıyorsanız hedef sunucuda yönetici izinleri olmalıdır. IIS bu izin düzeyini gerektirir. HTTP kullanarak yayımladığınız değil, yalnızca hedef yolunda izin yazmanız gerekir.  
  
##### <a name="server-authentication-issues"></a>Sunucu kimlik doğrulama sorunları  
 "Anonim erişimi devre dışı" olduğundan bir uzak sunucuya yayımladığınızda, aşağıdaki uyarıyı alırsınız:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  Site için varsayılan kimlik bilgilerinizi dışında kimlik bilgileri ister ve tıkladığınız güvenlik iletişim kutusunda, NTLM (NT sınama-yanıt) kimlik doğrulaması yapabilir **Tamam** sorulduğunda sağlanan kaydetmek istiyorsanız sonraki oturumlarda kimlik bilgileri. Ancak, bu çözüm için temel kimlik doğrulaması çalışmaz.  
  
## <a name="using-third-party-web-servers"></a>Üçüncü taraf Web sunucularını kullanma  
 Dağıtıyorsanız bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması dışında bir IIS Web sunucusundan, sorun yaşayabilirsiniz sunucu anahtarı için hatalı içerik türü döndürmesi durumunda [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım bildirimini ve uygulama bildirimi gibi dosyaları. Bu sorunu çözmek için Web sunucunuzun Yardım belgeleri sunucuya yeni içerik türlerini ekleyin ve tüm dosya adı uzantısı eşlemeler aşağıdaki tabloda listelenen emin hakkında mevcut olduğunu doğrulama bakın.  
  
|Dosya adı uzantısı|İçerik türü|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce ve eşlenen sürücüler  
 ClickOnce uygulaması yayımlama için Visual Studio kullanıyorsanız, eşlenmiş sürücü yükleme konumu olarak belirtemezsiniz. Ancak, eşlenmiş sürücüden Düzenleyicisi (Mage.exe ve MageUI.exe) ve Bildirim Oluşturucusu kullanarak yüklemek için ClickOnce uygulaması değiştirebilirsiniz. Daha fazla bilgi için [Mage.exe (bildirim üretme ve düzenleme aracı)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) ve [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP protokolünü uygulamaları yüklemek için desteklenmiyor  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] herhangi bir HTTP 1.1 Web sunucusu veya dosya sunucusu uygulamaları yüklemeyi destekler. FTP gibi Dosya Aktarım Protokolü, uygulamaları yüklemek için desteklenmiyor. Yalnızca uygulamaları yayımlamak için FTP kullanabilirsiniz. Aşağıdaki tabloda bu farklılıklar özetlenmiştir:  
  
|URL türü|Açıklama|  
|--------------|-----------------|  
|FTP: / /|Yayımlayabilmek için bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bu protokolü kullanarak uygulama.|  
|http://|Yükleyebileceğiniz bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bu protokolü kullanarak uygulama.|  
|https://|Yükleyebileceğiniz bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bu protokolü kullanarak uygulama.|  
|File://|Yükleyebileceğiniz bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bu protokolü kullanarak uygulama.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2'de: Windows Güvenlik Duvarı  
 Varsayılan olarak, Windows XP SP2, Windows Güvenlik Duvarı'nı etkinleştirir. Windows XP yüklü olduğu bir bilgisayarda uygulama geliştiriyorsanız, yayımlama ve çalıştırmak koruyabilmeyi [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] IIS çalıştıran sunucunun yerel uygulamalar. Ancak, Windows Güvenlik Duvarı açık değilse, IIS çalıştıran başka bir bilgisayardan o sunucuya erişemez. Windows Güvenlik Duvarı'nı yönetme hakkında yönergeler için Windows yardımına bakın.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: FrontPage sunucu uzantılarını etkinleştir  
 Microsoft FrontPage Server Extensions HTTP kullanan bir Windows Web sunucusundaki uygulama yayımlama için gereklidir.  
  
 Varsayılan olarak, FrontPage Server Extensions yüklü Windows Server yok. Kullanmak istiyorsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] FrontPage Server Extensions ile HTTP kullanan bir Windows Server Web sunucusuna yayımlamak için FrontPage Server Extensions önce yüklemelisiniz. Windows Server'da sunucunuzu yönetin Yönetim Aracı'nı kullanarak yükleme gerçekleştirebilirsiniz.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: Kilitli içerik türleri  
 IIS üzerinde [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] belirli bilinen içerik türü (örneğin, .htm, .html, .txt ve benzeri) hariç tüm dosya türlerini kilitler. Dağıtımını etkinleştirmek için [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bu sunucuyu kullanan uygulamalar, .application, .manifest ve uygulamanız tarafından kullanılan başka bir özel dosya türleri dosyalarının yüklenmesine izin verecek IIS ayarlarını değiştirmeniz gerekir.  
  
 Bir IIS sunucusu kullanarak dağıtırsanız, inetmgr.exe çalıştırın ve yeni dosya türleri için varsayılan Web Sayfası Ekle:  
  
- .Application ve .manifest uzantıları için MIME türü "application/x-ms-application." olmalıdır. Diğer dosya türleri için MIME türü "application/octet-stream." olmalıdır.  
  
- Bir MIME türü uzantı oluşturursanız, "*" ve MIME türü "application/octet-stream" yüklenmek üzere engellenmemiş dosya türlerinin sağlayacaktır. (Ancak, .aspx ve .asmx gibi türleri indirilen dosya engelledi.)  
  
  Windows Server'da MIME türleri yapılandırılıyor ayrıntılı yönergeler için Microsoft Bilgi Bankası makalesi KB326965, "IIS 6.0 mu değil hizmet bilinmeyen MIME türleri" başvurun [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>İçerik türü eşlemeleri  
 HTTP üzerinden yayımlarken, içerik türü (MIME türü olarak da bilinir) .application dosya "application/x-ms-application." olmalıdır Varsa [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] sunucuda yüklüyse, bu sizin için otomatik olarak ayarlanır. Bu yüklü değil ve ardından bir MIME türü ilişkilendirmesini oluşturmak için ihtiyacınız varsa [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama vroot (veya tüm sunucu).  
  
 Bir IIS sunucusu kullanarak dağıtırsanız, inetmgr.exe çalıştırın ve "application/x-ms-uygulama".application uzantısı için yeni bir içerik türü ekleyin.  
  
## <a name="http-compression-issues"></a>HTTP sıkıştırması sorunları  
 İle [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], gerçekleştirebilirsiniz HTTP sıkıştırması kullanan indirmeler, akış istemciye göndermeden önce veri akışını sıkıştırmak için GZIP algoritma kullanan bir Web sunucusu teknolojisi. İstemci — bu durumda, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]— dosyaları okumadan önce akışı açar.  
  
 IIS kullanıyorsanız, HTTP sıkıştırma kolayca etkinleştirebilirsiniz. HTTP sıkıştırmasını etkinleştirmek, ancak yalnızca belirli dosya türleri için etkin — yani, HTML ve metin dosyaları. Derlemeleri (.dll) için sıkıştırmayı etkinleştirmek için uygulama bildirimleri (.manifest) XML (.xml) ve dağıtım bildirimlerini (.application), bu dosya türlerini IIS'nin sıkıştırmasını türlerinde listesine eklemeniz gerekir. Yalnızca metin ve HTML dosyaları, dosya türlerini dağıtıma ekleme kadar sıkıştırılır.  
  
 IIS hakkında ayrıntılı yönergeler için bkz. [HTTP sıkıştırma için ek belge türlerini belirtmek nasıl](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Uygulama Dağıtımının Önkoşulları](../deployment/application-deployment-prerequisites.md)



