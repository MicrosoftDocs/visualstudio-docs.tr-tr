---
title: Init | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed9bffdcd9f5e6a862197928f2a7369cd3643625
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781302"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Etkin bir şekilde yakalayıp grafik bilgilerini bir grafik günlük dosyasına kaydetmek için grafik tanılama uygulama bileşeninin hazırlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `vsgLogGetter`  
 Aranabilir bir varlık — işlevi, işlev işaretçisi, lambda veya işlev nesnesi gibi — oluşan bir arabellek uzunluğu parametre olarak alan `wchar_t` ve bir işaretçi, arabellek ve döndürür `void`. Çağrıldığında çağrılabilir varlık grafik bilgilerini kaydetmek için kullanılır ve sonuç döndürülmeden önce belirtilen arabelleğe Yazar dosya adını belirler.  
  
## <a name="remarks"></a>Açıklamalar  
 `Init` İşlevi örneği otomatik olarak çağrılır `VsgDbg` sınıfı belirterek yapılandırılmıştır `bDefaultInit` parametre, oluşturucunun `true`; Aksi takdirde `Init` açıkça önce çağrılmalıdır etkin bir şekilde yakalayabilir ve grafik bilgilerini kaydedin.  
  
 Sonlandırma ve Kapat etkin grafikler çağırarak günlük dosyası `UnInit`, ardından yakalama ve yeni bir grafik günlük dosyası için daha fazla grafik bilgisi çağırarak kayıt `Init` yeniden. Bu olarak aynı kullanarak günlük dosyalarını birden fazla bağımsız grafik oluşturmak istediğiniz kadar tekrarlayabilirsiniz `VsgDbg` örneği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UnInit](../debugger/init.md)



