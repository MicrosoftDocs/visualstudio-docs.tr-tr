---
title: Android için Visual Studio öykünücüsü sistem gereksinimleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ea73057992447016b1b9ac68c98b79b68f70c17
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881618"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Android için Visual Studio öykünücüsü sistem gereksinimleri
Android için Visual Studio öykünücü Hyper-V sanallaştırma teknolojisini Windows 8 ve sonraki sürümler için bir sanal makine olarak çalışır. Öykünücüyü çalıştırmak için bilgisayarınızda bu konuda açıklandığı gibi Hyper-V çalıştırma gereksinimlerini karşılaması gerekir.  
  
 Öykünücü yüklediğinizde, bu önkoşulları sessiz bir şekilde yapılandırmak Kurulum programı çalışır. Kurulum Önkoşulları başarıyla yapılandırdığında öykünücü yalnızca beklendiği gibi çalışır. Aksi takdirde bu Önkoşullar el ile etkinleştirmeniz gerekebilir. Önkoşulları el ile yapılandırmanız varsa, araçları ve adımları açıklanan adımlarıyla aynıdır [burada](/previous-versions/windows/apps/jj863509\(v=vs.105\)) Windows Phone öykünücüsü.  
  
> [!IMPORTANT]
>  Kurulum programı öykünücüsü Android için Visual Studio öykünücüsü'nü çalıştıran önkoşulları denetler. Önkoşulları mevcut değildir, ancak bunları gerektirmeyen uyarıları görüntüler.  
  
 Bu konuda aşağıdaki bölümleri içerir.  
  
