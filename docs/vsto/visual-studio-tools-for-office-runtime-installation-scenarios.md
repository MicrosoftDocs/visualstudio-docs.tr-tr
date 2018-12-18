---
title: Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ebf335291246ac8c3c15d8f04fb064a3bfaa8ef7
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670903"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları
  Office çalışma zamanı için Visual Studio 2010 Araçları üç şekilde yükleyebilirsiniz:  
  
- Visual Studio yüklediğinizde.  
  
- Microsoft Office yüklediğinizde.  
  
- Office çalışma zamanı yeniden dağıtılabilir için Visual Studio 2010 araçları yüklediğinizde.  
  
  Yüklü çalışma zamanı bileşenleri bilgisayarın ve yükleme senaryosu yapılandırmasına bağlıdır.  
  
## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Her yükleme senaryosunda yüklü çalışma zamanı bileşenleri  
 Office çalışma zamanı için Visual Studio 2010 Araçları üç bileşeni vardır: Office çözüm yükleyicisini ve .NET Framework 3.5 için Office uzantıları için Office uzantılarını [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri. Office çözüm yükleyicisini, her zaman çalışma zamanını yüklediğinizde yüklenir. .NET Framework için Office uzantılarının yüklenmesini bilgisayarın ve yükleme senaryosu yapılandırmasına bağlıdır. Çalışma zamanı ilk yüklendiğinde bir Office uzantılarının yüklenemez, belirli gereksinimleri karşılandığında çalışma zamanı otomatik olarak eksik Office uzantıları daha sonra yüklenir. Bu özellik çalışma zamanının adlı *isteğe bağlı yükleme*.  
  
 Aşağıdaki tabloda, varsayılan olarak her çalışma zamanı yükleme senaryoları hangi çalışma zamanı bileşenlerinin yüklendiğini gösterir. Her senaryo hakkında daha fazla bilgi daha sonra görünür.  
  
|Çalışma zamanı yükleme senaryoları|Office çözüm yükleyicisi|.NET Framework 3.5 için Office uzantıları|İçin Office uzantıları [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|İçin Office uzantıları [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|  
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|  
|İle [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] ve üzeri|Evet|.NET Framework 3.5 yüklü ise, Evet.|Evet|Evet|  
|ile [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Evet|.NET Framework 3.5 yüklü ise, Evet.|Hayır|Hayır|  
|Office 2010 Service Pack 1 (SP1) veya üzeri|Evet|.NET Framework 3.5 yüklü ise, Evet.|Evet, varsa [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] zaten yüklü.|Hayır|  
|Çalışma zamanı yeniden dağıtılabilir|Evet|Evet, .NET Framework 3.5 yüklü ise|Evet, varsa [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] zaten yüklü.|Evet, varsa [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] zaten yüklü.|  
  
### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Visual Studio veya Microsoft Office geliştirici araçları ile çalışma zamanı için Visual Studio yükleme  
 Visual Studio'da Office uzantıları için Office geliştirici araçları yüklediğinizde [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ve [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] her zaman geliştirme bilgisayarına yüklenir. .NET Framework 3.5 için Office uzantılarını, yalnızca .NET Framework 3.5 zaten geliştirme bilgisayarında mevcutsa yüklenir. Yükledikten sonra .NET Framework 3.5 yüklerseniz [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], oluşturduğunuz bir Office projesi, ilk kez .NET Framework 3.5 hedefi .NET Framework 3.5 için Office uzantılarını çalışma zamanı otomatik olarak yükler.  
  
> [!WARNING]  
>  Kullanarak .NET Framework 3. 5'i hedefleyen bir Office projesi oluşturulamıyor [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] veya üzeri.  
  
 Office Geliştirici Araçları'nı yükleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
### <a name="install-the-runtime-with-office"></a>Office çalışma zamanı yükleme  
 Office yüklediğinizde, bilgisayarda .NET Framework 3.5 zaten varsa, .NET Framework 3.5 için Office uzantılarını yüklenir. .NET Framework 3.5 sonra Office yüklerseniz, çalışma zamanı bir çözümü hedefleyen .NET Framework 3.5 yüklemek için bir Office uygulaması çalışır .NET Framework 3.5 ilk saat için Office uzantıları otomatik olarak yükler.  
  
 İçin Office uzantılarını [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki sürümü Office ile yüklü değil bile [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra zaten Office yüklediğinizde mevcuttur.  
  
 İçin Office uzantılarını [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Office ile birlikte yüklenir. Son kullanıcılar için Office uzantılarını elde edebilirsiniz [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] bir Windows güncelleştirmesi yükleyerek.  
  
 Kullanıcılarınızın uygulamanızı kullanmak için gerekli genişletmeleri olmasını sağlamak için Office çalışma zamanı, çözümünüz için bir önkoşul olarak yeniden dağıtılabilir için Visual Studio 2010 Araçları en son sürümünü içerir. Önkoşullar hakkında daha fazla bilgi için bkz. [Office çözüm dağıtım önkoşullarını](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Çalışma zamanı yeniden dağıtılabilir çalışma zamanı'nı kullanarak yükleme  
 Office çalışma zamanı yeniden dağıtılabilir için Visual Studio 2010 Araçları el ile çalıştırarak veya bir Office çözümünü dağıttığınızda yeniden dağıtılabilir önkoşul olarak dahil olmak üzere, çalışma zamanı yükleyebilirsiniz.  
  
 Office çalışma zamanı yeniden dağıtılabilir ve .NET Framework 3.5 için Office uzantıları için Office uzantıları için Visual Studio 2010 araçları kullanarak çalışma zamanını yüklediğinizde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki sürümü, yüklü karşılık gelen .NET sürümleri Framework zaten mevcut. Çalışma zamanı yüklü olduğunda bilgisayarda .NET Framework'ün bu sürümlerinden birini eksikse, eksik sürümü .NET Framework için Office uzantılarını o anda yüklü değil. Eksik daha sonra .NET Framework sürümünü yüklerseniz, çalışma zamanı karşılık gelen Office uzantıları (çalışma zamanı dağıtıldığı bir çözüm ile yüklenmiş uzantıları gerektiren bir çözüm yüklendikten sonraki açışınızda otomatik olarak yükler. ClickOnce kullanarak) veya (çalışma zamanı, Windows Installer kullanarak dağıtılan bir çözüm ile yüklenmişse) yüklendi.  
  
 Bir ClickOnce çözümde Önkoşullar da dahil olmak üzere daha fazla bilgi için bkz: [nasıl yapılır: son kullanıcı bilgisayarlarında Office çözümlerinin çalışması için Önkoşulları Yükleme](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98). Çalışma zamanı yeniden dağıtılabilir paketi el ile yükleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yükleme](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Office çalışma zamanı için Visual Studio araçlarındaki derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)  
  
  