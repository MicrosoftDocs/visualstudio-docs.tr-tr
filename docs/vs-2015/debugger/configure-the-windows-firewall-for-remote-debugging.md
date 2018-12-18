---
title: Uzaktan hata ayıklama için Windows Güvenlik Duvarı yapılandırma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39854b47bd31660fdc523bfd122363d5958df8e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734593"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Uzaktan hata ayıklama için Windows Güvenlik duvarını yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, aşağıdaki işletim sistemlerini çalıştıran bilgisayarlarda uzaktan hata ayıklamayı etkinleştirmek için Güvenlik Duvarı'nı yapılandırmak açıklar:  
  
- Windows 7  
  
- Windows 8/8.1  
  
- Windows 10  
  
- Windows Server 2008 (R2)  
  
- Windows Server 2012  
  
- Windows Server 2012 R2  
  
  Bu yapılandırma üzerinde hata ayıklaması yapıyorsanız ağ güvenlik duvarı tarafından korumalı değilse gereksizdir. Aksi takdirde, hem Visual Studio barındıran bilgisayarda hem de ayıklanacak uzak bilgisayarda güvenlik duvarı yapılandırması değişiklikleri gerektirir.  
  
  **IPSec** ağınız iletişimin gerektiriyorsa olması IPSec kullanarak gerçekleştirilen, hem Visual Studio ana bilgisayar hem de uzak bilgisayara ek bağlantı noktalarını açmanız gerekir.  
  
  **Web sunucusu** uzak bir Web sunucusunda hata ayıklaması yapıyorsanız, uzak bilgisayardaki ek bir bağlantı noktası açmanız gerekir.  
  
  Her iki bilgisayar aynı işletim sistemini çalıştırmak olmadığını unutmayın. Örneğin, Visual Studio bilgisayarı, Windows 10 çalıştırabilirsiniz ve Windows Server 2012 R2 Uzak bilgisayarda çalıştırabilirsiniz.  
  
## <a name="to-configure-windows-firewall-on-the-visual-studio-computer"></a>Visual Studio bilgisayarda Windows Güvenlik Duvarı'nı yapılandırmak için  
 Windows Güvenlik Duvarı yapılandırma yönergeleri biraz daha farklı işletim sistemleri üzerinde farklı. Windows 7 veya Windows Server 2008, word **program** kullanılır; Windows 8/8.1, Windows 10 ve Windows Server 2012, word **uygulama** kullanılır.  Aşağıdaki adımlarda word kullanacağız **uygulama**.  
  
1.  Windows Güvenlik Duvarı sayfasını açın. (İçinde **Başlat** menü arama kutusuna **Windows Güvenlik Duvarı**).  
  
2.  Tıklayın **bir uygulama veya özelliğin Windows Güvenlik Duvarı üzerinden izin**.  
  
3.  İçinde **izin verilen uygulamalar ve Özellikler** listesinde, Aranan **Visual Studio uzaktan hata ayıklayıcı bulma**. Listeleniyorsa, seçili olduğunu ve bir veya daha fazla ağ türü ayrıca seçildiğinden emin olun.  
  
4.  Varsa **Visual Studio uzaktan hata ayıklayıcı bulma** olan listelenmeyen tıklayın **başka bir uygulamanın ver**. İçinde hala görmüyorsanız, **uygulama ekleme** penceresinde tıklayın **Gözat** gidin  **\<Visual Studio yükleme dizini > \Common7\IDE\Remotehataayıklayıcı**. (X86, x64, Appx) uygulama için ilgili klasörü bulun ve ardından **msvsmon.exe**. Ardından **Ekle**.  
  
5.  İçinde **izin verilen uygulamalar ve Özellikler** listesinden **Visual Studio uzaktan hata ayıklama İzleyicisi**. Bir veya daha fazla ağ türlerini denetleyin (**etki alanı, ev/iş (özel), ortak**) ile iletişim kurmak için uzaktan hata ayıklama İzleyicisi istiyor. Visual Studio bilgisayarın bağlı olduğu ağ türleri eklemeniz gerekir.  
  
## <a name="to-open-a-port-on-the-visual-studio-computer-to-enable-discovery"></a>Bulmayı etkinleştirmek için Visual Studio bilgisayarında bir bağlantı noktasını açmak için  
 Uzaktan hata ayıklayıcıyı çalıştıran bilgisayarlar bulunmasını izin vermek UDP bağlantı noktası 3702 gelen izin vermeniz gerekir. Eklemek için bkz. nasıl bir güvenlik duvarı bağlantı noktalarını yapılandırma.  
  
## <a name="to-configure-the-windows-firewall-of-the-remote-computer-for-remote-debugging"></a>Uzak bilgisayar uzaktan hata ayıklama için Windows Güvenlik Duvarı'nı yapılandırmak için  
 Uzaktan hata ayıklama bileşenlerini, uzak bilgisayarda yüklü veya paylaşılan bir dizinden çalıştırabilirsiniz. Güvenlik duvarının uzak bilgisayar, her iki durumda da yapılandırılması gerekir. Uzaktan hata ayıklama bileşenleri bulunur:  
  
 **\<Visual Studio yükleme dizini > \Common7\IDE\Remote hata ayıklayıcı**  
  
 Windows Güvenlik Duvarı yapılandırma yönergeleri biraz daha farklı işletim sistemleri üzerinde farklı. Windows 7 veya Windows Server 2008, word **program** kullanılır; Windows 8/8.1, Windows 10 ve Windows Server 2012, word **uygulama** kullanılır.  Aşağıdaki adımlarda word kullanacağız **uygulama**.  
  
