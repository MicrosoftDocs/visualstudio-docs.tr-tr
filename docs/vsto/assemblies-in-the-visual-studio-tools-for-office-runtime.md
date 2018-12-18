---
title: Office çalışma zamanı için Visual Studio araçlarındaki derlemeler
titleSuffix: ''
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66ee95d4f102ac4206a9ed55a1fc97fc251c4f9c
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248124"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio araçlarındaki derlemeler
  Bir Office projesi oluşturduğunuzda, Visual Studio başvuruları otomatik olarak ekler. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] proje türü ve hedef projenin .NET Framework için kullanılan derlemeler. .NET Framework 3.5 için Office uzantılarındaki derlemeler farklı vardır [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], ve [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Office uzantıları hakkında daha fazla bilgi için bkz. [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>.NET Framework 4 için Office uzantılarındaki derlemeler ve [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 Aşağıdaki tablo için Office uzantılarında dahil olan derlemeleri listeler [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ve [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Bu bütünleştirilmiş kodlarında türler ve ad alanları hakkında daha fazla bilgi için bkz [yönetilen başvurusu &#40;Visual Studio'da Office geliştirme&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Derleme adı|Açıklama|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Aşağıdaki türlerini sağlar:<br /><br /> -Şerit özelleştirmeleri ve akıllı etiketleri oluşturmak için türleri. **Not:**      Akıllı etiketler bırakılmıştır [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] ve [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Eylemler bölmeleri belge düzeyi özelleştirmeleri ve özel görev bölmeleri, VSTO eklentileri oluşturma türleri.|  
|Microsoft.Office.Tools.Excel.dll|Excel projeleri ve destekleyen türler için konak denetimlerinin ve konak öğelerinin temsil eden arabirim sağlar. Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Excel](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Outlook VSTO eklentileri özel form bölgeleri oluşturmak için kullanabileceğiniz türler sağlar.|  
|Microsoft.Office.Tools.Word.dll|Word projeleri ve destekleyen türler için konak denetimlerinin ve konak öğelerinin temsil eden arabirim sağlar. Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Word'ü](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Aşağıdaki türlerini sağlar:<br /><br /> -Office çalışma zamanı için Visual Studio Araçları tarafından oluşturulan özel durumlar.<br />-Form bölgeleri öznitelikleri Outlook oluştururken kullanabilirsiniz.|  
|Microsoft.Office.Tools.dll|Office çalışma zamanı altyapısı için Visual Studio Araçları'nın bir parçasıdır ve doğrudan kodunuzdan kullanılmaya yönelik değildir türler sağlar.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Aşağıdaki türlerini sağlar:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Özniteliği ve <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> belge düzeyi özelleştirmesinde önbellek veri nesneleri için kullanabileceğiniz bir arabirim. Daha fazla bilgi için [veriyi önbelleğe alma](../vsto/caching-data.md).<br />- <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Arabirimi, bir Office çözümü için ClickOnce yükleyicisi'nin son adım olarak ek yükleme adımlarını çalıştırmayı uygulayabilirsiniz. Daha fazla bilgi için [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Office çalışma zamanı için Visual Studio Araçları tarafından oluşturulan özel durumlar.<br />-Office çalışma zamanı altyapısı için Visual Studio Araçları'nın bir parçasıdır ve doğrudan kodunuzdan kullanılmaya yönelik değildir diğer türleri.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Aşağıdaki türlerini sağlar:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Belgelere özelleştirme derlemeleri eklemek ve belgelerdeki önbelleğe alınan verilere erişmek için kullanabileceğiniz sınıfı. Daha fazla bilgi için [ServerDocument sınıfını kullanarak bir sunucu üzerinde belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Belge düzeyi özelleştirmesinde veri hiyerarşisini temsil eden birden fazla sınıf önbelleğe. Daha fazla bilgi için [sunucudaki belgelerde verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] aşağıdaki derlemelere de başvurur. Bu derlemeler olmayan parçası [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yeniden dağıtılabilir. Bunun yerine, çözümünüz ile dağıtılmalıdır bağımlı derlemeleri değildirler. Varsayılan olarak, projenizin yapı çıkış klasörüne kopyalanırlar ( **Yereli Kopyala** özelliği bu derlemeler için ayarlanmış **True**). ClickOnce kullanarak projenize dağıtırsanız, bu derlemeleri oluşturulan pakete dahil edilir.  
  
|Derleme adı|Açıklama|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Temel sınıflar için oluşturulan sağlar `ThisAddIn` VSTO eklentisi projeleri ve tüm projeleri oluşturulan Şerit sınıfında sınıfı.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Aşağıdaki türlerini sağlar:<br /><br /> -Temel sınıflar için oluşturulan `ThisWorkbook` ve `Sheet` sınıflarda belge düzeyinde projeler için Excel.<br />-Excel projelerinde çalışma sayfalarında kullanabilirsiniz Windows Forms denetimleri.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Temel sınıflar için oluşturulan sağlar `ThisAddIn` ve form bölgesi sınıflarını Outlook projeleri.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Aşağıdaki türlerini sağlar:<br /><br /> -Temel sınıflar için oluşturulan `ThisDocument` Word için belge düzeyi projelere sınıf.<br />-Word projeleri belgelerinde kullanabileceğiniz Windows Forms denetimleri.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>.NET Framework 3.5 için Office uzantılarındaki derlemeler  
 Aşağıdaki tablo, .NET Framework 3.5 için Office uzantılarında bulunan derlemeleri listeler. Ad alanlarını ve sınıfları bu derlemeler ile ilgili belgeler için Visual Studio 2008 belgelerinde aşağıdaki başvuru bölümüne bakın: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Derleme adı|Açıklama|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Aşağıdaki türlerini sağlar:<br /><br /> -Microsoft.Office.Tools.AddIn temel sınıf için VSTO eklentileri.<br />-Şerit özelleştirmeleri ve akıllı etiketleri oluşturmak için sınıfları. **Not:**      Akıllı etiketler bırakılmıştır [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] ve [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Belge düzeyi özelleştirmeleri ve VSTO eklentileri özel görev bölmeleri Eylemler bölmesi oluşturmak için sınıfları.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Konak denetimlerinin ve konak öğelerinin Excel çözümleri sağlar. Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Excel](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Outlook VSTO eklentileri özel form bölgeleri oluşturmak için kullanabileceğiniz sınıflar sağlar.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Konak denetimlerinin ve konak öğelerinin Word çözümleri sağlar. Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Word'ü](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Aşağıdaki türlerini sağlar:<br /><br /> - [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) konak denetimlerinde belge düzeyi özelleştirmelerini için veri bağlama özellikleri sağlayan sınıf.<br />-Office çalışma zamanı altyapısı için Visual Studio Araçları'nın bir parçasıdır ve doğrudan kodunuzdan kullanılmaya yönelik değildir diğer türleri.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Aşağıdaki türlerini sağlar:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Özniteliği ve <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> belge düzeyi özelleştirmesinde önbellek veri nesneleri için kullanabileceğiniz bir arabirim. Daha fazla bilgi için [veriyi önbelleğe alma](../vsto/caching-data.md).<br />-Office çalışma zamanı için Visual Studio Araçları tarafından oluşturulan özel durumlar.<br />-Office çalışma zamanı altyapısı için Visual Studio Araçları'nın bir parçasıdır ve doğrudan kodunuzdan kullanılmaya yönelik değildir diğer türleri.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Sağlar <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> arabirimi, bir Office çözümü için ClickOnce yükleyicisi'nin son adım olarak ek yükleme adımlarını çalıştırmayı uygulayabilirsiniz. Daha fazla bilgi için [Gelişmiş Office çözümü dağıtımında](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Aşağıdaki türlerini sağlar:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Özelleştirme derlemeleri program aracılığıyla belgelere iliştirmek ve belgeleri önbelleğe alınan verilere erişmek için kullanabileceğiniz sınıfı. Daha fazla bilgi için [ServerDocument sınıfını kullanarak bir sunucu üzerinde belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Belge düzeyi özelleştirmesinde veri hiyerarşisini temsil eden birden fazla sınıf önbelleğe. Daha fazla bilgi için [sunucudaki belgelerde verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Aşağıdaki türlerini sağlar:<br /><br /> -Kullanıcı ekleme, Office için güven kazandırmak için Liste girişlerini oluşturmak için kullanabileceğiniz Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry ve Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList sınıfları .NET Framework 3.5 kullanan çözümler.<br />-Office çalışma zamanı altyapısı için Visual Studio Araçları'nın bir parçasıdır ve doğrudan kodunuzdan kullanılmaya yönelik değildir diğer türleri.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  