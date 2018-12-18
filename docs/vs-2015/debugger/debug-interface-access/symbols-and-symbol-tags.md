---
title: Simgeler ve simge etiketleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67fbe790eaded11806f1ca1fbfcaaeee38a36116
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732198"
---
# <a name="symbols-and-symbol-tags"></a>Simgeler ve Simge Etiketleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Derlenmiş bir program hata ayıklama bilgilerini program veritabanı (.pdb) dosyası hata ayıklama arabirimi erişim (DIA) SDK'sı API'leri kullanılarak erişilebilen simgeler olarak depolanır. Tüm sembolleri bir [Idiasymbol::get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) ve [Idiasymbol::get_symındexıd](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) özelliği. `symTag` Özelliği tarafından tanımlanan sembol türü gösterir [SymTagEnum numaralandırması](../../debugger/debug-interface-access/symtagenum.md) sabit listesi. `symIndexId` Özelliği bir `DWORD` içeren bir sembolü her örneği için benzersiz tanımlayıcı değeri.  
  
 Semboller çoğunlukla sembol yanı sıra diğer sembol başvuruları hakkında ek bilgi belirten özelliği de bir [Idiasymbol::get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) veya [Idiasymbol::get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Başvuru içeren bir özellik sorguladığınızda, başvuru olarak döndürülür bir [Idiasymbol](../../debugger/debug-interface-access/idiasymbol.md) nesne. Gibi özellikleri her zaman başka bir özellik ile aynı ada ancak "Id" ile sonekli tarafından Örneğin, eşleştirilmelidir [Idiasymbol::get_lexicalparentıd](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) ve [Idiasymbol::get_classparentıd](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Tablolardaki [simge konumları](../../debugger/debug-interface-access/symbol-locations.md), [sözcük hiyerarşisi sembol türleri](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), ve [sınıf hiyerarşisi sembol türleri](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) özellikleri her bir tür için anahat, simgeler. Bu özellikler, ilgili bilgileri veya diğer semboller başvuruları olabilir. Çünkü `*Id` özellikleri yalnızca sayısal sıralı tanımlayıcılar, ilgili özellikleri, daha fazla tartışma göz ardı edilir. Bunlar, parametre açıklama için yalnızca gerekli yerlerde denir.  
  
 Özellik, herhangi bir hata oluşursa ve sembol özelliği bir değer atanmadan erişmeye çalışırken, özelliğin "yöntemi Al" `S_OK`. Dönüş değeri `S_FALSE` özelliği için geçerli simge geçerli olmadığını gösterir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)  
 Bir sembol olabilir konumları farklı türlerde açıklar.  
  
 [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Dosyaları, modüller ve işlevleri gibi sözcük temelli hiyerarşileri form sembol türleri açıklanmaktadır.  
  
 [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Sınıflar, diziler ve işlev dönüş türleri gibi farklı dil öğesine karşılık gelen sembol türleri açıklanmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirim Erişimi SDK'sında Hata Ayıklama](../../debugger/debug-interface-access/debug-interface-access-sdk.md)



