---
title: Office çözümlerinde kod yazma
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e9773c06293f189e572ef84e9b10f45a1ca5d5d8
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670994"
---
# <a name="write-code-in-office-solutions"></a>Office çözümlerinde kod yazma
  Visual Studio'da proje türlerinde farklı Office projelerinde kod yazma bazı yönlerini vardır. Bu farklılıkların birçoğu, Office nesne modelleri, yönetilen kod için sunulan şekilde ilgilidir. Diğer farklar Office projeleri tasarımını ilgilidir.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="managed-code-and-office-programming"></a>Yönetilen kod ve Office programlama  
 Tümleşik Microsoft Office çözümünü oluşturmak mümkün kılan anahtar Bileşen Nesne Modeli (COM) teknolojisi parçası olan Otomasyon teknolojisidir. Otomasyon oluşturma ve herhangi bir uygulama tarafından DLL, kullanıma sunulan yazılım nesnelerini denetlemek için kod kullanmanıza olanak sağlar veya ActiveX denetimi uygun programlama arabirimleri destekler.  
  
### <a name="understand-primary-interop-assemblies"></a>Birincil birlikte çalışma derlemelerini anlama  
 Microsoft Office uygulamaları, işlevlerinin çoğunu kullanıma sunar. Ancak, doğrudan Office uygulamalarını otomatikleştirmek için yönetilen kod (örneğin, Visual Basic veya C#) kullanamazsınız. Yönetilen kod kullanarak Office uygulamalarını otomatikleştirmek için Office birincil birlikte çalışma derlemeleri (PIA) kullanmanız gerekir. Birincil birlikte çalışma derlemelerini yönetilen kodun Office uygulamasının COM tabanlı nesne modeliyle etkileşimini sağlar.  
  
 Her Microsoft Office uygulamasının PIA sahiptir. Visual Studio'da bir Office projesi oluşturduğunuzda, uygun PIA başvurusu otomatik olarak projeye eklenir. Diğer Office uygulamalarından Proje özelliklerinin otomatikleştirmek için uygun PIA başvurusu el ile eklemeniz gerekir. Daha fazla bilgi için [nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Birincil birlikte çalışma derlemelerini tasarım zamanı ve çalışma zamanı kullanın  
 Office yüklü ve uygulamanızı geliştirme bilgisayarınızın genel derleme önbelleğinde kayıtlı çoğu geliştirme görevlerinin gerçekleştirilebilmek için PIA'ların olması gerekir. Daha fazla bilgi için [Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 Office PIA'ların son kullanıcı bilgisayarlarında Office çözümlerini hedefleyen çalıştırmak için gerekli değildir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri. Daha fazla bilgi için [tasarım ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="use-types-in-primary-interop-assemblies"></a>Birincil birlikte çalışma bütünleştirilmiş kodlarında türlerini kullanın  
 Office PIA'ların Office uygulamalarını nesne modelini açığa çıkaran türleri ve doğrudan kodunuzda kullanılması amaçlanmamıştır ek altyapı türleri birleşimini içerir. Office PIA'ların türlerinde genel bakış için bkz: [sınıflar ve arabirimler Office birincil birlikte çalışma derlemelerindeki genel bakış](/previous-versions/office/office-12/ms247299\(v\=office.12\)).  
  
 Office PIA'ların türleri COM tabanlı nesne modellerinde türlere karşılık geldiğinden, bu tür şekilde genellikle diğer yönetilen türleri farklıdır. Örneğin, Office birincil birlikte çalışma derlemesi isteğe bağlı parametrelere sahip yöntemleri çağırma yolunuz projenizde kullandığınız programlama diline bağlıdır. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md).  
  
-   [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md).  
  
## <a name="program-model-of-office-projects"></a>Office projeleri program modeli  
 Tüm Office projeleri, kodunuz için giriş noktası sağlayan bir veya daha fazla oluşturulan sınıflar içerir. Bu sınıflar, konak uygulamanın nesne modeline erişim ve Eylemler bölmesi ve özel görev bölmeleri gibi özelliklerine erişim olanağı da sağlar.  
  
### <a name="understand-the-generated-classes"></a>Oluşturulan sınıflar anlama  
 Excel ve Word için belge düzeyinde projelerde oluşturulan sınıfın bir üst düzey nesnesi uygulamanın nesne modelinde benzer. Örneğin, oluşturulan `ThisDocument` sınıfta bir Word belgesi projesi olarak aynı üyelere <xref:Microsoft.Office.Interop.Word.Document> Word nesne modelinde sınıfı. Belge düzeyinde projelerde oluşturulan sınıflar hakkında daha fazla bilgi için bkz: [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).  
  
 VSTO eklentisi projelerine adında oluşturulmuş bir sınıf sağlamanız `ThisAddIn`. Bu sınıf, bir sınıf konak uygulamanın nesne modelinde benzemez. Bunun yerine, bu sınıf, VSTO eklentisi kendisini temsil eder ve konak uygulamanın nesne modeline erişme ve VSTO eklentileri kullanılabilir diğer özelliklerine erişmek için kullanabileceğiniz üyeleri sağlar. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
 Office projelerindeki tüm oluşturulan sınıfları `Startup` ve `Shutdown` olay işleyicileri. Kod yazmaya başlamak için genellikle bu olay işleyicilerine kod eklemeniz gerekir. VSTO eklenti başlatmak için kod ekleyebilirsiniz `Startup` olay işleyicisi. VSTO eklenti tarafından kullanılan kaynakları temizlemek için kod ekleyebilirsiniz `Shutdown` olay işleyicisi. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
### <a name="access-the-generated-classes-at-runtime"></a>Oluşturulan sınıflar, çalışma zamanında erişme  
 Office çözümünü yüklendiğinde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] her oluşturulan sınıflar, projenizdeki bir örneğini oluşturur. Kullanarak, projenizdeki herhangi bir kodu bu nesnelere erişebilirsiniz `Globals` sınıfı. Örneğin, kullanabileceğiniz `Globals` kodu çağırmak için sınıf `ThisAddIn` bir olay işleyicisi sınıfının bir VSTO eklentisi bir Şerit düğmesini.  
  
 Daha fazla bilgi için [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="namespace-considerations-in-office-solutions"></a>Office çözümlerinde Namespace konuları  
 Değiştiremezsiniz *varsayılan ad alanı* (veya *kök ad alanı* Visual Basic'te), projeyi oluşturduktan sonra bir Office projesi. Varsayılan ad alanı her zaman proje oluşturulduğunda, belirtilen proje adı eşleşir. Projenizi yeniden adlandırırsanız, varsayılan ad alanı değiştirmez. Projelerinde varsayılan ad alanı hakkında daha fazla bilgi için bkz. [uygulama sayfası, Proje Tasarımcısı &#40;C&#35; &#41; ](/visualstudio/ide/reference/application-page-project-designer-csharp) ve [uygulama sayfası, Proje Tasarımcısı &#40;Visual Basic&#41; ](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>C# projelerinde, ana bilgisayar öğesi sınıflarının ad alanını değiştirme  
 Ana bilgisayar öğesi sınıflarının (örneğin, `ThisAddIn`, `ThisWorkbook`, veya `ThisDocument` sınıfları) Visual C# Office projelerinde kendi isim uzaylarını sahip. Varsayılan olarak, projeyi oluşturduğunuzda, belirtilen proje adı, projenizdeki ana bilgisayar öğeleri için ad alanı ile eşleşir.  
  
 Visual C# Office projesinde ana bilgisayar öğesi ad alanı değiştirmek için kullanın **Namespace for Host Item** özelliği. Daha fazla bilgi için [Office projelerinde Özellikler](../vsto/properties-in-office-projects.md).  
  
## <a name="supported-programming-languages-in-office-projects"></a>Office projelerinde desteklenen programlama dilleri  
 Visual Studio'da Office proje şablonları yalnızca Visual Basic ve Visual C# programlama dillerini destekler. Bu nedenle, bu proje şablonları yalnızca altında kullanılabilir **Visual Basic** ve **Visual C#** düğümlerinin **yeni proje** iletişim kutusunda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="language-choice-and-office-programming"></a>Dil Seçimi ve Office programlama  
 Microsoft Office ve Visual Basic for Applications (VBA) uygulama özelleştirme iş akışını iyileştirmek için birlikte çalışmak üzere geliştirilmiştir. Visual Basic bu geliştirmelerin bazılarını devralınan izinlere sahip. Örneğin, Visual Basic, Visual C# kullandığınızda daha Microsoft Office birincil birlikte çalışma derlemelerindeki bazı yöntemleri çağrılırken daha az kod yazabilirsiniz anlamına gelir isteğe bağlı parametreleri destekler.  
  
## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Visual Basic vs ile program. Visual C# Office çözümleri  
 Visual Basic veya Visual C# kullanarak Office çözümleri oluşturabilirsiniz. Microsoft Office nesne modelleri ile Microsoft Visual Basic for Applications (VBA) kullanılmak üzere tasarlanmış olması nedeniyle, Visual Basic geliştiricileri rahatça Microsoft Office uygulamaları tarafından oluşturulan nesneleri ile çalışabilirsiniz. Visual C# geliştiricileri, Visual Basic geliştiricilerinin aynı özelliklerin çoğunu kullanabilirsiniz, ancak burada oldukları Office nesne modelini kullanmak için ek kod yazmanız gereken bazı durumlar vardır. Ofis geliştirmede temel programlama özelliklerini ve Visual Basic ve C# içinde yazılan yönetilen koda arasındaki bazı farklar vardır.  
  
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Visual Basic ve Visual C# arasındaki farklar  
 Aşağıdaki tabloda Office geliştirme Visual Basic ve Visual C# arasındaki temel farklar gösterilmektedir.  
  
|Özellik|Açıklama|Visual Basic desteği|Visual C# desteği|  
|-------------|-----------------|--------------------------|------------------------|  
|İsteğe bağlı parametreler|Birçok Microsoft Office yöntemi yöntemi çağırdığınızda, gerekli olmayan parametrelere sahip. Parametre için değer iletilmezse, varsayılan değer kullanılır.|Visual Basic, isteğe bağlı parametreleri destekler.|Visual C# isteğe bağlı parametreler, çoğu durumda destekler. Daha fazla bilgi için [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md).|  
|Parametreleri başvuruya göre geçirme|Microsoft Office birincil birlikte çalışma derlemelerini çoğunu isteğe bağlı parametreler değeri geçirilebilir. Ancak, bazı birincil birlikte çalışma derlemelerindeki, başvuru türlerini kabul eden isteğe bağlı parametreler başvuruya göre geçirilmelidir.<br /><br /> Değer ve başvuru türü parametreleri hakkında daha fazla bilgi için bkz. [bağımsız değişkenleri değere ve başvuruya göre geçirme &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic için) ve [parametreleri geçirmek &#40;C&#35; Programlama Kılavuzu&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|Ek bir iş tarafından başvuru parametreleri geçirmek için gereklidir. Visual Basic Derleyicisi, gerektiğinde başvuruya göre otomatik olarak parametrelerini geçirir.|Çoğu durumda, Visual C# derleyicisini gerektiğinde başvuruya göre otomatik olarak parametrelerini geçirir. Daha fazla bilgi için [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md).|  
|Parametreli özellikler|Bazı özellikler parametreleri kabul eder ve salt okunur işlevler olarak davranır.|Visual Basic parametre kabul eden özellikleri destekler.|Visual C# parametrelerini kabul eden özellikleri destekler.|  
|Geç bağlama|Geç bağlama, nesnelerin özelliklerini tasarım zamanında nesne türüne atama değişkenler yerine, çalışma zamanında belirlenmesi dahildir.|Visual Basic geç bağlamayı gerçekleştirir **Option Strict** kapalıdır. Zaman **Option Strict** açıktır, gerekir açıkça dönüştürmeniz nesneleri ve kullanım türleri <xref:System.Reflection> geç bağlanan üyelere erişim için ad alanı. Daha fazla bilgi için [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md).|Visual C# gerçekleştirir projelerinde hedefleyen geç bağlama [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Daha fazla bilgi için [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md).|  
  
## <a name="key-differences-between-office-development-and-managed-code"></a>Office geliştirme ve yönetilen kod arasındaki farklar  
 Aşağıdaki tabloda Office geliştirme ve Visual Basic veya Visual C# içinde yazılan yönetilen koda arasındaki temel farklar gösterilmektedir.  
  
|Özellik|Açıklama|Visual Basic ve Visual C# desteği|  
|-------------|-----------------|-----------------------------------------|  
|Dizi dizinleri|Microsoft Office uygulamalarında koleksiyonlarının alt dizi sınırı 1 ile başlar. Visual Basic ve Visual C#, 0 tabanlı diziler kullanın. Daha fazla bilgi için [diziler &#40;C&#35; Programlama Kılavuzu&#41; ](/dotnet/csharp/programming-guide/arrays/index) ve [Visual Basic'te diziler](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Microsoft Office uygulamasının nesne modelinde bir koleksiyonun ilk öğesine erişmek için dizin 1 yerine 0 kullanın.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)   
 [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md)   
 [Nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md)   
 [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md)   
 [Office çözümlerinin işbirlikçi geliştirmesi](../vsto/collaborative-development-of-office-solutions.md)  
  
  