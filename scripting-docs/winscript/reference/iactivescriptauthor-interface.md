---
title: Iactivescriptauthor arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37abb356ab24d64a05a1f1209809d63e2f55e228
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793325"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor Arabirimi
IntelliSense ve harmanlama bilgilerinin gibi hizmetler yazma temsil eder.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IActiveScriptAuthor` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Kök düzeyinde öğesinin adını altyapısının ad yazma komut dosyasına ekler. A *kök düzeyinde öğesi* özellikleri ve yöntemleri içerebilir ve, ayrıca içerebilir bir olay kaynağı bir nesnedir.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Kök düzeyinde alt sitesi olarak kod Resimli ekler `IScriptNode` nesnesi. Konak, yalnızca iki düzey Resimli tam adı olabilir.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Ad alanı komut dosyası için tür kitaplığı ekler.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|İstenen tamamlama bağlamı için tamamlama karakter kümesini döndürür.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Belirtilen öznitelikleri Resimli döndürür.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Döndürür kod bloğunda bilgi ve belirli bir karakter için bağlantı konumlarını yazın. IntelliSense, genel listeleri ve parametre ipuçları bu üye için bilgi sağlar.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Dil bilgileri döndürür.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Döndürür `IScriptNode` yazarın betik ağacının kökü.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Bir kod parçacığı metin özniteliklerini döndürür.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Bir betik bloğu metin özniteliklerini döndürür.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Belirli bir karakter deyim tamamlama uygulama tarafından tamamlama olup olmadığını belirten bir değer döndürür.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Betik metin ayrıştırır, altyapısı yazma yazma komut metni ekler ve oluşturur bir `IScriptEntry` betik bloğu karşılık gelen nesne.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Kaldırır bir `NamedItem` altyapısı yazma betik ad nesne.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Tür kitaplığı altyapısı ad yazma komut dosyasından kaldırır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası yazma arabirimleri](../../winscript/reference/active-script-authoring-interfaces.md)