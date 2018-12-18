---
title: Çevrimdışı yüklemesini oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 0ac8f1c1d631e4d5f682fea5e1841e3914241d14
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055244"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Visual Studio'nun çevrimdışı yüklemesini oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 için en son belgeler için bkz. [düşük bant genişliği veya güvenilir olmayan ağ ortamlarında Visual Studio 2017 yükleme](https://docs.microsoft.com/visualstudio/install/install-vs-inconsistent-quality-network), veya [Visual Studio 2017'in bir ağ yüklemesini oluşturma](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio) ve [Çevrimdışı bir ortamda Visual Studio 2017'yi yüklemek için özel durumlar](https://docs.microsoft.com/visualstudio/install/install-visual-studio-in-offline-environment).

Bu sayfa, Internet'e bağlı olmadıkları sırada Visual Studio 2015 yüklemeyi açıklar. Ancak, "bağlantısız" bir yükleme gerçekleştirmek için önce bir çevrimdışı yükleme düzenini Internet'e bağlı bir makinede kullanarak oluşturmanız gerekir. Bunun nasıl yapılacağı aşağıda verilmiştir.

> [!IMPORTANT]
>  Çevrimdışı makinenize Windows 7 SP1 veya Windows Server 2008 R2 çalıştırıyorsa, lütfen özel yönergelere bakın [çevrimdışı yükleme sorunlarını giderme](#BKMK_tshoot) bu konudaki.  Bu yönergeleri izlemelidir *önce* Visual Studio 2015'i yükleyin.

##  <a name="BKMK_Offline"></a> Çevrimdışı yükleme oluşturarak yükleme

#### <a name="to-create-an-offline-installation-layout"></a>Çevrimdışı yükleme düzeni oluşturmak için

1.  Gelen yüklemek istediğiniz Visual Studio sürümünü seçin [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) indirme sayfası.

2.  Dosya sisteminizdeki bir konuma yükleyiciyi indirdikten sonra Çalıştır "\<çalıştırılabilir dosya adı >/layout".

     Örneğin, şunu çalıştırın: `vs_enterprise.exe /layout D:\VisualStudio2015`

     Kullanarak `/layout` anahtarı, neredeyse tüm yükleme paketlerini yalnızca yükleme makinesi için geçerli olanları indirebilirsiniz. Bu yaklaşım, her yerden bu yükleyiciyi çalıştırmak için gereken dosyaları sağlar ve başlangıçta yüklenmemiş bileşenleri yüklemek istiyorsanız yararlı olabilir.

3.  Bu komutu çalıştırdıktan sonra çevrimdışı yükleme düzenini bulunmasını istediğiniz klasörü değiştirmek izin veren bir iletişim kutusu görünür.   Ardından, **indirme** düğmesi.

     Paket başarılı olduğunda, bildiren bir ileti görürsünüz **Kurulum başarılı! Belirtilen tüm bileşenler başarıyla alındı.**

4.  Daha önce belirttiğiniz klasörünü bulun. (Örneğin, D:\VisualStudio2015 bulun.) Bu klasör veya yükleme medyasına paylaşılan bir konuma kopyalamak için ihtiyacınız olan her şeyi içerir.

    > [!CAUTION]
    >  Şu anda Android SDK'sı bir çevrimdışı yükleme deneyimi desteklemez. Android SDK Kurulumu öğelerini Internet'e bağlı olmayan bir bilgisayara yüklerseniz, yükleme başarısız olabilir. Daha fazla bilgi için bu konudaki "bir çevrimdışı yükleme sorunlarını giderme" bölümüne bakın.

5.  Dosya konumundan veya yükleme medyasından yüklemeyi çalıştırın.

## <a name="updating-an-offline-installation"></a>Çevrimdışı yüklemeyi güncelleştirme
 Microsoft Visual Studio 2015 için birkaç güncelleştirme yayımladı. Visual Studio yüklemenizi güncelleştirmek için yalnızca istediğiniz sürümü indirme alanından [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) indirme sayfası. Ardından, yeni bir çevrimdışı yükleme düzeni oluşturmak için bu konuda özetlenen adımları izleyin ve Visual Studio 2015 kopyanızın güncelleştirmek için kullanın.

##  <a name="BKMK_tshoot"></a> Çevrimdışı yükleme sorunlarını giderme
 Çevrimdışı yükleme sırasında çevrimdışı durumdan önbelleği yüklemek, bazı bileşenler ve paketleri yüklemek yükleyememeyle ilgili uyarı iletileri görebilirsiniz. Aşağıdaki tablo, bu senaryolar için olası çözümleri içerir.


|                                                                                       Bileşen veya paket                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                   Çözüm                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dotfuscator ve Analytics Community Edition 5.19.1 (Community, Professional ve Enterprise sürümleri için Visual Studio'nun yüklü olarak **Windows 7 SP1** ve **Windows Server 2008 R2**) |                                                                                                                                       Çevrimdışı makinenize çalışıyorsa **Windows 7 SP1** veya **Windows Server 2008 R2**, Visual Studio 2015'i yüklemeden önce aşağıdaki adımları gerçekleştirmeniz gerekir:<br /><br /> 1.  CTL dosyalarını indirmek için bir dosya veya web sunucusu yapılandırın.<br /><br /> 2.    Bağlantısı kesilmiş bir ortam için Microsoft otomatik güncelleştirme URL'sini yeniden yönlendirme.<br /><br /> Daha fazla bilgi için [yapılandırma Güvenilen Kökleri ve izin verilmeyen sertifikaları](https://technet.microsoft.com/library/dn265983.aspx) Microsoft TechNet sitesindeki sayfası.                                                                                                                                       |
|                                                                                  Android SDK kurulumu (API düzeyi)                                                                                   |                                                                        Android SDK'sı (API düzeyi) paketleri yüklemek için internet bağlantısı olması gerekir. Kısıtlanmış bir ağda varsa, Visual Studio'yu yüklediğinizde aşağıdaki URL'lere erişim izin vermeniz gerekir:<br /><br /> -   http://dl.google.com:443<br />-   http://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />Proxy ayarları ile olası sorunları çözme hakkında daha fazla bilgi için bkz. [Visual Studio 2015 yükleme hataları (Android SDK Kurulumu) bir proxy'nin arkasında](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) blog gönderisi.                                                                         |
|                             Visual Studio genişletilebilirlik öğe şablonları<br /><br /> Visual Studio için GitHub uzantısı<br /><br /> Visual Studio için PowerShell araçları                             | Visual Studio 2015'i yüklediğinizde, internet bağlantısı yoksa, özel bir çevrimdışı yükleme düzenini oluşturmak için çevrimdışı akış kullanabilirsiniz. **Not:** özel bu akışa Visual Studio 2015 için en son güncelleştirmeleri içerir. <br /><br /> Çevrimdışı akış özel oluşturmak için aşağıdaki komutu çalıştırın: / Layout *sürücü:* \VisualStudio2015 /overridefeeduri *xml akışı URL'si*<br /><br /> Örneğin, İngilizce dil için Visual Studio 2015 Enterprise'nın özel çevrimdışı akış çalıştırın:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "http://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Tercih ettiğiniz dilde özel bir çevrimdışı akış oluşturmak için kullanabileceğiniz URL'leri tam bir listesi için aşağıdaki tabloya bakın. |

 Yukarıdaki tabloda açıklandığı gibi bir dile özgü özel çevrimdışı akış, oluşturmak için aşağıdaki URL'ler kullanın.


|       Dil        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| ve  | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| seçenekleri yerine | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Çekçe         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Almanca         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        İngilizce        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        İspanyolca        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Fransızca         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        İtalyanca        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japonca        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Korece         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Lehçe         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portekizce       | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Rusça        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Türkçe        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'yu yükleyin]()