---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27aab0ca87e589661798028ff38fb019dae815ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150146"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) yönteminin etkinleştirmeleri arasında yığın bağlamını korur.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaStackWalkFrame` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Bir kaydın değerini alır.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Bir kaydın değerini ayarlar.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Görüntüden belleği okur.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|En yakın işlev dönüş adresi için belirtilen yığın çerçevesini arar.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Belirtilen adreste veya yakınında bir dönüş adresi için belirtilen yığın çerçevesini arar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, kayıt ve yazma ve dönüş adreslerini okuma ve yazma için program yürütme sırasında kullanılır.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 İstemci uygulaması bu arabirimi uygular ve arabirim örneğini [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) yöntemine geçirir. Bu arabirimin aynı örneği yeniden kullanılır ve her yöntemin çağrılması sırasında yazmaçların durumunu korumak için yeniden kullanılır `execute` . `execute`Bu yöntem, dönüş adresini belirlemekte de bu arabirimi kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: dia2. h  
  
 Kitaplık: diaguid. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimler (hata ayıklama arabirimi erişim SDK 'Sı)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
