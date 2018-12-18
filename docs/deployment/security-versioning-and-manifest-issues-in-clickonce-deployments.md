---
title: Güvenlik, sürüm ve bildirim sorunları ClickOnce Dağıtımları içinde | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7ae835b53960ca6952b71c10a2348f707785e16
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081751"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Güvenlik, sürüm ve bildirim sorunları ClickOnce Dağıtımları

İle ilgili sorunları birçok [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] güvenlik, uygulama sürümü ve bildirim sözdizimi ve semantiği neden olabilecek bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtımının.

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce ve Windows Vista kullanıcı hesabı denetimi

İçinde [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], uygulamalar varsayılan olarak, geçerli kullanıcının yönetici izinlerine sahip bir hesapla oturum açarsa bile standart bir kullanıcı olarak çalıştırın. Bir uygulama yönetici izinleri gerektiren bir eylem gerçekleştirmeniz gerekirse, ardından yönetici kimlik bilgilerini girmesini ister. işletim sistemi söyler. Kullanıcı Hesabı Denetimi (UAC) olarak adlandırılır, bu özellik, uygulamalar, bir kullanıcının açık onayını olmadan işletim sisteminin tamamını etkileyebilecek değişiklikler yapmasını engeller. Windows uygulamaları bildirmek belirterek bu izni ayrıcalık gerektiren `requestedExecutionLevel` özniteliğini `trustInfo` kendi uygulama bildiriminin.

Güvenlik yükseltme saldırıları, uygulamaları gösterme riskini nedeniyle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] UAC istemci için etkinse, uygulamaları izin yükseltme isteği olamaz. Tüm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ayarlama girişiminde uygulama kendi `requestedExecutionLevel` özniteliğini `requireAdministrator` veya `highestAvailable` üzerinde yüklenmez [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].

Bazı durumlarda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama nedeniyle yükleyici algılama mantığı üzerinde yönetici izinleriyle çalıştırmak çalışabilir [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. Bu durumda, ayarlayabileceğiniz `requestedExecutionLevel` uygulama bildirimine özniteliğinde `asInvoker`. Bu yükseltme olmadan çalıştırmak uygulamanın kendisinin neden olur. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] otomatik olarak bu öznitelik için tüm uygulama bildirimleri ekler.

Tüm uygulama ömrü boyunca yönetici izinleri gerektiren bir uygulama geliştiriyorsanız Windows Installer (MSI) teknolojisini kullanarak uygulamayı dağıtma düşünmelisiniz. Daha fazla bilgi için [Windows Installer Temelleri](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Çevrimiçi uygulama kotaları ve kısmi güven uygulamaları

Varsa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama yerine çevrimiçi bir yükleme çalıştırır, çevrimiçi uygulamalar için ayrılan kota içine sığması gerekir. Ayrıca, kısmi güvende olduğu gibi kısıtlı güvenlik izinleri kümesi ile çalışan bir ağ uygulaması yarısı kota boyutu büyük olamaz.

Daha fazla bilgi için ve çevrimiçi uygulama kotasını değiştirme için bkz. [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Sürüm oluşturma sorunları

Bir derlemeye güçlü adlar atamak ve bir uygulama güncelleştirmesi yansıtmak için derleme sürüm numarasını Artır sorunlarla karşılaşabilirsiniz. Tanımlayıcı adlı bir derlemeye başvuru ile derlenmiş herhangi bir derleme kendisini derlenmesi gerekir veya derleme başvurusu eski sürümü çalışacaktır. Derleme için eski bir sürüm değeri kendi bağlanma isteği kullandığından bu derlemeyi çalışacaktır.

Örneğin, kendi projesi 1.0.0.0 sürümüne sahip bir tanımlayıcı adlı bütünleştirilmiş kod olduğunu varsayalım. Derlemeyi derledikten sonra ana uygulamanızı içeren projeye başvuru olarak ekleyin. Derlemeyi güncelleştirmek, 1.0.0.1 sürümüne artırmak ve ayrıca uygulama yeniden derlemeye gerek kalmadan dağıtmayı deneyin, uygulamanın çalışma zamanında derleme yüklemek mümkün olmayacaktır.

Yalnızca düzenlemekte olduğunuz bu hata oluşabilir, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] el ile; bildirimleri Visual Studio kullanarak dağıtımınızı oluşturursanız, bu hata yaşamaması gerekiyor.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>.NET Framework derlemeleri ayrı ayrı bildiriminde belirtin

Uygulamanızı el ile düzenlediyseniz yüklenemeyecek bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] daha eski bir sürümünü başvurmak deployment bir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] derleme. Örneğin, bir sürümü için System.Net derlemesine bir başvuru eklediyseniz [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] bildiriminde belirtilen sürümden önce ardından bir hata oluşacak. Genel olarak, size tek başvuruları belirtmek çalışmamalısınız [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] derlemeler, sürümü olarak [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] uygulama bildiriminde bağımlılık olarak, uygulamanızın çalıştığı karşı belirtilir.

