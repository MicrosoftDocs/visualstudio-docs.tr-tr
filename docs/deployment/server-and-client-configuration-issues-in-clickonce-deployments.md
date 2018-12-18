---
title: Sunucu ve istemci yapılandırma sorunları ClickOnce Dağıtımları içinde | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 444cfa375fd4e2059ddf6458224836cdec6ff18f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849449"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce dağıtımlarında sunucu ve istemci yapılandırma sorunları
Windows Server Internet Information Services (IIS) kullanın ve dağıtımınız Windows tanımadığı bir dosya içeriyorsa, bir Microsoft Word dosyası gibi dosya aktarmak IIS reddeder ve dağıtımınızın başarılı olmaz.  

 Ayrıca, bazı Web sunucuları ve uygulama yazılımı gibi Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], dosyaların listesini içeren ve dosya karşıdan yükleyemiyor türleri. Örneğin, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tüm indirilmesini engeller *Web.config* dosyaları. Bu dosyalar, kullanıcı adları ve parolalar gibi hassas bilgiler içerebilir.  

 Bu kısıtlama çekirdek bir soruna neden olmaz ancak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirimleri ve derlemeler gibi dosyaları, bu kısıtlama engelleyebilir parçası olarak dahil edilen veri dosyaları indirmesini, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama. İçinde [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], IIS Yapılandırma Yöneticisi'nden tür dosyaların karşıdan yüklenmesini yasaklar işleyici kaldırarak bu hatayı çözebilirsiniz. Ek ayrıntılar için IIS sunucusu belgelerine bakın.  

 Bazı Web sunucuları gibi uzantılara sahip dosyalar engelleyebilecek *.dll*, *.config*, ve *.mdf*. Windows tabanlı uygulamaları genellikle bazı uzantılara sahip dosyaları içerir. Bir kullanıcı çalıştırmayı denerse bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] erişen bir Web sunucusunda engellenen bir dosya uygulama hataya neden olur. Tüm dosya uzantıları, kaldırma yerine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yayımlar her uygulama dosyasını bir *.deploy* varsayılan dosya uzantısı. Bu nedenle, yöneticinin yalnızca aşağıdaki üç dosya uzantılarını engelini kaldırmak için Web sunucusunu yapılandırma gerekir:  

- *.Application*  

- *.manifest*  

- *.deploy* 

  Ancak, bu seçeneğin işaretini kaldırarak devre dışı bırakabilirsiniz **".deploy" dosya uzantısı** seçeneğini [Yayımlama Seçenekleri iletişim kutusu](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100)), bu durumda, tüm dosya uzantılarını engelini kaldırmak için Web sunucusu yapılandırmanız gerekir uygulamada kullanılır.  

  Yapılandırmanız gerekecektir *.manifest*, *.application*, ve *.deploy*, örneğin, IIS olmayan yüklü kullanıyorsanız [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], veya başka bir Web sunucusu (örn. Apache) kullanıyor.  

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce ve Güvenli Yuva Katmanı (SSL)  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama düzgün çalışır, SSL üzerinden SSL sertifikası hakkında bir istem zaman Internet Explorer görüntülemesi dışında. Bir zaman site adları eşleşmiyor gibi sertifika veya sertifika ile bu sorun süresi dolmuş olduğunda istemi yükseltilebilir. Yapmak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir SSL bağlantısı üzerinden çalışma, sertifikanın güncel olduğunu ve site verileri eşleşen sertifika veri emin olun.  

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce ve proxy kimlik doğrulaması  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .NET Framework 3. 5 ' başlayarak Windows tümleşik Ara sunucu kimlik doğrulaması için destek sağlar. Özel machine.config yönergeleri gereklidir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Temel veya Özet gibi diğer kimlik doğrulama protokolleri için destek sağlamaz.  

 Bu özelliği etkinleştirmek için .NET Framework 2.0 için bir düzeltme de uygulayabilirsiniz. Daha fazla bilgi için bkz. http://go.microsoft.com/fwlink/?LinkId=158730.  

 Daha fazla bilgi için [ \<defaultProxy > öğesi (ağ ayarları)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).  

## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce ve Web tarayıcı uyumluluğu  
 Şu anda [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yüklemeler yalnızca dağıtım bildirimini URL, Internet Explorer'ı kullanarak açıldığında başlatılır. Yalnızca Internet Explorer varsayılan Web tarayıcısı ayarlanırsa URL'si Microsoft Office Outlook gibi başka bir uygulamadan başlatılan bir dağıtım başarılı bir şekilde başlatılır.  

> [!NOTE]
>  Mozilla Firefox, dağıtım sağlayıcısı boş veya Microsoft .NET Framework Assistant uzantı yüklü değilse desteklenir. Bu uzantı, .NET Framework 3.5 SP1 ile paketlenmiştir. XBAP desteği NPWPF eklentisi gerektiğinde etkinleştirilir.  

## <a name="activate-clickonce-applications-through-browser-scripting"></a>ClickOnce uygulamaları tarayıcı betikler aracılığıyla etkinleştirme  
 Geliştirilmiş başlatan özel bir Web sayfası, bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] etkin komut dosyası kullanarak uygulamanın uygulama bazı makinelerde başlatmaz bulabilirsiniz. Internet Explorer olarak adlandırılan bir ayar içeriyor **Dosya indirmeleri için otomatik olarak sor**, bu davranışı etkiler. Bu ayar, üzerinde kullanılabilir **güvenlik** sekmesinde kendi **seçenekleri** bu davranışı etkiler menüsü. Çağrıldığı **Dosya indirmeleri için otomatik olarak sor**, ve altında listelenen **indirir** kategorisi. Özellik kümesine **etkinleştirme** intranet Web sayfaları ve için varsayılan **devre dışı** Internet Web sayfaları için varsayılan olarak. Bu ayar ayarlandığında **devre dışı**, yapmaya etkinleştirmek bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama program aracılığıyla (örneğin, gerçekleşen tarafından `document.location` özelliği) engellenir. Bu durumda, kullanıcıların yalnızca kullanıcı tarafından başlatılan bir indirme aracılığıyla uygulamaları gibi uygulamanın URL'sine ayarlayın bir köprüyü tıklatarak başlatabilirsiniz.  

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

