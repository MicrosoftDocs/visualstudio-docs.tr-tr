---
title: ClickOnce ve uygulama ayarlarını | Microsoft Docs
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
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 29f51960ad953318c8d9de749f28f684128e52ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177004"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce ve Uygulama Ayarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Forms için uygulama ayarları oluşturmak, depolamak ve özel uygulama ve kullanıcı tercihlerini istemcide bakımını yapmayı kolaylaştırır. Uygulama ayarları dosyaları bir ClickOnce uygulamasında nasıl çalışır ve kullanıcı sonraki bir sürüme yükseltildiğinde ClickOnce ayarları nasıl geçirdiğini aşağıdaki belge açıklar.  
  
 Aşağıdaki bilgiler yalnızca varsayılan uygulama ayarları sağlayıcısına geçerlidir <xref:System.Configuration.LocalFileSettingsProvider> sınıfı. Özel bir sağlayıcı sağlarsanız, bu sağlayıcı, verileri nasıl depoladı ve ayarlarına sürümleri arasında yükseltme nasıl belirler. Uygulama ayarları sağlayıcıları hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](http://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="application-settings-files"></a>Uygulama ayarları dosyası  
 Uygulama ayarları, iki dosya kullanır: *uygulama*. exe.config ve user.config burada *uygulama* Windows Forms uygulamanızın adıdır. User.config uygulamanızın kullanıcı kapsamlı ayarları depolayan istemciye ilk kez üzerinde oluşturulur. *Uygulama*. exe.config, aksine, var dağıtımdan önce ayarlar için varsayılan değerleri tanımlar. Visual Studio içerecektir bu dosya otomatik olarak kullandığınızda, **Yayımla** komutu. ClickOnce uygulamanızın emin olmanız gerekir, Mage.exe veya MageUI.exe kullanarak oluşturursanız, bu dosya ile birlikte gelir, uygulama bildiriminizi uygulamanızın diğer dosyaları kullanıcının.  
  
 ClickOnce, uygulama kullanıcının kullanmadan dağıtılan bir Windows Forms uygulamalarındaki *uygulama*. exe.config dosyası, uygulama dizininde depolanır, kullanıcının user.config file dosyanızı depolanma **belgeler ve ayarlar**  klasör. Bir ClickOnce uygulamasında *uygulama*. exe.config yaşadığı ClickOnce uygulama önbelleği içinde uygulama dizinindeki ve o uygulama için ClickOnce veri dizini user.config grafiğidir.  
  
 Uygulamanızı nasıl dağıtmak bağımsız olarak, uygulama ayarları sağlar güvenli okuma erişimi *uygulama*. exe.config ve user.config güvenli okuma/yazma erişimi.  
  
 Bir ClickOnce uygulamasında uygulama ayarları tarafından kullanılan yapılandırma dosyalarını boyutunu ClickOnce önbellek boyutuyla sınırlıdır. Daha fazla bilgi için [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Sürüm yükseltme  
 Yalnızca ClickOnce uygulaması'nün her sürümü tüm diğer sürümlerden yalıtılmış olduğundan, ClickOnce uygulaması için uygulama ayarları için diğer sürümlerinde de ayarlardan yalıtılır. Kullanıcınızın, uygulamanızın sonraki bir sürüme yükseltildiğinde, uygulama ayarları en son (en yüksek numaralı) sürümün ayarları ayarlar nesnesine yeni bir ayar dosyaları birleştirme ve güncelleştirilmiş sürümü ile sağlanan ayarların karşı karşılaştırır.  
  
 Aşağıdaki tabloda, uygulama ayarları kopyalamak için hangi ayarların nasıl karar verir açıklanmaktadır.  
  
|Değişiklik türü|Yükseltme eylemi|  
|--------------------|--------------------|  
|Eklenen ayarı *uygulama*. exe.config|Yeni ayar geçerli sürüme ait birleştirilir *uygulama*. exe.config|  
|Kaldırıldığında ayarı *uygulama*. exe.config|Eski ayarı güncel sürümün kaldırılır *uygulama*. exe.config|  
|Ayarın varsayılan; değiştirildi yerel ayar orijinal varsayılan olarak user.config hala ayarlanmış.|Ayar içine güncel sürümün user.config yeni varsayılan değer olarak birleştirilir.|  
|Ayarın varsayılan; değiştirildi ayar, varsayılan olmayan user.config olarak ayarlandı.|Ayar geçerli sürümün user.config korunur varsayılan olmayan değeriyle birleştirilir.|  
  
 Kendi uygulama ayarları sarmalayıcı sınıfı oluşturduysanız ve güncelleştirme mantığı özelleştirmek istiyorsanız, geçersiz kılabilirsiniz <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> yöntemi.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce ve Dolaşım ayarları  
 ClickOnce ile Dolaşım ayarları, ağdaki makineler arasında izlemek ayarlar dosyanızı sağlayan çalışmaz. Dolaşım ayarlarına ihtiyacınız varsa, ağ üzerinden ayarları depolayan bir uygulama ayarları sağlayıcısı veya bir uzak bilgisayarda ayarları depolamak için kendi özel ayarları sınıflarınızı geliştirmek ihtiyacınız olacak. Ayar sağlayıcıları daha fazla bilgi için bkz. [uygulama ayarları mimarisi](http://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [Uygulama ayarlarına genel bakış](http://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md)   
 [ClickOnce Uygulamalarında Yerel ve Uzak Veri Erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)



