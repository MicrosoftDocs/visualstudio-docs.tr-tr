---
title: İç içe geçme projeleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35d0f4f8906acc08733894d1c24b6d8c2199e1f7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131166"
---
# <a name="nesting-projects"></a>İç içe geçme projeleri
VS paketinizi kullanan kurumsal uygulama geliştiricileri rahat projeleri bir araya benzer türde grup [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanarak *proje iç içe geçme*. Örneğin, kuruluş şablon proje grubu projeleri iç içe geçmiş projelerine kategoriye kullanır. İş cephesi projeleri, Web kullanıcı arabirimini projeleri ve benzeri bir kategoride birlikte gruplandırılır.  
  
 Bu senaryoda, bir sınır yoktur Geliştirici her ana proje altında geçirebilmenize projeleri sayısına developer program aracılığıyla sınırları sağlayabilirse. Bu tür bir gruplandırma, özyinelemeli; bu durumda alt projesi olarak aynı türde projeleri bir alt proje üst alt bir alt olmasını alt altında içe olamaz de yapılabilir.  
  
 Proje iç içe geçme iç bir parçası değil [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. İç içe geçme etkinleştirmek ve alt projeleri içinde iç içe alt proje için kod yazmanız gerekir. Ana proje bir özel VSPackage veya proje türü oluşturulur ve proje iç içe geçme uygulamak için gereken kod içeren kendi GUID ile kayıtlı değil.  
  
 İç içe geçmiş projeleri örneği C# Example.Nested proje örneğinde bulabilirsiniz.  
  
## <a name="nested-projects-example"></a>İç içe geçmiş projeleri örneği  
 ![İç içe projeler çözümü](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
İç içe geçmiş projeleri örneği  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: iç içe Projeler uygulama](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Yüklemeyi kaldırma ve yeniden iç içe geçmiş projeleri için ilgili önemli noktalar](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [İç içe geçmiş projeleri için sihirbaz desteği](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Proje ve öğe şablonları kaydediliyor](../../extensibility/internals/registering-project-and-item-templates.md)   
 [İç içe geçmiş projeleri için işleme komutu uygulama](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [İç içe geçmiş projeleri için filtreleme addItem iletişim kutusu](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Denetim listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Bağlam parametreleri](../../extensibility/internals/context-parameters.md)   
 [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)