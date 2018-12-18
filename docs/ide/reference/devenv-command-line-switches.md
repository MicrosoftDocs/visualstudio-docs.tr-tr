---
title: Devenv komut satırı anahtarları
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3bf255a0e4eb622cb81718ddfc30d5b568bad2c2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063402"
---
# <a name="devenv-command-line-switches"></a>Devenv komut satırı anahtarları

Devenv, tümleşik geliştirme ortamı (IDE) için çeşitli seçenekleri yanı sıra derleme, hata ayıklama ve projeleri, komut satırından dağıtma olanak tanır. Bu anahtarları bir betik veya Gecelik Yapı betiği, bir .bat dosyası IDE çalıştırmak için veya belirli bir yapılandırmada IDE başlatmak için kullanın.

> [!NOTE]
> Derlemeyle ilgili görevler için devenv yerine MSBuild kullanmanız önerilir. Daha fazla bilgi için [MSBuild komut satırı başvurusu](../../msbuild/msbuild-command-line-reference.md).

## <a name="devenv-switch-syntax"></a>Devenv anahtarı sözdizimi

İle başlayan komutlar `devenv` tarafından işlenen `devenv.com` gibi standart sistem akışları çıkışını sunan yardımcı program `stdout` ve `stderr`. Çıktı, örneğin bir .txt dosyasına yakaladığında yardımcı programı uygun g/ç yönlendirmesi belirler.

Öte yandan, ile başlayan komutlar `devenv.exe` aynı anahtarlar kullanabilirsiniz ancak `devenv.com` yardımcı programı atlanır. Kullanarak `devenv.exe` doğrudan çıkış konsolda görüntülenmesini engeller.

Sözdizimi kurallarını için `devenv` anahtarları benzer diğer DOS komut satırı yardımcı programları için olanlar. Aşağıdaki sözdizimi kurallarını tümüne uygula `devenv` anahtarlar ve bunların bağımsız değişkenleri:

- İle başlayan komutlar `devenv`.

- Anahtarlar büyük küçük harfe duyarlı değildir.

- Bir çözüm veya proje belirtirken, ilk bağımsız değişken çözüm dosyası veya dosya yolu da dahil olmak üzere proje dosyasının adıdır.

- İlk bağımsız değişken bir çözüm veya proje değil bir dosya ise, bu dosyanın uygun düzenleyicide IDE yeni bir örneğini açar.

- Bir proje dosyası adı bir çözüm dosyası adı yerine sağladığında bir `devenv` komut aynı ada sahip bir çözüm dosyası için proje dosyasının üst klasörü arar. Örneğin, komut `devenv myproject1.vbproj /build` üst klasör için "myproject1.sln" adlı bir çözüm dosyası arar.

    > [!NOTE]
    > Bu projeye başvuran bir ve yalnızca bir çözüm dosyası, kendi üst klasörde bulunmalıdır. Üst klasör herhangi bir çözüm dosyası içeriyorsa bu projeye başvuran ya da üst klasör ona başvuran iki veya daha fazla çözüm dosyası içeriyorsa, ardından bir geçici çözüm dosyası oluşturulur.

- Dosya yolları ve dosya adı boşluklar, bunları tırnak içine almalısınız (""). Örneğin, "c:\project bir\\".

- Anahtarlar ve bağımsız değişkenler aynı satırda arasında bir boşluk karakteri Ekle. Örneğin, komut **devenv/log çýktý.txt** IDE açılır ve tüm bilgilerini günlüğe kaydetme oturumu için için çýktý.txt çıkarır.

- Desen eşleştirme sözdizimi kullanamazsınız `devenv` komutları.

## <a name="devenv-switches"></a>Devenv anahtarları

Aşağıdaki komut satırı anahtarları, IDE görüntülemek ve açıklandığı gibi görev gerçekleştirin.

