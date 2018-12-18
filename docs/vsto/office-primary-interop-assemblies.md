---
title: Office birincil birlikte çalışma derlemeleri
ms.custom: ''
ms.date: 09/20/2018
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b44352996c1f6cf343f8100abb4f75814765c22a
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672996"
---
# <a name="office-primary-interop-assemblies"></a>Office birincil birlikte çalışma derlemeleri

Bir Office projesinden bir Microsoft Office uygulamasının özelliklerini kullanmak için uygulama için birincil birlikte çalışma derlemesi (PIA) kullanmanız gerekir. PIA, yönetilen kodun bir Microsoft Office uygulamasının COM tabanlı nesne modeliyle etkileşimini sağlar.  
  
Yeni bir Office projesi oluşturduğunuzda, Visual Studio projesi oluşturmak için gerekli pıa'lara başvuru ekler. Bazı senaryolarda (örneğin, Microsoft Office Excel için Microsoft Office Word'ün bir özelliği projesinde kullanmak istiyorsanız) ek pıa'lara başvuru eklemeniz gerekebilir.  
  
Bu konu, Microsoft Office PIA'ların Office projelerinde kullanılmasıyla ilgili aşağıdaki noktaları açıklar:  
  
- [Derleme ve çalışma projeleri için ayrı birincil birlikte çalışma derlemeleri](#separateassemblies)  
  
- [Tek bir projede birden çok Microsoft Office uygulamasının özelliklerini kullanma](#usingfeatures)  
  
- [Microsoft Office uygulamaları için birincil birlikte çalışma derlemelerinin tam listesi](#pialist)  
  
Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz: [birincil birlikte çalışma derlemelerini](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  

<a name="separateassemblies"></a> 

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Derleme ve çalışma projeleri için ayrı birincil birlikte çalışma derlemeleri  

Visual Studio geliştirme bilgisayarında farklı PIA kümelerini kullanır. Bu farklı derleme kümeleri aşağıdaki konumlarda şunlardır:  
  
- Program dosyaları dizinindeki bir klasör  
  
  Bu kopyaları kod yazarken ve projeler derleme kullanılır. Visual Studio bu derlemeleri otomatik olarak yükler.  
  
- Genel Derleme Önbelleği  
  
  Bu derleme kopyaları, ne zaman çalıştırın veya projelerinde hata ayıklama gibi bazı geliştirme görevleri sırasında kullanılır. Visual Studio değil yükleyin ve bu derlemeler kaydedin; kendi başınıza yapmanız gerekir.  
  
### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Program dosyaları dizinindeki birincil birlikte çalışma derlemeleri  

Visual Studio yüklediğinizde, PIA'lar Genel Derleme Önbelleği dışında dosya sistemindeki bir konuma otomatik olarak yüklenir. Yeni bir proje oluşturduğunuzda, Visual Studio, PIA'ların bu kopyalarına başvuruları projenize otomatik olarak ekler. Visual Studio geliştirme ve projenizi oluştururken tür başvurularını çözümlemek için genel derleme önbelleğindeki derlemeler yerine bu PIA kopyalarını kullanır.  
  
PIA'lerin bu kopyaları, farklı PIA sürümleri genel derleme önbelleğinde kayıtlı olduğunda oluşabilecek bazı geliştirme sorunlarından kaçının Visual Studio yardımcı olur.  
  
Visual Studio PIA'ların bu kopyalarını geliştirme bilgisayarında şu konumlara yükler:  
  
- *%ProgramFiles%\Microsoft office\pıa\office14 için visual Studio 12. 0\visual Studio Tools*  
  
  (veya *% ProgramFiles (x86) %\Microsoft Visual Studio 12. 0\visual Studio Tools for office\pıa\office14* 64-bit işletim sistemlerinde)  
  
- *%ProgramFiles%\Microsoft office\pıa\office15 için visual Studio 12. 0\visual Studio Tools*  
  
  (veya *% ProgramFiles (x86) %\Microsoft Visual Studio 12. 0\visual Studio Tools for office\pıa\office15* 64-bit işletim sistemlerinde)  
  
### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Genel derleme önbelleğinde birincil birlikte çalışma derlemeleri  

Bazı gelişim görevlerini yapmak için PIA'ler yüklenmeli ve geliştirme bilgisayarında genel derleme önbelleğinde kayıtlı. Genellikle PIA, geliştirme bilgisayarına Office yüklediğinizde otomatik olarak yüklenir. Daha fazla bilgi için [Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
Office PIA son kullanıcı bilgisayarlarında Office çözümlerinin çalışması için gerekli değildir. Daha fazla bilgi için [tasarım ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md).  

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Tek bir projede birden çok Microsoft Office uygulamasının özelliklerini kullanma  

Visual Studio'daki her Office proje şablonu, tek bir Microsoft Office uygulaması ile çalışmak üzere tasarlanmıştır. Birden çok Microsoft Office uygulamasının özelliklerini kullanmayı veya bir uygulama veya Visual Studio'da bir proje yok bileşenin özelliklerini kullanmak için gerekli pıa'lara başvuru eklemeniz gerekir.  
  
Çoğu durumda, altında Visual Studio tarafından yüklenen pıa'lara başvuru eklemeniz gerekir `%ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\` dizin. Derlemelerin bu sürümleri görünür **Framework** sekmesinde **başvuru Yöneticisi** iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
Derlemelerin bu sürümleri yüklediyseniz ve PIA'lar genel derleme önbelleğinde kayıtlı görünür **COM** sekmesinde **başvuru Yöneticisi** iletişim kutusu. Bunları kullanırken oluşabilecek bazı geliştirme sorunları olduğundan, derlemelerin bu sürümlerine başvuruları eklemekten kaçının. Genel derleme önbelleğinde PIA'ların farklı sürümlerini kayıtlıysanız, örneğin, projeniz otomatik olarak en son kaydedilen derleme sürümüne bağlanır; üzerinde farklı bir derleme sürümü belirtseniz dahi  **COM** sekmesinde **başvuru Yöneticisi** iletişim kutusu.  
  
> [!NOTE]  
>  Onlara başvuran bir derleme eklendiğinde, bazı derlemeler otomatik olarak projeye eklenir. Örneğin, başvurular *Office.dll* ve *Microsoft.VBE.Interop.dll* derlemelere başvuru Word, Excel, Outlook, Microsoft Forms veya grafik eklediğinizde otomatik olarak eklenir bütünleştirilmiş kodları.  

<a name="pialist"></a> 

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Microsoft Office uygulamaları için birincil birlikte çalışma derlemeleri  

Aşağıdaki tablo, kullanılabilen birincil birlikte çalışma derlemelerini listeler [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  

<br/>

|Office uygulamasi veya bileşeni|Birincil birlikte çalışma derlemesi adı|  
|-------------------------------------|-----------------------------------|  
|Microsoft Access 14.0 Nesne Kitaplığı<br /><br /> Microsoft Access 15.0 Nesne Kitaplığı|Microsoft.Office.Interop.Access.dll|  
|Microsoft Office 14.0 Access veritabanı motoru Nesne Kitaplığı<br /><br /> Microsoft Office 15.0 Access veritabanı motoru Nesne Kitaplığı|Microsoft.Office.Interop.Access.Dao.dll|  
|Microsoft Excel 14.0 Nesne Kitaplığı<br /><br /> Microsoft Excel 15.0 Nesne Kitaplığı|[Microsoft.Office.Interop.Excel.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.excel?view=excel-pia)|  
|Microsoft Graph 14.0 Nesne Kitaplığı (grafikler için PowerPoint, Access ve Word tarafından kullanılır)<br /><br /> Microsoft Graph 15.0 Nesne Kitaplığı|Microsoft.Office.Interop.Graph.dll|  
|Microsoft InfoPath 2.0 tür kitaplığı (yalnızca InfoPath 2007)|[Microsoft.Office.Interop.InfoPath.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.infopath?view=infopath-form)|  
|Microsoft InfoPath XML Interop derleme (yalnızca InfoPath 2007 için)|Microsoft.Office.Interop.InfoPath.Xml.dll|  
|Microsoft Office 14.0 Nesne Kitaplığı (Paylaşılan Office işlevselliği)<br /><br /> Microsoft Office 15.0 Nesne Kitaplığı (Paylaşılan Office işlevselliği)|Office.dll|  
|Microsoft Office Outlook Görünüm Denetimi (Web sayfaları ve uygulamalarında, gelen kutunuza erişmek için kullanılabilir)|Microsoft.Office.Interop.OutlookViewCtl.dll|  
|Microsoft Outlook 14.0 Nesne Kitaplığı<br /><br /> Microsoft Outlook 15.0 Nesne Kitaplığı|[Microsoft.Office.Interop.Outlook.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia)|  
|Microsoft PowerPoint 14.0 Nesne Kitaplığı<br /><br /> Microsoft PowerPoint 15.0 Nesne Kitaplığı|Microsoft.Office.Interop.PowerPoint.dll|  
|Microsoft Project 14.0 Nesne Kitaplığı<br /><br /> Microsoft Project 15.0 Nesne Kitaplığı|[Microsoft.Office.Interop.MSProject.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.msproject?view=office-project-server)|  
|Microsoft Publisher 14.0 Nesne Kitaplığı<br /><br /> Microsoft Publisher 15.0 Nesne Kitaplığı|Microsoft.Office.Interop.Publisher.dll|  
|Microsoft SharePoint Designer 14.0 Web nesne başvuru kitaplığı|Microsoft.Office.Interop.SharePointDesigner.dll|  
|Microsoft SharePoint Designer 14.0 sayfa nesne başvuru kitaplığı|Microsoft.Office.Interop.SharePointDesignerPage.dll|  
|Microsoft akıllı etiketler 2.0 tür kitaplığı **Not:** akıllı etiketlerin kullanımı terk içinde [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] ve [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Microsoft.Office.Interop.SmartTag.dll|  
|Microsoft Visio 14.0 tür kitaplığı<br /><br /> Microsoft Visio 15.0 tür kitaplığı|Microsoft.Office.Interop.Visio.dll|  
|Microsoft Visio 14.0 Web tür kitaplığı olarak Kaydet<br /><br /> Microsoft Visio 15.0 Web tür kitaplığı olarak Kaydet|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|  
|Microsoft Visio 14.0 çizim denetimi tür kitaplığı<br /><br /> Microsoft Visio 15.0 çizim denetimi tür kitaplığı|Microsoft.Office.Interop.VisOcx.dll|  
|Microsoft Word 14.0 Nesne Kitaplığı<br /><br /> Microsoft Word 15.0 Nesne Kitaplığı|[Microsoft.Office.Interop.Word.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.word?view=word-pia)|  
|Microsoft Visual Basic, uygulama genişletilebilirliği 5.3|Microsoft.VBE.Interop.dll|  
  
### <a name="binding-redirect-assemblies"></a>Bağlama yeniden yönlendirme derlemeleri  

Yüklediğinizde ve Office PIA'larını genel derleme önbelleğinde (ya da Office ile veya Pıa'lara ilişkin yeniden dağıtılabilir paketi yükleyerek) kaydetme bağlama yeniden yönlendirme derlemeleri de yalnızca genel derleme önbelleğine yüklenir. Bu derlemeler, birincil birlikte çalışma derlemelerini doğru sürümünün çalışma zamanında yüklendiğinden emin olun yardımcı olur. 

Örneğin, ne zaman başvuran bir çözüm bir [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] derlemesi olan bir bilgisayarda çalışan [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aynı birincil birlikte çalışma bütünleştirilmiş kod sürümü, bağlama yeniden yönlendirme derlemesi bildirir [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] yüklenecek çalışma zamanı [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] birincil birlikte çalışma bütünleştirilmiş kod sürümü. 

Daha fazla bilgi için [nasıl yapılır: otomatik bağlama yeniden yönlendirmesini devre](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).  
  
## <a name="see-also"></a>Ayrıca bkz.  

- [Nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)   
- [InfoPath çözümleri](../vsto/infopath-solutions.md)   
- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)   
- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)   
- [Proje çözümleri](../vsto/project-solutions.md)   
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)   
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)   
- [Genel başvuru &#40;Visual Studio'da Office geliştirme&#41;](../vsto/general-reference-office-development-in-visual-studio.md)  
  
  
