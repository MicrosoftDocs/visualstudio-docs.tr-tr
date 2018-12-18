---
title: Visual Studio için R Araçları
description: R araçları için Visual Studio (RTVS), IntelliSense, hata ayıklama ve uzak çalışma alanları dahil olmak üzere birçok dil özellikleri sağlayan ücretsiz, açık kaynaklı bir uzantısıdır.
ms.date: 11/13/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 05ffd249be3d7734979f3a131a3a10423b76cb9d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35667021"
---
# <a name="work-with-r-in-visual-studio"></a>Visual Studio'da R ile çalışma

R, yüksek düzeyde genişletilebilir dil ve ortam istatistiksel bilgi işlem ve grafik için ' dir. GNU Genel Kamu Lisansı altında ücretsiz dağıtılır, güçlü topluluk desteği ölçeklenebilme ve güncelleyebileceği matematik simgeleri ve formüllerini dahil olmak üzere yayın kalitesinde çizimleri oluşturmak bilinen. R hakkında daha fazla bilgi [r-project.org](https://www.r-project.org/about.html) ve [R giriş](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

R araçları için Visual Studio (RTVS), ücretsiz bir, [açık kaynaklı](https://github.com/microsoft/RTVS) uzantısı için Visual Studio 2017 ve Visual Studio 2015 güncelleştirme 3 (veya üzeri), yayımlanan MIT lisansı altında. (İkinci açık kaynaklı bir bileşen olarak adlandırılan [RHost](https://github.com/microsoft/R-Host), hangi R yorumlayıcı ikili dosyaları, bağlantılar altında GNU genel lisans V2 yayımlanır.)

> [!Note]
> RTVS şu anda yalnızca Windows üzerinde Visual Studio ve Visual Studio olmayan Mac için desteklenir

Visual Studio'da R deneyimi için:

- [R Araçları'nı yükleme](installing-r-tools-for-visual-studio.md).
- İzleyin [Başlarken](getting-started-with-r.md) Kılavuzu, hem de [örnekleri](getting-started-samples.md) ve [Yardımı alma](getting-started-help.md) makaleler.

Ardından R güvenlikle ilgili özellikler ve bunun yanı sıra, Visual Studio'nun kendisi genel özellikleri hakkında daha fazla bilgi için aşağıdaki bağlantıları izleyin.

| Özellik | Açıklama | Genel Visual Studio belgeleri |
| --- | --- | --- |
| [Visual Studio Proje sistemi](r-projects-in-visual-studio.md) | Düzenleme ve uygun bir yapı içinde ilgili dosyaları yönetmek ve R kodu, dokumentace R, R Markdown, SQL sorguları ve saklı yordamlar gibi öğeleri için yararlı şablonlar yararlanın. Ayrıca ilginizi [Paket Yöneticisi](r-package-manager-in-visual-studio.md) ve [SQL Server tümleştirme](integrating-sql-server-with-r.md).  | [Visual Studio’da Çözümler ve Projeler](../ide/solutions-and-projects-in-visual-studio.md) |
| [Çalışma alanı](r-workspaces-in-visual-studio.md) | RTVS, verme R kodunu daha küçük veri kümeleri ile yerel ortamda geliştirmek, yerel ve uzak çalışma alanlarına bağlama ardından çok daha büyük veri kümeleriyle daha güçlü bulut tabanlı bilgisayarlarda kod bir kolayca çalıştırın. | yok |
| [R araçları seçenekleri](options-for-r-tools-in-visual-studio.md) | Çeşitli yönlerini RTVS denetler. | [Seçenekler iletişim kutusu](../ide/reference/options-dialog-box-visual-studio.md) |
| [Zengin düzenleme, IntelliSense ve kod parçacıkları](editing-r-code-in-visual-studio.md) | Sözdizimi renklendirme, içeren [IntelliSense](r-intellisense.md) tüm kod ve kitaplıkları arasında biçimlendirme, imza Yardımı, kod tanımı, tüm başvuruları Bul, Git [kod parçacıkları](code-snippets-for-r.md)ve daha fazlası. | [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | R Markdown belgeler markdown kod blokları içinde tümleşik R kodu ile veri sonuçlarınızı paylaşmanıza yardımcı olur. | yok |
| [Etkileşimli pencere](interactive-repl-for-r-in-visual-studio.md) | Bir tam REPL deneyimi için R etkileşimli pencerede kaynak dosyada kod bir kolayca çalıştırmanıza olanak sağlar. | yok |
| [Verileri görselleştirme](visualizing-data-with-r-in-visual-studio.md) | Çizim, R deneyiminin bir parçası olan ve RTVS destekleyen birden çok bağımsız çizim windows, her biri kendi geçmişi ve taşıma yeteneğini çizer pencereleri arasında. Çizimler bit eşlem ve PDF dosyaları için kaydedildi veya bir bit eşlem ya da meta dosyası olarak panoya kopyalandı.  | yok |
| [Değişken Gezgini](variable-explorer.md) | Genel veya özel paketi kapsamları değişkenlerinde sıralanabilir tabloları görüntüleyin ve CSV'ye aktarma olanağı ile inceleyin. | yok |
| [Tam özellikli hata ayıklama](debugging-r-in-visual-studio.md) | Etkileşimli pencere ile tümleştirmeyi içerir. | [Visual Studio’da hata ayıklama](../debugger/debugging-in-visual-studio.md) |

Ayrıca bkz: [sık sorulan sorular](faq.md).

|   |   |
|---|---|
| ![video kamera simgesini film](../install/media/video-icon.png "bir video izleyin") | [(Youtube.com) videoyu](https://www.youtube.com/watch?v=dll3IS1bfWQ) (12 m 36s) Visual Studio için R araçları genel bakış. Ayrıca bkz: [R araçları ile ilgili daha fazla video](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio). |

## <a name="send-us-your-feedback"></a>Bize geri bildirim gönderin!

1. **GitHub sorunları**: RTVS ekibine ulaşmak için en iyi yolu [Github'da bir sorun dosyalama](https://github.com/Microsoft/RTVS/issues), kullanarak veya **R Araçları** > **geri bildirim** menüsü.

1. **Gülümseme Gönder / Frown**: **R Araçları** > **geri bildirim** menü, geri bildirim gönderin ve sorunu tanılama aşamasında yardımcı olmak için RTVS günlük dosyalarını eklemek için hızlı bir yoludur. (Günlükleri içine yazılır *%temp%/RTVSlogs.zip* ayrı olarak göndermek istediğiniz durumunda.) Visual Studio telemetri dışı bıraktınız, günlüğe kaydetme devre dışı **yardımcı** > **geri bildirim** > **ayarları** menü komutu veya Yükleme sırasında.

1. **E-posta**: ekibi doğrudan geri bildirim gönderebilirsiniz *(,) microsoft.com rtvsuserfeedback*.
