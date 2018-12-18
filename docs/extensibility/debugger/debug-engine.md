---
title: Hata ayıklama altyapısı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 78bd5b732d7ea1714bb1c5627b570976e33a82c4
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203894"
---
# <a name="debug-engine"></a>Hata ayıklama altyapısı
Hata ayıklama altyapısı (DE), işletim sistemi ve yorumlayıcı yürütme denetimi, kesme noktaları ve ifade değerlendirme gibi hata ayıklama hizmetleri sağlamak için birlikte çalışır. Hata ayıklanan programa durumunu izlemek için DE sorumludur. Bunu yapmak için hangi yöntemler CPU veya API'leri çalışma zamanı tarafından sağlanan olmadığını desteklenen çalışma zamanı için kullanılabilir DE kullanır.  
  
 Örneğin, ortak dil çalışma zamanı (CLR) çalışan bir program ICorDebugXXX arabirimleri aracılığıyla izlemek için bir mekanizma sağlar. Destekleyen CLR DE uygun ICorDebugXXX arabirimleri hataları ayıklanmakta olan bir yönetilen kod program izlemek için kullanır. Bu bilgileri ileten oturum hata ayıklama Yöneticisi (SDM), ardından aktarır durumu değişiklikleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
> [!NOTE]
>  Hata ayıklama altyapısı belirli bir çalışma, diğer bir deyişle, programı olan çalıştırmaları hata ayıklaması sistem hedefler. CLR çalışma zamanı yönetilen kod için ve Win32 çalışma zamanını yerel Windows uygulamaları için. Oluşturduğunuz dil'ın bu iki çalışma zamanları birini hedeflediğinizde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zaten gerekli hata ayıklama altyapısı sağlar. Uygulamak için sahip olduğunuz şey bir ifade değerlendiricisi.  
  
## <a name="debug-engine-operation"></a>Hata ayıklama altyapısı işlemi  
 İzleme hizmetleri DE arabirimleri aracılığıyla uygulanır ve farklı çalışma modları arasında geçiş hata ayıklama paketi neden olabilir. Daha fazla bilgi için [çalışma modları](../../extensibility/debugger/operational-modes.md). Genellikle çalışma zamanı ortam başına yalnızca bir DE uygulama yok.  
  
> [!NOTE]
>  Transact-SQL için ayrı DE uygulamaları varken ve [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript ve [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] tek DE paylaşın.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama altyapıları iki yoldan biriyle çalıştırılacak hata ayıklama etkinleştirir: ya da aynı süreci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kabuk veya hedef programın aynı işlemde ayıklanan. İkinci form, genellikle ayıklanan işlemin gerçekten yorumlayıcıyı altında çalışan bir betik olduğunda gerçekleşir. Hata ayıklama altyapısı betik izlemek için yorumlayıcısı tutun bilgi olması gerekir. Bu durumda yorumlayıcı aslında bir çalışma zamanı, hata ayıklama altyapıları için belirli çalışma zamanı uygulamalarıdır. Ayrıca, tek bir DE uygulaması (örneğin, uzaktan hata ayıklama) işlem ve makine sınırlarında bölünebilir.  
  
 DE kullanıma sunan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama arabirimleri. COM içinden tüm iletidir DE işlem içi, çıkış işleminin veya başka bir bilgisayarda yüklü olmadığını bileşeni iletişim etkilemez.  
  
 İfadelerin söz dizimini anlamak bu belirli çalışma zamanı için DE etkinleştirmek için ifade değerlendirici bileşeni ile DE çalışır. DE dil derleyici tarafından oluşturulan sembolik hata ayıklama bilgilerine erişmek için bir sembol işleyici bileşeni ile de çalışır. Daha fazla bilgi için [ifade değerlendiricisi](../../extensibility/debugger/expression-evaluator.md) ve [sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)   
 [İfade değerlendirici](../../extensibility/debugger/expression-evaluator.md)   
 [Sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md)