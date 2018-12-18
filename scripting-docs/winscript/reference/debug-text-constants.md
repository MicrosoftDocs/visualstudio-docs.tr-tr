---
title: DEBUG_TEXT sabitleri | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5126a9efefaab611cd27d2104c40918f8dc7c7e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791831"
---
# <a name="debugtext-constants"></a>DEBUG_TEXT Sabitleri
Sırasında kullanılan [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Sabitler  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Metin bir deyim aksine bir ifade olduğunu gösterir. Bu bayrak metin bazı diller tarafından ayrıştırılır şekilde etkileyebilir.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Dönüş değeri kullanılabilir ise, çağıran tarafından kullanılır.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Yan etkiler izin vermez. İfade değerlendirme, bu bayrağı ayarlarsanız, çalışma zamanı durumu değiştirmeniz gerekir.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Kesme noktaları metin değerlendirme sırasında izin verir. Bu bayrağı ayarlanmamış olduğundan, kesme noktaları metin değerlendirme sırasında yoksayılacak.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Hata raporları metin değerlendirme sırasında izin verir. Bu bayrak ayarlanmazsa, ardından hataları konağa değerlendirmesi sırasında raporlanmaz.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|İfade çalıştırmak yerine bir kod bağlamı için değerlendirilecek ifade olduğunu gösterir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası hata ayıklayıcı sabitleri, numaralandırmaları ve yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)