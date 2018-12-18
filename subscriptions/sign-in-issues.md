---
title: Visual Studio abonelikleri için oturum açma sorunları | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 11/07/2018
ms.topic: conceptual
description: Visual Studio abonelikleri için oturum açarken çıkabilecek sorunlar hakkında bilgi edinin
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 0883e5228a44f0df80e9de912029e21545d5ec2a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810578"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Visual Studio abonelikleri için oturum açma sorunları
Visual Studio aboneliğinizi kullanmak için önce oturum açmanız gerekir.  Aboneliğinize bağlı olarak, bir Microsoft hesabı (MSA) veya bir Azure Active Directory (AAD) kimlik ile ayarlamış olduğunuz.  Bu makalede, aboneliğiniz için oturum açma sırasında karşılaşabileceğiniz sorunları bazıları açıklanmaktadır.  

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Microsoft hesapları (MSA) iş/Okul e-posta adreslerini kullanarak oluşturulamaz.

Azure AD'de e-posta etki alanı yapılandırılırken bir yeni kişisel Microsoft hesabı (iş/Okul e-posta adresini kullanarak MSA) oluşturma olanağı artık izin verilmez. Bu ne demektir? Kuruluşunuz Office 365 veya Azure AD kullanan diğer Microsoft hizmetlerini kullanıyorsa ve Azure AD kiracınız için bir etki alanı adı eklediyseniz, kullanıcılar artık e-posta adresi etki alanınızda kullanarak yeni bir kişisel Microsoft hesabı oluşturmak mümkün olacaktır. 

### <a name="why-was-this-change-made"></a>Neden bu değişiklik yapılmıştır?

Kişisel sahip bir kullanıcı adı olarak bir iş adresi Microsoft Account son kullanıcılar ve BT departmanlarının benzer sorunlarla kaybolduğu istenir. Örneğin: 
- Kullanıcılar kendi kişisel Microsoft hesabı iş uyumlu olduğunu ve kendi OneDrive iş belge kaydettiğinizde, uyumlu olduğunuzu düşünebilirsiniz. 
- Genellikle kuruluştan Ayrıl kullanıcıların iş e-posta adreslerini erişimini kaybeder. Bunu yaptıklarında, kullanıcılar parolalarını unuturlarsa kişisel Microsoft hesaplarına geri mümkün olmayabilir. Bu madalyonun, BT departmanı ve kullanıcının parolasını sıfırlamasını eski çalışanların kişisel dikkate almak olmasıdır. 
- BT departmanları, hesap sahibini ve güvenlik yanlış bir fikir edindiniz. Ancak kullanıcıların yalnızca iş e-posta bir kod kez adres ve kendi hesabını gelecekte dilediğiniz zaman yeniden adlandırabilirsiniz gidiş dönüş gerekir. 

Özellikle (bir Azure AD'de & da bir Microsoft hesabı) aynı e-posta adresine sahip iki hesap olmayan kullanıcılar için kafa karıştırıcı bir durumdur. 

### <a name="what-does-this-experience-look-like"></a>Bu deneyim ne gibi görünüyor?

Bir Microsoft tüketici uygulama bir iş için kaydolun veya Okul e-posta adresinizi kullanmayı denerseniz, aşağıdaki iletiyi görürsünüz. 

   > [!div class="mx-imgBorder"]
   > ![İş e-posta ile bir hesap oluşturulamıyor](_img/sign-in-issues/cannot-use-work-email.png)

Ancak, kişisel ve iş/Okul hesaplarını destekleyen bir Microsoft uygulaması için kaydolmak denerseniz bu iletiyi görmeniz gerekir:

   > [!div class="mx-imgBorder"]
   > ![Desteklenen iş/Okul hesapları](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>Var olan hesap etkilenir?
Burada açıklanan kayıt blok yalnızca yeni hesaplar oluşturulmasını engeller. Zaten bir iş/Okul e-posta adresiyle bir Microsoft Account sahip kullanıcılar üzerinde hiçbir etkisi olmaz. Bu durumda zaten varsa, kişisel bir Microsoft hesabı yeniden adlandırmak kolaylaştırarak yaptık. Bu [destek makalesi](http://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) basit adım adım rehberlik sunar. Kişisel Microsoft hesabınızı yeniden adlandırma, kullanıcı adı değiştirme anlamına gelir ve iş e-posta veya Office 365 gibi iş Hizmetleri için oturum açma etkilemez. Kişisel bilgilerinizi etkilemez; yalnızca bir oturum için şeklini değiştirir. Başka bir (Kişisel) e-posta adresi kullanın, yeni bir alma @outlook.com e-posta adresi Microsoft veya yeni bir kullanıcı adı olarak telefon numaranızı kullanın. 

> [!NOTE]
> BT departmanınız, iş/Okul e-posta ile kişisel bir Microsoft hesabı oluşturmak için istenirse, örneğin Microsoft erişmek iş Hizmetleri Premier Destek ister ve ardından yönetim ekibi, hesabınızı yeniden adlandırmadan önce konuşun. 

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Bir oturum açma adresi silme için abonelik erişimini engelleyebilir

Aboneliğinizle ilişkili bir veya daha fazla kimlik (MSA veya AAD) silmeniz halinde, kullanıcı adını ve oturum açma kimliği gibi abonelik bilgilerinizi anonim erişim kaybına aboneliğinize kaynaklanan çizilebilir. 

Abonelik erişiminizi yönelik etkileri önlemek için aşağıdaki tekniklerden birini kullanın.  
- Bir tek bir kimlik yönetimi sistemi--MSA veya AAD--ancak ikisini birden dağıtın.  
- AAD ile MSA kimliklerini Kiracı ile ilişkilendirirsiniz. 


## <a name="next-steps"></a>Sonraki adımlar
- Bilgi edinmek için nasıl [bağlantı MSA ve AAD hesaplarının](/azure/active-directory/b2b/add-users-administrator) AAD içinde.
- Daha fazla bilgi edinin [anonimleştirme](anonymization.md). 
