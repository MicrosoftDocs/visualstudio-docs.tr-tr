---
title: Seçenekler sayfaları için Otomasyon desteği | Microsoft Docs
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
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6205d01547f7243234facfb43db80303c9b71c51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720260"
---
# <a name="automation-support-for-options-pages"></a>Seçenekler Sayfaları için Otomasyon Desteği
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage özel sağlayabilir **seçenekleri** iletişim kutuları için **Araçları** (Araçlar Seçenekler sayfaları) menüde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve bunları otomasyon modeli için kullanılabilir hale getirebilirsiniz.  
  
## <a name="tools-options-pages"></a>Araçlar Seçenekler sayfaları  
 Oluşturmak için bir **Araçlar Seçenekler** sayfasında VSPackage VSPackage'nın uygulaması aracılığıyla ortamına döndürülen bir kullanıcı denetimi uygulama sağlamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> yöntemi (veya yönetilen kod için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> yöntemi).  
  
 Bu isteğe bağlıdır, ancak bu yeni sayfa otomasyon modeli aracılığıyla erişmesine izin vermek için önemle önerilir. Bunu aşağıdaki adımları izleyerek yapabilirsiniz:  
  
1. Genişletme <xref:EnvDTE._DTE.Properties%2A> IDispatch türetilmiş bir nesnenin uygulanmasına aracılığıyla nesne.  
  
2. Uygulanışı dönüş <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> yöntemi (veya yönetilen kod için <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> yöntemi) IDispatch türetilmiş nesne.  
  
3. Bir Otomasyon tüketici çağırdığında <xref:EnvDTE._DTE.Properties%2A> özel metodunda **seçeneği** özellik sayfası, ortam kullanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> özel elde etmek için yöntemi **Araçlar Seçenekler** sayfanın Otomasyon uygulama.  
  
4. Otomasyon nesne VSPackage'ı, ardından her sağlamak için kullanılan <xref:EnvDTE.Property> tarafından döndürülen <xref:EnvDTE._DTE.Properties%2A>.  
  
   Özel Araçlar Seçenekler sayfası uygulayan bir örnek için bkz. [VSSDK örnekleri](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje Nesnelerini Kullanıma Sunma](../../extensibility/internals/exposing-project-objects.md)

