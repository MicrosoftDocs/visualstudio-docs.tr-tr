---
title: Projeleri taşıma, geçirme ve yükseltme
description: Visual Studio ve Visual Studio'nın bir projeyi geçirmek gerektiğinde nasıl karar verir, önceki sürümlerinde oluşturulmuş projeleri Visual Studio 2017'de desteklemeye yönelik bir başvuru.
ms.date: 10/09/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload: multiple
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.openlocfilehash: a8161fd7534554da0ad45b3aa2b985a68dd9e49d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067067"
---
# <a name="project-migration-and-upgrade-reference-for-visual-studio-2017"></a>Visual Studio 2017 için proje geçiş ve yükseltme başvurusu

Visual Studio'nun her yeni sürümü genellikle önceki türlerinin projeler, dosyalar ve diğer varlıklardan çoğunu destekler. Bunlarla çalışabilirsiniz [her zaman sahip](../ide/solutions-and-projects-in-visual-studio.md), ve yeni özelliklere bağımlı olmayan şartıyla, Visual Studio genellikle geriye dönük uyumluluk gibi Visual Studio 2015, Visual Studio 2013, önceki sürümlerde korumaya çalışır ve Visual Studio 2012. (Bkz [sürüm notları](https://visualstudio.microsoft.com/vs/release-notes/) için hangi özelliklerin hangi sürümlerine özeldir.)

Bazı proje türleri için destek de zaman içinde değişir. Visual Studio'nun daha yeni bir sürümü artık belirli projelerin hiç destekleyebilir ya da bir proje artık geriye dönük olarak uyumlu şekilde güncelleştirilmesini gerektirir. Geçiş sorunları için geçerli durumunu almak için bkz [Visual Studio Geliştirici topluluğu sitesini](https://developercommunity.visualstudio.com).

Mevcut bu makalede, Visual Studio 2017 geçirebileceğiniz proje türleri için Ayrıntılar sağlar. Bu makalede, Visual Studio 2017'de artık desteklenmemektedir ve bu nedenle geçirilemiyor proje türleri dışlar. Makale ayrıca hiçbir geçiş sorunları olan desteklenen proje türleri dışlar; Bu liste bulunur [Platform hedefleme ve Uyumluluk](/visualstudio/productinfo/vs2017-compatibility-vs).

> [!Important]
> Belirli proje türleri, uygun iş yükleri için Visual Studio yükleyicisi aracılığıyla yüklenmesi gerekir. İş yükü yüklenmiş yoksa, Visual Studio bir bilinmeyen veya uyumsuz proje türü bildirir. Bu durumda, yükleme seçeneklerinizi denetleyin ve yeniden deneyin. Yeniden bakın [Platform hedefleme ve Uyumluluk](/visualstudio/productinfo/vs2017-compatibility-vs) makale Visual Studio 2017'de proje desteği hakkında ayrıntılı bilgi için.

## <a name="project-types"></a>Proje türleri

Aşağıdaki listede, önceki sürümlerde oluşturulmuş projeler için Visual Studio 2017 desteği açıklanmaktadır.

