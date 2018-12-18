---
title: Office çözüm güvenliğinde sorunlarını giderme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 002759a1a5fd8a16ee3e7842df7439d6e6b9755f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862937"
---
# <a name="troubleshoot-office-solution-security"></a>Office çözüm güvenliğinde sorunlarını giderme
  Bu konuda, Office çözümleri güvenliğini sağlama ile çalışırken karşılaşabileceğiniz genel sorunları çözmek için ipuçları verilmektedir.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Güvenilir çözümleri kısıtlı sitelerden yüklenemez.  
 Web sitesi Internet Explorer Yasak siteler bölgesi listede yoksa, kullanıcılar bir web konumundan bir çözüm yükleyemez. Çözüm, güvenilir bir sertifika ile imzalanmış olsa bile bu geçerlidir.  
  
 Dağıtım bildirimi URL'sini beş bölgeleri birine kategorilere ayrılabilir:  
  
- Bilgisayarım  
  
- Internet  
  
- Yerel intranet  
  
- Güvenilen siteler  
  
- Yasak siteler  
  
  Dağıtım bildiriminin konumunu Yasak siteler bölgesi için atanmış olan varsa [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çözüm yüklemez. Konumun bilinen ve güvenilir kullanıcı konumu Yasak siteler bölgesi kaldırabileceğiniz ve çözümü yükler. Bölgelerini yönetme hakkında daha fazla bilgi için bkz. [yapılandırma ClickOnce Güvenilen Yayımcılar](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Internet Explorer Artırılmış Güvenlik Yapılandırması veya Internet Explorer 7 yüklü olmadığında çözümleri ağ dosya paylaşımları veya web konumlarında yüklenemez  
 Internet Explorer Artırılmış Güvenlik Yapılandırması (IEESC) Windows Server 2003'te ve üstünde ve Internet Explorer 7 ve üzeri, İnternet'e göz atabilmenizi kullanıcıların önemli ölçüde kısıtlar. Kullanıcıların bir ağ dosya paylaşımı veya web konumundan Office çözümleri yüklemeye çalışırken şu hata iletisini alabilirsiniz: "Sertifika içindağıtımbildirimiimzalamakiçinkullanıldığındanbuuygulamadakiözelişlevsellikçalışmaz*SolutionName* güvenilir değil. Daha fazla yardım için yöneticinize başvurun."  
  
 Dağıtım bildirimi URL'sini Internet bölgesine kategorize edilirse IEESC ve Internet Explorer 7 ve üzeri ile bildirim güvenilir bir yayımcıdan bir sertifikası olmalıdır veya çözüm yüklenemez. IEESC, varsayılan davranışı güven karar vermek için son kullanıcı onay istemi görüntülenir.  
  
 IEESC ve Internet Explorer 7 etkisini yönetmek ve üzeri, Web siteleri ve Evrensel Adlandırma Kuralı (UNC) yolları belirlemek için güvenilir ve güvenilen güvenlik bölgeleri (Yerel intranet veya Güvenilen siteler) birine ekleyin. Bölgelerini yönetme hakkında daha fazla bilgi için bkz. [yapılandırma ClickOnce Güvenilen Yayımcılar](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri güvenliğini sağlama](../vsto/securing-office-solutions.md)  
  
  