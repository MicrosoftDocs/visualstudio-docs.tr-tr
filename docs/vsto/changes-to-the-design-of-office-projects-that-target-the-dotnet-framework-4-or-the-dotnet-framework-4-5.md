---
title: .NET Framework'ü hedefleyen Office projelerinde tasarımını değiştirir
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b200c5b0df5f150e0d34b351a3e36a8a986f3ed6
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248250"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Office projeleri tasarımını hedefleyen .NET Framework 4 veya .NET Framework 4.5 değiştirir.
  İtibariyle [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], Visual Studio hedefleyen Office projelerinde tasarımını bazı değişiklikler sunulan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri. Office projeleri Visual Studio'nun önceki sürümlerinde biliyorsanız, .NET Framework 4.0 veya daha sonra bu sürümleri hedefleyen Office projelerinde geliştirmeden önce bu değişikliklerin farkına olmalıdır. Varsayılan olarak, Visual Studio 2013 veya üzeri kullanarak oluşturduğunuz tüm projeleri .NET Framework 4.0 veya üzeri hedefler.  
  
 Aşağıdaki bölümlerde bu Office proje tasarım değişiklikleri açıklanmaktadır.  
  
## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio 2010 Araçları arabirimi tabanlı tasarımını anlayın  
 Hedefleyen bir Office projesi geliştirdiğinizde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra Visual Studio 2010 Tools for Office runtime kullandığınız türlerin çoğu arabirimdir. Bu, büyük bir değişiklik önceki sürümlerinden [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], bu tür sınıflar olduğu. Hedeflediğinizde gibi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya da sonraki <xref:Microsoft.Office.Tools.Excel.Worksheet> ve <xref:Microsoft.Office.Tools.Word.Document> sınıf yerine arayüzleridir türleridir. Daha fazla bilgi için [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
 Doğrudan'ın önceki sürümlerinde örneği oluşturulamadı herhangi bir türü için [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], artık yöntemlerini kullanın `Globals.Factory` bu türlerin örneklerini alınacak nesne. Örneğin, uygulayan bir nesne almak için <xref:Microsoft.Office.Tools.Excel.SmartTag> kullanın, arabirim `Globals.Factory.CreateSmartTag` yöntemi. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [.NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Office projelerindeki Şerit Özelleştirmelerini Güncelleştirme](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Outlook projelerindeki form bölgelerini güncelleştirme](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### <a name="new-base-classes-in-office-projects"></a>Office projelerinde yeni temel sınıflar  
 Office çalışma zamanı için Visual Studio 2010 Araçları arabirimi tabanlı yeni tasarımını Office projelerinde oluşturulan sınıflar gibi etkiler `ThisDocument`, `ThisWorkbook`, ve `ThisAddIn`. .NET Framework 3.5 ve framework'ün önceki sürümlerini hedefleyen Office projelerinde sınıflarda oluşturulan bu sınıfların türetilmesi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] gibi `Microsoft.Office.Tools.Word.Document`, `Microsoft.Office.Tools.Excel.Worksheet`, ve `Microsoft.Office.Tools.AddIn`. ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra bu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sınıfları artık arayüzleridir. Bu nedenle oluşturulan sınıflar Office projelerinde artık kendi uygulamasından türetebilirsiniz. Bunun yerine, oluşturulan sınıflar gibi yeni bir temel sınıftan türetilen <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>, ve <xref:Microsoft.Office.Tools.AddInBase>. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md) ve [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).  
  
 Taban sınıfları olmayan bir parçası [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yeniden dağıtılabilir. Bunun yerine, bunlar Visual Studio'ya dahil olan yardımcı programları derlemelerde tanımlanır. Bu derlemeler Office projeleri derlemek ve çözümünüzle birlikte dağıtılan çıktı klasörüne kopyalanır. Yardımcı programları derlemeler hakkında daha fazla bilgi için bkz. [Office çalışma zamanı için Visual Studio araçlarındaki derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>.NET Framework 4'e yeniden hedeflendi Office projelerinde bozucu değişiklikler  
 Office projelerinde için yeniden hedeflendi karşılaştığınız ana bozucu değişiklikler aşağıdaki tabloda listelenmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri. Daha fazla ayrıntı için bkz. [geçirme Office çözümlerini .NET Framework 4 veya sonraki bir sürüme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
|Yeni değişiklik|Sonucu|  
|---------------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute> Artık kullanılmaz ve Office projelerinde desteklenir.|Bu öznitelik, Visual Studio 2008'den yükseltme Office projelerinde AssemblyInfo kod dosyasından kaldırmanız gerekir. Daha fazla bilgi için [gerekli .NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Office projelerini çalıştırmak için değişiklikler](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|**ExcelLocale1033Attribute** artık kullanılmaz ve Excel projelerinde desteklenir.|Bu özniteliği kaldırmalısınız *AssemblyInfo* Excel projelerinde kod dosyası. Daha fazla bilgi için [.NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz güncelleştirme Excel ve Word projelerini](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Programlama modeli **Şerit (Görsel Tasarımcı)** proje öğeleri değişti.|Şerit öğeleri için arka plan kod dosyası projenize değiştirmeniz gerekir. Ayrıca, Şerit denetimlerini çalışma zamanında başlatır, Şerit olaylarını işleme veya program aracılığıyla bir Şerit bileşeninin konumunu ayarlar herhangi bir kodu değiştirmeniz gerekir. Daha fazla bilgi için [güncelleştirme Şerit özelleştirmeleri .NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Office projelerindeki](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Outlook form bölgeleri programlama modeli değişti.|Tüm form bölgeleri için arka plan kod dosyası projenize ve çalışma zamanında belirli bir form bölgesi sınıflarını başlatır herhangi bir kodu değiştirmeniz gerekir. Daha fazla bilgi için [.NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Outlook projelerindeki form bölgelerini güncelleştirme](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Akıllı etiketler Excel ve Word projeleri için programlama modeli değişti. Akıllı etiketler bırakılmıştır [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] ve [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Çözümünüzü akıllı etiketler kullanılıyorsa, proje derleme hataları ortaya çıkar. Akıllı etiketler kullanım dışıdır çünkü [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] ve [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], test ve hata ayıklama çözümde önce etiketleri kaldırmalısınız [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] veya üzeri.|  
|Söz dizimi `GetVstoObject` ve `HasVstoObject` yöntemleri değişti|Geçmesi gereken `Globals.Factory` nesnesi, yerel nesneler birincil birlikte çalışma derlemeleri (PIA) üzerinden erişim ya da bu yöntem tarafından döndürülen nesne üzerinde erişebileceğiniz bu yöntemlere yapılan `Globals.Factory` projenizdeki özellik. Daha fazla bilgi için [.NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz güncelleştirme Excel ve Word projelerini](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Word içerik denetimleri olaylarını yeni temsilciler ile ilişkilidir.|Word içerik denetimleri yeni temsilciler belirtmek için olayları işleyen herhangi bir kodu değiştirmeniz gerekir. Daha fazla bilgi için [.NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz güncelleştirme Excel ve Word projelerini](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|`OLEObject` Ve `OLEControl` sınıfları yeniden adlandırıldı.|Bu sınıfların örnekleri kullanmak için kullanan herhangi bir kodu değiştirmeniz gerekir <xref:Microsoft.Office.Tools.Excel.ControlSite> veya <xref:Microsoft.Office.Tools.Word.ControlSite> nesnelerini. Daha fazla bilgi için [.NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz güncelleştirme Excel ve Word projelerini](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Öğe sınıfları gibi ana bilgisayar `ThisWorkbook`, `Sheet` *n*, `ThisDocument`, ve `ThisAddIn`, artık sağlayan bir `Dispose` kılabileceğiniz yöntemi.|Herhangi bir kod taşımanız gerekir `Dispose` yöntemi geçersiz kılma `Shutdown` konak öğesi sınıfı, örneğin, olay işleyicisinde `ThisAddIn_Shutdown`, kaldırıp `Dispose` yöntemini geçersiz kılma, ana bilgisayar öğesi sınıfından.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Office geliştirme yenilikler nelerdir?](https://msdn.microsoft.com/library/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  