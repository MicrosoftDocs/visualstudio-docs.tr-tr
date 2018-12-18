---
title: Bir uzantıyı kaydetmek için bir özel kayıt özniteliğini kullanarak | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: douge
ms.openlocfilehash: 251c31efcbb8a72efac51f246e644a30a79ed999
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279844"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Bir uzantıyı kaydetmek için bir özel kayıt özniteliğini kullanarak
Bazı durumlarda Uzantınız için yeni bir kayıt öznitelik oluşturmanız gerekebilir. Yeni kayıt defteri anahtarlarını ekleyin veya yeni değerleri mevcut anahtarlar eklemek için kaydı öznitelikleri kullanabilirsiniz. Yeni öznitelik öğesinden türetilmelidir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, ve onu geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> ve <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> yöntemleri.  
  
## <a name="creating-a-custom-attribute"></a>Özel bir öznitelik oluşturma  
 Aşağıdaki kod, yeni bir kayıt öznitelik oluşturma işlemini gösterir.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute> Öznitelik sınıflarında program öğesi (sınıf, yöntem vb.), öznitelik ilgilidir, onu birden çok kez kullanılıp kullanılamayacağı ve devralınabilir olup olmadığını belirtmek için kullanılır.  
  
### <a name="creating-a-registry-key"></a>Bir kayıt defteri anahtarı oluşturma  
 Aşağıdaki kodda, özel öznitelik oluşturur bir **özel** Kaydedilmekte VSPackage'ı için anahtarı altındaki alt anahtar.  
  
```  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Mevcut bir kayıt defteri anahtarı altında yeni bir değer oluşturma  
 Var olan bir anahtar için özel değerler ekleyebilirsiniz. Aşağıdaki kod, bir VSPackage kayıt anahtarı için yeni değer eklemek gösterilmektedir.  
  
```  
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