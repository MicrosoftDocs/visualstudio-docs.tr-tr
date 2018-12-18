---
title: "Nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2017'ye geçirme | Microsoft Docs"
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 195d63e5ddb8b8536c1d0c1c4197270f5b3aa508
ms.sourcegitcommit: 331dbb12e11fcd7f5d15fab05f3c861e48126e43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51826823"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2017'ye geçirme

Bu belgede, genişletilebilirlik projelerini Visual Studio 2017'ye yükseltme açıklanmaktadır. Proje dosyaları güncelleştirilmeye nasıl açıklayan ek olarak, bu da yeni sürüm 3 VSIX bildirim biçimi için (VSIX v3) uzantı bildirim sürümünden 2 (VSIX v2) yükseltmek nasıl açıklar.

## <a name="install-visual-studio-2017-with-required-workloads"></a>Visual Studio 2017 gerekli iş yükleri ile yükleyin.

Aşağıdaki iş yükleri yüklemenizi içerdiğinden emin olun:

* .NET masaüstü geliştirme
* Visual Studio uzantısı geliştirme

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Visual Studio 2017'de VSIX çözümü açın

Tüm VSIX projeleri Visual Studio 2017 sürüm tek yönlü yükseltme gerektirir.

Proje dosyası (örneğin **.csproj*) güncelleştirilir:

* MinimumVisualStudioVersion - 15.0 için şimdi ayarlayın
* OldToolsVersion (, daha önce mevcut)-14.0 için şimdi ayarlayın

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Microsoft.VSSDK.BuildTools NuGet paketini güncelleştir

>**Not:** çözümünüzü Microsoft.VSSDK.BuildTools NuGet paketini başvurmuyorsa bu adımı atlayabilirsiniz.

Uzantınızı yeni VSIX v3'te oluşturmak için (sürüm 3) biçimi, çözümünüzü yeni VSSDK derleme araçları ile oluşturulması gerekir. Uzantınızı VSIX v2 NuGet aracılığıyla daha eski bir sürüme bir başvuru tutan ancak bu Visual Studio 2017 ile yüklenir. Bu durumda, çözümünüzün Microsoft.VSSDK.BuildTools NuGet paketinin bir güncelleştirmeyi el ile yüklemeniz gerekir.

Microsoft.VSSDK.BuildTools NuGet başvurularını güncelleştirmek için:

* Çözüme sağ tıklayın ve seçin **çözüm için NuGet paketlerini Yönet**.
* Gidin **güncelleştirmeleri** sekmesi.
* Seçin **Microsoft.VSSDK.BuildTools (en son sürüm)**.
* Tuşuna **güncelleştirme**.

