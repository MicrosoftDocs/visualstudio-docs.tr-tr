---
title: Tek dosya oluşturucuları kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a2e65a1ef3db913223d9248797d1cf4bd9c9ded6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876004"
---
# <a name="registering-single-file-generators"></a>Tek Dosya Oluşturucuları Kaydetme
Özel bir araç olarak kullanılabilir hale getirmek için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], bu nedenle kaydetmelisiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] örneği oluşturabilir ve belirli proje türüyle ilişkilendirir.  
  
### <a name="to-register-a-custom-tool"></a>Özel bir aracı kaydetmek için  
  
1. Özel araç DLL ya da kayıt içinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yerel kayıt defteri veya sistem kayıt defterinde HKEY_CLASSES_ROOT altında.  
  
    Örneğin, ile sunulan yönetilen MSDataSetGenerator özel aracı için kayıt bilgileri işte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
   ```  
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
   "ThreadingModel"="Both"  
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
   ```  
  
2. İstenen bir kayıt defteri anahtarı oluşturma [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluşturucuları altında hive\\*GUID* burada *GUID* GUID belirli dil proje sistemi veya hizmet tarafından tanımlanır. Anahtar adı özel aracınızı programlı adı haline gelir. Özel araç anahtar aşağıdaki değerlere sahip:  
  
   -   (Varsayılan)  
  
        İsteğe bağlı. Özel aracın kullanıcı dostu bir açıklama sağlar. Bu parametre isteğe bağlıdır ancak önerilir.  
  
   -   CLSID  
  
        Gerekli. Sınıf kitaplığı uygulayan COM bileşeninin tanımlayıcısını belirtir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
   -   GeneratesDesignTimeSource  
  
        Gerekli. Bu özel araç tarafından üretilen dosyaları türlerinden görsel tasarımcılar için kullanılabilir olup olmadığını gösterir. Bu parametrenin değeri türleri görsel tasarımcılar için kullanılabilir değil (sıfır) 0 veya (bir adet) 1 türleri için görsel tasarımcılar kullanılabilir olması gerekir.  
  
   > [!NOTE]
   >  Ayrı ayrı, özel aracın kullanılabilir olmasını istediğiniz her dil için özel aracı kaydetmeniz gerekir.  
  
    Örneğin, MSDataSetGenerator kendini kez her dil için kaydeder:  
  
   ```  
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
   @="Microsoft VB Code Generator for XSD"  
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
   "GeneratesDesignTimeSource"=dword:00000001  
  
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
   @="Microsoft C# Code Generator for XSD"  
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
   "GeneratesDesignTimeSource"=dword:00000001  
   ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Tek dosya oluşturucular ekleme](../../extensibility/internals/implementing-single-file-generators.md)   
 [Türleri görsel tasarımcıların gösterme](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [BuildManager nesnesine giriş](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)