---
title: Birden çok kullanıcı hesabıyla çalışma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b73c865c-74e0-420e-89cc-43524f4aafd0
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93f029a067e5a45930c2ac827862c1807e32aff8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176273"
---
# <a name="work-with-multiple-user-accounts"></a>Birden çok kullanıcı hesabıyla çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birden çok Microsoft hesabına ve/veya iş veya Okul hesapları varsa, böylece herhangi bir hesabı kaynakları için ayrı ayrı oturum açmanız gerek kalmadan erişebilir bunları tüm Visual Studio için ekleyebilirsiniz. Visual Studio 2015 RTM tarih itibarıyla Azure, Application Insights, Team Foundation Server ve Office 365 Hizmetleri kolaylaştırılmış oturum açma deneyimini destekler. Zaman geçtikçe ek hizmetler kullanılabilir duruma gelebilir.  
  
 Başka bir makinede Visual Studio'ya oturum açarsanız bir makine üzerinde birden çok hesap ekledikten sonra bu hesapları kümesi sizinle birlikte dolaşır. Hesap adlarını Dolaşımda olsa da, kimlik bilgileri sağlamadığı, dikkat edin önemlidir. Bu nedenle, ilk kez yeni makineye kaynaklarını kullanma girişimi diğer hesaplar için kimlik bilgilerini girin istenir.  
  
 Bu izlenecek yol, Visual Studio için birden fazla hesap ekleme işlemi açıklanır ve bu hesaplardan erişilebilir kaynakları yansıtılır nasıl yerleştirir gibi **bağlı hizmet Ekle** iletişim kutusunda **Sunucu Gezgini** , ve **Takım Gezgini**.  
  
#### <a name="sign-in-to-visual-studio"></a>Visual Studio’da oturum açma  
  
1.  Visual Studio 2015, bir Microsoft hesabı veya kuruluş hesabı ile oturum açın. Kullanıcı adınızı benzer penceresi sağ alt köşesindeki yansıtılan görmeniz gerekir:  
  
     ![Currentlly oturum açmış kullanıcı olarak](../ide/media/vs2015-username.png "VS2015_UserName")  
  
### <a name="access-your-azure-account-in-server-explorer"></a>Sunucu Gezgini'nde Azure hesabınıza erişin  
 Tuşuna **Ctrl + Alt + S** açmak için **Sunucu Gezgini**. Öğesini Azure simgesini, genişletirken, Visual Studio 2015 için oturum açma kimliği ile ilişkili Azure hesabındaki kullanılabilir kaynakları görmeniz gerekir. Kendi kaynaklarını değil Bay Tülin 's gördüğünüz dışında bunun gibi görünmelidir:  
  
 ![Sunucu Gezgini gösteren Azure Araçları düğümün genişletilmiş](../ide/media/vs2015-serverexplorer.png "VS2015_ServerExplorer")  
  
 İlk kez belirli bir cihazda Visual Studio kullandığınızda iletişim kutusu yalnızca IDE ile oturum açtığı kimliği altında kayıtlı abonelikleri gösterir. Herhangi diğer hesaplarınız doğrudan kaynaklara erişebilir **Sunucu Gezgini** Azure düğümüne sağ tıklayıp seçme **yönetin ve filtre abonelikleri** ve kendi hesaplarını ekleme Hesap Seçici denetimini. Ardından, isterseniz aşağı oka tıklayıp hesapları listesinden seçim başka bir hesap seçebilirsiniz. Bir hesap seçtikten sonra o hesapla sunucu Gezgini'nde görüntülemek istediğiniz abonelikleri seçebilirsiniz.  
  
 ![Azure abonelikleri iletişim yönetme](../ide/media/vs2015-manage-subs.png "vs2015_manage_subs")  
  
 Sunucu Gezgini, bir sonraki açışınızda, kaynaklar için aboneliklerinizi görüntülenir.  
  
### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Bağlı hizmet Ekle iletişim kutusu aracılığıyla Azure hesabınıza erişin  
  
1.  C# dilinde bir evrensel uygulama projesi oluşturun.  
  
