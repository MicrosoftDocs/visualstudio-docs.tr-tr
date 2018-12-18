---
title: Dinamik araç penceresini açma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d37a72629dfb7c10eeb51bcd2317151447e9edd
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636652"
---
# <a name="open-a-dynamic-tool-window"></a>Dinamik araç penceresini açın
Araç pencereleri genellikle bir menü veya eşdeğer bir kısayol komutundan açılır. Bazen, ancak belirli bir UI bağlamı uygular ve UI bağlamı Artık uygulanmadığında kapatır ne zaman açıldığını araç penceresi ihtiyacınız. Bu tür bir araç pencereleri adlı *dinamik* veya *otomatik görünür*.  
  
> [!NOTE]
>  Önceden tanımlanmış kullanıcı Arabirimi bağlamları listesi için bkz. <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>.  
  
 Başlangıçta dinamik araç penceresini açmak istiyor ve oluşturmanın başarısız olmasına mümkündür, uygulamanız gereken <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> arabirim ve hata koşulları test <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> yöntemi. Başlangıçta açılan dinamik araç penceresini üstlendiğini bilmek Kabuğu sırayla eklemeniz gerekir `SupportsDynamicToolOwner` paket kaydınızı değerine (1 olarak ayarlayın). Bu değer, standart bir parçası değil <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, özel bir öznitelik eklemek için oluşturmanız gerekir. Özel öznitelikler hakkında daha fazla bilgi için bkz. [bir uzantıyı kaydetmek için bir özel kayıt özniteliğini kullanın](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Kullanım <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> araç penceresi açın. Araç penceresi, gerektiğinde oluşturulur.  
  
> [!NOTE]
>  Dinamik araç penceresini, kullanıcı tarafından kapatılabilir. Kullanıcı araç penceresi açabilirsiniz. Bu nedenle, bir menü komutu oluşturmak istiyorsanız, araç penceresi ve aksi durumda devre dışı açılır UI bağlamda menü komutunu yeniden etkinleştirilmesi gerekir.  
  
## <a name="to-open-a-dynamic-tool-window"></a>Dinamik araç penceresini açmak için  
  
1.  Adlı bir VSIX projesi oluşturun **DynamicToolWindow** ve adlı bir araç penceresi öğesi şablonu ekleme *DynamicWindowPane.cs*. Daha fazla bilgi için [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  İçinde *DynamicWindowPanePackage.cs* dosya, DynamicWindowPanePackage bildirimi bulun. Ekleme <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> ve <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> araç penceresi kaydetmek için öznitelikler.  
  
    ```vb  
    [ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackage.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Yukarıdaki öznitelikleri Visual Studio kapatılıp yeniden yükleyen kalıcı bir geçici pencere olarak DynamicWindowPane adlı araç penceresi kaydedin. DynamicWindowPane açıldığı zaman <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> uygular ve aksi takdirde kapatıldı.  
  
3.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği görüntülenmesi gerekir. Araç penceresi görmemeniz gerekir.  
  
4.  Bir proje deneysel örneğinde açın. Araç penceresi görüntülenmelidir.