## <a name="manifest-parsing-issues"></a>Bildirim Ayrıştırma sorunları

Tarafından kullanılan bildirim dosyaları [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] XML dosyalarıdır ve hem iyi biçimlendirilmiş hem de geçerli olmalıdır: XML sözdizimi kurallarına uyan ve yalnızca öğeler ve öznitelikler ilgili XML Şeması'nda tanımlanan kullanın.

Bildirim dosyasında sorunlara neden olabilecek bir şey, tek veya çift tırnak işareti gibi bir özel karakter içeren uygulamanız için bir ad seçmektir. Uygulamanın adı bir parçasıdır, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kimlik. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] şu anda özel karakterler içeren kimlikleri ayrıştırmaz. Uygulamanızı etkinleştirmek başarısız olursa, adı yalnızca alfabetik ve sayısal karakter kullanıyor ve tekrar dağıtmayı denemeden emin olun.

El ile dağıtım veya uygulama bildirimlerinizi düzenlediyseniz, yanlışlıkla bunları bozulmuş olabilir. Bozulmuş bir bildirim doğru engeller [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yükleme. Tıklayarak, çalışma zamanında bu tür hataları ayıklayabilirsiniz **ayrıntıları** üzerinde **ClickOnce hata** iletişim kutusu ve günlüğünde hata iletisi okunuyor. Günlük şu iletilerden biri listelenir:

- Bir açıklama söz dizimi hatası, satır numarası ve karakter hatanın oluştuğu konum.

- Bir öğe veya öznitelik bildiriminin şemasını ihlal kullanılan adı. XML el ile bildirimlerinize eklediyseniz, eklemelerinizi bildirim şemalarını karşılaştırma gerekecektir. Daha fazla bilgi için [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md) ve [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md).

- ID çakışması. Dağıtım ve uygulama bildirimleri bağımlılık başvuruları ikisinde benzersiz olmalıdır, `name` ve `publicKeyToken` öznitelikleri. Her iki öznitelik, bir bildirim içinde herhangi iki öğe arasındaki eşleşirse, Bildirim Ayrıştırma başarılı olmaz.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Bildirimler ve uygulamaları el ile değiştirildiğinde önlemler

Bir uygulama bildirimi güncelleştirdiğinizde, hem uygulama bildirimi hem de dağıtım bildirimini yeniden imzalamanız gerekir. Dağıtım bildirimi o dosyanın karması ve dijital imzası içerir bir uygulama bildirimi bir başvuru içeriyor.

### <a name="precautions-with-deployment-provider-usage"></a>İle dağıtım sağlayıcı kullanım uyarıları

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Dağıtım bildirimi sahip bir `deploymentProvider` uygulamanın yüklü ve hizmet gelen konumun tam yolunu işaret eden özelliği:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Bu yol ayarlanır [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulaması oluşturur ve yüklü uygulamalar için zorunlu. Yolun standart konumuna işaret burada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yükleyici güncelleştirmeleri için arama ve uygulamayı yükler. Kullanırsanız **xcopy** kopyalamak için komut bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama farklı bir konuma ancak değiştiremez `deploymentProvider` özelliği [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yüklemeye çalıştığında hala geri özgün konuma başvuru yapar uygulama.

Uygulamanın taşınacak veya kopyalanacak isterseniz de güncelleştirmelisiniz `deploymentProvider` yolu, böylece istemci yeni konumundan gerçekten yükler. Bir uygulama yüklediyseniz bu yolu güncelleştiriliyor çoğunlukla bir konudur. Her zaman ayarı asıl URL aracılığıyla başlatılan çevrimiçi uygulamalar için `deploymentProvider` isteğe bağlıdır. Varsa `deploymentProvider` kabul edilir; Aksi takdirde, uygulamayı başlatmak için kullanılan URL temel URL olarak uygulama dosyalarını indirmek için kullanılacak ayarlanmış.

> [!NOTE]
> Bildirim her güncelleştirdiğinizde de yeniden imzalamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

[ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)  
[Securw ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md)  
[ClickOnce dağıtım stratejisini seçin](../deployment/choosing-a-clickonce-deployment-strategy.md)