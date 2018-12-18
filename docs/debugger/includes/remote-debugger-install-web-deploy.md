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
ms.openlocfilehash: c22ba73b464f91bf3036541304cdf94e8660970d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38811927"
---
1. Visual Studio Web dağıtımı ile uygulamalarınızı dağıtmak istiyorsanız, sunucuda Web Dağıtımı'nın en son sürümünü yükleyin.

    Web Dağıtımı'nı yüklemek için kullanın [Web Platformu Yükleyicisi (Webpı)](https://www.microsoft.com/web/downloads/platform.aspx). (Web Platformu yükleyicisi bağlantı IIS'den bulmak için seçin **IIS** Sunucu Yöneticisi'nin sol bölmesinde. Sunucuya sağ tıklayıp **Internet Information Services (IIS) Yöneticisi'ni**.)

    Web Platformu Yükleyicisi'nde, Web dağıtımı uygulamalar sekmesinde bulabilirsiniz. Doğrudan bir yükleyici de edinebilirsiniz [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Web dağıtımı doğru açarak çalıştığını doğrulayın **Denetim Masası > Sistem ve Güvenlik > Yönetim Araçları > Hizmetleri** emin olun **Web Dağıtım Aracı hizmeti** çalışıyor ( Hizmet eski sürümlerde farklı adıdır).

    Aracı hizmeti çalışmıyorsa başlatın. Hiç yoksa, Git **Denetim Masası > Programlar > program Kaldır**, bulma **Microsoft Web dağıtımı <version>** . Tercih **değişiklik** yükleme ve seçtiğiniz emin **yerel sabit diskinize yüklenecek** Web dağıtımı bileşenleri için. Değişiklik yükleme adımlarını tamamlayın.