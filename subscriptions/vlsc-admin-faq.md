---
title: VLSC yönetici geçiş ile ilgili SSS | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/13/2018
ms.topic: Get-Started-Article
description: Toplu Lisans Hizmet Merkezi Yönetim geçiş SSS
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: e4bc2902c819f4e677127d4c2c857ed1fb5dc015
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36296357"
---
# <a name="visual-studio-subscriptions-administration-migration"></a>Visual Studio abonelikleri yönetim geçiş

Sonraki birkaç ay Visual Studio abonelikleri (önceki adıyla MSDN Abonelikleri) yönetim için değişiklikleri geliyor. Bugün, Visual Studio Toplu Lisans Hizmet Merkezi (VLSC) portalını yönetilen Toplu Lisanslama aboneliği ve abonelik satın alabilirsiniz. Yeni bir Yönetim Portalı oluşturulur ve Visual Studio abonelik bu yeni portalında gelecekte yönetilecek. VLSC tarafından sağlanan mevcut işlemleri ek olarak, yeni portalı toplu atama izleme ve abonelikleri ve Azure erişimini yönetmek için Active Directory'ye (Azure AD) kullanma olanağı filtreleme sınırsız izin verir. En yeni Visual Studio Yönetim Portalı bulunur: [ https://manage.visualstudio.com ](https://manage.visualstudio.com).

> [!Note]
> Bu geçiş MPSA müşteriler etkilemez.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="why-is-it-changing"></a>Neden değiştiriyor?
Yeni portalı Visual Studio abonelik yönetimi deneyimini iyileştirmek ve nasıl satın alınan bağımsız olarak, Visual Studio Aboneliklerini Yönetme tek bir deneyim oluşturabilirsiniz. Yeni portalı, Azure AD sağlar ve gelecek için bize konumlandırır yeni bir platformu vardır. Ayrıca, gidin ve kullanmak, daha kolay bir güncelleştirilen kullanıcı arabirimini olacaktır yönetici verimliliği artırma.

### <a name="who-will-be-impacted"></a>Kimin etkilenecek?
Değişiklik etkin Toplu Lisanslama anlaşmaları varsa ve Visual Studio abonelikleri Toplu Lisanslama ile satın aldığınız tüm müşterileri etkiler.

### <a name="when-is-it-changing"></a>Ne zaman değiştiriyor?
Bu yoğun geçiş ve Visual Studio abonelikler için etkin Toplu Lisanslama sözleşmeleri ile tüm müşteriler için yeni Yönetim Portalı üzerinden geçirilene kadar aşamaları tamamlandı. Geçiş 2017 ilk üç ay boyunca başlamıştır. Biz, Toplu Lisanslama müşterilerimizin kendi zamanlanmış geçiş hafta çalıştırılmasının size bildirir.

### <a name="does-my-organization-need-to-sign-up-for-azure-active-directory-azure-ad"></a>Kuruluşum, Azure Active Directory (Azure AD) kaydolmak istiyor mu?
Kuruluşunuz için Azure AD kaydolun gerekmez, ancak herhangi bir zamanda bunu yapabilirsiniz. Azure AD eklemek isterseniz, hiçbir ücret Azure AD için ücretsiz katmanı kullanarak bunu yapabilirsiniz. Azure Active Directory ile kuruluşunuz Artırılmış güvenlik, Denetim ve uzun vadeli güvenilirlik koruyamıyor. Azure AD için hazır değilseniz, bugün yaptığınız gibi Microsoft Accounts (MSA) kullanmaya devam etmek mümkün olacaktır.

