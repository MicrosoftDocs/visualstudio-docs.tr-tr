---
title: Kod için Otomasyon sağlama | Microsoft Docs
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
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 399900bce10edbd6fec549fc3a52ca3dbeefdabc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761560"
---
# <a name="providing-automation-for-code"></a>Kod için Otomasyon Sağlama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kodunuz için bir otomasyon modeli oluşturulması gerekli değildir. Ortamı SDK'sı, bunu yapmak için bir örnek sağlamaz. Kod modelleri hakkında bilgi için bkz: <xref:EnvDTE.CodeModel> nesne.  
  
 Kod modeli uygulamak için iç veri yapısı tarafından belirlenen hiçbir arabirimi uygulamalıdır. Nesneleri nesnesinden türetilmesi `IDispatch` sınıfı.  
  
 Genişlettiğinizde, nesneleri <xref:EnvDTE.CodeModel> ve <xref:EnvDTE.FileCodeModel>, kullanılabilir <xref:EnvDTE.Project> nesne ve aşağıdakine benzer:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Uygulamak seçebilirsiniz yalnızca `CodeModel` veya `FileCodeModel` arabirimi, iade nesnesinde, `Project` ve <xref:EnvDTE.ProjectItem> nesneleri. Bu arabirimden, proje sistemi için uygun olan herhangi bir işlevsellik sağlar.  
  
 Yöntemleri veya özellikleri gibi özellikler eklemek istiyorsanız, kullanılabilir değil standart `CodeModel` ve `FileCodeModel` arabirimleri, standart devralan kendi arabirimi oluşturun. Son kullanıcılar için aranacak bilmesi, proje sisteminizi belgelediğinizden emin olun. Standart arabirimi döndürür, ancak kullanıcı çağırabilirsiniz `QueryInterface` yöntemi veya mevcut biliniyorsa, arabirime cast.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Otomasyon Modeline Genel Bakış](../../extensibility/internals/automation-model-overview.md)

