---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 103000c2ded944236762ffd55603877ece7b7968
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809462"
---
Bu adımlar, IIS'nin yalnızca bir temel yapılandırmasını gösterir. Daha ayrıntılı bilgi için veya bir Windows Masaüstü makineye yüklemek için bkz: [IIS yayımlama](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) veya [IIS 8.0 kullanarak ASP.NET 3.5 ve ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Windows Server işletim sistemleri için **rol ve Özellik Ekle** Sihirbazı aracılığıyla **Yönet** bağlantı veya **Pano** bağlantısını **Sunucu Yöneticisi'ni**. Üzerinde **sunucu rolleri** kutusunu işaretleyin, adım **Web sunucusu (IIS)**.

![Web sunucusu IIS rolünü sunucu rolleri adımda seçilir.](../media/remotedbg-server-roles-ws2012.png)

Üzerinde **rol hizmetlerini** adım, istediğiniz veya varsayılan rol hizmetlerini sağlanan kabul IIS rol hizmetlerini seçin. Dağıtım kullanarak etkinleştirmek istiyorsanız emin olun, ayarları ve Web dağıtımı yayımlama **IIS Yönetim betikleri ve araçları** seçilir.

Hizmetleri ve web sunucusu rolü yüklemek için onay adımlara devam edin. Web sunucusu (IIS) rolünü yükledikten sonra özelliği sunucusu/IIS yeniden başlatma gerekli değildir.