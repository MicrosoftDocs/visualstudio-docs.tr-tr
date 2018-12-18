---
title: Hata ayıklama altyapısı uygulama stratejisi seçme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 058e3d3087a46de4bb3c5d9b721d3c9111b77526
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203718"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Hata ayıklama altyapısı uygulama stratejisi seçme
Hata ayıklama altyapısı (DE) uygulaması stratejinizi belirleme için çalışma zamanı mimarisi kullanın. Hata ayıklama altyapısı işlem içi hata ayıklama programına oluşturabilirsiniz. Hata ayıklama altyapısı işlem içinde Visual Studio oturumu hata ayıklama Yöneticisi (SDM) oluşturun. Veya hata ayıklama altyapısı giden işlem her ikisine de oluşturabilirsiniz. Aşağıdaki yönergeler bu üç stratejiler arasında seçmenize yardımcı olmalıdır.  
  
## <a name="guidelines"></a>Kuralları  
 İşlem dışı olması için DE mümkün olmakla birlikte SDM ve hata ayıklaması program için genellikle Bunu yapmak için bir neden yoktur. Çağrıları işlem sınırları boyunca görece yavaş yükleniyor.  
  
 Hata ayıklama altyapıları ve ortak dil çalışma zamanı ortamı Win32 yerel çalışma zamanı ortamı için zaten sağlanır. Her iki ortam için DE değiştirmek varsa, işlemdeki DE SDM ile oluşturmanız gerekir.  
  
 Aksi takdirde DE işlem içinde SDM oluşturun veya ayıkladığınız işlemde program. İfade değerlendirici DE, sık kullanılan program simge deposuna erişimi gerektirip gerektirmediğini göz önünde bulundurmanız gerekir. Veya, hızlı erişim için belleğe simge deposundaki yüklü. Ayrıca, aşağıdaki yaklaşımlardan göz önünde bulundurun:  
  
-   İfade değerlendirici ve sembol deposundaki arasında birçok çağrı varsa veya sembol deposu SDM bellek alanı okunabiliyorsa DE işlem içinde SDM oluşturun. Programınızı ekler, SDM için hata ayıklama altyapısı CLSID değeri döndürmesi gerekir. SDM bu CLSID DE bir işlem örneğini oluşturmak için kullanır.  
  
-   Sembol deposuna erişmek için program DE çağırmanız gerekir, işlemdeki DE programla oluşturun. Bu durumda, program DE örneğini oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio hata ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)