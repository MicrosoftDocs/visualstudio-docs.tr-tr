---
title: Hata ayıklama görevleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a1d2ae4b05398daa7c42be441cebecb304bf956
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204173"
---
# <a name="debug-tasks"></a>Hata ayıklama görevleri
Bir programda hata ayıklamak için onu başlatan gerekir ve bir hata ayıklama altyapısı (DE) bağlı gerekir, aksi takdirde DE daha önce başlatılan bir program için'e bağlı olması gerekir. Bağlandıktan sonra DE bazı başlangıç olayları oluşturmanız gerekir. Yanıt olarak, hata ayıklama paketi IDE içinde ayarlanan kesme noktaları bağlama dener. Programı ilişkili bir kesme noktasına ulaştığında, durdurur ve kullanıcı girdisini bekler.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Güvenlik sorunları](../../extensibility/debugger/security-issues.md)  
 Bir programda hata ayıklamak için gerekli olan güvenlik adımlar açıklanmaktadır.  
  
 [Bir program Başlat](../../extensibility/debugger/launching-a-program.md)  
 Programı başlatmak için işletim sistemini çağıran bir DE belirleme konusunda adım adım yönergeler sağlar.  
  
 [Doğrudan programa ekleme](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Bir programda zaten çalışan bir işlemde hata ayıklamak için kullanılan işlem açıklanır.  
  
 [Başlatmadan sonra Başlangıç olaylarını gönderme](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Program kendi ana giriş noktasıdır ve hata ayıklama için hazır olana kadar DE programa ekledikten sonra gerçekleşecek olaylar listeler.  
  
 [Yürütme denetimi](../../extensibility/debugger/control-of-execution.md)  
 Açıklayan nasıl DE genellikle bir giriş noktası olayı, bir yük tamamlama olayı veya koşullara bağlı olarak bir durdurma olay gönderir.  
  
 [Kesme noktaları bağlama](../../extensibility/debugger/binding-breakpoints.md)  
 Nasıl, kullanıcı bir kesme noktası ayarlar, IDE istek formulates ve kesme noktası oluşturmak için hata ayıklama oturumu ister açıklar.  
  
 [İfadeleri değerlendirme](../../extensibility/debugger/evaluating-expressions.md)  
 İfadeler nasıl oluşturulduğunu ve bir ifade değerlendirildiğinde ne olacağını açıklar.  
  
 [Görselleştirme ve verileri görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Tür görselleştiricileri ve özel görüntüleyiciler (EE) ifade değerlendiricisi tarafından nasıl desteklendiği anlatılır.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)  
 Hata ayıklama ana mimari kavramlarını açıklar.  
  
 [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)  
 DE EE ve sembol işleyici (SH) Visual Studio hata ayıklama Bileşenleri'ne genel bakış sağlar.  
  
 [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md)  
 Nasıl DE aynı anda kod, belgeler ve ifade değerlendirme bağlamı içinde çalıştığı açıklanmaktadır. , Her üç bağlamları, konumu, konum veya değerlendirme için ilgili açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kullanmaya başlama](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)