2.  Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve seçin **Ekle > bağlı hizmet**. Bağlı Sihirbazı görünür ve gösterir Hizmet Ekle, Visual Studio oturum açma ile ilişkili Azure hesabındaki hizmetlerin listesi kimliği Azure için ayrı ayrı oturum açmanız gerekmez unutmayın. Ancak, diğer hesapları için belirli bir bilgisayardan kullanıcıların kaynaklara erişmeye ilk kez oturum açmanız gerekir.  
  
    > [!WARNING]
    >  Bu ilk kez kullanıyorsanız, belirli bir bilgisayarda Visual Studio 2015'te bir Store uygulaması oluşturuyorsanız, Cihazınızı geliştirme modu için ekranına giderek etkinleştirirsiniz istenir **ayarları &#124; . Güncelleştirmeler ve güvenlik &#124; geliştiriciler için** bilgisayarınızda. Daha fazla bilgi için [Cihazınızı geliştirme için etkinleştirme](https://msdn.microsoft.com/library/windows/apps/dn706236.aspx).  
  
###  <a name="access_azure"></a> Web projesinde erişimi Azure Active Directory  
 Azure AD, son kullanıcı çoklu oturum açma ASP.NET MVC web uygulamaları veya Web API hizmetlerindeki AD kimlik doğrulaması için destek sağlar. Etki alanı kimlik doğrulaması, kullanıcı hesabı kimlik doğrulamasını farklıdır; Active Directory etki alanınıza erişimi olan kullanıcılar, mevcut Azure AD hesaplarına web uygulamalarınıza bağlanmak için kullanabilirsiniz. Office 365 uygulamaları, etki alanı kimlik doğrulaması olarak da kullanabilirsiniz. Bu uygulamada görmek için bir web uygulaması oluşturma (**Dosya > Yeni Proje > C# > bulut > ASP.NET Web uygulaması**). Yeni ASP.NET projesi iletişim kutusunda seçin **kimlik doğrulamayı Değiştir**. Kimlik doğrulaması Sihirbazı görünür ve uygulamanızda kullanılacak kimlik doğrulaması türünü seçmenize olanak tanır.  
  
 ![ASP.NET kimlik doğrulaması iletişim kutusu değişimi](../ide/media/vs2015-change-authentication.png "VS2015_change_authentication")  
  
 ASP.NET kimlik doğrulaması farklı türleri hakkında daha fazla bilgi için bkz. [Visual Studio 2013'te ASP.NET Web projeleri oluşturma](http://www.asp.net/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (kimlik doğrulaması hakkında bilgi için Visual Studio 2015 hala geçerlidir).  
  
### <a name="access-your-visual-studio-team-services-account"></a>Visual Studio Team Services hesabınıza erişme  
 Ana menüden **takım > Team Foundation Server'a Bağlan** ortaya çıkarmak için **Takım Gezgini** penceresi. Tıklayarak **takım projeleri seçin**ve ardından liste kutusu altında **Team Foundation Server'ı seçin**, Visual Studio Team Services hesabınız için URL görmeniz gerekir. URL seçtiğinizde, kimlik bilgilerinizi yeniden girmek zorunda kalmadan oturumunuz açılır.  
  
## <a name="add-a-second-user-account-to-visual-studio"></a>Visual Studio için ikinci bir kullanıcı hesabı Ekle  
 Visual Studio sağ üst köşesindeki kullanıcı adınızın yanındaki aşağı oka tıklayın. Ardından **hesap ayarları** menü öğesi. **Hesap Yöneticisi** iletişim kutusu açılır ve oturum açmada görüntüler. Tıklayın **Hesap Ekle** yeni bir Microsoft hesabı veya yeni bir iş veya Okul hesabınızı eklemek için iletişim kutusunun sol alt köşesindeki bağlantı.  
  
 ![Visual Studio hesabı Seçici](../ide/media/vs2015-acct-picker.png "VS2015_acct_picker")  
  
 Yeni hesap kimlik bilgilerini girmek için istemleri izleyin. Bir kullanıcı Contoso.com iş hesabını ekledikten sonra Hesap Yöneticisi aşağıda gösterilmiştir.  
  
 ![Hesap Yöneticisi](../ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")  
  
## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Sunucu Gezgini ve bağlı hizmetler Ekleme Sihirbazı'nı yeniden ziyaret  
 Artık Git **Sunucu Gezgini** tekrar Azure düğümüne sağ tıklayın ve seçin **yönetin ve filtre abonelikleri**. Yeni hesap açılan geçerli hesap yanındaki oka tıklayarak seçin ve ardından sunucu Gezgini'nde görüntülemek istediğiniz abonelikleri seçin. Belirtilen aboneliği ile ilişkili tüm hizmetlerini görmelisiniz. Şu anda Visual Studio IDE ikinci hesabı ile oturum olsa bile, bu hesabın hizmetlerine ve kaynaklarına oturum açtınız. Aynı true **Proje > bağlı hizmet Ekle** ve **takım > Team Foundation Server'a Bağlan**.



