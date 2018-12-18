---
title: XML şemaları ve belge düzeyi özelleştirmelerdeki veriler
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e62a8a7bef72ce34c46621b63188f9d71512be20
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677122"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>XML şemaları ve belge düzeyi özelleştirmelerdeki veriler
  **Önemli** Microsoft Word ile ilgili bu konu kümesindeki bilgileri avantajı ve kişiler ve kimin bulunur Amerika Birleşik Devletleri ve kendi bölgeler dışında veya servis kullanan kuruluşlar için özel olarak sunulan veya geliştirme üzerinde çalışan programlar Ocak Microsoft uygulaması belirli işlevlerin ne zaman kaldırıldı 2010'dan önce Microsoft lisanslı Microsoft Word ürünler, Microsoft Word için özel XML ilgili. Bu bilgileri Microsoft Word ile ilgili değil okuma veya kişi ve kuruluşların Amerika Birleşik Devletleri ya da kullanarak veya Microsoft tarafından 10 Ocak 2010'dan sonra lisansına sahip Microsoft Word ürünleri üzerinde çalışan programlar geliştirme alt bölgeleri tarafından kullanılan ; Bu ürünlerin bu tarihten önce lisanslı veya satın alınan ve Amerika Birleşik Devletleri dışında kullanım için lisanslı ürünleri aynı davranmaz.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel ve Microsoft Office Word belgelerinize şemaları eşleme olanağı sağlar. Bu özellik, belgenin içine ve dışına XML veri alma ve verme basitleştirebilir.  
  
 Visual Studio kullanıma sunan bir programlama modeli denetimlerinde olarak belge düzeyi özelleştirmeleri şeması öğeleri eşlendi. Excel için Visual Studio, veritabanları, Web Hizmetleri ve nesneleri verilere denetimler bağlama için destek ekler. Word ve Excel için Visual Studio şema eşlenmiş bir belgeyle çözümleriniz için bir Gelişmiş son kullanıcı deneyimi oluşturmak için kullanılabilen eylemler bölmesi için destek ekler. Daha fazla bilgi için [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  Excel çözümleri, çok bölümlü XML şemaları kullanamazsınız.  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Excel çalışma kitaplarına şemaları eklendiğinde oluşturulan nesneleri  
 Bir çalışma kitabına bir şema eklediğinizde, Visual Studio otomatik olarak birkaç nesnesi oluşturur ve bunları projenize ekler. Excel tarafından yönetildiği bu nesneler, Visual Studio araçları kullanarak silinmemelidir. Silmek için çalışma sayfasından eşlenmiş öğeleri kaldırma veya Excel araçlarını kullanarak şema ayırma.  
  
 İki ana nesnesi vardır:  
  
-   XML Şeması (XSD dosyası). Çalışma kitabındaki tüm şema için Visual Studio şema projeye ekler. Bu proje öğesiyle XSD uzantı olarak görünür **Çözüm Gezgini**.  
  
-   Bir türü belirtilmiş <xref:System.Data.DataSet> sınıfı. Bu sınıf şemaya göre oluşturulur. Bu veri kümesi sınıfı görülebilir **sınıf görünümü**.  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Excel çalışma sayfalarına şema öğeleri eşleştirildiğinde oluşturulan nesneleri  
 Bir şema öğesinden eşlediğinizde **XML kaynağı** görev bölmesinde Visual Studio çalışma sayfasına otomatik olarak birkaç nesnesi oluşturur ve bunları projenize ekler:  
  
-   Denetimler. Çalışma kitabında, eşlenen her nesneye ilişkin bir <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> denetimi (yinelenmeyen şema öğeleri) veya bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi (şema öğeleri yinelenen için) programlama modeli içinde oluşturulur. <xref:Microsoft.Office.Tools.Excel.ListObject> Denetimi yalnızca eşlemeleri ve eşlenen nesneler çalışma kitabından silindiğinde silinebilir. Denetimleri hakkında daha fazla bilgi için bkz. [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource. Oluştururken bir <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> çalışma için yinelenmeyen bir şema öğesine eşleyerek bir <xref:System.Windows.Forms.BindingSource> oluşturulur ve <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> denetimin bağlı <xref:System.Windows.Forms.BindingSource>. Bağlamalısınız <xref:System.Windows.Forms.BindingSource> belirlenmiş örneği gibi bir belge için eşlenen şemaya uyan veri kaynağının bir örneği için <xref:System.Data.DataSet> oluşturulan sınıf. Bağlama ayarlayarak oluşturma <xref:System.Windows.Forms.BindingSource.DataSource%2A> ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> sunulan özellikler **özellikleri** penceresi.  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource> İçin oluşturulmamış <xref:Microsoft.Office.Tools.Excel.ListObject> nesneleri. El ile bağlamanız gerekir <xref:Microsoft.Office.Tools.Excel.ListObject> ayarlayarak veri kaynağına <xref:System.Windows.Forms.BindingSource.DataSource%2A> ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> özelliklerinde **özellikleri** penceresi.  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office şemaları ve Visual Studio veri kaynakları penceresi eşlenmiş.  
 Her iki eşlenen şema işlevselliğini Office ve Visual Studio **veri kaynakları** penceresi, raporlama veya düzenlemek için Excel çalışma sayfasındaki veri sunmanıza yardımcı olabilir. Her iki durumda da Excel çalışma sayfasına veri öğelerini sürükleyebilirsiniz. Her iki yöntem üzerinden veriye olan denetimler oluşturma bir <xref:System.Windows.Forms.BindingSource> gibi bir veri kaynağına bir <xref:System.Data.DataSet> veya bir web hizmeti.  
  
> [!NOTE]  
>  Bir çalışma sayfasına yinelenen bir şema öğesine eşlediğinizde, Visual Studio oluşturur bir <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Otomatik olarak verilerine bağlı <xref:System.Windows.Forms.BindingSource>. El ile bağlamanız gerekir <xref:Microsoft.Office.Tools.Excel.ListObject> ayarlayarak veri kaynağına <xref:System.Windows.Forms.BindingSource.DataSource%2A> ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> özelliklerinde **özellikleri** penceresi.  
  
 Aşağıdaki tabloda bazı iki yöntem arasındaki farklar gösterilmektedir.  
  
|XML Şeması|Veri Kaynakları penceresi|  
|----------------|-------------------------|  
|Office arabirimini kullanır.|Kullanan **veri kaynakları** Visual Studio'daki.|  
|XML dosyalarından verileri dışarı aktarma ve içeri aktarma için yerleşik Office özelliklerini etkinleştirir.|İçeri aktarma sağlayın ve işlevsellik programlı olarak dışarı aktarma gerekir.|  
|Oluşturulan denetimleri verilerle doldurmak için kod yazmanız gerekir.|Gelen eklenen denetimler **veri kaynakları** sahip veritabanı sunucuları kullandığınızda gerekli bağlantı dizeleri yanı sıra bunları doldurmak için otomatik olarak üretilen kod.|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Word belgelerine şemaları eklendiğinde davranışı  
 Veri nesneleri, bir belge düzeyinde Office projesinde kullanılan bir Word belgesi için bir şema iliştirdiğinizde oluşturulmaz. Ancak, bir şema öğesine belgenize eşlediğinizde, denetimleri oluşturulur. Denetim türü, harita öğesinin hangi türüne göre değişir; Yinelenen öğeler oluşturmak <xref:Microsoft.Office.Tools.Word.XMLNodes> denetimleri ve yinelenmeyen öğe oluştur <xref:Microsoft.Office.Tools.Word.XMLNode> kontrol eder. Daha fazla bilgi için [XMLNodes denetimi](../vsto/xmlnodes-control.md) ve [XMLNode denetimi](../vsto/xmlnode-control.md).  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>XML şemaları içeren çözüm dağıtımı  
 Belgeye eşlenen bir XML Şeması kullanan bir çözümü dağıtmak için bir yükleyici oluşturmanız gerekir. Yükleyici, kullanıcının bilgisayarında şema kitaplığındaki şema kaydolmalıdır. Şema kaydetmezseniz, Word belgesinde kullanıcı açıldığında olan öğeler üzerinde geçici bir şema oluşturur çünkü çözüm çalışmaya devam eder. Ancak, kullanıcı gerçekleştiremez veya projeyi oluşturmak için kullanılan şema doğrulama gerçekleştirmek mümkün olmayacaktır. Yükleyiciler hakkında daha fazla bilgi için bkz. [uygulamaları, hizmetleri ve bileşenleri dağıtma](/visualstudio/deployment/deploying-applications-services-and-components).  
  
 Ayrıca projenize şema kitaplıkta bulunuyor ve kayıtlı olup olmadığını denetlemek için kod ekleyebilirsiniz. Yüklü değilse, kullanıcıyı uyarır.  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: şemaları Visual Studio içindeki Word belgeleriyle eşleştirme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarıyla eşleştirme](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  
