---
title: 'Nasıl yapılır: ASP.NET işleminin adını bulma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ad3bea47bcde0da87bd185fac132c95f26ce4b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793249"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Nasıl Yapılır: ASP.NET İşleminin Adını Bulma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çalışan bir eklemek için [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulama sahip adını bilmek [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] işlemi:  
  
- IIS 6.0 veya IIS 7.0 çalıştırıyorsanız, w3wp.exe addır.  
  
- IIS önceki bir sürümünü çalıştırıyorsanız, aspnet_wp.exe addır.  
  
  Kullanılarak oluşturulan uygulamalar için [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] veya sonraki sürümler [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kod dosya sisteminde bulunan ve test sunucu WebDev.WebServer.exe altında çalıştırın. Bu durumda, yerine WebDev.WebServer.exe iliştirmeniz gerekir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] işlem. Bu senaryo, yalnızca yerel hata ayıklama için geçerlidir.  
  
  İşlem içi çalıştırırken eski ASP uygulamalarını IIS işlemi inetinfo.exe içinde çalıştırın.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Proje kodu dosya sisteminde veya IIS bulunduğunu belirlemek için  
  
1.  Visual Studio'da açın **Çözüm Gezgini** zaten açık değilse.  
  
2.  Uygulamanın adını içeren üst düğümü seçin.  
  
3.  Varsa **özellikleri** pencere başlığını içeren bir dosya yolu, dosya sisteminde uygulama kodu bulunur.  
  
     Aksi takdirde, **özellikleri** pencere başlığı Web sitesi adını içerir.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Uygulamanın çalıştırıldığı IIS sürümü belirlemek için  
  
1.  Bulma **Yönetimsel Araçlar** ve çalıştırın. İşletim sistemine bağlı olarak bu simge içinde olabilir **Denetim Masası**, ya da'a tıkladığınızda görüntülenen menü girdisi **Başlat**.  
  
     Windows XP'de **Denetim Masası** kategori görünümünde veya Klasik olabilir. Kategori görünümünde, tıklamanız gerekmiyor. **Klasik görünümüne geç** veya **performans ve Bakım** görmek için **Yönetimsel Araçlar** simgesi.  
  
2.  Gelen **Yönetimsel Araçlar**, Internet Information Services'ı çalıştırın. Bir MMC iletişim kutusu görüntülenir.  
  
3.  Sol bölmede listelenen birden fazla bilgisayar varsa, uygulama kodu yer aldığı bir tane seçin.  
  
4.  IIS sürümü bulunduğu **sürüm** sağ bölmenin sütun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama Web uygulamaları önkoşulları](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)   
 [ASP.NET'de hata ayıklamaya hazırlanıyor](../debugger/preparing-to-debug-aspnet.md)   
 [Web Uygulamalarında ve Betikte Hata Ayıklama](../debugger/debugging-web-applications-and-script.md)



