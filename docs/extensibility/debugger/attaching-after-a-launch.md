---
title: Başlatmadan sonra ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b767ef1aeed691255a62a9cb5c1e264034acf24e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152929"
---
# <a name="attach-after-a-launch"></a>Başlatmadan sonra ekleme
Bir programı başlattıktan sonra hata ayıklama oturumu için söz konusu program hata ayıklama altyapısı (DE) eklemek hazırdır.  
  
## <a name="design-decisions"></a>Tasarım kararları  
 İletişim paylaşılan adres alanı içinde daha kolay olduğundan, iki tasarım yaklaşımı arasında seçmeniz gerekir: hata ayıklama oturumunu DE arasındaki iletişimi ayarlayın. Veya kodu ve program arasındaki iletişimi ayarlayın. Aşağıdakiler arasında seçim yapın:  
  
-   Hata ayıklama oturumunu DE arasında iletişim kurmak için daha anlamlı olur, hata ayıklama oturumunu DE birlikte oluşturur ve programa eklemek için DE ister. Bu tasarım hata ayıklama oturumu ve DE birlikte bir adres alanı ve çalışma zamanı ortamı ve program başka bir araya bırakır.  
  
-   KODU ve program arasındaki iletişim kurmak için daha anlamlı olur, çalışma zamanı ortamı DE birlikte oluşturur. Bu tasarım SDM bir adres alanı ve DE, çalışma zamanı ortamı ve programın başka bir araya bırakır. Bu tipik komut dosyası dilleri çalıştırmak için yorumlayıcıyı ile uygulanan bir DE bir tasarımdır.  
  
    > [!NOTE]
    >  Ne DE programına iliştirir uygulamaya bağlıdır. KODU ve program arasındaki iletişimi de uygulamaya bağlıdır.  
  
## <a name="implementation"></a>Uygulama  
 Programlı olarak oturum hata ayıklama Yöneticisi (SDM) ilk kez aldığında [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) başlatılacak programı temsil eden bir nesne çağırır [iliştirme](../../extensibility/debugger/reference/idebugprogram2-attach.md) iletmeden yöntemi, bir [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) sonraki nesne kullanılan geri SDM için hata ayıklama olaylarını geçirilecek. `IDebugProgram2::Attach` Sonra yöntemi çağırır [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemi. SDM nasıl alan hakkında daha fazla bilgi için `IDebugProgram2` arabirim için bkz: [bağlantı noktasına bildirme](../../extensibility/debugger/notifying-the-port.md).  
  
 Sizin DE program aynı adres alanında çalıştırması gerekiyorsa ayıkladığınız: DE genellikle bir betik çalıştıran yorumlayıcıyı parçası olduğundan `IDebugProgramNodeAttach2::OnAttach` yöntemi döndürür `S_FALSE`. `S_FALSE` Dönüş gösterir ekleme işlemi tamamlandı.  
  
 Ancak, DE SDM adres alanında çalışır,: `IDebugProgramNodeAttach2::OnAttach` yöntemi döndürür `S_OK`, veya [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimi değil uygulanan tüm açık [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) hata ayıklaması programı ilişkili nesne. Bu durumda, [iliştirme](../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi iliştirme işlemi tamamlamak için sonunda çağrılır.  
  
 İkinci durumda, çağırmanız gerekir [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodunda `IDebugProgram2` geçildi nesne `IDebugEngine2::Attach` yöntemi, depolama `GUID` yerel programı nesne ve bu dönüş `GUID` olduğunda `IDebugProgram2::GetProgramId` yöntemi daha sonra bu nesne üzerinde çağrılır. `GUID` Programın çeşitli hata ayıklama bileşenleri arasında benzersiz olarak tanımlamak için kullanılır.  
  
 Durumunda, `IDebugProgramNodeAttach2::OnAttach` döndüren yöntem `S_FALSE`, `GUID` programını kullanmak için bu yönteme geçirilen ve bu `IDebugProgramNodeAttach2::OnAttach` ayarlar yönteminin `GUID` yerel program nesne üzerinde.  
  
 DE artık program ve herhangi bir başlangıç olayı göndermek hazır olarak eklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Doğrudan programa ekleme](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Bağlantı noktasına bildirme](../../extensibility/debugger/notifying-the-port.md)   
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Ekleme](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)