---
title: Hesapları seçenekleri başvurusu
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a77a7ee6c9f9cdb545c5cbfb1c4fb7336ab19b70
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378106"
---
# <a name="accounts-environment-options-dialog-box"></a>Hesapları, ortam, Seçenekler iletişim kutusu

Visual Studio'ya oturum açmak için kullandığınız hesapları ile ilgili çeşitli seçenekleri ayarlamak için bu sayfayı kullanın.

## <a name="personalization-account"></a>Kişiselleştirme hesabı

### <a name="synchronize-settings-across-devices"></a>Ayarları cihazlar arasında eşitleme

Ayarlarınızı birden fazla makinede senkronize belirtmek için bu seçeneği kullanın. Daha fazla bilgi için [eşitlenen ayarlar](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Cihaz kod akışı etkinleştir

Bu seçenek belirlendiğinde, Visual Studio davranışını değiştiren seçtiğinizde **Hesap Ekle** üzerinde **dosya** > **hesap ayarları** sayfası. Görme yerine **hesabınızda oturum** sayfasında karşılaşırsınız oturum açmak için bir URL ve kodu bir web tarayıcısına yapıştırın sunan bir iletişim kutusu. Bu seçenek, burada Visual Studio'ya normal şekilde, örneğin, Internet Explorer'ın daha eski bir sürümünü kullanıyorsanız veya güvenlik duvarınızı erişimi kısıtlıyorsa oturum açamazsınız durumlarda kullanışlıdır. Daha fazla bilgi için [birden çok kullanıcı hesabıyla çalışma](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Kayıtlı Azure Bulutları

Bu bölümde, bir veya daha fazla Visual Studio'ya oturum açmak için kullandığınız hesabın üzerinden erişime sahip Azure bulut örnekleri gösterilir. Örneğin, şirketinizin veri merkezinde özel bir Azure örneğine erişim olabilir. Veya, bağımsız veya kamu örneğine Azure gibi Azure Çin veya Azure ABD bölgesinde erişiminiz Kamu. Azure genel bulut örneği listesinde varsayılan olarak görünür ve kaldırılamaz.

Ek bir Azure bulut seçerek kayıt **Ekle** düğmesi. **Yeni Azure Bulutu Ekle** iletişim listeler çeşitli iyi bilinen bir Azure bulut örneklerine bağlanabilirsiniz veya özel bir Azure uç noktası URL'si girebilirsiniz.

![Yeni Azure bulut örneği ekleme](media/add-new-azure-cloud.png)

Ek bir Azure bulut kaydettikten sonra Visual Studio'da oturum açtığınızda oturum açmak için hangi Azure buluta seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden fazla bilgisayara ayarları eşitleme](../synchronized-settings-in-visual-studio.md)
- [Visual Studio’da oturum açma](../signing-in-to-visual-studio.md)
- [Birden çok kullanıcı hesabıyla çalışma](../work-with-multiple-user-accounts.md)
- [Ortam ayarları](../environment-settings.md)
- [Ortam Seçenekleri iletişim kutusu](../../ide/reference/environment-options-dialog-box.md)