---
title: Windows bilgi koruması muaf
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1a1b38e6e30a816382da72ef8280868fa68dfb10
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845896"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Süren iş muaf uygulama olarak Visual Studio'yu yapılandırma

[Windows bilgi koruması](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) e-posta, sosyal medya ve genel bulut kuruluşun denetimi dışında kalan gibi uygulamalar aracılığıyla sızmasını Kurumsal verileri koruyun (WIP) yardımcı olur. Süren iş ortamınız veya diğer uygulamalarda değişiklik yapmaya gerek kalmadan kuruluşa ait cihazlarda ve kişisel cihazlarda yanlışlıkla veri sızıntısına karşı korumaya yardımcı olur.

*Özelliğinin tanıtıldığı* uygulamaları Süren için Kurumsal verileri korumasız ağ konumlarına geçmesini engelleyebilir ve kişisel veri şifreleme önlemek için beklenir. Bu dışarıda sürece Süren etkin ortamlarda çalışmıyor şekilde visual Studio kullanan bir uygulamaya değil. Visual Studio Süren etkin bir makinede işlevi etkinleştirmek için bu makaledeki adımları izleyin.

## <a name="configure-vs-as-a-wip-exempt-app"></a>VS Süren muaf uygulama olarak yapılandırmanıza

Visual Studio Süren kısıtlamalarından muaf ancak hala Kurumsal verileri kullanmasını sağlar. Süren iş muaf uygulamaları Kurumsal bulut kaynakları için bir IP adresi veya ana bilgisayar adı kullanarak bağlanabilir. Şifreleme uygulanır ve uygulama yerel dosyalara erişebilir.

Süren iş Visual Studio'dan muaf tutmak için izleyin [bir masaüstü uygulamasının muaf tutmak için adımları](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Süren iş muaf AppLocker ilke dosyası oluşturma

Visual Studio birden çok ikili dosyaları içerdiğinden [Süren muaf AppLocker ilke dosyası oluşturma](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). AppLocker kuralları bir klasördeki tüm dosyalar için otomatik olarak oluşturmanızı sağlar.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Kurumsal bulut kaynak ilkesi için uygulama ekleme

Visual Studio ağınızdaki Kurumsal verileri erişebileceğiniz belirtmek için aşağıdaki adımları [burada korumalı uygulamalarınızı bulmak ve kurumsal veri gönderme tanımlamak için adımları](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data). Bir IP adresi kaynaklarına bağlantılar Engellemesi Windows durdurmak için eklediğinizden emin olun /\*uygulama\*/ dize ayarı.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulamanızın davranışını Süren ile birlikte](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)