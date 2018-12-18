---
title: Projeler ve Çözümler
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.savedeferredsaveprojectonclose
- vs.untrustedtemplateopeningdocuments
- Project Properties.FullPath
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.getopenfilename
- vs.addnewitem
- vs.encoding
- vs.addexistingitem
- Project Properties.URL
- VS.SolutionExplorer
- Project Properties.FileName
- SolutionProperties.Name
- VS.SaveChangesDlg
- vs.newproject
- VS.SolutionExplorer.Selection
- SolutionProperties.Path
- vs.getdirectoryname
- vs.addexistingsolutionitem
- SolutionProperties.Description
- vs.environment.solutions
- vs.saveordiscarddeferredsaveproject
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- vs.solutionpropertypages
- vs.solutionpropertypages.startupproject
- vs.solutionpropertypages.configurationsettings
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- workspaces
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- vs.solutionpropertypages.projectdependencies
- applications [Visual Studio]
- projects [Visual Studio], setting up
- miscellaneous files
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 068fe27df565f83312040fa0bcf6412e4984d9fd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067148"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio’da Çözümler ve Projeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oluşturduğunuz sırada bir uygulama, uygulama, Web sitesi, Web uygulaması, betik, eklenti, vb. ile başlamanız Visual Studio'da bir *proje*. Mantıksal bir anlamda, tüm kaynak kodu dosyaları, simgeler, görüntü, veri dosyaları ve diğer her şey bir yürütülebilir programı veya web sitesi derlenecek, aksi takdirde derleme gerçekleştirmek için gerekli bir proje içerir.  Bir proje, ayrıca tüm derleyici ayarlarını ve çeşitli hizmetler veya programınızın iletişim kuracağı bileşenleri tarafından gerekebilecek diğer yapılandırma dosyalarını içerir.

 Bir değişmez değer anlamda bir proje bir XML dosyasıdır (*.vbproj, \*.csproj, \*.vcxproj) tanımlayan bir sanal klasör hiyerarşisi yolları birlikte "içerdiği" tüm öğeler ve tüm yapı ayarları için. Visual Studio'da proje dosyası, proje içeriğini ve ayarlarını görüntülemek için Çözüm Gezgini tarafından kullanılır. Projenizi derlerken, MSBuild altyapısına yürütülebilir dosyayı oluşturmak için proje dosyasını kullanır. Çıkış diğer tür projelere ürün de özelleştirebilirsiniz.

 Bir proje, mantıksal açıdan ve dosya sistemi içinde bulunan bir *çözüm*, yapı bilgilerini, Visual Studio penceresi ayarlarını ve olmayan diğer tüm dosyalar yanı sıra bir veya daha fazla proje içerebilir herhangi bir proje ile ilişkili. Bir değişmez değer anlamda çözüm, kendi benzersiz bir biçime sahip bir metin dosyasıdır; Bu genellikle el ile düzenlenmesi kullanılmaya yönelik değildir.

 Bir çözüm ayarları, tercihleri ve projede çalıştığı her bir kullanıcı için yapılandırma bilgilerini depolayan bir ilişkili *.suo dosyası vardır.

 Aşağıdaki diyagramda, projeler ve çözümler ve mantıksal olarak içerdikleri öğeleri arasındaki ilişkiyi gösterir.

 ![Visual Studio projeleri ve çözümleri](../ide/media/vs2015-project-diagram.png "vs2015_project_diagram")

 Özel proje ve öğe şablonlarını da oluşturabilirsiniz. Daha fazla bilgi için [oluşturma proje ve öğe şablonları](../ide/creating-project-and-item-templates.md).

## <a name="creating-new-projects"></a>Yeni proje oluşturma
 Önceden oluşturulan kod dosyaları, yapılandırma dosyaları, varlıkları temel kümesinden oluşan bir önceden tanımlanmış proje şablonu ile başlatmak için yeni bir proje oluşturmak için en kolay yolu olan ve size ayarları başlatılan uygulama veya Web sitesinde belirli bir tür oluşturarak bir belirli programlama dili. Bu şablonları bölümüne bakın, **yeni proje iletişim kutusu** seçtiğinizde **dosya &#124; yeni &#124; proje** veya **dosya &#124; yeni &#124; Web sitesi** gelen ana menü ve ardından gidin. Daha fazla bilgi için [projeler ve çözümler oluşturma](../ide/creating-solutions-and-projects.md) ve [NIB oluşturma proje şablonları](http://msdn.microsoft.com/en-us/7c36d86a-6b79-4480-8228-0f925f1204b2).

## <a name="managing-projects-in-solution-explorer"></a>Çözüm Gezgini'nde projeleri yönetme
 Yeni bir proje oluşturduğunuzda, kullandığınız **Çözüm Gezgini** projeleri ve çözümleri ve onların ilişkilendirilmiş öğelerini görüntülemek ve yönetmek için. Aşağıdaki çizimde, iki proje içeren bir C# çözümü ile Sunucu Gezgini gösterir.

 ![Çözüm Gezgini](../ide/media/vs2015-solution-explorer.png "vs2015_solution_explorer")

## <a name="in-this-section"></a>Bu Bölümde

-   [Çözümler ve Projeler Oluşturma](../ide/creating-solutions-and-projects.md)

-   [Proje öğeleri ekleme ve kaldırma](../ide/adding-and-removing-project-items.md)

-   [Proje ve Çözüm Özelliklerini Yönetme](../ide/managing-project-and-solution-properties.md)

-   [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)

-   [Uygulama Özellikleri](../ide/application-properties.md)

-   [Derleme ve Bildirim İmzalamayı Yönetme](../ide/managing-assembly-and-manifest-signing.md)

-   [Nasıl Yapılır: Uygulama Simgesi Belirtme (Visual Basic C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)

-   [Belirli Bir .NET Framework Sürümünü Hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md)

-   [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio IDE](../ide/visual-studio-ide.md)
