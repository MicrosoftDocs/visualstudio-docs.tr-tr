---
description: ',, Bulma işleminde kısıtlamaların bulunmasına izin veren bir ÇYA sembol yordamının yerini alan geri çağırmaları alır.'
title: IDiaLoadCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9103157791f5ce67bb14bb05e708f7ffd87ee435
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148201"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
,, Bulma işleminde kısıtlamaların bulunmasına izin veren bir ÇYA sembol yordamının yerini alan geri çağırmaları alır.

## <a name="syntax"></a>Syntax

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Bu arabirim, [ıaloadcallback](../../debugger/debug-interface-access/idialoadcallback.md) arabirimindeki yöntemlere ek olarak aşağıdaki yöntemleri sunar:

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Özgün hata ayıklama dizininde bir. pdb dosyası arayıp araamayacağını belirler.|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|. Pdb dosyasına aranmaya,. exe dosyasının bulunduğu yolda izin verilip verilmeyeceğini belirler.|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|. Dbg dosyalarından hata ayıklama bilgilerinin aranmasına izin verilip verilmeyeceğini belirler.|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Sistem kök dizininde. pdb dosyalarına yönelik arama yapılmasına izin verilip verilmeyeceğini belirler.|

## <a name="remarks"></a>Açıklamalar
 İstemci uygulaması bu arabirimi uygular ve [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metoduna yapılan çağrıda buna bir başvuru sağlar. Tüm yöntemleri, [ıaloadcallback](../../debugger/debug-interface-access/idialoadcallback.md) arabirimindeki de uygulamayı unutmayın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