1.  Windows Güvenlik Duvarı sayfasını açın. (Üzerinde **Başlat** menü arama kutusuna **Windows Güvenlik Duvarı**.)  
  
2.  Tıklayın **bir uygulama veya özelliğin Windows Güvenlik Duvarı üzerinden izin**.  
  
3.  İçinde **izin verilen uygulamalar ve Özellikler** listesinde, Aranan **Visual Studio uzaktan hata ayıklama İzleyicisi**. Listeleniyorsa, seçili olduğunu ve bir veya daha fazla ağ türü ayrıca seçildiğinden emin olun.  
  
4.  Varsa **Visual Studio uzaktan hata ayıklama İzleyicisi** olan listelenmeyen tıklayın **başka bir uygulamanın ver**. İçinde hala görmüyorsanız, **ekleme uygulama penceresi**, tıklayın **Gözat** gidin  **\<Visual Studio yükleme dizini > \Common7\IDE\Remotehataayıklayıcı**. (X86, x64, Appx) uygulama için ilgili klasörü bulun ve ardından **msvsmon.exe**. Ardından **Ekle**.  
  
5.  İçinde **izin verilen uygulamalar** listesinden **Visual Studio uzaktan hata ayıklama İzleyicisi**. Bir veya daha fazla ağ türlerini denetleyin (**etki alanı, ev/iş (özel), ortak**) ile iletişim kurmak için uzaktan hata ayıklama İzleyicisi istiyor. Visual Studio bilgisayarın bağlı olduğu ağ türleri eklemeniz gerekir.  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Uzak bilgisayarda uzaktan hata ayıklamayı etkinleştirme bağlantı  
  
|||||  
|-|-|-|-|  
|**Bağlantı Noktaları**|**Gelen ve giden**|**Protokolü**|**Açıklama**|  
|3702|Giden|UDP|Uzaktan hata ayıklayıcı bulma işlemi için gereklidir.|  
|4020||TCP|VS 2015 için. Her bir Visual Studio sürümü için 2 bağlantı noktası numarası artırılır. Daha fazla bilgi için Visual Studio uzaktan hata ayıklayıcı bağlantı noktası atamaları konusuna bakın.|  
|4021||TCP|VS 2015 için. Her bir Visual Studio sürümü için 2 bağlantı noktası numarası artırılır. Daha fazla bilgi için Visual Studio uzaktan hata ayıklayıcı bağlantı noktası atamaları konusuna bakın.|  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging-with-managed-or-native-compatibility-mode"></a>Yönetilen veya yerel uyumluluk modunda uzaktan hata ayıklamayı etkinleştirme bağlantı noktalarını uzak bilgisayarda  
  
|||||  
|-|-|-|-|  
|**Bağlantı Noktaları**|**Gelen ve giden**|**Protokolü**|**Açıklama**|  
|135, 139, 445|Giden|TCP|Gerekli.|  
|137, 138|Giden|UDP|Gerekli.|  
|500, 4500|Giden|UDP|Etki alanı ilkeniz ağ iletişimi, IPSec gerçekleştirilmesini gerektiriyorsa gereklidir.|  
|80|Giden|TCP|Web sunucusu hata ayıklama için gereklidir.|  
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Windows Güvenlik Duvarı bağlantı noktalarını yapılandırma  
  
1.  Üzerinde **Başlat** menüsünde **Gelişmiş Güvenlik Özellikli Windows Güvenlik Duvarı**.  
  
2.  Tıklayın **gelen kuralları** veya **giden kuralları** ve ardından **yeni kural** içinde **eylemleri** listesi.  
  
3.  Üzerinde **kural türü** sayfasında **bağlantı noktası** ve ardından **sonraki**.  
  
4.  Üzerinde **protokol ve bağlantı noktaları** sayfasında, bağlantı noktası Protokolü (TCP veya UDP) seçin. Seçin **belirli yerel bağlantı noktaları** ve protokolü için etkinleştirmek istediğiniz bir veya daha fazla bağlantı noktası numaraları girin. Ayrı numaralarını virgülle. Sonra **İleri**'ye tıklayın.  
  
5.  Üzerinde **eylem** sayfasında **bağlantıya izin** ve ardından **sonraki**.  
  
6.  Üzerinde **profili** sayfasında, bağlantı noktasını etkinleştirmek için bir veya daha fazla ağ türlerini seçin. Seçtiğiniz türü, uzak bilgisayarın bağlı olduğu ağ içermelidir. Sonra **İleri**'ye tıklayın.  
  
7.  Üzerinde **adı** sayfasında kural için bir ad yazın ve ardından **son**.  
  
8.  Yeni kuralınıza görmelisiniz **gelen kuralları** veya **giden kuralları** listesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)



