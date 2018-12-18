---
title: Office çözümlerini geçirme ve yükseltme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5b86699f11ab59aaf0ef09f5c7ae52d69e41e96c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671748"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Office çözümlerini geçirme ve yükseltme
  Visual Studio'nun önceki bir sürümde oluşturulan Microsoft Office projeniz varsa, geçerli Visual Studio sürümlerinde kullanmak için projeyi yükseltmeniz gerekir. Microsoft Office projesini yükseltmek için bir Microsoft Office geliştirici araçlarını içeren Visual Studio sürümünde açın. Microsoft Office geliştirici araçlarını içeren Visual Studio sürümleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümlerle karşılaştırıldığında küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  
  
> [!NOTE]  
>  Visual Studio, Visual Studio'nun önceki sürümleri kullanılarak oluşturulan InfoPath form şablon projelerini yükseltemez. Bu tür projeler, Visual Studio'nun geçerli sürümünde desteklenmez.  
  
## <a name="changes-to-upgraded-projects"></a>Yükseltilen Projelerdeki değişiklikler  
 Visual Studio, Microsoft Office projesini yükselttiğinizde, aşağıdaki öğeleri hedefleyecek şekilde projeyi değiştirir:  
  
-   Office çalışma zamanı için Visual Studio 2010 Araçları. Daha fazla bilgi için [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Geçerli derleme referansları.  
  
-   (Visual Studio 2013'e yalnızca yükseltme sırasında) proje türü tarafından desteklenen .NET Framework sürümü.  
  
-   (Visual Studio 2013'e yalnızca yükseltme sırasında), proje türü tarafından desteklenen Microsoft Office sürümü.  
  
## <a name="assembly-references"></a>Derleme başvuruları  
 Visual Studio projede aşağıdaki derleme başvurularını yükseltir:  
  
-   Microsoft Office birincil birlikte çalışma derlemeleri (PIA).  
  
-   Derlemelerde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Bu derlemeler hakkında daha fazla bilgi için bkz. [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Bağımlı derlemelerin yeni veya güncelleştirilmiş sürümleri.  
  
## <a name="targeted-net-framework"></a>Hedeflenen .NET Framework  
 Bir projeyi Visual Studio 2013'e yükselttiğinizde, Visual Studio ya da hedeflemek için projeyi değiştirir [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] veya [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Projenin hedeflediği .NET framework sürümü hangi Office sürümü bilgisayarınızda yüklü bağlıdır. Varsa [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] olan yüklü Visual Studio hedeflemek için projeyi değiştirir [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Aksi takdirde, Visual Studio hedeflemek için projeyi değiştirir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
> [!NOTE]  
>  Geliştirme ve son kullanıcı bilgisayarlarında yeniden hedeflenen çözümü çalıştırmak için bazı ek adımlar gerçekleştirmeniz gerekebilir ve projeniz belirli özellikleri kullanıyorsa, artık derlemez. Daha fazla bilgi için [geçirme Office çözümlerini .NET Framework 4 veya sonraki bir sürüme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Hedefliyorsanız [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya Office projeleri daha sonra .NET Framework 3. 5'i hedeflediğiniz zaman kullanılamaz olan bazı özellikleri kullanabilirsiniz. Daha fazla bilgi için [tasarım ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="targeted-office-application"></a>Hedeflenen Office uygulaması  
 Visual Studio 2013 için Office projesini yükselttiğinizde, Visual Studio projenin belge düzeyi özelleştirme projesi veya VSTO eklenti projesi gibi proje türü tarafından desteklenen Microsoft Office sürümünü hedefleyecek şekilde değiştirir.  
  
 Office projeleri Visual Studio 2013'te [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] uygulamalar. Visual Studio yüklü office en son sürümünü hedeflemek için projeyi değiştirir. Bu Office sürümleri hiçbiri yüklü değilse, Visual Studio projeyi yükseltmez.  
  
> [!NOTE]  
>  Bir VSTO eklenti projesi hedefleyecek şekilde yükseltirseniz [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] veya daha sonra emin `ThisAddIn_Startup` VSTO eklentisi olay işleyicisi, uygulama bir belgeye erişen bir kod içermiyor. Daha fazla bilgi için [Office uygulaması başlatıldığında, bir belgeye erişme](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Belge düzeyi özelleştirmeleri için [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] dönüştürür sahip belgeler gibi ikili biçimi olan belgeleri bir projedeki bir *.xls* veya *.doc* Office Open XML biçimine uzantısı. Open XML hakkında daha fazla bilgi için bkz. [giriş yeni dosya adı uzantılarını ve açık XML biçimleri](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).  
  
> [!NOTE]  
>  Akıllı etiketler Excel 2010 ve Word 2010'da kullanım dışı bırakılmıştır. Çözümünüzü akıllı etiketler kullanılıyorsa, test edebilir ve Visual Studio 2013 veya Visual Studio 2015'te hata ayıklama önce bu nedenle, bunları kaldırmanız gerekir.  
  
## <a name="upgrade-microsoft-office-2003-projects"></a>Microsoft Office 2003 projelerini yükseltme  
 Belge düzeyi özelleştirmeleri ve Microsoft Office 2003'ü hedefleyen VSTO Add-Ins yükseltmek için bazı ek hususlar vardır.  
  
### <a name="document-level-projects"></a>Belge düzeyi projeleri  
 Projedeki belge Windows Forms denetimlerini içeriyorsa, ayrıca Office ikinci sürüm projeyi yükseltmeden önce çalışma zamanı için Visual Studio 2005 Araçları olmalıdır. Projeyi yükseltmeden önce çalışma zamanının bu sürümü geliştirme bilgisayarında yüklü değilse, yükseltilen proje derleme içeren veya çalışma zamanı hataları. Projenizi yükseltmeyi tamamladığınızda, başka bir Office çözümü tarafından kullanılmadığından, Visual Studio 2005 araçları Office Second Edition Runtime Geliştirme bilgisayarınızdan kaldırabilirsiniz. Çalışma zamanının bu sürümü Microsoft Download Center yeniden dağıtılabilir paket olarak kullanılabilir [için Microsoft Visual Studio 2005 araçları Office Second Edition Runtime (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
### <a name="vsto-add-in-projects"></a>VSTO eklentisi projeleri  
 Çözüm dosyası özgün projeniz için VSTO eklentisi yüklemek amacıyla yapılandırılan bir kurulum veya InstallShield Limited Edition projesi içeriyorsa, Visual Studio projeyi yükseltir, ancak projeye herhangi bir değişiklik yapmaz. VSTO eklenti dağıtmak için Windows Installer dosyasını kullanmaya devam etmek istiyorsanız, gibi yeni önkoşulları yüklemek için Kurulum veya InstallShield Limited Edition projesini değiştirmelisiniz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], Office çalışma zamanı için ve isteğe bağlı olarak Visual Studio 2010 Araçları VSTO eklenti tarafından başvurulan birincil birlikte çalışma bütünleştirilmiş kodları. Daha fazla bilgi için [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
 VSTO eklenti dağıtmak için ClickOnce kullanmak istiyorsanız, Kurulum veya InstallShield Limited Edition projesini tamamen silebilirsiniz. VSTO eklentileri ClickOnce kullanarak dağıtma hakkında daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: yükseltme Office çözümleri](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)   
 [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Proje yükseltme, Seçenekler iletişim kutusu](../vsto/project-upgrade-options-dialog-box.md)  
  
  