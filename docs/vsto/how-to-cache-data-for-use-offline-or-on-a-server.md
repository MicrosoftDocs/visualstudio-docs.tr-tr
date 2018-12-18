---
title: 'Nasıl yapılır: çevrimdışı veya sunucuda kullanmak için verileri önbelleğe alma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a53b3539d71383d4fad95838250380c5849e8c5b
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254218"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Nasıl yapılır: çevrimdışı veya sunucuda kullanmak için verileri önbelleğe alma
  Böylece kullanılabilir belgede önbelleğe alınacak bir veri öğesi çevrimdışı olarak işaretleyebilirsiniz. Bu ayrıca, belgenin bir sunucuda depolandığında başka bir kodla yönetilebilmesini belgedeki verileri mümkün kılar.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Veri öğesi, kodunuzda bildirilmişse veya, kullanıyorsanız önbelleğe alınacak bir veri öğesi işaretleyebilirsiniz bir <xref:System.Data.DataSet>, bir özellik ayarı tarafından **özellikleri** penceresi. Olmayan bir veri öğesi önbelleğe varsa bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>, belgede önbelleğe alınmasını ölçütlerini karşıladığından emin olun. Daha fazla bilgi için bkz: [veriyi önbelleğe](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Veri kümeleri olarak işaretlenmiş bir Visual Basic kullanılarak oluşturulan **önbelleğe alınan** ve **WithEvents** (gelen sürüklenen veri kümeleri dahil olmak üzere **veri kaynakları** penceresi veya **Araç** sahip **CacheInDocument** özelliğini **True**) önbelleğinde adları alt çizgi öneklerine sahiptir. Örneğin, bir veri kümesi oluşturursanız ve adlandırın **müşteriler**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> ad **_Customers** önbelleğinde. Kullandığınızda <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> bu önbelleğe alınan öğe erişmek için belirtmelisiniz **_Customers** yerine **müşteriler**.  
  
### <a name="to-cache-data-in-the-document-using-code"></a>Kod kullanarak belgede veriyi önbelleğe almak için  
  
1.  Bir ortak alan veya özelliği veri öğesi için bir konak öğesi sınıfı projenizdeki bir üyesi olarak gibi bildirin `ThisDocumen`t sınıfı bir Word projesinde veya `ThisWorkbook` Excel projesinde sınıfı.  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> özniteliği belgenin veri önbelleğinde depolanan veri öğesini işaretlemek için üyesine. Aşağıdaki örnekte, bu öznitelik için alan bildirimini uygulanır bir <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  Veri öğesinin bir örneğini oluşturmak için kodu ekleyin ve, varsa veritabanından yüklenemiyor.  
  
     Veri öğesi, yalnızca ilk oluşturulduğunda yüklenir; Bundan sonra önbellek belgeyle kalır ve güncelleştirmek için başka bir kod yazmanız gerekir.  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Özellikler penceresini kullanarak bir veri kümesini belgede önbelleğe almak için  
  
1.  Örneğin, Visual Studio tasarımcısı araçları kullanarak proje bir veri kaynağı ekleyerek kullanarak veri kümesini projeye ekleyin **veri kaynakları** penceresi.  
  
2.  Zaten bir tane ve örnek Tasarımcısı'nda seçerseniz dataset örneği oluşturun.  
  
3.  İçinde **özellikleri** penceresindeki ayarlayın **CacheInDocument** özelliğine **doğru**.  
  
     Daha fazla bilgi için bkz: [Office projelerinde Özellikler](../vsto/properties-in-office-projects.md).  
  
4.  İçinde **özellikleri** penceresindeki ayarlayın **değiştiricileri** özelliğine **ortak** (Bu varsayılan **dahili**).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Verileri önbelleğe](../vsto/caching-data.md)   
 [Nasıl yapılır: program aracılığıyla bir veri kaynağı Office belgesinden önbelleğe alma](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Nasıl yapılır: bir parola korumalı belgede veriyi önbelleğe alma](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Sunucudaki belgelerde verilere erişmek](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Verileri kaydetme](/visualstudio/data-tools/saving-data)  
  
  