-   [Hızlı Denetim listesi](#Checklist)  
  
-   [Sistem gereksinimleri](#System)  
  
-   [Ağ gereksinimleri](#Network)  
  
-   [Hyper-V gereksinimleri](#HyperV)  
  
-   [Önyüklenebilir bir VHD'den öykünücüyü çalıştırma desteklenmiyor](#BootableVHD)  
  
-   [Hyper-V sıkıştırılmamış ve şifrelenmemiş dosyaları gerektirir.](#Files)  
  
##  <a name="Checklist"></a> Hızlı Denetim listesi  
 Android için Visual Studio öykünücü çalıştırmak için gereksinimleri hızlı listesi aşağıda verilmiştir. Daha ayrıntılı bilgi için bu konudaki sonraki bölümlere bakın.  
  
 Sistem gereksinimleri  
  
- Hyper-V desteği (Hyper-V gereksinimler için aşağıya bakın)  
  
- 6 GB veya daha fazla RAM.  
  
- Pro sürümü Windows 8, Windows 8.1, Windows 10 veya üzerinin 64 bit sürümü  
  
- SSSE3 destekleyen bir işlemci veya üzeri.  
  
  Ağ gereksinimleri  
  
- DHCP  
  
- Otomatik olarak yapılandırılan DNS ve ağ geçidi ayarları  
  
  Hyper-V gereksinimleri  
  
- Aşağıdaki özellikler BIOS'ta desteklenmesi gerekir:  
  
  -   Donanım destekli sanallaştırma  
  
  -   İkinci düzey adres çevirisi (SLAT)  
  
  -   Donanım tabanlı Veri Yürütme Engellemesi (DEP)  
  
- Windows Hyper-V etkinleştirilmiş ve çalışıyor olması gerekir.  
  
- Yerel Hyper-V Yöneticileri grubunun bir üyesi olmanız gerekir.  
  
##  <a name="System"></a> Sistem gereksinimleri  
 Bilgisayarınız, aşağıdaki gereksinimleri karşılamalıdır:  
  
- Hyper-V desteği (bkz [Hyper-V gereksinimleri](#HyperV))  
  
- 6 GB veya daha fazla RAM.  
  
- Windows 8, Windows 8.1, Windows 10 veya daha yüksek Pro sürümü 64-bit sürümü.  
  
  RAM ve Denetim Masası ' nda Windows gereksinimleri denetlemek için sistem ve güvenlik seçin ve ardından sistemi seçin.  
  
  ![Sistem gereksinimlerini doğrulayın](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")  
  
##  <a name="Network"></a> Ağ gereksinimleri  
 Ağınızda aşağıdaki gereksinimleri karşılaması gerekir:  
  
- DHCP  
  
   Kendi IP adresini ağ üzerinde ayrı bir cihaz olarak kendisini yapılandırır için öykünücü DHCP gerektirir.  
  
- Otomatik olarak yapılandırılan DNS ve ağ geçidi ayarları  
  
   Öykünücü için el ile DNS ve ağ geçidi ayarlarını yapılandırmak mümkün değildir.  
  
  Öykünücü'de ağ sorunlarını gidermek için aşağıdaki konulara bakın:  
  
- [Android için Visual Studio Öykünücüsü’nde Sorun Giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)  
  
##  <a name="HyperV"></a> Hyper-V gereksinimleri  
 BIOS'u Hyper-V gereksinimleri  
  
 Bilgisayarınızın BIOS aşağıdaki gereksinimleri desteklemesi gerekir ve etkinleştirilmesi gerekir:  
  
- Donanım destekli sanallaştırma  
  
- İkinci düzey adres çevirisi (SLAT)  
  
- Donanım tabanlı Veri Yürütme Engellemesi (DEP)  
  
  Windows Hyper-V gereksinimleri  
  
  Bilgisayar ve BIOS ayarları zaten Hyper-V desteklemek üzere yapılandırıldığında, Kurulum programını sağlar ve Hyper-V başlatır. Aksi takdirde bu gereksinimleri el ile etkinleştirmeniz gerekebilir.  
  
|Gereksinim|Denetleyin ve bu gereksinim etkinleştirme|  
|-----------------|----------------------------------------------|  
|Hyper-V yüklü olmalıdır|İçin kullanılan aynı yönergeleri izleyerek [Hyper-V için Windows Phone öykünücüsü'nü etkinleştirme](https://docs.microsoft.com/previous-versions/windows/apps/jj863509(v=vs.105)).<br /><br /> Durumunu **Hyper-V sanal makine Yönetimi** Hizmetler ek bileşeninde hizmet.|  
|Hyper-V çalıştıran gerekir.|Hizmetleri yönetme hakkında daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> -   [Başlat, Durdur, duraklatma, sürdürme veya bir hizmetini yeniden başlatın](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Bir hizmetin nasıl başlatılacağını yapılandırın](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|  
  
 Yerel Hyper-V Yöneticileri grubunun bir üyesi olmanız gerekir.  
  
 Android için Visual Studio öykünücü haklarınızı yükseltmek için yinelenen bir istem olmadan çalıştırmak için yerel Hyper-V Yöneticileri grubunun bir üyesi olmanız gerekir. SDK'yı yüklediğinizde bilgisayarda yerel yönetici zaten varsa, SDK'sı için Kurulum programı Hyper-V Administrators grubuna ekler. Aksi takdirde bu gereksinim el ile etkinleştirmeniz gerekebilir.  
  
 Öykünücü çalıştırdığınızda, zaten Hyper-V Yöneticileri grubunun bir üyesi değilseniz, (Windows Phone öykünücüsü için iletişim kutusu atıfta bulunmaktadır) bir gruba katılması istenir. Gruba katılıyor yönetici hakları gerekir.  
  
> [!IMPORTANT]
> Gruba katıldıktan sonra oturumunu kapatmanız veya etkili değişiklik yapmak için yeniden başlatın.  
  
 ![Birleştirme Hyper&#45;V Administrators güvenlik grubunun](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")  
  
 Kendiniz bir gruba el ile eklemek için yerel kullanıcılar ve Gruplar ek bileşenini açın.  
  
##  <a name="BootableVHD"></a> Önyüklenebilir bir VHD'den öykünücüyü çalıştırma desteklenmiyor  
 Önyüklenebilir bir VHD'den Windows çalışırken bir uygulamayı Android için Visual Studio öykünücü üzerinde çalıştırmayı denerseniz öykünücü genellikle başlaması birkaç dakika sürer veya başlatılamıyor. Öykünücü başlatmak başarısız olduğunda, aşağıdaki iletiyi görürsünüz: uygulama dağıtımı başarısız oldu. Lütfen yeniden deneyin.  
  
 Bu yapılandırma desteklenmez. İlgili sorunlar hakkında daha fazla bilgi için bkz: [Android için Visual Studio öykünücü sorun giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
##  <a name="Files"></a> Hyper-V sıkıştırılmamış ve şifrelenmemiş dosyaları gerektirir.  
 Bir sabit sürücüde NTFS dosya sistemi ile yapılandırılmış Hyper-V tarafından kullanılan sanal sabit disk dosyalarını sıkıştırılmamış ve şifrelenmemiş. Aşağıdaki dizinler sıkıştırılmış veya şifrelenmiş değil, emin olun:  
  
- %localappdata%\Microsoft\XDE  
  
- C:\Program dosyaları (x86) \Microsoft öykünücü yöneticisi  
  
- C:\Program Files (x86)\Microsoft Visual Studio Emulator for Android  
  
- %localappdata%\Microsoft\VisualStudioEmulator  
  
  ReFS dosya sistemi sanal sabit disk dosyalarını bütünlüğü bit kümesi olmamalıdır.  
  
## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Donanım grafik (OpenGL ES destek) gereksinimlerini iletme  
 OpenGL ES tarafından kullanılanlar gibi GPU çağrıları benzetmek öykünücüsü makinenize DirectX uyumlu GPU'ya uygun DirectX sürücüleri yüklü olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Android için Visual Studio öykünücüsü sorunlarını giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
