---
title: VSPerf | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 830aa028e8c34beb5fd6818c40ffcfc7f3fa461b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755263"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanım **VsPerf** komut satırı aracı:  
  
1. Visual Studio cihazda yüklü değilse Windows Store uygulamaları komut satırından profil.  
  
2. Masaüstü uygulamalarını Windows 8 ve Windows Server 2012 uygulamalar örnekleme profili oluşturma yöntemi kullanarak profil.  
  
   Profil oluşturma seçenekleriniz hakkında daha fazla bilgi için bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 Bu konu ile kullanabileceğiniz seçenekler açıklanmaktadır `vsperf.exe` komut satırı aracı. Bu konuda aşağıdaki bölümleri içerir:  
  
 [Yalnızca Windows Store uygulamaları](#BKMK_windows_store_apps_only)  
  
 [Masaüstü uygulamalarını Windows 8 ve Windows Server 2012 uygulamalar](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Tüm uygulamalar](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Yalnızca Windows Store uygulamaları  
 Bu seçenekler yalnızca Windows Store uygulamaları için geçerlidir.  
  
|||  
|-|-|  
|**/App: {AppName}**|Profil oluşturucuyu başlatır ve Başlat Menüsü'nden başlatılmak üzere belirtilen uygulama bekler.<br /><br /> Çalıştırma `vsperf /listapps` Pakettamadı yüklü uygulamalar ve uygulama adı görüntülemek için.|  
|**/ Paket: {Pakettamadı}**|Profil oluşturucuyu başlatır ve Başlat Menüsü'nden başlatılmak üzere belirtilen uygulama bekler.<br /><br /> Çalıştırma `vsperf /listapps` Pakettamadı yüklü uygulamalar ve uygulama adı görüntülemek için.|  
|**/js**|Profil oluşturma JavaScript uygulamaları için gereklidir.<br /><br /> JavaScript uygulamalarından performans verilerini topla.<br /><br /> Sadece/Package kullanımı veya / ekleyin.|  
|**/noclr**|İsteğe bağlı. CLR veri toplamaz.<br /><br /> Sadece/Package kullanımı veya / ekleyin.<br /><br /> En iyi duruma getirilmesi, yönetilen sembol çözülecektir.|  
|**/listapps**|Yüklü uygulama adları ve PackageFullNames listeleyin.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Masaüstü uygulamalarını Windows 8 ve Windows Server 2012 uygulamalar  
 Bu seçenekler, Windows Store apps üzerinde çalışmaz.  
  
|||  
|-|-|  
|**/ launch: {yürütülebilir}**|Başlatır ve belirtilen yürütülebilir dosya profil oluşturma başlar.|  
|**args: {ExecutableArguments}**|Geçirilecek komut satırı bağımsız değişkenlerini belirtir **/başlatma** hedef.|  
|**/ Console**|Çalıştırmaları **/başlatma** hedef yeni bir komut penceresinde.|  
  
##  <a name="BKMK_All_applications"></a> Tüm uygulamalar  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Komut Satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)



