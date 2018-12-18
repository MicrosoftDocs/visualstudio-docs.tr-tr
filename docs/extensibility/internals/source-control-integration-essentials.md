---
title: Kaynak denetimini tümleştirme temel bileşenleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4533cac0ba6cbbcf5cf4354afdb29eefc5b2b726
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879174"
---
# <a name="source-control-integration-essentials"></a>Kaynak Denetimini Tümleştirme Temel Bileşenleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kaynak denetimi tümleştirmesi iki türlerini destekler: temel işlevleri sağlayan ve kaynak denetimi eklentisi API (eski adıyla MSSCCI API olarak da bilinir) ve bir VSPackage tabanlı kaynak denetimi tümleştirmesi çözümü kullanılarak oluşturulan bir kaynak denetimi eklentisi, daha sağlam işlevselliği sağlar.  
  
## <a name="source-control-plug-in"></a>Kaynak Denetimi Eklentisi  
 Kaynak Denetimi Eklentisi, kaynak denetimi eklentisi API uygulayan bir DLL yazılır. Kayıt ve kaynak denetimi tümleştirmesi işlevi API aracılığıyla sağlanır. Bu yaklaşım bir kaynak denetimi VSPackage'ı uygulamak daha kolaydır ve kullandığı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çoğu kaynak denetimi işlemleri için kullanıcı arabirimi (UI).  
  
 Kaynak Denetimi Eklentisi Kaynak Denetimi Eklentisi API kullanarak uygulamak için şu adımları izleyin:  
  
1. Belirtilen işlevleri uygulayan bir DLL'yi oluşturmak [kaynak denetimi eklentileri](../../extensibility/source-control-plug-ins.md).  
  
2. DLL'yi uygun kayıt defteri girişlerini yaparak açıklandığı kaydetme [nasıl yapılır: kaynak denetimi eklentisi yükleme](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3. Yardımcı bir kullanıcı Arabirimi oluşturma ve kaynak denetimi bağdaştırıcısı paketi tarafından istendiğinde görüntüleme ( [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetimi eklentileri ile kaynak denetimi işlevlerini işleyen bileşeni).  
  
   Daha fazla bilgi için [kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Kaynak denetimi VSPackage'ı  
 Kaynak denetimi VSPackage'ı uygulama özelleştirilmiş bir ardılı geliştirmenizi sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak UI denetimi. Bu yaklaşım, kaynak denetimi tümleştirmesi üzerinde tam denetim sağlar, ancak kullanıcı Arabirimi öğeleri sağlamak ve eklenti yaklaşım sağlanması kaynak denetimi arabirimlerini gerektirir.  
  
 Kaynak denetimi VSPackage'ı uygulamak için şunları yapmalısınız:  
  
1. Oluşturma ve açıklandığı gibi kendi kaynak denetimi VSPackage'ı, kaydetme [kayıt ve seçim](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2. Varsayılan kaynak denetimi kullanıcı Arabirimi, özel kullanıcı Arabirimi ile değiştirin. Bkz: [özel kullanıcı arabirimi](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3. Kullanılması ve işlemek için karakter belirtin **Çözüm Gezgini** glif olayları. Bkz: [karakter denetimi](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4. Sorgu düzenleme ve sorguyu kaydedin olayları, gösterildiği gibi işlemek [sorgu düzenleme sorgu kaydetme](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
   Daha fazla bilgi için [bir kaynak denetimi VSPackage'ı oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel bakış](../../extensibility/internals/source-control-integration-overview.md)   
 [Kaynak Denetimi Eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)