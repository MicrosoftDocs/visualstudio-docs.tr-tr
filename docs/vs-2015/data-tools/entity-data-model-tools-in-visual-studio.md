---
title: Varlık veri modeli araçları
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 942678000cf633caeb0a55d8ca41dc092f1e484f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53047651"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Varlık veri modeli Visual Studio Araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Entity Framework, .NET geliştiricilerinin etki alanına özel nesneler kullanarak ilişkisel verilerle çalışmak bir nesne ilişkisel eşleme teknolojisidir. Genellikle geliştiricilerin yazmak zorunda olduğu çoğu veri erişim koduna yönelik gereksinimi ortadan kaldırır. Varlık, yeni .NET uygulamaları için teknoloji modelleme önerilen nesne ilişkisel eşleme (ORM) çerçevedir.

 Mart 2016 itibariyle en son yayımlanmış sürümüdür [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) yayın öncesi sürümde olduğunu.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Araçlar oluşturmanıza yardımcı olmak için tasarlanmıştır [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] uygulamalar. Tüm belgeler için [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] araçları, burada: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 İle [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] oluşturabileceğiniz araçları, bir *kavramsal model* mevcut bir veritabanı ve grafik görselleştirin ve kavramsal model düzenleyin. Veya bir kavramsal model ilk grafik oluşturun ve ardından modelinizin destekleyen bir veritabanı oluşturun. Her iki durumda da temel alınan veritabanı değişiklikleri ve otomatik olarak uygulamanız için nesne katmanı kodu oluşturma modeliniz otomatik olarak güncelleştirebilirsiniz. Veritabanı oluşturma ve nesne katmanı kodu oluşturma özelleştirilebilir.

 Varlık veri modeli araçları Visual Studio 2015'te oluşturan özel araçlar şunlardır:

- Kullanabileceğiniz [!INCLUDE[vstecado](../includes/vstecado-md.md)]  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tasarımcısı** (**varlık Tasarımcısı**) görsel olarak oluşturma ve varlıklar, ilişkilendirmeleri, eşlemeler ve devralma ilişkilerinin değiştirin. **Varlık Tasarımcısı** ayrıca oluşturur [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nesne katmanı kodu.

- Kullanabileceğiniz  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Sihirbazı** varolan bir veritabanından kavramsal model oluşturmak ve veritabanı bağlantı bilgilerini uygulamanıza ekleyin.

- Kullanabileceğiniz **Veritabanı Oluşturma Sihirbazı'nı** ilk kavramsal model oluşturun ve ardından modelini destekleyen bir veritabanı oluşturun.

- Kullanabileceğiniz **güncelleştirme modeli Sihirbazı** temel alınan veritabanına değişiklikler yapıldığında, kavramsal model, depolama model ve eşleme güncelleştirilecek.

  > [!NOTE]
  >  Visual Studio 2010 ile başlayarak [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] araçları desteklemez [!INCLUDE[ss2k](../includes/ss2k-md.md)].

  Araçlar oluşturmak veya bir .edmx dosyasını değiştirin. Bu dosya, bunları arasındaki eşlemeleri kavramsal model ve depolama modeli açıklayan bilgileri içerir. Daha fazla bilgi için [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework güç araçları varlık veri modeli kullanan uygulamalar oluşturmanıza yardımcı olur. Araçları bir kavramsal model oluşturmak, mevcut bir model doğrulama, kavramsal model temelinde nesne sınıfları içeren kaynak kodu dosyaları üretmek ve modeli oluşturur görünümleri içeren kaynak kodu dosyaları üretir. Ayrıntılı bilgi için bkz. [Pre-Generated eşleme görünümleri](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Nasıl kullanılacağını açıklar [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] araçları, hangi [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] uygulamalar oluşturmasını sağlar.|
|[Varlık Veri Modeli](http://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Üzerinde oluşturulan uygulamaları tarafından kullanılan verilerle çalışmaya yönelik bilgi ve bağlantılar sağlanmıştır [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|
|[Tam .NET (konsol, WinForms, WPF, vb.) kullanmaya başlama](https://docs.efproject.net/en/latest/platforms/full-dotnet/getting-started.html)|Entity Framework 7 kullanan .NET Masaüstü uygulamaları oluşturma konusunda eğitimler sağlar.|
|[ASP.NET 5 uygulaması için yeni veritabanı](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Entity Framework 7 kullanarak yeni bir ASP.NET 5 uygulaması oluşturmayı açıklar.|

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