### <a name="how-do-i-know-when-my-organization-will-be-migrated"></a>Kuruluşumun zaman geçirilecek nasıl anlarım?
Birincil/bildirimler kişiler bunları bir kuruluşunuz geçirilmeden önce hafta ekleme işlemini tamamlamak için davet bizden e-posta alırsınız. Abonelik yöneticileri aynı zamanda bunları artık birincil/bildirimler kişiler temas ve ayrıntıları hakkında başarıyla Hazırlanmanız sağlamaya yardımcı olmak sağlanan olduğunu bilmeniz izin vererek bir e-posta alırsınız. Bilgi edinmek için nasıl [kuruluşunuzun birincil/bildirimler kişiler bulun](#How-do-I-find-out-who-my-Primary-or-Notices-Contact-is?).

### <a name="is-onboarding-different-from-migration"></a>Onboarding geçiş farklı mı çalışıyor?
Evet.  Bu işlemde iki aşama vardır. Ayarlama (veya ekleme), kuruluşunuzun geçiş çalıştırılmasının yönetici olarak kesinti olmadan iş içinde olmasını sağlar. Biz kuruluşunuzun bilgileri geçirmek sonra sonra yeni Portalı'nda Visual Studio Aboneliklerini yönetmek mümkün olacaktır. Birincil/bildirimler kişiler yerleşik geçirilen önce yapmazsanız, abonelik yöneticileri engellenir ve onboarding işlemi tamamlanana kadar Aboneliklerini yönetmek mümkün olmaz.

### <a name="what-is-the-onboarding-process"></a>Onboarding işlemi nedir?
Bir e-posta ekleme işlemini tamamlamak için birincil ve bunları davet kişiler bildirimler gönderilir.
İşlem hakkında yönergeler için aşağıya bakın.
1.  **PCN bulma ve oturum açma:**

    a.  E-posta ile birincil ve bildirimler kişiler benzersiz bir bağlantı ve bunların genel müşteri numarası (PCN), son üç basamak ile sağlanır. *

    b.  Tüm PCN elde etmek için birincil ilgili kişinin VLSC'ye oturum açmak gerekir (PCN yerini yönergeleri bulunabilir aşağıda).

    c.  PCN aldıktan sonra bunları oturum açmak için ister kendi benzersiz bağlantı seçmeniz gerekir. Bunlar yoksa, kuruluşunuzun üzerinde Azure AD (Kuruluşunuz üzerinde Azure AD ise) iş/Okul hesabı veya bir Microsoft hesabı (MSA) kullanarak oturum mümkün olacaktır.

    d.  Ardından, bunlar PCN girmeniz istenir.

2.  **Yöneticilerinizi ayarlayın:**

    PCN girdikten sonra kullanıcılar sayfasına Süper yöneticileri ve administrators (daha önce Abonelik Yöneticisi olarak da bilinir) eklemeniz mümkün olduğu ulaşabilirsiniz. İdeal olarak bu aboneliklerinizi yönetmede herhangi kesinti aktarıp, kuruluşunuzun geçiş tarihinden önce tamamlanmalıdır.

3.  **Yeni Abonelik Yönetim portalına erişim:** kuruluşunuz geçirildikten sonra e-postalar Süper yöneticileri ve yeni portalına erişmek ve abonelik yönetimi başlamak için Yöneticiler bunları davet gönderilir.

> [!NOTE]
> Birincil ya da bildirimler kişiler birden fazla e-posta almaya devam ederseniz, bu, birden fazla PCN sahip oldukları anlamına gelir. Her e-posta ile başvurulan PCN için benzersiz bağlantıyı kullanarak işlemini tamamlamak gerekir.

### <a name="what-is-the-difference-between-a-super-admin-and-an-administrator"></a>Süper yönetici ve yönetici arasındaki fark nedir?
Birincil/bildirimler kişi ilk kez oturum açtığında, bunlar otomatik olarak bir süper yönetici olarak ayarlanır Süper yönetici ekleme/diğer Süper yöneticileri veya Yöneticiler silerek abonelikleri yönetici erişimi yönetebilirsiniz ve abonelikleri da yönetebilirsiniz. Süper yönetici kendilerini yanı sıra diğer Süper yöneticilerin atamak seçebilirsiniz.

Yöneticiler (daha önce Abonelik Yöneticisi olarak da bilinir) yalnızca Aboneliklerini yönetmek kullanabilirsiniz ancak Aboneliklerini Yönetme erişimi olanların denetleyemezsiniz.

### <a name="how-will-i-as-an-administrator-onboard-to-the-new-portal"></a>Nasıl olacak ı, bir yönetici olarak, yeni portalı yerleşik?
Kuruluşunuzun birincil kişiler ve bildirimler kişiler bunları ya da iş kullanarak oturum açın veya Okul hesapları, Azure Active Directory (Azure AD) veya kişisel Msa'lar tarafından yedeklenen etmesine imkan tanıyacak bir sayfaya sürer benzersiz bir bağlantı içeren bir e-posta alırsınız. Oturum açtıktan sonra kuruluşunuzun genel müşteri numarası (PCN) veya Yetkilendirme numarası anlaşmaları doğrulamak için girmeniz gerekir. Bunlar daha sonra gibi diğer yöneticiler ekleyebilmek için bir süper yönetici olarak Visual Studio Aboneliklerini yönetmek için ayarlanması.

### <a name="where-do-i-manage-subscriptions-if-my-organization-has-been-onboarded-but-hasnt-been-migrated"></a>Kuruluşum edildi olmuştur, ancak geçirilen kurmadı abonelikleri nereden yönetirim?
Visual Studio, kuruluşunuzun geçirilmiş olan ve yeni Portalı'nda yönetilmeye hazırdır abonelikleri e-posta almak kadar VLSC aboneliği yönetmeye devam eder.

### <a name="where-can-i-locate-my-organizations-public-customer-number-pcn-or-authorization-number"></a>Burada ı kuruluşumun genel müşteri numarası (PCN) veya Yetkilendirme numarası bulabilir?
Oturum [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) ve aşağıdaki yola gidin: **abonelikleri** > **Visual Studio abonelikleri**. PCN altında bulunan **sözleşmesi/genel müşteri numarası sonuçları**. Bu konuda, PCN bulma hakkında adım adım yönergeleri almak [Yardım makalesinin](find-pcn.md).

### <a name="how-do-i-find-out-who-my-primary-or-notices-contact-is"></a>My birincil ya da bildirimler kişi kim olduğunu nasıl bulabilirim?
Oturum [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) ve aşağıdaki yola gidin: **lisansları > ilişki Özet** seçin, **lisans kimliği > kişiler**. Birincil ya da bildirimler kişi bu bulma konusunda adım adım yönergeler alın [Yardım makalesinin](find-primary-contact.md).

### <a name="what-if-my-primary-or-notices-contact-is-gone-no-longer-with-the-company-or-not-available-to-complete-onboarding"></a>Ne my birincil ya da bildirimler kişi, şirket ile artık veya tamamlamak için kullanılabilir gitti?
Etmeniz [desteğine başvurun](https://visualstudio.microsoft.com/subscriptions/support/#talktous) ve VLSC Aboneliklerini yönetmek için kullanılan e-posta sağlayın. Doğruladıktan sonra desteği ekleme işleminde size yardımcı erişemezsiniz.

### <a name="what-will-happen-with-renewing-customers"></a>Müşteriler yenileme ile ne?
Müşteriler yenilemek için yenileme aboneliği her zamanki gibi devam etmesi gerektiğini, yenileme işlemleri geçişten etkilenmez.

### <a name="should-my-organization-wait-to-set-up-a-new-agreement-in-the-new-system-rather-than-renew-an-existing-agreement"></a>Kuruluşumun yerine yeni sisteminde yeni bir anlaşma ayarlamak varolan sözleşme yenilemek için beklemesi gereken?
Hayır.  Geçiş oluşturma veya yenileme anlaşmaların etkilemez.

### <a name="what-if-my-organizations-agreement-is-in-the-grace-period-during-the-transition-will-they-also-be-migrated"></a>Ne kuruluşumun sözleşmesi geçiş sırasında yetkisiz kullanım süresi içinde olur? Bunlar ayrıca geçirilecek?
Evet, anlaşmayı etkin durumdaysa, kuruluşunuzun geçirilecektir.

### <a name="what-if-my-organization-has-over-claimed-in-the-current-system-will-we-still-be-migrated-to-the-new-system"></a>Ne Kuruluşum üzerinde geçerli sistemde istemiş olabilir? Biz yine yeni sisteme geçirilecek?
Evet, kuruluşunuzun hala yeni sisteme geçirilecektir. (Bu, olanak anlaşması türleri için) üzerinde talep olanağı yeni sistemde mevcut.

### <a name="what-if-my-organization-has-more-than-one-subscription-assigned-to-a-single-useremail-address"></a>Ne kuruluşumun bir tek kullanıcı/e-posta adresi atanmış birden fazla abonelik var?
Kuruluşunuz hala geçirilecektir.  Ancak, aynı düzeydeki herhangi bir ek aboneliği atamak mümkün olmaz (IE: Professional, Enterprise, vb.), kullanıcı/e-posta adresi. Geçiş sırasında aynı e-posta adresine sahip herhangi bir aboneliğiniz aynı düzeydeki hala görünür olacaktır, ancak yöneticilerinin e-posta adresleri benzersiz şekilde değiştirmeniz gerekir. Tek kullanıcı/e-posta adresi yeni Portalı'nda birden çok abonelik aynı düzeydeki atamak mümkün olmaz.

### <a name="where-can-i-find-the-most-up-to-date-information-about-the-migration"></a>Geçiş hakkında en güncel bilgileri nereden bulabilirim?
Bu geçiş ilgili tarih bilgisi kadar çoğu için lütfen bizim Visual Studio abonelikleri yönetici adresini ziyaret edin [Web sayfası](https://aka.ms/vs-admin). Destek gerekiyorsa, Visual Studio abonelikleri kontrol edin [destek sayfası](http://visualstudio.microsoft.com/subscriptions/support/#!collections/962-subscriptions), kendi kendine yardım içeren bilgi ve Destek iletişim bilgileri. Sonraki birkaç ay biz yönetici Web sayfasında ve kolayca ortaya bu geçiş yardımcı olmak için e-posta yoluyla güncelleştirmeleri sağlamaya devam edecek.

## <a name="resources-and-support-information"></a>Kaynaklar ve destek bilgileri
- [Yönetici Web sayfası](https://visualstudio.microsoft.com/subscriptions-administration/)

- Visual Studio abonelikleri ve Yönetim [desteği](https://visualstudio.microsoft.com/subscriptions/support/)

- [My PCN bulma](find-pcn.md)

- [My birincil ya da bildirimler kişi bulma](find-primary-contact.md)

- [Video](https://www.youtube.com/watch?v=ZmnywYGSFMg&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=1&t=0s) eklenmesi için kuruluş ve yöneten yöneticiler
