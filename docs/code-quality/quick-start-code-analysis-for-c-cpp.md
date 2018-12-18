---
title: 'Hızlı Başlangıç: C/C++ İçin Kod Çözümleme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 3aefc42e77c6ccaf14a426a26e12b81b49bb5632
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818776"
---
# <a name="quickstart-code-analysis-for-cc"></a>Hızlı başlangıç: C/C++ için kod analizi

Kod Analizi düzenli olarak C veya C++ kodu çalıştırarak uygulamanızı kalitesini artırabilir. Bu yaygın sorunlar, iyi bir programlama uygulama ya da test sürecinde bulmak zor olan hataları ihlalleri bulmanıza yardımcı olabilir. Geçerli olan, ancak yine de siz veya kodunuzu kullanan diğer kişilerin sorunlarına neden olabilir, belirli bir kod desenleri için Kod Analizi arar çünkü kod çözümleme uyarıları derleyici hataları ve Uyarıları farklılık gösterir.

## <a name="configure-rule-sets-for-a-project"></a>Bir proje için kural kümelerini yapılandırma

1. İçinde **Çözüm Gezgini**, proje adı için kısayol menüsünü açın ve ardından **özellikleri**.

2. Aşağıdaki adımlar isteğe bağlıdır:

    1. İçinde **yapılandırma** ve **Platform** listeleri, derleme yapılandırması ve hedef platformu seçin.

    2. Varsayılan olarak, Kod Analizi uyarıları otomatik olarak dış araçları tarafından oluşturulan kodu raporlamaz. Üretilen koddan gelen uyarıları görüntülemek için temizleyin **üretilen koddan gelen sonuçları Gizle** onay kutusu.

        > [!NOTE]
        > Bu seçenek hataları ve Uyarıları formları ve şablonlar görüntülendiğinde kod çözümleme hataları ve Uyarıları üretilen koddan gelen engellemez. Hem görüntüleyebilir ve bir form veya şablon için kaynak kodunu korumak.

3. Seçili yapılandırma kullanarak proje oluşturulan her zaman, Kod Analizi çalıştırmak için seçin **C/c++ derlemede kod çözümlemeyi etkinleştir** onay kutusu. Ayrıca kod analizini el ile açıp çalıştırabilirsiniz **Çözümle** menüsüne ve ardından **kod çözümlemeyi Çalıştır** *ProjectName*.

