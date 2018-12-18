---
title: Idiaenumtables::Item | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc95fe0f57eabbd933f8de842d842914948f3e4c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819961"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Bir dizin veya ad ile bir tabloyu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```C++  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `index`  
 [in] Dizin veya adını [Idiatable](../../debugger/debug-interface-access/idiatable.md) alınacak. Bir tamsayı değişken kullandıysanız, aralığı 0 olmalıdır `count`-1, burada `count` tarafından döndürülen [Idiaenumtables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) yöntemi.  
  
 `table`  
 [out] Döndürür bir [Idiatable](../../debugger/debug-interface-access/idiatable.md) istediğiniz tabloyu temsil eden nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dize değişken belirtilirse, dize belirli bir tablo adları. Adı bir tablo adlarının sınıfında tanımlandığı gibi olmalıdır [sabitler (arabirim erişimi SDK'ı hata ayıklama)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Örnek  
  
```C++  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiatable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiaenumtables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Sabitler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)