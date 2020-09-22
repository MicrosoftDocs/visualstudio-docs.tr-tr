---
title: Uzak makine uzak bağlantılar iletişim kutusunda görünmüyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5392a6219b1bf8bf42146cacf8216a63f1fa3832
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852569"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Hata: Uzak Makine, Uzaktan Bağlantılar iletişim kutusunda görünmüyor
Uzak makine uzak bağlantılar iletişim kutusunda görünmüyorsa, aşağıdaki genel nedenleri kontrol edin.

 Yönetilen Uyumluluk modu kullanıyorsanız, lütfen Visual Studio 2010 belgelerini denetleyin: [Uzaktan hata ayıklama sorunlarını giderme-Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Bu hatanın yaygın nedenleri

- Uzak makine, farklı bir alt ağda bulunan bir makinede çalışıyor. Bu hatayı gidermek için, niteleyici iletişim kutusunda makine adını veya IP adresini el ile yazın

- Uzak makinede uzaktan hata ayıklayıcı çalışmıyor. Bu hatayı düzeltemedi, uzaktan hata ayıklayıcıyı başlatın.

- Güvenlik Duvarı, Visual Studio ile uzak makine arasındaki iletişimi engelliyor. Bu hatayı onarmak için, güvenlik duvarınızı Visual Studio ve uzaktan hata ayıklayıcı 'nın (msvsmon) iletişim kurmasına izin verecek şekilde yapılandırın.

- Virüsten koruma yazılımı, Visual Studio ile uzak makine arasındaki iletişimi engelliyor. Bu hatayı onarmak için, virüsten koruma yazılımını Visual Studio ve uzaktan hata ayıklayıcı 'nın (msvsmon) iletişim kurmasına izin verecek şekilde yapılandırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)