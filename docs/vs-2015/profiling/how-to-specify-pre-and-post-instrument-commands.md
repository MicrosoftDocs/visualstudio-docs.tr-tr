---
title: 'Nasıl yapılır: ön ve son izleme komutları belirtme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b88d49be8ee4651d82135b3e8d27bef8218ffd43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772228"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Nasıl yapılır: Ön ve Son İzleme Komutları Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Önce veya sonra performans oturumu içindeki ikili dosyaları notınstrumented çalışan komutlar belirtebilirsiniz. Komut satırından verilen herhangi bir komutu bir işaretleme öncesi veya izleme sonrası olayı olarak belirtilebilir. Örneğin, ikili dosyaları algılayıcılarla sonra çalıştırılan bir toplu iş dosyasında bir tanımlayıcı ad anahtarıyla bir derlemenin bildirimin otomatikleştirmek komutları belirtebilirsiniz.  
  
 Komutları için profil oluşturma çalıştırmasını tüm izleme eklenmiş ikili dosyaları veya bireysel ikili dosyaları belirtebilirsiniz. Bununla birlikte, önce çalıştırmak için yalnızca bir işaretleme öncesi komutu ve izleme işleminden sonra çalıştırmak için yalnızca bir son izleme komut belirtebilirsiniz. Komutları bireysel ikili dosyaları ve hem tüm ikili dosyaları için belirtilemez. Tüm ikili dosyaları için komutları belirttiğinizde, önce veya sonra her bir ikili izleme oturumunda komutları çalıştırılır.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Çalıştırdığınız işletim systen üzerinde komutları yürütülürken çalışma dizini bağlıdır [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ve profili oluşturulan uygulamanın hedef platformu.  
  
  **32-bit bilgisayarlar**  
  
  32-bit bilgisayarlarda varsayılan profil oluşturucu Araçlar önyükleme sürücüsü\Program Files\Microsoft Visual Studio 10.0\Team Araçlar\Performans araçları dizindir.  
  
  **64-bit bilgisayarlar**  
  
  64-bit bilgisayarlarda, profili oluşturulan uygulamanın hedef platformu göre yolu belirtin:  
  
- 32-bit uygulamalar için varsayılan profil oluşturucu Araçlar dizindir:  
  
   *Sürücü*\Program dosyaları (x86) \Microsoft Visual Studio 10.0\Team Araçlar\Performans araçları  
  
- 64-bit uygulamalar için varsayılan profil oluşturucu Araçlar dizindir:  
  
   *Sürücü*\Program dosyaları (x86) \Microsoft Visual Studio 10.0\Team Araçlar\Performans Tools\x64  
  
### <a name="to-specify-pre-instrument-commands"></a>İşaretleme öncesi komut belirtmek için  
  
1.  Aşağıdaki adımlardan birini uygulayın:  
  
    -   İşaretleme öncesi komutlar tüm ikili dosyaları için bir performans oturumu belirtmek için performans oturumu düğümünde seçin **performans Gezgini**ve ardından sağ tıklayıp **özellikleri**.  
  
    -   İşaretleme öncesi komut için belirli bir ikili belirtmek için ikili adına sağ tıklayın **hedefleri** performans oturumu tıklayın ve ardından listesi **özellikleri**.  
  
2.  İçinde **özellik sayfaları**, tıklayın **izleme**.  
  
3.  Komut türü **komut satırı** metin kutusu altında **işaretleme öncesi olaylar**.  
  
    > [!NOTE]
    >  Üç nokta düğmesine tıklayabilirsiniz **(...)**  bitişik olan **komut satırı** kutusunu göz atın ve uygun .exe, .cmd veya .bat dosyasını seçin.  
  
4.  **Tamam**'ı tıklatın.  
  
     Komut çalışmasını kaldırmadan devre dışı bırakmak için seçin **İzleme'den Dışla** onay kutusu. Derleyici veya bağlayıcı ayarları değiştirmek için proje özellik sayfalarını kullanın.  
  
### <a name="to-specify-post-instrument-commands"></a>Son izleme komutları belirtmek için  
  
1.  Aşağıdaki adımlardan birini uygulayın:  
  
    -   Son izleme komutları tüm ikili dosyaları için bir performans oturumu belirtmek için performans oturumu düğümünde seçin **performans Gezgini**ve ardından sağ tıklayıp **özellikleri**.  
  
    -   Son izleme komutları için belirli bir ikili belirtmek için ikili adına sağ tıklayın **hedefleri** performans oturumu tıklayın ve ardından listesi **özellikleri**.  
  
2.  İçinde **özellik sayfaları**, tıklayın **izleme**.  
  
3.  Komut türü **komut satırı** metin kutusu altında **son izleme olayları**.  
  
    > [!NOTE]
    >  Üç nokta düğmesine tıklayabilirsiniz **(...)**  bitişik olan **komut satırı** kutusunu göz atın ve uygun .exe, .cmd veya .bat dosyasını seçin.  
  
4.  **Tamam**'ı tıklatın.  
  
     Komut çalışmasını kaldırmadan devre dışı bırakmak için seçin **İzleme'den Dışla** onay kutusu. Derleyici veya bağlayıcı ayarları değiştirmek için proje özellik sayfalarını kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Oturumlarını Yapılandırma](../profiling/configuring-performance-sessions.md)



