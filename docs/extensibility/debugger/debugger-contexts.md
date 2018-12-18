---
title: Hata ayıklayıcı bağlamları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 49af504b27afc6171a914d9559a5ff83f3d595eb
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204108"
---
# <a name="debugger-contexts"></a>Hata ayıklayıcı bağlamları
İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama, hata ayıklama altyapısı (DE) aynı anda birçok farklı bağlamları içinde şu şekilde çalışır:  
  
-   Kod bağlamı bir programın yürütülmesine stream'de geçerli konumu açıklar.  
  
-   Belge bağlamı veya konum, kaynak belge içindeki geçerli konumu açıklar.  
  
-   Hangi ifadesinde değerlendirmesi yer alacak bağlam tanımlayan ifade değerlendirme bağlamı.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Kod bağlamı](../../extensibility/debugger/code-context.md)  
 Bugünün çalışma zamanı mimarileri nontraditional diller ve burada kod yönergeleri, ancak başka bir yolla tarafından temsil edilebilir değil, bir programın yönerge stream'de adresi olarak kod bağlamı anlatır.  
  
 [Belge konumu](../../extensibility/debugger/document-position.md)  
 Visual Studio IDE'ye bilinen kaynak dosyada bir konumdaki bir soyutlama yoluyla hata ayıklama belge konumunu tanımlar.  
  
 [Belge bağlamı](../../extensibility/debugger/document-context.md)  
 Açıklar bir kaynak dosya ile ilgili olarak Visual Studio hata ayıklama hangi belge bağlamı temsil eder. Ayrıca, sembol işleyici kod bağlamı belge bağlamına nasıl eşlendiğini anlatılmaktadır.  
  
 [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md)  
 Visual Studio'da bir ifade değerlendirme bağlamı hakkında bilgi sağlar. Örneğin, bir yığın çerçevesiyle ilgili bir ifade değerlendirme bağlamı, yerel değişkenler, yöntem parametreleri ve sınıf üyeleri değerlendirmesi için bağlamı sağlar.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md)  
 Hata ayıklama ana mimari kavramlarını açıklar.  
  
 [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md)  
 Hata ayıklama altyapısı (DE) ifade değerlendiricisi (EE) ve sembol işleyici (SH) Visual Studio hata ayıklama Bileşenleri'ne genel bakış sağlar.  
  
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)  
 Program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerini bağlantılar içerir.