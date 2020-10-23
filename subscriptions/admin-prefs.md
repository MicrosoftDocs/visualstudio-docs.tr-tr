---
title: Yönetim portalında anlaşma tercihlerini ayarlama
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 10/22/2020
ms.topic: conceptual
description: Yönetim portalında dil, kişiler, abonelik düzeyi ve diğer kullanıcılara yönelik tercihleri ayarlama hakkında bilgi edinin
ms.openlocfilehash: e044db92a318114cd2f159b859843db354fac6c7
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467446"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Yönetim portalında anlaşmalarda tercihleri ayarlama
Süper Yöneticiler yönetim portalında (Yönetim Portalı) her anlaşma için global olarak uygulanacak belirli tercihleri ayarlayabilir.  Bu tercihler, aboneler eklendiğinde yönetici için abonelik ayrıntılarını otomatik olarak doldurur ve yalnızca süper yöneticiler tarafından genel olarak değiştirilebilir.  

## <a name="access-preferences"></a>Erişim tercihleri
Tercihleri görüntülemek veya değiştirmek için sözleşmede süper yönetici haklarına sahip bir oturum açma KIMLIĞI kullanarak [yönetici portalında](https://manage.visualstudio.com) oturum açmış olmanız gerekir.  

Tercihlerinizi ayarlamak için:
1. Yönetim portalında süper yönetici ayrıcalıklarına sahip bir KIMLIKLE oturum açın.
2. Sol bölmedeki ayar simgesine tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Yönetici tercihleri düğmesi](_img/admin-prefs/admin-prefs-button.png "Tercihleri Yönet ' e tıklayarak yöneticileri görüntüleyin")

3. **Anlaşma tercihleri**' ne tıklayın.
Sol tarafta bir panel açılır ve kullanılabilir tercihleriniz görüntülenir. 

   > [!div class="mx-imgBorder"]
   > ![Yönetici tercihleri açılır kutusu](_img/admin-prefs/admin-prefs-flyout.png "Tercihlerinizi ayarlayın ve Kaydet ' e tıklayın.")

## <a name="set-your-preferences"></a>Tercihlerinizi ayarlama
Kullanılabilir tercihlerin her birini ve etkilerini keşfedelim. 

### <a name="agreement"></a>Sözleşme
Süper yönetici olduğunuz birden çok anlaşmanız varsa, genişletilmiş ayarlar panelinin sağ tarafındaki açılan kutuda istediğiniz sözleşmeyi seçebilirsiniz.  Ayarladığınız Tercihler yalnızca bu sözleşme için geçerlidir.  Bireysel Yöneticiler, abonelikleri atarken bu tercihlerden bazılarını büyük/küçük harfe göre geçersiz kılabilir. 

Oturum açmak için kullandığınız e-posta adresiyle ilişkili yalnızca bir anlaşma varsa, genişletilmiş ayarlar panelinin sağında görüntülenir ve açılır liste devre dışı bırakılır. 

### <a name="contact-email-address"></a>İletişim e-posta adresi
Bu tercih, abonelerinizin, abone portalının [abonelikler sayfasında](https://my.visualstudio.com/subscriptions) **yöneticime başvur** düğmesini kullanarak yöneticilere ulaşması için bir yol sağlar.  Bu tercih boş bırakılırsa, abone iletileri anlaşmada tüm yöneticilere ve süper yöneticilere iletilir.  Bu iletişim e-postasına yönelik kitlelerinizi uyarlamak için bir grup e-posta diğer adı veya güvenlik grubu kullanmanızı öneririz. İsterseniz, tek bir e-posta adresi girişi yapmayı da tercih edebilirsiniz.

> [!NOTE]
> Burada listeettiğiniz e-posta adresi abonelere sağlanmaz.  Bir abone abone portalında **yönetici isteime bir iletişim** gönderdiğinde ileti, abone üzerinde kullanıma sunulmadan diğer ada iletilir. 

### <a name="default-subscription-level"></a>Varsayılan abonelik düzeyi
Bu ayarı, bir kullanıcıya bir abonelik atandığında, sözleşmenizde bulunan abonelik düzeylerinin hangisinin varsayılan olarak seçili olduğunu anlamak için kullanabilirsiniz.  Yöneticiler ayarı sözleşmenizde herhangi bir abonelik düzeyiyle değiştirebilir; bu, en sık kullanılan seçiminizi sürekli olarak yapmayı önler. 

### <a name="default-communication-preferences"></a>Varsayılan iletişim tercihleri
Varsayılan bir iletişim dili ve yerel ayar ayarlamak, abonelikleri atama sürecini kolaylaştırabilir.  Örneğin, geliştirme ekibiniz yönetici takımından farklı bir ülkeyi temel alıyorsa, abonelerin konumuna en uygun tercihleri ayarlayabilirsiniz. Bu ayarlar, bireysel aboneler için tüm yöneticiler tarafından hala değiştirilebilir. 

### <a name="default-external-subscribers-setting"></a>Varsayılan dış aboneler ayarı
Bu tercih, yöneticilerin kuruluşunuzun kiracı/Dizin dışından abone ekleyip ekleyemeyeceğine karar vermenize olanak tanır.  Bunu kapatırsanız, dış abonelere izin verilmez.  Bunu etkinleştirirseniz ve bir yöneticinin dış abone ekleme denemeleri varsa, bu kullanıcıların kendi seçimini onaylamasını istenir ve aboneliği atamasına izin verilir. Yöneticiler bu ayarı geçersiz kılamaz. 

### <a name="default-downloads-setting"></a>Varsayılan indirmeler ayarı
Varsayılan olarak açık olan bu ayarın etkinleştirilmesi, yöneticilerin yeni abonelikler oluştururken indirmelere erişmesini sağlayacaktır.  Yöneticiler, ayrı bir abonelik temelinde İndirmeleri hala devre dışı bırakabilir.  İndirmelere erişimin devre dışı bırakılması, ürün anahtarlarına erişimi de devre dışı bırakır.  


## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-admins"></a>S: abonelerin yöneticilerle iletişim kurabilmesi için **iletişim e-posta adresini** devre dışı bırakabilir miyim?
Y: Hayır-bir güvenlik grubu, Grup e-posta diğer adı veya tek bir e-posta adresi kullanarak hangi yöneticilere bağlantı kurulabildiğini belirleyebilmeniz için özellik devre dışı bırakılamaz.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>S: bir abonenin e-postasını yanıtlıyorum, e-posta adresim olur mu?
Y: yanıtınız, kullanmakta olduğunuz herhangi bir e-posta istemcisinden geldiği için, abonenin aldığı yanıt, kullandığınız e-posta adresini gösterir.  Bu nedenle, bir grup diğer adından yanıt verirseniz, grup diğer adını görürler.  Kendi e-posta adresinizden yanıt verirseniz, bunu görür.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>S: abone portalında **yöneticime başvur** özelliği hakkında daha fazla bilgi bulabilirim?
A: [Yöneticimde Iletişim kurun](contact-my-admin.md) makalemize göz atın. 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>S: **iletişim e-posta adresini** tamamlamadığımızda bir abone, kendi Isteklerini alan **yönetici ile iletişim kurun özelliğimi** kullanıyor mu?
Y: **ilgili e-posta adresi** tercihine belirli bir e-posta adresi ayarlanmamışsa, anlaşmada tüm yöneticiler isteği alır. 

## <a name="resources"></a>Kaynaklar
- [Visual Studio Yönetim ve Abonelik Desteği](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi edinin.
- [Ayrı abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)