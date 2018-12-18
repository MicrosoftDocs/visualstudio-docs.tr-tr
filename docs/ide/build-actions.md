---
title: Derleme dosyaları için eylemleri
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5eb4c000973afd1eef92d283e5688862413add16
ms.sourcegitcommit: f61ad0e8babec8810295f039e67629f4bdebeef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "52001782"
---
# <a name="build-actions"></a>Derleme eylemleri

Tüm Visual Studio proje dosyalarında derleme eylemine sahip. Derleme eylemi, proje derlendiğinde dosyanın için ne denetler.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [derleme Mac için Visual Studio'da işlemleri](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Bir derleme eylemi

Bir dosyanın derleme eylemi ayarlamak için dosyanın özelliklerinde açın **özellikleri** dosyasında seçerek penceresi **Çözüm Gezgini** tuşuna basarak **Alt** + **Girin**. Veya dosyayı sağ **Çözüm Gezgini** ve **özellikleri**. İçinde **özellikleri** penceresinin altında **Gelişmiş** bölümünde, aşağı açılan listenin yanındaki kullanın **derleme eylemi** dosyası için derleme eylemine ayarlamak için.

![Visual Studio'da dosya oluştur](media/build-actions.png)

## <a name="build-action-values"></a>Eylem değerlerini oluşturma

İçin derleme eylemlerin bazıları C# ve Visual Basic proje dosyaları:

* **Hiçbiri** -dosyası herhangi bir şekilde oluşturma işleminin bir parçası değil. Bu değer "Benioku" dosyaları gibi belge dosyaları için örneğin kullanılabilir.
* **Derleme** -dosya derleyici kaynak dosyası olarak geçirilir.
* **İçerik** -bir dosya olarak işaretlenmiş **içerik** çağırarak bir akış olarak alınabilir <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. Dağıtıldığında ASP.NET projeleri için bu dosyalar sitenin bir parçası olarak dahil edilir.
* **Katıştırılmış kaynak** -dosya, derleyiciye derleme içine gömülü olması için bir kaynak olarak geçirilir. Çağırabilirsiniz <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> derlemeden dosyası okunamıyor.
* **AdditionalFiles** -geçirilen kaynak olmayan metin dosyası C# veya Visual Basic derleyicisine giriş olarak. Bu yapı eylemi girişleri sağlamak için çoğunlukla kullanılır [Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md) kod kalitesini doğrulamak için bir proje tarafından başvurulan. Daha fazla bilgi için [ek dosyaları kullanma](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#Derleyici Seçenekleri](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Visual Basic derleyici seçenekleri](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Derleme eylemleri (Mac için Visual Studio)](/visualstudio/mac/build-actions)