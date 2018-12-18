---
title: Iwefdebuggingsupport arabirimi
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 351fb69b99393a10518168f4f9b01efe1f9efaa7
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572679"
---
# <a name="iwefdebuggingsupport-interface"></a>Iwefdebuggingsupport arabirimi
  Visual hata ayıklama için Office uygulamaları kolaylaştırmak için Studio gibi bir hata ayıklama ortamı tarafından uygulanır. Word veya Excel gibi Office uygulamasının Visual Studio'dan bu arabirim alır ve yöntemleri bazı noktalarda arabirimde hata ayıklama oturumu sırasında çağırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp 
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Yöntemler  
 Aşağıdaki tabloda Iwefdebuggingsupport arabirimi tanımlar yöntemlerini listeler.  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[Getautoınsertextensions yöntemi](../vsto/getautoinsertextensions-method.md)|Hata ayıklama sırasında otomatik olarak eklenmesini olan Office için uygulamalar hakkındaki bilgileri alır.|  
|[Setwefprocessıd yöntemi](../vsto/setwefprocessid-method.md)|Web uzantılarının Framework (WEF) içerik çalışacak işlem tanımlayıcısını sağlar.|  
  
  