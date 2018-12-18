---
title: Özel XML bölümlerine genel bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 71720ef96ee7d17bd52ea118a8c44a8f4b117cad
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671735"
---
# <a name="custom-xml-parts-overview"></a>Özel XML bölümlerine genel bakış
  Bazı Microsoft Office uygulamaları için belgelerde XML veri ekleyebilir. Bir belgedeki XML verileri ekleme, veriler adlı bir *özel XML bölümleri*.  
  
 Oluşturabilir ve VSTO eklentisi kullanarak özel XML bölümleri belgede değiştirmek veya belge düzeyi Visual Studio'da çözüm. Microsoft Office uygulamasının özel XML bölümleri oluşturup başlatmak gerekmez.  
  
 **İçin geçerlidir:** Bu konu başlığı altındaki bilgiler Excel, PowerPoint ve Word için belge düzeyi projelerine ve VSTO eklentisi projelerine yöneliktir. Daha fazla bilgi için [Office uygulaması ve proje türüne göre kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio ayrıca, veri nesnelerini belge düzeyi özelleştirmelerdeki önbelleğe sağlar. Bazı benzerlikler olsa bu özel XML bölümleri, farklı bir özelliğidir. Daha fazla bilgi için [veri belge düzeyi özelleştirmelerdeki önbelleğe alınmış](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understand-custom-xml-parts"></a>Özel XML bölümleri anlama  
 Özel XML bölümleri 2007 Microsoft Office sistemindeki açık XML Biçimleri birlikte sunulur. Bu yeni XML tabanlı bir dosya biçimleri Excel, PowerPoint ve Word için biçimler (gibi *.xlsx*, *.pptx*, ve *.docx*). Bu biçimlerdeki belgeler oluşur XML dosyaları (olarak da adlandırılan *XML bölümleri*) ZIP arşivindeki klasörlerde düzenlenir. XML bölümleri çoğunu, yapısı ve belge durumunu tanımlamanıza yardımcı olur yerleşik bölümleri şunlardır. Bununla birlikte, belgeleri belgelerde rasgele XML verilerini depolamak için kullanabileceğiniz özel XML bölümleri de içerebilir.  
  
 Eski bir ikili dosya biçimleri ile mümkün olmayan bir yolla belgelerle çalışmak üzere etkinleştirme uygulamaları XML dosya biçimleri (gibi *.xls*, *.ppt*, ve *.doc*). ZIP arşivlerini okuyan herhangi bir uygulama, inceleyin ve Microsoft Office yüklü olsa bile, belge içeriklerini değiştirin.  
  
 Open XML ve özel XML bölümleri yapısı hakkında daha fazla bilgi için aşağıdaki makalelere bakın:  
  
-   [Office (2007) Open XML dosya biçimleri](/previous-versions/office/developer/office-2007/aa338205(v=office.12))  
  
-   [Nasıl yapılır: Açık XML Biçimleri belgelerini değiştirme](/previous-versions/office/developer/office-2007/aa982683(v=office.12))  
  
-   [İzlenecek yol: Word 2007 XML biçimi](/previous-versions/office/developer/office-2007/bb266220(v=office.12))  
  
-   [Word 2007 belgelerini açık XML biçimleri kullanarak derleme](/previous-versions/office/developer/office-2007/bb264572(v=office.12))  
  
> [!NOTE]  
>  Ayrıca Excel, Word ve PowerPoint ikili dosya biçimlerinde kaydedilir belgelerde özel XML bölümleri kullanmanıza olanak sağlar. Ancak, ikili biçimde bir belge kaydedilirse, ekleyemez veya Microsoft Office uygulamasını başlatmadan özel XML bölümleri değiştirin.  
  
## <a name="create-and-modify-custom-xml-parts"></a>Oluşturma ve değiştirme özel XML bölümleri  
 Oluşturabilir veya belgeyi Office uygulamasında açık olduğunda ya da belge kapatıldığında özel XML bölümleri değiştirmek — bile Microsoft Office yüklü değil.  
  
### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Office uygulama çalışırken XML bölümlerini Değiştir  
 Belge düzeyinde özelleştirme veya bir VSTO eklentisi kullanarak özel XML bölümleri ile çalışabilirsiniz. Belge düzeyi özelleştirmesi kullanıyorsanız, genellikle özelleştirilmiş belgeye özel XML bölümleri ile çalışır. Bir VSTO eklenti kullanıyorsanız, oluşturun veya özel XML bölümleri uygulamada açık olan herhangi bir belgedeki değiştirin.  
  
 Visual Studio kullanarak özel XML parçaları oluşturmak için yeni bir ekleme <xref:Microsoft.Office.Core.CustomXMLPart> için <xref:Microsoft.Office.Core.CustomXMLParts> belgedeki koleksiyonu. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Nasıl yapılır: VSTO eklentileri kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modify-xml-parts-without-starting-the-office-application"></a>Office uygulamasını başlatmadan XML bölümlerini Değiştir  
 Ekleyebilir veya Excel, PowerPoint ve Word başlatmadan özel bir XML parçasına değiştirebilirsiniz. Bu, yüklü bir sunucu gibi Microsoft Office uygulamalarının yüklü olmadığı bir bilgisayarda, bir belgedeki XML verileriyle çalışmak istiyorsanız kullanışlıdır.  
  
 Microsoft Office başlatmadan özel XML bölümleri ekleme için sınıflar açık XML SDK'yı kullanın. Bu sınıflar, Office belgeleri için özel bir Open XML içeriğe erişim sağlamak üzere tasarlanmıştır. Örneğin, bir Excel çalışma kitabına özel bir XML parçasına eklemek için kullandığınız <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> yöntemi bir <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> nesne. Daha fazla bilgi için [açık XML SDK](/office/open-xml/open-xml-sdk).  
  
## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Word içerik denetimlerini özel XML bölümlerine bağlama  
 İçerik denetimleri bir sözcük çözüme özel bir XML parçasına öğeleri bağlayabilirsiniz. Bir içerik denetimi için özel bir XML parçasına bağlı olduğunda özel bir XML parçasına verileri içerik denetimi kullanıcı arabiriminde (UI) görüntülenir. Karşılık gelen XML öğesi, bir kullanıcı denetiminde metin düzenlerse, otomatik olarak güncelleştirilir. Benzer şekilde, özel XML bölümleri içindeki öğe değerlerini değiştirdiyseniz, XML öğelerine bağlanan içerik denetimlerini yeni verileri görüntüleyin. Daha fazla bilgi için [içerik denetimleri](../vsto/content-controls.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [XML şemaları ve belge düzeyi özelleştirmelerdeki veriler](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Nasıl yapılır: VSTO eklentileri kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [İçerik denetimleri](../vsto/content-controls.md)   
 [İzlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
