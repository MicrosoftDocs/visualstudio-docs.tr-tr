---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bd2273e7ca2769c5dde43d1c29f08989503659f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949129"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Bir yığın çerçeve nesnesi hakkında almak için bilgileri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Üyeler  
 FIF_FUNCNAME  
 Başlat/kullanım `m_bstrFuncName` alan.  
  
 FIF_RETURNTYPE  
 Başlat/kullanım `m_bstrReturnType` alan.  
  
 FIF_ARGS  
 Başlat/kullanım `m_bstrArgs` alan.  
  
 FIF_LANGUAGE  
 Başlat/kullanım `m_bstrLanguage` alan.  
  
 FIF_MODULE  
 Başlat/kullanım `m_bstrModule` alan.  
  
 FIF_STACKRANGE  
 Başlat/kullanım `m_addrMin` ve `m_addrMax` alanlar (yığın aralığı).  
  
 FIF_FRAME  
 Başlat/kullanım `m_pFrame` alan.  
  
 FIF_DEBUGINFO  
 Başlat/kullanım `m_fHasDebugInfo` alan.  
  
 FIF_STALECODE  
 Başlat/kullanım `m_fStaleCode` alan.  
  
 FIF_ANNOTATEDFRAME  
 Başlat/kullanım `m_fAnnotatedFrame` alan.  
  
 FIF_DEBUG_MODULEP  
 Başlat/kullanım `m_pModule` alan.  
  
 FIF_FUNCNAME_FORMAT  
 İşlev adı biçimlendirir. Sonucun içerisinde geri dönmemiş ise `m_bstrFunName` alan ve başka bir alan doldurulmalıdır.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Dönüş türüne ekler `m_bstrFuncName` alan.  
  
 FIF_FUNCNAME_ARGS  
 Bağımsız değişkenleri ekler `m_bstrFuncName` alan.  
  
 FIF_FUNCNAME_LANGUAGE  
 Dil ekler `m_bstrFuncName` alan.  
  
 FIF_FUNCNAME_MODULE  
 Modül adı ile ekler `m_bstrFuncName` alan.  
  
 FIF_FUNCNAME_LINES  
 Ekler için satır sayısı `m_bstrFuncName` alan.  
  
 FIF_FUNCNAME_OFFSET  
 Ekler `m_bstrFuncName` satırını başından itibaren bayt uzaklığını simgesini `FIF_FUNCNAME_LINES` belirtilir. Varsa `FIF_FUNCNAME_LINES` belirtilmezse veya satır numaralarını kullanılamıyorsa uzaklık bayt cinsinden işlevi başlangıcından ekler.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Her işlev bağımsız değişken türü ekler `m_bstrFuncName` alan.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Her işlev bağımsız değişkeni adını ekler `m_bstrFuncName` alan.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Her işlev bağımsız değişken değerini ekler `m_bstrFuncName` alan.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Türü, adı ve tüm bağımsız değişkenlerinin değerini ekler `m_bstrFuncName` alan.  
  
 FIF_ARGS_TYPES  
 Bağımsız değişken türleri alınır ve biçimlendirilmiş.  
  
 FIF_ARGS_NAMES  
 Bağımsız değişken adları alınır ve biçimlendirilmiş.  
  
 FIF_ARGS_VALUES  
 Bağımsız değişken değerlerini alınır ve biçimlendirilmiş.  
  
 FIF_ARGS_ALL  
 Almak ve türü, adı ve tüm bağımsız değişkenlerin değerini biçimlendirin.  
  
 FIF_ARGS_NOFORMAT  
 Bağımsız değişkenleri olan olması biçimlendirilmemiş olduğunu belirtir (örneğin, değil açılış ve kapanış ayraçlarını bağımsız değişken listesi geçici olarak ekleyin ya da bağımsız değişkenler arasındaki ayırıcı ekleyin).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 (Özellik) işlev değerlendirmesi bağımsız değişken değerlerini alınırken kullanılmamalıdır belirtir.  
  
 FIF_FILTER_NON_USER_CODE  
 Hata ayıklama altyapısı dahil edilmez kullanıcı olmayan kod çerçevelerini filtre sağlamaktır.  
  
 FIF_ARGS_NO_TOSTRING  
 İzin verme `ToString()` İşlev değerlendirmesi veya işlev bağımsız değişkenleri döndürülürken biçimlendirme.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Barındırma işlemi yerine barındırılan uygulama etki çerçeve bilgi edinmiş.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bayraklar geçirilen [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) ve [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) içinde başlatılacak hangi alanların olduğunu göstermek için yöntemlerini [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapıyla veya yapılarla.  
  
 Bu bayraklar Ayrıca hangi alanları göstermek için kullanılan [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapısı, kullanılan ve geçerli yapısı döndürülür. Bu değerler, bit düzeyinde ile birleştirilebilir `OR`.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)