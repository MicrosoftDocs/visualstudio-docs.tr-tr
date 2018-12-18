---
title: VSPerf | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c841e6930db8f65aaf93c314359656689ecfd1c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903549"
---
# <a name="vsperf"></a>VSPerf
Kullanım **VsPerf** komut satırı aracı:  
  
1. Visual Studio cihazda yüklü değilse komut satırından UWP uygulamaları profil.  
  
2. Masaüstü uygulamalarını Windows 8 ve Windows Server 2012 uygulamalar örnekleme profili oluşturma yöntemi kullanarak profil.  
  
   Profil oluşturma seçenekleriniz hakkında daha fazla bilgi için bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="uwp-apps-only"></a>Yalnızca UWP uygulamaları  
 Bu seçenekler yalnızca UWP uygulamaları için geçerlidir.  
  
|||  
|-|-|  
|**/App: {AppName}**|Profil oluşturucuyu başlatır ve Başlat Menüsü'nden başlatılmak üzere belirtilen uygulama bekler.<br /><br /> Çalıştırma `vsperf /listapps` Pakettamadı yüklü uygulamalar ve uygulama adı görüntülemek için.|  
|**/ Paket: {Pakettamadı}**|Profil oluşturucuyu başlatır ve Başlat Menüsü'nden başlatılmak üzere belirtilen uygulama bekler.<br /><br /> Çalıştırma `vsperf /listapps` Pakettamadı yüklü uygulamalar ve uygulama adı görüntülemek için.|  
|**/js**|Profil oluşturma JavaScript uygulamaları için gereklidir.<br /><br /> JavaScript uygulamalarından performans verilerini topla.<br /><br /> Sadece/Package kullanımı veya / ekleyin.|  
|**/noclr**|İsteğe bağlı. CLR veri toplamaz.<br /><br /> Sadece/Package kullanımı veya / ekleyin.<br /><br /> En iyi duruma getirilmesi, yönetilen sembol çözülecektir.|  
|**/listapps**|Yüklü uygulama adları ve PackageFullNames listeleyin.|  
  
## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>Masaüstü uygulamalarını Windows 8 ve Windows Server 2012 uygulamalar  
 Bu seçenekler, UWP uygulamaları üzerinde çalışmaz.  
  
|||  
|-|-|  
|**/ launch: {yürütülebilir}**|Başlatır ve belirtilen yürütülebilir dosya profil oluşturma başlar.|  
|**args: {ExecutableArguments}**|Geçirilecek komut satırı bağımsız değişkenlerini belirtir **/başlatma** hedef.|  
|**/ Console**|Çalıştırmaları **/başlatma** hedef yeni bir komut penceresinde.|  
  
## <a name="all-applications"></a>Tüm uygulamalar  
 Bu seçenek, herhangi bir Windows 8 veya Windows Server 2012 uygulama için geçerlidir.  
  
|||  
|-|-|  
|**/ ekleme: {PID&#124;ProcessName} [, PID&#124;ProcessName]...**|Belirtilen işlemlerden veri toplar.<br /><br /> İşlem kimliği (PID) görüntülemek ve işlem adları çalışan uygulamalar için Görev Yöneticisi'ni kullanın.|  
|**/ file:{ReportName}**|İsteğe bağlı. Çıkış dosyası (varolan dosyanın üzerine yazar) belirtir.<br /><br /> Sadece/Package kullanımı veya / ekleyin.|  
|**/ Pause**|Veri koleksiyonu duraklatın.|  
|**/Resume**|Veri koleksiyonu devam ettirin.|  
|**/ stop**|Veri toplama işlemini durdurun ve hedef işlemleri sonlandırın.|  
|**/ detach**|Veri toplamayı Durdur, ancak çalışmaya devam hedef işlemler sağlar.|  
|**/ Status**|Profil Oluşturucu durumunu gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)