---
title: Windows 8 ve Windows Server 2012 uygulamalarında performans araçları | Microsoft Docs
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 404a8a3f40d5d84d60fe4822fb692e4f48a57503
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220813"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Windows 8 ve Windows Server 2012 uygulamalarında performans araçları

Windows 8 ve Windows Server 2012'de başlayarak Gelişmiş güvenlik özelliklerine şekilde Visual Studio performans araçları de yapılan önemli değişiklikler bu platformlarda veri toplama gerekli. UWP uygulamaları, ayrıca yeni toplama teknikleri gerektirir. Bu konuda, değişikliklerin platformlarında Windows 8 ve Windows Server 2012 sürümünden itibaren performans araçları açıklanmaktadır.

> [!NOTE]
> Windows (Windows 7, Windows Server 2008 R2) desteklenen diğer sürümleri için performans araçları değişmedi.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Visual Studio IDE içinden UWP uygulamaları veri topla

JavaScript ve HTML 5 yazılmış bir UWP uygulaması profil, JavaScript kodu için ölçümlü izleme verilerini toplayın. Bir UWP uygulamasında ya da Visual C++, Visual C# veya Visual Basic içinde yazılan bileşen profil, yerel ve yönetilen kod için örnekleme verileri toplayın. Uygulamanızı yerel olarak veya bir uzak makinede profil oluşturabilirsiniz.

Bu profil özellikleri ve seçenekleri UWP uygulamalarının profili oluşturulurken desteklenmez:

- JavaScript uygulamaları örnekleme metodu kullanılarak profili oluşturma.
- Araçlar yöntemini kullanarak, yönetilen ve yerel kod profil oluşturma.
- Eşzamanlılık profili oluşturma
- .NET bellek profili oluşturma
- Katman etkileşimli profil oluşturma (TIP)
- Örnekleme seçenekleri, örnekleme olay ve zamanlama aralığı ayarını veya ek performans sayacı verilerini toplama gibi.
- Performans ve windows sayaç verileri toplama veya ek komut satırı seçenekleri belirtme gibi izleme seçenekleri.

