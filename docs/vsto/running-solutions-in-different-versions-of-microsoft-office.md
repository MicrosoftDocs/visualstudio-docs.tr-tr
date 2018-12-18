---
title: Çözümleri Microsoft Office'in farklı sürümlerinde çalıştırma
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ed8a9b7cc78b0605b7fcc3931a7ee8992360125b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676746"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Çözümleri Microsoft Office'in farklı sürümlerinde çalıştırma
    
## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Visual Studio 2010 kullanarak ve yukarıda oluşturulan Office çözümlerini çalıştırma  
  
|Proje şablonu tarafından hedeflenen Office sürümü|Hedef .NET Framework projesinin<sup>1</sup>|Çözümü çalıştırmadan Office sürümleri|Son kullanıcı bilgisayarda gerekli çalışma zamanı|  
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|  
|Office 2016 ve [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistemi<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistemi<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools for Office Runtime|  
|2007 Microsoft Office sistemi|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki sürümlerde,<br /><br /> veya<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistemi|Visual Studio 2010 Tools for Office Runtime|  
  
 1. .NET Framework sürümü, projenizin hedeflediği işletim sistemi, son kullanıcı bilgisayarlarında çözümünüzün çalışması için gereklidir. Örneğin, projeniz .NET Framework 3.5 olmasını istiyorsanız, son kullanıcı bilgisayarlarında .NET Framework 3.5 gereklidir. Bu örnekte, çözümünüzü yalnızca çalışmaz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] son kullanıcı bilgisayarlarında yüklü.  
  
 2. Yalnızca yeni özellikleri kullanmıyorsa bu senaryoda, çözüme hatasız 2007 Microsoft Office sistemi içinde çalışır [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Visual Studio'nun Visual Studio 2010'dan önceki sürümleri kullanılarak oluşturulan Office çözümlerini çalıştırın  
 Microsoft Office uygulamaları, Visual Studio'nun Visual Studio 2010'dan önceki sürümlerini kullanarak oluşturulan çözümleri çalıştırabilirsiniz. Bazı durumlarda, bu çözümleri farklı sürümlerini gerektirir. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Farklı sürümlerini [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aynı bilgisayarda yan yana yüklenebilir.  
  
 Aşağıdaki tablo, Visual Studio'nun önceki sürümlerini kullanarak oluşturulan çözümleri Microsoft Office'in hangi sürümünü çalıştırabilir ve hangi sürümlerinin gösterir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ve her çözüm için .NET Framework gereklidir.  
  
|Visual Studio çözümü oluşturmak için kullanılan sürüm|Proje şablonu tarafından hedeflenen Office sürümü|Çözümü çalıştırmadan Office sürümleri|Son kullanıcı bilgisayarda gerekli çalışma zamanı|Son kullanıcı bilgisayarda gerekli .NET Framework sürümü|  
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> veya<br /><br /> Visual Studio Team System 2008|2007 Microsoft Office sistemi|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> 2007 Microsoft Office sistemi|Visual Studio 2010 Tools for Office Runtime<sup>1</sup><br /><br /> veya<br /><br /> Microsoft Office sistemi için Visual Studio Araçları (sürüm 3.0 çalışma zamanı)|.NET Framework 3.5|  
|Visual Studio 2005 VSTO 2005 SE ile aşağıdaki sürümlerden birine<sup>2</sup> yüklü:<br /><br /> -Office için visual Studio 2005 Araçları<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 Professional|2007 Microsoft Office sistemi|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (yalnızca 32-bit<sup>3</sup>)<br /><br /> 2007 Microsoft Office sistemi|Office için Visual Studio 2005 Araçları Second Edition çalışma zamanı|.NET framework 2.0, .NET Framework 3.0 veya .NET Framework 3.5|  
|Aşağıdaki sürümlerinden herhangi birindeki Visual Studio'nun:<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />-Office için visual Studio 2005 Araçları (VSTO 2005 SE olmadan ya da ile<sup>2</sup> yüklü)<br />-Visual Studio Team System 2005 (ile veya olmadan VSTO 2005 SE<sup>2</sup> yüklü)<br />-VSTO 2005 SE visual Studio 2005 Professional<sup>2</sup> yüklü|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (yalnızca 32-bit<sup>3</sup>)<br /><br /> 2007 Microsoft Office sistemi<br /><br /> Microsoft Office 2003|Office için Visual Studio 2005 Araçları Second Edition çalışma zamanı|.NET framework 2.0, .NET Framework 3.0 veya .NET Framework 3.5|  
  
 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] uygulamalar, Office çalışma zamanı için Visual Studio 2010 araçları içerir. Bu nedenle, bu uygulamalar her zaman Office çalışma zamanı için Visual Studio 2010 Araçları yerine Visual Studio Araçları Microsoft Office sistemi için kullanın (sürüm 3.0 çalışma zamanı) Bu senaryoda. 2007 Microsoft Office sistemi uygulamalarda, Office çalışma zamanı veya Microsoft Office sistemi için Visual Studio Araçları için Visual Studio 2010 araçları kullanabilir (sürüm 3.0 çalışma zamanı).  
  
 2. VSTO 2005 SE Microsoft Office 2003 ve 2007 Microsoft Office sistemi için VSTO eklentisi proje şablonlarını sağlayan ücretsiz bir Visual Studio eklentisidir. Visual Studio 2005 Professional, Office için Visual Studio 2005 Araçları veya Visual Studio Team System 2005'teki bir sürüm ile yüklenebilir. Daha fazla bilgi için [Visual Studio 2005 Tools for Office İkinci Sürüm](http://go.microsoft.com/fwlink/?LinkId=148446).  
  
 3. Visual Studio 2005 araçları Office Second Edition Runtime gerektiren office çözümleri 64-bit sürümleriyle uyumlu değildir [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. 64-bit sürümünde bu çözümleri çalıştırmak için [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] veya [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], projeyi yükseltmeniz gerekir [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] veya 2007 Microsoft Office sistemi hedefleyen bir Visual Studio 2008 projeye.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)   
 [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  