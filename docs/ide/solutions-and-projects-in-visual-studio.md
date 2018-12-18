---
title: Projeler ve çözümler
ms.date: 10/05/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.newproject
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items [Visual Studio]
- solutions [Visual Studio]
- project items [Visual Studio]
- solutions [Visual Studio], designing
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db576170443952a3090d57fc8046b34428cc8095
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348334"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio'da projeler ve çözümler

Bu makalede bu kavramı bir *proje* ve *çözüm* Visual Studio'da. Yeni bir proje oluşturmak nasıl de kısaca ele alınmaktadır ve **Çözüm Gezgini** araç penceresi.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [projeler ve çözümler Mac için Visual Studio'da](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projeler

Web sitesi, eklenti, vb. bir uygulama oluşturduğunuzda, Visual Studio'da ile başlatma bir *proje*. Mantıksal bir anlamda, bir projenin tüm kaynak kodu dosyaları, simgeler, resimler, veri dosyalarını, bir yürütülebilir dosya, kitaplık veya Web sitenize derlenmiş vb. içerir. Bir proje, derleyici ayarları ve çeşitli hizmetler veya programınızın iletişim kuran bileşenler tarafından gerekebilecek diğer yapılandırma dosyalarını da içerir.

> [!NOTE]
> Çözümlerin veya projelerin düzenlemek, yapı ve kod hatalarını ayıklamak için Visual Studio'da kullanmak zorunda değilsiniz. Yalnızca Visual Studio kaynak dosyalarını içeren klasörü açın ve düzenlemeye başlayın. Daha fazla bilgi için [kod Visual Studio'da projeler veya çözümler olmadan geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Bir proje uzantılı bir XML dosyasında aşağıdaki gibi tanımlanır *.vbproj*, *.csproj*, veya *.vcxproj*. Bu dosya, projedeki tüm öğeleri yolları ve sanal klasör hiyerarşisi içerir. Ayrıca, yapılandırma ayarlarını içerir.

> [!TIP]
> Visual Studio'da bir proje dosyasının içeriğini bakmak için ilk proje adlarında'i seçerek projeyi **Çözüm Gezgini** seçip **kaldırma proje** bağlamı veya sağ tıklama menüsünde. Daha sonra yeniden bağlam menüsünü açın ve seçin **Düzenle \<projectname\>**.

Visual Studio'da proje dosyası tarafından kullanılan **Çözüm Gezgini** proje içeriğini ve ayarlarını görüntülemek için. Projenizi derlerken, MSBuild altyapısına yürütülebilir dosyayı oluşturmak için proje dosyasını kullanır. Çıkış diğer türleri üretmek için projeleri de özelleştirebilirsiniz.

## <a name="solutions"></a>Çözümler

Bir proje içinde yer alan bir *çözüm*. Adını rağmen bir çözüm "yanıt" değildir. Bu yalnızca bir veya daha fazla ilgili projelerini, yapı bilgilerini, Visual Studio penceresi ayarlarını ve belirli bir proje ile ilişkili olmayan diğer tüm dosyalar yanı sıra bir kapsayıcıdır. Bir metin dosyası tarafından açıklanan bir çözüm (uzantı *.sln*) kendi benzersiz biçimde; bunu el ile düzenlenmesi amaçlanmaz.

Visual Studio kullanan iki dosya türleri (*.sln* ve *.suo*) çözümleri için ayarları saklamak için:

|Dahili numara|Ad|Açıklama|
|---------------|----------|-----------------|
|.sln|Visual Studio çözümü|Projeler, proje öğeleri ve çözümde çözüm öğeleri düzenler.|
|.suo|Çözüm kullanıcı seçenekleri|Kullanıcı düzeyi ayarları ve kesme noktaları gibi özelleştirmelerini depolar.|

## <a name="create-new-projects"></a>Yeni projeler oluştur

Belirli bir tür uygulama veya Web sitesi için bir proje şablondan yeni bir proje oluşturmak için en kolay yolu başlatmaktır. Bir proje şablonu, önceden oluşturulan kod dosyaları, yapılandırma dosyaları, varlıkları ve ayarları temel bir kümesinden oluşur. Bu şablonları bölümüne bakın, **yeni proje** seçtiğinizde iletişim kutusu **dosya** > **yeni** > **proje**. Daha fazla bilgi için [çözümler ve projeler oluşturma](../ide/creating-solutions-and-projects.md).

Özel proje ve öğe şablonlarını da oluşturabilirsiniz. Daha fazla bilgi için [proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

## <a name="manage-projects-in-solution-explorer"></a>Çözüm Gezgini'nde projeleri yönetme

Yeni bir proje oluşturduğunuzda, kullanabileceğiniz **Çözüm Gezgini** proje ve çözüm ve onların ilişkilendirilmiş öğelerini görüntülemek ve yönetmek için. Aşağıdaki çizimde gösterildiği **Çözüm Gezgini** ile bir C# iki proje içeren bir çözümü:

![Çözüm Gezgini](../ide/media/vs2015_solution_explorer.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Projeler ve çözümler (Mac için Visual Studio)](/visualstudio/mac/projects-and-solutions)
- [Ekleme ve kaldırma proje öğeleri (Mac için Visual Studio)](/visualstudio/mac/add-and-remove-project-items)