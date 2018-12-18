---
title: Simgeler ve simge etiketleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72f4cb4b6ed35e880e1cb26980420f4e951ffc16
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471226"
---
# <a name="symbols-and-symbol-tags"></a>Simgeler ve Simge Etiketleri
Derlenmiş bir program hata ayıklama bilgilerini program veritabanı (.pdb) dosyasında hata ayıklama arabirimi erişim (DIA) SDK API'leri kullanılarak erişilebilir simgeler olarak depolanır. Tüm sembolleri sahip bir [Idiasymbol::get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) ve [Idiasymbol::get_symındexıd](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) özelliği. `symTag` Özelliği tarafından tanımlanan simgesi türünü gösterir [SymTagEnum numaralandırması](../../debugger/debug-interface-access/symtagenum.md) numaralandırması. `symIndexId` Özelliği bir `DWORD` bir simge, her örneği için benzersiz tanımlayıcı içeren değer.  
  
 Simgeler çoğunlukla simgesi yanı sıra diğer simgelerini başvurular hakkında ek bilgi belirtebilirsiniz özellikleri de bir [Idiasymbol::get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) veya [Idiasymbol::get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Bir başvuru içeren bir özelliği sorguladığınızda başvuru olarak döndürülür bir [Idiasymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi. Gibi özellikleri her zaman başka bir özellik aynı ada ve "Id" ile suffixed tarafından Örneğin, eşleştirilmelidir [Idiasymbol::get_lexicalparentıd](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) ve [Idiasymbol::get_classparentıd](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Tablolarda [simge konumları](../../debugger/debug-interface-access/symbol-locations.md), [sözcük hiyerarşisi sembol türleri](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), ve [sınıf hiyerarşisi sembol türleri](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) özellikleri her tür için anahat, simgeler. Bu özellikler, ilgili bilgileri veya diğer simgelerini başvurular olabilir. Çünkü `*Id` özellikleri yalnızca sayısal sıralı tanımlayıcıları ilgili özellikleri, daha fazla tartışma göz ardı edilir. Bunlar, parametre açıklama için yalnızca gerekli yerlerde denir.  
  
 Herhangi bir hata oluşur ve sembol özellik değeri atanan özellik erişmeye çalışırken özelliğin "yöntemi döndürür Al" `S_OK`. Dönüş değeri `S_FALSE` özelliği için geçerli sembolü geçerli olmadığını gösterir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)  
 Bir simge olabilir konumların farklı türleri açıklanmaktadır.  
  
 [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Dosyaları, modüller ve işlevleri gibi sözcük hiyerarşileri form simgesi türleri açıklanmaktadır.  
  
 [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Sınıfları, dizileri ve işlev dönüş türleri gibi farklı dil öğelerine karşılık sembol türleri açıklanmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirim Erişimi SDK'sında Hata Ayıklama](../../debugger/debug-interface-access/debug-interface-access-sdk.md)