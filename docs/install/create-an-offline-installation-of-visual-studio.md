---
title: Çevrimdışı yüklemesini oluşturma
description: Visual Studio bir güvenilir bir internet bağlantısı veya düşük bant genişliğine sahip olduğunuzda çevrimdışı yüklemeyi öğrenin.
ms.custom: seodec18
ms.date: 08/28/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37d218893ab16a8d0907e608ebeb3b02ab944385
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159990"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Visual Studio 2017'in çevrimdışı yüklemesini oluşturma

Biz, Visual Studio 2017'de ağ ve bilgisayar yapılandırmalarını çeşitli içinde çalışacak şekilde tasarlanmıştır. Denemenizi öneririz ancak [Visual Studio web yükleyicisini](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)&mdash;küçük bir dosyadır ve en son düzeltmeler ve özellikler ile güncel kalın sağlar&mdash;için aktarmanızı değil olduğunu biliyoruz.

Örneğin, düşük bant genişliğine sahip bir ya da güvenilir bir internet bağlantısına sahip olabilir. Bu durumda, birkaç seçeneğiniz vardır: Kullanabileceğiniz yeni "Tümünü indir ve sonra Yükle" özelliğini yüklemeniz veya dosyaların yerel önbellek oluşturmak için komut satırını kullanabilirsiniz önce dosyaları indirmek için.

> [!NOTE]
> Visual Studio 2017'in bir dağıtım için bir ağ güvenlik duvarı istemci iş istasyonları, internet'ten gerçekleştirmek isterse bkz Kurumsal Yönetici olduğunuz bizim [Visual Studio 2017'in bir ağ yüklemesini oluşturma](../install/create-a-network-installation-of-visual-studio.md) ve [Visual Studio'yu çevrimdışı yükleme için gerekli sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md) sayfaları.

## <a name="use-the-download-all-then-install-feature"></a>Kullanım "tümünü indir ve Yükle" özelliği

[**Yeni 15,8**](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017#install
): Web yükleyiciyi indirdikten sonra yeni seçin **tümünü indir ve Yükle** Visual Studio Yükleyicisi'nden seçeneği. Ardından, yükleme işlemine devam.

   !["Tümünü indir ve Yükle" seçeneği](media/download-all-then-install.png)

## <a name="use-the-command-line-to-create-a-local-cache"></a>Yerel önbellek oluşturmak için komut satırını kullanın

Küçük bir önyükleyici indirdikten sonra komut satırında yerel önbellek oluşturmak için kullanın. Ardından Visual Studio'yu yüklemek için yerel önbellek kullanın. (Bu işlem, önceki sürümleri için ISO dosyalarını değiştirir.)

İşte nasıl.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>1. adım - Visual Studio önyükleyicisini yükleyin

Bu adımı tamamlamak için bir internet bağlantısı olması gerekir.

Seçtiğiniz Visual Studio sürümünüz için Visual Studio önyükleyicisi indirerek başlayın. Kurulum dosyanızı&mdash;veya önyükleyici&mdash;ile eşleşir veya şunlardan birini benzer.

| Sürüm                    | Dosya                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

### <a name="step-2---create-a-local-install-cache"></a>2. adım - yerel yükleme önbelleği oluşturma

Bu adımı tamamlamak için bir internet bağlantısı olması gerekir.

> [!IMPORTANT]
> Visual Studio Community 2017 yüklerseniz, yükleme 30 gün içinde etkinleştirmeniz gerekir. Bu, internet bağlantısı gerektirir.

Bir komut istemi açın ve aşağıdaki örneklerde komutlardan birini kullanın. Visual Studio Community sürümünü kullanıyorsanız, burada listelenen örnekler varsayılır; komut sürümünüz için uygun şekilde ayarlayın.

- .NET web ve .NET masaüstü geliştirme için çalıştırın:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- .NET Masaüstü ve Office geliştirme için çalıştırın:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- C++ Masaüstü geliştirmesi için çalıştırın:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Tüm özellikleri ile tam olarak yerel bir düzen oluşturmak için (Bu uzun sürer&mdash;sahibiz _çok_ özelliklerinin!) çalıştırın:

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

İngilizce dışında bir dil yüklemek isterseniz değiştirme `en-US` yerel için [dil yerel ayarlar listesini](#list-of-language-locales). Ardından, [kullanılabilir iş yükleri ve bileşenlerin listesini](workload-and-component-ids.md) yükleme önbelleğiniz daha fazla özelleştirmek için.

> [!IMPORTANT]
> Visual Studio 2017 Düzen tamamlanamadı, en az 35 GB disk alanı gerektirir ve indirmek için biraz zaman alabilir. Bkz: [Visual Studio 2017'yi yüklemek için komut satırı parametreleri kullanmak](use-command-line-parameters-to-install-visual-studio.md) yüklemek istediğiniz bileşenleri ile yalnızca bir düzen oluşturma konusunda bilgi için.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Adım 3 - yerel önbellekten Visual Studio yükleme

> [!TIP]
> Yerel Yükleme önbellekten çalıştırdığınızda, Kurulum bu dosyaların her biri yerel sürümünü kullanır. Ancak önbellekte olmayan bileşenleri yüklemesi sırasında seçerseniz, bunları internet'ten indirmek Kurulum çalışır.

Yalnızca daha önce indirilen dosyaları yüklediğinizden emin olmak için Düzen önbelleği oluşturmak için kullanılan aynı komut satırı seçeneklerini kullanın. Örneğin, aşağıdaki komutla bir düzen önbelleği oluşturduysanız:

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Ardından yüklemesini çalıştırmak için bu komutu kullanın:

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> İmza geçersiz olduğunu belirten bir hata alırsanız, güncelleştirilmiş bir sertifika yüklemeniz gerekir. Çevrimdışı önbelleğinize sertifikaları klasörünü açın. Her sertifika dosyasını çift tıklayın ve Sertifika Yöneticisi sihirbazda'ye tıklayın. İçin bir parola istenirse, boş bırakın.

### <a name="list-of-language-locales"></a>Dil yerel ayarlar listesi

| **Dil yerel ayar** | **Dil** |
| ----------------------- | --------------- |
| cs-CZ | Çekçe |
| de-DE | Almanca |
| en-US | İngilizce |
| es-ES | İspanyolca |
| fr-FR | Fransızca |
| İt-IT | İtalyanca |
| ja-JP | Japonca |
| ko-KR | Korece |
| pl-PL | Lehçe |
| pt-BR | Portekizce - Brezilya |
| ru-RU | Rusça |
| tr-TR | Türkçe |
| zh-CN | Çince - Basitleştirilmiş |
| zh-TW | Çince - Geleneksel |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2017'in bir ağ oluşturun](../install/create-a-network-installation-of-visual-studio.md)
- [Visual Studio'yu çevrimdışı yükleme için gerekli sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio 2017 iş yükü ve Bileşen kimlikleri](workload-and-component-ids.md)
