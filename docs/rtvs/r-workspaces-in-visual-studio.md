---
title: R çalışma alanları
description: Visual Studio'da çalışma alanlarını kullanarak R kodunu çalıştığı denetlemek nasıl.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 11b5086c934b433d4e28095c1d50471ea44e15a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919305"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>R kodu ile çalışma çalıştığı denetimi

Bir çalışma alanında R araçları için Visual Studio (RTVS) bir R oturumu, hangi hem yerel hem de uzak bilgisayarlarda oluşabilir çalıştığı yapılandırmanıza olanak sağlar. Amacı, potansiyel olarak daha güçlü bulut tabanlı bilgisayarlar yararlanmak olanağı sunan bir karşılaştırılabilir kullanıcı deneyimi ile çalışmak için izin vermektir.

Açmak için **çalışma alanları** penceresinde kullanım **R Araçları** > **Windows** > **çalışma alanları** komutu veya tuşlarına basın **Ctrl**+**9**.

![Çalışma alanları penceresinde (VS2017) Visual Studio için R araçları](media/workspaces-window.png)

Bu pencerede, yeşil onay işareti RTVS bağlandığı etkin çalışma gösterir. Mavi bir oku seçerek, etkin çalışma ayarlar. Her bir çalışma alanının sağ ayarları (dişli) simgesini adı, konumu ve komut satırı bağımsız değişkenleri değiştirmenize izin verir. Kırmızı X el ile eklenen bir çalışma alanı kaldırır.

## <a name="save-and-reset-a-workspace"></a>Kaydet ve bir çalışma alanını sıfırlama

