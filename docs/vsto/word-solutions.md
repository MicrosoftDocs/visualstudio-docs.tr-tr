---
title: Word çözümleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2b443cd985910cbb6e81ce79016193623bdeb2dd
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676907"
---
# <a name="word-solutions"></a>Word çözümleri
  Visual Studio, Microsoft Office Word için belge düzeyi özelleştirmeleri ve VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. Word'ü otomatikleştirmek, Word özelliklerini genişletmek ve Word kullanıcı arabirimini (UI) özelleştirmek için bu çözümleri kullanabilirsiniz. Belge düzeyi özelleştirmeleri ve VSTO eklentileri arasındaki farklar hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümlerle karşılaştırıldığında küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  
  
 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:  
  
-   [Word'ü otomatikleştirirken](#automating).  
  
-   [Word için belge düzeyi özelleştirmeleri geliştirme](#doclevel).  
  
-   [Word için VSTO eklentileri geliştirme](#applevel).  
  
-   [Word kullanıcı arayüzünü özelleştirme](#UI).  
  
##  <a name="automating"></a> Sözcük otomatikleştirme  
 Word nesne modeli, Word'ü otomatikleştirirken kullanabileceğiniz birçok türü ortaya çıkarır. Örneğin, program aracılığıyla tablolar oluşturabilir, biçim belgeleri ve aralık ve paragraflardaki metni ayarlama. Daha fazla bilgi için [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md).  
  
 Visual Studio'da Word çözümleri geliştirirken aynı zamanda kullanabilirsiniz *konak öğelerini* ve *konak denetimlerini* Çözümlerinizdeki. Bunlar gibi Word nesne modeli, yaygın olarak kullanılan belirli nesneleri genişleten nesnelerdir <xref:Microsoft.Office.Interop.Word.Document> ve <xref:Microsoft.Office.Interop.Word.ContentControl> nesneleri. Genişletilmiş nesneler temel aldıkları Word nesneleri gibi davranırlar fakat nesnelere veri bağlama becerileri ve ek olaylar ekleyin. Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Word'ü](../vsto/automating-word-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Word için belge düzeyi özelleştirmeleri geliştirme  
 Microsoft Office Word için belge düzeyi özelleştirmesinde, belirli bir belge ile ilişkilendirilen derleme oluşur. Derleme, genellikle UI'yi özelleştirerek ve Word'ü otomatikleştirerek belgeyi genişletir. Yalnızca ilişkili belge Word'de açık olduğunda bir VSTO Word'ün kendisiyle ilişkilendirilen eklentiyi bir özelleştirmede uyguladığınız işlevsellik kullanılabilir.  
  
 Word için belge düzeyi özelleştirme projesi oluşturmak için Word belgesi veya Word Şablonu proje şablonlarını kullanın. **yeni proje** Visual Studio'nun iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Belge düzeyi özelleştirmelerinin hakkında daha fazla bilgi için [belge düzeyi özelleştirmeler mimarisi](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="word-customization-programming-model"></a>Word özelleştirme programlama modeli  
 Word için belge düzeyi projesi oluşturduğunuzda, Visual Studio isimli bir sınıf oluşturur. `ThisDocument`, çözümünüzün temeli. Bu sınıf çözümünüzle ilişkilendirilmiş belgeyi temsil eder ve kodunuzu yazmanız için bir başlangıç noktası sağlar.  
  
 Hakkında daha fazla bilgi için `ThisDocument` sınıfı ve bir belge düzeyi projesinde kullanabileceğiniz diğer özellikler bkz [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Word için VSTO eklentileri geliştirin  
 Microsoft Office Word'ün bir VSTO eklentisi Word tarafından yüklenen bir derleme içerir. Derleme, genellikle UI'yi özelleştirerek ve Word'ü otomatikleştirerek Word genişletir. Belirli bir belge ile ilişkilendirilen belge düzeyi özelleştirmesinin aksine bir VSTO eklentide uyguladığınız işlevsellik, herhangi bir tek belge ile sınırlı değildir.  
  
 Word için VSTO eklentisi projesi oluşturmak için Word eklentisi proje şablonlarını kullanın **yeni proje** Visual Studio'nun iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 VSTO eklentileri nasıl çalıştığı hakkında genel bilgi için bkz. [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="word-add-in-programming-model"></a>Word eklenti programlama modeli  
 Bir sözcük VSTO eklenti projesi oluşturduğunuzda, Visual Studio isimli bir sınıf oluşturur. `ThisAddIn`, çözümünüzün temeli. Bu sınıf kodunuzu yazmanız için bir başlangıç noktası sağlar ve ayrıca bir VSTO eklenti Word nesne modeli sunar.  
  
 Hakkında daha fazla bilgi için `ThisAddIn` sınıfı ve bir VSTO eklenti, kullanabileceğiniz diğer özellikler bkz [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Word kullanıcı arayüzünü özelleştirme  
 Word kullanıcı arayüzünü özelleştirmek için birçok farklı yol vardır. Bazı seçenekleri tüm proje türleri için kullanılabilir ve diğer seçenekleri yalnızca VSTO eklentileri veya belge düzeyi özelleştirmeleri için kullanılabilir.  
  
### <a name="options-for-all-project-types"></a>Tüm proje türleri için Seçenekler  
 Aşağıdaki tabloda, hem belge düzeyi özelleştirmeleri ve VSTO eklentileri için kullanılabilen seçenekleri listeler.  
  
|Görev|Daha fazla bilgi için|  
|----------|--------------------------|  
|Şeridi özelleştirme.|[Şerite Genel Bakış](../vsto/ribbon-overview.md)|  
|Windows Forms veya genişletilmiş Word denetimleri, özelleştirilmiş belgeye (belge düzeyi özelleştirmeleri için) veya herhangi bir açık belgeye (bir VSTO eklenti için) ekleyin.|[Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Nasıl yapılır: Word belgelerine yer işareti denetimi ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|  
  
### <a name="options-for-document-level-customizations"></a>Belge düzeyi özelleştirmeleri seçenekleri  
 Aşağıdaki tabloda, yalnızca belge düzeyi özelleştirmeleri tarafından kullanılabilen seçenekleri listeler.  
  
|Görev|Daha fazla bilgi için|  
|----------|--------------------------|  
|Belgeye eylemler bölmesi ekleme.|[Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)<br /><br /> [Nasıl yapılır: Word belgelerine Eylemler bölmesi ekleme veya Excel çalışma kitapları](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Belge yüzeyine genişletilmiş XMLNode ve XMLNodes denetimleri ekleme.|[Nasıl yapılır: Word belgelerine XMLNode denetimleri ekleme](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Nasıl yapılır: Word belgelerine XMLNodes denetimleri ekleme](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|  
  
### <a name="options-for-vsto-add-ins"></a>VSTO eklentileri için seçenekleri  
 Aşağıdaki tabloda yalnızca VSTO eklentileri için kullanılabilen seçenekleri listeler.  
  
|Görev|Daha fazla bilgi için|  
|----------|--------------------------|  
|Özel görev bölmesi oluşturun.|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)|Word nesne modeli tarafından sağlanan ana türlerine genel bir bakış sağlar.|  
|[Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)|Genişletilmiş nesneler hakkında bilgi sağlar (tarafından sağlanan [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) Word çözümleri kullanabileceğiniz.|  
|[Windows Forms denetimlerine Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)|Word belgelerine Windows Forms denetimlerini nasıl ekleyebileceğinizi açıklar.|  
|[İzlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Word için temel bir belge düzeyi özelleştirmeyi oluşturma işlemini gösterir.|  
|[İzlenecek yol: Word için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Word için basit bir VSTO eklentisi oluşturma işlemini gösterir.|  
|[İzlenecek yol: bir belgeye çalışma zamanında VSTO eklenti denetimler ekleme](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Bir Windows eklemek için Forms düğmesinin ve gösterir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> belgeye çalışma zamanında VSTO eklenti kullanarak.|  
|[Ofis geliştirmede Word 2010](http://go.microsoft.com/fwlink/?LinkId=199020)|Makaleler ve Word çözümleri (Visual Studio kullanarak Office geliştirmeye özgü olmayan) geliştirme hakkında başvuru belgelerine bağlantılar sağlar.|  
  
  