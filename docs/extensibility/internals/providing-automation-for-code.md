---
title: Otomasyon kodu için sağlama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f9dbb7a8ddad39f01f5b29443168eebe12a2da8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130694"
---
# <a name="providing-automation-for-code"></a>Otomasyon kodu için sağlama
Kodunuz için bir otomasyon modeli oluşturma gerekli değildir. Ortamı SDK'sı, bunu yapmak için bir örnek sağlamaz. Kod modelleri hakkında bilgi için bkz: <xref:EnvDTE.CodeModel> nesne.  
  
 Kod modeli uygulamak için iç veri yapısı tarafından belirlenir hiçbir arabirim uygulamalıdır. Nesneleri öğesinden türetilmelidir `IDispatch` sınıfı.  
  
 Genişlettiğinizde, nesneleri <xref:EnvDTE.CodeModel> ve <xref:EnvDTE.FileCodeModel>, kullanılabilir <xref:EnvDTE.Project> nesne ve şu şekilde görünür:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Uygulanacak seçebilirler yalnızca `CodeModel` veya `FileCodeModel` , dönüş nesnesindeki arabirim, `Project` ve <xref:EnvDTE.ProjectItem> nesneleri. Proje sisteminiz için uygun olan bu arabirimden herhangi bir işlevsellik sağlar.  
  
 Yöntemleri veya özellikleri gibi özellikleri eklemek istiyorsanız, kullanılabilir değil standart `CodeModel` ve `FileCodeModel` arabirimleri, standart devralır kendi arabirimi oluşturun. Son kullanıcılar için aranacak bilmesi proje sisteminizle belgelediğinizden emin olun. Standart arabirimini döndürür, ancak kullanıcı çağırabilirsiniz `QueryInterface` yöntemi veya cast bulunmasını biliniyorsa arabiriminiz için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Otomasyon Modeline Genel Bakış](../../extensibility/internals/automation-model-overview.md)