![VSSDK derleme araçları](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>VSIX uzantı bildirimi için değişiklik yapma

Kullanıcının yükleme Visual Studio Uzantısı'nı çalıştırmak için gerekli tüm bütünleştirilmiş kodlara sahip olmak için tüm önkoşul bileşenleri veya paketler uzantı bildirim dosyası belirtin. Bir kullanıcı, uzantıyı yüklemeye çalıştığında Vsıxınstaller tüm önkoşulların yüklü olup olmadığını kontrol eder. Bazı eksikse, eksik bileşenleri uzantı yükleme işleminin bir parçası yüklemek için kullanıcı istenir.

>**Not:** en azından tüm uzantılar Visual Studio çekirdek Düzenleyicisi bileşenini bir önkoşul olarak belirtmeniz gerekir.

* Uzantı bildirim dosyası Düzenle (genellikle adlı *source.extension.vsixmanifest*).
* Olun `InstallationTarget` 15.0 içerir.
* Gerekli yükleme önkoşulları (aşağıdaki örnekte gösterildiği gibi) ekleyin.
  * Yalnızca bileşen kimlikleri için yükleme önkoşulları belirlemek öneririz.
  * Bu belgenin sonuna bakın [belirleme Bileşen kimlikleri yönergeleri](#find-component-ids).

Örnek:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Seçenek: değişiklik için VSIX uzantısı bildirim Tasarımcısı'nı kullanın

Bildirim XML doğrudan düzenlemek yerine yeni kullanabileceğiniz **önkoşulları** sizin için sekmesinde önkoşulları seçmek için bildirim Tasarımcısı ve XML güncelleştirilir.

>**Not:** bildirim Tasarımcısı yalnızca geçerli Visual Studio örneğinde yüklü bileşenleri (iş yükleri veya paketleri) seçmenizi sağlayacak. Bir iş yükü, paket veya şu anda yüklü olmayan bir bileşen için bir önkoşul eklemeniz gerekiyorsa, XML bildirimi doğrudan düzenleyin.

* Açık *source.extension.vsixmanifest [Design]* dosya.
* Seçin **önkoşulları** sekmesi ve ENTER tuşuna **yeni** düğmesi.

  ![VSIX bildirim Tasarımcısı](media/vsix-manifest-designer.png)

* **Yeni önkoşul ekleme** penceresi açılacaktır.

  ![VSIX önkoşul Ekle](media/add-vsix-prerequisite.png)

* İçin açılan listeyi tıklatın **adı** ve istenen önkoşul seçin.
* Gerekli sürüme güncelleştirin.

  >Not: Sürüm alanı bir aralığı kadar kapsayan (ancak değil de dahil olmak üzere) ile yüklü bileşen sürümü ile önceden doldurulur sonraki ana sürümünden bileşen.

  ![roslyn önkoşul Ekle](media/add-roslyn-prerequisite.png)

* Tuşuna **Tamam**.

## <a name="update-debug-settings-for-the-project"></a>Projenin hata ayıklama ayarlarını güncelleştirme

Visual Studio'nun Deneysel örneğindeki uzantınızın hatalarını ayıklamak isterseniz emin olun ilişkin proje ayarlarını **hata ayıklama** > **başlangıç eylemi** sahip **dış Başlat Program:** değerine *devenv.exe* Visual Studio 2017 yüklemenizi dosyası.

Gibi görünebilir: *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![Harici program Başlat](media/start-external-program.png)

>**Not:** hata ayıklama başlatma eylemi genellikle depolanan *. csproj.user* dosya. Bu dosya genellikle yer aldığı *.gitignore* dosya ve bu nedenle, normal olarak kabul edilen kaynak denetimine diğer proje dosyaları ile kaydedilmez. Bu nedenle, kaynak denetiminden yeni çözümünüzü aldıysanız proje başlangıç eylemi için hiçbir değer olacaktır olma olasılığı yüksektir. Visual Studio 2017 ile oluşturulan yeni VSIX projeleri sahip olacak bir *. csproj.user* geçerli Visual Studio yükleme dizinini işaret varsayılanları ile oluşturulan dosya. Bir VSIX v2 uzantısı geçiriyorsanız, ancak olasıdır, *. csproj.user* dosya önceki Visual Studio sürüme ait yükleme dizini için başvurular içerir. Değeri ayarlanırken **hata ayıklama** > **başlangıç eylemi** uzantınızı hatasını ayıklamaya çalıştığınızda başlatmak doğru Visual Studio deneysel örneğinde izin verir.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Uzantı düzgün (bir VSIX v3) derlemeleri denetleme

* VSIX projesi oluşturun.
* Oluşturulan VSIX sıkıştırmasını açın.
  * Varsayılan olarak, VSIX dosyasını yaşadığı içinde *bin/Debug* veya *bin/yayın* olarak *[YourCustomExtension] .vsix*.
  * Yeniden adlandırma *.vsix* için *.zip* kolayca içeriğini görüntüleyin.
* Üç dosyayı varlığını denetleyin:
  * *Extension.vsixmanifest*
  * *bazıları manifest.JSON*
  * *catalog.JSON*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Tüm gerekli Önkoşullar yüklendi denetimi

VSIX gereken tüm önkoşulları yüklü bir makinede başarıyla yükler. test edin.

>**Not:** uzantıyı yüklemeden önce lütfen Visual Studio'nun tüm örneklerini kapatın.

Uzantıyı yüklemek çalışır:

* Visual Studio 2017'de

![Visual Studio 2017'de VSIX yükleyicisi](media/vsixinstaller-vs-2017.png)

* İsteğe bağlı: Visual Studio'nun önceki sürümlerini kontrol edin.
  * Geriye dönük uyumluluk kanıtlar.
  * Çalışmalıdır Visual Studio 2012, Visual Studio 2013, Visual Studio 2015 için.
* İsteğe bağlı: Onay, VSIX yükleyicisi sürüm denetleyicisi sürümlerinin bir seçenek sunar.
  * Visual Studio'nun önceki sürümleri (yüklüyse) içerir.
  * Visual Studio 2017'yi içerir.

Visual Studio kısa bir süre önce açıldı, bu gibi bir iletişim kutusu görebilirsiniz:

![çalışan işlemlerin bir karşılaştırması](media/vs-running-processes.png)

Kapatmak işlemler için bekleyin veya görevleri el ile bitmelidir. Listelenen adı veya PID'si parantez içinde listelenen işlemleri bulabilirsiniz.

>**Not:** Visual Studio'nun bir örneğinde çalışırken bu işlemleri otomatik olarak kapatılacak değil. Makinede - diğer kullanıcıların dahil olmak üzere Visual Studio'nun tüm örneklerini kapatın sonra yeniden denemeye devam emin olun.

## <a name="check-when-missing-the-required-prerequisites"></a>Gerekli Önkoşullar eksik olduğunda denetleyin

* Uzantı bir makinede Visual Studio 2017, olmadığı içeren Önkoşullarda (yukarıda) tanımlanan tüm bileşenleri yüklenmeye çalışıldı.
* Yükleme eksik Bileşen/sn tanımlar ve bunları bir önkoşul olarak Vsıxınstaller listeler denetleyin.
* Not: ön koşulları uzantısıyla yüklenmesi gerekiyorsa ayrıcalık gerekli olacaktır.

![vsıxınstaller önkoşulu eksik](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Bileşenleri karar verin

Bağımlılıklarınızı baktığımda, bir bağımlılık için birden çok bileşen eşleyebilirsiniz bulacaksınız. Hangi bağımlılıklar, önkoşul olarak belirttiğiniz öneririz Uzantınız için benzer bir işlevsellik olan bileşen seçin ve ayrıca, kullanıcılarınızın ve bileşenleri hangi türde olur dikkate almanız için bunlar büyük olasılıkla yüklü belirlemek için veya Yükleme sorun mıydı. Ayrıca belirli varsa bileşenleri algılanmadı etkinliği olmayan olması uzantılarınızı burada uzantınızı çalışmasına izin veren en düşük gerekli önkoşulları karşılayan bir şekilde ve ek özellikler için sahip yapı öneririz.

Ek rehberlik için ortak olan birkaç uzantı türleri ve bunların önerilen Önkoşullar belirledik:

Uzantı türü | Görünen ad | Kimliği
--- | --- | ---
Düzenleyici | Visual Studio temel Düzenleyicisi  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# ve Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Yönetilen masaüstü iş yükü Çekirdeği | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Hata Ayıklayıcısı | Just-In-Time hata ayıklayıcı | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Bileşen kimliklerini bulun

Visual Studio ürün tarafından sıralanan bileşenlerin listesini altındadır [Visual Studio 2017 iş yükü ve Bileşen kimlikleri](https://aka.ms/vs2017componentIDs). Bu bileşeni kimliklerinin önkoşul kimliklerinizi bildiriminizdeki kullanın.

Hangi bileşenin belirli bir ikili içeren emin değilseniz, indirme [bileşen ikili eşleme elektronik tablosunu ->](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Excel tablosunda dört sütun vardır: **bileşen adı**, **ComponentId**, **sürüm**, ve **ikili / dosya adları**.  Arama ve belirli bileşenler ve ikili dosyaları bulmak için filtreleri kullanabilirsiniz.

Tüm başvuruları için ilk olarak, hangilerinin çekirdek Düzenleyici (Microsoft.VisualStudio.Component.CoreEditor) bileşeni olduğunu belirleyin.  En az çekirdek Düzenleyicisi bileşenini tüm uzantılar için bir önkoşul olarak belirtilmesi zorunlu kılarız. Çekirdek Düzenleyicisi'nde olmayan bırakılan başvuruları, filtre eklemesine **ikili dosyaları / dosya adlarını** bölümü herhangi bir alt kümesine ilişkin bu başvuruları bileşenleri bulunamadı.

Örnekler:

* Hata ayıklayıcı uzantısına sahiptir ve projenize bir başvuru olduğunu bildiğiniz *VSDebugEng.dll* ve *VSDebug.dll*, filtre düğmesine tıklayın **ikili dosyaları / dosya adlarını**başlığı.  "VSDebugEng.dll" için arama yapın ve seçin *Tamam*.  Ardından filtre düğmesine tıklayın **ikili dosyaları / dosya adlarını** yeniden başlığı ve "VSDebug.dll" arayın.  Onay kutusunu işaretleyin **geçerli seçimi filtreye Ekle** seçip **Tamam**.  Şimdi Ara **bileşen adı** en çok bir bileşen bulmak için uzantı türünüz için ilgili. Bu örnekte, Just-ın-Time seçtiğiniz hata ayıklayıcı ve için vsixmanifest ekleyin.
* Projenizin hata ayıklayıcı öğeleri ile anlaştığından emin biliyorsanız, "adında hata ayıklayıcı hangi bileşenleri içeren görmek için hata ayıklayıcı" Filtre Arama kutusuna arama yapabilirsiniz.

## <a name="specify-a-visual-studio-2017-release"></a>Visual Studio 2017 sürüm belirtin

Uzantınızı Visual Studio 2017'in belirli bir sürüm gerektirir, örneğin, 15.3 sürümünde kullanıma sunulan bir özelliği bağımlı, VSIX'İNİZE derleme numarasını belirtmelisiniz **InstallationTarget**. Örneğin, bir derleme sayısı '15.0.26730.3' sürüm 15.3 vardır. Yapı numaralarını sürümlerinin eşleme gördüğünüz [burada](../install/visual-studio-build-numbers-and-release-dates.md). Sürüm numarasını '15.3' kullanarak düzgün çalışmaz.

Uzantınızı 15.3 gerektirir ya da üzeri bildirirsiniz **InstallationTarget sürüm** olarak [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
