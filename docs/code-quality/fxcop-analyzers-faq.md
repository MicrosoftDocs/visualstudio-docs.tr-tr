---
title: FxCop kod analizi ve FxCop çözümleyicileri
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc04cbc6d46d8dc47a08d06c8c5949bb5d9107f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79431371"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>FxCop ve FxCop çözümleyicileri hakkında sık sorulan sorular

Eski FxCop ve FxCop çözümleyicileri arasındaki farkları anlamak biraz kafa karıştırıcı olabilir. Bu makalede, karşılaşabileceğiniz soruların bazılarını ele alabilirsiniz.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Eski FxCop ve FxCop çözümleyicileri arasındaki fark nedir?

Eski FxCop derleme sonrası analizini derlenmiş bir derlemede çalıştırır. **FxCopCmd.exe**olarak adlandırılan ayrı bir yürütülebilir dosya olarak çalışır. FxCopCmd.exe derlenen derlemeyi yükler, Kod analizini çalıştırır ve sonuçları (veya *tanılamayı*) raporlar.

FxCop çözümleyicileri .NET Compiler Platform ("Roslyn") temel alır. Bunları, proje veya çözüm tarafından başvurulan [bir NuGet paketi olarak yüklersiniz](install-fxcop-analyzers.md#nuget-package) . FxCop çözümleyicileri, derleyici yürütme sırasında kaynak kodu tabanlı analizler çalıştırır. FxCop çözümleyicileri derleyici işlemi içinde barındırılır, **csc.exe** veya **vbc.exe**ve proje oluşturulduğunda Analizi çalıştırır. Çözümleyici sonuçları derleyici sonuçlarıyla birlikte raporlanır.

> [!NOTE]
> [Visual Studio uzantısı olarak FxCop çözümleyicileri de yükleyebilirsiniz](install-fxcop-analyzers.md#vsix). Bu durumda, çözümleyiciler kod düzenleyicisine yazarken yürütülür, ancak derleme zamanında yürütülmez. FxCop çözümleyicileri 'ni sürekli tümleştirme (CI) kapsamında çalıştırmak istiyorsanız, bunları bir NuGet paketi olarak yükleyebilirsiniz.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Kod analizini Çalıştır komutu FxCop çözümleyicileri çalıştırmalıdır mi?

Visual Studio 2019 16,5 sürümünden önce, **Analyze**  >  **çalışma kodu analizini**Çözümle ' yi seçtiğinizde eski analiz yürütülür. Visual Studio 2019 16,5 başlatılıyor, **Kod Analizi Çalıştır** menü seçeneği, seçili proje veya çözüm Için Roslyn tabanlı Çözümleyicileri yürütür. Roslyn tabanlı FxCop çözümleyicileri yüklediyseniz, bunlar da yürütülür. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen kod Için kod analizini El Ile çalıştırma](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis MSBuild proje özelliği çözümleyiciler çalıştıranlar mı?

Hayır. Bir proje dosyasındaki **RunCodeAnalysis** özelliği (örneğin, *. csproj*) yalnızca eski FxCop yürütmek için kullanılır. **FxCopCmd.exe**çağıran bir oluşturma sonrası MSBuild görevi çalıştırır.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Bu nedenle, FxCop çözümleyicileri nasıl çalıştırılır?

FxCop çözümleyicileri 'ni çalıştırmak için önce bunlar için [NuGet paketini yüklemeniz](install-fxcop-analyzers.md) gerekir. Ardından, Visual Studio 'dan veya MSBuild kullanarak projenizi veya çözümünüzü oluşturun. FxCop çözümleyicileri tarafından oluşturulacak uyarılar ve hatalar **hata listesi** veya komut penceresinde görünür.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>FxCop çözümleyicileri NuGet paketini yükledikten sonra bile uyarı CA0507 alıyorum

FxCop analizlerini yüklediyseniz ve uyarı almaya devam ederseniz **, "" Kod analizini Çalıştır "özelliği derleme sırasında çalıştırılan FxCop çözümleyicileri lehçında kullanım dışı**bırakılmıştır, [proje dosyanızdaki](../ide/solutions-and-projects-in-visual-studio.md#project-file) **RunCodeAnalysis** MSBuild özelliğini **false**olarak ayarlamanız gerekebilir. Aksi halde, eski analiz her derlemeden sonra yürütülür.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>FxCop çözümleyicileri hangi kuralları kapsayan?

[FxCop](install-fxcop-analyzers.md)analizler 'e hangi eski analiz kurallarının oluşturulduğu hakkında daha fazla bilgi için bkz. [FxCop kuralı bağlantı noktası durumu](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Kod Analizi uyarıları hata olarak kabul edilir

Projeniz uyarıları hata olarak değerlendirmek için Build seçeneğini kullanıyorsa, FxCop Çözümleyicisi uyarıları hata olarak görünebilir. Kod Analizi uyarılarının hata olarak işlenmesine engel olmak için, [kod analizi hakkında SSS bölümündeki](../code-quality/analyzers-faq.md#treat-warnings-as-errors)adımları izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Compiler Platform çözümleyicilerine genel bakış](roslyn-analyzers-overview.md)
- [FxCop çözümleyicilerine geçiş yapma](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [FxCop çözümleyicilerini yükleme](install-fxcop-analyzers.md)
