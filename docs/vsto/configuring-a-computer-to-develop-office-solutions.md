---
title: Office çözümleri geliştirmek için bilgisayarı yapılandırma
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 19c7e012775ff1a761b5c267f05b8f7ff250d5c6
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672232"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Office çözümleri geliştirmek için bilgisayarı yapılandırma

VSTO eklentileri ve Microsoft Office özelleştirmelerini oluşturmak için Visual Studio, .NET Framework ve Microsoft Office desteklenen bir sürümünü yükleyin.

|Yazılım|Desteklenen sürümler|
|--------------|------------------------|
|Visual Studio 2017| Herhangi bir sürümü ile **Office/SharePoint geliştirme** iş yükü.|
|.NET Framework|-.NET Framework 4 veya üzeri.|
|Microsoft Office|<ul><li>Office Professional Plus için Office 365 dahil olmak üzere Office Paket sürümü.</li><li>Herhangi biri aşağıdaki tek başına uygulamalar:<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 ve Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Proje</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) Office'in bir parçası yüklü olmalıdır. **Önemli:** Tıkla-Çalıştır Office 2010 uygulamalarının sürümleri desteklenmez.|

Ayrıntılı yükleme adımları için bkz [nasıl yapılır: Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Proje şablonları görünmez ya da Visual Studio'da iş yok

Visual Studio, .NET Framework ve Microsoft Office desteklenen bir sürümü yükleyin, ancak Office proje şablonları ya da Visual Studio'da görünür olmayan **yeni proje** iletişim kutusu veya bir kullanmaya çalıştığınızda bir hata alıyorsunuz aşağıdakileri denetleyin:

- Microsoft Office geliştirici araçları yüklü olduğundan emin olun.

     Office geliştirici araçları, Visual Studio'nun isteğe bağlı bir bileşenidir, ancak Visual Studio ile birlikte otomatik olarak yüklenir. Hangi özelliğin yükleneceğini belirterek Visual Studio yüklemesini özelleştirirseniz, seçtiğiniz emin **Microsoft Office geliştirici araçları** araçlarını yüklemek için Kurulum sırasında.

     Bu araçların yüklendiğinden emin olmak için Visual Studio Kurulum programını başlatın ve seçin **Değiştir** düğmesi. Seçin **Microsoft Office geliştirici araçları** onay kutusunu işaretleyin ve ardından **güncelleştirme** düğmesi.

- Tıkla-Çalıştır tarafından dağıtılan Office sürümü çalıştırmadığınızı emin olun. Bkz: [nasıl yapılır: Outlook bir bilgisayardaki bir Tıkla-Çalıştır uygulaması olup olmadığını](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Microsoft Office yalnızca bir sürümü çalıştırdığınızdan emin olun.

Sorun yaşamaya devam ederseniz bkz [Office çözümlerindeki hatalar için ek destek](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Ayrıca bkz.

[Başlama &#40;Visual Studio'da Office geliştirme&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Nasıl yapılır: Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yükleme](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Nasıl yapılır: yükleme Office birincil birlikte çalışma derlemeleri](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Office uygulaması ve proje türüne göre kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md)
