---
title: Windows Installer temel bilgileri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3756f8e9c8b22b9e6a7da52e076364024fe49d1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747658"
---
# <a name="windows-installer-basics"></a>Temel Windows Installer Bilgileri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Windows Installer yükler ve uygulamalar veya yazılım ürünlerinin bir kullanıcının bilgisayarında Windows Yükleyici bileşenlerini (bazen WICs veya yalnızca bileşenleri olarak adlandırılır) olarak adlandırılan birimler içinde bu görevleri gerçekleştirmeye kaldırır. Bir GUID, yükleme ve başvuru sayımı Windows Installer kullanarak ayarları için temel birimdir her WIC tanımlar.  
  
 Windows Installer'ın kapsamlı belgeler için Platform SDK'sı, konusuna [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## <a name="authoring-a-vspackage"></a>VSPackage geliştirme  
 Windows Installer, Windows Installer yükleme, kaldırma veya bir ürünü onarın ve Kurulum kullanıcı arabirimi (UI) çalıştırmak için gereken bilgileri içeren yükleme paketleri kullanır. Her yükleme paketini yükleme veritabanı, Özet bilgi akışı ve veri akışları için yükleme çeşitli kısımlarını içeren bir .msi dosyasını içerir. Yükleyici kullanmak için bir yükleme yazmanız gerekir. Yükleyici bileşenlerini kavramı çevresinde yüklemeleri düzenler ve yükleme hakkında bilgi ilişkisel bir veritabanında depolar için geniş bir yükleme paketi yazma işlemi aşağıdaki adımları kapsar:  
  
1. Sürüm oluşturma ve yan yana stratejileri desteklemek için yazma kurulumunuzu planlayın.  
  
2. Kullanıcılara sunulması için özellikleri tanımlayın.  
  
3. VSPackage'ı ve bağımlılıkları bileşenlerine düzenleyin.  
  
4. Yükleme veritabanı bilgileri ile doldurun.  
  
5. Yükleme paketini doğrula.  
  
   Bu belge, öncelikli olarak birinci ve üçüncü adımlarla işleminin ilgilidir. Sürüm oluşturma ve hizmet sunma stratejisi sonraki sürümleri için hesap için çerçeve için bu adımları sırasında VSPackage özelliklerinizi WICs düzenlemenize [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Kalan üç adımı ayrıntılı olarak Windows Installer Platform SDK belgelerinde ele alınmaktadır.  
  
## <a name="key-terms"></a>Önemli terimler  
 İçin Windows Yükleyici teknolojisi ilgili anahtar terimlerin tanımları aşağıda verilmiştir.  
  
 Kaynak  
 Dosyaları, kayıt defteri anahtarlarını, kısayolları, veya vb., yüklenmiş olabilir bir bilgisayara. Bu kaynakları mantıksal olarak Windows Yükleyici bileşenlerini gruplandırılır.  
  
 Windows Installer component (WIC)  
 Yükleme yüklü olan ve kaldırılmış bir birim olarak ilgili kaynakların mantıksal bir gruplandırmasını gösteren temel birimidir. Windows Yükleyici bileşenlerini bir bileşen benzersiz kimliği veya GUID tarafından tanımlanır. Ayrıca, Windows Installer WIC düzeyinde sayım, başvuru tutar. En yüksek sürüm esneklik için bir DLL gibi birden fazla birincil kaynak belirli bir WIC içerir. Sizi tanımlamak ve bir WIC doldurmak, bir GUID verin ve dağıttıktan sonra kendi bileşim değiştiremeyeceğinizi unutmayın. Daha fazla bilgi için [bileşenleri düzenleme uygulamalarınızı](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Paket (yeniden dağıtılabilir paketi)  
 .Msi dosyasını ve dış kaynak dosyaları bu dosyayı işaret ediyor olabilir oluşan bir dağıtım birimidir. Bir paketi Windows Installer kullanıcı arabirimini çalıştırın ve yüklemek veya uygulamayı kaldırmak için gereken tüm bilgileri içerir.  
  
 .msi dosyası  
 Yönergeler ve bir uygulamayı yüklemek için gereken verileri içeren bir COM yapılandırılmış depolama dosyası. Her paket, en az bir .msi dosyasını içerir. .Msi dosyasını yükleyici veritabanı, bir Özet bilgi akışı ve büyük olasılıkla bir veya daha fazla dönüşümler ve iç kaynak dosyaları içerir. Yüklenecek dosyaları bir dolap sıkıştırılmış ve .msi dosyasına bir akışa depolanır veya depolanan, sıkıştırılmış veya sıkıştırılmamış kaynak ortamdaki .msi dosyasını dışında. Daha fazla bilgi için [Windows Installer dosya uzantıları](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Windows Installer kuralları zorlama  
 İki kural kümesi kurulumunuzu ait bileşenleri kaynaklarında dağıtımını belirleyin. İkinci Küme yükleme yazarı olarak uygulamalıdır sırada bir kural kümesi Windows Installer kendisi tarafından korunur.  
  
> [!NOTE]
>  Yalnızca .msi dosyasının bir doğrulama çalıştırırsanız, Windows Installer kural zorlama gerçekleşir. Bununla birlikte, bu kurallar en iyi yöntemler olarak değerlendirilecek dikkatli olmalıdır. Daha fazla bilgi için [yükleme veritabanı doğrulanıyor](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) ve [paket doğrulama](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Yükleyici tarafından zorlanan kuralları  
  
-   Belirli bir bileşene tüm dosyalar aynı dizinine yüklenmelidir. Buna karşılık, dosya klasörleri ayırmak için yüklü bileşenleri ayrı ait olmalıdır.  
  
-   Bileşen başına yalnızca bir anahtar yolu olabilir. Tüm bileşeni gösteren basit bir dosya veya kayıt defteri anahtarı anahtar yoludur.  
  
#### <a name="component-provider-responsibilities"></a>Bileşen sağlayıcısı sorumlulukları  
  
-   Sonraki sürümlerde de ayrı olarak sevk herhangi iki kaynakları ayrı bileşenler var olmalıdır. Yalnızca bu kaynakları hiçbir zaman ayrı olarak sevk edilir, belirli işiniz kaynakları aynı bileşenin gruplandırılmalıdır. Aslında, önerilir tüm birincil kaynaklar (örneğin, dll) her zaman ayrı WICs içinde mevcut. Daha fazla bilgi için [tanımlama yükleyici bileşenlerini](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Tutulan kaynak hiç olmadığı kadar içinde birden fazla WIC sevk etmesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bileşen kuralları bozuk olması durumunda ne olur?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)

