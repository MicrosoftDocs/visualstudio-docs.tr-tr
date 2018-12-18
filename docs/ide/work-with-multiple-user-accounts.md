---
title: Birden çok kullanıcı hesabıyla çalışma
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e623734cbe2aedee962e9f1b139ac1d50d473072
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348238"
---
# <a name="work-with-multiple-user-accounts"></a>Birden çok kullanıcı hesabıyla çalışma

Birden çok Microsoft hesabına ve/veya iş veya Okul hesapları varsa, böylece herhangi bir hesabı kaynakları için ayrı ayrı oturum açmanız gerek kalmadan erişebilir bunları tüm Visual Studio için ekleyebilirsiniz. Azure, Application Insights, Azure DevOps ve Office 365 Hizmetleri tüm kolaylaştırılmış oturum açma deneyimini destekler.

Bir makine üzerinde birden çok hesap ekledikten sonra başka bir makinede Visual Studio'ya oturum açarsanız, sizinle hesapları Dolaşımda kümesi.

> [!NOTE]
> Hesap adlarını Dolaşımda olsa da, kimlik bilgileri yoktur. Kimlik bilgileri diğer hesaplar için yeni bir makineye kaynaklarını kullanma girişimi ilk kez girmeniz istenir.

Bu makalede, Visual Studio için birden çok hesap ekleyin işlemini göstermektedir. Ayrıca, bu hesapları yerde erişilebilir kaynakları gibi görmek nasıl gösterir **bağlı hizmet Ekle** iletişim kutusunda **Sunucu Gezgini**, ve **Takım Gezgini**.

## <a name="sign-in-to-visual-studio"></a>Visual Studio’da oturum açma

Visual Studio'ya bir Microsoft hesabı veya kuruluş hesabı ile oturum açın. Kullanıcı adınızı, şuna benzer şekilde penceresinin üst köşesinde görünür görmeniz gerekir:

