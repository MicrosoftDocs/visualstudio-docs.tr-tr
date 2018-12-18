---
title: Dosya durumu kod numaralandırıcısı | Microsoft Docs
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
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3b7847efba2a185590c63cba19392e2ae87390d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732296"
---
# <a name="file-status-code-enumerator"></a>Dosya Durumu Kod Numaralandırıcısı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SccStatus` Numaralandırıcı kaynak denetimi sisteminizden bir dosya durumunu belirten adlandırılmış sabit değerleri içerir. Bu sabit listesi tarafından kullanılan [Sccqueryınfo](../extensibility/sccqueryinfo-function.md) ve `POPLISTFUNC` geri çağırma işlevi (bkz [POPLISTFUNC](../extensibility/poplistfunc.md) Ayrıntılar için).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>Üyeler  
 SCC_STATUS_INVALID  
 Durumu alınamadı; üzerinde güvenmeyin.  
  
 SCC_STATUS_NOTCONTROLLED  
 Dosya kaynak denetimi altında değil.  
  
 SCC_STATUS_CONTROLLED  
 Kaynak denetimi altında dosyasıdır.  
  
 SCC_STATUS_CHECKEDOUT  
 Yerel diskte geçerli bir kullanıcı tarafından kullanıma alınmış.  
  
 SCC_STATUS_OUTOTHER  
 Dosya başka bir kullanıcı tarafından kullanıma alındı.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Dosya özel olarak kullanıma.  
  
 SCC_STATUS_OUTMULTIPLE  
 Dosya birden fazla kullanıcı tarafından kullanıma alındı.  
  
 SCC_STATUS_OUTOFDATE  
 Dosyanın en son değil.  
  
 SCC_STATUS_DELETED  
 Dosyayı projeden silindi.  
  
 SCC_STATUS_LOCKED  
 Dosya kilitli; Daha fazla sürüm izin verilir.  
  
 SCC_STATUS_MERGED  
 Dosya birleştirilmiş ancak henüz sabit/doğrulandı.  
  
 SCC_STATUS_SHARED  
 Dosya, projeler arasında paylaşılır.  
  
 SCC_STATUS_PINNED  
 Açık bir sürüm için paylaşılan bir dosya.  
  
 SCC_STATUS_MODIFIED  
 Dosya değişiklik/ayrılmış/ihlal olmuştur.  
  
 SCC_STATUS_OUTBYUSER  
 Dosya geçerli bir kullanıcı tarafından kullanıma alındı.  
  
 SCC_STATUS_NOMERGE  
 Dosya hiçbir zaman ile birleştirilebilir ve GET önce kaydedilmemiş.  
  
 SCC_STATUS_RESERVED_1  
 İç kullanım için ayrılmıştır.  
  
 SCC_STATUS_RESERVED_2  
 İç kullanım için ayrılmıştır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [Sccqueryınfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)

