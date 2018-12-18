---
title: Idiasession::findfile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 32c8fa5c6f3cd8ec3cf1cead397eadadb99e050d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909947"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Derlenecek dosya ve ada göre kaynak dosyaları alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```C++  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pCompiland`  
 [in] Bir [Idiasymbol](../../debugger/debug-interface-access/idiasymbol.md) arama bağlamı olarak kullanılacak derlenecek temsil eden nesne. Bu parametre kümesine `NULL` kaynak dosyaları tüm derleme bulunamıyor.  
  
 `name`  
 [in] Alınacak kaynak dosyasının adını belirtir. Bu parametre kümesine `NULL` tüm kaynak dosyaları alınacak.  
  
 `option`  
 [in] Ad arama uygulanan karşılaştırma seçeneklerini belirtir. Değerlerini [NameSearchOptions numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md) numaralandırma, tek başına veya birlikte kullanılabilir.  
  
 `ppResult`  
 [out] Döndürür bir [Idiaenumsourcefiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) kaynak dosyaların listesini içeren bir nesne alındı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="example"></a>Örnek  
  
```C++  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idiaenumsourcefiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [Idiasession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions Numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md)