|Komut satırı anahtarı|Açıklama|
| - |-----------------|
|[/Command](../../ide/reference/command-devenv-exe.md)|IDE'yi başlatır ve belirtilen komutu yürütür.|
|[/DebugExe](../../ide/reference/debugexe-devenv-exe.md)|Hata ayıklayıcının denetiminin altında bir C++ yürütülebilir dosyayı yükler. Visual Basic için bu anahtarı kullanılamıyor veya C# yürütülebilir. Daha fazla bilgi için [otomatik olarak hata ayıklayıcıda bir işlem başlatmak](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|
|[/ LCID veya/l](../../ide/reference/lcid-devenv-exe.md)|IDE için varsayılan dili ayarlar. Belirtilen dil Visual Studio yüklemenizde dahil edilmemişse, bu ayar yoksayılır.|
|[/Log](../../ide/reference/log-devenv-exe.md)|Visual Studio başlatılır ve tüm etkinlik günlük dosyasına kaydeder.|
|[/ Run veya /r](../../ide/reference/run-devenv-exe.md)|Derler ve belirtilen çözüm çalıştırır.|
|[/Runexit](../../ide/reference/runexit-devenv-exe.md)|Derler ve belirtilen çözüm çalıştırır, çözüm çalıştırılır ve çözüm çalışması bittikten sonra IDE'yi kapatır, IDE'nin en aza indirir.|
|[/UseEnv](../../ide/reference/useenv-devenv-exe.md)|VC ++ dizinleri kısmında belirtilen ayarlara yerine C++ derlemesi için yol, Ekle ve kitaplığı ortam değişkenlerini kullanmak IDE neden **projeleri** seçeneklerini **seçenekleri** iletişim kutusu. Bu anahtar ile birlikte yüklenir **C++ ile masaüstü geliştirme** iş yükü. Daha fazla bilgi için [komut satırı derlemeleri için yolu ve ortam değişkenlerini ayarlama](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|
|[/Edit](../../ide/reference/edit-devenv-exe.md)|Belirtilen dosyalar, bu uygulamanın çalışan bir örneğini açar. Varsa çalışan örnek yoksa Basitleştirilmiş pencere düzenini ile yeni bir örneğini başlatır.|
|[/SafeMode](../../ide/reference/safemode-devenv-exe.md)|Visual Studio güvenli modda başlatır ve yalnızca varsayılan ortama ve hizmetler yükler ve üçüncü taraf paketi sürümlerini birlikte gönderilir.|
|[/ResetSkipPkgs](../../ide/reference/resetskippkgs-devenv-exe.md)|Sorun VSPackages yüklenmesini engellemek istediğiniz kullanıcılar tarafından Vspackages'a eklenmiş tüm SkipLoading etiketlerini temizler.|
|[/Setup](../../ide/reference/setup-devenv-exe.md)|Menüleri, araç çubukları ve komut grupları, kullanılabilir tüm VSPackages tanımlayan kaynak meta verileri birleştirmek için Visual Studio zorlar. Bu komutu yönetici olarak çalıştırmanız gerekir.|

Aşağıdaki komut satırı anahtarları IDE görüntülemez.

|Komut satırı anahtarı|Açıklama|
| - |-----------------|
|[/?](../../ide/reference/q-devenv-exe.md)|Devenv anahtarları için yardımı görüntüler **komut istemi penceresi**.<br /><br /> `devenv /?`|
|[/Build](../../ide/reference/build-devenv-exe.md)|Belirtilen çözüm veya projeyi yapılandırmasına göre belirtilen çözümü derler.<br /><br /> `devenv myproj.csproj /build`|
|[/Clean](../../ide/reference/clean-devenv-exe.md)|Kaynak dosyaları etkilemeden oluşturma komutu tarafından oluşturulan tüm dosyaları siler.<br /><br /> `devenv myproj.csproj /clean`|
|[/Deploy](../../ide/reference/deploy-devenv-exe.md)|Çözümleri yapılandırmasına bir dağıtım için gerekli dosyaları ile birlikte çözümü derler.<br /><br /> `devenv myproj.csproj /deploy`|
|[/Diff](../../ide/reference/diff.md)|İki dosyayı karşılaştırır. Dört parametre alır: Kaynakdosya, Hedefdosya, SourceDisplayName (isteğe bağlı), TargetDisplayName (isteğe bağlı).|
|[/Out](../../ide/reference/out-devenv-exe.md)|Oluşturma sırasında hatalar almak için bir dosya belirtmenizi sağlar.<br /><br /> `devenv myproj.csproj /build /out log.txt`|
|[/Project](../../ide/reference/project-devenv-exe.md)|Projeyi oluşturmak için temizlemek veya dağıtmak. Yalnızca / Build ayrıca sağladıysanız bu anahtarı kullanabilirsiniz. / rebuild, / clean veya / deploy anahtarı.|
|[/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)|Derleme veya dağıtım için proje yapılandırmasını belirtir. Yalnızca/Project anahtarı da sağladıysanız bu anahtarı kullanabilirsiniz.|
|[/Rebuild](../../ide/reference/rebuild-devenv-exe.md)|Temizler ve daha sonra belirtilen çözüm veya projeyi yapılandırmasına göre belirtilen çözümü derler.|
|[/ResetSettings](../../ide/reference/resetsettings-devenv-exe.md)|Visual Studio varsayılan ayarlarına geri yükler. İsteğe bağlı olarak belirtilen .vssettings dosya ayarlarını sıfırlar.|
|[/Upgrade](../../ide/reference/upgrade-devenv-exe.md)|Bu dosyalar için geçerli Visual Studio biçimlerinde belirtilen çözüm dosyasını ve tüm proje dosyaları ya da belirtilen proje dosyasını yükseltir.|

## <a name="see-also"></a>Ayrıca bkz.

* [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
