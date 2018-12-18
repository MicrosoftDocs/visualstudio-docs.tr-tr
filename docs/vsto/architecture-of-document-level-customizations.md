---
title: Belge düzeyi özelleştirmeler mimarisi
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4e07c8ae29c773a1f50fedd68376a062e2203570
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248276"
---
# <a name="architecture-of-document-level-customizations"></a>Belge düzeyi özelleştirmeler mimarisi
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] Microsoft Office Word ve Microsoft Office Excel için belge düzeyi özelleştirmelerini oluşturmak için projeleri içerir. Bu konu, belge düzeyinde özelleştirmeler şu yönlerini açıklar:  
  
- [Özelleştirmeleri anlama](#UnderstandingCustomizations)  
  
- [Özelleştirmelerin bileşenleri](#Components)  
  
- [Özelleştirmeleri Microsoft Office uygulamaları ile nasıl çalışır?](#HowCustomizationsWork)  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
  Belge düzeyinde özelleştirmeler oluşturma hakkında genel bilgi için bkz. [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md), [Wordiçinbelgedüzeyiözelleştirmeleriniprogramlamakullanmayabaşlayın](../vsto/getting-started-programming-document-level-customizations-for-word.md), ve [Excel için belge düzeyi özelleştirmelerini programlama başlama](../vsto/getting-started-programming-document-level-customizations-for-excel.md).  
  
##  <a name="UnderstandingCustomizations"></a> Özelleştirmeleri anlama  
 Belge düzeyi özelleştirmesi oluşturmak için Visual Studio Office geliştirici araçları kullandığınızda, belirli bir belge ile ilişkilendirilen bir yönetilen kod derlemesi oluşturun. Bir belge veya çalışma kitabıyla bağlantılı bir derleme, yönetilen kod uzantıları bildirilir. Daha fazla bilgi için [tasarım ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md).  
  
 Belgeyi bir kullanıcı oturum açtığında, derleme Microsoft Office uygulaması tarafından yüklenir. Derleme yüklendikten sonra belgeyi açıkken özelleştirme olaylara yanıt verebilir. Özelleştirme otomatikleştirmek ve belge açıksa ve sınıflarda birini kullanabilirsiniz ancak uygulamayı genişletmek için nesne modelini de çağırabilirsiniz [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 Derleme uygulamasının birincil birlikte çalışma derlemesi uygulamanın COM bileşenleriyle iletişim kurar. Daha fazla bilgi için [Office birincil birlikte çalışma derlemelerini](../vsto/office-primary-interop-assemblies.md) ve [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 Her derleme farklı uygulama etki alanında bir kullanıcı aynı anda birden çok belge düzeyi özelleştirmeleri açarsa yüklenir. Başka bir deyişle, hatalı davranan tek bir çözüm diğer çözümlerin başarısız olmasına neden olmayabilir. Belge düzeyi özelleştirmeleri, tek bir uygulama etki alanındaki tek bir belge ile çalışacak şekilde tasarlanmıştır. Belgeler arası iletişim için tasarlanmamıştır. Uygulama etki alanları hakkında daha fazla bilgi için bkz. [uygulama etki alanları](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Visual Studio Office geliştirici araçları kullanarak oluşturduğunuz belge düzeyi özelleştirmeleri, yalnızca bir son kullanıcı tarafından uygulama başlatıldığında kullanılmak üzere tasarlanmıştır. Uygulamayı programlı olarak başlatılırsa, örneğin, otomasyon, kullanarak özelleştirme beklendiği gibi çalışmayabilir.  
  
### <a name="design-time-and-run-time-experiences"></a>Tasarım zamanı ve çalışma zamanı deneyimleri  
 Belge düzeyi özelleştirmeler mimarisi anlamak için bir çözüm tasarlamak ve bir çözüm çalıştırma deneyimleri anlamanıza yardımcı olur.  
  
#### <a name="design-time"></a>Tasarım zamanı  
 Tasarım zamanı deneyimi, aşağıdaki adımları içerir:  
  
1.  Bir belge düzeyi projede Geliştirici oluşturur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Projeyi, belge ve belgenin arkasında çalışan derleme içerir. Belge zaten (bir tasarımcı tarafından oluşturulan) mevcut veya yeni bir belge projesiyle birlikte oluşturulabilir.  
  
2.  Tasarımcı — proje veya bir başkasının oluşturur ya da Geliştirici — son kullanıcıya belgeyi son Görünüm ve yapısını oluşturur.  
  
#### <a name="runtime"></a>Çalışma zamanı  
 Çalışma zamanı deneyimi, aşağıdaki adımları içerir:  
  
1.  Son kullanıcı, belge veya yönetilen kod uzantıları çalışma kitabı açılır.  
  
2.  Derlenmiş bütünleştirilmiş kodun belge veya çalışma kitabındaki yükler.  
  
3.  Kullanıcı belge veya çalışma kitabındaki içinde çalıştığı derleme olaylara yanıt verir.  
  
#### <a name="developer-and-end-user-perspective-compared"></a>Geliştirici ve son kullanıcı açısından karşılaştırma  
 Geliştirici birincil olarak çalıştığından [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ve son kullanıcının Word veya Excel'de çalışır, belge düzeyinde özelleştirmeler anlama iki yolu vardır.  
  
|Geliştiricinin Bakış açısı|Son kullanıcının perspektifi|  
|-----------------------------|----------------------------|  
|Kullanarak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], geliştiricinin Word ve Excel tarafından erişilebilen bir kod yazar.<br /><br /> Geliştiricinin Word veya Excel'de çalışan bir yürütülebilir dosya oluşturuyor görünse de, işlem gerçekten şekilde çalışır. Belge bir derlemeyle ilişkilendirilir ve bu derlemeye bir işaretçi içerir. Belge açıldığında, Word veya Excel derlemeyi bulur ve kod işlenen tüm olaylara yanıt olarak çalışır.|Çözüm kullananlar yalnızca belge veya çalışma kitabını açın (veya bir şablondan yeni bir belge oluşturmak) gibi herhangi bir Microsoft Office dosyasını açmak.<br /><br /> Derleme özelleştirmeleri belge veya otomatik olarak, geçerli verilerle doldurma veya bilgi istemek için bir iletişim kutusu gösteren gibi çalışma kitabındaki sağlar.|  
  
### <a name="supported-document-formats-for-document-level-customizations"></a>Desteklenen belge düzeyi özelleştirmeleri için belgenin biçimleri  
 Özelleştirme projesi oluşturduğunuzda, projede kullanmak istediğiniz belge biçimi seçebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Aşağıdaki tabloda, Excel ve Word için belge düzeyi özelleştirmeleri kullanabilirsiniz biçimlerden listeler.  
  
|Excel|Word|  
|-----------|----------|  
|Excel çalışma kitabı (*.xlsx*)<br /><br /> Makro içerebilen Excel çalışma kitabı (*.xlsm*)<br /><br /> Excel İkili çalışma kitabı (*.xlsb*)<br /><br /> Excel 97-2003 çalışma kitabı (*.xls*)<br /><br /> Excel şablonu (*.xltx*)<br /><br /> Makro içerebilen Excel şablonu (*.xltm*)<br /><br /> Excel 97-2003 şablonu (*.xlt*)|Word belgesi (*.docx*)<br /><br /> Makro içerebilen Word belgesi (*.docm*)<br /><br /> Word 97-2003 belgesi (*.doc*)<br /><br /> Word şablonu (*.dotx*)<br /><br /> Makro içerebilen Word şablonu (*.dotm*)<br /><br /> Word 97-2003 şablonu (*.dot*)|  
  
 Yönetilen kod uzantıları yalnızca desteklenen biçimlerdeki belgeler için tasarlamanız gerekir. Aksi takdirde, belge uygulamada açıldığında belirli olaylar oluşmayabilir. Örneğin, <xref:Microsoft.Office.Tools.Excel.Workbook.Open> olayı web sayfası veya Excel XML elektronik tablosu biçiminde kaydedilmiş çalışma kitapları ile yönetilen kod uzantıları kullandığınız zaman oluşmaz (*.htm*; *.html*) biçimi.  
  
### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>.Xml dosya adı uzantılarına sahip Word belgeleri için destek  
 Belge düzeyi projesi şablonlarının üzerinde aşağıdaki dosya biçimlerini tabanlı projeler oluşturmaya izin verme:  
  
- Word XML belgesi (*\*xml*).  
  
- Word 2003 XML belgesi (*\*xml*).  
  
  Son kullanıcılarınızın bu dosya biçimlerinde özelleştirmeleri kullanmak istiyorsanız, oluşturun ve yukarıdaki tabloda belirtilen desteklenen dosya biçimleri birini kullanan bir özelleştirme dağıtın. Özelleştirme yükledikten sonra son kullanıcıların Word XML belgesinde belgeyi kaydedebilirsiniz (*\*xml*) biçimi veya Word 2003 XML belgesi (*\*xml*) biçiminde ve özelleştirme beklendiği gibi çalışmayı sürdürecektir.  
  
##  <a name="Components"></a> Özelleştirmelerin bileşenleri  
 Temel bir özelleştirme belge ve derleme bileşenleridir. Bu bileşenlerin yanı sıra, Microsoft Office uygulamalarını keşfedin ve yükledikleri nasıl önemli bir rol oynar diğer birkaç bölümü vardır.  
  
### <a name="deployment-manifest-and-application-manifest"></a>Dağıtım bildirimini ve uygulama bildirimi  
 Özelleştirmeleri özelleştirme bütünleştirilmiş kodu en güncel sürümünü yüklemek üzere dağıtım bildirimleri ve uygulama bildirimleri kullanın. Dağıtım noktaları için geçerli bir uygulama bildirimi bildirimi. Uygulamayı özelleştirme bütünleştirilmiş kodu noktalarına bildirim ve giriş noktası sınıfı (veya sınıfları) derlemede yürütmek için belirtir. Daha fazla bilgi için [uygulama ve dağıtım bildirimlerini Office çözümlerinde](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio Araçları  
 Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan bir belge düzeyi özelleştirmeleri çalıştırmak için son kullanıcı bilgisayarlarında yüklü olmalıdır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yüklü. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Yük özelleştirme bütünleştirilmiş kodu ve yönetilen bir derleme kümesi yönetilmeyen bileşenler içerir. Bu yönetilen derlemeleri otomatikleştirme ve ana bilgisayar uygulamasını genişletmek için özelleştirme kodunuzun kullandığı nesne modeli sağlar.  
  
 Daha fazla bilgi için [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowCustomizationsWork"></a> Özelleştirmeleri Microsoft Office uygulamaları ile nasıl çalışır?  
 Bir kullanıcı bir Microsoft Office Özelleştirme bir parçası olan bir belgeyi açtığında, uygulama bulmak ve özelleştirme bütünleştirilmiş kodu en güncel sürümünü yüklemek için belgenin bağlı olduğu dağıtım bildirimini kullanır. Dağıtım bildiriminin konumunu adlı bir özel belge özelliğinde depolanıyor **AssemblyLocation**. Çözüm derlediğinizde, bu konumu tanımlayan dize özelliğe eklenir.  
  
 Dağıtım bildirimi işaret sonra en son derlemeye işaret eden bir uygulama bildirimi. Daha fazla bilgi için [uygulama ve dağıtım bildirimlerini Office çözümlerinde](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Aşağıdaki çizim belge düzeyinde bir özelleştirmenin temel mimarisini gösterir.  
  
 ![2007 office Özelleştirme mimarisi](../vsto/media/office07-custom.png "2007 Office Özelleştirme mimarisi")  
  
> [!NOTE]  
>  Office çözümlerinde hedef [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], konak uygulama tarafından nesne modeline çağrı PIA içine doğrudan çağırmak yerine çözüm derlemesindeki gömülü birincil birlikte çalışma derlemesi (PIA) tür bilgileri kullanılarak çözümler. Daha fazla bilgi için [tasarım ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Yükleme işlemi  
 Aşağıdaki adımlar, bir kullanıcı bir Microsoft Office çözümünün parçası olan bir belgeyi açtığında gerçekleşir.  
  
1.  Microsoft Office uygulamasının özel belge özellikleri, yönetilen kod uzantıları belgeyle ilişkili olup olmadığını denetler. Daha fazla bilgi için [özel belge özelliklerine genel bakış](../vsto/custom-document-properties-overview.md).  
  
2.  Yönetilen kod uzantıları varsa, uygulamayı yükleyen *VSTOEE.dll*, hangi yükleri *VSTOLoader.dll*. Yönetilmeyen bunlar yükleyici bileşenleri Office çalışma zamanı için Visual Studio 2010 Araçları DLL'ler. Daha fazla bilgi için [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  *VSTOLoader.dll* yükler [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] ve yönetilen kısmına başlar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  Belgeyi yerel bilgisayardan farklı bir konumdan açarsa [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] belgenin konumunu olduğunu doğrular **Güvenilen Konumlar** listesinde **Güven Merkezi Ayarları** için Bu belirli Office uygulaması. İçin belge konumunu güvenilir değilse, özelleştirme güvenilir değil ve yükleme işlemi burada durdurulur.  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Çözümü yükler henüz yüklü değil, en son uygulama ve dağıtım bildirimlerini indirir ve bir dizi güvenlik denetimi gerçekleştirir. Daha fazla bilgi için [güvenli Office çözümleri](../vsto/securing-office-solutions.md).  
  
6.  Özelleştirme çalıştırmak için güvenilir ise [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derleme güncelleştirmeleri denetlemek için dağıtım bildirimini ve uygulama bildirimini kullanır. Derlemenin yeni bir sürüm varsa, çalışma zamanı derlemesi için yeni sürümü indirmeleri [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] istemci bilgisayarda önbelleği. Daha fazla bilgi için [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
7.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Özelleştirme derlemesini yüklemek yeni bir uygulama etki alanı oluşturur.  
  
8.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Özelleştirme bütünleştirilmiş kodu, uygulama etki alanına yükler.  
  
9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Çağrıları **başlangıç** özelleştirme derlemenizde olay işleyicisi. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio'da Office çözümleri mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Office çözümleri güvenliğini sağlama](../vsto/securing-office-solutions.md)   
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)   
 [Özel belge özelliklerine genel bakış](../vsto/custom-document-properties-overview.md)   
 [Belge düzeyi özelleştirmelerdeki önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)  
  
  