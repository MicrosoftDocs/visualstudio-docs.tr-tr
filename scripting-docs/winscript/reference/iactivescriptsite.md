---
title: Iactivescriptsite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23dba403a7889fe46817a21ed8e4be65b1c05b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793613"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Windows komut dosyası altyapısı için bir site oluşturmak için ana bilgisayar tarafından uygulanır. Genellikle, bu site (örneğin, ActiveX denetimleri) komut dosyası için görünür olan tüm nesneler kapsayıcısı ile ilişkilendirilecek. Genellikle, bu kapsayıcı, belge veya görüntülenmesini sayfasına karşılık gelir. Microsoft Internet Explorer, örneğin, bu tür bir kapsayıcı için görüntülenen her HTML sayfası oluşturur. Her ActiveX denetimi (veya diğer Otomasyon nesnesi) sayfası ve komut dosyası altyapısı kendisini olacaktır bu kapsayıcıda numaralandırılabilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|||  
|-|-|  
|Yöntem|Açıklama|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Kullanıcı arabirimi öğeleri görüntülemek için konağın kullandığı yerel ayar kimliği alır.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Altyapının çağrısıyla eklendi bir öğe hakkında bilgi edinir [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) yöntemi.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Geçerli belge sürümü açısından ana bilgisayarın benzersiz olarak tanımlayan ana bilgisayar tarafından tanımlanan bir dize alır.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Komut dosyası yürütme tamamlandıktan sonra çağrılır.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Ana bilgisayara komut dosyası altyapısı durumları değiştiğini bildirir.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Ana bilgisayara altyapı komut dosyası çalıştırılırken bir yürütme hatası oluştu bildirir.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Ana bilgisayara komut dosyası altyapısı kod yürütme başladıktan bildirir.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Ana bilgisayar komut dosyası altyapısı kod yürütülmesini döndürdüğünü bildirir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası arabirimleri](../../winscript/reference/active-script-interfaces.md)