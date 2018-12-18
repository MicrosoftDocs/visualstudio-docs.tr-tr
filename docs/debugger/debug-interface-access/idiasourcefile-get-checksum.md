---
title: Idiasourcefile::get_checksum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f0484fce6f5355361c0c5156cd3c7ad827775c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919435"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
Sağlama toplamı bayt sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```C++  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cbData`  
 [in] Veri arabelleğin bayt cinsinden boyutu.  
  
 `pcbData`  
 [out] Sağlama toplamı bayt sayısını döndürür. Bu parametre olamaz `NULL`.  
  
 `data`  
 [out içinde] Sağlama toplamı bayt ile doldurulmuş bir arabellek. Bu parametre `NULL`, ardından `pcbData` gereken bayt sayısını döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Sağlama toplamı bayt oluşturmak için kullanılan sağlama toplamı algoritma türünü belirlemek için çağrı [Idiasourcefile::get_checksumtype](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) yöntemi.  
  
 Kaynak dosyadaki değişiklikler değişiklikleri sağlama toplamı bayt yansıtılması için sağlama toplamı genellikle kaynak dosyasının görüntüden oluşturulur. Sağlama toplamı bayt eşleşmiyorsa, dosyanın düşünülmesi gereken sonra dosya yüklenen görüntüden oluşturulan bir sağlama toplamı zarar görmüş veya değiştirilmiş.  
  
 Tipik sağlama toplamları hiçbir zaman boyutu 32 bayttan fazla olduğu ancak bir sağlama toplamı en büyük boyutu olan varsaymayın. Ayarlama `data` parametresi `NULL` sağlama toplamını almak için gereken bayt sayısını almak için. Ardından uygun boyutta bir arabellek ayırın ve bir kez daha yeni bir arabellek bu yöntemi çağırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idiasourcefile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)