---
title: Idiasymbol::get_undecoratednameex | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de8eb57e8b1e31be835163e67fa12e3cd6556892
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930667"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Alır kısmını veya tamamını ve bir adı bir c++ ile düzenlenmiş adın (bağlantı).  
  
## <a name="syntax"></a>Sözdizimi  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `undecoratedOptions`  
 [in] Bayrakların birleşimi, denetimin ne döndürülür belirtir. Belirli değerleri ve ne yaptıkları için Açıklamalar bölümüne bakın.  
  
 `pRetVal`  
 [out] Düzenlenmemiş adını bir C++ ile düzenlenmiş adın döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi halde döndürür `S_FALSE` veya bir hata kodu.  
  
> [!NOTE]
>  Dönüş değeri `S_FALSE` özelliği simge için kullanılabilir değil anlamına gelir.  
  
## <a name="remarks"></a>Açıklamalar  
 `undecorateOptions` Aşağıdaki bayrakların birleşimi olabilir.  
  
> [!NOTE]
>  Bildirimleri kodunuza ekleyin ya da kullandığınız ham değerler gerek bayrağı adları DIA SDK içinde tanımlı değil.  
  
|Bayrağı|Değer|Açıklama|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Tam undecoration etkinleştirir.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Genişletilmiş anahtar sözcükler Microsoft alt çizgi baştaki kaldırır.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Microsoft genişletilmiş anahtar sözcükleri genişletilmesi devre dışı bırakır.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Genişletme birincil bildirimi için dönüş türünün devre dışı bırakır.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Bildirim modelinin genişletme devre dışı bırakır.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Bildirim dil tanımlayıcısı genişletilmesi devre dışı bırakır.|  
|UNDNAME_RESERVED1|0x0020|AYRILMIŞ.|  
|UNDNAME_RESERVED2|0x0040|AYRILMIŞ.|  
|UNDNAME_NO_THISTYPE|0x0060|Üzerindeki tüm değiştiricilere devre dışı bırakır `this` türü.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Üyeleri için erişim belirticileri genişletilmesi devre dışı bırakır.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Genişletme "throw-imzası" işlevleri ve işlev işaretçileri için devre dışı bırakır.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Genişletme, devre dışı bırakır `static` veya `virtual` üyeleri.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|UDT döndüren için Microsoft modelinin genişletme devre dışı bırakır.|  
|UNDNAME_32_BIT_DECODE|0x0800|32-bit düzenlenmiş adlar undecorates.|  
|UNDNAME_NAME_ONLY|0x1000|Yalnızca birincil bildiriminin adı alır; yalnızca döndürür [kapsam::] adı.  Şablon parametreleri genişletir.|  
|UNDNAME_TYPE_ONLY|0x2000|Kodlama türü yalnızca bir giriştir; bir soyut bildirimcisi oluşturur.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|Gerçek şablon parametreleri büyük/küçük harf kullanılabilir.|  
|UNDNAME_NO_ECSU|0x8000|Enum/sınıf/yapı/birleşim bastırır.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Geçerli tanımlayıcı karakterler için onay bastırır.|  
|UNDNAME_NO_PTR64|0x20000|Ptr64 çıktısında içermez.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)