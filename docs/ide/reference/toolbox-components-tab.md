---
title: Araç Kutusu, Bileşenler Sekmesi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a6365ebc9c44d5d453e04a3579d1b87d766413f
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924323"
---
# <a name="toolbox-components-tab"></a>Araç kutusu, bileşenler sekmesi

Windows Forms için Visual Basic ve C# tasarımcılarınızı ekleyebileceğiniz bileşenlerini gösterir. Visual Studio ile gibi dahil .NET Framework bileşenlerini yanı sıra <xref:System.Messaging.MessageQueue> ve <xref:System.Diagnostics.EventLog> bileşenleri ekleyebilir, kendi veya üçüncü taraf bileşenleri için bu sekme.

Bu sekme görüntülemek için bir Windows Form Tasarımcısı'nı açın. Seçin **görünümü** > **araç kutusu**. İçinde **araç kutusu**seçin **bileşenleri** sekmesi.

## <a name="components"></a>Bileşenler

**BackgroundWorker**

Oluşturur bir <xref:System.ComponentModel.BackgroundWorker> bileşen örneği, bir işlem ayrı, özel bir iş parçacığı üzerinde çalıştırabilirsiniz. Daha fazla bilgi için [BackgroundWorker bileşeni](/dotnet/framework/winforms/controls/backgroundworker-component).

**DirectoryEntry**

Oluşturur bir <xref:System.DirectoryServices.DirectoryEntry> bir düğüm veya Active Directory hiyerarşisinde nesne kapsüller ve Active Directory hizmet sağlayıcıları ile etkileşim kurmak için kullanılan bileşen örneği.

**DirectorySearcher**

Oluşturur bir <xref:System.DirectoryServices.DirectorySearcher> gerçekleştirmek için kullanabileceğiniz bir bileşen örneğinin Active Directory karşı sorgular.

**ErrorProvider**

Oluşturur bir <xref:System.Windows.Forms.ErrorProvider> son kullanıcıya bir form denetiminde kendisiyle ilişkili bir hata olduğunu gösteren bileşen örneği. Daha fazla bilgi için [ErrorProvider bileşeni](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Oluşturur bir <xref:System.Diagnostics.EventLog> bileşen örneğinin sistem ve özel olay günlükleri, olaylar bir günlüğe yazma ve günlük verileri okuma gibi etkileşim kurmak için kullanabilirsiniz.

**FileSystemWatcher**

Oluşturur bir <xref:System.IO.FileSystemWatcher> herhangi bir dizin veya dosya erişim sahibi izlemek için kullanabileceğiniz bileşen örneği değiştirir.

**HelpProvider**

Oluşturur bir <xref:System.Windows.Forms.HelpProvider> bileşen örneği açılır veya çevrimiçi Yardım denetimleri sağlar. Daha fazla bilgi için [HelpProvider bileşeni](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**ImageList**

Oluşturur bir <xref:System.Windows.Forms.ImageList> koleksiyonunu yönetmek için yöntemler sağlar bileşen örneğinin <xref:System.Drawing.Image> nesneleri. Daha fazla bilgi için [ImageList bileşeni](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Oluşturur bir <xref:System.Messaging.MessageQueue> gelen iletileri okumak ve kuyruklara ileti yazılıyor, işlemleri ve kuyruk yönetim görevlerini gerçekleştirme dahil, ileti kuyrukları ile etkileşim kurmak için kullanabileceğiniz bileşen örneği.

**PerformanceCounter**

Oluşturur bir <xref:System.Diagnostics.PerformanceCounter> sayaç verilerinin hesaplamaları yeni kategori ve örnekleri oluşturma ve sayaçlarından okumanızı dahil olmak üzere Windows performans sayaçları ile etkileşimde bulunmak için kullanabileceğiniz bileşen örneği.

**İşlem**

Oluşturur bir <xref:System.Diagnostics.Process> bileşen örneğinin durdurun, başlatın ve sisteminizdeki süreçleri ile ilişkili verileri işlemek için kullanabilirsiniz.

**Çevirmek için SerialPort**

Oluşturur bir <xref:System.IO.Ports.SerialPort> bileşen örneği ve olay odaklı, zaman uyumlu g/ç, erişim için PIN ve kesme durumları ve seri sürücü özelliklerine erişim sağlar.

**ServiceController**

Oluşturur bir <xref:System.ServiceProcess.ServiceController> bileşen örneği başlatma, durdurma Hizmetleri ve komutlar göndererek dahil olmak üzere var olan hizmetleri yönetmek için kullanabilirsiniz.

**Timer**

Oluşturur bir <xref:System.Windows.Forms.Timer> bileşen örneği, Windows tabanlı uygulamalar için zamana bağlı işlevselliği eklemek için kullanabilirsiniz. Daha fazla bilgi için [süreölçer bileşeni](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> De mevcuttur sistem tabanlı <xref:System.Timers.Timer> için ekleyebileceğiniz **araç kutusu** bu <xref:System.Timers.Timer> sunucu uygulamaları ve Windows Forms için optimize edilmiştir <xref:System.Windows.Forms.Timer> Windows formlarında kullanmak için uygundur.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'da kullanılacak denetimler](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Araç kutusu öğelerini, WPF bileşenlerini seçme](choose-toolbox-items-wpf-components.md)
- [Araç Kutusu](../../ide/reference/toolbox.md)