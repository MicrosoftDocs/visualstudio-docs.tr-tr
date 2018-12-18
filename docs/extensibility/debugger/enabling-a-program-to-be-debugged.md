---
title: Ayıklanacak Program etkinleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad6e8e9cb8dd34e3cd084bde1eb94ff5774dd4ba
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204394"
---
# <a name="enable-a-program-to-be-debugged"></a>Bir program görüntüde hata ayıklamayı etkinleştir
Bir program, hata ayıklama altyapısı (DE) hata ayıklama yapılabilmesi, önce DE başlatın ya varolan bir program ekleyin.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Bir bağlantı noktası alma](../../extensibility/debugger/getting-a-port.md)  
 Bir program görüntüde hata ayıklamayı etkinleştirmek için ilk adım olarak bir bağlantı noktası alınacağını açıklar.  
  
 [Kayıt programı](../../extensibility/debugger/registering-the-program.md)  
 Sonraki adım bir program görüntüde hata ayıklamayı etkinleştirme açıklanmaktadır: bağlantı noktası ile kaydediliyor. Kaydedildikten sonra program ayıklanabilir ya da ekleme veya just-in-time (JIT) hata ayıklama işlemi.  
  
 [Programa ekleme](../../extensibility/debugger/attaching-to-the-program.md)  
 Sonraki adımda açıklanmaktadır: hata ayıklayıcı programa ekleme.  
  
 [Başlatma tabanlı ekleme](../../extensibility/debugger/launch-based-attachment.md)  
 Otomatik başlatma SDM ile bağlı olan bir program için başlatma tabanlı ek açıklar.  
  
 [Gerekli olayları gönderme](../../extensibility/debugger/sending-the-required-events.md)  
 Hata ayıklama altyapısı (DE) oluştururken gerekli olayları adımları ve programa ekleme.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Bir özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Hata ayıklama altyapısı (DE) tanımlar ve DE arabirimler ve bunlar farklı çalışma modları arasında geçiş için hata ayıklayıcının nasıl neden aracılığıyla uygulanan hizmetlerini açıklar.