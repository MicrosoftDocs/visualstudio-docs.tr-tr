---
title: DevEnv Build anahtarı
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdd510e523aaabc468c1f01626593e51d0ad1558
ms.sourcegitcommit: 9571742f4a808c75b1034aa72fc24b54bc50692e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410968"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Belirtilen çözüm yapılandırma dosyası kullanarak bir çözüm oluşturur.

## <a name="syntax"></a>Sözdizimi

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Arguments

|||
|-|-|
|*SolutionName*|Gerekli. Çözüm dosyasının adını ve tam yolu.|
|*SolnConfigName*|Gerekli. Adlı çözümü derlemek için kullanılan çözüm yapılandırması adı *SolutionName*. Birden çok çözüm platformları kullanamıyorsanız, ayrıca platform örneğin belirtmelisiniz **"hata ayıklama\|Win32"**.|
|/ project *ProjName*|İsteğe bağlı. Çözüm içindeki bir proje dosyasının adı ve yolu. Göreli bir yol girebilirsiniz *SolutionName* klasör proje dosyası veya projenin görünen adı veya tam yolu ve proje dosyasının adı.|
|/ projectconfig *ProjConfigName*|İsteğe bağlı. Bir proje adı, adlandırılmış bir proje derlenirken kullanılacak yapılandırması oluşturun. Birden çok proje platformu varsa, aynı zamanda platforma, örneğin belirtmeniz gerekir **"hata ayıklama\|Win32"**.|

## <a name="remarks"></a>Açıklamalar

- **/Build** anahtarı ile aynı işlevi gerçekleştirir **Çözümü Derle** tümleşik geliştirme ortamında (IDE) menü komutu.

- Çift tırnak içine boşluk dizeleri alın.

- Komut penceresinde veya belirtilen herhangi bir günlük dosyasını hataları dahil olmak üzere, derlemeler için Özet bilgiler görüntülenebilir **/out** geçin.

- **/Build** geçiş yalnızca son derlemeden sonra değiştirilen projeleri oluşturur. Bir çözümdeki tüm projeleri oluşturmak için kullanın [/rebuild](../../ide/reference/rebuild-devenv-exe.md) yerine.

- Bildiren bir hata iletisi alırsanız **geçersiz proje yapılandırması**, çözüm platformu veya proje platformu, örneğin belirlediğiniz emin emin **"hata ayıklama\|Win32"**.

## <a name="example"></a>Örnek

Aşağıdaki komut, "CSharpConsoleApp", "MySolution", "Debug" çözüm yapılandırması içindeki "Debug" Proje yapı yapılandırmasını kullanarak projeyi oluşturur.

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Projeleri ve çözümleri oluşturma ve temizleme](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ (Devenv.exe out)](../../ide/reference/out-devenv-exe.md)