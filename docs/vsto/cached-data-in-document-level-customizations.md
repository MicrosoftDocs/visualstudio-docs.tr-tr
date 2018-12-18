---
title: Belge düzeyi özelleştirmelerdeki önbelleğe alınmış veriler
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: c17c24dda11ea210c190a31197b783036357f2de
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248302"
---
# <a name="cached-data-in-document-level-customizations"></a>Belge düzeyi özelleştirmelerdeki önbelleğe alınmış veriler
  Belge düzeyi özelleştirmeleri işleminin birincil amacı, Office belgeleri görünümden veri ayırmaktır. Veri, sayı ve metin içeren belge içinde depolanan bilgileri ifade eder. Görünümü kullanıcı arabirimi hem de Microsoft Office Excel ve Microsoft Office Word nesne modeli anlamına gelir.  
  
 Visual Studio ayıran veri belge düzeyi özelleştirmeleri görünümünden olarak katıştırılmış veri sağlayarak bir *veri adası*ayrıca adlı *veri önbelleğini*. Okuma veya Word veya Excel başlatmadan doğrudan verileri değiştirebilirsiniz. Microsoft Office'in yüklü olmayan bir sunucudaki belgelerde verilere değiştirmeniz gerektiğinde kullanışlıdır. Word ve Excel istemci ortamlarda kullanıma yöneliktir; bir sunucuda çalıştırılmak üzere tasarlanmamıştır.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Belge düzeyi özelleştirmeleri hakkında daha fazla bilgi için bkz: [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) ve [belge düzeyi özelleştirmeler mimarisi](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understand-the-cached-data-programming-model"></a>Önbelleğe alınmış verileri programlama modelini anlama  
 Veri adası, çözümünüzdeki belirli gereksinimleri karşılayan herhangi bir nesne içerebilir. Bu nesneler içerir <xref:System.Data.DataSet> nesneleri <xref:System.Data.DataTable> nesneleri ve tarafından seri hale getirilebilir herhangi bir nesne <xref:System.Xml.Serialization.XmlSerializer> sınıfı. Daha fazla bilgi için [veriyi önbelleğe alma](../vsto/caching-data.md).  
  
 Önbelleğe alınmış verileri görüntülemenizi sağlamak için Windows Forms denetimlerine bağlayabilirsiniz ve *konak denetimlerini* belgesinde nesnelere veri adası içinde. Veri adası verilere bağlı denetimler arasında veri bağlamayı ikisini eşitler. Ayrıca, denetimleri bağımsız veri doğrulama kodu ekleyebilirsiniz. Daha fazla bilgi için [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Konak denetimleri, Excel ve Word nesne modellerinde yerel nesnelerin sürümleri genişletilir. Yerel nesnelerden farklı olarak, konak denetimleri yönetilen veri nesnelerine doğrudan bağlı olabilir. Daha fazla bilgi için [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md) ve [Windows Forms denetimleri Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="access-cached-data-on-the-server"></a>Sunucuda verileri önbelleğe erişim  
 Bir belgede önbelleğe alınan verilere erişmek için kullanabileceğiniz <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfı. Bu sınıf, parçasıdır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], ve bir sunucuda çalışan Excel veya Word'den olmadan kullanılabilir. Ne zaman önbelleğe alınmış verileri değiştirmek için verilere bağlı herhangi bir denetim değişiklikleri otomatik olarak eşitlenir ve kullanıcıya güncelleştirilen verilerle sunulur sonra kullanıcı belgeyi açar. Daha fazla bilgi için [sunucudaki belgelerde verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel ve Word yalnızca istemcide görüntülemek için bu sunucudaki veri yazmak için gerek yoktur. Excel ve Word bile sunucuya yüklenmesi gerekmez. Bu, geliştirilmiş ölçeklenebilirlik ve veri Adaları içeren belgeleri hızlı toplu işlemleri gerçekleştirmenize olanak sağlar.  
  
## <a name="data-caching-for-offline-use"></a>Çevrimdışı kullanım için önbelleğe alma  
 Verileri veri adası içinde depolamak, çevrimdışı senaryolar sağlar. Bir kullanıcı önce bir belgeyi açtığında veya belge sunucudan ister veri adası en son verilerle doldurulur. Veri adası, belgede önbelleğe alınır ve sonra çevrimdışı kullanılabilir olur. Canlı bağlantı kullanılabilir olsa bile kullanıcı (ve kodunuzu) veri işleyebilirsiniz. Kullanıcı bağlandığında, bu verilerdeki değişiklikleri bir sunucu veri kaynağına geri yayılır.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Önbelleğe alınan veriler ve karşılaştırıldığında özel XML bölümleri  
 Özel XML bölümleri 2007 Microsoft Office sistemi bir belgede rasgele XML parçalarının depolamak için bir yol olarak sunulur. Özel XML bölümleri birçok veri önbelleğini aynı senaryolarda yararlı olsa da, veri adası özel XML bölümleri arasındaki bazı farklar vardır. Özel XML bölümleri hakkında daha fazla bilgi için bkz. [özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md).  
  
 Aşağıdaki tabloda bazı benzerlikler ve farklar listelenmektedir.  
  
||Veri önbelleği|Özel XML bölümleri|  
|-|----------------|----------------------|  
|Office uygulamaları bu kullanabilir miyim?|Aşağıdaki uygulamalar için belge düzeyi özelleştirmeleri:<br /><br /> -Excel<br />-Word|Aşağıdaki uygulamalar için belge düzeyi ve uygulama düzeyi Çözümler:<br /><br /> -Excel<br />-PowerPoint<br />-Word|  
|Hangi veri türlerini depolayabilir miyim?|Belirli gereksinimleri karşılayan, özelleştirme bütünleştirilmiş kodu genel nesne. Daha fazla bilgi için [veriyi önbelleğe alma](../vsto/caching-data.md).|Herhangi bir XML verisi.|  
|Microsoft Office uygulamaları başlatmadan verilere erişebilir?|Kullanarak Evet, <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfı tarafından sağlanan [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Evet, de sınıfları kullanarak <xref:System.IO.Packaging> ad veya Open XML biçimi SDK'sını kullanarak.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)   
 [Visual Studio'da Office çözümleri mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  