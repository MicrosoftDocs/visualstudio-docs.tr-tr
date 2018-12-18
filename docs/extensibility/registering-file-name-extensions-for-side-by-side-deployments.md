---
title: Yan yana dağıtımlar için dosya adı uzantılarını kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1aa553b5370f637f5a779bbdff432319ce3e0bf4
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638485"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Yan yana dağıtımlar için dosya adı uzantılarını kaydetme
Yan yana bir ortamda dağıtılan Vspackage'lar için dosyaları doğru sürümü ile ilişkilendirilecek dosya adı uzantıları kaydetmelisiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sürüme özgü dosya adı uzantısı kullanmıyorsanız, kayıt, kullanıcıların projenizi açın ve proje öğesi dosyaları uygun sürümünü de olanak tanır. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Dosya adı uzantıları hakkında](../extensibility/about-file-name-extensions.md)  
 Dosya adı uzantıları nasıl kayıtlı açıklanır.  
  
 [Dosya adı uzantıları için dosya işleyicileri belirtme](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Açmak için uygulamalar, düzenleme ve benzeri, belirli bir dosya adı uzantısı kaydetme hakkında bilgi sağlar.  
  
 [Dosya adı uzantıları için fiil kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Fiil kaydetme anlatılmaktadır.  
  
 [Yan yana dosya ilişkilendirmelerini yönetme](../extensibility/managing-side-by-side-file-associations.md)  
 Yan yana yüklemeleri, nasıl ele alınacağını açıklar belirli bir sürümü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir dosyayı açmak için çağrılmalıdır.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Visual Studio'nun birden çok sürümünü destekler](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Birden çok sürümleri için ilgili sorunlar açıklanmaktadır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve geliştirme ve son kullanıcıların dağıtım sırasında VSPackage'ı.