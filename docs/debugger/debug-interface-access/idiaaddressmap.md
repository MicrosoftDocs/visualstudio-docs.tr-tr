---
title: Idiaaddressmap | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb1593f59125c4b6325bfd97015485cc2a4d85f6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468976"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
DIA SDK'sı sanal ve göreli sanal adresleri hata ayıklama nesneleri için nasıl hesaplar üzerinde denetim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDiaAddressMap`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Belirli bir oturum için bir adres eşlemesi kurulduğunda olup olmadığını gösterir.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Adres eşlemesi simgesi adresleri çevirmek için kullanılması gerekip gerekmediğini belirtir.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Hesaplama ve göreli sanal adresleri kullanımını etkinleştirilip etkinleştirilmediğini gösterir.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|İstemcinin etkinleştirmek veya devre dışı göreli sanal adresleri hesaplama olanak tanır.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Geçerli resmi hizalaması alır.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Resmi hizalaması ayarlar.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Ayarlar göreli sanal adres çevirisi etkinleştirmek için üstbilgiler görüntü.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Görüntü düzeni çevirileri desteklemek için bir adres eşlemesi sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim tarafından sağlanan denetim iki sağladığınız veri kümesi içinde kapsüllenir: görüntü üstbilgileri ve adres eşlemeleri. Çoğu istemcilerin kullandığı [Idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) yöntemi bir görüntü ve yöntem genellikle tüm gerekli üst bilgileri ve haritalar verileri kendisini bulabilir uygun hata ayıklama bilgilerini bulamıyor. Ancak bazı istemciler özel işleme ve veri için arama uygular. Bu tür istemciler yöntemlerini kullanın `IDiaAddressMap` DIA SDK ile arama sonuçları sağlamak için arabirim.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim DIA session nesnesinden kullanılabilir. İstemci çağrılarını `QueryInterface` yöntemi arabirimde DIA oturum nesnesi, genellikle [Idiasession](../../debugger/debug-interface-access/idiasession.md)almak için `IDiaAddressMap` arabirimi.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: Dia2.h  
  
 Kitaplığı: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimler (arabirim erişimi SDK'SINDA hata ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)