---
title: ClickOnce ve uygulama ayarlarını | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d3cf6320401f58cd8ea1733e3b972202ba9b6d3
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081100"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce ve uygulama ayarları
Windows Forms için uygulama ayarları oluşturmak, depolamak ve özel uygulama ve kullanıcı tercihlerini istemcide bakımını yapmayı kolaylaştırır. Uygulama ayarları dosyaları bir ClickOnce uygulamasında nasıl çalışır ve kullanıcı sonraki bir sürüme yükseltildiğinde ClickOnce ayarları nasıl geçirdiğini aşağıdaki belge açıklar.  
  
 Aşağıdaki bilgiler yalnızca varsayılan uygulama ayarları sağlayıcısına geçerlidir \<xref:System.Configuration.LocalFileSettingsProvider > sınıfı. Özel bir sağlayıcı sağlarsanız, bu sağlayıcı, verileri nasıl depoladı ve ayarlarına sürümleri arasında yükseltme nasıl belirler. Uygulama ayarları sağlayıcıları hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="application-settings-files"></a>Uygulama ayarları dosyaları  
 Uygulama ayarları, iki dosya kullanır:  *\<uygulama >. exe.config* ve *user.config*burada *uygulama* Windows Forms uygulamanızın adıdır. *User.config* uygulamanızın kullanıcı kapsamlı ayarları depolar istemciye ilk kez üzerinde oluşturulur. *\<Uygulama >. exe.config*, ayarlar için varsayılan değerleri tanımlarsanız aksine, dağıtımdan önce mevcut. Visual Studio içerecektir bu dosya otomatik olarak kullandığınızda, **Yayımla** komutu. ClickOnce kullanarak uygulama oluşturursanız *Mage.exe* veya *MageUI.exe*, bu dosya ile dahil olduğundan emin olmanız gerekir, uygulama bildiriminizi uygulamanızın diğer dosyaları kullanıcının.  
  
 ClickOnce, uygulama kullanıcının kullanmadan dağıtılan bir Windows Forms uygulamalarındaki  *\<uygulama >. exe.config* dosya, uygulama dizininde depolanır ancak *user.config* dosyasının depolandığı kullanıcının içinde **belgeler ve ayarlar** klasör. Bir ClickOnce uygulamasında  *\<uygulama >. exe.config* ClickOnce uygulama önbelleği içinde uygulama dizininde yer alan ve *user.config* ClickOnce veri dizininde bulunur Bu uygulama için.  
  
 Uygulamanızı nasıl dağıtmak bağımsız olarak, uygulama ayarları sağlar güvenli okuma erişimi  *\<uygulama >. exe.config*ve güvenli okuma/yazma erişimi *user.config*.  
  
 Bir ClickOnce uygulamasında uygulama ayarları tarafından kullanılan yapılandırma dosyalarını boyutunu ClickOnce önbellek boyutuyla sınırlıdır. Daha fazla bilgi için [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Sürüm yükseltme  
 Yalnızca ClickOnce uygulaması'nün her sürümü tüm diğer sürümlerden yalıtılmış olduğundan, ClickOnce uygulaması için uygulama ayarları için diğer sürümlerinde de ayarlardan yalıtılır. Kullanıcınızın, uygulamanızın sonraki bir sürüme yükseltildiğinde, uygulama ayarları en son (en yüksek numaralı) sürümün ayarları ayarlar nesnesine yeni bir ayar dosyaları birleştirme ve güncelleştirilmiş sürümü ile sağlanan ayarların karşı karşılaştırır.  
  
 Aşağıdaki tabloda, uygulama ayarları kopyalamak için hangi ayarların nasıl karar verir açıklanmaktadır.  
  
|Değişiklik türü|Yükseltme eylemi|  
|--------------------|--------------------|  
|Eklenen ayarı  *\<uygulama >. exe.config*|Yeni ayar geçerli sürüme ait birleştirilir  *\<uygulama >. exe.config*|  
|Kaldırıldığında ayarı  *\<uygulama >. exe.config*|Eski ayarı güncel sürümün kaldırılır  *\<uygulama >. exe.config*|  
|Ayarın varsayılan; değiştirildi yerel ayar hala ayarlanmış orijinal varsayılan olarak *user.config*|Ayar güncel sürümün birleştirilir *user.config* yeni varsayılan değer olarak|  
|Ayarın varsayılan; değiştirildi Varsayılan olmayan olarak ayarlanmasını *user.config*|Ayar güncel sürümün birleştirilir *user.config* korunur varsayılan olmayan değere sahip|  
  
Kendi uygulama ayarları sarmalayıcı sınıfı oluşturduysanız ve güncelleştirme mantığı özelleştirmek istiyorsanız, geçersiz kılabilirsiniz \<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A > yöntemi.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce ve Dolaşım ayarları  
 ClickOnce ile Dolaşım ayarları, ağdaki makineler arasında izlemek ayarlar dosyanızı sağlayan çalışmaz. Dolaşım ayarlarına ihtiyacınız varsa, ağ üzerinden ayarları depolayan bir uygulama ayarları sağlayıcısı veya bir uzak bilgisayarda ayarları depolamak için kendi özel ayarları sınıflarınızı geliştirmek ihtiyacınız olacak. Ayar sağlayıcıları daha fazla bilgi için bkz. [uygulama ayarları mimarisi](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [Uygulama ayarlarına genel bakış](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md)   
 [ClickOnce uygulamalarında yerel ve uzak veri erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)