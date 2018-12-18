---
title: ClickOnce Dağıtımları içinde belirli hataları giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: d0b7e53eba21372641bad683c442e796648a4765
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213648"
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>ClickOnce Dağıtımları İçinde Belirli Hataları Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, dağıtırken oluşabilecek aşağıdaki yaygın hataları listeler bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama ve her sorunu gidermek için adımları sağlar.  
  
## <a name="general-errors"></a>Genel hatalar  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Ne zaman bir .application dosya hiçbir şey olmaz, bulmaya veya XML Internet Explorer'da oluşturur veya bir çalışma veya Farklı Kaydet iletişim kutusu görüntülenir  
 Bu hata büyük olasılıkla istemci ve sunucu üzerinde doğru şekilde kaydedilmemiş içerik türü (MIME türleri olarak da bilinir) neden olur.  
  
 İlk olarak, sunucunun .application uzantısı içerik türü "application/x-ms-uygulama" ile ilişkilendirmek için yapılandırıldığından emin olun.  
  
 Sunucunun doğru şekilde yapılandırıldıysa, emin [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] bilgisayarınızda yüklü. Varsa [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] yüklü olduğu ve yeniden yüklemeyi deneyin. Bu sorunu hala görüyorsanız [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] içerik türü istemcide yeniden kaydetmek için.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Hatayı bildiren, "Uygulama alınamıyor. Dağıtımda eksik dosyaları"veya"uygulama indirme kesintiye, ağ hataları kontrol edin ve daha sonra yeniden deneyin"  
 Bu ileti, tarafından başvurulan bir veya daha fazla dosya gösterir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bildirimleri karşıdan yüklenemiyor. URL indirmek bu hata ayıklama için en kolay yolu denemektir, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] indiremiyorsa, diyor. Bazı olası nedenleri şunlardır:  
  
