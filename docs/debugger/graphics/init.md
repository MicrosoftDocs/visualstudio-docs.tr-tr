---
title: Init | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0436384e0af816475590ab84dc645848113f5ab7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476204"
---
# <a name="init"></a>Init
Etkin olarak yakalamak ve grafik bilgilerini bir grafik günlük dosyasına kaydetmek için grafik tanılamayı uygulama bileşeninin hazırlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```C++  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `vsgLogGetter`  
 Aranabilir varlık — işlevi, işlev işaretçisi, lambda veya işlev nesnesi gibi — oluşan bir arabellek uzunluğu parametreler olarak alır `wchar_t` , arabellek ve döndürür gösteren bir işaretçi `void`. Çağrıldığında, aranabilir varlık grafik bilgilerini kaydetmek için kullanılan ve döndürmeden önce belirtilen arabellek Yazar dosya adını belirler.  
  
## <a name="remarks"></a>Açıklamalar  
 `Init` İşlevi çağrılır otomatik olarak örneği `VsgDbg` sınıfı belirterek yapılandırılmıştır `bDefaultInit` kurucusu parametresinin `true`; Aksi halde, `Init` önce açıkça çağrılmalıdır Etkin olarak yakalayabilir ve grafik bilgilerini kaydedin.  
  
 Sonlandırma ve Kapat etkin grafikler çağırarak günlük dosyası `UnInit`ve ardından yakalamak ve yeni bir grafik günlük dosyası için daha fazla grafik bilgilerini çağırarak kayıt `Init` yeniden. Bu sayıda birkaç bağımsız grafik aynı kullanarak günlük dosyalarını oluşturmak istediğiniz yineleyebilirsiniz `VsgDbg` örneği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UnInit](init.md)