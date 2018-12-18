---
title: IDebugPortNotify2 | Microsoft Docs
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
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5bc329807d4b610ae42d3bb5ac5c95faf37db40
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740381"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim kaydeder veya üzerinde çalıştığı bağlantı noktası ile ayıklanabilir bir program kaydını siler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Özel bağlantı noktası sağlayıcısı ekleme ve kaldırma bağlantı noktasından desteklemek için bu arabirimi uygular. Genellikle uygulayan aynı nesne üzerinde uygulanan [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimi.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bir çağrı [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) üzerinde `IDebugPort2` arabirimi bu arabirim döndürür. Ayrıca, bir çağrı [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) bu arabirimi döndürür. Hata ayıklama altyapısı, bir parametre olarak bu arabirimi görebilirsiniz [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugPortNotify2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Hata ayıklaması yapılabilir bir program çalıştığı bağlantı noktası ile kaydeder.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Bir program çalıştığı bağlantı noktasından ayıklanabilir kaydını siler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Özel bağlantı noktası sağlayıcısı, hata ayıklama bağlantı programlar zaman yüklü veya kaldırılmış bilmenin bir yolu olmadığı sürece, bu arabirimini uygulaması gerekir. Belirli bir bağlantı noktası üzerinden hata ayıklama için yüklenen tüm programlar bu arabirimi kullanılarak izlenir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

