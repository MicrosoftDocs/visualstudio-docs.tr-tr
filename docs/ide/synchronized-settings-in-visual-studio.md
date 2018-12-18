---
title: Ayarları eşitleme
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7dcddc06233f439547f0725c1fb39fff26152237
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348423"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Birden fazla bilgisayara Visual Studio ayarları eşitleme

Birden çok bilgisayar üzerinde aynı kişiselleştirme hesabı kullanarak Visual Studio'da oturum açtığınızda, ayarlarınızı bilgisayarlarda eşitlenebilir.

## <a name="synchronized-settings"></a>Eşitlenmiş ayarlar

Varsayılan olarak, şu ayarlar eşitlenir:

- Geliştirme Ayarları. Bir ayarlar koleksiyonu seçin ilk kez Visual Studio'yu açın, ancak zaman seçimi değiştirebilirsiniz. Daha fazla bilgi için [ortam ayarları](../ide/environment-settings.md).

- Kullanıcı tanımlı komut diğer adları. Komut diğer adlarını tanımlama hakkında daha fazla bilgi için bkz. [Visual Studio komut diğer adları](../ide/reference/visual-studio-command-aliases.md).

- Kullanıcı tanımlı pencere düzenleri **penceresi** > **pencere düzenlerini Yönet** sayfası.

- Aşağıdaki seçenekleri **Araçları** > **seçenekleri** sayfalar:

   - Tema ve menü çubuğunda büyük/küçük harf ayarlarını **ortam** > **genel** seçenekler sayfası.

   - Tüm ayarlar **ortam** > **yazı tipleri ve renkler** seçenekler sayfası.

   - Tüm şirket klavye kısayolları **ortam** > **klavye** seçenekler sayfası.

   - Tüm ayarlar **ortam** > **sekmeler ve Windows** seçenekler sayfası.

   - Tüm ayarlar **ortam** > **başlangıç** seçenekler sayfası.

   - Tüm ayarlar **metin düzenleyici** seçenekler sayfaları.

   - Tüm ayarlar **XAML Tasarımcısı** seçenekler sayfaları.

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Belirli bir bilgisayardaki eşitlenmiş ayarlar devre dışı bırakma

Eşitlenmiş ayarlar Visual Studio için varsayılan olarak açık olabilir. Eşitlenmiş ayarlar bir bilgisayara giderek kapatabilirsiniz **Araçları** > **seçenekleri** > **ortam**  >   **Hesapları** sayfası ve işaretini **ayarlarını Visual Studio oturumu açıldığında cihazlar arasında eşitleme**.

"A", bilgisayarda Visual Studio'nun ayarlarını eşitlemek isterseniz örnek olarak, "B" veya "C" bir bilgisayarda bilgisayar "A" ayarı değişiklikleri görünmez. Bilgisayarları "B" ve "C", birbirleriyle, ancak bilgisayar "A" ile değil eşitlemeye devam eder.

> [!NOTE]
> Ayarlar seçeneği seçimini kaldırarak eşitleme seçerseniz **Araçları** > **seçenekleri** > **ortam**  >  **Hesapları** sayfasında, diğer sürümlerini veya aynı bilgisayarda yüklü Visual Studio sürümleri etkilenmez. Visual Studio'nun bu yan yana yüklemeler (seçeneği, çok işaretini sürece) ayarlarına eşitlemeye devam eder.

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Visual Studio ailesi ürünler ve sürümleri ayarları eşitleme

Ayarları, sürümleri ve yüklü Visual Studio sürümleri arasında eşitlenir *yan yana*. Ayarları, aynı zamanda Visual Studio için Blend dahil olmak üzere Visual Studio ailesi ürünler arasında eşitlenir. Ancak, bir ürünün ailesi, Visual Studio ile paylaşılmaz kendi ayarlarına sahip olabilir. Örneğin, özel ayarları için Visual Studio için Blend bilgisayarda "A", "A" veya "B" bilgisayarlarda Visual Studio ile paylaşılmazlar.

## <a name="side-by-side-synchronized-settings"></a>Yan yana eşitlenmiş ayarlar

Visual Studio 2017 sürüm 15.3 ve daha sonra Visual Studio 2017 farklı yan yana yüklemeleri arasında araç penceresi düzeni gibi belirli ayarların paylaşılmaz. *CurrentSettings.vssettings* dosyası *%userprofile%\Documents\Visual Studio 2017\Settings* benzer bir özel yükleme klasöründeki *%localappdata%\ Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*.

> [!NOTE]
> Yeni yükleme özgü ayarları kullanmak için yeni bir yüklemesidir yapın. Mevcut bir Visual Studio 2017 yüklemesini son güncelleştirmeye yükseltmesi gerçekleştirdiğinizde, mevcut paylaşılan konum kullanılır.

Şu anda Visual Studio 2017'in yan yana yüklemelerine sahipseniz ve yeni yükleme için özel ayarlar dosya konumunu kullanmak istiyorsanız, aşağıdaki adımları izleyin:

1. Visual Studio 2017 15.3 veya üzeri bir sürüme yükseltin.

1. Kullanım **ayarları ayarları** tüm mevcut ayarlarınızı dışındaki bir konuma dışarı Aktarma Sihirbazı'nı *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* klasör.

1. Açık **VS 2017 için geliştirici komut istemi** yükseltilen Visual Studio yükleme ve çalıştırma `devenv /resetuserdata`.

1. Visual Studio’yu başlatın ve dışarı aktarılan ayarlar dosyasından kayıtlı ayarları içeri aktarın.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
- [Ortam ayarları](../ide/environment-settings.md)
- [Ortam > hesapları Seçenekler iletişim kutusu](reference/accounts-environment-options-dialog-box.md)
