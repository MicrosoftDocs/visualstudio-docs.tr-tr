---
title: IDebugProcess3 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b6c81634b89eb4c722e09a2449efbeb993fd8bf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753109"
---
# <a name="idebugprocess3"></a>IDebugProcess3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, çalışan bir işleme ve programları temsil eder. Bu arabirim için çeşitli yöntemlerin yerine mevcut [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimi. Bu işlemdeki tüm programlar üzerinde denetim sağlar.  
  
> [!NOTE]
>  [Devam](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md), ve [adım](../../../extensibility/debugger/reference/idebugprogram2-step.md) yöntemleri kullanım dışı ve artık kullanılmamalıdır. Karşılık gelen yöntemler kullanır `IDebugProcess3` bunun yerine arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Bu arabirim, programlar, grup olarak yönetmek için özel bağlantı noktası sağlayıcısı tarafından uygulanır. Programlar bir grup olarak yönetilen, bunların yürütme kontrol edebilir ve ifade değerlendiricisi için bir dil oluşturmak. Bu arabirim bağlantı sağlayıcı tarafından uygulanmalıdır.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim, bu işlemde tanıtılan programlar bir grup ile etkileşim kurmak için öncelikle oturum hata ayıklama Yöneticisi tarafından (SDM) adı verilir.  
  
 Çağrı [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) üzerinde bir [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) arabirimi bu arabirim elde edilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Devralınan yöntemleri yanı sıra [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` aşağıdaki yöntemleri uygular.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Yürütülmesini veya bir işlem üzerinden Adımlama devam eder.|  
|[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Yürütme işlemi başlar.|  
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Bir yönerge veya deyimi işlemindeki adımları iletin.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Hata ayıklama işlemi başlatıldı nedenini alır.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Hata ayıklama altyapısı yükleyebilir ve uygun ifade değerlendiricisi barındırma dili ayarlar.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Bu işlem için ayarlanmış dili alır.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Düzenle ve devam et (ENC) Bu işlem için devre dışı bırakır.<br /><br /> Bu yöntem bir özel bağlantı noktası sağlayıcısı uygulamaz (her zaman döndürmelidir `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Bu işlem için ENC durumunu alın.<br /><br /> Bu yöntem bir özel bağlantı noktası sağlayıcısı uygulamaz (her zaman döndürmelidir `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Kullanılabilir hata ayıklama altyapıları için benzersiz tanımlayıcıları dizisini alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

