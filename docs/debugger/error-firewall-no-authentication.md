---
title: 'Hatası: Hiçbir kimlik doğrulama güvenlik duvarı | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ca9603b7b678eb288b78d09f62cc8aac5774ebc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481466"
---
# <a name="error-firewall-no-authentication"></a>Hata: Güvenlik Duvarı Kimlik Doğrulaması Yok
Internet Bağlantısı Güvenlik Duvarı uzak makinesinde uzaktan hata ayıklama izin verecek şekilde ayarlanır değil. İle uzaktan hata ayıklama için `No Authentication`, msvsmon.exe özel durumlar listesine eklenmelidir. Bazı IPSec bağlantı noktaları açma de gerekebilir.  
  
> [!NOTE]
>  Uzaktan hata ayıklayıcı otomatik olarak Windows Güvenlik Duvarı'nı yapılandırmanız mümkün olur. Üçüncü taraf güvenlik duvarı yazılımı veya bir donanım güvenlik duvarı gibi Windows Güvenlik Duvarı dışında bir güvenlik duvarı kullanırken, uzaktan hata ayıklama izin vermek için Güvenlik Duvarı'nı el ile yapılandırılması gerekir. Bunu yapmak için bu msvsmon.exe TCP/IP bağlantı noktalarında trafiğe izin dinlemede. Varsayılan olarak, bu, bağlantı noktası 4018 ve burada 4018 tüm işletim sistemlerinde kullanılır ve 4019 yalnızca Windows x64 x86 hata ayıklama izin vermek için kullanılan 4019 işlemlerdir.  
  
 Daha fazla bilgi için bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md).