---
title: Visual Studio ile ilgili SSS için R araçları
description: Visual Studio'da R hakkında sık sorulan sorular.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 29634d63cf8e898203ff4d72a23296bdb14019e0
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348491"
---
# <a name="frequently-asked-questions"></a>Sık sorulan sorular

## <a name="visual-studio-support"></a>Visual Studio desteği

**SORU. RTVS, OS X veya Linux üzerinde çalışır mı?**

A. RTVS, şu anda yalnızca Windows uygulaması olan Visual Studio üzerinde oluşturulmuştur. Microsoft Visual Studio Code ve Visual Studio Mac desteği araştırmaktadır. Başvurmak [RTVS sorun #1295](https://github.com/Microsoft/RTVS/issues/1295).

**SORU. RTVS, Visual Studio Express sürümleri ile çalışır mı?**

A. Hayır.

**SORU. Visual Studio uzantıları RTVS ile kullanabilir miyim?**

A. Kesinlikle. Aslında, popüler r ile çalışan kişiler için birkaç şunlardır

- [VsVim vim tuş bağlamaları için](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Markdown Düzenleyicisi ile Canlı Önizleme](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Bkz: [Visual Studio Market](https://marketplace.visualstudio.com/) daha fazlasını bulmak için.

**SORU. Visual Studio'da RTVS olduğu için R ile kolayca kullanılabilir anlamı C#, C++ ve diğer Microsoft diller?**

A. Hayır. RTVS R kodunu geliştirmek için bir araçtır ve standart yerel R yorumlayıcılarını kullanır. R ve diğer diller arasında birlikte çalışma şu anda desteklenmemektedir.

**SORU. RTVS bir İngilizce olmayan yerel ayar ile çalışır mı?**

A. RTVS 1.0 sürümünde yalnızca İngilizce. 1.1 sürüm, Visual Studio'nun kendisi diller aynı kümesine yerelleştirilecek. Bu sırada, kullanın [Visual Studio 2015 dil paketi, İngilizce](https://www.microsoft.com/download/details.aspx?id=48157), veya Visual Studio 2017'de yükleyiciyi çalıştırın ve İngilizce seçin **dil paketlerini** sekmesi.

![Visual Studio 2017 için uluslararası ayarlar](media/FAQ-international-settings.png)

**SORU. Geçerli Visual Studio ayarlarımı gerçekten istiyorum, ancak yeni veri bilimi ayarları istiyor. Ne yapmalıyım?**

A. Geçerli Visual Studio ayarlarınızı kullanarak kaydetmek **Araçları** > **içeri ve dışarı aktarma ayarları**, sonra veri bilimi ayarlarına geçin. Kayıtlı ayarları geri yüklemek için kullanın **içeri ve dışarı aktarma ayarları** yeniden komutu.

**SORU. Visual Studio Proje bir ağ paylaşımında depolayabilir miyim?**

A. Hayır, Visual Studio, bir ağ paylaşımından yükleme projelerini desteklemez.

## <a name="r-interpretersintegration"></a>R yorumlayıcılarını/tümleştirmesi

**SORU. Hangi R yorumlayıcılarını RTVS ile çalışır mı?**

A. [CRAN R](https://cran.r-project.org/), [Microsoft R istemcisi ve Microsoft Machine Learning Server](/machine-learning-server/)

**SORU. Bu yorumlayıcılarını nereden indirebilirim?**

A. Bkz: [yükleme](installing-r-tools-for-visual-studio.md).

Q **Microsoft R Server nedir?**

A. R Server, eski adı olan [Microsoft Machine Learning sunucusu](/machine-learning-server/what-is-machine-learning-server).

**SORU. RTVS R 32-bit sürümleri ile çalışır mı?**

A. Hayır, RTVS, yalnızca 64 bit Windows sürümlerinde çalışan R 64-bit sürümleri destekler.

**SORU. RTVS benim kaynak denetim sistemi ile çalışır mı?**

A. Evet, Visual Studio'ya entegre herhangi bir kaynak denetim sistemi kullanabilirsiniz.

**SORU. Önerilen nelerdir *.gitignore* RTVS proje ayarlarını?**

A. GitHub, ana deposuna tutar önerilen *.gitignore* dosyaları. Burada görebilirsiniz: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Uzak Hizmetleri

S. **Visual Studio'da uzak Hizmetleri nedir?**

A. Visual Studio için Uzak R Services, Windows veya Linux makinesi kurmak ve sonra RTVS bağlanmak sağlar. Bkz: [uzak çalışma alanlarını ayarlayın](setting-up-remote-r-workspaces.md).

S. **Microsoft Machine Learning Server'a RTVS bağlanabilir miyim?**

A. Hayır, Microsoft ML Server farklı bir teknolojidir ve aynı bağlantı mekanizması olarak sağlamaz çünkü RTVS tarafından gerekli.

S. **RTVS, Azure üzerinde veri bilimi VM görüntüsü kullanılarak oluşturulan bir sanal makineye bağlanabilir miyim?**

A. Evet; [veri bilimi sanal makinesi - Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) görüntü Visual Studio için Uzak R Hizmetleri ile önceden yüklenmiş olarak gelir.

Soru, **olabilir RTVS yüklü R ile bir uzak makineye bağlanma?**

Uzak makinede var olan bazı hizmeti istekleri dinlemek için R kodu yürütmek için kodu alma ve gönderme sonuçları istemci makineye yedekleyin. Visual Studio için Uzak R Hizmetleri neler budur. Bkz: [uzak çalışma alanlarını ayarlayın](setting-up-remote-r-workspaces.md).

S. **Uzak oturumu nedir?**

A. Bkz [uzak sunucuda çalıştırma](/machine-learning-server/r/how-to-execute-code-remotely) Machine Learning sunucusu belgelerinde.

## <a name="rtvs-development-and-features"></a>RTVS geliştirme ve özellikleri

**SORU. X özellik eksik, ancak RStudio vardır!**

A. RStudio, yıllar boyunca geliştirilmekte olan R için harika ve olgun bir ıde'dir. Başarılı olması için gereken tüm önemli özelliklere sahip RTVS çalışmaktadır. Yardım alarak gelecekteki önceliklerini [RTVS anket](https://www.surveymonkey.com/r/RTVS1) ve sorunları dosya çubuğunda [GitHub](https://github.com/Microsoft/RTVS/issues/).

**SORU. RTVS için katkıda bulunduğum?**

A. Kesinlikle! Kaynak kodu yaşamaktadır [Github](https://github.com/microsoft/RTVS). Hataları gönderme ve önceden dosyalanmış üzerindekiler açıklama sorun İzleyicisi'ni kullanın.

Ayrıca bu belgelerine katkıda bulunun Hoş Geldiniz&mdash;yalnızca select **Düzenle** sağ üst kısmındaki herhangi bir sayfa üzerinde komutu. Belgelerdeki yorumlar da herhangi bir sayfanın alt kısmında ekleyebileceğiniz Hoş Geldiniz.
