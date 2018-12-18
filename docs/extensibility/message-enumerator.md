---
title: İleti numaralandırıcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f83692db7755ae4b65f794a570b8c656d6dad145
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897023"
---
# <a name="message-enumerator"></a>İleti numaralandırıcısı
Aşağıdaki bayrakları için kullanılan `TEXTOUTPROC` işlevini çağırdığında, IDE sağlayan bir geri çağırma işlevidir [SccOpenProject](../extensibility/sccopenproject-function.md) (bkz [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) geri çağırma hakkında ayrıntılı bilgi için işlevi).  
  
 İşlemi iptal etmek için IDE istenirse, iptal iletilerinden birini alabilirsiniz. Bu durumda, kaynak denetim eklentisini kullanan `SCC_MSG_STARTCANCEL` görüntülemek için IDE sormak **iptal** düğmesi. Bundan sonra herhangi bir dizi normal ileti gönderilebilir. Bu döndürür varsa `SCC_MSG_RTN_CANCEL`, eklenti işlemi çıkar ve döndürür. Ayrıca eklentinin yoklar `SCC_MSG_DOCANCEL` düzenli aralıklarla kullanıcı işlemi iptal etti belirlemek için. Tüm işlemler yapılır ya da devre dışı kullanıcı iptal etti, eklenti gönderirken `SCC_MSG_STOPCANCEL`. `SCC_MSG_INFO`, SCC_MSG_WARNING, ve SCC_MSG_ERROR türleri, iletileri kaydırma listesinde gösterilen iletileri için kullanılır. `SCC_MSG_STATUS` metin bir durum çubuğu veya geçici görüntüleme alanı içinde gösterilmesi gerekir olduğunu gösteren özel bir türdür. Kalıcı olarak listede kalmaz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Üyeler  
 SCC_MSG_RTN_CANCEL  
 Belirtmek için geri dönüş iptal edin.  
  
 SCC_MSG_RTN_OK  
 Devam etmek için geri çağrısından döndürür.  
  
 SCC_MSG_INFO  
 Bilgilendirme iletisidir.  
  
 SCC_MSG_WARNING  
 İleti bir uyarıdır.  
  
 SCC_MSG_ERROR  
 İleti bir hatadır.  
  
 SCC_MSG_STATUS  
 İleti için durum çubuğunu yöneliktir.  
  
 SCC_MSG_DOCANCEL  
 Herhangi bir metin; IDE döndürür `SCC_MSG_RTN_OK` veya `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Bir iptal döngü başlatır.  
  
 SCC_MSG_STOPCANCEL  
 İptal döngü durdurur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)