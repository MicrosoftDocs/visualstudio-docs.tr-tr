---
title: Visio nesne modeline genel bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 872665a9af220e1b86a3d053254880e3ababa6cd
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671410"
---
# <a name="visio-object-model-overview"></a>Visio nesne modeline genel bakış
  Office çözümleri geliştirmek için Microsoft Office Visio için Visio nesne modeli ile etkileşim kurabilir. Bu nesne modeli sınıfları ve arabirimleri Visio için birincil birlikte çalışma derlemesi olarak sağlanır ve tanımlanan oluşur `Microsoft.Office.Interop.Visio` ad alanı.  
  
 Bu konu, Visio nesne modeline kısa bir genel bakış sağlar. Visio nesne modeline Office projelerinde görevleri gerçekleştirmek için kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Visio belgeleriyle çalışma](../vsto/working-with-visio-documents.md)  
  
-   [Visio şekilleri ile çalışma](../vsto/working-with-visio-shapes.md)  
  
## <a name="understand-the-visio-object-model"></a>Visio nesne modelini anlama  
 Visio birçok nesne ile etkileşim sağlar. Kullanıcı arabirimi yakından takip eden bir hiyerarşide bu nesneleri düzenlenir. Hiyerarşisinin en üstünde olan [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) nesne. Bu nesne, Visio'nün geçerli örneğini temsil eder. `Microsoft.Office.Interop.Visio.Application` Nesnesini içeren `Microsoft.Office.Interop.Visio.Document` ve `Microsoft.Office.Interop.Visio.Page` nesnelerin yanı sıra `Microsoft.Office.Interop.Visio.Documents` ve `Microsoft.Office.Interop.Visio.Pages` koleksiyonları. Her bu nesneleri ve koleksiyonları, birçok yöntem ve ve onunla etkileşime için erişebileceği özellikler vardır.  
  
 Daha fazla bilgi için bkz: VBA başvuru belgelerine [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document), ve [ Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) nesneleri ve ayrıca [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) ve [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) koleksiyon.  
  
 Aşağıdaki bölümlerde, en üst düzey nesnelerin ve birbiriyle nasıl etkileşim kurduklarını kısaca açıklanmaktadır. Bu nesneler, aşağıdaki nesneler içerir:  
  
-   Uygulama nesnesi  
  
-   Belge nesnesi  
  
-   Sayfa nesnesi  
  
### <a name="application-object"></a>Uygulama nesnesi  
 Microsoft.Office.Interop.Visio.Application nesnesi, Visio uygulamasını temsil eder ve tüm diğer nesnelerin üst. Üyeleri, Visio genellikle bir bütün olarak uygular. Özellikleri ve yöntemleri Microsoft.Office.Interop.Visio.Application kullanabilirsiniz ve `Microsoft.Office.Interop.Visio.ApplicationSettings` Visio ortam denetlemek için nesneleri.  
  
 VSTO eklentisi projelerinde Microsoft.Office.Interop.Visio.Application nesnesi kullanarak erişebilirsiniz `Application` alanını `ThisAddIn` sınıfı. Daha fazla bilgi için [programlama VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
### <a name="document-object"></a>Belge nesnesi  
 Programlama Visio'ya merkezi Microsoft.Office.Interop.Visio.Document nesnedir. Çizim, şablon veya şablon dosyasını temsil eder. Bir Visio belgesini açın veya yeni bir belge oluşturun, Microsoft.Office.Interop.Visio.Application nesnesi Microsoft.Office.Interop.Visio.Documents koleksiyonuna eklenen yeni bir Microsoft.Office.Interop.Visio.Document nesne oluşturma .  
  
 Odağı olan belgeyi etkin belgeyi çağrılır. Tarafından temsil edilen `Microsoft.Office.Interop.Visio.Application.ActiveDocument` Microsoft.Office.Interop.Visio.Application nesnesinin özelliği.  
  
### <a name="page-object"></a>Sayfa nesnesi  
 Microsoft.Office.Interop.Visio.Page nesne bir ön plan veya arka plan sayfası çizim alanını temsil eder. Kullanabileceğiniz `Microsoft.Office.Interop.Visio.Page.Background` özellik sayfa ön plan veya arka plan sayfa olup olmadığını belirlemek için.  
  
 Şekil oluşturmak için içeren yöntemleri kullanabilirsiniz `Microsoft.Office.Interop.Visio.Page.DrawSpline` ve `Microsoft.Office.Interop.Visio.Page.DrawOval` yöntemleri. Ayrıca, kalıp örnekleri alabilir ve kullanarak bir sayfada şekilleri Yerleştir `Microsoft.Office.Interop.Visio.Page.Drop` veya `Microsoft.Office.Interop.Visio.Page.DropMany` yöntemleri.  
  
## <a name="use-the-visio-object-model-documentation"></a>Visio nesne modeli belgeleri kullanın  
 Visio nesne modeli hakkında tam bilgi için Visio VBA nesne modeli başvurusu başvurabilir. Visual Basic for Applications (VBA) kodundaki sunulur şekilde VBA nesne modeli başvurusu Visio nesne modeline listelenmiştir. Daha fazla bilgi için [Visio 2010 nesne modeli başvurusu](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Tüm nesnelerin ve üyelerin VBA nesne modeli başvurusu türlerine ve üyelerine Visio birincil birlikte çalışma derlemesi (PIA) karşılık gelir. Örneğin, `Document` VBA nesne modeli başvurusu nesnesinde Visio PIA Microsoft.Office.Interop.Visio.Document türü karşılık gelir. VBA nesne modeli başvurusu çoğu özellikleri, yöntemleri ve olayları için kod örnekleri sağlasa da bu başvuru Visual Basic veya Visual VBA kodu çevir C# bunları kullanarak oluşturduğunuz bir Visio VSTO eklenti projesinde kullanmak istiyorsanız Visual Studio.  
  
> [!NOTE]  
>  Şu anda Visio birincil birlikte çalışma derlemesi için başvuru belgeleri yoktur.  
  
 İlgili kod örnekleri ve Visio çözümleri oluşturmak için ek araçlar için bkz: [Visio 2010 Yazılım Geliştirme Seti](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### <a name="additional-types-in-primary-interop-assemblies"></a>Ek birincil birlikte çalışma bütünleştirilmiş kodlar içindeki türleri  
 Uygulama farklar nedeniyle VBA'ya görünür olmayan birincil birlikte çalışma bütünleştirilmiş kodlarında türler bulabilirsiniz. VBA yalnızca nesneleri ve doğrudan kullanabileceğiniz üyeleri içerir Visio nesne modeline genel bir görünümünü sağlar. Birincil birlikte çalışma derlemeleri, aynı nesne modelini kullanıma sunar, ancak bunlar diğer arabirimler, sınıflar ve yönetilen koda COM nesne modelinde Çevir üyeleri de içerir. Bu ek öğeler kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.  
  
 Daha fazla bilgi için [sınıflar ve arabirimler Office birincil birlikte çalışma derlemelerindeki genel bakış](http://go.microsoft.com/fwlink/?LinkId=189592) ve [Office birincil birlikte çalışma derlemelerini](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visio çözümleri](../vsto/visio-solutions.md)   
 [Visio belgeleriyle çalışma](../vsto/working-with-visio-documents.md)   
 [Visio şekilleri ile çalışma](../vsto/working-with-visio-shapes.md)  
  
  