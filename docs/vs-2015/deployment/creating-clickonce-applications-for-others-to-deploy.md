---
title: Dağıtmak için ClickOnce uygulamaları başkalarının oluşturma | Microsoft Docs
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
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: f2b7bb6c990567a483ab28d215019fe1b259d166
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862092"
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>Başkalarının Dağıtması için ClickOnce Uygulamaları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamaları dağıtmak ClickOnce dağıtımı oluşturan tüm geliştiricilerin planlayın. Çoğu yalnızca ClickOnce kullanarak uygulama paketini ve ardından dosyaları kapatma gibi büyük bir kuruluşa bir müşteriye el. Müşteri, bir alt ağı üzerinde uygulamayı barındırmak için sorumlu olur. Bu konu, .NET Framework sürüm 3.5 önceki sürümlerinde bu tür dağıtımlarda devralınan sorunlardan bazılarını açıklar. Ardından, .NET Framework 3. 5'yeni "bildirimi için güven kullan" özelliğini kullanarak sağlanan yeni bir çözüm açıklanmaktadır. Son olarak, ClickOnce dağıtımları için yine de .NET Framework'ün eski sürümlerini kullanan müşteriler oluşturmak için önerilen stratejiler ile sonlanır.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Müşteriler için dağıtımları oluşturma konuları  
 Bir müşteri için bir dağıtım sağlamak planlama yaparken, çeşitli sorunlar oluşur. İlk sorun, kod imzalama ile ilgilidir. Bir ağ üzerinden dağıtılması için dağıtım bildirimini ve uygulama bildirimi bir ClickOnce dağıtımının hem de bir dijital sertifika ile oturum açmanız gerekir. Bu sorunun bildirimleri yeniden imzalarken Geliştirici sertifikası veya müşterinin kullanılıp kullanılmayacağını başlatır.  
  
 ClickOnce uygulamasının kimlik, dağıtım bildiriminin dijital imza tabanlı olarak hangi sertifikanın kullanılacağını soru kritik. Geliştirici bir dağıtım bildirimini imzalar, müşteri büyük bir şirkettir ve şirketin birden fazla bölme uygulama özelleştirilmiş bir sürümünü dağıtır çakışmalarına neden.  
  
 Örneğin, Adventure Works Finans departmanı ve İnsan Kaynakları departmanı olduğunu varsayalım. Her iki departman bir ClickOnce uygulamasını bir SQL veritabanında depolanan verilerden raporlar oluşturan bir Microsoft Corporation lisanslayın. Microsoft, her departman için verileri özelleştirilmiş uygulama sürümü ile sağlar. ClickOnce ikinci uygulama birinciyle aynı olarak dikkate gibi her iki uygulamayı kullanmaya çalıştığında bir kullanıcı, uygulamaları aynı Authenticode sertifikası ile imzalanmış bir hata karşılaşacaktır. Bu durumda, müşteri beklenmedik ve istenmeyen yan uygulama tarafından yerel olarak depolanan herhangi bir veri kaybı içeren etkilerle karşılaşabilir.  
  
 Kod imzalama için ek bir sorunla ilgili `deploymentProvider` ClickOnce uygulama güncelleştirmelerini bulacağınız dağıtım bildirimi içinde öğesi. Bu öğe imzalamadan önce dağıtım bildirimi eklenmesi gerekir. Bu öğe daha sonra eklediyseniz, dağıtım bildirimini yeniden imzalanması gerekir.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>Dağıtım bildirimi imzalamak müşteri gerektirme  
 Bu sorunun benzersiz olmayan dağıtımlar için tek bir çözüm uygulama bildirimini Geliştirici oturum sahip olmaktır ve müşteri dağıtım bildirimini imzalayın. Bu yaklaşım çalışırken diğer sorunları ortaya çıkarır. Authenticode sertifikası bir Korunan varlık kalmalıdır olduğundan, müşterinin dağıtım imzalamak için geliştirici yalnızca sertifika veremez. Müşteri dağıtım bildirimini kendilerini ücretsiz araçlar .NET Framework SDK ile birlikte kullanarak oturum açabilir, ancak bu müşteri işleyemeyeceği ya da sağlamak mümkün olandan daha fazla teknik bilgi gerektirebilir. Bu gibi durumlarda, geliştirici genellikle bir uygulama, Web sitesi veya müşteri imzalamak için uygulamanın kendi sürüm gönderebilmek için başka bir mekanizma oluşturur.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>ClickOnce uygulama güvenliği imzalama müşteri etkisi  
 Geliştirici ve müşteri müşteri uygulama bildirimini imzalayın kabul etmiş olsanız bile, bu uygulamanın kimlik çevreleyen diğer sorunlar, özellikle de güvenilir uygulama dağıtımına geçerli olarak başlatır. (Bu özellik hakkında daha fazla bilgi için bkz. [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).) İstemci bilgisayarlarını kendilerine Microsoft Corporation tarafından sağlanan herhangi bir uygulama tam güven ile çalışması şekilde yapılandırmak Adventure Works istediğini varsayalım. Adventure Works bir dağıtım bildirimini imzalar, ClickOnce Uygulama güven düzeyini belirlemek için Adventure iş güvenlik imzasını kullanır.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>Müşteri dağıtımları için güven uygulama bildirimi kullanarak oluşturma  
 .NET Framework 3. 5'te, geliştiricilere ve müşterilere bildirimleri nasıl imzalanıp imzalanmayacağını, senaryosu için yeni bir çözüm sağlayan yeni bir özellik içerir. ClickOnce Uygulama bildirimi adlı yeni bir öğe destekler `<useManifestForTrust>` uygulama bildiriminin dijital imza ne güven kararları için kullanılması gereken olduğunu belirtmek bir geliştirici sağlar. Geliştirici ClickOnce paketleme araçlarını kullanan — Mage.exe MageUI.exe ve Visual Studio gibi — bu öğe uygulama bildiriminde dahil olarak bildirimde hem kendi Yayımcı adı hem de uygulamanın adını eklemek için.  
  
 Kullanırken `<useManifestForTrust>`, dağıtım bildirimini bir sertifika yetkilisi tarafından verilen Authenticode sertifikası ile imzalanması gerekmez. Bunun yerine, otomatik olarak imzalanan bir sertifika bilinen ile imzalanabilir. Kendinden imzalı bir sertifika, standart .NET Framework SDK araçlarını kullanarak, müşteri veya geliştirici tarafından oluşturulan ve ardından standart ClickOnce dağıtım araçlarını kullanarak dağıtım bildirimine uygulanır. Daha fazla bilgi için [Makecert.exe (sertifika oluşturma aracı)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
 Dağıtım bildirimi için otomatik olarak imzalanan bir sertifika kullanarak çeşitli avantajlar sunar. İhtiyacını ortadan alın veya kendi Authenticode sertifikası oluşturmak üzere müşteri tarafından `<useManifestForTrust>` geliştiricinin aplikaci marka kendi kimlik korumasına izin verirken, müşteri dağıtımı kolaylaştırır. Sonuç daha güvenlidir ve benzersiz uygulama kimlikleri olan imzalı dağıtımları kümesidir. Bu, aynı uygulamanın birden çok müşteriyi dağıtması oluşabilecek olası çakışmaları ortadan kaldırır.  
  
 ClickOnce dağıtımı ile oluşturma hakkında bilgi için `<useManifestForTrust>` etkin bkz [izlenecek yol: ClickOnce uygulaması söz konusu mu değil gerektiren Re-Signing'el ile dağıtma ve bu korur markalama bilgileri](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Çalışma zamanında çalışır güven için nasıl uygulama bildirimi  
 Uygulama bildiriminin güven kullanarak çalışma zamanında nasıl çalıştığını daha iyi anlamak için aşağıdaki örneği göz önünde bulundurun. .NET Framework 3. 5'i hedefleyen ClickOnce uygulaması, Microsoft tarafından oluşturulur. Uygulama bildirimi kullanan `<useManifestForTrust>` öğesi ve Microsoft tarafından imzalanır. Adventure Works, otomatik olarak imzalanan bir sertifika kullanarak bir dağıtım bildirimini imzalar. Adventure Works istemciler Microsoft tarafından imzalanmış herhangi bir uygulamaya güvenecek şekilde yapılandırılır.  
  
 Kullanıcı dağıtım bildirimine bir bağlantıyı tıklattığında, ClickOnce, uygulama kullanıcının bilgisayara yükler. Sertifika ve dağıtım bilgileri istemci bilgisayarda ClickOnce uygulamaya benzersiz olarak tanımlayın. Kullanıcı, aynı uygulamanın farklı bir konumdan yeniden yüklemeye çalışırsa, ClickOnce, uygulama zaten istemcide mevcut olduğunu belirlemek için bu kimlik kullanabilirsiniz.  
  
 Ardından, ClickOnce vereceği güven düzeyini belirler uygulama bildirimini imzalamak için kullanılan Authenticode sertifikası inceler. Adventure Works istemcileri Microsoft tarafından imzalanmış herhangi bir uygulamanın güvenmek üzere yapılandırıldığı bu ClickOnce Uygulama tam güven izni verilir. Daha fazla bilgi için [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>Önceki sürümler için müşteri dağıtımları oluşturma  
 Bir geliştirici ClickOnce uygulamaları için .NET Framework'ün eski sürümlerini kullanan müşteriler dağıtıyor ne olur? Aşağıdaki bölümlerde, avantajları ve dezavantajları birlikte birkaç önerilen çözümler özetler.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>Müşteri adına oturum dağıtımları  
 Olası bir Dağıtım stratejisi, müşterinin kendi özel anahtarı kullanarak dağıtımları, müşterileri adına oturum açmak için bir mekanizma oluşturmak Geliştirici içindir. Bu, geliştirici özel anahtarlar ya da birden çok dağıtım paketleri yönetme zorunluluğunu ortadan kaldırır. Geliştirici, her müşteri için yalnızca aynı dağıtım sağlar. Bu, müşterinin imzalama hizmetini kullanarak kendi ortamlarından özelleştirmek için en fazla olur.  
  
 Bu yöntem bir dezavantajı, uygulamak için gereken zaman ve ' dir. Böyle bir hizmet, .NET Framework SDK'SINDA sağlanan araçları kullanarak oluşturulabilir olsa da ürün yaşam döngüsü için daha fazla geliştirme süresini ekleyeceksiniz.  
  
 Bu konunun önceki kısımlarında belirtildiği gibi başka bir dezavantajı, uygulamanın her müşteri'nin sürümü çakışmalarına neden ve aynı uygulama kimliği sahip olmasıdır. Geliştirici, bir sorun varsa, her uygulamanın benzersiz bir ad vermek için dağıtım bildirimi oluşturulurken kullanılan ad alanı değiştirebilirsiniz. Bu uygulamanın her sürümü için ayrı bir kimlik oluşturmak ve tüm olası kimlik çakışmaları ortadan kaldırabilirsiniz. Bu alan için karşılık gelen `-Name` Mage.exe ve için bağımsız değişken **adı** alanını **adı** MageUI.exe sekmesindedir.  
  
 Örneğin, geliştirici Application1 adlı bir uygulama oluşturduğunu varsayalım. Ad alanı Application1 olarak ayarlanmış olan tek bir dağıtım oluşturmak yerine, geliştirici Application1 CustomerA, Application1 CustomerB gibi bu ad, müşteriye özgü varyasyonunu ile birkaç dağıtımı oluşturabilir ve benzeri.  
  
### <a name="deploy-using-a-setup-package"></a>Kurulum paketini kullanarak dağıtma  
 İkinci bir olası Dağıtım stratejisi, ClickOnce uygulamasının ilk dağıtımı yapmak için bir Microsoft Setup projesi oluşturmaktır. Bu farklı olarak bulunan biçimlerden birinde sağlanabilir: yürütülebilir bir kurulum olarak bir MSI dağıtım olarak (. EXE) veya toplu komut dosyası ile birlikte bir dolap (.cab) dosyası olarak.  
  
 Bu tekniği kullanarak, geliştirici müşteri uygulama dosyaları, uygulama bildirimini ve şablon olarak hizmet veren bir dağıtım bildirimi içeren bir dağıtımı sağlar. Müşteri, bir dağıtım URL'si (sunucu veya dosya paylaşımı konumu kullanıcılar ClickOnce uygulamasını yükleyecek), bir dijital sertifika yanı sıra bunları belirtmeyi tercih Kurulum programı çalıştırılır. Kurulum uygulama güncelleştirme denetleme aralığı gibi ek ClickOnce yapılandırma seçenekleri için istemek de tercih edebilirsiniz. Bu bilgi toplandıktan sonra Kurulum programı, gerçek dağıtım bildirimi oluşturun, imzalayın ve atanan sunucu konumuna ClickOnce uygulaması yayımlama.  
  
 Müşteri bu durumda dağıtım bildirimi imzalamak için üç yol vardır:  
  
1. Müşteri, bir sertifika yetkilisi (CA) tarafından verilen geçerli bir sertifika kullanabilirsiniz.  
  
2. Bu yaklaşım, alternatif olarak, dağıtım bildirimini otomatik olarak imzalanan bir sertifika ile imzalamak müşteri seçebilirsiniz. Bu bir dezavantajı, kullanıcı bu yüklemeyi yeniden sorulduğunda "Bilinmeyen Yayımcı" sözcüklerini görüntülenecek uygulama neden olmasıdır. Ancak, gerekli bir sertifika yetkilisi tarafından verilmiş bir sertifika için para ve zaman harcamak zorunda kalmaktan daha küçük müşteriler engellediğini avantajdır.  
  
3. Son olarak, geliştirici kendi kendinden imzalı bir sertifika Kurulum paketine dahil edebilirsiniz. Bu, bu konunun önceki kısımlarında açıklanan uygulama kimliği ile ilgili olası sorunları ortaya çıkarır.  
  
   Kurulumu dağıtım projesi yöntemi dezavantajı, özel bir dağıtım uygulaması oluşturmak için gereken zaman ve ' dir.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Müşteri oluşturma sahip dağıtım bildirimi  
 Üçüncü bir olası dağıtım stratejisini el yalnızca uygulama dosyaları ve uygulama bildirimi müşteriye kapalıdır. Bu senaryoda, oluşturmak ve dağıtım bildirimi imzalamak için .NET Framework SDK'sını kullanarak müşteri sorumludur.  
  
 Bu yöntemin dezavantajı müşteri .NET Framework SDK Araçları'nı yükleme ve bir geliştirici veya bunları kullanmayı nitelikli olan sistem yöneticisi olmasını gerektirmesidir. Bazı müşteriler yapmalarına teknik çok az kayıpla veya hiç çaba gerektirir bir çözüme ihtiyaç duyulabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Test etmek için ClickOnce uygulamaları dağıtma ve üretim sunucularına teslim etmeden](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [İzlenecek yol: Bir ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [İzlenecek yol: Yeniden İmzalama Gerektirmeyen ve Marka Bilgisini Koruyan bir ClickOnce Uygulamasını El ile Dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)



