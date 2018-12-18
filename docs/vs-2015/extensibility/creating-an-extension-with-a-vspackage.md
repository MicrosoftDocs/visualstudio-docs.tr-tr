---
title: VSPackage içeren bir uzantı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 945ae5b3cf6cd8769795c31a10a4f51e1f7eccb6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773307"
---
# <a name="creating-an-extension-with-a-vspackage"></a>VSPackage İçeren Bir Uzantı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bir VSIX projesi oluşturun ve bir VSPackage proje öğesi ekleyin işlemini göstermektedir. Bir ileti kutusu görüntüleme için kullanıcı Arabirimi Shell hizmetinin almak için VSPackage'ı kullanacağız.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>VSPackage'ı oluşturma  
  
1.  Adlı bir VSIX projesi oluşturun **FirstPackage**. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C# / genişletilebilirlik**.  
  
2.  Projeyi açtığında, adlı bir Visual Studio Paket öğesi şablonu ekleme **FirstPackage**. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. İçinde **Yeni Öğe Ekle** iletişim kutusunda, Git **Visual C# / genişletilebilirlik** seçip **Visual Studio paket**. İçinde **adı** alan penceresinin en altında komut dosyası adı için değiştirme **FirstPackage.cs**.  
  
3.  Projeyi oluşturmak ve hata ayıklamaya başlayın.  
  
     Visual Studio'nun deneysel örneğinde görünür. Deneysel örnek hakkında daha fazla bilgi için bkz. [deneysel örneğinde](../extensibility/the-experimental-instance.md).  
  
4.  Deneysel örneğinde açın **araçları / Uzantılar ve güncelleştirmeler** penceresi. Görmelisiniz **FirstPackage** uzantıyı şurada. (Açarsanız **Uzantılar ve güncelleştirmeler** Visual Studio, çalışma örneğinde göremezsiniz **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>VSPackage yükleme  
 Olmadığı için yüklemek neden bir şey bu noktada uzantısı, yüklemez. (Bir araç penceresi açıp bir menü komutu tıklandığında) kullanıcı arabirimini veya VSPackage'ı belirli bir kullanıcı Arabirimi bağlamda yükleyeceğini belirterek etkileşim kurduğunuzda, genellikle uzantı yükleyebilirsiniz. VSPackages ve UI bağlamı yükleme hakkında daha fazla bilgi için bkz. [VSPackage yükleme](../extensibility/loading-vspackages.md). Bu yordam için nasıl bir çözümü açtığınızda VSPackage yükleme göstereceğiz.  
  
1.  FirstPackage.cs dosyasını açın. FirstPackage sınıfının bildirimi arayın. Mevcut öznitelikleri içerikleri şu kodla değiştirin:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  VSPackage'ı yükledi bize sağlayan bir ileti ekleyelim. VSPackage'ı bir yalnızca tarihli sonra Visual Studio Hizmetleri elde edebilirsiniz çünkü VSPackage'nın önce Initialize() yöntemini Bunu yapmak için kullanırız. (Hizmetler alma hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md).) FirstPackage önce Initialize() yöntemini alır koduyla değiştirin <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> hizmetini alır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimi ve çağrılarını kendi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> yöntemi.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
4.  Bir çözüm deneysel örneğinde açın. Bildiren bir ileti kutusu görmeniz gerekir **içinde ilk paketi Initialize()**.

