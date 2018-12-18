---
title: POPLISTFUNC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 061f7b4d1c1fb9ddeb76444f058a95fe30abe47c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920878"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Bu geri çağırma için sağlanan [SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE tarafından ve kaynak denetimi eklentisi tarafından bir dosya veya dizinlerin listesini güncelleştirmek için kullanılır (Ayrıca sağlanan `SccPopulateList` işlevi).  
  
 Ne zaman bir kullanıcının seçtiği **alma** komut IDE'de IDE kullanıcı alabileceği tüm dosyaların bir liste kutusu görüntüler. Ne yazık ki, IDE kullanıcı alabilirsiniz tüm dosyaların tam listesini bilmez; Bu liste yalnızca eklenti vardır. Diğer kullanıcılar için kaynak kodu denetim projesinin dosyaları eklediyseniz, bu dosyalar, listede görünmesi gerekir, ancak IDE bunları hakkında bilmez. IDE kullanıcı alabilirsiniz gördüğü dosyaların bir listesini oluşturur. Kullanıcıya bu listeyi gösterir önce çağrılır [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` kaynak denetimi eklentisi vererek eklemek ve dosyaları listeden silmek için bir fırsat.  
  
## <a name="signature"></a>İmza  
 Kaynak Denetimi Eklentisi aşağıdaki prototipe sahip bir IDE uygulanan işlevi çağrılarak listenin değiştirir:  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 pvCallerData  
 `pvCallerData` Parametresi için (IDE) çağıran tarafından geçirilen [SccPopulateList](../extensibility/sccpopulatelist-function.md). Kaynak Denetimi Eklentisi bu parametrenin içeriği hakkında hiçbir şey varsaymanız gerekir.  
  
 fAddRemove  
 Varsa `TRUE`, `lpFileName` dosya listesine eklenmesi gereken bir dosyadır. Varsa `FALSE`, `lpFileName` dosya listesinden silinmesi gereken bir dosyadır.  
  
 nStatus  
 Durumunu `lpFileName` (bir birleşimini `SCC_STATUS` BITS; bkz: [dosya durum kodu](../extensibility/file-status-code-enumerator.md) Ayrıntılar için).  
  
 lpDosyaAdı  
 Dosya adı eklemek veya listeden silmek için tam dizin yolu.  
  
## <a name="return-value"></a>Dönüş değeri  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`TRUE`|Eklenti bu fonksiyonu çağıran devam edebilirsiniz.|  
|`FALSE`|IDE tarafında (örneğin, yetersiz bellek durumunun) ilgili bir sorun oluştu. Eklenti işlem durdurmanız gerekir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İsteğe bağlı olarak ekleyin veya dosya listeden silmek için kaynak denetimi eklentisi isteyen her dosya için tümleştirilmesidir, bu işlevi çağıran `lpFileName`. `fAddRemove` Bayrak listeye eklemek için yeni bir dosya veya silmek için eski bir dosyayı belirtir. `nStatus` Parametre dosyanın durumunu sağlar. Eklenti SCC dosya eklemeye ve silmeye sona erdiğinde arasında döndürür [SccPopulateList](../extensibility/sccpopulatelist-function.md) çağırın.  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST` Özelliği bit Visual Studio için gereklidir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Dosya durum kodu](../extensibility/file-status-code-enumerator.md)