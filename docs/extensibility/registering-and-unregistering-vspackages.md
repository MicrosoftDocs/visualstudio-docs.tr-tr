---
title: Kaydetme ve kaydını VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2075bec37e29359fb9c403f9cb149b70c01845b6
ms.sourcegitcommit: 9571742f4a808c75b1034aa72fc24b54bc50692e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410994"
---
# <a name="register-and-unregister-vspackages"></a>Kaydolun ve VSPackage kaydı
Öznitelik bir VSPackage'ı kaydetmek için kullandığınız ancak  
  
## <a name="register-a-vspackage"></a>VSPackage kaydetme  
 Yönetilen VSPackages kaydını denetlemek için öznitelikleri kullanabilirsiniz. Tüm kayıt bilgileri içerdiği bir *.pkgdef* dosya. Dosya tabanlı kayıt hakkında daha fazla bilgi için bkz. [CreatePkgDef yardımcı programı](../extensibility/internals/createpkgdef-utility.md).  
  
 Aşağıdaki kod, VSPackage'ı kaydetmek için standart kayıt öznitelikleri kullanmayı gösterir.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{
    // ...
}  
```  
  
## <a name="unregister-an-extension"></a>Bir uzantı kaydı  
 Çok sayıda farklı VSPackage'ları ile denemeler ve bunları deneysel örneği kaldırmak istiyorsanız, yalnızca çalıştırabilirsiniz **sıfırlama** komutu. Aranacak **Visual Studio Deneysel örneğini sıfırlama** başlangıç sayfasında, bilgisayarın veya komut satırından şu komutu çalıştırın:  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Git, Visual Studio geliştirme örneğinde yüklü olduğu bir uzantıyı kaldırmak istiyorsanız, **Araçları** > **Uzantılar ve güncelleştirmeler**, uzantı bulabilir ve tıklayın **Kaldırma**.  
  
 Bazı nedenlerden dolayı bu yöntemlerin hiçbiri uzantısını kaldırmayı en başarılı olursa komut satırından VSPackage derleme gibi kaydını kaldırabilirsiniz:  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Bir uzantıyı kaydetmek için bir özel kayıt özniteliği kullanın  
  
Bazı durumlarda Uzantınız için yeni bir kayıt öznitelik oluşturmanız gerekebilir. Yeni kayıt defteri anahtarlarını ekleyin veya yeni değerleri mevcut anahtarlar eklemek için kaydı öznitelikleri kullanabilirsiniz. Yeni öznitelik öğesinden türetilmelidir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, ve onu geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> ve <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> yöntemleri.  
  
### <a name="create-a-custom-attribute"></a>Özel bir öznitelik oluşturma  
  
Aşağıdaki kod, yeni bir kayıt öznitelik oluşturma işlemini gösterir.  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
public class CustomRegistrationAttribute : RegistrationAttribute  
{  
}  
```  
  
 <xref:System.AttributeUsageAttribute> Öznitelik sınıflarında program öğesi (sınıf, yöntem vb.), öznitelik ilgilidir, onu birden çok kez kullanılıp kullanılamayacağı ve devralınabilir olup olmadığını belirtmek için kullanılır.  
  
### <a name="create-a-registry-key"></a>Bir kayıt defteri anahtarı oluşturma  
  
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
  
### <a name="create-a-new-value-under-an-existing-registry-key"></a>Mevcut bir kayıt defteri anahtarı altında yeni bir değer oluşturma  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPackage’lar](../extensibility/internals/vspackages.md)
