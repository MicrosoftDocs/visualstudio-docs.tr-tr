---
title: Proje ayarları için bir C# yapılandırma hatalarını ayıklama | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6de7bfd547516b227063c0d3143b508bcbd9ddfd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059278"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# hata ayıklama yapılandırması proje ayarları

Değiştirebileceğiniz C# proje hata ayıklama ayarlarında [hata ayıklama sekmesini](#debug-tab) ve [derleme sekmesi](#build-tab) proje özellik sayfaları. 

Özellik Sayfaları'ni açmak için projeyi seçin **Çözüm Gezgini** seçip **özellikleri** simgesini veya projeye sağ tıklayıp seçin **özellikleri**.

Daha fazla bilgi için [hata ayıklama ve dağıtım yapılandırmalarını](how-to-set-debug-and-release-configurations.md). 

>[!IMPORTANT]
>Bu ayarlar, .NET Core, ASP.NET veya UWP uygulamaları için geçerli değildir. UWP uygulamaları için hata ayıklama ayarları yapılandırmak için bkz [bir UWP uygulaması için bir hata ayıklama oturumu başlatma](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
## <a name="debug-tab"></a>Hata ayıklama sekmesi  
  
|Ayar|Açıklama|
|-------------------------------------| - |
| **Yapılandırma** | Uygulama oluşturmaya yönelik modunu ayarlar. Seçin **etkin (hata ayıklama)**, **hata ayıklama**, **yayın**, veya **yapılandırmalarında** açılır listeden. |
| **Başlatma eylemi** | Seçtiğinizde bir eylem belirtir **Başlat** hata ayıklama yapılandırması.<br />- **Proje başlangıç** varsayılandır ve hata ayıklama için başlangıç projesi başlatır. Daha fazla bilgi için [başlangıç projesi seçme](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Harici program Başlat** başlar ve olmayan bir uygulama ekler parçası olan bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proje. Daha fazla bilgi için [ekleme hata ayıklayıcısı ile çalıştırma işlemleri](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Tarayıcı URL'si ile başlayın** bir web uygulamasında hata ayıklama olanak tanır. |
| **Başlatma seçenekleri** > **komut satırı bağımsız değişkenleri** | Hatası ayıklanmakta olan uygulamayı komut satırı bağımsız değişkenlerini belirtir. Komut adı belirtilen uygulamanızın adıdır **harici program Başlat**. |
| **Başlatma seçenekleri** > **çalışma dizini** | Hatası ayıklanmakta olan uygulamayı çalışma dizini belirtir. İçinde C#, çalışma dizini *\bin\debug* varsayılan olarak.
| **Başlatma seçenekleri** > **uzak makine**|Uzaktan hata ayıklama için bu seçeneği belirleyin ve uzak hata ayıklama hedefi adını girin veya bir [Msvsmon sunucu adı](../debugger/remote-debugging.md). <br />Uygulama uzak makinede konumunu tarafından belirtilen **çıkış yolu** özelliği **derleme** sekmesi. Konum, uzak makinede paylaşılabilir bir dizin olmalıdır. 
| **Hata ayıklayıcısı altyapısı** > **yönetilmeyen kodun hata ayıklamasını etkinleştir** | Yerel (yönetilmeyen) Win32 koddaki çağrıları yönetilen bir uygulamadan hata ayıklamasına. |
| **Hata ayıklayıcısı altyapısı** > **etkinleştirme SQL Server hata ayıklama** | SQL Server veritabanı nesnelerini hata ayıklamasına. |
  
## <a name="build-tab"></a>Derleme sekmesi  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Genel** > **koşullu derleme simgeleri**|Hata ayıklama ve izleme sabitleri seçtiyseniz tanımlayın.<br /><br /> Bu sabitler koşullu derlenmesini etkinleştirmek [hata ayıklama sınıfı](/dotnet/api/system.diagnostics.debug) ve [izleme sınıfı](/dotnet/api/system.diagnostics.trace). Tanımlanan Bu sabitler ile hata ayıklama ve izleme sınıfı yöntemleri oluşturmak için çıkış [çıkış penceresine](../ide/reference/output-window.md). Bu sabitler olmadan hata ayıklama ve izleme sınıfı yöntemleri derlenmemiş ve hiçbir çıktı oluşturulur.<br /><br />Genellikle, hata ayıklama yapı hata ayıklama sürümünde tanımlanır ve sürümde tanımlanmamış. İzleme hata ayıklama ve yayın sürümleri tanımlanır.|  
|**Genel** > **kodu En İyileştir**|Yalnızca en iyi duruma getirilmiş kodda bir hata görünür değilse bu hata ayıklama yapıları için seçilmeyen ayarı bırakın. Doğrudan kaynak kodundaki deyimleri için yönergeler karşılık gelmediğinden en iyi duruma getirilmiş kod hatalarını ayıklamak için zordur.|  
|**Çıkış** > **çıkış yolu**|Genellikle kümesine *bin\Debug* hata ayıklama.|
|**Gelişmiş** düğmesi|Gelişmiş hata ayıklama seçenekleri hakkında daha fazla bilgi için bkz: [Gelişmiş derleme Ayarları iletişim kutusu (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Sembol taşınabilir biçimi (*.pdb*) dosyaları olan .NET Core uygulamaları için yeni bir platformlar arası biçimi. 
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)