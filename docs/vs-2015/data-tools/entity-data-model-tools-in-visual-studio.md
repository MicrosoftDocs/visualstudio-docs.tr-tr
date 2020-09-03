---
title: Varlık Veri Modeli araçları
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d663b86603145f8a665f189e5abfbfa2b0b360ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672390"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Visual Studio'daki Varlık Veri Modeli Araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework, .NET geliştiricilerin, etki alanına özgü nesneleri kullanarak ilişkisel verilerle çalışmasını sağlayan, nesne ilişkisel bir eşleme teknolojisidir. Geliştiricilerin genellikle yazması gereken çoğu veri erişim kodu gereksinimini ortadan kaldırır. Entity Framework, yeni .NET uygulamaları için önerilen nesne ilişkisel eşleme (ORM) modelleme teknolojisidir.

 2016 Mart itibariyle, en güncel yayımlanmış sürüm [Entity Framework 6](https://msdn.microsoft.com/data/ef) ' dır. [Entity Framework 7](https://docs.efproject.net/en/latest/) yayın öncesi sürümündedir.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Araçlar, uygulamalar oluşturmanıza yardımcı olacak şekilde tasarlanmıştır [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] . Araçların tüm belgeleri [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] şunlardır: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]Araçlarla, mevcut bir veritabanından *kavramsal model* oluşturabilir ve ardından kavramsal modelinizi grafiksel olarak görselleştirebilir ve düzenleyebilirsiniz. Ya da önce bir kavramsal model oluşturabilir, ardından modelinizi destekleyen bir veritabanı oluşturabilirsiniz. Her iki durumda da, temel alınan veritabanı değiştiğinde modelinizi otomatik olarak güncelleştirebilir ve uygulamanız için otomatik olarak nesne katmanı kodu oluşturur. Veritabanı oluşturma ve nesne katmanı kod üretimi özelleştirilebilir.

 Bunlar Visual Studio 2015 ' de Varlık Veri Modeli araçları oluşturan özel araçlardır:

- [!INCLUDE[vstecado](../includes/vstecado-md.md)] ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tasarımcı** (**Entity Desisgner**) kullanarak varlıklar, ilişkilendirmeler, eşlemeler ve devralma ilişkilerini görsel olarak oluşturabilir ve değiştirebilirsiniz. **Entity Desisgner** Ayrıca, [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nesne katmanı kodu oluşturur.

- ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Sihirbazı** , mevcut bir veritabanından kavramsal bir model oluşturmak ve uygulamanıza veritabanı bağlantı bilgilerini eklemek için kullanabilirsiniz.

- Önce kavramsal model oluşturmak için **veritabanı oluşturma Sihirbazı 'nı** kullanabilir, sonra da modeli destekleyen bir veritabanı oluşturabilirsiniz.

- Temel veritabanında değişiklik yapıldığında kavramsal modelinizi, depolama modelinizi ve eşlemelerinizi güncelleştirmek için **model güncelleştirme sihirbazını** kullanabilirsiniz.

  > [!NOTE]
  > Visual Studio 2010 ' den itibaren [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Araçlar desteklemez [!INCLUDE[ss2k](../includes/ss2k-md.md)] .

  Araçlar bir. edmx dosyası oluşturur veya değiştirir. Bu dosya kavramsal modeli, depolama modelini ve bunlar arasındaki eşlemeleri açıklayan bilgiler içerir. Daha fazla bilgi için bkz.  [edmx](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework güç araçları, Varlık Veri Modeli kullanan uygulamalar oluşturmanıza yardımcı olur. Araçlar kavramsal model oluşturabilir, var olan bir modeli doğrulayabilir, kavramsal modeli temel alan nesne sınıflarını içeren kaynak kodu dosyaları üretebilir ve modelin oluşturduğu görünümleri içeren kaynak kodu dosyaları oluşturabilir. Ayrıntılı bilgi için bkz. [önceden oluşturulmuş eşleme görünümleri](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[ADO.NET Entity Framework](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] Uygulamaları oluşturmak için sağlayan araçların nasıl kullanılacağını açıklar.|
|[Varlık Veri Modeli](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Üzerinde oluşturulan uygulamalar tarafından kullanılan verilerle çalışmaya yönelik bağlantılar ve bilgiler sağlar [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] .|
|[Tam .NET kullanmaya başlama (konsol, WinForms, WPF vb.)](/ef/ef6/get-started)|Entity Framework 7 kullanan .NET masaüstü uygulamaları oluşturma hakkında öğreticiler sağlar.|
|[ASP.NET 5 uygulamasını yeni veritabanına](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Entity Framework 7 kullanarak yeni bir ASP.NET 5 uygulamasının nasıl oluşturulduğunu açıklar.|

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
