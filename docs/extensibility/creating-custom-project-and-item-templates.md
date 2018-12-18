---
title: Özel proje ve öğe şablonları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eeea0f92fc846b6ed51673d22450b22e01b348eb
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497868"
---
# <a name="create-custom-project-and-item-templates"></a>Özel proje ve öğe şablonları oluşturma

Visual Studio SDK, bir özel Proje şablonu ve özel öğe şablonu oluşturma proje şablonları içerir. Bu şablonlar, bazı ortak parametresi değişimleri dahil ve zip dosyaları olarak oluşturun. Değil bunlar otomatik olarak dağıtılır ve deneysel örneğinde kullanılabilir değildir. Oluşturulan zip dosyası kullanıcı şablonu dizinine kopyalamanız gerekir.
  
Şablon oluşturma şablonları, daha büyük uzantılarında şablonları dahil sağlar. Bu kaynak dosyaları üzerinde sürüm denetimi uygulamak ve bir grup şablon projelerini bir VSIX paketi oluşturmanıza olanak sağlar.  
  
NuGet paketlerini yüklemek için bir şablon da yapılandırabilirsiniz. Daha fazla bilgi için [Visual Studio şablonları NuGet paketlerinde](/nuget/visual-studio-extensibility/visual-studio-templates).

Temel şablon oluşturma senaryoları için kullanmanız gereken **şablonu dışarı aktar** Sihirbazı'nı, ama için sıkıştırılmış bir dosya çıkarır. Temel şablon oluşturma hakkında daha fazla bilgi için bkz: [proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).  

> [!NOTE]
> Visual Studio 2017'den itibaren özel Proje ve öğe şablonları için tarama artık gerçekleştirilir. Bunun yerine, uzantı yükleme konumu olarak bu şablonları tanımlamak, şablon bildirim dosyalarını sağlamanız gerekir. VSIX uzantılarınızı güncelleştirmek için Visual Studio 2017'yi kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız, şablon bildirim dosyalarını el ile oluşturmanız gerekir. Daha fazla bilgi için [yükseltme Visual Studio 2017 için özel Proje ve öğe şablonlarını](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Şablon bildirim şeması belgelenen [Visual Studio şablon bildirim şeması başvurusu](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Bir proje şablonu oluşturma  
  
1.  Bir proje şablonu projesi oluşturun. Proje şablonunda bulabilirsiniz **yeni proje** iletişim kutusunda, Visual Basic veya Visual C# *genişletilebilirlik* klasör.  
  
     Şablon sınıf dosyası, bir simge oluşturur bir *.vstemplate* adlı bir düzenlenebilir proje dosyası dosyasında *ProjectTemplate.vbproj* veya *ProjectTemplate.csproj*ve bazı genellikle diğer proje türleri tarafından oluşturulan dosyaları gibi bir *resources.resx* dosyası bir *AssemblyInfo* dosyası ve bir *.settings* dosya. Her kod dosyası, uygun yerlerde genel parametresi değişimleri içerir.  
  
2.  Ekleme ve projeniz için gereken proje öğeleri kaldırın. Düzenlenebilir bir proje dosyasının kaldırmayın *AssemblyInfo* dosyası veya *.vstemplate* dosya.  
  
3.  Güncelleştirme *.vstemplate* herhangi ekleme ve silme işlemleri yansıtacak şekilde dosya. [Proje](../extensibility/project-element-visual-studio-templates.md) öğesi içermelidir bir [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) şablona dahil edilecek her bir dosya için öğesi.  
  
4.  Kod dosyalarınızı ve diğer kullanıcıya yönelik içeriği değiştirme ve uygun parametresi değişimleri ekleyin.  
  
5.  Oluşturulan içerik gerektiği gibi değiştirin.  
  
6.  Projeyi oluşturun.  
  
     Visual Studio oluşturur bir *.zip* şablonunuzu içeren dosya. Değil dağıtılan ve deneysel örneğinde kullanılabilir değil.  
  
## <a name="create-an-item-template"></a>Öğe şablonu oluşturma  
  
1.  Bir öğe şablonu projesi oluşturun.  
  
     Şablon sınıf dosyası, bir simge oluşturur bir *.vstemplate* dosyası ve bir *AssemblyInfo* dosya. Bazı ortak parametresi değişimleri sınıf dosyası içerir.  
  
2.  Ekleme ve projeniz için gereken proje öğeleri kaldırın.  
  
3.  Güncelleştirme *.vstemplate* herhangi ekleme ve silme işlemleri yansıtacak şekilde dosya. [Proje](../extensibility/project-element-visual-studio-templates.md) öğesi içermelidir bir [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) şablona dahil edilecek her bir dosya için öğesi.  
  
4.  Kod dosyalarınızı ve diğer kullanıcıya yönelik içeriği değiştirme ve uygun parametresi değişimleri ekleyin.  
  
5.  Oluşturulan içerik gerektiği gibi değiştirin.  
  
6.  Projeyi oluşturun.  
  
     Visual Studio, şablonunuzu içeren sıkıştırılmış bir dosya oluşturur. Değil dağıtılan ve deneysel örneğinde kullanılabilir değil.  
  
## <a name="deployment"></a>Dağıtım  
  
### <a name="to-deploy-the-project-or-item-template"></a>Proje veya öğe şablonu dağıtmak için  
  
1.  Bir VSIX projesi oluşturun. Daha fazla bilgi için [VSIX proje şablonu](../extensibility/vsix-project-template.md).  
  
2.  VSIX projesini başlangıç projesi olarak ayarlayın. İçinde **Çözüm Gezgini**, VSIX proje düğümünü sağ tıklatın ve seçin seçin **başlangıç projesi olarak ayarla**.  
  
3.  Proje şablonu projesi VSIX projesinin bir varlık ayarlayın. Açık *.vsixmanifest* dosya. Git **varlıklar** sekmesine **yeni**.  
  
    1.  Ayarlama **türü** alanı **Microsoft.VisualStudio.ProjectTemplate** veya **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Kaynağı için **mevcut çözümde bir proje** seçeneğini ve ardından şablonunuzu içeren projeyi seçin.  
  
4.  Derleme çözümü ve tuşuna **F5**. Deneysel örneği açılır.  
  
5.  Bir proje şablonu projesi için listelenen, proje şablonunu görmeniz gerekir **yeni proje** iletişim (**dosya** > **yeni**  >  **Proje**), Visual C# veya Visual Basic düğümü. Bir öğe Şablonu proje öğesi şablonunuzu listelenen görmeniz gerekir **Yeni Öğe Ekle** iletişim. Görüntülenecek **Yeni Öğe Ekle** iletişim kutusunda, gelen **Çözüm Gezgini**, proje düğümünü seçin ve tıklayın **Ekle** > **yeni öğe**).  
  
## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio şablon başvurusu](../ide/visual-studio-template-reference.md)  
[Visual Studio şablonları NuGet paketleri](/nuget/visual-studio-extensibility/visual-studio-templates)