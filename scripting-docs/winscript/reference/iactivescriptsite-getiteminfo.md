---
title: IActiveScriptSite::GetItemInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccb898c14571d1f1fd1fcae7cb0b9a6d322f2754
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793781"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
İle eklenen bir öğe hakkında bilgi almak komut dosyası altyapısı sağlar [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrName`  
 [in] Belirtilen öğe ile ilişkili adı [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) yöntemi.  
  
 `dwReturnMask`  
 [in] Öğe hakkındaki bilgiler döndürülmelidir belirten bir bit maskesi. Komut dosyası altyapısı bilgileri olası en az miktarda olduğundan isteği bazı dönüş parametreleri (örneğin, `ITypeInfo`) yüklemek veya oluşturması uzun zaman alabilir. Aşağıdaki değerlerden bir bileşimi olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Döndürür `IUnknown` bu öğe için arabirim.|  
|SCRIPTINFO_ITYPEINFO|Döndürür `ITypeInfo` bu öğe için arabirim.|  
  
 `ppunkItem`  
 [out] Bir işaretçi alan değişkenin adresini `IUnknown` verilen öğeyle ilişkili arabirimi. Komut dosyası altyapısı kullanabilirsiniz `IUnknown::QueryInterface` elde etmek için yöntemi `IDispatch` öğesi için arabirim. Bu parametre NULL ise alır `dwReturnMask` SCRIPTINFO_IUNKNOWN değer içermez. Ayrıca, öğe adı ile ilişkili hiçbir nesnesi yoksa NULL alır; Bu mekanizma SCRIPTITEM_CODEONLY bayrağı ayarlanmış adlandırılmış öğe eklendiğinde basit bir sınıf oluşturmak için kullanılan [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) yöntemi.  
  
 `ppTypeInfo`  
 [out] Bir işaretçi alan değişkenin adresini `ITypeInfo` öğeyle ilişkili arabirimi. Bu parametre NULL ise alır `dwReturnMask` SCRIPTINFO_ITYPEINFO değer içermez veya bu öğe için tür bilgileri kullanılamıyor. Tür bilgileri kullanılabilir değilse, nesne olayları kaynak olamaz ve ad bağlama gerçekleşen, ile `IDispatch::GetIDsOfNames` yöntemi. Unutmayın `ITypeInfo` alınan arabirimi nesne birden çok arabirimleri ve olay arabirimleri destekleyebilir çünkü maddenin coclass'ı (TKIND_COCLASS) açıklanmaktadır. Öğe destekliyorsa `IProvideMultipleTypeInfo` arabirimi, `ITypeInfo` alınan arabirimidir sıfır dizini ile aynı `ITypeInfo` , elde edilebilir kullanarak `IProvideMultipleTypeInfo::GetInfoOfIndex` yöntemi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersiz.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`TYPE_E_ELEMENTNOTFOUND`|Belirtilen adda bir öğe bulunamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem yalnızca tarafından gösterilen bilgileri alır `dwReturnMask` parametresi; bu performansını artırır. Örneğin, bir `ITypeInfo` arabirimi bir öğe için gerekli değildir, bu yalnızca içinde belirtilmemiş `dwReturnMask`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md)