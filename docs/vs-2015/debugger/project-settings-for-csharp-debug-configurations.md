---
title: Proje ayarları C# hata ayıklama yapılandırmaları için | Microsoft Docs
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
- debug configurations, C#
- debugging [J#], debugger settings
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
- debug configurations, J#
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07da36adc1615217315d5ebb23f8ef62db59f5c7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721172"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# Hata Ayıklama Yapılandırması Proje Ayarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir C# hata ayıklama yapılandırması proje ayarları değiştirebilirsiniz **özellik sayfaları** anlatıldığı gibi penceresinde [hata ayıklama ve yayın yapılandırmaları](../debugger/how-to-set-debug-and-release-configurations.md). Aşağıdaki tablolarda, hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir **özellik sayfaları** penceresi.  
  
> [!WARNING]
>  Bu konu, Windows Store uygulamaları için geçerli değil. Bkz: [(VB, C#, C++ ve XAML) bir hata ayıklama oturumu başlatın](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Hata ayıklama sekmesi  
  
|**Ayarı**|**Açıklama**|  
|-----------------|---------------------|  
|**Yapılandırma**|Uygulama derlemek için modu ayarlar. Arasından seçim **etkin (hata ayıklama)**, **hata ayıklama**, **yayın**, **yapılandırmalarında**.|  
|**Başlatma eylemi**|Bu grubu denetimleri, hata ayıklama menüsünden Başlangıç meydana gelir eylemi belirtir.<br /><br /> -   **Proje başlangıç** varsayılandır ve hata ayıklama için başlangıç projesi başlatır. Daha fazla bilgi için [başlangıç projesi seçme](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Harici program Başlat** başlatmak ve olmayan bir programa ekledikten sağlayan parçası olan bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje. Daha fazla bilgi için [çalışan programa ekleme](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **URL'de tarayıcı başlatmak** bir Web uygulaması ayıklamanızı sağlar.|  
|**Komut satırı bağımsız değişkenleri**|Ayıklanacak programın komut satırı bağımsız değişkenlerini belirtir. Komut başlangıç dış program içinde belirtilen program adı addır. Başlatma eylemi için başlangıç URL'si olarak ayarlanırsa, komut satırı bağımsız değişkenleri belirtilemez.|  
|**Çalışma dizini**|Ayıklanan programın çalışma dizini belirtir. İçinde [!INCLUDE[csprcs](../includes/csprcs-md.md)], çalışma dizini uygulama \bin\debug varsayılan olarak başlatıldığında dizindir.|  
|**Uzak makine kullanma**|Hata ayıklama amacıyla nerede uygulamanın çalışacağı uzak bir makine adı veya bir [Msvsmon sunucu adı](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Uzak makinede EXE konumunu, yapılandırma özellikleri klasöründe, yapı kategori çıkış yolu özelliği tarafından belirtilir. Konum, uzak makinede paylaşılabilir bir dizin olmalıdır.|  
|**Yönetilmeyen kodun hata ayıklamasını etkinleştir**|Yerel (yönetilmeyen) Win32 koddaki çağrıları yönetilen uygulamanızın hatalarını ayıklamanızı sağlar.|  
|**SQL Server hata ayıklamayı etkinleştir**|SQL Server veritabanı nesnelerini hata ayıklamasını sağlar.|  
  
##  <a name="BKMK_Build_tab"></a> Derleme sekmesi  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Koşullu derleme simgeleri:**|Hata ayıklama ve izleme sabitler burada tanımlanır.<br /><br /> Bu sabitler koşullu derlenmesini etkinleştirmek [hata ayıklama sınıfı](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) ve [izleme sınıfı](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Tanımlanan Bu sabitler ile hata ayıklama ve izleme sınıfı yöntemleri oluşturmak için çıkış [çıkış penceresine](../ide/reference/output-window.md). Bu sabitler olmadan hata ayıklama ve izleme sınıfı yöntemleri derlenmemiş ve hiçbir çıktı oluşturulur.<br /><br /> -Debug normalde bir program hata ayıklama sürümünde tanımlanır ve sürümde tanımlanmamış.<br />-İzleme, hem hata ayıklama ve yayın sürümleri normal olarak tanımlanır.|  
|**Kodu En İyileştir**|Yalnızca en iyi duruma getirilmiş kodda görüntülenen bir hatayı Bul sürece, bu ayar hata ayıklama sürümünde devre dışı bırakmanız gerekir. En iyi duruma getirilmiş kodu doğrudan deyimlerinde kaynak windows için yönergeler karşılık gelmediğinden hata ayıklamak zordur.|  
|**Çıkış yolu:**|Genellikle bin\Debug hata ayıklama için ayarlayın.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)



