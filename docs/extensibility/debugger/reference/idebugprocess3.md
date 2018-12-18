---
title: IDebugProcess3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21c4dfffe02d2550bccf5b23f264ab8283524aa2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121098"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Bu arabirim, çalışan bir işlemi ve programları temsil eder. Bu arabirim için çeşitli yöntemlerin yerine mevcut [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimi. İşlemdeki tüm programlar üzerinde denetim sağlar.  
  
> [!NOTE]
>  [Devam](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md), ve [adım](../../../extensibility/debugger/reference/idebugprogram2-step.md) yöntemleri kullanım dışı bırakılmış ve artık kullanılmalıdır. Karşılık gelen yöntemleri kullanılacağı `IDebugProcess3` yerine arabirim.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Bu arabirim, bir grup olarak programları yönetmek için özel bir bağlantı noktası sağlayıcı tarafından uygulanır. Programları grup olarak yönetilen, kendi yürütme kontrol edebilir ve bir dil için bir ifade değerlendiricisi oluşturun. Bu arabirim bağlantı noktası sağlayıcı tarafından uygulanmalıdır.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim, bu işlemde tanıtılan programlar grubu ile etkileşim kurmak için öncelikle oturum hata ayıklama Yöneticisi tarafından (SDM) adı verilir.  
  
 Çağrı [QueryInterface](/cpp/atl/queryinterface) üzerinde bir [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) bu arabirimi sağlamak için arabirim.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Kaynağından devralındı yöntemleri yanı sıra [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` aşağıdaki yöntemlerini uygular.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Devam etmek](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Yürütülmesi veya bir işlem üzerinden atlama devam eder.|  
|[Yürütme](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Bir işlemin yürütülmesine başlar.|  
|[Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Bir yönerge veya işlem deyiminde adımları iletin.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Hata ayıklama işlemi başlatıldı nedenini alır.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Barındırma dili ayarlar, böylece hata ayıklama altyapısı uygun ifade değerlendiricisi yükleyebilirsiniz.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Bu işlem için ayarlanmış dili alır.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Düzenle ve devam (ÇÖZÜCÜ) Bu işlem için devre dışı bırakır.<br /><br /> Bu yöntem bir özel bağlantı noktası tedarikçi uygulamaz (her zaman döndürmelidir `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|ÇÖZÜCÜ durumu için bu işlemi alma.<br /><br /> Bu yöntem bir özel bağlantı noktası tedarikçi uygulamaz (her zaman döndürmelidir `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Kullanılabilir hata ayıklama altyapıları için benzersiz tanımlayıcı dizisini alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)