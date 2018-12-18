---
title: 64-bit hata ayıklayıcı COM sınıfı kaydını geçirme | Microsoft Docs
ms.custom: ''
ms.date: 11/10/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: douge
ms.workload:
- greggm
ms.openlocfilehash: 6c7578ddbdf84a1520a732fb64380bb53e5359f9
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637857"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>64-bit hata ayıklayıcı COM sınıfı kaydı geçirme

COM kaydetmek için hata ayıklayıcı uzantıları regasm, regsvr32, kullanarak veya doğrudan kayıt defterine ve içine yüklenen yazma HKEY_CLASSES_ROOT sınıfları *msvsmon.exe* (uzaktan hata ayıklayıcı), artık bu bilgiyi sağlamanız mümkündür msvsmon i HKEY_CLASSES_ROOT olarak yazmaya gerek kalmadan kayıt. Bu, eski .NET hata ayıklayıcı ifade değerlendiricilerini veya yüklemek için yapılandırılan hata ayıklama motorlarını etkiler *msvsmon.exe* işlem.

## <a name="msvsmon-comclass-def"></a>msvsmon comclass def

Bu tekniği kullanması için ekleme bir  **.msvsmon comclass def.json* msvsmon yanındaki dosyası (Installdır:* \Common7\IDE\Remote Debugger\x64*).

Yönetilen kaydeden bir örnek msvsmon comclass def dosyası ve bir yerel sınıf aşağıda verilmiştir:

Dosya adı: *MyCompany.MyExample.msvsmon comclass def.json*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
