---
title: Nasıl yapılır gidiş geliş uzantıları
ms.date: 06/25/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: gregvanl
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 826089f1018bc6156cd49bab3afb19e7bb34a47d
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750738"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Nasıl yapılır: uzantıları Visual Studio 2017 ve Visual Studio 2015 ile uyumlu hale getirin

Bu belgede, genişletilebilirlik projeleri Visual Studio 2015 ve Visual Studio 2017 gidiş dönüş yapmak açıklanmaktadır. Bu yükseltme işlemini tamamladıktan sonra bir proje açın, derleme, yükleme ve Visual Studio 2015 ve Visual Studio 2017 ' çalıştırmak mümkün olacaktır. Bir başvuru, Visual Studio 2015 ve Visual Studio 2017 arasındaki gidiş dönüş yapabilen bazı uzantılar bulunabilir [VS SDK'sı genişletilebilirlik örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Daha sonra başvurmak yalnızca Visual Studio 2017'de derleme, ancak Visual Studio 2015 ve Visual Studio 2017 ' çalıştırmak için VSIX çıktısının yer almasını istiyorsanız [uzantısı dokumentu migrace](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> Sürümleri arasında Visual Studio'da değişiklikleri nedeniyle, başka bir sürümünde çalışan bazı şeyleri çalışmaz. Erişmeye çalıştığınız özellikler her iki sürümde de kullanılabilir uzantısına sahip olacaktır olduğundan emin olun veya beklenmeyen sonuçlar.

Anahat bir VSIX gidiş dönüşlü hale getirmek için bu belgedeki tamamlayacağınız gelişmiş adımlar aşağıda verilmiştir:

1. Doğru NuGet paketlerini içeri aktarın.
2. Uzantı bildirimi güncelleştirin:
    * Yükleme hedefi
    * Önkoşullar
3. CSProj güncelleştirin:
    * Güncelleştirme `<MinimumVisualStudioVersion>`.
    * Ekleme `<VsixType>` özelliği.
    * Hata ayıklama özelliği Ekle `($DevEnvDir)` 3 kez.
    * Derleme araçları ve hedefleri içeri aktarmaya yönelik koşullar ekleyin.

4. Derleme ve Test

## <a name="environment-setup"></a>Ortam Kurulumu

Bu belge, makinenizde yüklü olduğunu varsayar:

* VS yüklü SDK'sı ile Visual Studio 2015
* Genişletilebilirlik iş yükü yüklenmiş olan Visual Studio 2017

## <a name="recommended-approach"></a>Önerilen yaklaşım

Visual Studio 2015, Visual Studio 2017 yerine bu yükseltmeyi başlatmak için önerilir. Visual Studio 2015'te geliştirmenin ana avantajı, Visual Studio 2015'te kullanılabilir olmayan derlemelere başvurma sağlamaktır. Visual Studio 2017'deki geliştirme bunu yaparsanız, yalnızca Visual Studio 2017'de var olan bir derleme bağımlılığı yapabilecek riski yoktur.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Project.json başvuru olduğundan emin olun

Bu belgede daha sonra biz de koşullu içeri aktarma deyimlerini ekler, **.csproj* dosya.  NuGet başvurularınızı depolanıyorsa çalışmaz *project.json*. Bu nedenle, tüm NuGet başvurularını taşımanız önerilir *packages.config* dosya.
Projeniz varsa bir *project.json* dosyası:

* Başvuruları Not *project.json*.
* Gelen **Çözüm Gezgini**, silme *project.json* proje dosyası. Bu siler *project.json* dosya ve projeden kaldırır.
* NuGet başvuruları projeye geri ekleyin:
    * Sağ **çözüm** ve **çözüm için NuGet paketlerini Yönet**.
    * Visual Studio otomatik olarak oluşturur *packages.config* dosyayı.

> [!NOTE]
> Projenizi EnvDTE paketler içeriyorsa, bunlar sağ tıklanarak eklenmesi gerekebilir **başvuruları** seçerek **Başvurusu Ekle** ve uygun başvurusu ekleniyor.  NuGet paketlerini kullanarak projenizi çalışılırken hatalar oluşturabilir.

## <a name="add-appropriate-build-tools"></a>Uygun derleme araçları ekleme

Biz emin olmak için bize oluşturmak ve uygun şekilde hata ayıklama izin derleme araçları eklemeniz gerekir. Microsoft, bir derleme için bu çağrılan Microsoft.VisualStudio.Sdk.BuildTasks oluşturdu.

Yapı ve Visual Studio 2015 ve 2017 bir Vsıxv3 dağıtmak için aşağıdaki NuGet paketlerini gerektirir:

Sürüm | Yerleşik araçlar
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Bunu yapmak için:

* Microsoft.VisualStudio.Sdk.BuildTasks.14.0 NuGet paketini projenize ekleyin.
* Projenizi Microsoft.VSSDK.BuildTools içermiyorsa, bunu ekleyin.
* Microsoft.VSSDK.BuildTools sürüm 15.x olduğundan emin olun veya büyük.

## <a name="update-extension-manifest"></a>Güncelleştirme uzantı bildirimi

### <a name="1-installation-targets"></a>1. Yükleme hedefleri

Hangi sürümleri hedefleyen bir VSIX oluşturmak için Visual Studio söylemeniz gerekir.  Genellikle, bu başvuruları sürüm 14.0 (Visual Studio 2015) veya sürüm 15.0 (Visual Studio 2017) ' dir.  Bu örnekte, iki sürümünü hedefleyecek şekilde yüzden, bir uzantı her ikisi için de yükleyecek bir VSIX oluşturmak istiyoruz.  VSIX oluşturup 14.0'dan önceki sürümlerinde yüklemek istiyorsanız, bu önceki sürüm numarasını ayarlayarak gerçekleştirilebilir; Bununla birlikte, sürüm 10.0 ve önceki sürümleri artık desteklenmemektedir.

* Açık *source.extension.vsixmanifest* dosyasını Visual Studio'da.
* Açık **hedefleri Yükle** sekmesi.
* Değişiklik **sürüm aralığı** için [14.0, 16,0).  ' [', Geçmiş 14.0 ve tüm sürümleri dahil etmek için Visual Studio söyler.  ')' 15.0 kadar ancak sürüm 16,0 içermeyen tüm sürümlerini dahil etmek için Visual Studio söyler.
* Tüm değişiklikleri kaydedin ve Visual Studio'nun tüm örneklerini kapatın.

![Yükleme hedefleri görüntüsü](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Önkoşullar ekleme *extension.vsixmanifest* dosyası

Önkoşullar, Visual Studio 2017 ile yeni bir özelliktir.  Bu durumda, Visual Studio çekirdek Düzenleyicisi bir önkoşul olarak ihtiyacımız var. Visual Studio 2015 VSIX Tasarımcı yeni işlemez beri `Prerequisites` bölümünde bu bölümünde el ile XML kodunu düzenle gerekir.  Alternatif olarak, Visual Studio 2017'yi açın ve önkoşulları eklemek için güncelleştirilmiş bildirim Tasarımcısı'nı kullanın.

Bunu el ile yapmak için:

* Dosya Gezgini'nde proje dizinine gidin.
* Açık *extension.vsixmanifest* dosyasını bir metin düzenleyici.
* Aşağıdaki etiketi ekleyin:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Dosyayı kaydedin ve kapatın.

> [!NOTE]
> Visual Studio 2017'de VSIX Tasarımcısı ile bunu kullanmayı tercih ederseniz Visual Studio 2017'in tüm sürümleri ile uyumlu olduğundan emin olmak için önkoşul sürümü el ile düzenlemeniz gerekir.  Tasarımcı en düşük sürüm (örneğin, 15.0.26208.0) Visual Studio'nun geçerli sürümünüzü ekleyecek olmasıdır.  Ancak, diğer kullanıcıların daha önceki bir sürümü olabileceği el ile düzenlemeniz isteyeceksiniz 15.0 için.

Bu noktada, bildirim dosyanız aşağıdakine benzer görünmelidir:

![Önkoşullar örneği](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Proje dosyası (myproject.csproj) değiştirme

Bu adımı yaparken açık olan bir değiştirilmiş .csproj başvuru olması önerilir.  Bazı örnekler bulabilirsiniz [burada](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Herhangi bir genişletilebilirlik örnek seçin, Bul *.csproj* dosya başvurusu için ve aşağıdaki adımları uygulayın:

* Proje dizininde gidin **dosya Gezgini**.
* Açık *myproject.csproj* dosyasını bir metin düzenleyici.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Güncelleştirme MinimumVisualStudioVersion

* En düşük visual studio sürümü kümesine `$(VisualStudioVersion)` ve bunun için bir koşullu ifade ekleyin.  Bunlar yoksa, bu etiketler ekleyin.  Etiketler aşağıdaki gibi ayarlandığından emin olun:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. VsixType özelliği ekleyin.

* Aşağıdaki etiketi Ekle `<VsixType>v3</VsixType>` özellik grubuna.

> [!NOTE]
> Bu eklemek için önerilen aşağıda `<OutputType></OutputType>` etiketi.

### <a name="3-add-the-debugging-properties"></a>3. Hata ayıklama özellikleri ekleyin

* Aşağıdaki özellik grubu ekleyin:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Aşağıdaki kod örneği tüm örneklerini silmek *.csproj* dosya ve *. csproj.user* dosyaları:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Derleme araçları içeri aktarmalara koşulları ekleme

* İçin ek koşul deyimlerini ekleyin `<import>` Microsoft.VSSDK.BuildTools başvurusuna sahip etiketler.  INSERT `'$(VisualStudioVersion)' != '14.0' And` önündeki koşul deyimi.  Bu deyimler, üstbilgi ve altbilgi csproj dosyasının görünür.

Örneğin:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* İçin ek koşul deyimlerini ekleyin `<import>` bir Microsoft.VisualStudio.Sdk.BuildTasks.14.0 sahip etiketler. INSERT `'$(VisualStudioVersion)' == '14.0' And` önündeki koşul deyimi. Bu deyimler, üstbilgi ve altbilgi csproj dosyasının görünür.

Örneğin:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* İçin ek koşul deyimlerini ekleyin `<Error>` Microsoft.VSSDK.BuildTools başvurusuna sahip etiketler.  Ekleyerek bunu `'$(VisualStudioVersion)' != '14.0' And` önündeki koşul deyimi. Bu deyimler csproj dosyasının alt bilgiden görünür.

Örneğin:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* İçin ek koşul deyimlerini ekleyin `<Error>` bir Microsoft.VisualStudio.Sdk.BuildTasks.14.0 sahip etiketler.  INSERT `'$(VisualStudioVersion)' == '14.0' And` önündeki koşul deyimi. Bu deyimler csproj dosyasının alt bilgiden görünür.

Örneğin:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Csproj dosyasını kaydedin ve kapatın.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Visual Studio 2015 ve Visual Studio 2017 uzantı yüklemeleri test

Bu noktada, projenizi Visual Studio 2015 ve Visual Studio 2017'yi yükleyebilmek için bir Vsıxv3 derlemek için hazır olması gerekir.

* Projenizi Visual Studio 2015'te açın.
* Projenizi derleyin ve onaylayın çıktıda bir VSIX doğru şekilde oluşturur.
* Proje dizininize gidin.
* Açık *\bin\Debug* klasör.
* VSIX dosyasına çift tıklayın ve uzantınızın Visual Studio 2015 ve Visual Studio 2017'yi yükleyin.
* Uzantı görebildiğinizden emin olun **Araçları** > **Uzantılar ve güncelleştirmeler** içinde **yüklü** bölümü.
* Çalıştır/çalışıp çalışmadığını denetlemek için uzantıyı kullanmak çalışır.

![Bir VSIX Bul](media/finding-a-VSIX-example.png)

> [!NOTE]
> Projenizi iletisiyle yanıt vermemeye başlıyor, **dosyayı açmayı**zorla Visual Studio'yu kapatın, proje dizinine gidin, gizli klasörlere Göster ve Sil *.vs* klasör.