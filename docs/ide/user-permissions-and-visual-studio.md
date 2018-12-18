---
title: Yönetici olarak çalıştır
ms.date: 06/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b48a9cae19faa592eecb2f02af67e9ad8b2ca9b3
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348318"
---
# <a name="user-permissions-and-visual-studio"></a>Kullanıcı izinleri ve Visual Studio

Güvenlik nedenleriyle, Visual Studio normal kullanıcı mümkün olduğunca olarak çalıştırmanız gerekir.

> [!WARNING]
> Ayrıca güvenilir bir kişi ya da güvenilir bir konumdan gelmeyen herhangi bir Visual Studio çözümüyle derleme, başlatma veya hata ayıklama yapmadığınızdan emin olmalısınız.

Normal bir kullanıcı olarak Visual Studio IDE içinde hemen her şeyi yapabilirsiniz. Aşağıdaki görevleri tamamlamak için yönetici izinlerine ihtiyacınız vardır:

|Alan|Görev|Daha fazla bilgi için|
|----------|----------| - |
|Yükleme|Visual Studio'yu yükleyin.|[Visual Studio'yu yükleyin](../install/install-visual-studio.md)|
||Yüklemek, güncelleştirmek veya yerel Yardım içeriğini kaldırın.|[Yerel Yardım içeriği yükleme ve yönetme](../help-viewer/install-manage-local-content.md)|
|Araç Kutusu|Klasik COM denetimleri ekleme **araç kutusu**.|[Araç Kutusu](../ide/reference/toolbox.md)|
|Oluşturma|Bir bileşeni kayıt ettiren oluşturma sonrası olayları kullanın.|[Özel derleme adımları anlayın ve derleme olayları](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||C++ projeleri oluşturduğunuzda kayıt adımı içerir.||
|Hata Ayıklama|Yükseltilmiş izinlerle çalışan uygulamalarda hata ayıklama.|[Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)|
||Hesap, ASP.NET Web siteleri gibi farklı bir kullanıcı altında çalışan uygulamalarda hata ayıklama.|[ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)|
||XAML tarayıcı uygulamaları (XBAP) için bölgede hata ayıklama|[WPF Konağı (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||İçin Microsoft Azure bulut hizmeti projelerinde hata ayıklamak için öykünücü kullanma.|[Bir bulut hizmetinde Visual Studio'da hata ayıklama](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Uzaktan hata ayıklama için bir güvenlik duvarını yapılandırın.|[Uzaktan hata ayıklama](../debugger/remote-debugging.md)|
|Performans araçları|Uygulama profili oluşturma.|[Performans profili oluşturma Başlangıç Kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)|
|Dağıtım|Internet Information Services (IIS) için yerel bir bilgisayardaki bir web uygulaması dağıtın.|[Visual Studio kullanarak ASP.NET web uygulaması dağıtma](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Visual Studio'yu yönetici olarak çalıştırın

Visual Studio'yu yönetici olarak çalıştırmanız gerekir IDE açmak için şu adımları izleyin:

> [!NOTE]
> Bu yönergeler, Windows 10 için içindir. Bunlar diğer Windows sürümleri için benzerdir.

1. Açık **Başlat** menü ve Visual Studio 2017 gidin.

1. Sağ tıklayın veya bağlam menüsünde **Visual Studio 2017**seçin **daha fazla** > **yönetici olarak çalıştır**.

   Visual Studio başladığında **(Yönetici)** başlık çubuğundaki ürün adının görünür.

Uygulama kısayolunu her zaman yönetim izinleriyle çalıştırmak için de değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Taşıma, geçirme ve Visual Studio projelerini yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Visual Studio'yu yükleyin](../install/install-visual-studio.md)