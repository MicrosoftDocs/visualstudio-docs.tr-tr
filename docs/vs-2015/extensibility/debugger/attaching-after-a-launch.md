---
title: Başlatmadan sonra ekleme | Microsoft Docs
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
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 416c05a7592d9f036a76a5d96537b4be917a0651
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774711"
---
# <a name="attaching-after-a-launch"></a>Başlatmadan Sonra Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir programı başlatan sonra hata ayıklama oturumu için söz konusu program hata ayıklama altyapısı (DE) eklemek hazırdır.  
  
## <a name="design-decisions"></a>Tasarım kararları  
 İletişim paylaşılan adres alanı içinde daha kolay olduğundan, hata ayıklama oturumunu DE arasındaki veya DE ve program arasındaki iletişimi kolaylaştırmak için daha fazla mantıklı olmadığını karar vermeniz gerekir. Aşağıdakiler arasında seçim yapın:  
  
-   Hata ayıklama oturumunu DE arasındaki iletişimi kolaylaştırmak için daha anlamlı olur, hata ayıklama oturumunu DE birlikte oluşturur ve programa eklemek için DE ister. Bu hata ayıklama oturumu ve DE birlikte bir adres alanı ve çalışma zamanı ortamı ve program başka bir araya bırakır.  
  
-   Ardından DE ve program arasındaki iletişimi kolaylaştırmak için daha anlamlı olur, çalışma zamanı ortamı birlikte DE oluşturur. SDM bir adres alanında ve DE, çalışma zamanı ortamı ve program başka bir araya bırakır. Tipik bir komut dosyası dilleri çalıştırmak için yorumlayıcıyı ile uygulanan bir DE budur.  
  
    > [!NOTE]
    >  Ne DE programına iliştirir uygulamaya bağlıdır. KODU ve program arasındaki iletişimi de uygulamaya bağlıdır.  
  
## <a name="implementation"></a>Uygulama  
 Programlı olarak oturum hata ayıklama Yöneticisi (SDM) ilk kez aldığında [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) başlatılacak programı temsil eden bir nesne çağırır [iliştirme](../../extensibility/debugger/reference/idebugprogram2-attach.md) iletmeden yöntemi, bir [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) sonraki nesne kullanılan geri SDM için hata ayıklama olaylarını geçirilecek. `IDebugProgram2::Attach` Sonra yöntemi çağırır [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemi. SDM nasıl alan hakkında daha fazla bilgi için `IDebugProgram2` arabirim için bkz: [bağlantı noktasına bildirme](../../extensibility/debugger/notifying-the-port.md).  
  
 Sizin DE, genellikle DE bir betik çalıştırarak yorumlayıcıyı bir parçası olduğundan hata ayıklanan programa aynı adres alanında çalıştırması gerekiyorsa `IDebugProgramNodeAttach2::OnAttach` yöntemi döndürür `S_FALSE`, attach işleminin tamamlandığını belirten.  
  
 DE SDM adres alanında çalıştırıyorsa, diğer taraftan, `IDebugProgramNodeAttach2::OnAttach` yöntemi döndürür `S_OK` veya [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimi hiç üzerinde uygulanmadı [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) ayıklanan programla ilişkili nesne. Bu durumda, [iliştirme](../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi iliştirme işlemi tamamlamak için sonunda çağrılır.  
  
 İkinci durumda, çağırmanız gerekir [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodunda `IDebugProgram2` geçildi nesne `IDebugEngine2::Attach` yöntemi, depolama `GUID` yerel programı nesne ve bu dönüş `GUID` olduğunda `IDebugProgram2::GetProgramId` yöntemi daha sonra bu nesne üzerinde çağrılır. `GUID` Programın çeşitli hata ayıklama bileşenleri arasında benzersiz olarak tanımlamak için kullanılır.  
  
 Durumunda, dikkat `IDebugProgramNodeAttach2::OnAttach` döndüren yöntem `S_FALSE`, `GUID` programını kullanmak için bu yönteme geçirilen ve bu `IDebugProgramNodeAttach2::OnAttach` ayarlar yönteminin `GUID` yerel program nesne üzerinde.  
  
 DE artık program ve herhangi bir başlangıç olayı göndermek hazır olarak eklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
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