Bir proje görmüyorsanız veya dosya türü listelenen Burada, olması, başvurun [bu makalede Visual Studio 2015 sürümünü](https://docs.microsoft.com/visualstudio/porting/porting-migrating-and-upgrading-visual-studio-projects?view=vs-2015) ve projenizin ayrıntılarını sağlamak için bu sayfanın altındaki "belgeleri geri bildirimde bulunun" seçeneğini kullanın. (Bir yanıt isterseniz, belge geri bildirimi kullanmak yerine "Bu sayfa faydalı anonimdir?" Denetim.)

| Proje Türü | Destek |
| --- | --- |
| .NET core projeleri (xproj) | Visual Studio 2015 ile oluşturulan projeleri bir xproj proje dosyası dahil önizleme araçları kullanılır. Visual Studio 2017 ile bir xproj dosyasını açtığınızda, dosya (xproj dosyasının yedek bir kopyası yapılır) csproj biçimine geçiş istenir. Visual Studio 2015'te ve daha önce bu csproj biçimine .NET Core projeleri için desteklenmiyor.  Xproj biçimi dışında Visual Studio 2017'de csproj'a geçiş için desteklenmiyor. Daha fazla bilgi için [csproj biçimine geçiş .NET Core projeleri](/dotnet/core/migration/#visual-studio-2017).|
| ASP.NET Web uygulaması ve etkin Application Insights ile ASP.NET Core Web uygulaması | Her bir Visual Studio kullanıcı için kaynak bilgileri kullanıcı örneği başına kayıt defterinde depolanır. Bu bilgiler kullanıcının açılan bir proje sahip olmadığında kullanılır ve Azure Application Insights verilerini aramak istiyor. Visual Studio 2015, Visual Studio 2017'den farklı bir kayıt defteri konumu kullanır ve yok çakışmadığını.<br/><br/>Bir kullanıcı bir ASP.NET Web uygulaması veya ASP.NET Core Web uygulaması oluşturur, sonra kaynak .suo dosyasında depolanır. Kullanıcı projeyi açabilir, Visual Studio 2015 veya 2017 ve Visual Studio, projeler ve çözümler her iki sürümde kullanılmasını desteklediği sürece kaynak bilgileri her ikisi için kullanılır. Kullanıcıların her bir ürün üzerinde bir kez kimlik doğrulaması gerekir. Örneğin, bir projeyi Visual Studio 2015 ile oluşturulan ve Visual Studio 2017'de açılır, Visual Studio 2017'de kimlik doğrulaması kullanıcının olmalıdır. |
| C#/Visual Basic Webform veya Windows Form | Visual Studio 2015 ve Visual Studio 2017 ile projeyi açabilirsiniz. |
| Veritabanı birim testi projeleri (csproj, .vbproj) | Test projeleri Visual Studio 2017'de yüklenir ancak GAC kullanan eski veri birimi bağımlılıkları sürümünü 'd. Birim test projesi'nın en son bağımlılıklarını kullanacak şekilde yükseltmek için Çözüm Gezgini'nde projeye sağ tıklayın ve seçin **SQL Server birim test projesine Dönüştür...** . |
| F# | Visual Studio 2017, Visual Studio 2013 ve 2015 oluşturulan projeleri açabilirsiniz. Bu projeler Visual Studio 2017 özelliklerini etkinleştirmek için ancak proje özelliklerini açın ve değiştirmek için hedef fsharp.core F# 4.1. Ayrıca  **F# dil desteği** varsayılan .NET iş yükleri ile Visual Studio Yükleyicisi'nde seçeneği belirlenmemişse; iş yükü için bu seçeneği'ni seçerek veya menüsünden seçim içermelidir  **Tek tek bileşenler** sekmesinde altında **geliştirme etkinliklerini**. |
| InstallShield<br/>MSI Kurulumu | Yükleyici projeleri Visual Studio 2010'da oluşturulan yardımıyla daha yeni sürümlerinde açılabilir [Visual Studio yükleyici projeleri uzantısı](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects). Ayrıca bkz: [WiX Toolset Visual Studio 2017 uzantısı](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension). InstallShield Limited Edition, artık Visual Studio'ya dahildir. Danışın [Flexera yazılım](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) Visual Studio 2017 için kullanılabilirliği hakkında. |
| LightSwitch | LightSwitch, Visual Studio 2017'de artık desteklenmiyor. Visual Studio 2012 ile oluşturulan ve daha önce Visual Studio 2013 veya Visual Studio 2015'te açtığınız projeler yükseltilir ve bundan sonra yalnızca Visual Studio 2013 veya Visual Studio 2015'te açılabilir. |
| Visual Studio için Microsoft Azure Araçları | Bu proje türleri'ni açmak için ilk yükleme [.NET için Azure SDK'sı](http://azure.microsoft.com/downloads/), sonra projeyi açabilirsiniz. Gerekirse, projenizi güncelleştirilir. |
| Model-View-Controller framework (ASP.NET MVC) | MVC sürümleri ve Visual Studio desteği:<ul><li>MVC 2 ve MVC 3, Visual Studio 2010 SP1'i destekler. MVC 4 desteği aracılığıyla eklenen [ASP.NET 4 MVC 4 ile Visual Studio 2010 SP1'i indirmek için](https://www.microsoft.com/download/details.aspx?id=30683)</li><li>Visual Studio 2012 yalnızca MVC 3 ve MVC 4 destekler.</li><li>Visual Studio 2013 yalnızca MVC 4 ve MVC 5 destekler.</li><li>Visual Studio 2017 ve Visual Studio 2015 (var olan projeleri açın ancak yenilerini oluşturma değil) MVC 4 ve MVC 5 destekler</li></ul><br/>MVC sürümlerini yükseltme:<ul><li>MVC 2'den MVC 3'e otomatik olarak yükseltme hakkında daha fazla bilgi için bkz: [ASP.NET MVC 3 uygulama Yükseltici](http://go.microsoft.com/fwlink/?LinkID=238178).</li><li>MVC 2'den MVC 3'e el ile yükseltme hakkında daha fazla bilgi için bkz: [ASP.NET MVC 2 projesini ASP.NET MVC 3 araç güncelleştirmesine yükseltme](http://go.microsoft.com/fwlink/?linkid=238178).</li><li>MVC3 MVC 4'e el ile yükseltme hakkında daha fazla bilgi için bkz. [ASP.NET MVC 3 projesini ASP.NET MVC 4'e yükseltme](http://www.asp.net/whitepapers/mvc4-release-notes). Projeniz .NET Framework 3.5 SP1'i hedefliyorsa, .NET Framework 4 kullanacak şekilde yeniden hedeflemeniz gerekir.</li><li>MVC 4'ten MVC 5'e el ile yükseltme hakkında daha fazla bilgi için bkz: [bir ASP.NET MVC 4 ve Web API projelerini ASP.NET MVC 5 ve Web API 2'ye yükseltme](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2).</li></ul> |
| Modelleme | Visual Studio'nun projeyi otomatik olarak güncelleştirmesine izin verirseniz, Visual Studio 2015, Visual Studio 2013 veya Visual Studio 2012 açabilirsiniz.<br/><br/>Modelleme projesi biçimi, Visual Studio 2015 ve Visual Studio 2017 arasında değişmemiştir ve proje açılabilir ve her iki sürümde değiştirildi. Ancak, Visual Studio 2017'de davranış farklılıkları vardır:<ul><li>Modelleme projeleri artık "Bağımlılık doğrulama" projelerinde menüler ve şablonları denir.</li><li>UML diyagramları, artık Visual Studio 2017'de desteklenir. UML dosyaları Çözüm Gezgini'nde önce listelenir, ancak XML dosyası olarak açılır. Visual Studio 2015, görüntülemek, oluşturmak veya UML diyagramları düzenlemek için kullanın.</li><li>Modelleme projesi oluşturulurken Visual Studio 2017'de artık mimari bağımlılık doğrulama gerçekleştirilir. Her kod projesini yerleşik olarak bunun yerine, doğrulama gerçekleştirilir. Bu değişiklik, modelleme projesine etkilemez, ancak Doğrulanmakta olan kod projeleri için değişiklik gerektirmez. Visual Studio 2017 otomatik olarak kod projeleri için gerekli değişiklikleri yapabilir ([daha fazla bilgi](http://go.microsoft.com/fwlink/?LinkId=827800)).</li></ul> |
| MSI kurulumu (vdproj) | InstallShield projeyi görürsünüz. |
| Office 2007 VSTO | Visual Studio 2017 için tek yönlü yükseltme gerektirir. |
| Office 2010 VSTO | Proje .NET Framework 4 hedefliyse, Visual Studio 2010 SP1 ve sonraki sürümlerinde açabilirsiniz. Tüm diğer projeler tek yönlü yükseltme gerektirir. |
| Service Fabric (sfproj) | Service Fabric uygulaması proje bir ASP.NET Core hizmeti projeye başvuruyor sürece Service Fabric uygulaması projeleri, Visual Studio 2015 veya Visual Studio 2017 açılabilir. Service Fabric Visual Studio 2017'de açtığınız Visual Studio 2015 projelerden csproj'a geçirilmesi xproj biçiminden geçiş yönlüdür. ".NET Core projeleri (xproj)" Bu tablodaki bakın. |
| SharePoint 2010 | SharePoint çözüm proje ile Visual Studio 2017 açıldığında, SharePoint 2013 veya SharePoint 2016 için yükseltilir. ".NET masaüstü geliştirme" iş yükü yükseltme için Visual Studio 2017'de yüklü olması gerekir.<br/><br/>SharePoint projeleri yükseltme hakkında daha fazla bilgi için bkz. [SharePoint 2013'e yükseltme](https://technet.microsoft.com/library/cc303420.aspx), [güncelleştirme iş akışını SharePoint Server 2013'te](https://technet.microsoft.com/library/dn133867.aspx), ve [SharePoint Server 2016 grubu oluşturma veritabanı için yükseltme ekleme](https://technet.microsoft.com/library/cc263026(v=office.16).aspx). |
| SharePoint 2016 | Office geliştirici araçları Önizleme 2'de oluşturulan SharePoint eklentisi projeleri, Visual Studio 2017'de açılamaz. Bu sınırlara yakın çalışmak için güncelleştirme `MinimumVisualStudioVersion` 12.0 için ve `MinimumOfficeToolsVersion` csproj vbproj dosyasında 12.2 için. |
| Silverlight | Silverlight projeleri Visual Studio 2017'de desteklenmez. Silverlight uygulamalarını korumak için Visual Studio 2015 kullanmaya devam edin. |
| SQL Server Raporlama Hizmetleri ve SQL Server Analysis Services (SSRS, SSDT, SSAS, MSA'lar) | Desteği bu proje türleri için sağlanan iki uzantılar Visual Studio Galerisi aracılığıyla: [Microsoft Analysis Services modelleme projeleri](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) ve [Microsoft Reporting Services projeler](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio). SSDT'yi destek veri depolama ve işleme iş yüküyle Visual Studio 2017'de de dahildir. |
| SQL Server Integration Services (SSIS) | Visual Studio 2017 desteği, SQL Server veri Araçları (SSDT) aracılığıyla kullanılabilir. Daha fazla bilgi için [SQL Server Integration Services blogu](https://blogs.msdn.microsoft.com/ssis/2017/08/23/ssis-designer-is-now-available-for-visual-studio-2017/). |
| Visual C++ | Visual Studio 2017, Visual Studio 2010 için geri Visual Studio'nun önceki sürümlerinde oluşturulmuş projeleri çalışmaya kullanabilirsiniz. Projeyi ilk kez açtığınızda, en son derleyici ve araç takımı yükseltmek veya özgün olanları kullanmaya devam etmek için seçeneğiniz vardır. Özgün olanları kullanmaya devam etmek seçtiğinizde, Visual Studio 2017 proje dosyasını değiştirmez ve projenizi oluşturmak için araç takımı'önceki Visual Studio yükleme kullanır. Özgün seçenekleri anlamına gelir tutma, hala proje Visual Studio özgün sürümünde gerekirse açabilirsiniz. Daha fazla bilgi için [yerel çoklu sürüm desteğinin Visual Studio'da eski projeleri oluşturmak için kullanmak](/cpp/porting/use-native-multi-targeting). |
| Visual Studio genişletilebilirlik/VSIX | MinimumVersion 14.0 veya daha az projeleri, projeyi önceki Visual Studio sürümlerinde açılmasını engelleyen MinimumVersion 15.0 bildirmek için güncelleştirilir. MinimumVersion önceki sürümlerinde açmak bir proje izin vermek için kümesine `$(VisualStudioVersion)`. Ayrıca bkz: [nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2017'ye geçirme](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md). |
| Visual Studio Laboratuvar Yönetimi | Microsoft Test Yöneticisi ya da Visual Studio 2010 SP1'i kullanabilirsiniz ve daha sonra herhangi bir bu sürümüyle oluşturduğunuz ortamları açabilirsiniz. Ancak, ortamları oluşturmadan önce Microsoft Test Yöneticisi'nin sürümü Team Foundation Server sürümü için Visual Studio 2010 SP1 eşleşmelidir. |
| Apache Cordova için Visual Studio Araçları | Projeleri Visual Studio 2017'de açılabilir ancak geriye dönük olarak uyumlu değildir. Visual Studio 2015'ten bir proje açıldığında, değişiklikler projenize izin istenir. Bu değişikliği yerine araç takımları kullanacak şekilde projeyi yükseltir bir `taco.json` Cordova kitaplığı, onun platformlar, kendi eklentiler ve düğüm/npm bağımlılıkları, sürüm oluşturmayı yönetmek için dosya. Bkz: [Geçiş Kılavuzu](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/first-steps/migrate-from-visual-studio-2015) daha fazla bilgi için. |
| Web dağıtımı (wdproj) | Destek için Web dağıtımı projeleri kaldırıldı Visual Studio 2012'de yayımlama profili desteği olan'ın eklenmesiyle. Visual Studio 2017'de eşdeğeri olduğundan, bu gibi projeler için otomatik geçiş yolu yoktur. Bunun yerine, wdproj dosyasını bir metin düzenleyicisinde açın ve tüm özelleştirmeleri içine pubxml kopyala-yapıştır (Yayımlama profilini) dosya çubuğunda açıklandığı [StackOverflow](https://stackoverflow.com/a/12061065/1203388). Ayrıca bkz: [planları Web sitesi ve web dağıtımı projeleri ilgili](https://blogs.msdn.microsoft.com/webdev/2012/08/06/plans-regarding-website-projects-and-web-deployment-projects/). |
| Windows Communication Foundation, Windows Workflow Foundation | Bu projeyi Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 ve Visual Studio 2012 açabilirsiniz |
| Windows Presentation Foundation | Bu proje, Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 içinde açabilirsiniz. |
| Windows Store/telefon uygulamaları | Windows Store 8.1 ve 8.0 ve Windows Phone 8.1 ve 8.0 projeleri Visual Studio 2017'de desteklenmez. Bu uygulamaları korumak için Visual Studio 2015 kullanmaya devam edin. Windows Phone 7.x projelerini korumak için Visual Studio 2012 kullanın. |

## <a name="how-visual-studio-decides-when-to-migrate-a-project"></a>Visual Studio zaman bir projeyi geçirmek nasıl karar verir

Visual Studio'nun her yeni sürümü, aynı projede açıldı, değiştirilebilir ve farklı sürümler arasında oluşturulan şekilde önceki sürümlerle uyumluluk sağlamak genel olarak arar. Ancak, kaçınılmaz değişiklikler var. zamanla sağlayacak şekilde bazı proje türleri artık desteklenmiyor (Bkz [Platform hedefleme ve Uyumluluk](/visualstudio/productinfo/vs2017-compatibility-vs) için proje türleri Visual Studio 2017'de desteklenir.) Bu gibi durumlarda, daha yeni bir sürümü Visual Studio'nun projeyi yüklenmiyor ve bir geçiş yolu sunmaz; önceki bir sürümünü destekleyen Visual Studio projede korumak gerekir.

Diğer durumlarda, Visual Studio'nun daha yeni sürümü bir proje açın ancak gerekir güncelleştirin veya, önceki sürümlerle uyumlu işleyebilir şekilde projede geçirin. Visual Studio, bu geçiş gerekli olup olmadığını belirlemek için bir dizi ölçütü kullanır:

- Visual Studio 2013 RTM için geri platformu sürümlerinde veritabanı hedef ile uyumluluk.

- Visual Studio'nun önceki sürümleriyle uyumluluk tasarım zamanı varlıklar. (Yani farklı kanallar Visual Studio 2017'in; Visual Studio 2015 RTM ve güncelleştirme 3; Visual Studio 2013 RTM ve güncelleştirme 5; Visual Studio 2012 güncelleştirme 4; Visual Studio 2010 SP 1.) Visual Studio 2017 önceki sürümleri yine de projeyi açabilirsiniz, düzgün bir şekilde kullanım dışı tasarım zamanı varlıklarla bunları bozan olmadan başarısız amaçlar.

- Olup yeni tasarım zamanı varlıkları güncelleştirme 5 içeren Visual Studio 2013 RTM & Aşağı önceki sürümlerle uyumluluk sonu.

Söz konusu proje türü mühendislik sahibi bu ölçütlerin görünür ve burada desteği, uyumluluk, çağrı yapar ve geçiş açısından. Tekrar Visual Studio sürümleri arasında saydam uyumluluk mümkün olduğunda, bunun anlamı oluşturabilir ve bir sürümü Visual Studio projelerinde değiştirebilirsiniz ve diğer sürümlerinde de çalışır duruma korumak Visual Studio dener.

Böyle uyumluluk mümkün değilse, ancak olarak bu makalede açıklanan proje türlerinden bazıları ile sonra Visual Studio tek yönlü gerekli değişiklikleri yapmak için Yükseltme Sihirbazı açılır.

Tek yönlü tür değişiklikler değiştirilmektedir `ToolsVersion` MSBuild'ın tam olarak hangi sürümünü gösterir. proje dosyasındaki özelliği projenin kaynak kodu, sonuçta istediğiniz çalıştırılabilir ve dağıtılabilir yapıtları kapatabilir. Diğer bir deyişle, hangi bir proje, Visual Studio'nun önceki sürümüyle uyumsuz işler değil *Visual Studio* sürümü, ancak *MSBuild* tarafından belirlenen şekilde bir sürümünü `ToolsVersion`. Visual Studio sürümünüzle eşleşen MSBuild araç zinciri içeriyor sürece `ToolsVersion` bir projede, Visual Studio Projeyi derlemek için bu araç zinciri çağırabilirsiniz.

Eski sürümlerinde oluşturulmuş projeleri maksimum uyumluluğu korumak için Visual Studio 2017 desteği için gerekli MSBuild araç zincirlerinden içerir `ToolsVersion` 15, 14, 12 ve 4. Aşağıdakilerden herhangi birini kullanan projeler `ToolsVersion` değerler, başarılı bir derleme içinde neden. (Yine, Visual Studio 2017 proje türü hiç üzerinde açıklandığı destekleyip desteklemediği için konu [Platform hedefleme ve Uyumluluk](/visualstudio/productinfo/vs2017-compatibility-vs).)

El ile güncelleştirin veya bir proje için yeni bir geçiş denemelisiniz olup bu bağlamda soru doğal olarak ortaya `ToolsVersion` değeri. Bu tür bir değişikliğin yapılması gerekli değildir ve büyük olasılıkla çok sayıda hata ve yeniden oluşturmak için proje almak düzeltmek için gereken uyarılar üretir. Ayrıca, Visual Studio için belirli bir destek düşerse `ToolsVersion` gelecekte projeyi açarak project geçiş işlemi olduğundan, özellikle tetikleyecek `ToolsVersion` değer değiştirilmelidir. Böyle bir durumda, bu belirli proje türü için alt tam olarak değiştirilmesi için gerekenler bilir ve bu değişiklikleri otomatik olarak bu makalenin önceki bölümlerinde açıklandığı şekilde yapabilirsiniz.

# <a name="next-steps"></a>Sonraki adımlar

Daha fazla açıklama için şu makalelere göz atın:

- [ToolsVersion Kılavuzu](../msbuild/msbuild-toolset-toolsversion.md)
- [Framework Kılavuzu hedefleme](../ide/visual-studio-multi-targeting-overview.md)

## <a name="see-also"></a>Ayrıca bkz.

[Proje geçiş ve yükseltme reference for Visual Studio 2019 Önizleme](port-migrate-upgrade-visual-studio-projects-2019.md)
