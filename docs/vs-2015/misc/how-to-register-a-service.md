---
title: 'Nasıl yapılır: bir hizmet kaydı | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: a1f8026a648b2a0809af17664d4399f815c329be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206264"
---
# <a name="how-to-register-a-service"></a>Nasıl yapılır: bir hizmeti kaydedin
Yönetilen paket çerçevesini (MPF), yönetilen hizmetler kaydını denetlemek için öznitelikleri sağlar. RegPkg yardımcı programı bir hizmetiyle kaydetmek için bu öznitelikler kullanan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod dandır [VSSDK örnekleri](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> SMyGlobalService hizmetine kaydeder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Hakkında daha fazla bilgi için <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> ve <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, bkz: [kaydetme ve kaydını kaldırma VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Aynı ada sahip başka bir hizmete yerini alan bir hizmeti kaydetmek için kullanın <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> yerine <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bir hizmet sağlayıcısı hizmeti istemcisi değiştirmeden yeniden derleyin daha kolay hale getirmek için veya tam tersi hizmet ve arabirimlerini ayrı derleme modülünde tanımlayabilirsiniz. Aşağıdaki kod Reference.Services (C#) örnek IMyGlobalService.cs dosyasında arasındadır.  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Arabirimi, yönetilmeyen koddan elde etmek için gereklidir.  
  
> [!NOTE]
>  Hizmet ve arabirimi için aynı türe veya GUID kullanabilirsiniz, ancak bir hizmet farklı arabirimleri kullanıma sunabileceğinden iki ayrı öneririz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage'ları kaydetme](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Hizmet Temel Bileşenleri](../extensibility/internals/service-essentials.md)