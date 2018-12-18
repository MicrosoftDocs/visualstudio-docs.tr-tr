---
title: Office çalışma zamanına genel bakış için Visual Studio Araçları
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b169242b9828f47f1ecfb87ebf02a9f86234699f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837002"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Office çalışma zamanına genel bakış için Visual Studio Araçları
  Visual Studio'da Microsoft Office geliştirici araçlarını kullanarak oluşturulan çözümleri çalıştırmak için son kullanıcı bilgisayarlarında Office çalışma zamanı için Visual Studio 2010 Araçları yüklenmesi gerekir. Daha fazla bilgi için [nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yükleme](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Office çalışma zamanı için Visual Studio 2010 Araçları iki ana bileşenden oluşur:  
  
- .NET Framework için Office uzantıları. Bu bileşenler, çözümünüz ile Microsoft Office uygulaması arasındaki iletişim katmanını sağlayan yönetilen derlemelerdir. Daha fazla bilgi için [.NET Framework için Office uzantılarını anlama](#officeextensions).  
  
- Office çözüm yükleyicisi. Bu bileşen, Office uygulamalarının çalışma zamanını ve çözümlerinizi yüklemek için kullandığı bir yönetilmeyen DLL'ler kümesidir. Daha fazla bilgi için [Office çözüm yükleyicisini anlama](#UnmanagedLoader).  
  
  Çalışma zamanı birkaç farklı yolla yüklenebilir. Bilgisayarın yapılandırmasına bağlı olarak, çalışma zamanını yüklediğinizde farklı çalışma zamanı bileşenlerinin yüklemesi gerçekleşir. Daha fazla bilgi için [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
##  <a name="officeextensions"></a> .NET Framework için Office uzantılarını anlama  
 Office çalışma zamanı için Visual Studio 2010 Araçları, .NET Framework 3.5 için Office uzantılarını içeren [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ve daha sonra. Her bir .NET Framework sürümünü hedefleyen çözümler, ilgili sürüm için uygun uzantıları kullanır.  
  
 Bu uzantılar, çözümlerinizin Office uygulamalarını otomatikleştirmek ve genişletmek için kullandığı derlemelerden oluşur. Bir Office projesi oluşturduğunuzda, Visual Studio projenin .NET Framework hedefi ve proje türü için kullanılan derlemelerin başvurularını otomatik olarak ekler. Office uzantılarındaki derlemeler hakkında daha fazla bilgi için bkz. [Office çalışma zamanı için Visual Studio araçlarındaki derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
### <a name="design-differences-in-the-office-extensions"></a>Office uzantılarındaki tasarım farkları  
 .NET Framework 3.5 için Office uzantılarında kullandığınız türlerin çoğu sınıflardır. Bunlar önceki sürümlerinde bulunan aynı sınıflardır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Buna karşılık, için Office uzantılarında kullandığınız türlerin çoğu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki arabirimdir. Hedeflediğinizde gibi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya da sonraki <xref:Microsoft.Office.Tools.Excel.Worksheet> ve <xref:Microsoft.Office.Tools.Word.Document> sınıf yerine arayüzleridir türleridir.  
  
 Çözümünüzün hedefi .NET Framework 3.5 çoğu durumda, Office çözümlerinde yazdığınız kod aynıdır veya [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Ancak belirli özellikler, .NET Framework'ün farklı sürümlerini hedeflediğinizde farklı kod gerektirir. Daha fazla bilgi için [geçirme Office çözümlerini .NET Framework 4 veya sonraki bir sürüme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>.NET Framework 4 veya sonraki Office uzantılarındaki arabirimler  
 İçin Office uzantılarındaki arabirimlerin çoğu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra kullanıcı kodu tarafından uygulanmak üzere amaçlanmamıştır. Doğrudan uygulayabileceğiniz arabirimler yalnızca adları harfi ile başlayan sahip **miyim**, gibi <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.  
  
 Harfiyle başlamayan tüm arabirimler **miyim** Office çalışma zamanı için Visual Studio 2010 araçları tarafından dahili olarak uygulanır ve bu arabirimler gelecek sürümlerde değişebilir. Bu arabirimleri uygulayan nesneler oluşturmak için tarafından sağlanan yöntemleri kullanın. `Globals.Factory` projenizdeki nesne. Örneğin, uygulayan bir nesne almak için <xref:Microsoft.Office.Tools.Excel.SmartTag> kullanın, arabirim `Globals.Factory.CreateSmartTag` yöntemi. Hakkında daha fazla bilgi için `Globals.Factory`, bkz: [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Tür eşdeğerliği ve katıştırılmış türleri .NET Framework 4 veya sonraki sürümlerini hedefleyen projelerde etkinleştir  
 Çünkü için Office uzantılarının nesne modeli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra temel arabirimleri üzerinde tür bilgilerini katıştırma için Visual C# hem Visual Studio Visual Basic'te tür denklik özelliğini kullanabilirsiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çözümünüze . Bu özellik, Office çözümlerini etkinleştiren ve [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] birbirinden sürüm. Örneğin, çözümünüz kullanıyorsa <xref:Microsoft.Office.Tools.Word.Document> katıştırılmış tür olarak sonraki çalışma zamanı sürümü arabirim üye eklerse <xref:Microsoft.Office.Tools.Word.Document> arabirimi, çözümünüz çalışma zamanının sonraki sürümüyle çalışacaktır. Çözümünüzü kullanmıyorsa <xref:Microsoft.Office.Tools.Word.Document> arabirim katıştırılmış tür olarak, çözümünüz çalışma zamanının sonraki sürümüyle artık çalışmayacaktır.  
  
 Hedefleyen bir Office projesi oluşturduğunuzda varsayılan olarak tür denklik özelliği etkin değil [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri. Bu özelliği etkinleştirmek istiyorsanız, **birlikte çalışma türlerini katıştır** projenize aşağıdaki derleme başvurularının herhangi birinin özelliğini **True**:  
  
- Microsoft.Office.Tools.dll  
  
- Microsoft.Office.Tools.Common.dll  
  
- Microsoft.Office.Tools.Excel.dll  
  
- Microsoft.Office.Tools.Outlook.dll  
  
- Microsoft.Office.Tools.Word.dll  
  
  Bu değişikliği yaptıktan sonra, projeyi oluşturduğunuzda, proje tarafından kullanılan tüm çalışma zamanı türlerine ilişkin tür bilgileri çözüm derlemesine eklenir. Tür bilgilerini başvurulan derlemelerdeki yerine bu katıştırılmış bilgi türünü çalışma zamanında bir çözüm tarafından kullanılır.  
  
##  <a name="UnmanagedLoader"></a> Office çözüm yükleyicisini anlama  
 Office çalışma zamanı için Visual Studio Araçları çalışma zamanı ve Office çözümlerini yüklemek için Office uygulamalarının kullandığı bazı yönetilmeyen DLL'ler içerir. Hiçbir zaman bu DLL'ler ile doğrudan çalışmanız gerekmese de, bu DLL'lerin amaçlarını bilmeniz, Office çözümlerinin mimarisini daha iyi anlamanıza yardımcı olabilir.  
  
 Yükleme işlemi sırasında bu bileşenlerin nasıl kullanıldığı hakkında daha fazla bilgi için bkz: [belge düzeyi özelleştirmeler mimarisi](../vsto/architecture-of-document-level-customizations.md) ve [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="vstoeedll"></a>VSTOEE.dll  
 Bir kullanıcı belge düzeyinde bir özelleştirme açtığında veya bir VSTO eklentisi başlattığında, Office uygulamasının içine yapılan çağrılar *VSTOEE.dll* yüklemek için gereken görevleri gerçekleştirmek için [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 *VSTOEE.dll* emin olun doğru sürümünü [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çözüm ve yüklü Office sürümü için yüklenir. Ancak birden çok sürümünü [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yalnızca bir örneği aynı bilgisayarda yüklü *VSTOEE.dll* aynı anda yüklenir. Bu *VSTOEE.dll* , bilgisayarda yüklü çalışma zamanı en son sürümü dahildir. Farklı sürümleri hakkında daha fazla bilgi için [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] diğer çözümler için kullanılabilmesi için bkz: [çözümleri Microsoft Office'in farklı sürümlerinde çalıştırma](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
### <a name="vstoloaderdll"></a>VSTOLoader.dll  
 Sonra *VSTOEE.dll* uygun sürümünü yükler [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], *VSTOLoader.dll* çözüm derlemesini yüklemek için gerekli çalışmanın çoğunu gerçekleştirir. *VSTOLoader.dll* çeşitli işlemler yapar:  
  
- Her bir çözüm derlemesi için uygulama etki alanı oluşturur.  
  
- Çözüm derlemesinin çalışma izni olduğunu doğrulamak için bir dizi güvenlik denetimi gerçekleştirir.  
  
- Çözüm için gerekli .NET Framework için Office uzantıları sürümünü yükler.  
  
  *VSTOLoader.dll* ayrıca VSTO eklentileri özgü çeşitli işlemler yapar:  
  
- Bunu uygulayan <xref:Extensibility.IDTExtensibility2> arabirimi. <xref:Extensibility.IDTExtensibility2> Tüm VSTO eklentileri için Microsoft Office uygulamaları uygulamalıdır bir COM arabirimidir. Bu arabirim, uygulamanın VSTO eklenti ile iletişim kurmak için çağırdığı yöntemleri tanımlar.  
  
- Imanagedaddin arabirimi uygular. Bu arabirim, VSTO eklentileri yükünü dengeleyebilmek için Office uygulamaları tarafından kullanılır. Daha fazla bilgi için [Imanagedaddin arabirimi](../vsto/imanagedaddin-interface.md).  
  
## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Çalışma zamanının 32-bit ve 64 bit sürümlerini anlama  
 Office çalışma zamanı için Visual Studio 2010 Araçları'nın ayrı 64-bit ve 32-bit sürümleri vardır. Çalışma zamanının bu sürümü, 64-bit ve 32-bit sürümlerinde Office çözümleri çalıştırmak için kullanılır. Aşağıdaki tabloda gösterilen her Windows ve Office birleşimi için hangi çalışma zamanı sürümü gereklidir.  
  
|Windows sürümü|Microsoft Office sürümü|Office çalışma zamanı için Visual Studio Araçları'nın gerekli sürümü|  
|------------------------|---------------------------------|--------------------------------------------------------------------|  
|32 bit:|32 bit:|32 bit:|  
|64 bit|32 bit:|64 bit|  
|64 bit|64 bit|64 bit|  
  
 Office, gerekli sürümünü yüklediğinizde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Office ile birlikte yüklenir. Örneğin, yüklediğinizde Office 64-bit sürüm Windows, 64-bit sürümü 64-bit sürümünde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] de yüklenir. Yükleme hakkında daha fazla bilgi için [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Office ile bkz [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 Office'in 64 bit sürümü, Visual Studio 2008'de 2007 Microsoft Office sistemi proje şablonları kullanılarak oluşturulan Office çözümlerini de çalıştırabilirsiniz. Ancak Visual Studio 2005 kullanılarak oluşturulan Office çözümlerini veya Visual Studio 2008'de Microsoft Office 2003 proje şablonları kullanılarak oluşturulan Office çözümlerini çalıştıramaz. Daha fazla bilgi için [çözümleri Microsoft Office'in farklı sürümlerinde çalıştırma](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio 2010 Araçları onarın  
 Çalışma zamanını onarmanız gerekirse açın **programlar ve Özellikler** veya **Program Ekle veya Kaldır** Denetim Masası'nda seçin **için Microsoft Visual Studio 2010 Araçları Office çalışma zamanı**programları ve ardından listesinde **kaldırma**. Çalıştırılan kurulum programı çalışma zamanını onarmanızı sağlar. Tıklarsanız **değişiklik**, çalışma zamanını onarma seçeneği sunulmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Office çalışma zamanı için Visual Studio araçlarındaki derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)   
 [Visual Studio'da Office çözümleri mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Belge düzeyi özelleştirmeler mimarisi](../vsto/architecture-of-document-level-customizations.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Office çözümlerini geçirme ve yükseltme](../vsto/upgrading-and-migrating-office-solutions.md)  
  
  