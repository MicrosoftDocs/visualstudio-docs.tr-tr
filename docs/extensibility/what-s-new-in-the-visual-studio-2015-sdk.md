---
title: Hangi&#39;'teki Visual Studio 2015 SDK'sı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4926ed9fafb64664d3ac0426466d90611cae4450
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566699"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Hangi&#39;Visual Studio 2015 SDK yenilikler
Visual Studio SDK, Visual Studio 2015, Visual Studio 2015 güncelleştirme ve Visual Studio 2017 için aşağıdaki yeni ve güncelleştirilmiş özelliklere sahiptir.  
  
## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK'sı güncelleştirme 1  
 Güncelleştirme 1 iyi renk temaları ve Visual Studio Görüntü hizmeti çalışma uzantınız yardımcı olacak araçlar içerir.  
  
 Bu konu başlıkları altında olan [VSSDK yardımcı programları](../extensibility/internals/vssdk-utilities.md) bölümü:  
  
-   [Renk teması oluşturma araçları](../extensibility/internals/color-theming-tools.md) oluşturun ve Visual Studio için özel renkler Düzenle yardımcı.  
  
-   [Görüntü Hizmeti Araçları](../extensibility/internals/image-service-tools.md) Visual Studio görüntü bildirim dosyaları ile çalışma sağlar.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Visual Studio SDK'sı için Visual Studio eklemek için yeni yol  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK'yı ayrı olarak karşıdan yüklemek gerekmez. Bunun yerine, normal yükleme işleminin bir parçası yükleyin ya da daha sonra yüklemek seçebilirsiniz. Bir VSIX çözümüne oluşturun veya açın, Visual Studio, Visual Studio genişletilebilirlik araçları yüklemek için sorar. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Uzantıları oluşturmanın yeni yolu  
 Visual Studio 2015 SDK başlayarak, hangi programlama diline bağlı olarak, kullandığınız uzantıları oluşturmak için farklı seçenekler vardır.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# ve Visual Basic  
 C# ve Visual Basic için tam kapsamlı bir VSPackage, menü komutları, araç pencerelerini, düzenleyici sınıflandırıcılar, düzenleyici Kenarlıklar ve düzenleyici kenar boşluğu uzantıları oluşturmanıza imkan tanır ve proje öğesi şablonları yoktur. Bu şablonlar bir bölümünü veya tamamını standart bir VSIX projesine ekleyebilirsiniz. Daha fazla bilgi için bkz.:  
  
-   [Bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [VSPackage içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     VSPackage Sihirbazı, uzantıları artık C# veya Visual Basic'te oluşturur.  
  
### <a name="c"></a>C++  
 C++ için VSPackage Sihirbazı'nı menü komutları, araç pencereleri ve özel düzenleyicileri destekler. İçinde arayın **yeni proje** iletişim kutusunda **Visual C++ / genişletilebilirlik**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>VS SDK başvurusu derlemeleri'nin NuGet aracılığıyla  
 Taşınabilirliği artırmak ve genişletilebilirlik projeleri paylaşımı için VS SDK başvurusu derlemeleri'nin NuGet sürümlerini kullanabilirsiniz. Bu derlemeler kullanılabilir [nuget.org](http://www.nuget.org) tarafından yayımlanan [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) ve proje veya çözümü Visual Studio ile kolayca eklenebilir **başvuran / yönetme NuGet paketlerini** iletişim. Tek tek özgü genişletilebilirlik derlemelere başvurular ekleyin veya tüm VS SDK'yi başvuran tek seferde VS SDK'sını kullanarak derlemeleri eklemek [Meta paket](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). NuGet hakkında daha fazla bilgi için bkz: [NuGet belgeleri](/NuGet) ve [Paket Yöneticisi UI](/NuGet/Tools/Package-Manager-UI) konuları.  
  
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