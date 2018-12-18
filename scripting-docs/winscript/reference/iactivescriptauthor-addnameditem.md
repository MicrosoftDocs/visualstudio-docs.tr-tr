---
title: IActiveScriptAuthor::AddNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83d2597f8468bb97d20da655a56a751191ec4b55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793277"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Kök düzeyinde öğesinin adını altyapısının ad yazma komut dosyasına ekler. A *kök düzeyinde öğesi* özellikleri ve yöntemleri içerebilir ve, ayrıca içerebilir bir olay kaynağı bir nesnedir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszName`  
 [in] Komut dosyasını görüntülendiği şekilde öğenin adı. Adın benzersiz ve kalıcı olması gerekir.  
  
 `dwFlags`  
 [in] Adlandırılmış öğesi ile ilişkilendirilmiştir bayraklar. Aşağıdaki değerlerden bir bileşimi olabilir:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Öğenin adını betik ad alanında kullanılabilir olduğunu gösterir. Bu öğenin özellikleri, yöntemleri ve olayları erişim sağlar.<br /><br /> Kurala göre öğenin alt üye öğesinin özelliklerini içerir. Bu nedenle, tüm alt nesne özellikleri ve yöntemleri (ve alt üyeleri, yinelemeli olarak) erişebilir.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Komut dosyası komut dosyası olay işleyicileri olabilir öğesi kaynağının olayları gösterir.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Öğesi genel özellikleri ve komut dosyasıyla ilişkili yöntemleri topluluğu gösterir. Üyeleri genel değişkenler ve yöntemleri yazılan.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Altyapısı yazma komut dosyası kaydettiyseniz öğesi kaydedilmesi gerektiğini gösterir.|  
|SCRIPTITEM_CODEONLY|0x00000200|Adlandırılmış öğe yalnızca kod bir nesneyi temsil eder ve yazar için üye yok gösterir.|  
|SCRIPTITEM_NOCODE|0x00000400|Adlandırılmış öğe eklenmekte olan bir adı olduğunu ve yazmak için hiçbir şey sahip olduğunu gösterir.|  
  
 `pdisp`  
 [in] `IDispatch` , `NamedItem` Yöntemler, özellikler veya olay kaynağı toplamak için kullanılan nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)