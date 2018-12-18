---
title: .NET Framework'ü hedefleyen
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e0004678b62b9deba97d31815de577721008f77d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058304"
---
# <a name="visual-studio-multi-targeting-overview"></a>Visual Studio çoklu sürüm desteğine genel bakış

Visual Studio sürümünü veya profilini projenizi hedefleyecek şekilde istediğiniz .NET Framework'ün belirtebilirsiniz. Bir uygulamayı başka bir bilgisayardaki uygulamayı hedef bilgisayarda yüklü Framework sürümü ile uyumlu olması gereken Framework sürümünü çalıştırmak için.

Ayrıca, farklı sürümlerini hedefleyen framework'ün projeleri içeren bir çözüm oluşturabilirsiniz. Çerçeve hedefleme, uygulamanın yalnızca belirtilen çerçeve sürümünde kullanılabilir olan işlevleri kullanmasının garantilenmesine yardımcı olur.

> [!TIP]
> Ayrıca, farklı platformlar için uygulamaları hedefleyebilirsiniz. Daha fazla bilgi için [çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Çerçeve hedefleme özellikleri

Çerçeve hedefleme şu özellikleri içerir:

- Önceki bir sürümünü hedefleyen bir proje açtığınızda [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio, otomatik olarak yükseltebilir veya hedefi olarak bırakın-olduğu.

- Bir proje oluşturduğunuzda, sürümünü belirtebilirsiniz [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] hedeflemek istediğiniz.

- Sürümünü değiştirebilirsiniz [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] varolan bir projenin hedefler.

- Farklı bir sürümünü hedefleyebilirsiniz [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] aynı çözümdeki çeşitli projelerin her birinde içinde.

- Sürümünü değiştirdiğinizde [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , bir projenin hedeflediği [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] başvurular ve yapılandırma dosyalarında gerekli değişiklikleri yapar.

Önceki bir sürümünü hedefleyen bir proje üzerinde çalışırken [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio dinamik olarak geliştirme ortamını aşağıdaki gibi değişir:

- Öğelere **Yeni Öğe Ekle** iletişim kutusu, **Yeni Başvuru Ekle** iletişim kutusu ve **hizmet Başvurusu Ekle** kullanılabilir olmayan seçenekleri atlamak için iletişim kutusu hedeflenen sürümü.

- Özel denetimlerinde filtreler **araç kutusu** hedeflenen sürümde olmayanları kaldırın ve yalnızca göstermek için birden çok denetim uygun olduğunda en güncel kontrol eder.

- Bu filtreler **IntelliSense** hedeflenen sürümde olmayan dil özelliklerini atlamak için.

- Özelliklere **özellikleri** hedeflenen sürümde olmayanları atlamak için penceresi.

- Bu, hedeflenen sürümde kullanılabilir olmayan seçenekleri atlamak için menü seçeneklerine filtre uygular.

- Derlemeler için derleyici ve derleyici seçenekleri hedeflenen sürüm için uygun sürümünü kullanır.

> [!NOTE]
> Çerçeve hedefleme, uygulamanızın doğru şekilde çalışacağını garanti etmez. Hedeflenen sürümde çalışacağından çalıştığından emin olmak için uygulamanızı test etmeniz gerekir. .NET Framework 2. 0 ' daha eski framework sürümlerini hedefleyemezsiniz.

## <a name="select-a-target-framework-version"></a>Hedef framework sürümü seçin

Bir proje oluşturduğunuzda, hedef .NET Framework sürümünü seçin **yeni proje** iletişim kutusu. Seçili şablon türü için geçerli olan yüklü framework sürümleri kullanılabilir çerçeveleri listesini içerir. .NET Framework, .NET Core şablonları, gerektirmeyen şablon türleri için **Framework** açılır listede gizlenir.

![Framework açılan yeni proje iletişim kutusunda](media/vside-newproject-framework.png)

Varolan bir projede, hedef değiştirebilirsiniz [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sürümünü Proje Özellikleri iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolve-system-and-user-assembly-references"></a>Sistem ve kullanıcı derleme başvurularını çözümleme

Bir .NET Framework sürümünü hedeflemek için önce uygun derleme başvurularını yüklemeniz gerekir. .NET Framework'ün farklı sürümleri için geliştirici paketlerinin indirebileceğiniz [.NET indirir](https://www.microsoft.com/net/download/windows) sayfası.

**Başvuru Ekle** iletişim kutusu, hedefine ait olmayan sistem derlemelerini devre dışı bırakır [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sürüm böylece bunlar yanlışlıkla bir projeye eklenemez. (Sistem derlemeleri, *.dll* dahil edilen dosyaların bir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sürümü.) Hedeflenen sürümden daha sonraki bir framework sürümüne ait başvuruları çözmeyecek ve böyle bir başvuruya dayanan denetimler eklenemez. Böyle bir başvuruyu etkinleştirmek istiyorsanız, sıfırlama [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] hedef başvuru içeren bir proje.  Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Derleme başvuruları hakkında daha fazla bilgi için bkz: [tasarım zamanında derlemeleri çözme](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>LINQ'i etkinleştirmek

.NET Framework 3.5 veya sonraki sürümler, bir başvuru hedeflediğinizde **System.Core** ve bir proje seviyesinde içeri alma için <xref:System.Linq> (yalnızca Visual Basic'te) otomatik olarak eklenir. LINQ özelliklerini kullanmak istiyorsanız, ayrıca etkinleştirmelisiniz `Option Infer` üzerinde (yalnızca Visual Basic'te). Hedefi önceki bir .NET Framework sürümü ile değiştirirseniz başvuru ve içe aktarma otomatik olarak kaldırılır. Daha fazla bilgi için [LINQ ile çalışma](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu sürüm desteği (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Nasıl yapılır: hedef framework ve platform araç takımını (C++) değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)