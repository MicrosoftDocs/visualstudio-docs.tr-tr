---
title: Kod analizini yapılandırma
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c94c1a82acfcabaa8bc6d73eb302b8760c5df2ec
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062428"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Nasıl yapılır: Yönetilen Kod Projesi İçin Kod Çözümlemesini Yapılandırma

Visual Studio'da, Kod Analizi listesinden seçim yapabilir [kural kümeleri](../code-quality/rule-set-reference.md)) yönetilen kod projesi için uygulanacak. Varsayılan olarak, **Microsoft en az önerilen kurallar** kural kümesi işaretli, ancak isterseniz kümesi farklı bir kural uygulayabilirsiniz. Bir çözümde bir veya birden çok proje için kural kümeleri uygulanabilir.

> [!TIP]
> ASP.NET web uygulamaları için bir kural yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: yapılandırma kod analizi için bir ASP.NET web uygulaması](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework projesi için bir kural yapılandırmak için

1. Açık **Kod Analizi** projenin özellik sayfalarındaki sekmesinde. Bu aşağıdaki yollardan biriyle yapabilirsiniz:

   - İçinde **Çözüm Gezgini**, projeyi seçin. Menü çubuğunda, seçin **Çözümle** > **Kod Analizi yapılandırma** > **için \<projectname >**.

   - Projeye sağ **Çözüm Gezgini** seçip **özellikleri**ve ardından **Kod Analizi** sekmesi.

1. İçinde **yapılandırma** ve **Platform** listeleri, derleme yapılandırması ve hedef platformu seçin.

1. Seçili yapılandırma kullanarak proje oluşturulan her zaman, Kod Analizi çalıştırmak için seçin **derlemede kod analizini etkinleştir** onay kutusu. Ayrıca kod analizini el ile seçerek çalıştırabilirsiniz **Çözümle** > **kod çözümlemeyi Çalıştır** > **kod çözümlemeyi Çalıştır \<projectname >**.

1. Varsayılan olarak, Kod Analizi uyarıları otomatik olarak dış araçları tarafından oluşturulan kodu raporlamaz. Üretilen koddan gelen uyarıları görüntülemek için temizleyin **üretilen koddan gelen sonuçları Gizle** onay kutusu.

    > [!NOTE]
    > Bu seçenek hataları ve Uyarıları formları ve şablonlar görüntülendiğinde kod çözümleme hataları ve Uyarıları üretilen koddan gelen engellemez. Hem görüntüleyebilir ve bir form veya şablon için kaynak kodu, üzerine zorunda kalmadan korumak.

1. İçinde **bu kural kümesini Çalıştır** listesinde, aşağıdakilerden birini yapın:

    - Kullanmak istediğiniz bir kural kümesi seçin.

    - Seçin  **\<Gözat … >** var olan bir özel kural kümesi bulmak için listesinde değil.

    - Tanımlayan bir [özel kural kümesi](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Bir çözümde birden çok proje için kural kümeleri belirtin

Varsayılan olarak, bir çözümün tüm yönetilen projelere atanır *Microsoft en az önerilen kurallar* Kod Analizi kural kümesi. Bir Çözümdeki projeler için atanan kural kümeleri değiştirebilirsiniz **özellikleri** çözümü iletişim kutusu.

1. Visual Studio içinde çözümü açın.

2. Üzerinde **Çözümle** menüsünde **çözüm için Kod Analizi yapılandırma**.

3. Gerekirse genişletin **ortak özellikler**ve ardından **Kod Analizi ayarları**.

4. Bir veya daha fazla proje için bir kural belirtebilirsiniz:

    - Bir kural kümesi için bir projeyi belirtmek için proje adını seçin.

    - Birden çok proje için bir kural belirtmek için basılı **Ctrl** ve proje adları seçin.

    - Çözümdeki tüm projeleri belirtmek için basılı **Shift** ve Proje listesinde tıklayın.

5. Seçin **kural kümesi** bir proje alanı ve ardından uygulamak istediğiniz kuralın adını ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)
- [Nasıl yapılır: bir ASP.NET web uygulaması için kod çözümlemesini yapılandırma](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)