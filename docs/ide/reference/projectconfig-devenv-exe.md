---
title: DevEnv ProjectConfig anahtarı
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44f5d4479658b450074ba35f2759a273bb584e0a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764660"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Yapı, temizleme, yeniden oluşturun veya adlı projeyi dağıtmak uygulanacak bir proje derleme yapılandırmasını belirten **/project** bağımsız değişkeni.

## <a name="syntax"></a>Sözdizimi

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Arguments

|||
|-|-|
|/ BUILD|Tarafından belirtilen proje derlemeler **/project** bağımsız değişkeni.|
|/ clean|Tüm aracı dosyaları ve yapılandırma sırasında oluşturulan çıktı dizinleri temizler.|
|/ Rebuild|Temizler sonra tarafından belirtilen proje derlemeler **/project** bağımsız değişkeni.|
|/ deploy|Proje derleme veya yeniden sonra dağıtılması belirtir.|
|*SolnConfigName*|Gerekli. Adlı çözüm için uygulanan çözüm yapılandırmasının adı *SolutionName*. Birden çok çözüm platformu varsa de platform örneğin belirtmelisiniz **"hata ayıklama\|Win32"**.|
|*solutionName*|Gerekli. Tam yol ve çözüm dosyasının adı.|
|/ project *ProjName*|İsteğe bağlı. Yol ve çözüm içinde proje dosyasının adı. Gelen göreli bir yol girin *SolutionName* klasörü proje dosyası veya projenin görünen adı veya tam yolunu ve proje dosyasının adı.|
|/ projectconfig *ProjConfigName*|İsteğe bağlı. Bir proje adını derleme yapılandırması tarafından belirtilen proje uygulanacak **/project** bağımsız değişkeni. Birden çok çözüm platformu varsa de platform örneğin belirtmelisiniz **"hata ayıklama\|Win32"**.|

## <a name="remarks"></a>Açıklamalar

**/Projectconfig** anahtar kullanılan, ile **/project** geçiş parçası olarak bir **/build**, **/ temiz**,  **/rebuild**, veya **/ deploy** komutu.

Çift tırnak içine boşluk dizeler alın.

Komut penceresinde veya ile belirtilen herhangi bir günlük dosyasını derlemeleri hatalar dahil olmak üzere, ilgili özet bilgileri görüntülenebilir **/out** geçin.

## <a name="example"></a>Örnek

Aşağıdaki komutu proje "CSharpConsoleApp", "Hata ayıklama" proje derleme yapılandırmasını "MySolution" "Hata ayıklama" Çözüm yapılandırmasını içinde kullanılarak oluşturulur:

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/ Yapı (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ (Devenv.exe) dağıtma](../../ide/reference/deploy-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)