## <a name="use-third-party-web-servers"></a>Üçüncü taraf Web sunucuları kullanın  
 Dağıtıyorsanız bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulaması dışında bir IIS Web sunucusundan, sorun yaşayabilirsiniz sunucu anahtarı için hatalı içerik türü döndürmesi durumunda [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimini ve uygulama bildirimi gibi dosyaları. Bu sorunu çözmek için Web sunucunuzun Yardım belgeleri sunucuya yeni içerik türlerini ekleyin ve tüm dosya adı uzantısı eşlemeler aşağıdaki tabloda listelenen emin hakkında mevcut olduğunu doğrulama bakın.  

|Dosya adı uzantısı|İçerik türü|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  

## <a name="clickonce-and-mapped-drives"></a>ClickOnce ve eşlenen sürücüler  
 ClickOnce uygulaması yayımlama için Visual Studio kullanıyorsanız, eşlenmiş sürücü yükleme konumu olarak belirtemezsiniz. Ancak, eşlenmiş sürücüden Düzenleyicisi (Mage.exe ve MageUI.exe) ve Bildirim Oluşturucusu kullanarak yüklemek için ClickOnce uygulaması değiştirebilirsiniz. Daha fazla bilgi için [Mage.exe (bildirim üretme ve düzenleme aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) ve [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP protokolünü uygulamaları yüklemek için desteklenmiyor  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] herhangi bir HTTP 1.1 Web sunucusu veya dosya sunucusu uygulamaları yüklemeyi destekler. FTP gibi Dosya Aktarım Protokolü, uygulamaları yüklemek için desteklenmiyor. Yalnızca uygulamaları yayımlamak için FTP kullanabilirsiniz. Aşağıdaki tabloda bu farklılıklar özetlenmiştir:  


| URL türü | Açıklama |
|----------| - |
| FTP: / / | Yayımlayabilmek için bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bu protokolü kullanarak uygulama. |
| http:// | Yükleyebileceğiniz bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bu protokolü kullanarak uygulama. |
| https:// | Yükleyebileceğiniz bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bu protokolü kullanarak uygulama. |
| File:// | Yükleyebileceğiniz bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bu protokolü kullanarak uygulama. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2'de: Windows Güvenlik Duvarı  
 Varsayılan olarak, Windows XP SP2, Windows Güvenlik Duvarı'nı etkinleştirir. Windows XP yüklü olduğu bir bilgisayarda uygulama geliştiriyorsanız, yayımlama ve çalıştırmak koruyabilmeyi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] IIS çalıştıran sunucunun yerel uygulamalar. Ancak, Windows Güvenlik Duvarı açık değilse, IIS çalıştıran başka bir bilgisayardan o sunucuya erişemez. Windows Güvenlik Duvarı'nı yönetme hakkında yönergeler için Windows yardımına bakın.  

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: FrontPage sunucu uzantılarını etkinleştir  
 Microsoft FrontPage Server Extensions HTTP kullanan bir Windows Web sunucusundaki uygulama yayımlama için gereklidir.  

 Varsayılan olarak, FrontPage Server Extensions yüklü Windows Server yok. Kullanmak istiyorsanız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] FrontPage Server Extensions ile HTTP kullanan bir Windows Server Web sunucusuna yayımlamak için FrontPage Server Extensions önce yüklemelisiniz. Windows Server'da sunucunuzu yönetin Yönetim Aracı'nı kullanarak yükleme gerçekleştirebilirsiniz.  

## <a name="windows-server-locked-down-content-types"></a>Windows Server: Kilitli içerik türleri  
 IIS üzerinde [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] kilitler bilinen belirli içerik türlerini hariç tüm dosya türleri (örneğin, *.htm*, *.html*, *.txt*, vb.). Dağıtımını etkinleştirmek için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bu sunucuyu kullanan uygulamalar, dosya türü yüklenmesine izin verecek IIS ayarlarını değiştirmeniz gerekir. *.application*, *.manifest*ve herhangi bir özel dosya türleri uygulamanız tarafından kullanılan.  

 Bir IIS sunucusu kullanarak dağıtırsanız, çalıştırma *inetmgr.exe* ve varsayılan Web sayfası için yeni bir dosya türü ekleyin:  

- İçin *.application* ve *.manifest* uzantıları, MIME türü "application/x-ms-application." olmalıdır Diğer dosya türleri için MIME türü "application/octet-stream." olmalıdır.  

- Bir MIME türü uzantı oluşturursanız "<em>" ve MIME türü "application/octet-stream" yüklenmek üzere engellenmemiş dosya türlerinin sağlayacaktır. (Ancak, engellenen dosya türleri gibi *.aspx</em> ve *.asmx* karşıdan yüklenemiyor.)  

  Microsoft Bilgi Bankası makalesine KB326965 özel yönergeler Windows Server'da MIME türleri yapılandırılıyor başvurmak için "IIS 6.0 bilinmeyen MIME türlerine adresindeki sunmuyor." [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  

## <a name="content-type-mappings"></a>İçerik türü eşlemeleri  
 HTTP üzerinden içerik türü (MIME türü olarak da bilinir) için yayımlarken *.application* dosyası olmalıdır. "application/x-ms-application." Varsa [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] sunucuda yüklüyse, bu sizin için otomatik olarak ayarlanır. Bu yüklü değil ve ardından bir MIME türü ilişkilendirmesini oluşturmak için ihtiyacınız varsa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama vroot (veya tüm sunucu).  

 Bir IIS sunucusu kullanarak dağıtırsanız, çalıştırma <em>inetmgr.</em> exe ve yeni bir içerik türü "application/x-ms-uygulama" add *.application* uzantısı.  

## <a name="http-compression-issues"></a>HTTP sıkıştırması sorunları  
 İle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], gerçekleştirebilirsiniz HTTP sıkıştırması kullanan indirmeler, akış istemciye göndermeden önce veri akışını sıkıştırmak için GZIP algoritma kullanan bir Web sunucusu teknolojisi. İstemci — bu durumda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]— dosyaları okumadan önce akışı açar.  

 IIS kullanıyorsanız, HTTP sıkıştırma kolayca etkinleştirebilirsiniz. HTTP sıkıştırmasını etkinleştirmek, ancak yalnızca belirli dosya türleri için etkin — yani, HTML ve metin dosyaları. Derlemeler için sıkıştırmayı etkinleştirmek için (*.dll*), XML (*.xml*), dağıtım bildirimleri (*.application*) ve uygulama bildirimleri (*.manifest*), bu dosya türleri için IIS'nin sıkıştırmasını türleri listesine eklemeniz gerekir. Yalnızca metin ve HTML dosyaları, dosya türlerini dağıtıma ekleme kadar sıkıştırılır.  

 IIS hakkında ayrıntılı yönergeler için bkz. [HTTP sıkıştırma için ek belge türlerini belirtmek nasıl](http://go.microsoft.com/fwlink/?LinkId=178459).  

## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce dağıtım stratejisini seçin](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Uygulama dağıtımının önkoşulları](../deployment/application-deployment-prerequisites.md)