Bir projeyi kapatıp, varsayılan olarak, çalışma durumu RTVS kaydetmez. Bu davranışı değiştirebilirsiniz ancak aracılığıyla [çalışma alanı seçeneklerini](options-for-r-tools-in-visual-studio.md#workspace).

**R Araçları** > **oturumu** > **sıfırlama** komut ve etkileşimli pencerede sıfırlama araç çubuğu düğmesini ayrıca herhangi bir çalışma alanı durumunu Sıfırla saat. Uzak çalışma alanları ile sıfırlama ilk etkili toplanan tüm dosyaları siler bir uzak sunucuya bağlanırken oluşturulan kullanıcı profili siler.

## <a name="local-workspaces"></a>Yerel çalışma alanları

Bilgisayarınızda yüklü olan tüm R yorumlayıcılarını yerel çalışma alanlarını listeler. 

Visual Studio başlatıldığında bakarak yüklediğiniz R sürümleri otomatik olarak algılamak çalışır **HKEY_LOCAL_MACHINE\Software\R çekirdek\\**  kayıt defteri anahtarı. Bu denetim yalnızca başlangıçta yapıldığı için yeni İnterpret R yüklerseniz, Visual Studio'yu yeniden başlatmanız gerekir.

Standart dışı bir şekilde (örneğin, yalnızca bir yükleyici çalıştırmak yerine bir klasöre dosyalar kopyalanıyor) yüklü olan R yorumlayıcıyı RTVS algılayamayabilir. Bu durumda, el ile yeni bir yerel R çalışma alanı gibi oluşturun:

1. Seçin **Ekle** çalışma alanları penceresinde düğmesine.
1. Yeni çalışma alanı için bir ad girin.
1. İçeren bir R kök klasörün yolunu girin *bin* klasöründe RTVS başladığında yorumlayıcısı geçirilecek herhangi isteğe bağlı komut satırı bağımsız değişkenleri yanı sıra bir yorumlayıcıya sahip.
1. Seçin **Kaydet** bitirdiğinizde.

![Yeni bir çalışma alanı ekleme](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Uzak çalışma alanları

Uzak çalışma alanlarını bir uzak bilgisayar üzerinde bir R oturumuna bağlamanızı sağlar. (Bkz [uzak çalışma alanlarını ayarlayın](setting-up-remote-r-workspaces.md) bir bilgisayar bu amaç için nasıl yapılandıracağınızı öğrenmek için.)

Visual Studio otomatik olarak algılamıyor uzak çalışma alanlarını, bunları kullanarak el ile eklemelisiniz **Ekle** önceki bölümde açıklandığı gibi çalışma alanları penceresinde düğmesi. Bu durumda, uzak bilgisayarın URI yerine yerel bir yol girin.

> [!Important]
> Uzak çalışma alanlarını bir URI tarafından tanımlanan, *HTTPS protokolünü kullanmalıdır* gizliliği ve uzak bilgisayar ile iletişimde bütünlüğünü sağlamak için. Visual Studio, HTTPS desteklemeyen bir uzak bilgisayara bağlanamıyor.

> [!Note]
> Uzak çalışma alanlarını etkili bir şekilde Önizleme aşamasındadır. Biz, dosya eşitleme sorunun gelecekteki bir yayın için daha iyi bir uygulama üzerinde çalışıyorsanız ve fikirlerinizi ve geri bildirim Hoş Geldiniz.

## <a name="remote-workspace-logon"></a>Uzak çalışma alanı oturum açma

Uzak çalışma alanına bir kullanıcı adı ve parolayla oturum açma kullanmanız gerekir.

### <a name="logon-to-windows-workspace"></a>Windows çalışma alanına oturum açma

Kurulum, etki alanı hesabı kullanmak için uzak makine ise bir uzak çalışma alanına erişmek için etki alanı oturum açma kullanabilirsiniz. Bunun olmaması durumunda kullanmak zorunda `machine-name\username` uzak makinede bir makine hesabı kullanarak oturum açmak için biçim.

### <a name="logon-to-linux-workspace"></a>Linux çalışma alanına oturum açma

Oturum açmak için bir linux hesabı kullanımı `<<unix>>\username` biçimi. Örneğin, bir hesap adına göre varsa `ruser`, kullanıcı adı olarak yazmanız sonra `<<unix>>\ruser`.

## <a name="switch-between-workspaces"></a>Çalışma alanları arasında geçiş yapın

RTVS aynı anda yalnızca tek bir çalışma alanına bağlı. İlişkili çalışma alanı, küçük yeşil bir onay işareti çalışma alanları penceresinde ile belirtilir. Varsayılan olarak, RTVS önceki bir oturumda son açık yerel çalışma alanına bağlar.

Etkin çalışma alanı değiştirmek için istediğiniz çalışma alanını yanındaki mavi oku seçin. Bunun yapılması oturumunuzun kaydetmenizi ister geçerli çalışma sonlandırır ve ardından yeni bir tane geçer.

> [!Tip]
> Kaydetme devre dışı bırakmak için komut istemi, select **R Araçları** > **seçenekleri** ayarlayın ve komut **çalışma alanları geçmeden önce onay iletişim kutusunu göster** seçeneği`No`. Bkz: [çalışma alanı seçeneklerini](options-for-r-tools-in-visual-studio.md#workspace).

Kaldırılıyor, veya deftere kullanılamaz RTVS oluşturulmaması bir uzak çalışma alanına herhangi bir çalışma alanına bağlı bir yerel çalışma alanı geçmek çalışır. Sonuç olarak, kodu etkileşimli pencerede girin veya aksi halde kodu çalıştırmak çalıştığınızda bir hata görebilirsiniz:

![Çalışma alanı için RTVS bağlı olduğunda hata](media/workspaces-disconnected-interactive-window.png)

Bunu düzeltmek için çalışma alanları penceresinde başka bir çalışma alanına geçin. Çalışma alanı varsa, İnterpret R yüklemeniz gerekir. Ayrıca, Visual Studio çalışırken yorumlayıcıyı yüklediyseniz, Visual Studio'yu yeniden başlatmayı deneyebilirsiniz.

### <a name="switch-to-a-remote-workspace"></a>Bir uzak çalışma alanına geçin

RTVS bir uzak çalışma alanına bağlanırken kimlik bilgilerini ister ve ardından (güvenli Windows kimlik bilgileri kasası kullanarak) bu kimlik bilgilerinin sonraki oturumlar için önbelleğe alır. Uzak sunucu ile iletişimi güvenli bir şekilde (gereklidir) HTTPS gerçekleştirilir.

Sunucu yapılandırmasına bağlı olarak, "uzak R Hizmetleri tarafından sunulan güvenlik sertifikası (name) makinesi gerçekten de bağlandığınız kanıtlamak bize izin vermiyor." okuyan, bağlanırken uyarı sertifika görebilirsiniz.

![Bir uzak çalışma alanına bağlanırken otomatik olarak imzalanan bir sertifika Uyarısı](media/workspaces-remote-self-signed-certificate-warning.png)

Sertifika için RTVS, bağlanmaya çalıştığınız bilgisayarın tarafından sunulan bir belgedir. Sertifika, o bilgisayardaki URI tanımlar bir alan içeriyor. Sertifika URI'de ve sunucunun güvenliği tehlikeye girmiş olabilecek olduğunu gösteren bilgisayara bağlanmak için kullanılan URI arasında bir uyuşmazlık RTVS algıladığında bir uyarı görüntülenir.

Ancak, bu uyarı ayrıca görünür bir *otomatik olarak imzalanan sertifika* güvenilen bir sağlayıcı birinden kullanmak yerine uzak bilgisayarda HTTPS'yi etkinleştirmek için kullanıldı. Daha fazla bilgi için [uzak çalışma alanlarını ayarlayın](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Yerel ve uzak bilgisayarlarda dizinleri

Varsayılan olarak, geçerli çalışma dizininize yerel bir çalışma alanında yeni bir R yorumlayıcı başlattığınızda olduğu *%userprofile%\Documents*. Dizini kullanarak istediğiniz zaman değiştirebilirsiniz **R Araçları** > **çalışma dizini** komutlar, veya ile Visual Studio Çözüm Gezgini'nde projeye sağ ve gibikomutlarseçme **Çalışma dizini buraya ayarlayın**.

Uzak bir bilgisayarda ilk kez bağlandığınızda, RTVS çalışma dizinini ayarlar için bir kullanıcı profili kimlik bilgileri temelinde otomatik olarak oluşturur. *belgeleri* klasörü altında bu profili. Bu klasör, aynı kimlik bilgilerini kullanan tüm sonraki uzak oturumlar için kullanılır.

Sonuç olarak, kodunuzun çalıştığı tam konumu, yerel ve uzak çalışma alanları arasında değişebilir. Böylece kodunuzun çalışma alanı arasında taşınabilir olduğundan kodunuzda, ardından her zaman veri dosyaları ve gibi göreli yollar kullanın.

Ayrıca, uzak çalışma alanları ile çalışma dizinindeki tüm dosyalar aynı kullanıcı profili oturumlar arasında değiştirilmez olduğunu unutmayın. Daha önce belirtildiği gibi kullanarak bu dosyaları silebilirsiniz **R Araçları** > **oturumu** > **sıfırlama** komutu (ya da Sıfırla düğmesini Etkileşimli pencere) bir uzak çalışma alanı kullanarak. Bu komut, kullanıcı profili yeniden bağlandığınızda, yeniden sunucudan siler.

## <a name="copy-project-files-to-remote-workspaces"></a>Uzak çalışma alanları için proje dosyaları Kopyala

Bile bir uzak çalışma alanı kullanırken R projeleri Visual Studio ile çalışırken, yerel bilgisayarda her zaman en son proje dosyalarını sahiptir. Bir projeyi Visual (genellikle bu projeyi içeren bir çözüm açılırken anlamına gelir) Studio'da açtığınızda, projenin içeriği tamamen yerel bilgisayarda bulunan diğer bir deyişle, RTVS varsayar. Uzak çalışma alanı, etkin ve tüm proje dosyaları için yalnızca geçici bir ana bilgisayardır koddan çıktı. Bu, örneğin, kullanarak bir dosya yüklenirken anlamına `source` etkileşimli pencerede, bu dosya zaten yolunda bir uzak bilgisayarda sağladığınız veya uzak İnterpret R geçerli çalışma dizininde olması gerekir olmalıdır (ile ayarlamak`setwd()`</c2>işlevi).

Dosyalar uzak sunucuya şu şekilde kopyalanır:

- Etkileşimli pencere üzerinden uzaktan dosyalarıyla çalışmak için önce bunları el ile Çözüm Gezgini'nde, dosyaları (veya proje) sağ tıklatıp seçerek kopyalamanız gerekir **kaynak seçili**. Tek tek dosyalar için sunucu üzerindeki çalışma dizinine kopyalanana; bir proje kopyalarken RTVS proje için bir klasör oluşturur.

- Dosyaları daha sonra Çözüm Gezgini'nde ve ardından seçerek kopyalayabilirsiniz **seçili kaynak dosyaları (s)**. Bu eylem, bunları etkileşimli pencereye yükler ve orada çalışır. Oturum, bir uzak bilgisayara bağlıysa, dosyalar var. önce kopyalanır.

- Ne zaman RTVS bir uzak çalışma alanına bağlı ve tuşuna **F5**seçin **hata ayıklama** > **hata ayıklamayı Başlat**, veya aksi takdirde varsayılan RTVS kodunuzu çalıştırmaya başlayın Projenin dosya uzak çalışma alanına otomatik olarak kopyalar (aşağıda bu davranışını denetlemek için bakın).

- Sunucuda zaten mevcut olan tüm dosyaların üzerine yazılır.

> [!Note]
> Tüm R işlev çağrıları RTVS güvenilir bir şekilde müdahale edemez çünkü gibi işlevleri çağırma `source()` veya `runApp()` (Shiny uygulamalarını için) etkileşimli pencereye mu *değil* dosyaları uzak çalışma alanına kopyalayın.

[Proje Özellikleri](r-projects-in-visual-studio.md#project-properties) Denetim dosyalarını bir projesi RTVS kopyalar olup çalıştırın ve tam olarak hangi dosyalar kopyalanır. Bu sayfayı açmak için seçmeniz **proje** > **(ad) özellikleri** menü komutu ya da Çözüm Gezgini'nde ve select projeyi sağ **özellikleri**.

![Proje Özellikleri sekmesi ile dosya aktarımı çalıştırma ayarları](media/workspaces-remote-file-transfer-filter-settings.png)

Burada, **aktarım çalışma dosyalarını** özellik RTVS proje dosyaları otomatik olarak kopyalar olup olmadığını belirler. **Dosyaları aktarmak için** sonra tam olarak hangi dosyaların aktarılır filtreleri değer. Yalnızca kopyalamak için varsayılandır *. R*, *. Rmd*, *.sql*, *.md*, ve *.cpp* dosyaları. Bu davranış, yanlışlıkla sunucu her çalıştırma ile büyük veri dosyalarını kopyalamak önler. 

## <a name="copy-files-from-a-remote-workspace"></a>Dosyaları bir uzak çalışma alanından Kopyala

R betiğinizi dosyaları sunucu üzerinde oluşturursa, bu dosyaları kullanarak istemciyi yeniden kopyalayabilirsiniz `rtvs::fetch_file` işlevi. Bu işlev, en az, uzak bilgisayarınıza kopyalamak istediğiniz dosya yolunu ve isteğe bağlı olarak, bilgisayarınızda hedef yolu kabul eder. Bir yol belirtmezseniz, dosya olarak kopyalanır, *%userprofile%\Downloads* klasör.
