---
title: Yönetilen kod için statik kod analizi
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 96f00e6080cb10778a92aaa860422da8366be54d
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389318"
---
# <a name="overview-of-static-code-analysis-for-managed-code-in-visual-studio"></a>Visual Studio'da yönetilen kod için statik kod analizi genel bakış

Visual Studio 2017 Kod Analizi yönetilen kod iki yolla gerçekleştirebilirsiniz: ile *FxCop* statik analiz Yönetilen derlemeler ve daha fazla modern *Roslyn Çözümleyicileri*. Bu konu, FxCop statik kod analizi içerir. Kod Çözümleyicileri kullanarak kodunu analiz etme hakkında daha fazla bilgi için bkz: [genel bakış, Roslyn Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md).

Yönetilen kod için kod analizi, yönetilen derlemeleri çözümler ve derlemeler, programlama ve Microsoft .NET Framework tasarım yönergeleri ile ortaya konan Tasarım Kuralları ihlalleri gibi bilgileri raporlar.

Analiz aracı uyarı iletileri bir Çözümleme sırasında gerçekleştirdiği denetimleri temsil eder. Uyarı iletileri ilgili programlama ve tasarım sorunlarını belirleyin ve mümkünse sorunu gidermek nasıl bilgi olduğunda.

> [!NOTE]
> Statik kod analizi, Visual Studio'da .NET Core ve .NET Standard projeleri için desteklenmiyor. Kod Analizi bir .NET Core veya .NET Standard projesi msbuild bir parçası olarak çalıştırırsanız, benzer bir hata göreceğiniz **hata: CA0055: platform tanımlanamadı \<your.dll >**. .NET Core veya .NET Standard projelerine kodda çözümlemek için kullanın [Roslyn Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md) yerine.

## <a name="ide-integrated-development-environment-integration"></a>IDE (tümleşik geliştirme ortamı) Tümleştirmesi

El ile veya otomatik olarak projenizde kod analizi çalıştırabilirsiniz.

Bir projeyi derleme yaptığınızda Kod Analizi çalıştırmak için seçin **derlemede kod analizini etkinleştir** projenin özellik sayfasında. Daha fazla bilgi için [nasıl yapılır: etkinleştirme ve devre dışı otomatik kod analizini](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Kod Analizi proje üzerinde el ile çalıştırmak için menü çubuğundan seçin **Çözümle** > **kod çözümlemeyi Çalıştır** > **kod çözümlemeyi Çalıştır \<proje >**.

## <a name="rule-sets"></a>Kural kümeleri

Yönetilen kod için Kod Analizi kuralları halinde gruplanır [kural kümeleri](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Microsoft Standart kural kümelerinden birini kullanabilir veya [bir özel kural kümesi oluşturma](../code-quality/how-to-create-a-custom-rule-set.md) belirli bir gereksinimi karşılamak için.

## <a name="suppress-warnings"></a>Uyarıları gizleme

Genellikle, geçerli olmayan bir uyarı olduğunu belirtmek kullanışlıdır. Bu geliştiriciye ve kodu daha sonra gözden geçirecek diğer kişilere bir uyarı araştırılması ve sonra da gizlenen veya yoksayıldı olduğunu bildirir.

Uyarıların kaynak sıkıştırması özel öznitelikler ile gerçekleştirilir. Bir uyarıyı bastırmak için öznitelik Ekle `SuppressMessage` aşağıdaki örnekte gösterildiği gibi kaynak koda:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Daha fazla bilgi için [uyarıları bastırma](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Bir projeyi Visual Studio 2017'ye geçirirseniz, birden çok sayıda kod çözümleme uyarıları karşılaştığı. Uyarıları gidermek ve hemen üretken olmak hazır değilseniz yapabilecekleriniz *temel* projenizin çözümleme durumu. Gelen **Çözümle** menüsünde **kod analizini Çalıştır ve etkin sorunlar bastır**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>İade ilkesinin parçası olarak kod analizini Çalıştır

Bir kuruluş olarak tüm iade etmelerin bazı ilkeleri karşılamasını zorunlu isteyebilirsiniz. Özellikle, aşağıdaki ilkeleri uyguladığınızdan emin olmanız gerekir:

- Teslim edilen kodda derleme hataları vardır.

- Kod Analizi en son derlemenin bir parçası çalıştırılır.

Bu iade etme ilkeleri belirterek gerçekleştirebilirsiniz. Daha fazla bilgi için [projesi iade ilkeleriyle kod kalitesini geliştirme](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Ekip Oluşturma entegrasyonu

Analiz aracı yapı işleminin bir parçası olarak çalıştırmak için derleme sisteminin tümleşik özelliklerini kullanabilirsiniz. Daha fazla bilgi için [Azure işlem hatları](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Ayrıca bkz.

- [Roslyn çözümleyicilerini genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [Kod Analizi Kurallarını Gruplandırmak için Kural Kümeleri Kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Nasıl Yapılır: Otomatik Kod Çözümlemesini Etkinleştirme ve Devre Dışı Bırakma](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
