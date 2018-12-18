---
title: Visual Studio 2015 SDK yenilikler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb7f3e98f0860d05c879a81fb14f05142678baae
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055708"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Hangi&#39;'teki Visual Studio 2015 SDK'sı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK, Visual Studio 2015, Visual Studio 2015 güncelleştirme ve Visual Studio 2017 için aşağıdaki yeni ve güncelleştirilmiş özelliklere sahiptir.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Visual Studio 2017'den itibaren özel Proje ve öğe şablonları için tarama artık gerçekleştirilir. Bunun yerine, uzantı yükleme konumu olarak bu şablonları tanımlamak, şablon bildirim dosyalarını sağlamanız gerekir. VSIX uzantılarınızı güncelleştirmek için Visual Studio 2017'yi kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız, şablon bildirim dosyalarını el ile oluşturmanız gerekir. Daha fazla bilgi için [özel Proje ve öğe şablonlarını yükseltme Visual Studio 2017 için](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Şablon bildirim şeması belgelenen [Visual Studio şablon bildirim şeması başvurusu](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK'sı güncelleştirme 1
 Güncelleştirme 1 iyi renk temaları ve Visual Studio Görüntü hizmeti çalışma uzantınız yardımcı olacak araçlar içerir.

 Bu konu başlıkları altında olan [VSSDK yardımcı programları](../extensibility/internals/vssdk-utilities.md) bölümü:

-   [Renk teması oluşturma araçları](../extensibility/internals/color-theming-tools.md) oluşturun ve Visual Studio için özel renkler Düzenle yardımcı.

-   [Görüntü Hizmeti Araçları](../extensibility/internals/image-service-tools.md) Visual Studio görüntü bildirim dosyaları ile çalışma sağlar.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Visual Studio için Visual Studio SDK eklemek için yeni yol
 Visual Studio 2015'ten başlayarak, Visual Studio SDK'yı ayrı olarak karşıdan yüklemek gerekmez. Bunun yerine, normal yükleme işleminin bir parçası yükleyin ya da daha sonra yüklemek seçebilirsiniz. Bir VSIX çözümüne oluşturun veya açın, Visual Studio, Visual Studio genişletilebilirlik araçları yüklemek için sorar. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Uzantıları oluşturmanın yeni yolu
 Visual Studio 2015 SDK başlayarak, hangi programlama diline bağlı olarak, kullandığınız uzantıları oluşturmak için farklı seçenekler vardır.

### <a name="visual-c-and-visual-basic"></a>Visual C# ve Visual Basic
 C# ve Visual Basic için tam kapsamlı bir VSPackage, menü komutları, araç pencerelerini, düzenleyici sınıflandırıcılar, düzenleyici Kenarlıklar ve düzenleyici kenar boşluğu uzantıları oluşturmanıza imkan tanır ve proje öğesi şablonları yoktur. Tüm standart VSIX projesine ekleyebilirsiniz. Daha fazla bilgi için bkz.:

-   [Bir Menü Komutuyla Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

-   [Araç Penceresi İçeren Bir Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)

-   [Düzenleyici Öğesi Şablonuyla Uzantı Oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)

-   [VSPackage İçeren Bir Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md)

     VSPackage Sihirbazı, uzantıları artık C# veya Visual Basic'te oluşturur.

### <a name="c"></a>C++
 C++ için VSPackage Sihirbazı'nı menü komutları, araç pencereleri ve özel düzenleyicileri destekler. İçinde arayın **yeni proje** iletişim kutusunda **Visual C++ / genişletilebilirlik**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>VS SDK başvurusu Derlemeleri'nin NuGet aracılığıyla
 Taşınabilirliği artırmak ve genişletilebilirlik projeleri paylaşımı için VS SDK başvurusu derlemeleri'nin NuGet sürümlerini kullanabilirsiniz.  Bunlar üzerinde kullanılabilir [nuget.org](http://www.nuget.org) tarafından yayımlanan [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) ve proje veya çözümü Visual Studio ile kolayca eklenebilir **başvuran / yönetme NuGet Paketleri** iletişim. Tek tek özgü genişletilebilirlik derlemelere başvurular ekleyin veya tüm VS SDK'yi başvuran tek seferde VS SDK'sını kullanarak derlemeleri eklemek [Meta paket](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). NuGet hakkında daha fazla bilgi için bkz: [NuGet genel bakış](http://docs.nuget.org/) ve [yönetme NuGet paketlerini kullanarak iletişim](http://docs.nuget.org/Consume/Package-Manager-Dialog).

 VS SDK başvurusu derlemeleri'nin NuGet sürümlerini kullandığınızda, başka bir kullanıcı açın ve derleme için VS SDK'sını yükleme gerekmez.  VS SDK derleme araçları ve NuGet başvuru bütünleştirilmiş kodları bilgisayarlarında bu proje için otomatik olarak yüklenir.

 VS SDK'sı öğe şablonları NuGet başvurularını için kullanın ve varsayılan olarak NuGet avantajlarını elde derleme araçları.

> [!NOTE]
>  Projelerinizi VS SDK'sı başvuru derlemelerini kullanmaya devam edebilirsiniz (altında bulunan \<Visual Studio yükleme konumu > \ VSSDK\VisualStudioIntegration\Common\Assemblies) ve mevcut genişletilebilirlik projeleri olması gerekmez NuGet paketlerini kullanacak şekilde yükseltildi.  Proje **başvuran / başvuru ekleme** VS SDK'sı başvuru bütünleştirilmiş kodlarını kullanan iletişim devam etmektedir.
>
>  Mevcut projelerinizi NuGet kullanmak üzere değiştirmek istiyorsanız, [nasıl yapılır: Visual Studio 2015 Vspackages'a geçirme](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) genişletilebilirlik projeleri için NuGet paketlerini güncelleştirme bir bölümü vardır.

## <a name="light-bulbs"></a>Ampuller
 Uzantı kod yazmayı en heyecan verici yeni yollardan biriyle Roslyn proje tarafından sağlanır. Daha fazla bilgi için [Roslyn](https://github.com/dotnet/Roslyn).

 Ampuller VSSDK ile birlikte gelen yeni bir özelliktir. Visual Studio Düzenleyicisi'nde kullanılan simgeler, kod yeniden düzenleme işlemleri veya yerleşik kod çözümleyicileri tarafından tanımlanan sorunlar için düzeltmeler gösterecek şekilde genişletmek değildirler. Daha fazla bilgi için [izlenecek yol: ampul önerilerini görüntüleme](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Güncelleştirilmiş kullanıcı deneyimi yönergeleri
 Visual Studio için yeni uzantıları veya özellikler tasarlama? Güncelleştirilmiş genişletilmiş kullanıma alıp [Visual Studio kullanıcı deneyimi yönergeleri](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Bölümünde bulabilirsiniz [renk belirteçleri](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [yazı tipi boyutlarını](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [iletişim düzeni belirtimleri](../extensibility/ux-guidelines/layout-for-visual-studio.md)ve yeni kullanıcı Arabirimi Visual Studio ile sorunsuz bir şekilde tümleştirmek için ihtiyacınız olan diğer Kılavuzlar.
