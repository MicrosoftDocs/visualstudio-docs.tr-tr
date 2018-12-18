---
title: VSPackage yükleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e351f49ea3e9579202e21868361e5d6f3d53b8fd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753875"
---
# <a name="loading-vspackages"></a>VSPackage Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İşlevleri gerekli olduğunda VSPackages Visual Studio'ya yüklenir. Örneğin, Visual Studio bir proje fabrikası ya da VSPackage'ı uygulayan bir hizmet kullanırken bir VSPackage yüklenir. Bu özellik, mümkün olduğunda performansını artırmak kullanılan Gecikmeli yüklemeyi çağrılır.  
  
> [!NOTE]
>  Visual Studio VSPackage'ı yüklemeden VSPackage sunan komutlar gibi belirli bir VSPackage bilgileri belirleyebilirsiniz.  
  
 Bir çözümü açtığınızda VSPackages sorsorgu belirli kullanıcı arabirimi (UI) bağlamında gibi olarak ayarlanabilir. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Özniteliği bu bağlamda ayarlar.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>VSPackage'ı belirli bir bağlamda Autoloading  
  
-   Ekleme `ProvideAutoLoad` özniteliği VSPackage öznitelikleri:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Numaralandırılmış alanlarını bkz <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> UI bağlamı ve GUID değerlerinin listesi.  
  
-   Bir kesim noktası <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi.  
  
-   VSPackage'ı oluşturun ve hata ayıklamaya başlayın.  
  
-   Bir çözümü yüklemek veya bir tane oluşturabilirsiniz.  
  
     VSPackage'ı yükler ve kesme noktasında durur.  
  
## <a name="forcing-a-vspackage-to-load"></a>VSPackage'ı yüklemek için zorlama  
 Bazı koşullar altında bir VSPackage yüklenecek başka bir VSPackage zorlamanız gerekebilir. Örneğin, basit bir VSPackage'ı bir CMDUIContext kullanılamayan bir bağlamda daha büyük bir VSPackage yükleyebilir.  
  
 Kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> VSPackage'ı yüklemeye zorlamak için yöntemi.  
  
-   Bu koda Ekle <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yüklemek için başka bir VSPackage zorlar VSPackage'ı yöntemi:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     VSPackage'ı başlatıldığında zorlayacak `PackageToBeLoaded` yüklenemedi.  
  
     Zorla yüklenmesini VSPackage iletişimi için kullanılmaması gerekir. Kullanım [kullanma ve sağlama Hizmetleri](../extensibility/using-and-providing-services.md) yerine.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>VSPackage kaydetme için özel bir öznitelik kullanma  
 Bazı durumlarda Uzantınız için yeni bir kayıt öznitelik oluşturmanız gerekebilir. Yeni kayıt defteri anahtarlarını ekleyin veya yeni değerleri mevcut anahtarlar eklemek için kaydı öznitelikleri kullanabilirsiniz. Yeni öznitelik öğesinden türetilmelidir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, ve onu geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> ve <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> yöntemleri.  
  
## <a name="creating-a-registry-key"></a>Bir kayıt defteri anahtarı oluşturma  
 Aşağıdaki kodda, özel öznitelik oluşturur bir **özel** Kaydedilmekte VSPackage'ı için anahtarı altındaki alt anahtar.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Mevcut bir kayıt defteri anahtarı altında yeni bir değer oluşturma  
 Var olan bir anahtar için özel değerler ekleyebilirsiniz. Aşağıdaki kod, bir VSPackage kayıt anahtarı için yeni değer eklemek gösterilmektedir.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage’lar](../extensibility/internals/vspackages.md)

