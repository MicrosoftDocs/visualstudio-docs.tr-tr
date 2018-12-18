---
title: Git ile çalışma
description: Mac için Visual Studio'da Git kullanma
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.openlocfilehash: 10d5b34ece7d093a42bafc1f0e410b670dd342f1
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296456"
---
# <a name="working-with-git"></a>Git ile çalışma

Git takımlar aynı belgelerde aynı anda çalışmasına izin veren bir dağıtılmış sürüm denetim sistemidir. Bu, tüm dosyaları içeren bir merkezi sunucu yoktur, ancak bu kaynaktan bir depo kullanıma alındığında, deponun tamamı için yerel makine kopyalanmış olan anlamına gelir.

Aşağıdaki bölümlerde nasıl Git sürüm denetimi Visual Studio'da için Mac için kullanılabileceğini keşfedin

## <a name="git-version-control-menu"></a>Git sürüm denetimi menüsü

Aşağıdaki resimde, sürüm denetimi menü öğesi tarafından Mac için Visual Studio tarafından sağlanan seçenekleri gösterir:

![Sürüm denetimi menü öğesi](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Gönderme ve çekme

Gönderme ve çekme Git içinde en yaygın kullanılan eylemleri ikisidir. Diğer kişilerin Uzak depoya yapmış olduğunuz değişiklikleri eşitlemek için **çekme** buradan. Bu seçerek Mac için Visual Studio'da yapılır **sürüm denetimi > güncelleştirme çözümünü**.

Daha sonra dosyalarınızı güncelleştirildi, gözden geçirdikten ve bunları kaydedilen sonra gerekir **anında iletme** diğerleri değişikliklerinizi erişmesine izin vermek için Uzak depoya bunları. Bu seçerek Mac için Visual Studio'da yapılır **sürüm denetimi > anında iletme değişiklikleri**. Bu, böylece Kaydettiğim değişiklikleri görüntülemek anında iletme iletişim kutusunu görüntülemek ve göndermek için dalı seçin:

![İletişim için yürütmek için dal gösteriliyor](media/version-control-gitPush.png)

Ayrıca kaydedin ve işleme iletişim kutusu aracılığıyla aynı anda Değişikliklerinizi gönderin:

![Kaydet ve anında iletme gösteren seçeneği aynı anda.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>, Günlük, sorumlu ve birleştirme

Pencerenin en altında görüntülenen beş sekme bulunur aşağıda gösterildiği gibi:

![Sürüm denetimi sekmeleri](media/version-control-gitTabs.png)

Bu, aşağıdaki eylemleri izin ver:

* **Kaynak** -kaynak kod dosyanız görüntüler.
* **Değişiklikleri** -yerel dosyanızı ve temel dosya arasında kod değişikliği görüntüler. Ayrıca, dosyanın farklı sürümlerini farklı karmaları karşılaştırabilirsiniz:

    ![Değişiklikleri sekmesi](media/version-control-gitChange.png)

* **Sorumlu** -her bir kod bölümünü ile ilişkili kullanıcı adını görüntüler.
* **Günlük** -tüm işlemeleri, saat, tarih, iletileri ve dosyayı sorumlu olan kullanıcılar görüntüler:

    ![Günlük Sekmesi](media/version-control-gitLog.png)

* **Birleştirme** -iş işleme alırken bir birleştirme çakışması varsa, bu kullanılabilir. Bu, siz ve böylece hem kod bölümlerini düzgün bir şekilde birleştirmek diğer geliştirici, tarafından yapılan değişiklikleri görsel bir temsilini gösterir.

## <a name="switching-branches"></a>Dallar arasında geçiş

Varsayılan olarak, bir depoda oluşturduğunuz ilk dalı olarak bilinen **ana** dal. Hiç teknik ana dal ile diğer arasında farklı bir şey, ancak çoğunlukla geliştirme takımları 'Canlı' veya 'üretim' dalı olarak zorlayıcı bir ana daldır.

Bağımsız bir satırı geliştirme ana (veya başka bir daldan, sorgunuzun) kapalı dallara ayırma tarafından oluşturulabilir. Bu ana dala bir noktada yeni bir sürümü 'Canlı' nedir bağımsız olarak geliştirme için izin verme zamanında sağlar Dallar bu şekilde kullanılması genellikle yazılım geliştirme özellikleri için kullanılır

Kullanıcılar, bunlar için her deponun ancak önerilen bir dalı kullanılarak tamamladıktan sonra silinmeden aynı sayıda dallar oluşturabilir depoyu saklamak için düzenlenir.

Dalları görüntülendiğinde Visual Studio'da Mac için göz atarak **sürüm denetimi > yönetme dalları ve uzak kaynakları...** :

![Dalları görüntüle](media/version-control-gitBranch2.png)

Başka bir dala geçmek liste ve tuşlarına basarak seçerek **dalına** düğmesi.

Yeni bir dal seçin oluşturmak için **yeni** düğmesine Git deposu yapılandırması iletişim. Yeni dal adı girin:

![Yeni dal oluştur](media/version-control-gitBranch.png)

De bir uzak dal ayarlayabilirsiniz, _izleme_ dal. Dalları izleme hakkında daha fazla okuma [Git belgeleri](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Geçerli dal proje adı yanında çözüm panelinde bakın:

 ![Çözüm panelinde görüntülenen geçerli dal](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Gözden geçirme ve işleme

Dosyalardaki değişiklikleri gözden geçirmek için değişiklikleri, sorumluyu günlük kullanın ve bu konunun önceki kısımlarında gösterilen her bir belge sekmelerinde birleştirin.

Göz atarak, projenizdeki tüm değişiklikleri gözden **sürüm denetimi > İnceleme çözüm ve işleme** menü öğesi:

![Kod Görünümü gözden geçirin](media/version-control-gitReviewCommit.png)

Bu, tüm değişiklikleri geri al, bir düzeltme eki oluşturma veya işleme seçeneği projenin her bir dosyadaki izlenmesini sağlar.

Dosya uzak depoya kaydetmeye basın **işleme**bir işleme iletisi girin ve Kaydet düğmesi ile onaylayın:

![Dosya işleniyor](media/version-control-gitCommit.png)

Değişikliklerinizi tamamladıktan sonra bunları diğer kullanıcıların görebileceği izin vermek için Uzak depoya gönderin.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017 ve Azure depoları Git ile kod paylaşma](/azure/devops/repos/git/share-your-code-in-git-vs-2017)