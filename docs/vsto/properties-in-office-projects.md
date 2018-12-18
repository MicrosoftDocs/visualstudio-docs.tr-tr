---
title: Office projelerinde Özellikler
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9369a42f1f4a8497df42f940bb8bd23453803a26
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862157"
---
# <a name="properties-in-office-projects"></a>Office projelerinde Özellikler
  Visual Studio'da Office projeleri için kullanılabilir olan çeşitli önemli özellikleri vardır. Bu özellikler erişilebilen **özellikleri** penceresi.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="namespace-for-host-item"></a>Namespace for host Item  
 Kullanım **Namespace for Host Item** özelliğinin ana öğesi sınıfları için ad alanı değiştirmek için (örneğin, `ThisAddIn`, `ThisWorkbook`, veya `ThisDocument` sınıflar) görselde C# projeleri. Bu özellik görünür **özellikleri** bir belge düzeyinde projedeki belge düğümünü seçtiğinizde penceresi (gibi *ExcelWorkbook1.xlsx* veya *WordDocument1.docx* ) veya bir VSTO eklenti projesinde (örneğin, Excel veya Word'den) uygulama düğümü **Çözüm Gezgini**.  
  
 Bir görsel oluşturduğunuzda C# Office project, ana bilgisayar öğeleri proje adını temel alarak bir ad verilir. Kullanmanız önerilir **Namespace for Host Item** ad alanı değiştirmek yerine, kodu düzenleme için özellik dosyalarını doğrudan. Bu özelliği kullandığınızda, ad alanı görünür kod dosyalarını yanı sıra (gizli) oluşturulan kod dosyaları, değiştirilir.  
  
## <a name="cacheindocument"></a>CacheInDocument  
 **CacheInDocument** özellik görünür **özellikleri** penceresi örneği seçtiğinizde belge düzeyinde projeler için bir <xref:System.Data.DataSet> Visual Studio Tasarımcısı'nda. Yalnızca Genel üyeler önbelleğe alınabilir; emin **değiştiriciler** özelliği **genel** önbelleğe almak istiyorsanız bir <xref:System.Data.DataSet>.  
  
 Bu özellik, bir Boole değeri alır:  
  
- Seçin **true** belgedeki veri kümesinin önbelleğe.  
  
- Seçin **false** belgede önbelleğe alınması için veri kümesini istemiyorsanız.  
  
  Verileri önbelleğe alma hakkında daha fazla bilgi için bkz. [veri belge düzeyi özelleştirmelerdeki önbelleğe alınmış](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="value2"></a>Value2  
 **Value2** özelliği, yalnızca Excel çalışma kitabı veya şablondaki projeleri için kullanılabilir. Altında görünür **Databindings** özelliği düğümünde **özellikleri** seçtiğinizde penceresi bir <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma Tasarımcı üzerinde denetim.  
  
 Kullanım **Value2** özelliğinde **özellikleri** bağlamak için pencere <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliği <xref:Microsoft.Office.Tools.Excel.NamedRange> veri kaynağınızdaki bir alana.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)   
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)   
 [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md)  
  
  