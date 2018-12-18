---
title: Multi-Targeting'e genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 54aabe4871ee7f40e32d42cefd8d291276f361cb
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049806"
---
# <a name="visual-studio-multi-targeting-overview"></a>Visual Studio Çoklu Sürüm Desteğine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sürümünde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], sürümünü belirtebilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] uygulamanız için gerekli olmasıdır. Bu nedenle, bu sürümü kullanmak istiyorsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] önceki bir sürümde başlatılan bir projeyi geliştirmeye devam etmek için çerçeve hedefini değiştirmeniz gerekmez. Ayrıca, farklı sürümlerini hedefleyen framework'ün projeleri içeren bir çözüm oluşturabilirsiniz. Çerçeve hedefleme ayrıca uygulamanın yalnızca belirtilen çerçeve sürümünde kullanılabilir olan işlevleri kullanmasının garantilenmesine yardımcı olur.

> [!TIP]
>  Ayrıca, farklı platformlar için uygulamaları hedefleyebilirsiniz. Daha fazla bilgi için [çoklu sürüm desteği](../msbuild/msbuild-multitargeting-overview.md)

## <a name="framework-targeting-features"></a>Çerçeve hedefleme özellikleri
 Çerçeve hedefleme şu özellikleri içerir:

- Önceki bir sürümünü hedefleyen bir proje açtığınızda [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] otomatik olarak bu yükseltebilir veya hedefi olduğu gibi bırakın.

- Bir proje oluşturduğunuzda, sürümünü belirtebilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] hedeflemek istediğiniz.

- Sürümünü değiştirebilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] varolan bir projenin hedefler.

- Farklı bir sürümünü hedefleyebilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] aynı çözümdeki çeşitli projelerin her birinde içinde.

- Sürümünü değiştirdiğinizde [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , bir projenin hedeflediği [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] başvurular ve yapılandırma dosyalarında gerekli değişiklikleri yapar.

  Önceki bir sürümünü hedefleyen bir proje üzerinde çalışırken [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], Visual Studio dinamik olarak geliştirme ortamını aşağıdaki gibi değişir:

- Öğelere **yeni proje** iletişim kutusu, **Yeni Öğe Ekle** iletişim kutusu, **Yeni Başvuru Ekle** iletişim kutusu ve **hizmetBaşvurusuEkle** hedef sürümde bulunmayan seçimleri atlamak için iletişim kutusu.

- Özel denetimlerinde filtreler **araç kutusu** hedeflenen sürümde olmayanları kaldırın ve yalnızca göstermek için birden çok denetim uygun olduğunda en güncel kontrol eder.

- Bu, hedeflenen sürümde olmayan dil özelliklerini atlamak için Intellisense'e filtre uygular.

- Özelliklere **özellikleri** hedeflenen sürümde olmayanları atlamak için penceresi.

- Bu, hedeflenen sürümde kullanılabilir olmayan seçenekleri atlamak için menü seçeneklerine filtre uygular.

- Derlemeler için derleyici ve derleyici seçenekleri hedeflenen sürüm için uygun sürümünü kullanır.

> [!NOTE]
>  Çerçeve hedefleme, uygulamanızın doğru şekilde çalışacağını garanti etmez. Hedeflenen sürümde çalışacağından çalıştığından emin olmak için uygulamanızı test etmeniz gerekir. .NET Framework 2. 0 ' daha eski framework sürümlerini hedefleyemezsiniz.

## <a name="selecting-a-target-framework-version"></a>Hedef Framework sürüm seçme
 Bir proje oluşturduğunuzda, hedef seçin [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünde **yeni proje** iletişim kutusu. Kullanılabilir proje şablonları listesinde, seçime göre filtrelenir. Varolan bir projede, hedef değiştirebilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünü Proje Özellikleri iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

> [!NOTE]
>  Visual Studio'nun Express sürümlerinde hedef Framework'ü olarak ayarlanamıyor **yeni proje** iletişim kutusu.

## <a name="resolving-system-and-user-assembly-references"></a>Sistem ve kullanıcı derleme başvurularını çözümleme
 Bir .NET Framework sürümünü hedeflemek için önce uygun derleme başvurularını yüklemeniz gerekir. .NET Framework sürüm 2.0, 3.0 ve 3.5 için derleme başvuruları karşıdan yükleyebileceğiniz .NET Framework 3.5 SP1, dahil edilecek [Microsoft Download Center, Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602) Web sitesi. .NET Framework 3.5 istemci profili, .NET Framework 4, .NET Framework 4 istemci profili ve Silverlight için derleme başvuruları web'da ayrıca [Visual Studio indirmeleri](http://go.microsoft.com/fwlink/?LinkId=179687) Web sitesi.

> [!NOTE]
>  .NET Framework istemci profili, kitaplıkların ve özelliklerin sınırlı bir kümesini sağlayan .NET Framework'ün bir alt kümesidir. İstemci profilleri hakkında daha fazla bilgi için bkz. [.NET Framework istemci profili](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

 **Başvuru Ekle** iletişim kutusu, hedefine ait olmayan sistem derlemelerini devre dışı bırakır [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürüm böylece bunlar yanlışlıkla bir projeye eklenemez. (Sistem derlemeleri, dahil olan .dll dosyaları bir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümü.) Hedeflenen sürümden daha sonraki bir framework sürümüne ait başvuruları çözmeyecek ve böyle bir başvuruya dayanan denetimler eklenemez. Böyle bir başvuruyu etkinleştirmek istiyorsanız, sıfırlama [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] hedef başvuru içeren bir proje.  Daha fazla bilgi için [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).

 Derleme başvuruları hakkında daha fazla bilgi için bkz: [tasarım zamanında derlemeleri çözme](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enabling-linq"></a>LINQ'i etkinleştirme
 .NET Framework 3.5 veya sonraki sürümler, bir System.Core başvurusu ve bir proje düzeyi içeri aktarma (yalnızca Visual Basic'te) System.Linq hedeflediğinizde otomatik olarak eklenir. LINQ özelliklerini kullanmak istiyorsanız, ayrıca Option Infer (yalnızca Visual Basic'te) açmanız gerekir. Hedefi önceki bir .NET Framework sürümü ile değiştirirseniz başvuru ve içe aktarma otomatik olarak kaldırılır. Daha fazla bilgi için [nasıl yapılır: bir LINQ projesi oluşturma](http://msdn.microsoft.com/library/a929e653-09a3-44be-881f-68ca33f192b2).

## <a name="see-also"></a>Ayrıca Bkz.
 [Çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md) [ASP.NET Web projeleri için .NET Framework çoklu sürüm desteğinin](http://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76) [Platform uyumluluğu ve sistem gereksinimleri](http://www.microsoft.com/visualstudio/eng/products/compatibility)
