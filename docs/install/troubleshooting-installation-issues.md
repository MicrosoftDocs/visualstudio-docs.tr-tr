---
title: Yükleme sorunlarını giderme veya yükseltme sorunları
description: Bazı durumlarda sorunlar. Visual Studio yüklemesi veya yükseltmesi başarısız olursa, bu sayfa yardımcı olabilir.
ms.date: 08/01/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 39accaa3b8ee6a5ac2979b7e93b02a1ce00716be
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159940"
---
# <a name="troubleshoot-visual-studio-2017-installation-and-upgrade-issues"></a>Visual Studio 2017 yükleme sorunlarını giderme ve yükseltme sorunları

> [!IMPORTANT]
> Yükleme sorun yaşıyorsunuz? Size yardımcı olabiliriz. Sunuyoruz bir [ **canlı sohbet** ](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) destek seçeneği.

Bu sorun giderme kılavuzu çoğu yükleme sorunları çözmelisiniz adım adım yönergeler içerir.

## <a name="how-to-troubleshoot-an-online-installation"></a>Bir çevrimiçi yükleme sorunlarını giderme

Aşağıdaki adımları, tipik bir çevrimiçi yükleme için en iyi duruma getirilir. Çevrimdışı yükleme etkileyen bir sorun için lütfen bkz [çevrimdışı yükleme sorunlarını giderme](#how-to-troubleshoot-an-offline-installation).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>1. adım - bu sorunun bilinen bir sorun olup olmadığını denetleyin

Microsoft düzeltmek için çalışmaktadır Visual Studio Yükleyicisi ile ilgili bazı bilinen sorunlar vardır. Sorununuz için geçici bir çözüm olup olmadığını görmek için [sürüm notlarımızda bilinen sorunlar bölümünü](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

### <a name="step-2---check-with-the-developer-community"></a>Adım 2 - Geliştirici topluluğu denetimiyle

Arama, hata iletisiyle [Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html). Diğer topluluk üyelerinin belgelenmiş bir çözüm.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>3. adım - yükseltme sorunlarını gidermek için Visual Studio yükleyicisi dizinini Sil

Visual Studio yükleyicisi önyükleyici, Visual Studio Yükleyicisi'nin rest yükleyen en az bir hafif çalıştırılabilir öğesidir. Bazı güncelleştirme hataları, Visual Studio Installer dosyalarını silerek ve sonra önyükleyici artırarak algoritmanın yeniden çalıştırılması çözebilir.

> [!NOTE]
> Aşağıdaki eylemleri gerçekleştirerek, Visual Studio Installer dosyalarını yükler ve yükleme meta verileri sıfırlar.

1. Visual Studio Yükleyicisi’ni kapatın.
2. Visual Studio yükleyicisi dizini silin. Genellikle, dizindir `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Visual Studio yükleyicisi önyükleyici çalıştırın. İndirmeler klasörüne bir dosya adıyla izleyen önyükleyici bulabileceğiniz bir `vs_[Visual Studio edition]__*.exe` deseni. Bu uygulamayı bulamazsanız, önyükleyici giderek indirebilirsiniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfası ve tıklayarak **indirme** Visual Studio sürümünüz için. Ardından yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
4. Yükleme veya Visual Studio güncelleştirmeyi yeniden deneyin. Yükleyici başarısız olmaya devam ederse, sonraki adıma gidin.

### <a name="step-4---report-a-problem"></a>4. adım - sorun bildirin

Bozuk dosyalarla ilgili olanlar gibi bazı durumlarda olay olarak denetlenmesi sırasında sorunlar yaşayabilirsiniz. Yardımımıza katkıda yardımcı olmak için lütfen aşağıdakileri yapın:

1. Uygulamanızın Kurulum günlükleri toplayın. Bkz: [Visual Studio yükleme günlüklerini almak nasıl](#how-to-get-visual-studio-installation-logs) Ayrıntılar için.
2. Visual Studio Yükleyicisi'ni açın ve ardından **sorun bildir** Visual Studio geri bildirim aracını açın.
![Geri bildirim aracını açmak için geri bildirim sağlamak düğmesine sekme](media/report-a-problem.png)
3. Sorun raporunuza bir başlık verin ve ilgili ayrıntıları sağlayın. Tıklayın **sonraki** gitmek için **ekleri** bölümüne ve ardından oluşturulan günlük dosyasını ekleyin (dosya altındadır genellikle `%TEMP%\vslogs.zip`).
4. Tıklayın **sonraki** sorun raporunuzu gözden geçirin ve ardından **Gönder**.

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Adım 5 - Çalıştır InstallCleanup.exe yükleme dosyalarını kaldırmak için

Son çare yapabilecekleriniz [Visual Studio kaldırmak](remove-visual-studio.md) tüm yükleme dosyalarını ve ürün bilgileri kaldırmak için.

1. Bölümündeki yönergeleri [Kaldır Visual Studio](remove-visual-studio.md).
2. Açıklanan önyükleyici yeniden [adım 3 - yükseltme sorunlarını gidermek için Visual Studio yükleyicisi dizini silme](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Yükleme veya Visual Studio güncelleştirmeyi yeniden deneyin.

### <a name="step-6---contact-us-optional"></a>6. adım - (isteğe bağlı) bizimle iletişime geçin

Önceki adımlardan hiçbiri başarılı bir şekilde yardımcı, yükleme veya yükseltme Visual Studio, kullanarak bizimle iletişime geçin bizim [ **canlı sohbet** ](https://visualstudio.microsoft.com/vs/support/#talktous) seçeneği (yalnızca İngilizce) daha fazla yardım için destek.

## <a name="how-to-troubleshoot-an-offline-installation"></a>Çevrimdışı yükleme sorunlarını giderme

Bilinen sorunlar ve geçici yerel bir düzenden yükleme sırasında yardımcı olabilecek bazı çözümler tablosu aşağıdadır.

| Sorun       | Öğe                   | Çözüm |
| ----------- | ---------------------- | -------- |
| Kullanıcılar dosyalara erişimi yoktur. | izinleri (ACL) | Bunlar diğer kullanıcılara Okuma yetkisi vermek için izinleri (ACL) ayarlayın sağlayın *önce* çevrimdışı yükleme paylaşın. |
| Yeni iş yükleri, bileşenleri ve dil yüklenemedi.  | `--layout`  | Kısmi bir düzenden yükleme ve daha önce iş yükleri, bileşenler veya indirilmedi diller, kısmi düzeni'ni seçin, internet erişimi olduğundan emin olun. |

## <a name="how-to-get-visual-studio-installation-logs"></a>Visual Studio yükleme günlüklerini alma

Kurulum günlükleri, çoğu yükleme sorunlarını gidermek için gereklidir. Ne zaman gönderdiğiniz bir sorun kullanarak [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio-2017.md) Visual Studio Yükleyicisi ', bu günlükleri otomatik olarak, rapora dahil edilir.

Microsoft Support başvurursanız kullanarak bu ayar günlüklerini göndermeniz gerekebilir [Microsoft Visual Studio ve .NET Framework günlük toplama aracı](https://aka.ms/vscollect). Günlük toplama aracı Visual Studio .NET Framework ve Windows SDK'sı SQL Server 2017'de tarafından yüklü tüm bileşenleri Kurulum günlüklerini toplar. Ayrıca, bilgisayar bilgilerini, Windows Installer envanterini ve Visual Studio yükleyicisi, Windows Installer ve sistem geri yükleme için Windows olay günlüğü bilgilerini toplar.

Günlükleri toplamak için:

1. [Aracı indirmek](https://aka.ms/vscollect).
2. Bir yönetici komut istemi açın.
3. Çalıştırma `Collect.exe` aracı kaydettiğiniz dizinden.
4. Ortaya çıkan Bul `vslogs.zip` dosyası, `%TEMP%` dizine, örneğin, `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> Aracı altında başarısız yüklemenin çalıştırıldığı kullanıcı hesabı altında çalıştırılması gerekir. Aracı farklı bir kullanıcı hesabından çalıştırıyorsanız, `–user:<name>` altında başarısız yüklemenin çalıştırıldığı kullanıcı hesabı belirtmek için seçeneği. Çalıştırma `Collect.exe -?` ek seçenekler ve kullanım bilgileri için bir yönetici komut isteminden.

## <a name="get-live-help"></a>Canlı yardım alın

Bu sorun giderme Kılavuzu'nda listelenen çözümleri başarıyla yüklemeniz veya Visual Studio yükseltme, kullanmanız için size yardımcı bizim [ **canlı sohbet** ](https://visualstudio.microsoft.com/vs/support/#talktous) seçeneği (yalnızca İngilizce) daha fazla yardım için destek.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017'yi kaldırma](remove-visual-studio.md)
* [Yükleme ve bir güvenlik duvarı veya proxy sunucusunun arkasına Visual Studio ve Azure hizmetlerini kullanma](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
