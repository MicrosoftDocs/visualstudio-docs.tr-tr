---
title: DebugStackFrameDescriptor yapısı | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 346f039ca96f2160d7ac28686e542b3d88a91dfb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791852"
---
# <a name="debugstackframedescriptor-structure"></a>DebugStackFrameDescriptor Yapısı
Yığın çerçevelerini listeler ve aynı iş parçacığındaki çeşitli listeleyicilerden alınan çıktıyı birleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Üyeler  
 `pdsf`  
 Yığın çerçeve nesnesi.  
  
 `dwMin`  
 Bu yığın çerçevesi ile ilişkili fiziksel adreslerini alt aralığı makine bağımlı gösterimi.  
  
 `dwLim`  
 Bu yığın çerçevesi ile ilişkili fiziksel adreslerini üst aralığı makine bağımlı gösterimi.  
  
 `fFinal`  
 Çerçeve işlenmekte olduğunu belirten bayrak.  
  
 `punkFinal`  
 Bu parametre değilse `NULL`, birleştirme geçerli Numaralandırıcı durdurmanız gerekir ve yeni bir tane başlatılmalıdır. Nesne yeni numaralandırması başlatmak nasıl gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem Hata Ayıklama Yöneticisi'ni, birden çok komut dosyası motorları yığını çerçevelerden sıralamak için bu yapı kullanır. Kurala göre yığınları aşağı artar. Sonuç olarak, yığınları büyüdüğü yukarı mimarileri üzerinde ikişer baytının adresleri olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası hata ayıklayıcı sabitleri, numaralandırmaları ve yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)