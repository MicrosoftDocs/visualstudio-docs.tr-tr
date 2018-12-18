---
title: Yayımlama Sihirbazı (Visual Studio'da Office Geliştirme)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0d1b72745b3bd8a24dc69a5bc4e1508c8b2f7571
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672762"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Yayımlama Sihirbazı (Visual Studio'da Office Geliştirme)
  Kullanım **Yayımlama Sihirbazı** çözüm dosyaları belirtilen bir konuma kopyalamak için bildirim dosyalarını oluşturmak ve bir Kurulum programı oluşturma.  
  
 Bu Sihirbazı'na erişmek için **derleme** menüsünde seçin **Yayımla** *SolutionName*. Ayrıca erişebileceğiniz **Yayımlama Sihirbazı** gelen **Çözüm Gezgini**. Proje düğümü için kısayol menüsünü açın ve ardından **Yayımla**.  
  
 Aşağıdaki bölümde her bir sayfasında açıklar.  
  
## <a name="where-do-you-want-to-publish-the-application"></a>Burada uygulamayı yayımlamak istiyor musunuz?  
 **Bu uygulamayı yayımlamak için konumu belirtin**  
 Gerekli. Yayımlama konumunun dizinidir burada **Yayımlama Sihirbazı** derlemeden bildirimleri, derlemeleri, geçici sertifika ve diğer dosyalar gibi çözüm dosyalarını kopyalar. Bu dizine yazma erişimi olmalıdır.  
  
 Bir disk yolu, dosya paylaşımı, FTP sitesi veya web sitesi URL'si bir konum yazın ya da tıklayın **Gözat** konumu için Gözat düğmesini. Yol, aşağıdaki biçimlerde olabilir:  
  
- Göreli veya mutlak bir yol standart Windows, aşağıdakiler gibi biçimlendirme *C:\Deploy\MyApplication* veya *\MyApplication*.  
  
- Bir Evrensel Adlandırma Kuralı (UNC) yolu gibi  *\\\ServerName\MyApplication\\*.  
  
- Gibi bir URL bir web sitesi http://www.microsoft.com/MyApplication.  
  
  Varsayılan olarak, yayımlama konumdur *http://localhost/projectname/* IIS yüklü veya bunu yaparsanız yayınla\ dizini IIS yüklü.  
  
> [!NOTE]  
>  Hedef bilgisayarın Windows Vista çalıştırıyorsa, daha fazla ilgili önemli noktalar vardır. Yerel yayımlama seçeneğini kullanmak için Windows Vista bilgisayarda yönetici olması gerekir. Ayrıca, her zaman varsayılan konumu: *yayımlama\\*  IIS yüklü olup olmadığından bağımsız olarak dizin.  
  
## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Son kullanıcı bilgisayarlarında varsayılan yükleme yolu nedir?  
 Yükleme yolu isteğe bağlıdır. İsterseniz, yükleme yolu daha sonra ayarlayabilirsiniz. Ayrıntılar için bkz [nasıl yapılır: bir Office çözümünü yükleme yolunu değiştirmek](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 Yükleme yolu, son kullanıcının özelleştirme yükleyecek dizindir. Ayrıca çözüm güncelleştirmeleri denetlemek için kullanacağı yoludur. **Yayımlama Sihirbazı** çözüm yolu, girdiğiniz aynı olmadığı sürece bu konuma dağıtmaz **bu uygulamayı yayımlamak için konumu belirtin** önceki sayfada kutusu.  
  
 **Bir Web sitesinden**  
 Son kullanıcıların çözümü yüklemek için izleyeceği URL'sini belirtin.  
  
 **Bir UNC yolu veya dosya paylaşımından**  
 Son kullanıcıların çözümü yüklemek için izleyeceği UNC yolunu belirtin.  
  
 **Bir CD-ROM veya DVD-ROM'dan**  
 Bu seçenek, bir yükleme yolu gerektirmez.  
  
 Visual Studio, CD veya DVD yazma değil. Çıktı bir CD veya DVD elle kopyalamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Yayımlama Sayfası, Proje Tasarımcısı &#40;Visual Studio'da Office geliştirme&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)  
  
  