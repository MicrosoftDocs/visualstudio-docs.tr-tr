---
title: Visual Studio 'da VBA ve Office çözümleri karşılaştırması
description: Visual Studio 'da Microsoft Visual Basic for Applications (VBA) ve Microsoft Office çözümleri arasındaki farklılıklar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a07711fd854bd0dc035cab776f713701d5d85200
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838119"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Visual Studio 'da VBA ve Office çözümleri karşılaştırması
  Microsoft Visual Basic for Applications (VBA), Office uygulamalarıyla sıkı bir şekilde tümleştirilmiş yönetilmeyen kod kullanır. Visual Studio kullanılarak oluşturulan Microsoft Office projeleri, .NET Framework ve Visual Studio tasarım araçlarından yararlanmanızı sağlar.

 Visual Studio kullanarak oluşturabileceğiniz Office çözümlerinin türleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="comparison"></a>Karşılaştırma
 Aşağıdaki tabloda, Visual Studio 'da VBA çözümleri ve Office çözümleri arasında temel bir karşılaştırma sunulmaktadır.

|VBA çözümleri|Visual Studio 'da Office çözümleri|
|-------------------|---------------------------------------|
|Belirli bir belgeye bağlı ve kalıcı olan kodu kullanır.|Belgeden (belge düzeyi özelleştirmeleri için) veya uygulama tarafından yüklenen bir derlemede (VSTO eklentileri için) ayrı olarak depolanan kodu kullanır.|
|Office nesne modelleri ve VBA API 'Leri ile birlikte kullanılır.|Hem Office nesne modellerine hem de API 'lere erişim sağlar [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|Makro kaydı ve Basitleştirilmiş geliştirici deneyimi için tasarlanmıştır.|Güvenlik, daha kolay kod bakımı ve tam Visual Studio tümleşik geliştirme ortamı (IDE) kullanma özelliği için tasarlanmıştır.|
|Office uygulamalarıyla sıkı bir şekilde tümleştirmeden faydalanabilir çözümler için iyi sonuç verir.|, Visual Studio 'nun ve ' nin tam kaynaklarından faydalanabilir çözümler için iyi sonuç verir [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|, Özellikle güvenlik ve dağıtım alanlarında bulunan, kuruluş için sınırlamalar içerir.|Kuruluşta kullanım için tasarlandı.|

 Daha hızlı bir şekilde VBA kullanarak daha kolay hale getiriyoruz. Özellikle, için VBA 'Yı kullanmaya devam etmek isteyebilirsiniz:

- Özel çalışma sayfası işlevleri.

- Makro kaydı.

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Visual Studio kullanılarak oluşturulan VBA çözümlerini ve Office çözümlerini birleştirme
 Visual Studio kullanarak oluşturulan Office Çözümlerinden VBA kodunu çağırabilirsiniz ve ayrıca VBA 'dan Visual Studio kullanarak oluşturulan Office çözümlerinde kod çağırabilirsiniz. Belirli bir teknik, Office çözümünüzün VSTO eklentisi veya belge düzeyi özelleştirmesi olmasına bağlı olarak farklılık gösterir. Daha fazla bilgi için bkz. [VSTO eklentilerindeki kodu diğer Office Çözümlerinden çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) ve [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Diğer Office çözümlerindeki VSTO eklentilerindeki kodu çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)
- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Visual Studio 'da Office geliştirme &#40;kullanmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
