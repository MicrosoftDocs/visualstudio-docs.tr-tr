---
title: Testler sırasında ekran ve ses kaydı
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 1470ab88cb21a7a80fa46f57f944ec5df21d544f
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894419"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Nasıl yapılır: test ayarlarını kullanarak testler sırasında ekran ve ses kayıtlarını dahil

Visual Studio'daki yapılandırma düzenleyicisinden, testi çalıştıran kullanıcının ses ve ekran kayıtları tanılama veri bağdaştırıcısını yapılandırabilirsiniz. Bu tanılama veri bağdaştırıcısı, test sırasında masaüstü oturumunun bir ekran ve ses kaydını kaydeder. Kayıt test sonucuyla birlikte kaydedilir veya bir hataya iliştirilebilir. Diğer ekip üyeleri, yeniden oluşturulması zor olan uygulama sorunlarını yalıtmak için kaydı kullanabilir.

> [!WARNING]
> Ekran ve ses kayıtları birden çok ekran yapılandırmasını desteklemez.

Ekran ve Ses Kaydedici el ile veya otomatikleştirilmiş testlerle kullanılabilir. Örneğin, kodlanmış UI testini uzaktan çalıştırırsanız, çalışırken kodlanmış UI testini görebilmek için masa üstünü kaydetmek isteyebilirsiniz. Bir ekran ve ses kaydını uzaktan yakalama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Masaüstü ile etkileşim kuran testleri çalıştırmak için test aracınızı ayarlama](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Ekran ve ses kaydını test ayarlarınız için yapılandırmak için

1.  Ekran ve ses kaydetmek için yapılandırmak istediğiniz test ayarlarını açın. Daha fazla bilgi için [(Azure Test planları) test sırasında tanılama verilerini toplama](/azure/devops/test/collect-diagnostic-data?view=vsts) veya [test ayarlarını kullanarak tanılama bilgi toplayan](../test/collect-diagnostic-information-using-test-settings.md).

2.  Test ayarları'nda seçin **rol** ekran ve ses kaydetmekte kullanılacak.

    > [!NOTE]
    > El ile ve otomatikleştirilmiş testler için bu testleri çalıştıran makine olabilir.

3.  Seçin **ekran ve Ses Kaydedici** seçip **yapılandırma**.

     **Yapılandırma tanılama veri bağdaştırıcısı-ekran ve Ses Kaydedici** iletişim kutusu görüntülenir.

     ![Video yapılandırma](../test/media/testsettingvideoconfiggdr.png)

4.  (İsteğe bağlı) Seçin **ses kaydını etkinleştir** Kaydınızda bir ses içeriğini yakalamak için.

5.  (İsteğe bağlı) Yanındaki onay kutusunu işaretleyin **test durumu geçerse kaydı Kaydet** ekran ve ses kayıtları için her ikisini de kaydetme başarısız ve başarılı test belirtmek için.

    > [!WARNING]
    > Seçerseniz **test durumu geçerse kaydı Kaydet**, kayıt sunucu üzerinde depolama alanı kullanan test sonuçları ile saklanır. Kullanabileceğiniz **Test eki Temizleyicisi** bu ekleri temizlemek için aracı.

6.  Altında **ekran kaydı kalitesi**, aşağıdaki açılır liste seçenekleri yapılandırın:

    1.  **Kare hızı:** kullanmak istediğiniz ekran ve ses kaydında saniyede kaç kare belirtin. 4 Saniyedeki varsayılan değerdir. 2 ile 20 arasındaki değerler belirtilebilir.

    2.  **Bit hızı:** saniyede kaç kilobayt ekran ve ses kaydında kullanılacağını belirtin. Varsayılan değer 512'dır. 512 ve 10.000 arasındaki değerler belirtilebilir.

    3.  **Kalite(1-100):** kalitesini ekran ve ses 1 ile 100 arasında bir aralık belirleyerek belirtebilirsiniz. 50 (Orta aralık) varsayılandır.

7.  Seçin **Tamam**. Tanılama izleme toplayıcı ayarları şimdi yapılandırılır ve test ayarlarınız için kaydedildi.

    > [!TIP]
    > Bu tanılama veri bağdaştırıcısı için yapılandırmayı sıfırlamak için seçin **varsayılan yapılandırmaya Sıfırla** Visual Studio için ve **Varsayılana Sıfırla** Microsoft Test Yöneticisi için.

## <a name="see-also"></a>Ayrıca bkz.

- [(Azure Test planları) test sırasında tanılama verilerini toplayın](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [El ile testlerde (Azure Test planları) tanılama verilerini toplayın](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Test ayarlarını kullanarak tanılama bilgileri Topla](../test/collect-diagnostic-information-using-test-settings.md)
- [El ile yapılan testleri (Azure Test planları)](/azure/devops/test/run-manual-tests?view=vsts)