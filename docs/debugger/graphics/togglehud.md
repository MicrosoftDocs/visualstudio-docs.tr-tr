---
title: ToggleHUD | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86ce582ab49d4d079f01f7231f49aa761baa1069
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472519"
---
# <a name="togglehud"></a>ToggleHUD
Grafik tanılama değiştirir *HUD* (Head yukarı görüntüle) kaplama açıp kapatma.  
  
## <a name="syntax"></a>Sözdizimi  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Grafik tanılama HUD grafik tanılama altında çalışan uygulama sol üst köşesinde görüntülenir. Çalışma zamanı grafik bilgilerini yakalama ve çağrılarak eklenir iletileri ve uygulama hakkında bilgi görüntüler [AddMessage](addmessage.md) üye işlevi.  
  
 HUD geçiş yapmak için etkin olarak grafik bilgilerini yakalama gerekmez — diğer bir deyişle, bir örneği üzerinden değiştirilebilir `VsgDbg` sınıfı, ancak [Init](init.md) üye işlevi ilk çağrılması gerekmez.