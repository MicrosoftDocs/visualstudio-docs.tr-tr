---
title: .NET Core projeleri için veritabanı kullanımını analiz etme | Microsoft Docs
description: Uygulamanızın veritabanı sorgularını kaydetmek için veritabanı aracını kullanın, ardından performansı artırmanın yollarını bulmak için bunları çözümleyin.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- database, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: a8518e3f43bec3a9d5f696a07613dee84829dbc2
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205469"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>Veritabanı aracını kullanarak veritabanı performansını çözümleme

Tanılama oturumu sırasında uygulamanızın yaptığı veritabanı sorgularını kaydetmek için veritabanı aracını kullanın. Daha sonra, uygulamanızın performansını iyileştirecek yerleri bulmak üzere ayrı sorgular hakkındaki bilgileri çözümleyebilirsiniz.

> [!NOTE]
> Veritabanı aracı, [ADO.net]( https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) veya [Entity Framework Core](/ef/core/)kullanarak Visual Studio 2019 sürüm 16,3 veya üstünü ve Windows üzerinde .NET Core projesi gerektirir.

## <a name="setup"></a>Kurulum

1. Visual Studio 'da performans profil oluşturucuyu açmak için **alt + f2** ' yi seçin.

1. **Veritabanı** onay kutusunu seçin.

   ![Veritabanı aracı seçildi](./media/db-launch.png "Veritabanı aracı seçildi")

   > [!NOTE]
   > Araç seçilebilir olarak yoksa, bazı araçların tek başına çalıştırılması gerektiğinden, diğer her aracın onay kutusunu temizleyin. Araçları birlikte çalıştırma hakkında daha fazla bilgi için bkz. [komut satırından profil oluşturma araçlarını kullanma](../profiling/using-the-profiling-tools-from-the-command-line.md).
   >
   > Araç hala kullanılamıyorsa, projenizin önceki gereksinimleri karşıladığından emin olun. En doğru verileri yakalamak için projenizin yayın modunda olduğundan emin olun.

1. Aracı çalıştırmak için **Başlat** düğmesini seçin.

1. Araç çalışmaya başladıktan sonra, uygulamanızda profili eklemek istediğiniz senaryoya gidin. Ardından, **toplamayı durdur** ' u seçin veya verilerinizi görmek için uygulamanızı kapatın.

1. Koleksiyon durdurulduktan sonra, profil oluşturma oturumunuz sırasında çalıştırılan sorguların bir tablosunu görürsünüz.

   ![Veritabanı aracı durdu](./media/db-after.png "Veritabanı aracı durdu")

Sorgular kronolojik olarak düzenlenir, ancak bunları sütunlardan herhangi birine göre de sıralayabilirsiniz. Sütun başlıklarına sağ tıklayarak daha fazla sütun gösterebilirsiniz. **Süre** sütununun belirlenmesi en uzun olan sorguları en kısasına göre sıralar.

Araştırmak istediğiniz bir sorgu bulduktan sonra sorguya sağ tıklayın. Sonra bu sorgudan sorumlu kodu görmek için **kaynak dosyasına git** ' i seçin.

![Kaynak dosyasına git seçili](./media/db-gotosource.png "Kaynak dosyasına git seçili")

Grafik üzerinde bir zaman aralığı seçerseniz, sorgu tablosu yalnızca o zaman aralığında gerçekleşen sorguları gösterir. Bu davranış, özellikle de [CPU kullanımı aracını](./cpu-usage.md?view=vs-2019&preserve-view=true)çalıştırdığınızda yararlı olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturucu ayarlarını iyileştirme](../profiling/optimize-profiler-settings.md)