![Oturum açmış kullanıcı](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Sunucu Gezgini'nde Azure hesabınıza erişin

Tuşuna **Ctrl**+**Alt**+**S** açmak için **Sunucu Gezgini**. Genişletin **Azure** düğüm ve Visual Studio'ya oturum açmak için kullandığınız hesapla ilişkili Azure hesabındaki kullanılabilir kaynakları içerdiğine dikkat edin. Aşağıdaki görüntüye benzer:

![Sunucu Gezgini ile genişletilmiş Azure düğümü](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

İlk kez belirli bir cihazda Visual Studio kullandığınızda iletişim kutusu yalnızca, oturum açtığınız hesabı altında kayıtlı abonelikleri de gösterir. Herhangi diğer hesaplarınız doğrudan kaynaklara erişebilir **Sunucu Gezgini** sağ tıklayarak **Azure** düğümünü seçme **yönetin ve filtre abonelikleri**ve ardından hesap Seçici denetim hesaplarınızı ekleme. Ardından, isterseniz aşağı oka tıklayıp hesapları listesinden seçim başka bir hesap seçebilirsiniz. Bir hesap seçtikten sonra abonelikleri görüntülemek için söz konusu hesap altında özelleştirebilirsiniz **Sunucu Gezgini**.

![Azure abonelikleri iletişim yönetme](../ide/media/vs2015_manage_subs.png)

Bir sonraki açışınızda **Sunucu Gezgini**, kaynaklar söz konusu abonelik için görüntülenir.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Bağlı hizmet Ekle iletişim kutusu aracılığıyla Azure hesabınıza erişin

1. Varolan bir projeyi açın veya yeni bir proje oluşturun.

1. İçinde proje düğümünü seçin **Çözüm Gezgini**, sağ tıklayın ve ardından seçin **Ekle** > **bağlı hizmet**.

   **Bağlı hizmet Ekle** Sihirbazı görünür ve Visual Studio kişiselleştirme hesabınızla ilişkili Azure hesabındaki hizmetlerin listesini gösterir. Azure için ayrı ayrı oturum açmanız gerekmez. Ancak, diğer hesapları için farklı bir makineden kullanıcıların kaynaklara erişmeye ilk kez oturum açmanız gerekir.

### <a name="access-azure-active-directory-in-a-web-project"></a>Web projesinde erişimi Azure Active Directory

Azure Active Directory (AAD) son kullanıcı çoklu oturum açma web apps'te ASP.NET MVC veya web API hizmetlerindeki AD kimlik doğrulaması için destek sağlar. Etki alanı kimlik doğrulaması, kullanıcı hesabı kimlik doğrulamasını farklıdır. Active Directory etki alanınıza erişimi olan kullanıcılar, web uygulamalarınıza bağlanmak için mevcut bir AAD hesaplarını kullanabilirsiniz. Office 365 uygulamaları, etki alanı kimlik doğrulaması olarak da kullanabilirsiniz.

Bu uygulamada görmek için bir web uygulaması oluşturma (**dosya** > **yeni proje** > **C#** > **bulut**  >  **ASP.NET Web uygulaması**). İçinde **yeni ASP.NET projesi** iletişim kutusunda seçin **kimlik doğrulamayı Değiştir**. Kimlik doğrulaması Sihirbazı görünür ve uygulamanızda kullanılacak kimlik doğrulaması türünü seçmenize olanak tanır.

![ASP.NET kimlik doğrulaması iletişim kutusu değişimi](../ide/media/vs2015_change_authentication.png)

ASP.NET kimlik doğrulaması farklı türleri hakkında daha fazla bilgi için bkz. [oluşturma ASP.NET web projeleri Visual Studio'da](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods).

### <a name="access-your-azure-devops-organization"></a>Azure DevOps kuruluşunuza erişmesini

Ana menüden **takım** > **bağlantıları Yönet** açmak için **Takım Gezgini - Bağlan** penceresi. Seçin **bağlantıları yönetme** > **projeye bağlanmanız**. İçinde **projeye bağlan** iletişim kutusunda, bir proje listeden seçin (veya **TFS Sunucusu Ekle** sunucunuza URL'sini girin). Bir URL seçin, kimlik bilgilerinizi girmek zorunda kalmadan oturum açtınız.

Daha fazla bilgi için [projelerine Takım Gezgini bağlanma](connect-team-project.md).

## <a name="add-an-additional-account-to-visual-studio"></a>Visual Studio'ya ek bir hesap ekleyin

Visual Studio için ek bir hesap eklemek için:

1. Seçin **dosya** > **hesap ayarları**.

1. Altında **tüm hesapları**, seçin **Hesap Ekle**.

1. Üzerinde **hesabınızda oturum** sayfasında, kullanılacak hesabı seçin ya da seçin **başka bir hesap kullan**. Yeni hesap kimlik bilgilerini girmek için istemleri izleyin.

(İsteğe bağlı) Şimdi giderek **Sunucu Gezgini** ve yeni eklediğiniz hesapla ilişkili Azure Hizmetleri görebilirsiniz. İçinde **Sunucu Gezgini**, sağ **Azure** düğüm ve **yönetin ve filtre abonelikleri**. Geçerli hesap yanındaki açılır oka tıklayarak yeni bir hesap seçin ve ardından görüntülemek istediğiniz abonelikleri **Sunucu Gezgini**. Belirtilen aboneliği ile ilişkili tüm hizmetlerini görmelisiniz. Şu anda ikinci hesabıyla Visual Studio'ya oturum açmadıysanız olsa bile, bu hesabın hizmetlerine ve kaynaklarına oturum açtınız. Aynı true **proje** > **bağlı hizmet Ekle** ve **takım** > **Team Foundation ServerBağlan**.

### <a name="add-an-account-using-device-code-flow"></a>Cihaz kod akışını kullanarak Hesap Ekle

Bazı durumlarda, oturum açın veya normal bir şekilde bir hesap ekleyin. Bu, Internet Explorer için herhangi bir nedenle engellenirse veya ağınıza bir güvenlik duvarının arkasında olduğunda ortaya çıkabilir. Bu sorunu çözmek için etkinleştirebilirsiniz *cihaz kod akışını* bir hesap ekleyin veya hesabınız yeniden kimlik doğrulamaya zorlayabilir. Cihaz kod akışını sağlar, farklı bir tarayıcı kullanarak veya farklı bir makinede oturum&mdash;fiziksel veya sanal (VM).

Cihaz kod akışını kullanarak oturum açmanız:

1. Açık [ **hesapları** ](reference/accounts-environment-options-dialog-box.md) altındaki **Araçları** > **seçenekleri** > **ortamı**ve ardından **eklerken veya bir hesap yeniden kimlik doğrulaması cihaz kod akışı etkinleştir**. Seçin **Tamam** seçenekler sayfaları kapatın.

1. Seçin **dosya** > **hesap ayarları** hesabı Yönetim sayfasını açın.

1. Seçin **Hesap Ekle** altında **tüm hesapları**.

   Bir iletişim kutusu, bir URL ve kodu bir web tarayıcısına yapıştırın gösterir.

   ![Cihaz kod akış URL'si ve kod](media/work-with-multiple-user-accounts/device-login-code.png)

1. Tuşuna **Ctrl**+**C** iletişim kutusundaki metni kopyalayın ve ardından **Tamam** iletişim kutusunu kapatmak için. Not Defteri gibi bir metin düzenleyicisine kopyalanan metni yapıştırın. Bu, sonraki adımda kodu kopyalamak kolaylaştırır.

1. Visual Studio'da oturum açın ve ardından yapıştırın veya ifadesini içeren kutuya kopyaladığınız kodunu girmeniz için kullanmak istediğiniz makine veya web tarayıcısında cihaz oturum açma URL'sine gidin **kod**.

   **Visual Studio** uygulama adı sayfanın daha aşağı görünür.

1. Altında **Visual Studio**, seçin **devam**.

   ![cihaz oturum açma page.png](media/work-with-multiple-user-accounts/device-login-page.png)

1. Hesap kimlik bilgilerinizi girmek için istemleri izleyin.

   Cihazınızda Visual Studio'da oturum açıldıktan ve tarayıcı penceresini kapatabilirsiniz belirten bir sayfa görüntülenir.

   ![Visual Studio'da oturum açın tarayıcıdan tamamlandı](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Visual Studio hesabı Yönetim sayfasına geri dönün ve yeni eklenen hesabın altında listelenen göreceğiniz **tüm hesapları**. Seçin **Kapat**.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da oturum açma](signing-in-to-visual-studio.md)
- [Oturum açmak için Visual Studio Mac için](/visualstudio/mac/signing-in)
