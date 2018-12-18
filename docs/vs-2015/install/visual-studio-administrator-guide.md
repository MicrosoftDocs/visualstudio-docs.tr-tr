---
title: Visual Studio Yönetici Kılavuzu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 25d6655969245adf1b2a28df2b3327561d149983
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722817"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio Yönetici Kılavuzu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 için en son belgeler için bkz. [Visual Studio 2017 Yönetici Kılavuzu](/visualstudio/install/visual-studio-administrator-guide).

Her hedef bilgisayar karşıladığı sürece Visual Studio 2015 bir ağda dağıtabilirsiniz [minimum yükleme gereksinimlerini](http://www.microsoft.com/visualstudio/eng/products/2013-editions). Bir ağ paylaşımı ile/layout anahtarını yükleme dosyasını çalıştırarak oluşturabilirsiniz (üzerinde açıklandığı [bir çevrimdışı Visual Studio yüklemesi oluşturma](../install/create-an-offline-installation-of-visual-studio.md) sayfası) ve ardından yerel makinede ağ paylaşımına kopyalama. Bir ISO kullanıyorsanız ISO'yu bağlamak ve paylaşın veya ISO dosyasını bir ağ paylaşımına kopyalayın.  
  
 Bir ağ paylaşımından yüklemeleri "kaynaklarına kaynak konumu hatırlayacağınızdan" unutmayın. Başka bir deyişle, istemci ilk olarak yüklendiği ağ paylaşımına döndürmek bir istemci makinesi onarılması gerekebilir. Böylece, kuruluşunuzda çalışan Visual Studio 2015 istemcileri sahip olmayı beklediğiniz kullanım ömrü hizalar, ağ konumu dikkatle seçin.  
  
## <a name="detection-and-servicing-keys"></a>Algılama ve hizmet anahtarları  
 Visual Studio ürün bir bilgisayarda zaten yüklü olup olmadığını belirlemek için kayıt defterinde algılama alt anahtarlarını kullanabilirsiniz. Bu algılama anahtarları bir yüklemeyle devam etmek gerekli olup olmadığını belirlemek için bir otomatik dağıtım kullanmanız gerekir.  Bkz: [sistem gereksinimlerini algılama](../extensibility/internals/detecting-system-requirements.md)[sistem gereksinimlerini algılama].  
  
## <a name="avoiding-reboots"></a>Yeniden başlatmaları önleme  
 Visual Studio dağıtmadan önce uygun Visual Studio önkoşulları karşıladığından emin olarak yeniden başlatmalar azaltabilir. .NET Framework için Visual Studio 2015 üzerinde .NET Framework 4.6 yüklemeden dağıtırsanız Windows 8 çalıştıran bilgisayarlarda yeniden başlatma gerekebilir.  
  
 Windows ve Android cihaz öykünmesi için Hyper-V açık Windows özelliği zaten yoksa bilgisayar yeniden başlatma gerekebilir. Web geliştirme Web sunucusu açık Windows özelliği zaten yoksa bilgisayar yeniden başlatmanız gerekebilir. Office geliştirme için Windows tanımlamak Foundation açık Windows özelliği zaten yoksa bilgisayar yeniden başlatmanız gerekebilir. Web sunucusu açık Windows özelliği zaten yoksa bilgisayar yeniden başlatın. Office geliştirme için Windows tanımlamak Foundation açık Windows özelliği zaten yoksa bilgisayar yeniden başlatmanız gerekebilir. Algılama ve Windows özellikleri yüklemesini otomatikleştirme hakkında daha fazla bilgi için bkz: [Windows Server 2008 R2 Sunucu Çekirdeği yüklemesini çalıştıran bir sunucuda bir sunucu rolü yükleme](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx).  
  
## <a name="error-return-codes"></a>Hata dönüş kodları  
 Aşağıdaki tablo önemli hata kodlarını listeler. Yeniden başlatma gerekli olduğunda ve yükleme başarılı olursa karar vermek için bu hata kodları, Otomasyon kullanabilirsiniz. Bir hata kodu alırsanız, sorun giderme adımlarını göz önünde bulundurun [Visual Studio'yu yükleyin](../install/install-visual-studio-2015.md) sayfası.  
  
|Kurulum durumu|Yeniden başlatma gerekmiyor.|Yeniden başlatma gerekiyor|Açıklama|  
|------------------|--------------------------|----------------------|-----------------|  
|Başarılı|0x00000000 [0]|0x00000bc2 [3010]|Başarılı yükleme.|  
|Blok|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|Rapor edilecek tek blok "Yeniden başlatma bekliyor" ise, döndürülen değer Incomplete-Reboot Required değeri (0x80048bc7) ' dir.|  
|İptal|0x00000642 [1602]|0x80048642 [-2147187134]|Yeniden başlatma değeri döndürüldüğünde dönüş kodu 1602'dir.|  
|Eksik-yeniden başlatma gerekiyor|Yok|0x80048bc7 [-2147185721]|Yüklemeye devam etmeden önce yeniden başlatılması gerekiyor.|  
|hata|0x00000643 [1603]|0x80048643 [-2147187133]|Yeniden başlatma değeri döndürüldüğünde dönüş kodu 1603 ' dir.|  
  
## <a name="interactive-administrator-installer"></a>Etkileşimli yönetici yükleyici  
 Visual Studio yüklemesi üzerinde etkileşimli bir yükleyici oluşturuyorsanız, Visual Studio yükleyicisinden ilerleme durumunu görüntüleyebilirsiniz. Visual Studio 2015 yükleyicisi açık kaynak Windows Installer XML (WiX) bağlayıcı teknolojisi, yerleşik olarak da bilinen "yazın." Yazma teknoloji iki iletişim protokollerini destekler: yazma ve netfx4. Kısa bir başvuru için lütfen ExePackage öğe için belgelerinde Protokolü öznitelik açıklamasına bakın [wixtoolset.org](http://wixtoolset.org/). Bir gözden geçirme, bu protokolü özniteliğin WiX açık kaynak uygulaması tümleştirmesi için gerekli olabilir.  
  
## <a name="controlling-what-is-installed"></a>Yüklenenler denetleme  
 Son kullanıcınızın yükleyebilmek için denetlemek istiyorsanız, iki seçenek vardır: yönetici dosya yükleme ve komut satırı seçenekleri. Amacınız ne, son kullanıcı kendi Visual Studio yükleyicisi deneyiminden seçebilir kısıtlamak için ise yönetici Dosya Yükleme'yi seçin. Bir başlangıç yapılandırması oluşturma, ancak kendi Visual Studio yükleyicisi deneyiminizi seçmek, son kullanıcı izin vermek istiyorsanız, komut satırı parametreleri seçin.  
  
 Yönetici dosya deneyimi hakkında daha fazla bilgi için bkz [nasıl yapılır: bir katılımsız yükleme Visual Studio'nun oluşturup](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) ve [nasıl yapılır:VisualStudio'yudağıtırkenürünanahtarlarınıotomatikolarakuygulama](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).  Komut satırı denetimleri hakkında daha fazla bilgi için bkz. [Visual Studio'yu yükleyin komut satırı parametreleri kullanmak](../install/use-command-line-parameters-to-install-visual-studio.md) sayfası.  
  
## <a name="specifying-customer-feedback-settings"></a>Müşteri geri bildirim ayarlarını belirtme  
 Varsayılan olarak, Visual Studio yüklemesini müşteri geri bildirim sağlar. "0" dizesi için aşağıdaki kayıt defteri anahtarının değerini değiştirerek tek tek bilgisayarlarda müşteri geri bildirimleri devre dışı bırakmak için Visual Studio yapılandırabilirsiniz:  
  
 **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
 (Örneğin, HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM OptIn olarak değiştirmek = "0")  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Nasıl Yapılır: Visual Studio’nun Belirli Bir Sürümünü Yükleme](../install/how-to-install-a-specific-release-of-visual-studio.md)|Geçerli sürümde olan belirli yapılandırmalar yüklemeyi açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Nasıl Yapılır: Katılımsız Visual Studio Yüklemesi Oluşturma ve Çalıştırma](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|Nasıl yüklendiğini açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] katılımsız modda.|  
|[Nasıl Yapılır: Visual Studio’yu dağıtırken ürün anahtarlarını otomatik olarak uygulama](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Birden çok makineye dağıtırken ürün anahtarlarını uygulama açıklar.|  
|[Yardım Görüntüleyicisi Yönetici Kılavuzu](../ide/help-viewer-administrator-guide.md)|Yerel Yardım yüklemelerini olması ya da internet erişimi olmaması ağ ortamları yönetme hakkında bilgi sağlar.|  
|[Visual Studio'yu yükleyin](../install/install-visual-studio-2015.md)|Yönergeler ve nasıl yükleneceğini açıklayan konulara bağlantılar sağlamaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|