---
title: Hata ayıklama görevleri | Microsoft Docs
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
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dd73bb7bf7fa744946dca788ed669c6153e63fea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757080"
---
# <a name="debugging-tasks"></a>Hata Ayıklama Görevleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir programda hata ayıklamak için onu başlatan gerekir ve bir hata ayıklama altyapısı (DE) bağlı gerekir, aksi takdirde DE daha önce başlatılan bir program için'e bağlı olması gerekir. Bağlandıktan sonra DE bazı başlangıç olayları oluşturmanız gerekir. Yanıt olarak, hata ayıklama paketi IDE içinde ayarlanan kesme noktaları bağlama dener. Programı ilişkili bir kesme noktasına ulaştığında, durdurur ve kullanıcı girdisini bekler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Güvenlik Sorunları](../../extensibility/debugger/security-issues.md)  
 Bir programda hata ayıklamak için gerekli olan güvenlik adımlar açıklanmaktadır.  
  
 [Program Başlatma](../../extensibility/debugger/launching-a-program.md)  
 Programı başlatmak için işletim sistemini çağıran bir DE belirleme konusunda adım adım yönergeler sağlar.  
  
 [Doğrudan Programa Ekleme](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Bir programda zaten çalışan bir işlemde hata ayıklamak için kullanılan işlem açıklanır.  
  
 [Başlatmadan Sonra Başlangıç Olaylarını Gönderme](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Program kendi ana giriş noktasıdır ve hata ayıklama için hazır olana kadar DE programa ekledikten sonra gerçekleşecek olaylar listeler.  
  
 [Yürütme Denetimi](../../extensibility/debugger/control-of-execution.md)  
 Açıklayan nasıl DE genellikle bir giriş noktası olayı, bir yük tamamlama olayı veya koşullara bağlı olarak bir durdurma olay gönderir.  
  
 [Kesme Noktaları Bağlama](../../extensibility/debugger/binding-breakpoints.md)  
 Nasıl, kullanıcı bir kesme noktası ayarlar, IDE istek formulates ve kesme noktası oluşturmak için hata ayıklama oturumu ister açıklar.  
  
 [İfadeleri Değerlendirme](../../extensibility/debugger/evaluating-expressions.md)  
 İfadeler nasıl oluşturulduğunu ve bir ifade değerlendirildiğinde ne olacağını açıklar.  
  
 [Verileri Görselleştirme ve Görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Tür görselleştiricileri ve özel görüntüleyiciler (EE) ifade değerlendiricisi tarafından nasıl desteklendiği anlatılır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklayıcı Kavramları](../../extensibility/debugger/debugger-concepts.md)  
 Hata ayıklama ana mimari kavramlarını açıklar.  
  
 [Hata Ayıklayıcı Bileşenleri](../../extensibility/debugger/debugger-components.md)  
 DE EE ve sembol işleyici (SH) Visual Studio hata ayıklama Bileşenleri'ne genel bakış sağlar.  
  
 [Hata Ayıklayıcı Bağlamları](../../extensibility/debugger/debugger-contexts.md)  
 Nasıl DE aynı anda kod, belgeler ve ifade değerlendirme bağlamı içinde çalıştığı açıklanmaktadır. , Her üç bağlamları, konumu, konum veya değerlendirme için ilgili açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

