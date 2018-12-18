---
title: Yönetilen Kod için Özel Kod Çözümleme İade İlkelerini Uygulama
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4c39ef2c70108eabb3c3d87dc7ab5af17dccd9f8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049872"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Yönetilen Kod için Özel Kod Analizi İade İlkelerini Uygulama

Kod Analizi İlkesi iade sürüm denetimine iade edilmeden önce Azure DevOps projesinin üyeleri kaynak kodunu çalıştırmanız gereken kurallar kümesi belirtir. Microsoft, standart bir dizi sağlar *kural kümeleri* bu grubu Kod Analizi kuralları işlevsel alanlara. *Özel iade ilke kural kümelerinin* projeye özgü kod analizi kuralları kümesi belirtin. Bir kural kümesi bir .ruleset dosyası depolanır.

İade ilkeleri Azure DevOps projesi düzeyinde belirlenir ve sürüm denetimi ağacındaki bir .ruleset dosyası konumunu tarafından belirtilen. Takım ilke özel kural kümesi sürüm denetimi konumunu ilgili bir kısıtlama yoktur.

Kod Analizi her proje için Özellikler penceresindeki bireysel kod projeleri için yapılandırılır. Bir kod projesi için özel bir kural .ruleset dosyası yerel bilgisayardaki fiziksel konumunu belirtilir. Kod projesini aynı sürücüde bulunan bir .ruleset dosyası belirtildiğinde, Visual Studio Proje yapılandırma dosyasına göreli bir yol kullanır.

İade İlkesi .ruleset dosyası herhangi bir kod projesinin bir parçası değil özel bir klasörde depolamak için proje özel kural kümesi olan bir Azure DevOps oluşturmak için önerilen bir uygulamadır. Adanmış bir klasörde dosya depolama, kural dosyası düzenleyebilen kısıtlayan izinler uygulayabilirsiniz ve dizin yapısı kolayca taşıyabilirsiniz, proje başka bir dizin ya da bilgisayar içeriyor.

## <a name="create-the-project-custom-check-in-rule-set"></a>Projeyi iade özel kural kümesi oluşturma

Bir Azure DevOps projesi için özel bir kural oluşturmak için önce kümesinde iade ilkesi kuralı için özel bir klasör oluşturun **Kaynak Denetim Gezgini**. Ardından, kural kümesi dosyası oluşturun ve dosyayı sürüm denetimine ekleyin. Son olarak, kural olarak kod çözümleme iade ilkesi proje için kümesi belirtin.

> [!NOTE]
> Azure DevOps projesinde bir klasör oluşturmak için önce proje kök dizinini yerel bilgisayardaki bir konuma eşlemeniz gerekir.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Sürüm denetimi klasörü İade İlkesi kural kümesi oluşturmak için

1. Ekip Gezgini'nde proje düğümünü genişletin ve ardından **kaynak denetimi**.

2. İçinde **klasörleri** bölmesinde, projeye sağ tıklayın ve ardından **yeni klasör**.

3. Ana Kaynak Denetim Masası'nda, sağ **yeni klasör**, tıklayın **Yeniden Adlandır**, klasör kural kümesi için bir ad yazın.

### <a name="to-create-the-check-in-policy-rule-set"></a>İade İlkesi kural kümesi oluşturmak için

1. Üzerinde **dosya** menüsünde **yeni**ve ardından **dosya**.

2. İçinde **kategorileri** listesinde **genel**.

3. İçinde **şablonları** listesinde, çift **Kod Analizi kural kümesi**.

4. [Kuralları](../code-quality/how-to-create-a-custom-rule-set.md) dosyası kural kümesine dahil edin ve ardından kuralını kaydetmek için oluşturduğunuz kural kümesi klasörü ayarlayın.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Kural eklemek için dosya sürüm denetimi için ayarlama

1. İçinde **Kaynak Denetim Gezgini**yeni klasörü sağ tıklatın ve ardından **öğeleri klasöre Ekle**.

     Daha fazla bilgi için [Git ve Azure depoları](/azure/devops/repos/git/overview?view=vsts).

