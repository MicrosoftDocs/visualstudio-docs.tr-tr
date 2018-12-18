---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4655b6105a940b7f2c742ba8bcd0812d0be5ab95
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433191"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
Varsayılan örneği olup olmadığını, varlığı tanımlayan [VsgDbg sınıfı](vsgdbg-class.md) sınıfı — programlı yakalama arabirimi sağlayan — sağlanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```C++  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Değer  
 Bir önişlemci tarafından varlığını simgesini veya olmaması, varsayılan örneği olup olmadığını belirler `VsgDbg` sınıfı sağlanır. Bu simge tanımlanmazsa, ardından hiçbir varsayılan örneğini `VsgDbg` sınıfı sağlanır; Aksi takdirde, varsayılan bir örnek sağlanan ve programınızı çalıştırılmadan önce başlatılır.  
  
 Programlı yakalama arabirimi genel kapsamda olan bir işaretçi yoluyla sağlanır `g_pVsgDbg`.  
  
```cpp
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan örnek genellikle yeterli olur, ancak bu DLL dışında D3D cihazı oluşturulduğunda programlı yakalama arabirim bir DLL içinde kullanmak için oluşturabilir ve kendi örneğini yönetme `VsgDbg` sınıfı. Bu şekilde programlı yakalama API için kendi arabirimi yönetiyorsanız tanımlayarak varsayılan örneği devre dışı `VSG_NODEFAULT_INSTANCE` ek yükten kaçınmak için.  
  
 Varsayılan örnek devre dışı değil ise, program çalışmadan önce otomatik olarak başlatılır ve programınızı sona erdiğinde otomatik olarak yok. Başlatma veya bu örneğin açıkça uninitialize gerekmez.  
  
 Varsayılan örnek devre dışı bırakmak için tanımlamalısınız `VSG_NODEFAULT_INSTANCE` dahil önce `vsgcapture.h` programınızdaki.  
  
## <a name="example"></a>Örnek  
 Bu örnek, varsayılan örnek devre dışı bırakma gösterir:  
  
```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```
