---
title: Sorun giderme ve bilinen sorunlar (Unity için Visual Studio Araçları) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 1c69c78e9a081680c6ee5279ddce1816bf500672
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027295"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Sorun giderme ve bilinen sorunlar (Unity için Visual Studio Araçları)

Bu bölümde, bilinen sorunların açıklamalarını Unity için Visual Studio Araçları ile sık karşılaşılan sorunlara çözümler bulmak ve Unity için Visual Studio Araçları hata bildirimi tarafından geliştirilmesine nasıl yardımcı olabileceğini öğrenin.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Unity ve Visual Studio arasında bağlantı sorunlarını giderme

### <a name="confirm-editor-attaching-is-enabled"></a>Düzenleyici ekleme etkin onaylayın

Unity menüde **Düzenle > Tercihler** seçip **dış Araçlar** sekmesi. Onaylayın **Düzenleyici ekleme** onay kutusunu etkin. Daha fazla bilgi için [Unity tercihleri belgeleri](https://docs.unity3d.com/Manual/Preferences.html).

### <a name="unable-to-attach"></a>İliştirme başarısız

- VS ve Unity için hariç tutma kuralları oluşturun veya geçici olarak virüsten koruma devre dışı bırakmak deneyin.
- Geçici olarak güvenlik duvarını devre dışı bırakın veya TCP/UDP ağ Unity VS arasındaki vermeye yönelik kuralları oluşturma deneyin.
- Teamviewer gibi bazı programlar Algılama işlemi engelleyebilir. Bir şey değiştiğinde olursa görmek için herhangi bir ek yazılımın geçici olarak durdurmak deneyebilirsiniz.
- VSTU yalnızca "Unity.exe" işlemleri izleme gibi temel Unity yürütülebilir dosyasını yeniden adlandırmayın.

## <a name="visual-studio-crashes"></a>Visual Studio kilitleniyor

Bu sorun, Visual Studio MEF önbelleği bozuk nedeniyle olabilir.

MEF önbelleği (Kapat bunu yapmadan önce VisualStudio) sıfırlamak için şu klasörü kaldırmayı deneyin:

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Bu sorunu çözer. Sorun yaşamaya durumunda, yönetici olarak Visual Studio için geliştirici Komut İstemi'ni çalıştırın ve aşağıdaki komutu kullanın:

```batch
 devenv /setup
```

## <a name="visual-studio-hangs"></a>Visual Studio yanıt vermemeye başlıyor

Ayrıştırma, FMOD, ZNEYİ (Evrensel Media Player), ZFBrowser veya katıştırılmış tarayıcı gibi çok sayıda Unity eklenti yerel iş parçacığı kullanmaktadır. Bir eklenti sonra işletim sistemi engelleme çağrıları yapan çalışma zamanı, yerel bir iş parçacığı ekleme yukarı sona erdiğinde bir sorundur. Unity hata ayıklayıcı (veya etki alanı yeniden yükle) için iş parçacığı kesme ve bağlantıyı anlamına gelir.

FMOD, geçici bir çözüm yoktur, geçirebilirsiniz `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` başlatma [bayrağı](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) zaman uyumsuz işleme devre dışı bırakabilir ve tüm işlemleri ana iş parçacığı üzerinde gerçekleştirin.

## <a name="incompatible-project-in-visual-studio"></a>Visual Studio uyumlu proje

İlk olarak, Visual Studio Unity (tercihleri/düzenleme/dış araçları) düzenleyiciniz dış betik olarak ayarlandığından emin olun. Ardından Visual Studio eklentisi içinde Unity yüklenip yüklenmediğini denetleyin (Yardım/hakkında Unity için Visual Studio Araçları Microsoft altındaki etkin gibi bir ileti görüntüler gerekir). Ardından uzantısı düzgün bir şekilde Visual Studio'da (Yardım/hakkında) yüklenip yüklenmediğini denetleyin.

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Ek yeniden yükler ve tüm açık pencereleri kaybetme Visual Studio

Hiçbir zaman doğrudan bir varlık işlemci veya herhangi bir aracı konumundan proje dosyaları touch emin olun. Proje dosyasını işlemek gerçekten ihtiyacınız varsa, bir API için kullanıma sunuyoruz. Lütfen denetleyin [derlemeye başvuran sorunları bölümüne](#Assembly-reference-issues).

Ek yüklemelere karşılaşırsanız veya Visual Studio kaybetme tüm açık Windows üzerinde yeniden yüklemek, doğru .NET hedefleme paketlerinin yüklü olduğundan emin olun. Çerçeveleri daha fazla bilgi için ilgili aşağıdaki bölüme bakın.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Hata ayıklayıcı özel durumları kesmez

İşlenmeyen bir özel durum olduğunda hata ayıklayıcı eski Unity çalışma zamanı (.NET 3.5 eşdeğeri) kullanırken, her zaman keser (= bir try/catch bloğu dışında). Özel durumun işlenip, hata ayıklayıcı bir kesme gerekli olup olmadığını belirlemek için özel durum Ayarları penceresi kullanacak.

Yeni çalışma zamanı (.NET 4.6 eşdeğeri), kullanıcı özel durumlarını yönetmek için yeni bir yolunu Unity sunulan ve bir try/catch bloğu dışında olsalar bile, sonuç olarak, tüm özel durumları "kullanıcı işlenen" görülür. İşte bu nedenle şimdi açıkça bunları denetleyin özel durum Ayarları penceresi hata ayıklayıcının istiyorsanız gerekir.

Özel durum Ayarları penceresinde (hata ayıklama > Windows > özel durum ayarları), (örneğin, ortak dil çalışma zamanı .NET özel anlamı özel durumları,) özel durumlar kategorisi için düğümü genişletin ve istediğiniz belirli özel durum için onay kutusunu işaretleyin Bu kategoride (örneğin System.NullReferenceException) yakalayın. Bir tüm özel durumlar kategorisi belirleyebilirsiniz.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Windows üzerinde Visual Studio Unity hedef Framework'ü indirmek sorar.

Unity için Visual Studio Araçları varsayılan olarak, Windows 8 ya da 10 yüklü değilse .NET framework 3.5 gerektirir. Bu sorunu gidermek için indirmek ve .NET framework 3.5 yüklemek için yönergeleri izleyin.

Yeni Unity çalışma zamanı kullanırken, .NET hedefleme paketlerini sürümü 4.6 ve 4.7.1 de gerekli. VS2017 Yükleyicisi (VS2017 yükleme, tek tek bileşenler, .NET kategorisi, select hedefleme paketlerinin tüm 4.x değiştirin) hızlı bir şekilde yüklemek için kullanmak mümkündür.

## <a name="assembly-reference-issues"></a>Bütünleştirilmiş kod başvurusu konuları

Projenizi reference-wise karmaşık ise veya bu nesil adım daha iyi denetlemek istiyorsanız, kullanabileceğiniz bizim [API](../cross-platform/customize-project-files-created-by-vstu.md) oluşturulan proje veya çözüm içeriği düzenlemek için. Ayrıca [yanıt dosyaları](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) içinde Unity proje ve bunları işlemeniz.

## <a name="breakpoints-with-a-warning"></a>Bir uyarı kesme noktaları

Visual Studio, belirli bir kesme noktası için kaynak konumu bulamıyor ise, kesme noktası bir uyarı görürsünüz. Kullanmakta olduğunuz kodun düzgün bir şekilde yüklendi/geçerli Unity sahnede kullanılan olup olmadığını denetleyin.

## <a name="breakpoints-not-hit"></a>Kesme noktaları isabet değil

Kullanmakta olduğunuz kodun düzgün bir şekilde yüklendi/geçerli Unity sahnede kullanılan olup olmadığını denetleyin. Hem Visual Studio ve Unity çıkmak sonra oluşturulan tüm dosyaları silin (\*.csproj, \*.sln) ve tüm kitaplık klasörü.

## <a name="unable-to-debug-android-players"></a>Android oynatıcılarda hata ayıklaması yapılamıyor

Çok noktaya yayın kullanırız (olan Unity tarafından kullanılan varsayılan bir mekanizma) player algılama, ancak bundan sonra normal TCP bağlantısı eklemek için kullanırız. Android cihazları için ana sorunu algılama aşamasıdır.

WiFi USB gecikme nedeniyle karşılaştırıldığında çok yönlü ancak Süper yavaş değildir. Bazı yönlendiriciler veya cihazları (Bunun için bilinen Nexus serisi) için uygun çok noktaya yayın desteği eksikliği gördük.

USB hata ayıklama için süper hızlı çalışır ve Unity için Visual Studio Araçları artık USB cihazları algılamak ve hata ayıklama için bağlantı noktalarını düzgün bir şekilde iletmek üzere adb sunucusu konuşun.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Visual Studio 2015 ve IntelliSense veya kod coloration ile ilgili sorunlar

Güncelleştirme 3 için Visual Studio 2015 ', yükseltmeyi deneyin.

## <a name="known-issues"></a>Bilinen sorunlar

 Bilinen sorunlar vardır, hata ayıklayıcı Unity'nın daha eski C# Derleyici sürümü ile nasıl etkileştiğini gelen neden Visual Studio Araçları Unity için. Bu sorunları çözmek için çalışıyoruz ancak bu sırada aşağıdaki sorunlarla karşılaşabilirsiniz:

- Hata ayıklama sırasında Unity bazen kilitleniyor.

- Unity bazen hata ayıklama sırasında donuyor.

- İçine ve dışına yöntemleri bazen Adımlama özellikle yineleyiciler veya switch deyimleri içinde yanlış bir şekilde davranır.

## <a name="report-errors"></a>Rapor hataları

 Lütfen kilitlenen, donuyor veya diğer hatalarla karşılaşırsanız, hata raporları göndermek kalite Unity için Visual Studio Araçları'nın geliştirmemize yardımcı olun. Bu, bize araştırmak ve Unity için Visual Studio Araçları'ndaki sorunları gidermeye yardımcı olur. Teşekkür ederiz!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Visual Studio donuyor olduğunda bir hata bildirme

 Visual Studio bazen Unity için Visual Studio Araçları ile hata ayıklama sırasında donuyor raporlar vardır, ancak bu sorunu anlamak için daha fazla veriye ihtiyacımız. Bize aşağıdaki adımları izleyerek araştırmanıza yardımcı olabilir.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Visual Studio Unity için Visual Studio Araçları ile hata ayıklama sırasında donuyor bildirmek için

*Windows üzerinde:*

1. Visual Studio'nun yeni bir örneğini açın.

1. İşleme İliştir'iletişim kutusunda açın. Yeni Visual Studio örneğinde ana menüsündeki seçin **hata ayıklama**, **iliştirme**.

1. Hata ayıklayıcı, Visual Studio dondurulmuş örneğine ekleyin. İçinde **iliştirme** iletişim kutusunda, Visual Studio'dan dondurulmuş örneğini seçin **kullanılabilir işlemler** tablosuna ve sonra seçin **iliştirme** düğmesi.

1. Hata ayıklayıcı duraklatın. Yeni Visual Studio örneğinde ana menüsündeki seçin **hata ayıklama**, **tümünü Kes**, veya tuşuna basarak **Ctrl + Alt + Break**.

1. Bir iş parçacığı dökümü oluşturun. Komut penceresinde komut enter tuşuna basarak aşağıdaki **Enter**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Yapmanız gerekebilecek **komut** pencere ilk görünür. Visual Studio'da ana menüde seçin **görünümü**, **diğer Windows**, **komut penceresi**.

*Mac bilgisayarda:*

1. Bir terminal açın ve Mac için PID Visual Studio'nun alın:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Lldb hata ayıklayıcıyı başlatın:

    ```shell
    lldb
    ```

1. PID kullanarak Mac örneği için Visual Studio ekleme:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Stacktrace için tüm iş parçacıkları alın:

    ```shell
    bt all
    ```

Son olarak, iş parçacığı-dökümü gönderme [ vstusp@microsoft.com ](mailto:vstusp@microsoft.com), ne zaman yapmakta olduğunuz açıklaması ile birlikte Visual Studio dondurulmuş hale geldi.
