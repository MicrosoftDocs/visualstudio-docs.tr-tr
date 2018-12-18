---
title: Kesme noktaları bağlama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e02b3da843f7e4cffe33d660a8a82ab3c4c0dc03
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153452"
---
# <a name="bind-breakpoints"></a>Kesme noktaları bağlama
Kullanıcı bir kesme noktası, belki de tuşlarına basarak ayarlar varsa **F9**, IDE istek formulates ve kesme noktası oluşturmak için hata ayıklama oturumu ister.  
  
## <a name="set-a-breakpoint"></a>Bir kesme noktası ayarlayın  
 Bir kesme noktası ayarlamak, kod veya veri kesme noktası tarafından etkilenen henüz kullanılabilir olmayabileceğinden iki adımlı bir işlem olduğu. İlk olarak, bir kesme noktası açıklanan ve kod ve veriler kullanıma sunulduğunda, daha sonra bu kod veya veri gibi bağlı olması gerekir:  
  
1.  Kesme noktası (DEs) ilgili hata ayıklama motorlardan istenen ve uygun olduğunda ardından kesme noktası kod veya veri bağlıdır.  
  
2.  Kesme noktası istek için tüm ilgili DEs gönderir hata ayıklama oturumu için gönderilir. Kesme noktasına karşılık gelen bir kesme noktası işlemek için seçtiği herhangi bir DE oluşturur.  
  
3.  Hata ayıklama oturumu bekleyen kesme noktalarının toplar ve bunları hata ayıklama paketi geri (Visual Studio hata ayıklama bileşeni) gönderir.  
  
4.  Hata ayıklama paketi bekleyen kesme noktasının kod veya veri bağlamak için hata ayıklama oturumu ister. Hata ayıklama oturumu için tüm ilgili DEs bu isteği gönderir.  
  
5.  Kesme noktasına bağlamak için DE ise, bir kesme noktası olay hata ayıklama oturumu bağımlı gönderir. Aksi durumda, bunun yerine bir kesme noktası hatası olay gönderir.  
  
## <a name="pending-breakpoints"></a>Bekleyen kesme noktaları  
 Bir bekleyen kesme noktasının birden çok kod konumlara bağlayabilirsiniz. Örneğin, bir C++ şablon için kaynak kod satırı şablondan oluşturulan her kod dizisi bağlayabilirsiniz. Hata ayıklama oturumu, bir kesme noktası ilişkili olay, olay gönderildiği sırada bir kesme noktasına bağlı kod bağlamları listelemek için kullanabilirsiniz. DE olayları bağlama her istek için birden fazla kesme noktası bağlı gönderebilir. Bu nedenle daha fazla kod bağlamı daha sonra bağlı olabilir. Ancak, bir DE bağlama istek başına yalnızca bir kesme noktası hatası olay göndermesi gerekir.  
  
## <a name="implementation"></a>Uygulama  
 Programlı olarak hata ayıklama paketi Yöneticisi (SDM) oturum hata ayıklama çağırır ve verir bir [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) sarmalar arabirimi bir [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) açıklayan yapısı Ayarlanacak kesme noktası. Kesme noktaları birçok biçimlerinin olsa da, bunlar sonuç olarak bir kod veya veri bağlamı çözümleyin.  
  
 SDM çağırarak ilgili her DE bu çağrıyı geçirir, [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) yöntemi. Kesme noktası işlemek DE seçerse, oluşturur ve döndürür bir [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimi. SDM Bu arabirimler toplar ve bunları tek bir hata ayıklama paketin dön geçirir `IDebugPendingBreakpoint2` arabirimi.  
  
 Şu ana kadar hiçbir olay üretilmedi.  
  
 Bekleyen kesme noktasının çağırarak kod veya veri bağlamak hata ayıklama paketi daha sonra çalışır [bağlama](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), DE tarafından gerçekleştirilir.  
  
 Kesme noktasına bağlıysa DE gönderir. bir [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) olay arabirimi hata ayıklama paketi. Bu arabirim, tüm kod bağlamları (veya tek bir veri bağlamı) Numaralandırılacak çağırarak kesme noktasına bağlı hata ayıklama paketi kullandığı [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), bir veya daha fazla döndüren [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) arabirimleri. [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) arabirim döndürür bir [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) arabirimi ve [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) döndürür bir [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) kod veya veri bağlamını içeren bir birleşimi.  
  
 Kesme noktası bağlanamıyor DE ise, tek bir gönderdiği [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) olay arabirimi hata ayıklama paketi. Hata ayıklama paketi çağırarak iletisidir ve hata türü (hata veya uyarı) alır [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)çizgidir [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) ve [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Bu döndürür bir [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) hata türünü ve iletisini içeren yapısı.  
  
 Bir DE bir kesme noktası işler, ancak bağlama yapılamaz, hata türü döndürür. `BPET_TYPE_ERROR`. Bir hata iletişim kutusu göstererek paketinin Hatalarını Ayıkla yanıt verir ve IDE bir ünlem işareti karakteri kaynak kod satırının sol kesme noktası glifine içine yerleştirir.  
  
 Bir DE bir kesme noktası işleme, bunu ancak bazı diğer bağlanamıyor DE bağlamak, bir uyarı verir. IDE içinde kaynak kod satırının sol kesme karakteri bir soru glif yerleştirerek yanıt verir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)