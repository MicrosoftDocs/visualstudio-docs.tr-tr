---
title: Doğrudan programa ekleme | Microsoft Docs
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
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 01845979c838c065774aeab55abc9a1a2cfcde6c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773567"
---
# <a name="attaching-directly-to-a-program"></a>Doğrudan Programa Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Program zaten genellikle çalışan bir işlemde hata ayıklamak istediğiniz kullanıcılar bu süreci izleyin:  
  
1. IDE'de seçin **hata ayıklama işlemleri** komutunu **Araçları** menüsü.  
  
    **İşlemleri** iletişim kutusu görüntülenir.  
  
2. Bir işlem seçin ve tıklayın **iliştirme** düğmesi.  
  
    **İliştirme** iletişim kutusu görüntülenirse, makinede yüklü tüm hata ayıklama altyapısı (DEs) listesi.  
  
3. Seçilen işlem hata ayıklama ve ardından kullanmak için DEs belirtin **Tamam**.  
  
   Hata ayıklama paketi bir hata ayıklama oturumu başlatır ve DEs listesini geçirir. Hata ayıklama oturumu, seçilen işlem için bir geri çağırma işlevini yanı sıra bu liste sırayla geçirir ve sonra çalışan programları listeleme işlemi sorar.  
  
   Programlı olarak kullanıcı isteğine yanıt olarak, hata ayıklama paketi oturum hata ayıklama Yöneticisi (SDM) oluşturur ve bu seçilen DEs listesini geçirir. Listenin yanı sıra hata ayıklama paketi SDM geçirir. bir [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) arabirimi. Hata ayıklama paketi DEs listesini çağırarak seçili işleme geçirir [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). SDM sonra çağıran [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) işlemde çalışan programlar numaralandırmak için bağlantı noktası.  
  
   Bu noktadan itibaren her hata ayıklama altyapısı tam olarak, ayrıntılı bir program iliştirildiği [ekleme sonra bir başlatma](../../extensibility/debugger/attaching-after-a-launch.md), iki özel durumu.  
  
   Verimlilik için bir adres alanı ile SDM paylaşmak için uygulanan DEs gruplanır her DE bir dizi program, bağlanacağı sahip olacak şekilde. Bu durumda, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) çağrıları [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) ve bir dizi eklemek için programlar geçirir.  
  
   Zaten çalışan bir programa ekleme bir DE gönderdiği başlangıç olayları genellikle giriş noktası olayı içermez ikinci istisnadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlatmadan sonra Başlangıç olaylarını gönderme](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Hata Ayıklama Görevleri](../../extensibility/debugger/debugging-tasks.md)