2. Kural kümesi oluşturduğunuz dosya tıklayın ve ardından **son**.

     Dosya kaynak denetimine eklediğiniz ve sizin için kullanıma.

3. İçinde **Kaynak Denetim Gezgini** Ayrıntıları penceresi, dosya adına sağ tıklayın ve ardından **bekleyen değişiklikleri iade et**.

4. İçinde **iade** iletişim kutusu, bir açıklama ekleyin ve ardından seçeneğine sahip **iade**.

    > [!NOTE]
    > Azure DevOps projeniz için bir kod analizi iade ilkesi zaten yapılandırdıysanız ve seçtiğiniz **yalnızca geçerli çözümün bir parçası olan dosyaları içerecek şekilde iade zorunlu**, bir ilke hatası uyarısı tetikler. İlke hatası iletişim kutusunda **ilke hatası geçersiz kıl ve iade etmeye devam et**. Gerekli bir açıklama ekleyin ve ardından **Tamam**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Dosyası kural belirtmek için iade ilke olarak ayarlayın

1. Üzerinde **takım** menüsünde **proje ayarları**ve ardından **kaynak denetimi**.

2. Tıklayın **iade ilkesi**ve ardından **Ekle**.

3. İçinde **iade ilkesi** listesinde, çift **Kod Analizi**, emin olun **yönetilen kod için kod analizini zorla** onay kutusu seçilidir.

4. İçinde **bu kural kümesini Çalıştır** listesinde  **\<kaynak denetiminden kural kümesi seçin >**.

5. Sürüm denetimine iade ilkesi kural kümesi dosyası yolunu yazın.

     Yol aşağıdaki sözdizimine uygun olmalıdır:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Yolu aşağıdaki yordamlardan birini kullanarak kopyalayabilirsiniz **Kaynak Denetim Gezgini**:

    - İçinde **klasörleri** bölmesinde, kural kümesi dosyası içeren klasörü tıklatın. Görünen klasörün sürüm denetim yolu Kopyala **kaynak** kutusuna ve kural kümesi dosyası adını elle yazın.

    - Kural kümesi dosyası Ayrıntıları penceresinde sağ tıklayın ve ardından **özellikleri**. Üzerinde **genel** sekmesinde, bu değeri kopyalayın **sunucu adı**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Kod projeleri iade ilkesi kuralı kümesine eşitleme

Belirttiğiniz bir projeyi iade ilkesi kuralı Özellikler iletişim kutusunda kod projesinin kod proje yapılandırmasının Kod Analizi kural kümesi olarak ayarlayın. Kural kümesi kod projesini aynı sürücüde yer alıyorsa, göreli bir yol kural kümesi yolu dosya iletişim kutusundan seçildiğinde belirtmek için kullanılır. Denetim yapıları benzer yerel sürüm kullanan diğer bilgisayarlar için taşınabilir proje özellikleri ayarlar göreli bir yol sağlar.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Bir proje kural belirtmek için bir kod proje kural kümesi olarak ayarlayın.

1. Gerekirse, iade ilkesi kuralı kümesi klasör ve dosya sürüm denetiminden alın.

   Bu adımda gerçekleştirdiğiniz **Kaynak Denetim Gezgini** sağ tıklayarak kural klasörünü ve ardından kümesi **en son sürümü Al**.

2. İçinde **Çözüm Gezgini**kod projesine sağ tıklayın ve ardından **özellikleri**.

3. **Kod Analizi tıklayın**.

4. Gerekirse, uygun seçenekleri tıklayın **yapılandırma** ve **Platform** listeler.

5. Kod Analizi proje kodu belirtilen yapılandırma kullanılarak oluşturulan her tamamlanışında çalıştırılacak seçin **etkinleştir (code_analysıs sabitini tanımlar) derlemede kod analizini** onay kutusu.

6. Diğer şirketlerin bileşenleri kodda yoksaymak için seçin **üretilen koddan gelen sonuçları Gizle** onay kutusu.

7. İçinde **bu kural kümesini Çalıştır** listesinde  **\<Gözat … >**.

8. İade İlkesi kural kümesi dosyası yerel sürümünü belirtin.