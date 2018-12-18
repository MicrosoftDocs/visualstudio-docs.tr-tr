---
title: Visual Studio abonelikleri için oturum açma başarısız olabilir diğer adlar kullanırken | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/02/2018
ms.topic: Get-Started-Article
description: Diğer ad veya kolay adlar kullanılması durumunda oturum açma başarısız olabilir
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 3743cc11d5001d12ba4cd030ddc0cfc914db3131
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817444"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Visual Studio abonelikleri için oturum açarken diğer adlar kullanırken başarısız olabilir

Oturum açmak için kullanılan hesap türüne bağlı olarak, mevcut abonelikler düzgün açarken görüntülenmeyebilir [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Olası bir nedeni "diğer" veya "kolay adlar" abonelik atandığı oturum açma yerine kimliktir. Bu, "diğer ad kullanımı" olarak adlandırılır.

## <a name="what-is-aliasing"></a>Diğer ad kullanımı nedir?

"Diğer ad kullanımı" terimi farklı kimliklere sahip olmasını, kullanıcıların Windows (veya Active Directory'nizde) oturum açmak ve e-postaya erişmeye ifade eder.

Diğer ad kullanımı ile bir şirket Microsoft çevrimiçi hizmeti için kendi directory oturum açma gibi olduğunda karşılaşılabilir JohnD@contoso.com, ancak kullanıcılar diğer adları veya kolay adlar gibi kullanarak e-posta hesaplarına erişim John.Doe@contoso.com. Kendi aboneliklerini Toplu Lisanslama hizmeti Merkezi (VLSC) aracılığıyla yöneten birçok müşteri için bu bir başarısız oturum açma deneyimine e-posta adresi olarak sağlanan neden olabilir (John.Doe@contoso.com) ile dizin adresinin eşleşmiyor (JohnD@contoso.com) "İş veya Okul hesabı" seçeneği aracılığıyla başarılı kimlik doğrulaması için gereklidir.

## <a name="as-an-administrator-what-options-do-i-have"></a>Yönetici olarak, hangi seçenekleri zorundayım?

Yönetici olarak, abonelerinize sahip başarılı bir oturum açma deneyimi sağlamak için iki seçenek vardır [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
- İlk seçenek (önerilir), Toplu Lisanslama hizmeti Merkezi (VLSC) olarak atanan adresi olarak dizin hesabı yararlanmasına gelir. Başvurmak [bir dizin hesabı atama abonelere](#assigning-subscribers-to-a-directory-account) daha fazla ayrıntı için bu makaledeki bir bölüm.
- (Daha az güvenlidir), ikinci seçenek olur (yani), "Kişisel" hesap "İş veya Okul" e-posta adresine ilişkilendirilecek abonelerinize izin vermek için Microsoft hesabı veya MSA). Başvurmak [kişisel bir hesap bir iş veya Okul hesabı tanımlama ](#defining-a-work-or-school-account-as-a-personal-account ) daha fazla ayrıntı için bu makaledeki bir bölüm.

> [!NOTE]
> Yeni Visual Studio abonelikleri için şirketinizin geçirildikten sonra [Yönetim Portalı](https://manage.visualstudio.com), bir parçası olarak sağlanacak hem dizin ve e-posta adreslerini sağlayan yeni bir yönetim deneyimi yararlanmak mümkün olacaktır abonenin profili. Daha fazla bilgi edinin [geçiş](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="as-a-subscriber-what-options-do-i-have"></a>Abone olarak, hangi seçenekleri zorundayım?

Abone açısından bakıldığında, ilk iş yöneticinize, şirketinizin kimlik yapılandırması anlamak için önemlidir. Gerekirse, Yönetici hesap ayarlarınızı, Yönetim Portalı'ndan güncelleştirmeniz gerekebilir veya şirket e-posta adresinizi kullanarak bir Microsoft hesabı (MSA) oluşturmanız gerekebilir. Bir MSA oluşturmak için adımları gerçekleştirmeden önce tüm ilkeleri veya bu eylemi gerçekleştirmeden sorunları ile ilgili yöneticinizle konuşun. Başvurmak [kişisel bir hesap bir iş veya Okul hesabı tanımlama](#defining-a-work-or-school-account-as-a-personal-account) daha fazla ayrıntı için bu makaledeki bir bölüm.

## <a name="assigning-subscribers-to-a-directory-account"></a>Bir dizin hesabına abonelerin atama

Tüm durumlarda, Toplu Lisanslama hizmeti Merkezi (VLSC) içinde Abonelik Yöneticisi ile dizin adresinin yeni aboneleri için kullanabilir veya "var" aboneler için e-posta adresini güncelleştirmek gerekir. Dizin adresinin kullanarak herhangi bir yeni aboneler Hoş Geldiniz e-posta almaz ve yönetici bildirmek için bir abonelik atanmış abone gerekecek anlamına gelir olduğunu unutmayın. Sonra aşağıdaki adımları, lütfen ayrıca e-posta araştırmalarında [şablon](#notifying-your-subscribers-with-directory-addresses) abonelerinize bildirmek ve oturum açma işleminde size yardımcı olmak için.

### <a name="adding-new-subscribers"></a>Yeni aboneler ekleme

Lütfen bir dizin hesabıyla yeni aboneleri eklemek için bu adımları izleyin.

1. Ziyaret [Toplu Lisanslama Hizmet Merkezi](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) ve oturum açın.
2. VLSC yönetici sayfasından tıklatın **abonelikleri** ardından **Visual Studio abonelikleri**.

    > [!div class="mx-imgBorder"]
    > ![Abonelik menü](_img//vlsc/vlsc-subscriptions.png)


3. Tıklayın **anlaşma numarası** Visual Studio aboneliği ile ilişkili.

    > [!div class="mx-imgBorder"]
    > ![Sözleşme seçin](_img/vlsc/vlsc-agreement.png)

4. Tıklayın **atama, aboneliğini**.
5. İstenen seçin **abonelik düzeyi**.
6. Doğrulama abonelikleri atamak ve kullanılabilir olan **sonraki**.
7. Abone ayrıntıları ve dizin adresinin e-posta adres alanına girin ve tıklayın **sonraki**.
8. Abone bilgisi doğrulamak ve tıklayın **son**.
9. Abone, aboneliğini kullanarak sağlandığını bildir aşağıda [şablon](#notifying-your-subscribers-with-directory-addresses).

### <a name="updating-an-existing-subscriber"></a>Mevcut bir abone güncelleştiriliyor

Lütfen mevcut bir abone directory hesabıyla güncelleştirmek için aşağıdaki adımları.

1. Ziyaret [Toplu Lisanslama Hizmet Merkezi](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) ve oturum açın.
2. VLSC Yöneticisi sayfalarından tıklayın **abonelikleri** ardından **Visual Studio abonelikleri**.
3. Tıklayın **anlaşma numarası** Visual Studio aboneliği ile ilişkili.
4. Tıklayın **aşağı ok** arama çubuğundaki.
5. "E-posta adresi" alanını kullanarak aboneyi arayın.
6. Sonuç listesinden tıklayın **Soyadı** abonenin.
7. 
              **Düzenle**‘ye tıklayın.
8. İstenen dizine adresine e-posta adresi alanından değiştirin ve **Kaydet**.
9. Abone, aboneliğini kullanarak sağlandığını bildirim e-posta şablonu aşağıda.

### <a name="notifying-your-subscribers-with-directory-addresses"></a>Abonelerinize directory adresleriyle bildirme

Hoş Geldiniz e-posta başarıyla abonenizi ulaşarak olduğundan, Lütfen kopyalama ve yapıştırma aşağıda iletiye bir e-posta ve abonenizi Gönder. Word'ün % her abone için uygun bilgi ile değiştirin.

---Kopyalama aşağıdaki (Ctrl + C)---

Hello % abone adı %

Visual Studio aboneliği atandı. Lütfen https://my.visualstudio.com, etkinleştirmek ve aboneliğinize erişmek için % dizin ADRESİNİN % adresinizi bilgilerinizle oturum açın.

Sorun yaşıyorsanız, lütfen Destek ekibine başvurun (https://visualstudio.microsoft.com/subscriptions/support/).

Sayfanın en altında aşağıdakileri seçin:
   - Hesapları, abonelikleri ve faturalandırma desteği
   - Sorunu, abonelik oturum desteği seçin.
   - İlgili ülke seçin
   - İstenen Yardımlı Destek seçeneğini belirleyin

---Son kopyalama---

## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Bir iş veya Okul hesabı kişisel bir hesap tanımlama

Lütfen bölümünde açıklanan yönergeleri yararlanarak [bir dizin hesabı atama abonelere](#assigning-subscribers-to-a-directory-account) yeni bir kullanıcı eklemek veya bir kullanıcının e-posta adresi Toplu Lisanslama hizmeti Merkezi (VLSC) içinde güncelleştirmek için bölüm.  Burada e-posta adresi directory tarafından tanınmıyor durumlarda, kullanıcının e-posta adresi bir kişisel hesap tanımlamak için yeni bir hesap oluşturma işlemi adım adım gerekir.  Kısa vadede için Visual Studio abonelikleri ekibi, aşağıda tanımlanan Kimlik İlkesi bir muafiyet güvenli var. ancak Biz bu ilkeyi kaldırmak gerekli özellikleri yatırım yapıyor.

> [!WARNING]
> Microsoft, "İş veya Okul" kimlik "Kişisel" kimliklerle birleştirme önermez.  Bu eylem kuruluş sahipliği ve denetimi hesabının kaybetmenize neden olur ve çalışan şirket ayrıldıktan sonra belirli bir ürün veya hizmetler erişmeye devam edebilirsiniz.  Lütfen bu başvuru [blog gönderisi](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/), ek bilgi için Microsoft Identity ekibinin.

### <a name="defining-an-email-address-as-a-personal-account"></a>Kişisel bir hesap bir e-posta adresi tanımlama

Aboneye abonelik atandıktan sonra bunları ziyaret etmek isteyen bir e-posta alırsınız [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs) , abonelik avantajlarının yararlanmak için.  Çalışırken oturum açma, Visual Studio aboneliği oturum açma bir hesap tanınmıyor belirten hata ile başarısız olur.  Önce oturum içinde [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs) deneyimi, aşağıdaki yönergeleri izleyin, abonenin isteyin.  Gerekirse, bunu kullanıp kullanamayacağını [şablon](#notifying-your-subscribers-using-personal-accounts) abonelik atandıktan sonra abone bildirir.

1. Gidin https://my.visualstudio.com, tıklatıp **yeni bir Microsoft hesabı oluşturun**.

2. Alanları doldurun:
   - Hoş Geldiniz e-postada alınan e-posta adresi girin Someone@example.com kutusu
   - Parola oluşturma
   - Promosyon ayarlarınızı seçin
   - **İleri**'ye tıklayın.

3. Doğrulama adımları tamamlayın ve tıklayın **sonraki**.

4. Yeni kullanıcılar, Visual Studio profili gerçekleştirmeniz gerekebilir.

5. Abonelik ve avantajları artık görünür olmalıdır.

### <a name="notifying-your-subscribers-using-personal-accounts"></a>Abonelerinize kişisel hesapları bildirme

Yukarıda özetlenen senaryo, abonenin "Hoş Geldiniz e" alırsınız, ancak diğer ad kullanımı nedeniyle oturum açamıyor oldukları oldukları fark edebilirsiniz.  Kullanabileceğiniz aşağıdaki abonenizi yukarıdaki adımların bildirim ve destek seçenekleri gerekirse önermek için metni.  Word'ün % her abone için uygun bilgi ile değiştirin.

---Kopyalama aşağıdaki (Ctrl + C)---

Hello % abone adı %

Visual Studio aboneliği atanmış olan ve oturum açmak için yönlendirilmiş https://my.visualstudio.com Hoş Geldiniz e-postalarınızı göre.  Bu avantajlar kullanma için doğru Web sitesi olsa da, kuruluşumuz site erişebilmeniz için önce bazı ek adımlar uygulaması gerekir.  Lütfen şu adımları izleyin, "Microsoft, müşterilerimizin şirket e-posta adresine bağlanan Account" oluşturmanıza yardımcı olacak yönergeler aşağıda.  Bu adımları tamamladıktan sonra aboneliğinizin avantajlarına erişmek için e-posta adresinizi kullanır.
1. Ziyaret edin https://my.visualstudio.com

2. Sağ taraftaki yeni Microsoft Account Oluştur'a tıklayın.

3. Formu doldurun:
   - Şirket e-posta adresinizi someone@example.com kutusu
   - Bir parola girin
   - Promosyon tercihlerinizi seçin
   - İleri'ye tıklayın

4. Hesap doğrulama adımları tamamlayın

5. Gerekirse, Visual Studio profilini tamamlayın

6. Avantajlarınızı hemen görmeniz gerekir

Not: ziyaret https://my.visualstudio.com gelecekte (örn. kullanmak istediğiniz hesabı seçin istenebilir "İş veya Okul hesabı" veya "Kişisel hesap").  Yukarıdaki adımları tamamladıktan sonra "Kişisel hesap" seçeneğini yararlanarak gerekecektir.

Sorun yaşıyorsanız, lütfen Destek ekibine başvurun (https://visualstudio.microsoft.com/subscriptions/support/).

Sayfanın en altında aşağıdakileri seçin:
   - Hesapları, abonelikleri ve faturalandırma desteği
   - Sorunu, abonelik oturum desteği seçin.
   - İlgili ülke seçin
   - İstenen Yardımlı Destek seçeneğini belirleyin

---Son kopyalama---