UWP uygulamaları profil oluşturma hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Yerel makinede UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-the-local-machine.md)
- [Uzak makinede UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [Araçlar profil oluşturmaya ilk bakış](profiling-feature-tour.md)
- [JavaScript bellek](../profiling/javascript-memory.md)
- [Profili Visual C++, Visual C# ve Visual Basic kodu yerel makinede UWP uygulamaları](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)
- [UWP uygulamalarında uzak bir cihazda profili Visual C++, Visual C# ve Visual Basic kodu](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)
- [UWP uygulamalarında Visual C++, Visual C# ve Visual Basic kodu için performans verilerini çözümleme](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Visual Studio IDE içinden masaüstünde Windows 8 veya Windows Server 2012'de çalışan uygulamaları üzerinde veri toplamayı

Araçlar yöntemini kullanarak profil oluşturma Windows 8 için değiştirilmemiştir.

Katman etkileşimli profil oluşturma (TIP) örnekleme metodu kullanılarak desteklenmiyor.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Visual Studio IDE'den örnekleme kullanarak Windows Server 2012 veya Windows 8 masaüstünde çalışan uygulamalar üzerinde veri toplayın

Bu profil özellikleri ve seçenekleri Masaüstü uygulamalarını Windows 8 veya Windows Server 2012 uygulamalar örnekleme metodu kullanılarak profili oluşturulurken desteklenmez:

- Katman etkileşim profili oluşturma (TIP). İpucu verileri toplama araçları kullanılarak desteklenir.

- Örnekleme olay ve zamanlama aralığı ayarını veya ek performans sayacı verilerini toplama gibi örnekleme Seçenekleri'ni kullanın.

## <a name="profile-from-the-command-line"></a>Komut satırından profil

İki komut satırı araçları, Visual Studio yüklemesini olmayan cihazlar da dahil olmak üzere Windows 8 ve Windows Server 2012 cihazlarında, profil oluşturma verilerini toplamak için kullanın:

|Araç adı|Açıklama|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|UWP uygulamaları profil oluşturma verilerini toplar ve Masaüstü uygulamalarını Windows 8 ve Windows Server 2012 uygulamaları örnek profil oluşturma verileri toplar...|
|[VSPerfCmd](../profiling/vsperfcmd.md)|İzleme, eşzamanlılık ve katman etkileşimli profil oluşturma Windows 8 Masaüstü veya Windows Server 2012 üzerinde çalışan uygulamaların verileri toplar. Tüm profil oluşturma veri türlerini Windows'ın önceki sürümlerinden toplar.|

Her iki araçları, yerel bilgisayarda kullanım için Visual Studio ile yüklenir.

Profil için cihazlarında uygulamalar Visual Studio yüklü olmayan aşağıdakilerden birini yapın:

- Visual Studio için Uzak Araçlar'ın bir parçası olarak araçları indirin [MSDN web sitesinde](http://go.microsoft.com/fwlink/?LinkID=219549).

- Kopyalama ve bilgisayarınızda Visual Studio bağımsız profil oluşturucuyu araçları yükleme programını çalıştırın. Yükleme programları bulunan *%VSInstallDir%\Team Araçlar\Performans Tools\Setups* klasör. Uzak bilgisayarın işletim sistemi (x86/x64) için Kurulum programı seçin.

> [!NOTE]
> İpucu profil oluşturma verilerini toplamak için uzak bilgisayardaki Visual Studio makinenizden bağımsız profil oluşturucuyu yüklemeniz gerekir.

Bu profil özellikleri ve seçenekleri komut satırından Windows 8 ve Windows Server 2012 uygulamalarında profil oluşturma sırasında desteklenmez:

- Örnekleme modu ile kullanarak Windows 8 ve Windows Server 2012 web uygulamalarından veri toplamayı [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).

- VsPerfCmd.exe'ı kullanarak örnekleme verileri toplama.

- Örnekleme olay ve zamanlama aralığı ayarını veya ek performans sayacı verilerini toplama gibi örnekleme Seçenekleri'ni kullanın.

## <a name="collect-tier-interaction-tip-data"></a>Katman etkileşim (TIP) verileri toplama

Katman etkileşim profili oluşturma, ADO.NET Hizmetleri aracılığıyla veritabanları ile iletişim kuran çok katmanlı uygulamaların işlevlerini yürütme sürelerini hakkında ek bilgi sağlar. Verileri yalnızca zaman uyumlu işlev çağrıları için toplanır.

**Visual Studio sürümleri**

Katman etkileşimli profil oluşturma verileri, herhangi bir Visual Studio sürümünü kullanarak toplanabilir. Ancak, yalnızca Visual Studio Enterprise'da katman etkileşimli profil oluşturma veri görüntülenebilir.

**Windows 8 ve Windows Server 2012**

1. Windows 8 Masaüstü veya Windows Server 2012 üzerinde çalışan uygulamaların katman etkileşim verileri toplamak için izleme metodunu kullanmanız gerekir.

2. UWP uygulamaları için katman etkileşim verileri toplanamıyor.

3. Desteklenen diğer Windows sürümünde tüm profil oluşturma yöntemlerini katman etkileşim verileri içerebilir.

**Performans Sihirbazı ve performans Gezgini**

Bir profil oluşturma yürütmesine katman etkileşim verileri toplama seçeneği performans Gezgini'nden eklemeniz gerekir. Ayrıca proje, yürütülebilir dosya veya Web performans Gezgini hedef düğüme eklemeniz gerekir. Bkz: [katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md).

**Uzak makinede ipucu verileri toplama**

Uzak makinede katman etkileşim verileri toplamak için kopyalamanız gereken **vs\_profil oluşturucu\_**_\<Platform >_ **\_**  _\<Dil >_**.exe** dosya *%VSInstallDir%\Team Araçlar\Performans Tools\Setups* bir Visual Studio makineyi klasörü Uzak bilgisayar ve yükleyin. Profil oluşturma araçları kullanamazsınız [uzaktan hata ayıklama](../debugger/remote-debugging.md) paketini indirin.

Kullanabileceğiniz [VSPerfCmd](../profiling/vsperfcmd.md) veya [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) profil oluşturma verileri toplamak için.

**İpucu raporları**

Katman etkileşim verileri yalnızca Visual Studio Enterprise'da görüntülenebilir. Dosya tabanlı katman etkileşim raporlar aracılığıyla [VSPerfReport](../profiling/vsperfreport.md) kullanılabilir değil.

## <a name="see-also"></a>Ayrıca bkz.

[Performans Gezgini](../profiling/performance-explorer.md)
[performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
[komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)