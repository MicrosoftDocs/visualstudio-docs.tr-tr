---
title: VSTO Eklentileri Mimarisi
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
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: dccfd3a3344ef9bde46b0b1e6bed50294d832acb
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248169"
---
# <a name="architecture-of-vsto-add-ins"></a>VSTO Eklentileri Mimarisi
  Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan VSTO eklentileri kararlılık ve güvenlik sağlayan mimari özelliklere sahiptir ve bunları Microsoft Office ile yakından çalışmaya etkinleştirin. Bu konu, VSTO eklentileri şu yönlerini açıklar:  
  
- [VSTO eklentileri anlama](#UnderstandingAddIns)  
  
- [VSTO eklentileri bileşenleri](#AddinComponents)  
  
- [VSTO eklentileri Microsoft Office uygulamaları ile nasıl çalışır?](#HowAddinsWork)  
  
  [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
  VSTO eklentileri oluşturma hakkında genel bilgi için bkz: [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) ve [VSTO eklentileri programlama başlama](../vsto/getting-started-programming-vsto-add-ins.md).  
  
##  <a name="UnderstandingAddIns"></a> VSTO eklentileri anlama  
 Bir VSTO eklenti oluşturmak için Visual Studio Office geliştirici araçları kullandığınızda, Microsoft Office uygulama tarafından yüklenen bir yönetilen kod derlemesi oluşturun. Derleme yüklendikten sonra VSTO Eklentisi (örneğin, bir kullanıcı bir menü öğesini tıkladığında) uygulamasında başlatılan olaylara yanıt verebilirsiniz. VSTO eklentisi ayrıca uygulamasını otomatikleştirmek ve genişletmek için nesne modeli çağırabilir ve sınıflarda birini kullanabilirsiniz [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 Derleme uygulamasının birincil birlikte çalışma derlemesi uygulamanın COM bileşenleriyle iletişim kurar. Daha fazla bilgi için [Office birincil birlikte çalışma derlemelerini](../vsto/office-primary-interop-assemblies.md) ve [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 Her VSTO eklentisi birden çok VSTO eklentileri için bir uygulama yüklediyseniz, farklı uygulama etki alanında yüklenir. Başka bir deyişle, bir VSTO hatalı davranan eklentisi diğer VSTO başarısız olmasına eklentileri sebep olamaz. Ayrıca uygulama kapatıldığında tüm VSTO eklentisi derlemeleri bellekten olduğundan emin olun yardımcı olur. Uygulama etki alanları hakkında daha fazla bilgi için bkz. [uygulama etki alanları](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Visual Studio Office geliştirici araçları kullanarak oluşturduğunuz VSTO Add-Ins yalnızca bir son kullanıcı tarafından konak Microsoft Office uygulaması başlatıldığında kullanılmak üzere tasarlanmıştır. Uygulama, program aracılığıyla (örneğin, Otomasyon kullanılarak) başlatılır, VSTO eklentisi beklendiği gibi çalışmayabilir.  
  
##  <a name="AddinComponents"></a> VSTO eklentileri bileşenleri  
 VSTO eklenti derlemesinin ana bileşeni olmakla birlikte, Microsoft Office uygulamaları nasıl keşfetmek ve VSTO eklentileri yük önemli bir rol oynar çeşitli bileşenler vardır.  
  
### <a name="registry-entries"></a>Kayıt defteri girdileri  
 Microsoft Office uygulamaları, VSTO eklentileri için kayıt defteri girdileri kümesini bakarak keşfedin. VSTO eklentileri tarafından kullanılan kayıt defteri girdileri tam bir listesi için bkz. [VSTO eklentileri için kayıt defteri girdileri](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Çözümünüzü oluşturduğunuzda, Visual Studio hata ayıklama ve VSTO eklenti çalıştırmak için tüm gerekli kayıt defteri girdilerini geliştirme bilgisayarında oluşturur. Daha fazla bilgi için [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
 Çözümünüzü dağıtmak için ClickOnce kullanırsanız, Kurulum programı yayımlama işlemi tarafından otomatik olarak oluşturulan son kullanıcı bilgisayarda kayıt defteri anahtarlarını oluşturur. Daha fazla bilgi için [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
### <a name="deployment-manifest-and-application-manifest"></a>Dağıtım bildirimini ve uygulama bildirimi  
 VSTO eklentileri, VSTO eklenti derlemesi en güncel sürümünü yüklemek üzere dağıtım bildirimleri ve uygulama bildirimleri kullanın. Dağıtım noktaları için geçerli bir uygulama bildirimi bildirimi. Uygulama bildirimi, VSTO eklentisi derlemeye işaret eden ve derlemede yürütmek için giriş noktası sınıfını belirtir. Daha fazla bilgi için [uygulama ve dağıtım bildirimlerini Office çözümlerinde](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio Araçları  
 Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan VSTO Add-Ins çalıştırmak için son kullanıcı bilgisayarlarında yüklü olmalıdır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yüklü. Çalışma zamanı yönetilmeyen bileşenler ve yönetilen bir derleme kümesi içerir. Yönetilmeyen bileşenler, VSTO eklenti derlemesi yüklenemiyor. Yönetilen derlemeler, ana bilgisayar uygulamasını otomatikleştirmek ve genişletmek için VSTO eklentisi kodunuzun kullandığı nesne modeli sağlar.  
  
 Daha fazla bilgi için [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowAddinsWork"></a> VSTO eklentileri Microsoft Office uygulamaları ile nasıl çalışır?  
 Bir kullanıcı bir Microsoft Office uygulaması başlatıldığında uygulama bulmak ve VSTO eklentisi derleme en güncel sürümünü yüklemek için dağıtım bildirimini ve uygulama bildirimini kullanır. Aşağıdaki çizimde bu VSTO eklentileri temel mimarisini gösterir.  
  
 ![2007 office eklenti mimarisi](../vsto/media/office07addin.png "2007 Office eklenti mimarisi")  
  
> [!NOTE]  
>  Office çözümlerinde hedef [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], konak uygulama tarafından nesne modeline çağrı PIA içine doğrudan çağırmak yerine çözüm derlemesindeki gömülü PIA tür bilgileri kullanılarak çözümler. Daha fazla bilgi için [tasarım ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Yükleme işlemi  
 Bir kullanıcı bir uygulama başlattığında aşağıdaki adımlar oluşur:  
  
1.  Uygulama, Visual Studio'da Office geliştirme araçları kullanılarak oluşturulmuş VSTO Add-Ins tanımlayan girişleri için kayıt defterini denetler.  
  
2.  Uygulama bu kayıt defteri girdileri bulursa, VSTOLoader.dll yükleyen VSTOEE.dll, uygulamayı yükler. Yönetilmeyen bunlar yükleyici bileşenleri Office çalışma zamanı için Visual Studio 2010 Araçları DLL'ler. Daha fazla bilgi için [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  *VSTOLoader.dll* yükler [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] ve yönetilen kısmına başlar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Bildirim güncelleştirmeleri denetler ve en son uygulama ve dağıtım bildirimlerini indirir.  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Bir dizi güvenlik denetimi gerçekleştirir. Daha fazla bilgi için [güvenli Office çözümleri](../vsto/securing-office-solutions.md).  
  
6.  VSTO eklenti çalıştırmak için güvenilir olup olmadığını [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derleme güncelleştirmeleri denetlemek için dağıtım bildirimini ve uygulama bildirimini kullanır. Derlemenin yeni bir sürüm varsa, çalışma zamanı derlemesi için yeni sürümü indirmeleri [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] istemci bilgisayarda önbelleği. Daha fazla bilgi için [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
7.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO eklentisi derlemesini yüklemek yeni bir uygulama etki alanı oluşturur.  
  
8.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO eklentisi derlemeyi uygulama etki alanına yükler.  
  
9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Çağrıları <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> VSTO siz kıldıysanız eklenti, yöntemi.  
  
     İsteğe bağlı olarak, diğer Microsoft Office çözümleri için VSTO eklenti, bir nesneyi göstermek için bu yöntemi geçersiz kılabilirsiniz. Daha fazla bilgi için [çağrı kod VSTO eklentileri diğer Office Çözümlerinden](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
10. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Çağrıları <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> VSTO siz kıldıysanız eklenti, yöntemi.  
  
     İsteğe bağlı olarak bir Microsoft Office özellik genişletilebilirlik arabirimi uygulayan bir nesne döndürerek genişletmek için bu yöntemi geçersiz kılabilirsiniz. Daha fazla bilgi için [genişletilebilirlik arabirimlerini kullanarak kullanıcı Arabirimi özelleştirme özellikleri](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
    > [!NOTE]  
    >  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Ayrı için çağrılar yapar <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> konak uygulama tarafından desteklenen her bir genişletilebilirlik arabirimi için yöntemi. Yapılan ilk çağrı rağmen <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> yöntemi genellikle gerçekleşir çağırmadan önce `ThisAddIn_Startup` yöntemi, VSTO eklenti yapmamalıdır ne zaman hakkında varsayımlar <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> yöntemin çağrılacağı ya da kaç kez çağrılır.  
  
11. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Çağrıları `ThisAddIn_Startup` VSTO eklenti yöntemi. Bu yöntem için varsayılan olay işleyicisini olan <xref:Microsoft.Office.Tools.AddInBase.Startup> olay. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio'da Office çözümleri mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Belge düzeyi özelleştirmeler mimarisi](../vsto/architecture-of-document-level-customizations.md)   
 [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [Office çözümleri güvenliğini sağlama](../vsto/securing-office-solutions.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)  
  
  