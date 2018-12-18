---
title: Doğrudan programa ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 361a321a2b06f777adefadae45fc50693983d339
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898375"
---
# <a name="attach-directly-to-a-program"></a>Doğrudan programa ekleme
Program zaten genellikle çalışan bir işlemde hata ayıklamak istediğiniz kullanıcılar bu süreci izleyin:  
  
1. IDE'de seçin **hata ayıklama işlemleri** komutunu **Araçları** menüsü.  
  
    **İşlemleri** iletişim kutusu görüntülenir.  
  
2. Bir işlem seçin ve tıklayın **iliştirme** düğmesi.  
  
    **İliştirme** iletişim kutusu görüntülenirse, makinede yüklü tüm hata ayıklama altyapısı (DEs) listesi.  
  
3. Seçilen işlem hata ayıklama ve ardından kullanmak için DEs belirtin **Tamam**.  
  
   Hata ayıklama paketi bir hata ayıklama oturumu başlatır ve DEs listesini geçirir. Hata ayıklama oturumu, seçilen işlem için bir geri çağırma işlevini yanı sıra bu liste sırayla geçirir ve sonra çalışan programları listeleme işlemi sorar.  
  
   Programlı olarak kullanıcı isteğine yanıt olarak, hata ayıklama paketi oturum hata ayıklama Yöneticisi (SDM) oluşturur ve bu seçilen DEs listesini geçirir. Listenin yanı sıra hata ayıklama paketi SDM geçirir. bir [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) arabirimi. Hata ayıklama paketi DEs listesini çağırarak seçili işleme geçirir [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). SDM sonra çağıran [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) işlemde çalışan programlar numaralandırmak için bağlantı noktası.  
  
   Bu noktadan itibaren her hata ayıklama altyapısı tam olarak, ayrıntılı bir program iliştirildiği [başlatmadan sonra ekleme](../../extensibility/debugger/attaching-after-a-launch.md), iki özel durumu.  
  
   Verimlilik için bir adres alanı ile SDM paylaşmak için uygulanan DEs gruplanır her DE bir dizi program, bağlanacağı sahip olacak şekilde. Bu durumda, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) çağrıları [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) ve bir dizi eklemek için programlar geçirir.  
  
   Zaten çalışan bir programa ekleme bir DE gönderdiği başlangıç olayları genellikle giriş noktası olayı içermez ikinci istisnadır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Başlatmadan sonra Başlangıç olaylarını gönderme](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)