4. İçinde **bu kural kümesini Çalıştır** listesinde, aşağıdakilerden birini yapın:

    - Kullanmak istediğiniz bir kural kümesi seçin.

    - Seçin  **\<Gözat … >** var olan bir özel kural kümesini belirlemek için listesinde değil.

    - Tanımlayan bir [özel kural kümesi](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Standart C/C++ kural kümeleri

Visual Studio iki standart yerel kod için kural kümesi içerir:

|Kural kümesi|Açıklama|
|--------------|-----------------|
|Önerilen Microsoft yerel Minimum kurallar|Bu kural kümesi, olası güvenlik açıkları ve Uygulama Kilitlenmesi gibi yerel, kodunuzda en kritik sorunlara odaklanır. Doğal projeleriniz için oluşturduğunuz herhangi bir özel kural kümesi bu kural kümesini içermelidir.|
|Microsoft yerel önerilen kurallar|Bu kural kümesi, çok çeşitli sorunları kapsar. Bu yerel en az önerilen kurallar Microsoft tüm kurallar içerir.|

## <a name="run-code-analysis"></a>Kod analizini Çalıştır

Proje özellik sayfaları, Kod Analizi sayfasında projenizi her çalıştırma için Kod Analizi yapılandırabilirsiniz. Kod analizini el ile çalıştırabilirsiniz.

Bir çözüm üzerinde kod analizi çalıştırmak için:

- Üzerinde **derleme** menüsünde seçin **çözüm üzerinde kod analizini Çalıştır**.

Bir proje üzerinde kod analizi çalıştırmak için:

1. Çözüm Gezgini'nde proje adını seçin.

2. Üzerinde **derleme** menüsünde seçin **kod çözümlemeyi Çalıştır** *proje adı*.

   Proje veya çözüm derlenir ve Kod Analizi çalıştırır. Sonuçlar hata Listesi'nde görüntülenir.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analiz ve kod çözümleme uyarıları çözün

Belirli bir uyarıyı çözümlemek için hata listesinde bir uyarı başlığı seçin. Sorun hakkında ek bilgileri görüntülemek için uyarı genişletir. Mümkün olduğunda, kod analizi, uyarıya yol açan analiz mantığı ve satır numaralarını görüntüler. Sorun için olası çözümleri dahil olmak üzere uyarı hakkında ayrıntılı bilgi için karşılık gelen Yardım konusunun görüntülenecek Uyarı Kimliği'ni seçin.

Bir uyarıyı seçtiğinizde, Visual Studio Kod Düzenleyicisi'nde uyarıya yol açan kod satırının vurgulanır.

Sorun anladıktan sonra kodunuzu çözebilirsiniz. Sonra uyarı artık hata Listesi'nde görüntülenir ve düzeltmenizi henüz oluşturulan tüm yeni uyarılar emin olmak için kod analizini yeniden çalıştırın.

## <a name="suppress-code-analysis-warnings"></a>Kod çözümleme uyarılarını bastırma

Kod Analizi uyarısı düzeltmemeyi ne zaman karar verebilirsiniz zamanlar vardır. Uyarı çözümleme sorunu kodunuzun tüm gerçek uygulamasında ortaya çıkacağını olasılık ile ilgili çok fazla değiştirilemeyen gerektirir karar verebilirsiniz. Veya uyarıda kullanılan analiz belirli bir içerik için uygun olduğunu düşündüğünüz. Böylece artık hata listesinde görünürler bireysel uyarıları gösterilmemesini sağlayabilirsiniz.

Bir uyarıyı bastırmak için:

1. Ayrıntılı bilgi görüntülenmiyorsa genişletmek için uyarı başlığı seçin.

2. Seçin **eylemleri** Uyarı alt kısmındaki bağlantı.

3. Seçin **ileti Gizle** seçip **içinde kaynak**.

   Bir ileti gizleme ekler `#pragma warning (disable:[warning ID])` , kod satırının için uyarı bastırır.

## <a name="create-work-items-for-code-analysis-warnings"></a>İş öğeleri için kod çözümleme uyarıları oluşturma

Visual Studio içinden hatalardan oturum iş öğesi izleme özelliğini kullanabilirsiniz. Bu özelliği kullanmak için Team Foundation Server'ın bir örneğine bağlanmak gerekir.

**Bir veya daha fazla C/C++ kod uyarıları için bir iş öğesi oluşturmak için**

1. Hata listesini genişletin ve Uyarıları seçin

2. Uyarılar için kısayol menüsünde **iş öğesi oluştur**, iş öğesi türünü seçin.

3. Visual Studio seçili uyarılar için tek bir iş öğesi oluşturur ve iş öğesini IDE'nin belge penceresinde görüntüler.

4. Ek bilgileri ekleyin ve ardından **çalışma öğesini Kaydet**.

## <a name="search-and-filter-code-analysis-results"></a>Kod Analizi sonuçları arama ve filtreleme

Uzun listesi uyarı iletilerini arayabilir ve çoklu proje çözümlerinde uyarıları filtreleyebilirsiniz.

- **Başlık veya Uyarı Kimliği Filtresi uyarılarını için**: anahtar sözcük arama kutusuna girin.

- **Filtre Uyarıları önem derecesine göre için**: varsayılan olarak, Kod Analizi ileti önem derecesi atanan **uyarı**. Bir veya daha fazla ileti olarak önemi atamak için **hata** özel bir kuralda ayarlayın. Üzerinde **önem derecesi** sütununun **hata listesi**, açılan liste okunu ve ardından filtre simgesini seçin. Seçin **uyarı** veya **hata** ilgili önem atanmış olan iletileri görüntülemek için. Seçin **Tümünü Seç** tüm iletileri görüntülemek için.

## <a name="see-also"></a>Ayrıca bkz.

[C/C++ için Kod Analizi](../code-quality/code-analysis-for-c-cpp-overview.md)