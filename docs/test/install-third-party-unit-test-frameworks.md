---
title: 'Nasıl yapılır: Üçüncü taraf birim testi çerçevelerini yükleme'
ms.date: 06/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8acdeb17c9c45613d6a987d503deeaf63beecdaa
ms.sourcegitcommit: 150fa6ec89ea2d086c0af9ababbaf6103a12eff1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2018
ms.locfileid: "52954090"
---
# <a name="install-unit-test-frameworks"></a>Birim testi çerçevelerini yükleme

Visual Studio Test Gezgini'yle herhangi bir bağdaştırıcı arabirimi Gezgini geliştirdi test çerçevesi çalıştırabilirsiniz. Framework'ün yükleme programını ikilileri yükler ve onu destekleyen diller için Visual Studio Proje şablonları ekler. Framework şablonu içeren bir proje oluşturduğunuzda, Test Gezgini ile kayıtlı. Visual Studio çözüm, farklı çerçeveler kullanan ve farklı dil hedeflenen birim testi projelerini içerebilir. Test Gezgini tümünü çalıştırır.

[MSTest](getting-started-with-unit-testing.md) olan Visual Studio tarafından sağlanan test framework ve Visual Studio ile varsayılan olarak yüklenir.

## <a name="acquire-frameworks"></a>Çerçeveler Al

İndirme ve Visual Studio Uzantı Yöneticisi'ni kullanarak veya üçüncü taraf birim testi çerçevelerini yükleme [Visual Studio Market](https://marketplace.visualstudio.com/vs). Çerçeveler, framework'ün bir Web sitesi gibi diğer sitelerdeki de indirilebilir.

### <a name="install-from-visual-studio"></a>Visual Studio'dan yükleyin

1. Seçin **Araçları** standart menüde seçip **Uzantılar ve güncelleştirmeler**.

2. Genişletin **çevrimiçi** > **Visual Studio Market** > **Araçları**. Seçin **test**.

3. Framework bulmak için liste göz atın.

4. Framework seçip **indirme**.

Daha fazla bilgi için [bulabilir ve Visual Studio uzantıları](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="install-from-the-web"></a>Web'den yükleme

İlgilendiğiniz framework biliyorsanız:

1. Açık [Visual Studio Market](https://marketplace.visualstudio.com/vs).

2. Framework'ün adı **Bul** kutusu.

3. Gitmek için sonuç listesinde çerçevesini seçin **Visual Studio Market** aracı için sayfa.

Bir liste diğer test araçları ile birlikte çerçevesini göz atmak için:

1. Açık [Visual Studio Market](https://marketplace.visualstudio.com/vs).

2. İçinde **kategoriye göre filtrele / koleksiyon**, seçin **tümünü gör**.

3. İçinde **kategori** listesi (olarak etiketlenmiş **gösteren**), genişletin **Araçları** düğümünü seçip **test**.

4. Sonuç listesinde gitmek için bir çerçeve seçin bir **Visual Studio Market** aracı için sayfa.

## <a name="update-to-the-latest-test-adapters"></a>İçin en son test bağdaştırıcısı güncelleştirme

Test bulma ve yürütme için daha iyi bir deneyim için en son kararlı test bağdaştırıcısı güncelleştirme. MSTest, NUnit ve xUnit test bağdaştırıcısı güncelleştirmeleri hakkında daha fazla bilgi için bkz. [Visual Studio blogu](https://blogs.msdn.microsoft.com/visualstudio/2017/11/16/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>En son kararlı test bağdaştırıcısı sürümüne güncelleştirmek için

1. Çözümünüz için Nuget Paket Yöneticisi giderek açın **Araçları** > **NuGet Paket Yöneticisi** > **ÇözümiçinNuGetpaketleriniYönet**.

2. Tıklayarak **güncelleştirmeleri** sekmesinde ve arama MSTest, NUnit veya xUnit test yüklenen bağdaştırıcıları.

3. Her test bağdaştırıcısı seçin ve ardından açılan menüde en son kararlı sürümünü seçin.

4. Seçin **yükleme** düğmesi.

   ![Test bağdaştırıcısı yükseltme](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Birim testi kod](../test/unit-test-your-code.md)
