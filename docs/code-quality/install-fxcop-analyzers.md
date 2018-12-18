---
title: FxCop çözümleyicilerini yükleme
ms.date: 08/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 7690d1c67797c3a13dc22364d93d8af686e4f90c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892057"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Visual Studio'da FxCop Çözümleyicileri yükleyin

Microsoft, bir dizi olarak adlandırılan Çözümleyicileri, oluşturulan [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), statik kod analizi için Roslyn Çözümleyicileri dönüştürülür, en önemli "FxCop" kuralları içerir. Bu çözümleyici kodunuzu güvenlik, performans ve diğerlerinin yanı sıra tasarım konularını inceleyin.

Bir NuGet paketi olarak veya Visual Studio bir VSIX uzantısı, bu FxCop Çözümleyicileri yükleyebilirsiniz. Artıları ve eksileri her biri hakkında bilgi edinmek için [NuGet paketi vs. VSIX uzantısı](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>FxCop Çözümleyicileri bir NuGet paketi olarak yüklemek için

1. [Hangi Çözümleyicisi paket sürümünü](#fxcopanalyzers-package-versions) yüklemek için Visual Studio sürümünüze bağlı.

2. Visual Studio kullanarak kullanarak paketi yükleyin [Paket Yöneticisi Konsolu](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) veya [Paket Yöneticisi UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Nuget.org sayfasında her bir çözümleyici paket yapıştırmak için komutu gösterir **Paket Yöneticisi Konsolu**. Metni panoya kopyalamak için kullanışlı bir düğme bile yoktur.
   >
   > ![NuGet.org sayfasında Paket Yöneticisi Konsolu komut gösteriliyor](media/nuget-package-manager-command.png)

   Çözümleyici bütünleştirilmiş kodlarının yüklenir ve görünürler **Çözüm Gezgini** altında **başvuruları** > **Çözümleyicileri**.

   ![Çözüm Gezgininde çözümleyiciler](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>FxCopAnalyzers paket sürümleri

Visual Studio sürümünüz için yüklenecek FxCop Çözümleyicileri paketini hangi sürümünü belirlemek için aşağıdaki yönergeleri kullanın:

| Visual Studio sürümü | FxCop Çözümleyicisi Paket sürümü |
| - | - |
| Visual Studio 2017 sürüm 15.5 ve üzeri | 2.6.2, örneğin https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2 |
| Visual Studio 2017 sürüm 15.3 için 15.4 | Örneğin, 2.3.0-Beta1 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1 |
| Visual Studio 2017 sürüm 15.0 için 15.2 | Örneğin, 2.0.0-Beta2 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2 |
| Visual Studio 2015 güncelleştirme 2 ve 3 | Örneğin, sürüm 1.2.0-beta2 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2 |
| Visual Studio 2015 Güncelleştirme 1 | Örneğin, 1.1.0 sürümü https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1. |
| Visual Studio 2015 RTW | Örneğin, 1.0.1 sürümü https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1 |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>FxCop Çözümleyicileri bir VSIX yüklemek için

Visual Studio 2017'de sürüm 15.5 ve üzeri yükleyebileceğiniz [Microsoft Kod Analizi 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) tüm FxCop Çözümleyicileri yönetilen projeler içeren bir uzantı.

1. Visual Studio'da **Araçları** > **Uzantılar ve güncelleştirmeler**.

   **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

   > [!NOTE]
   > Alternatif olarak, doğrudan uzantısını [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Genişletin **çevrimiçi** sol bölmesi ve ardından **Visual Studio Market**.

1. Arama kutusuna "Kod Analizi" yazın ve Ara **Microsoft Kod Analizi 2017** uzantısı.

   ![Microsoft Kod Analizi uzantısı](media/extensions-and-updates-code-analysis.png)

1. Seçin **indirme**.

   Uzantı yüklenir.

1. Seçin **Tamam** iletişim kutusunu kapatın ve ardından başlatmak için Visual Studio'nun tüm örneklerini kapatın **VSIX yükleyicisi**.

   **VSIX yükleyicisi** iletişim kutusu açılır.

   ![Microsoft Kod Analizi için VSIX yükleyicisi](media/vsix-installer-code-analysis.png)

1. Seçin **Değiştir** yüklemeyi başlatmak için.

1. Bir veya iki dakika sonra yükleme işlemini tamamlar. Seçin **Kapat**.

1. Visual Studio'yu yeniden açın.

Seçeneğini yüklü olup olmadığını ' uzantısı denetlemek istiyorsanız **Araçları** > **Uzantılar ve güncelleştirmeler**. İçinde **Uzantılar ve güncelleştirmeler** iletişim kutusunda, **yüklü** solda, kategori ve uzantısı adına göre arayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Roslyn çözümleyicilerini Visual Studio'da genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [Roslyn çözümleyicilerini Visual Studio'da kullanın](../code-quality/use-roslyn-analyzers.md)
- [Roslyn çözümleyicilerini FxCop geçiş](../code-quality/fxcop-analyzers.yml)