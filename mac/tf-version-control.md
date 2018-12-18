---
title: Team Foundation sürüm denetimi (TFVC)
description: Team Foundation Server veya Team Foundation sürüm denetimi (TFVC) Azure DevOps hizmetleriyle bağlanıyor.
author: conceptdev
ms.author: crdun
ms.date: 09/05/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 9cb6a466d764c85012477fb2d849c05920908f02
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295936"
---
# <a name="connecting-to-team-foundation-version-control"></a>Team Foundation sürüm denetimine bağlama

> [!NOTE]
> Team Foundation sürüm denetimi desteği şu anda Önizleme aşamasındadır ve bazı işlevler henüz tam olarak çalışmıyor. Sizden geri bildirim herhangi bir sorun üzerinde isteriz [Geliştirici topluluğu](https://developercommunity.visualstudio.com/spaces/41/index.html). Daha fazla değişiklik hala gelen üzeresiniz!

Azure depoları, sürüm denetimi, iki modeli sağlar: dağıtılan Git sürüm denetimi ve Team Foundation sürüm denetimi (olan TFVC), merkezi sürüm denetimi. Mac için Visual Studio ile TFVC kullanmak için bu makalede bir genel bakış ve bir başlangıç noktası sağlar

## <a name="requirements"></a>Gereksinimler

* Visual Studio Community, Professional veya Enterprise Mac 7.5 veya sonraki bir sürümü için.
* Azure DevOps Services veya Team Foundation Server 2013 ve üzeri sürümler.
* Azure DevOps Services veya Team Foundation Server, Team Foundation sürüm denetimi kullanmak üzere yapılandırılmış bir proje.

## <a name="installation"></a>Yükleme

Mac için Visual Studio'da **Visual Studio > Uzantılar** menüsünde. İçinde **galeri** sekmesinde **sürüm denetimi > Team Foundation sürüm denetimi için TFS ve VSTS** tıklatıp **yükleme**:

![Uzantı Yöneticisi](media/tfvc-install.png)

Uzantıyı yüklemek için istemleri izleyin. Yüklendikten sonra IDE yeniden başlatın.

## <a name="updating-the-extension"></a>Uzantıyı güncelleştirirken

TFVC uzantı güncelleştirmeleri düzenli olarak gerçekleştirilir. Güncelleştirmeleri erişmek, seçin **Visual Studio > uzantılar...**  seçin ve menüden **güncelleştirmeleri** sekmesi. Uzantı listesi ve ENTER tuşuna seçin **güncelleştirme** düğmesi:

![Uzantı Yöneticisi'ni gösteren güncelleştirme](media/tfvc-update.png)

Tuşuna **yükleme** sonraki iletişim kutusunda eski paketi kaldırın ve yenisini yükleyin.

Her sürümdeki yenilikler hakkında daha fazla bilgi için bkz: [sürüm notları](/visualstudio/releasenotes/vs2017-mac-preview-relnotes#team-foundation-version-control-extension--release-notes).

## <a name="using-the-add-in"></a>Eklenti kullanma

Uzantıyı yükledikten sonra seçin **sürüm denetimi > TFS/Azure DevOps > Uzak depodan açık** menü öğesi.

![Uzantı açmak için menü öğesi](media/tfvc-source-control-explorer-devops.png)

VSTS veya Team Foundation Server kullanmaya başlayın ve basın seçin **devam**:

![Bir sunucuyla bağlanma](media/tfvc-choose-server-type-devops.png)

### <a name="azure-repos-authentication"></a>Azure depoları kimlik doğrulaması

Azure depoları üzerinde barındırılan bir proje seçtiğinizde, Microsoft hesabı ayrıntılarını girin istenir:

![Azure depoları ile bağlanma](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>TFS kimlik doğrulaması

TFS'ye bağlanmak için sunucu ayrıntıları ve hesap kimlik bilgilerinizi girin. Aksi takdirde temel kimlik doğrulaması kullanmak için boş bırakın, NTLM kimlik doğrulaması kullanmak için bir etki alanını girin. Seçin **sunucusu ekleme**:

![Bir TFS sunucusuna oturum açın](media/tfvc-login.png)

## <a name="selecting-a-project"></a>Bir proje seçme

Başarıyla kimlik doğrulaması yaptınız sonra hesabı ile ilişkili olan depolar listesini görebilirsiniz **kaynak denetiminden Aç** iletişim:

![Kaynak denetimi iletişim kutusunda görüntülenen projeleri ile Aç](media/tfvc-vsts-projects.png)

Bu iletişim kutusunda, aşağıdaki düğümleri düzenlenmiştir:

- Azure DevOps kuruluş veya koleksiyon – Bu, oturum açtığınız Microsoft hesabı bağlı tüm organizasyonlar görüntüler.
- Her Kuruluş ve koleksiyon - projeleri projelerinin sayısına sahip olabilir. Kaynak kodu, iş öğeleri ve otomatik yapılara barındırıldığı bir projedir.

Bu noktada, arama filtre ve bir proje veya kuruluş adına göre.

### <a name="adding-a-new-server"></a>Yeni bir sunucu ekleme

Listeye yeni bir sunucu eklemek için basın **konak Ekle** düğmesini **kaynak denetiminden Aç** iletişim:

![Vurgulanmış yeni sunucu listesine eklemek için düğme ekleme](media/tfvc-add-new-server.png)

Listeden sağlayıcıyı seçin ve kimlik bilgilerinizi girin:

![Kaynak denetimi sağlayıcısı için seçeneğini gösteren iletişim](media/tfvc-add-new-creds-devops.png)

## <a name="creating-a-new-workspace"></a>Yeni bir çalışma alanı oluşturma

Bir proje ile çalışmaya başlamak için ihtiyacınız bir _çalışma_. Bir çalışma alanı yoksa, bir oluşturabilirsiniz **çalışma** combobox içinde **kaynak denetiminden Aç** iletişim:

![Yeni çalışma alanı combobox seçenek oluştur](media/tfvc-create-new-workspace.png)

Yeni bir çalışma alanınız için yerel yolunu ve adını ayarlar ve **çalışma alanı oluştur**:

![Yeni çalışma alanı için bir ad ve yerel yol girme](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>Kaynak kod Gezgini kullanma

Bir çalışma alanı oluşturup projenizi eşlenen ile çalışmaya başlayabilir _kaynak kod Gezgini_.

Kaynak kod gezginini açmak için seçmeniz **sürüm denetimi > TFS/Azure DevOps > Kaynak Denetim Gezgini** menü öğesi.

Kaynak kod Gezgini eşlenen tüm projeler, dosyalar ve klasörler gitmenizi sağlar. Ayrıca gibi tüm temel kaynak denetim eylemleri gerçekleştirmenize olanak sağlar:

- En son sürümü Al
- Belirli Sürümü Al
- Dosyaları kullanıma alma ve iade etme
- Kilitleme ve dosyaları kilidini açma
- Ekleme, silme ve dosyaları yeniden adlandırma
- Geçmişi görüntüle
- Değişiklikleri Karşılaştır.

Bu eylemlerin çoğunu, projenin bağlam eylemleri aracılığıyla sunulur:

![Bir proje için bağlam menüsünü eylemleri](media/tfvc-sourcecode-actions.png)

## <a name="managing-workspaces"></a>Çalışma alanlarını yönetme

Açıklandığı zaten bir çalışma alanı oluşturmadıysanız, [çalışma alanı oluşturma](#creating-a-new-workspace) bölümünde seçeneğinde kaynak kod Gezgini boştur:

![boş bir kaynak kod Gezgini](media/tfvc-setup-empty-sce.png)

Uzak bir yerel çalışma alanı projenizle ayarlamak için aşağıdaki adımları kullanın:

1. Seçin **sunucu** Açılır kutudan.
1. Yerel yol "Eşlenmemiş" ise ve "çalışma alanı" olduğunu unutmayın. Seçin **eşlenmedi** görüntülemek için bağlantıyı **yeni çalışma alanı oluşturma** iletişim.
1. Çalışma alanı için bir ad belirtin ve ardından **çalışma klasörü Ekle** bilgisayarınızdaki bir yerel klasör proje eşlemek için:

    ![Varsayılan seçenekleri gösteren yeni bir çalışma alanı iletişim kutusu oluşturma](media/tfvc-workspace1.png)

1. Sunucunuzdaki tüm projeleri aynı çalışma alanına eşleme her bir proje seçin veya tıklayın "$" klasörü seçin **Tamam**:

    ![Tüm projeler gösteren klasör iletişim kutusu için Gözat](media/tfvc-workspace2.png)

1. Yerel makinenizde ve projeleri için harita tıklayın istediğiniz konumu seçin **Klasör Seç**.
1. Yeni çalışma alanı ayrıntılarını tuşlarına basarak onaylayın **Tamam**

    ![Eklenen çalışma klasörü ile yeni çalışma alanı iletişim kutusu oluşturma](media/tfvc-workspace3.png)

Çalışma alanınızı ayarladıktan sonra onu değiştirilebilir ya tıklayarak kaldırıldı **çalışma alanlarını yönet** düğmesi kaynak kod gezginindedir.

![Çalışma alanlarını yönetme](media/tfvc-workspace4.png)

## <a name="troubleshooting"></a>Sorun giderme

### <a name="problems-using-basic-authentication"></a>Temel kimlik doğrulaması kullanma ile ilgili sorunlar

Bir sunucunun kimliğini doğrulamak için aşağıdaki seçenekler kullanılabilir:

- OAuth
- Temel
- NTLM

Bunu etkinleştirmek için gereken temel kimlik doğrulaması kullanacak şekilde **alternatif kimlik doğrulama bilgilerini** aşağıdaki adımları izleyerek Azure DevOps Hizmetleri:

1. Azure DevOps kuruluşunuza sahibi olarak oturum açın (https://dev.azure.com/{organization}/{project}).

2. Kuruluş, araç çubuğunda, dişli simgesini seçin ve seçin **ilke**:

    ![Seçili İlkesi ayarları seçeneği](media/tfvc-auth2.png)

3. Uygulama bağlantı ayarlarınızı gözden geçirin. Güvenlik ilkelerine bağlı olarak, bu ayarları değiştirin:

    ![Seçili İlkesi ayarları seçeneği](media/tfvc-auth.png)

### <a name="i-do-not-see-anything-in-tfvc"></a>Tfvc'de herhangi bir şey göremiyorum

Geliştirme makinenizde Team Foundation sürüm denetimi (TFVC) kurmak ayarlamak için **gerekir** açıklandığı bir çalışma alanı oluşturma [çalışma alanlarını yönetme](#managing-workspaces) bölümü.

Kaynak denetimi Gezgini'nde basın **çalışma alanlarını yönet** düğmesi. Projenin geliştirme makinenizde bir klasörü eşlemek için adımları izleyin.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Göremiyorum / all, projelerim

Kimlik doğrulandıktan sonra projelerinin listesini görmeniz gerekir. Varsayılan olarak, yalnızca TFS projelerine gösterilmektedir. Diğer proje türleri görmek için "tüm projeleri bkz" kutusunu işaretleyin.

Doğru ayrıcalıklara sahip değilseniz, sunucu üzerinde olan projeler görünmez göz önünde bulundurun.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Hatası "çalışma alanı oluşturulamıyor. alıyorum Lütfen yeniden deneyin"

Çalışırken [yeni bir çalışma alanı oluşturma](#creating-a-new-workspace), aşağıdaki koşulların yerine getirildiğinden emin olmanız gerekir:

- Çalışma alanı adı geçersiz karakterler markaları kullanılamaz.
- Ad 64 karakterden kısa olmalıdır.
- Yerel yol diğer çalışma alanları tarafından kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirin ve kodunuzu Visual Studio (Windows üzerinde) kullanarak tfvc'de paylaşma](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)