-   Günlük dosyası "(403) Yasak" diyorsa, veya "(404) bulunamadı" Web sunucusu, böylece bu dosyayı karşıdan yüklemeyi engellemez yapılandırıldığını doğrulayın. Daha fazla bilgi için [sunucu ve istemci yapılandırma sorunları ClickOnce Dağıtımları içinde](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
-   .Config dosyası sunucu tarafından engelleniyorsa bölümüne bakın. "indirme hatası yüklemeye çalıştığınızda bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .config dosyası olan bir uygulama" Bu konunun devamındaki.  
  
-   Bu nedeniyle oluşup oluşmadığını belirlemek `deploymentProvider` etkinleştirmesi için kullanılan URL'den farklı bir konuma işaret dağıtım bildiriminde URL.  
  
-   Tüm dosyaları sunucu üzerinde mevcut olduğundan emin olun; [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] günlük hangi dosya bulunamadı söyler.  
  
-   Ağ bağlantısı sorunları olup olmadığını; Yükleme sırasında istemci bilgisayar çevrimdışı olursa bu ileti alabilir.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>.Config dosyasına sahip bir ClickOnce uygulamasını yüklemeye çalıştığınızda indirme hatası  
 Varsayılan olarak, Visual Basic Windows tabanlı bir uygulama, bir App.config dosyası içerir. Bir kullanıcı, işletim sistemi yükleme .config dosyalarının güvenlik nedenleriyle engellediğinden kullanan Windows Server 2003, Web sunucusundan yüklemeye çalıştığında bir sorun olacaktır. Yüklenecek .config dosyasını etkinleştirmek için tıklayın **".deploy" dosya uzantısı** içinde **yayımlama seçeneği** iletişim kutusu.  
  
 Ayrıca içerik türü (MIME türleri olarak da bilinir) uygun şekilde .application, .manifest ve .deploy dosya için ayarlamanız gerekir. Daha fazla bilgi için Web-server belgelerinize bakın.  
  
 Daha fazla bilgi için "Windows Server 2003: yansıtır içerik türleri" konusuna bakın. [sunucu ve istemci yapılandırma sorunları ClickOnce Dağıtımları içinde](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Hata iletisi: "Uygulama yanlış biçimlendirilmiş;" "XML imzası geçersiz" günlük dosyası içerir.  
 Bildirim dosyası güncelleştirildi ve yeniden imzalanmış emin olun. Uygulamanızı kullanarak yeniden yayımlamanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veya uygulamayı yeniden imzalamak için Mage kullanın.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Sunucu uygulama güncelleştirildi, ancak istemci güncelleştirme karşıdan yüklemez  
 Bu sorun aşağıdaki görevlerden birini tamamlayarak:  
  
-   İnceleme `deploymentProvider` dağıtım bildiriminde URL. BITS ile aynı konumda güncelleştirmesini sağlamak, `deploymentProvider` işaret eder.  
  
-   Dağıtım bildirimi içinde güncelleştirme aralığı doğrulayın. Bu aralık için altı saatte bir kez gibi düzenli bir aralıkta ayarlanırsa [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bu aralığı geçinceye kadar güncelleştirme taramaz. Uygulama başladığında her zaman bir güncelleştirme için tarama bildirimi değiştirebilirsiniz. Güncelleştirmeler yükleniyor, ancak uygulama aktivasyonunu yavaşlatır doğrulamak için kullanışlı bir seçenektir geliştirme zamanı sırasında güncelleştirme aralığı değiştiriyor.  
  
-   Uygulama başlangıç menüsünde yeniden başlatmayı deneyin. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Güncelleştirme arka planda tespit ettik ancak sonraki etkinleştirme BITS yüklemek isteyip istemediğinizi sorar.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Güncelleştirme sırasında aşağıdaki günlük Giriş bir hata alırsınız: "başvuru dağıtımdaki uygulama bildiriminde tanımlanan kimlik eşleşmiyor."  
 El ile dağıtım ve uygulama bildirimleri düzenlediniz ve açıklamayı bir derlemenin kimliğinin bir bildirim ile eşitlenmemiş neden olduğundan, bu hata oluşabilir. Bir derlemenin kimliğini, adını, sürüm, kültür ve ortak anahtar belirteci oluşur. Bildirimlerinizi kimlik açıklamasında inceleyin ve farkları düzeltin.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>İlk kez yerel bir disk veya CD-ROM'u etkinleştirme başarılı, ancak Başlat menüsünden sonraki etkinleştirme başarılı  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama için güncelleştirmeleri almak için dağıtım sağlayıcı URL'sini kullanır. URL işaret ettiği konum doğru olduğundan emin olun.  
  
#### <a name="error-cannot-start-the-application"></a>Hata: "uygulama başlatılamıyor"  
 Bu hata iletisi, genellikle bu uygulamaya yüklenmesinde bir sorun olduğunu gösterir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] depolayın. Uygulamada hata var ya da deposu bozuk. Günlük dosyası hatanın oluştuğu söyleyebilir.  
  
 Şunları yapmanız:  
  
-   Dağıtım bildirimi kimliğini, uygulama bildiriminin kimlik ve kimlik EXE ana uygulamanın tüm benzersiz olduğundan emin olun.  
  
-   Dosya yolu 100 karakterden uzun olmadığını doğrulayın. Uygulamanız çok uzun dosya yollarını içeriyorsa, depolamanın en fazla yol sınırlamalar aşabilir. Yolları kısaltmayı deneyin ve yeniden yükleyin.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Uygulama yapılandırma dosyasında PrivatePath ayarları onaylanmaz  
 PrivatePath (Fusion algılama yolları) kullanmak için uygulama tam güven izni istemeniz gerekir. Uygulama bildiriminin tam güven isteme ve yeniden deneyin değiştirmeyi deneyin.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Kaldırma sırasında bir ileti "uygulamayı kaldırmak için başarısız oldu" görüntülenir  
 Bu ileti genellikle Uygulama zaten kaldırılmış olan veya deposu bozuk olduğunu gösterir. Tıkladıktan sonra **Tamam**, **Program Ekle/Kaldır** giriş kaldırılacak.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Yükleme sırasında platform bağımlılıkları yüklü olmadığını bildiren bir ileti görüntülenir  
 Uygulamayı çalıştırmak için gereken GAC (Genel Derleme Önbelleği) içindeki önkoşul eksik.  
  
## <a name="publishing-with-visual-studio"></a>Visual Studio ile yayımlama  
  
#### <a name="publishing-in-visual-studio-fails"></a>Visual Studio'da yayımlama başarısız  
 Sunucuya yayımlayın hakkı, hedeflediğiniz emin olun. Bir terminal sunucusu bilgisayara bir yönetici olarak değil, normal bir kullanıcı olarak oturum açarsanız, örneğin, büyük olasılıkla yerel Web sunucusuna yayımlamak için gereken hakları yoktur.  
  
 Bir URL ile yayımlıyorsanız, hedef bilgisayarın FrontPage Server Extensions'ın etkin olduğundan emin olun.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Hata iletisi: Web sitesi oluşturulamadı. '\<site >'. FrontPage Server Extensions'ı ile iletişim kurmak için bileşenler yüklü değil.  
 Microsoft Visual Studio Web geliştirme yayımlamakta olduğunuz makinede bileşeninin yüklü olduğundan emin olun. Hızlı kullanıcılar için varsayılan olarak bu bileşen yüklü değil. Daha fazla bilgi için bkz. [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Hata iletisi: dosya bulunamadı. ' Microsoft.Windows.Common-denetimleri, sürüm= 6.0.0.0, kültür =\*, PublicKeyToken 6595b64144ccf1df, ProcessorArchitecture =\*, türü= win32'  
 Görsel stiller etkinken WPF uygulaması yayımlama açmaya çalıştığında bu hata iletisi görünür. Bu sorunu çözmek için bkz: [nasıl yapılır: görsel stiller etkin bir WPF uygulaması yayımlama](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Görüntü kullanma  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Sertifika deponuza ve alınan boş ileti kutusu içinde bir sertifika ile oturum açmaya  
 İçinde **imzalama** iletişim kutusunda, şunları yapmalısınız:  
  
-   Seçin **depolanan bir sertifika ile oturum**, ve  
  
-   Listeden bir sertifika seçin; ilk sertifikayı varsayılan seçim değil.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>"Oturum yok" düğmesine tıklayarak bir özel durum neden olur  
 Bu sorunun bilinen bir hatadır. Tüm [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bildirimlerinin imzalanmasını gerekli. İmzalama seçeneklerden birini seçin ve ardından **Tamam**.  
  
## <a name="additional-errors"></a>Ek hataları  
 Aşağıdaki tablo kullanıcı yüklediğinde, bir istemci bilgisayar kullanıcısının alabilirsiniz bazı yaygın hata iletilerini gösterir bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama. Her hata iletisi, hatanın en olası neden açıklamasını yanındaki listelenir.  
  
|hata iletisi|Açıklama|  
|-------------------|-----------------|  
|Uygulama başlatılamıyor. Uygulama yayımcısına başvurun.<br /><br /> Uygulama başlatılamıyor. Yardım için uygulama satıcısına başvurun.|Uygulama başlatılamıyor ve belirli herhangi bir nedenle bulunabilir ortaya genel hata iletileri şunlardır. Sık sık uygulama bir şekilde bozulmuş anlamına gelir veya [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] deposu bozuk.|  
|Devam edemiyor. Uygulama, yanlış biçimlendirilmiş. Yardım için uygulama yayımcısına başvurun.<br /><br /> Uygulama doğrulaması başarılı olmadı. Devam edilemiyor.<br /><br /> Uygulama dosyaları alınamadı. Dağıtımda bozuk dosyalar.|Dağıtım bildirim dosyalarında biri sözdizimsel olarak geçerli değil veya karşılık gelen dosya ile mutabık kılınamayan bir karma değer içerir. Bu hata ayrıca bir derleme içine gömülü bildirimi bozuk olduğunu gösterebilir. Dağıtımınızı yeniden oluşturun ve uygulamanızı yeniden derleyin veya bulun ve hataları bildirimlerinizi içinde el ile düzeltin.|  
|Uygulama alınamıyor. Kimlik doğrulama hatası.<br /><br /> Uygulama yüklemesi başarısız oldu. Uygulama dosyalarını sunucusunda bulunamıyor. Uygulama Yayımcısı veya yöneticinizle iletişime geçin.|Onlara erişim izniniz olmadığı için dağıtımdaki bir veya daha fazla dosyaları karşıdan yüklenemiyor. Bu, dağıtımınızdaki dosyalardan biri Web sunucusu korumalı bir dosyayı kabul yapan bir uzantı ile bitiyorsa, oluşabilecek bir Web sunucusu tarafından döndürülen bir 403 Yasak hata tarafından kaynaklanabilir. Ayrıca, bir veya daha fazla uygulamanın dosya içeren bir dizine erişmek için bir kullanıcı adı ve parola gerektirebilir.|  
|Uygulamayı karşıdan yükleyemiyor. Uygulama, gerekli dosyaları eksik. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun.|Bir veya daha fazla uygulama bildiriminde listelenen dosya sunucusunda bulunamıyor. Dağıtımın tüm bağımlı dosyaları karşıya yüklediğiniz olduğunu doğrulayıp yeniden deneyin.|  
|Uygulama yükleme başarılı olmadı. Ağ bağlantınızı denetleyin veya sistem yöneticinize veya ağ hizmeti sağlayıcısına başvurun.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Sunucunun ağ bağlantısı kurulamıyor. Sunucunun kullanılabilirlik ve ağ durumunu inceleyin.|  
|URLDownloadToCacheFile başarısız oldu; HRESULT '\<sayı >'. İndirilmeye çalışılırken bir hata oluştu '\<Dosya >'.|Bir kullanıcı Internet Explorer Gelişmiş Güvenlik seçeneğini "Arasında güvenli değişiyorsa uyar ve güvenli mod değil" dağıtım hedef bilgisayarda ayarlanmış ve yüklenen ClickOnce uygulamasının kurulum URL güvenli olmayan güvenli bir siteye yönlendirilir (veya Internet Explorer uyarısı keser çünkü tam tersi), yükleme başarısız olur.<br /><br /> Bu sorunu çözmek için şunlardan birini yapabilirsiniz:<br /><br /> -Güvenlik seçeneğini kaldırın.<br />-Olun emin Kurulum URL'si güvenlik modları değiştirecek şekilde yeniden yönlendirilmediği.<br />-Yeniden yönlendirme tamamen kaldırın ve gerçek kurulum URL'sini seçin.|  
|Sabit diske yazılırken bir hata oluştu. Olabilir yeterli alan kullanılabilir disk üzerinde. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun.|Bu uygulamayı depolamak için yeterli disk alanı gösterebilir, ancak uygulama dosyaları diske kaydetmeye çalışırken de daha genel bir g/ç hatası gösteriyor olabilir.|  
|Uygulama başlatılamıyor. Diskte yeterli alan yok.|Sabit disk dolu. Boş alan açın ve uygulamayı yeniden çalıştırmayı deneyin.|  
|Çok fazla dağıtılan etkinleştirmeleri tek seferde yüklemeye çalışıyorsunuz.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aynı anda çalışabilecek farklı uygulama sayısını sınırlar. Bu yerel karşı hizmet reddi saldırılarını için kötü amaçlı saldırılara karşı korumaya yardımcı olmak için büyük ölçüde olduğu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] hizmeti; kullanıcılardan yalnızca tek bir örneği ile son bulur, aynı uygulama sayfayı hızlı bir şekilde tekrar tekrar başlatmayı deneyin uygulama.|  
|Ağ üzerinden kısayolları etkinleştirilemiyor.|Kısayollar bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama yerel sabit diskinde yalnızca başlatılabilir. Uzak bir sunucuda bir kısayol dosyasına işaret eden bir URL açarak başlatılamıyor.|  
|Uygulama, kısmi güven çevrimiçi çalıştırmak için çok büyük. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun.|Kısmi güvende çalışan bir uygulama yarısı 250 MB'tır, varsayılan olarak çevrimiçi uygulama kota boyutu büyük olamaz.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce Dağıtım Sorunlarını Giderme](../deployment/troubleshooting-clickonce-deployments.md)



