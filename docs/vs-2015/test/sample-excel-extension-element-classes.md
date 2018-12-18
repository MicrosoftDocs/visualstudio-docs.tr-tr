---
title: 'Örnek Excel uzantısı: Öğe sınıfları | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: fb5085bdd9a79330f7c4f73fb39993af63eb0a78
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811952"
---
# <a name="sample-excel-extension-element-classes"></a>Örnek Excel Eklentisi: Öğe Sınıfları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğesinden türetilen sınıflarda uzantı kullanır <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> ve çalışma ve hücre denetimi içinde temsil [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
 Bu uzantı için temel öğe `ExcelElement`. `ExcelWorksheetElement` Sınıfı ve `ExcelCellElement` sınıfı bu öğeden devralır  
  
## <a name="element-and-elementinformation-classes"></a>Öğe ve ElementInformation sınıfları  
 `Element` Excel eklentisi için tüm kullanıcı arabirimi öğeleri için temel sınıf ve devraldığı <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> sınıfı. `ElementInformation` öğe için temel sınıf bilgisi sınıfları örneğinde olduğu ve hiç üye yok.  
  
#### <a name="simple-properties-and-methods"></a>Basit özellikleri ve yöntemleri  
 Bu üyeler dönüş değerini gibi basit değerleri `Name` özelliği veya değerinin `ClassName` özelliği ve kod NET ve kolay okunur. Bazı değerler kullanarak döndürülür `Utility` daha sonra açıklanan sınıfı. Başkalarının dönüş `null` olduğundan bu örnek uzantıyla ilgili değildir. İki üyesi diğerlerine göre daha ilgi çekici: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> özelliği ve <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> yöntemi.  
  
#### <a name="queryid-property"></a>QueryId özelliği  
 Bu özellik benzersiz olarak tanımlanabilmesi denetim kayıttan yürütme sırasında özellik ad-değer çiftleri yapılan bir koşul döndürür. Her denetim türetilmiş sınıf için geliştirici döndürmek için bu özellik geçersiz kılmanız gerekir bir <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> framework denetimin kullanıcı Arabiriminde bulmak için kullanabileceğiniz nesne.  
  
#### <a name="cacheproperties-method"></a>CacheProperties yöntemi  
 Bu yöntem kayıt işlemi sırasında önemli özellikleri anlık görüntüsünü kaydetmek için öğe bildirmek için test çerçevesi tarafından çağrılır. Gerçek UI denetimi artık ekranda olsa bile bu özellikler kullanılabilir durumda tutar.  
  
## <a name="worksheetelement-and-worksheetinformation-classes"></a>WorksheetElement ve WorksheetInformation sınıfları  
 `WorksheetElement` Sınıfı bir Excel çalışma sayfasına test çerçevesi temsil eder ve devralınan `Element` temel sınıfı. Üç özellik Excel çalışma sayfası nesnesi hakkında özel bilgiler sağlamak için geçersiz kılınır: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A>, ve <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Da COM görünür hale getirmek için bu sınıfın uygulanır  
  
 `WorksheetInformation` Sınıfı, bir Excel çalışma hakkında bilgi gösterir. Tek bir üyeye sahip `SheetName` özelliği bu örnek için yeterlidir.  
  
## <a name="cellelement-and-cellinformation-classes"></a>CellElement ve CellInformation sınıfları  
 `CellElement` Sınıfı bir Excel hücresini temsil eder ve devralınan `Element` temel sınıfı. Geçersiz kılınan tek üye <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> döndüren özelliğinin bir <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> kullanan `RowIndex` ve `ColumnIndex` hücrenin tanımlamak için özellikleri.  
  
## <a name="utilities-and-excelutilities-classes"></a>Yardımcı programları ve ExcelUtilities sınıfları  
 İç `ExcelUtilities` sınıfı teknoloji adı ve belirtilen pencere tanıtıcısı bir Excel çalışma sayfasına temsil edip etmediğini belirleyen bir yöntemi gibi bazı sabit değerler sağlar.  
  
 `Utilities` Sınıfında yardımcı yöntemler, çeşitli kullanıcı Arabirimi hakkında bilgiler döndürür. Dış Sistem DLL'lerini, doğrudan çağrıları gibi bazı yöntemler kullanmanız **USER32. DLL** ve **OLEACC. DLL**, kullanıcı Arabiriminden pencere işleyicileri almak için<strong>.</strong>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



