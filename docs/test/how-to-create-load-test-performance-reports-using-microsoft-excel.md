---
title: Microsoft Excel kullanarak yük testi başarım raporları oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 5f276702aef4bf062d7da3e921965e674d5ec738
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065002"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Nasıl yapılır: oluşturma yük testi başarım raporları kullanarak Microsoft Excel

İki veya daha fazla test sonucunu temel alan Microsoft Excel yük testi raporları oluşturabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yük testi raporlarının iki türü kullanılabilir:

-   **Karşılaştırmayı Çalıştır** bu tabloları ve çubuk grafikleri kullanarak iki yük testi sonuçları verilerden karşılaştıran rapor kümesini oluşturur.

-   **Eğilim** , iki veya daha fazla yük test sonucu eğilim çözümlemesi oluşturabilirsiniz. Çizgi grafikler kullanarak sonuçlar görüntülenir, ancak veriler pivot tablolardan ulaşılabilir.

> [!TIP]
> Özet görünümü, grafik görünümü ve tablolar görünümünden veri yapıştırarak Microsoft Word raporlarını el ile de oluşturabilirsiniz. Bkz: [nasıl yapılır: Microsoft Word kullanılarak bir yük testi başarım raporunu el ile oluşturma](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

Başarım verisini hissedarlarla paylaşmak ve genel performansı ve sistem durumu iyiye iletmek için her iki rapor kullanılabilir ya da daha da kötüsü.

Rapor tanımları yük testi veritabanında depolanır. Rapor kaydedildiğinde, rapor için tanım veritabanında kaydedilir ve daha sonra yeniden kullanılabilir.

Ayrıca, Excel çalışma kitabı, hissedarların raporu görmek için veritabanına bağlanmak zorunda değilsiniz için hissedarlarla paylaşılabilir.

> [!NOTE]
> Excel çalışma kitabını paylaşabilirsiniz; Ancak, yalnızca Visual Studio, makinede yüklü olan kullanıcılar elektronik tablolarda değişiklik mümkün olacaktır. Diğer kullanıcılar **yük testi raporu** seçeneğini **Office** Şerit, ancak bunlar oluşturabileceksiniz çalışma kitabını görüntüleme.

Aşağıdaki çizim işlem (alışveriş sepetini güncelleştir) hız dejenerasyonu ve (% işlemci) sayacın degeneration arasında bir bağıntı gösteren bir rapor örneğidir. Bu, veritabanı veya ağ yerine uygulama kodundaki olası bir sorunu işaret eden ve ASP.NET Profiler'ı kullanarak tanılamak için iyi bir adaydır.

![Uygulama kodundaki olası bir sorunu](../test/media/lt_excel.png)

Excel raporları oluşturulabilir **Yük Testi Çözümleyicisi**, kullanarak **Excel Raporu Oluştur** kullanarak düğme araç çubuğunda veya Excel'den **yük testi raporu** seçeneğini **yük testi** sekmesinde **Office** Şerit.

> [!NOTE]
> Bir yük testine yorum eklerseniz, bunlar Excel raporunda görüntülenir.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Excel kullanarak yük testi karşılaştırma raporları oluşturmak için

1. Rapor oluşturmadan önce öncelikle bir yük testi çalıştırmanız gerekir.

2. Excel yük test raporlarını iki şekilde oluşturabilirsiniz:

   - İçinde bir yük testi tamamlandıktan sonra **yük testi sonuçlarını** sayfasında **Excel Raporu Oluştur** araç çubuğu düğmesi.

      > [!NOTE]
      > Varsa **Excel Raporu Oluştur** düğmesini devre dışı **Web Performans Test Sonuçları Görüntüleyicisi** araç, Microsoft Excel'i çalıştırmak gerekebilir ise, etkinleştirmeden önce zaman. Visual Studio Enterprise yük testi eklentisi bilgisayarınıza Visual Studio Enterprise yüklü olduğunda, Microsoft Excel için kopyalanır; Ancak, Microsoft Excel için eklenti yükleme işleminin tamamlanması için çalıştırmanız gerekir.

      Microsoft Excel açılır **bir yük testi Rapor Sihirbazı Oluştur**.

   **VEYA**

   1. Microsoft Excel'i açın, **yük testi** sekmesinde **Office** Şerit ve ardından **yük testi raporu**.

       **Bir yük testi Rapor Sihirbazı Oluştur** görünür.

   2. İçinde **yük testlerini içeren veritabanını Seç** sayfasındaki **sunucu adı**, yük testi sonuçlarını içeren sunucunun adını yazın.

   3. İçinde **Databasename** aşağı açılan listesinde, yük testi sonuçlarını içeren veritabanını seçin.

3. İçinde **nasıl raporunuzu oluşturmak istiyorsunuz** sayfasında, **rapor oluşturma** seçin ve seçilen **sonraki**.

4. İçinde **hangi türde rapor oluşturmak istiyorsanız** sayfasında, **karşılaştırmayı Çalıştır** seçin ve seçilen **sonraki**.

5. İçinde **Enter yük testi rapor ayrıntılarını** sayfasında, rapor için bir ad yazın **rapor adı**.

6. Seçin ve raporunu oluşturmak istediğiniz yük testini seçin **sonraki**.

7. İçinde **raporunuz için çalıştırmaları seçin** sayfasındaki **rapora eklemek için bir veya daha fazla çalıştırma seçin**seçin ve raporda karşılaştırmak istediğiniz test sonuçlarını iki yük **sonraki**.

   > [!NOTE]
   > Yalnızca iki yük testi sonuçları üzerinde bir karşılaştırma raporu oluşturabilirsiniz. Ya da bir yük testi sonucunu seçin veya ikiden daha fazla yük testi sonuçları, bir uyarı iletisi görüntülenir.

8. İçinde **raporunuz için sayaçlar seçin** sayfasındaki **rapora eklenecek bir veya daha fazla sayaç seçin** sayaçların Genişletilebilir listesi, raporunuzu özelleştirmek kullanılabilirdir. Seçin ve raporun iki seçili test çalıştırmasından karşılaştırmak istediğiniz sayaçları seçin **son**.

9. Excel çalışma kitabı raporu aşağıdaki elektronik tablo sekmeleriyle oluşturulur:

   - **İçindekiler tablosu** - yük testi rapor adını görüntüler ve raporda çeşitli sekmelere için bağlantılarla birlikte içindekiler tablosu sağlar.

   - **Çalıştırır -** üzerinde iki çalıştırmanın karşılaştırıldığı raporda ayrıntıları sağlar.

   - **Test Karşılaştırması -** performans gerilemeleri ve ilerlemeleri Karşılaştırılan iki çalıştırma arasında çubuk grafiği ayrıntıları sağlar.

   - **Sayfa karşılaştırması -** çubuk grafiği ve yüzde başarım test çalıştırmalarında çeşitli sayfalar üzerinde iki çalıştırma arasında karşılaştırma verisini sağlar.

   - **Makine karşılaştırması -** kullanılan makineleri temel iki çalıştırma arasında karşılaştırma verisini sağlar.

   - **Hata karşılaştırması -** iki çalıştırma ve yineleme sayısı arasında karşılaşılan hata türlerini karşılaştırır.

     > [!TIP]
     > Daha iyi raporlar için çeşitli özellikler, daha zengin raporlara olanak tanıyan bir web performans testleri ve yük testleri de kullanılabilir. Sayfa istekleri raporlarda sunulan iki özelliğe sahiptir: hedef ve raporlama adı. Sayfa yanıt zamanı hedefe yönelik bildirilir ve raporlama adı URL'nin raporlarında yerine kullanılacak. Sayaç Kümelerini Yönet altında çalıştırma ayarları yük testinde özelliği bilgisayar etiketleri rapor makina adlarında sunulur. Bu rapor belirli bir makinenin rolünü tanımlamak kullanışlıdır.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Excel kullanarak yük testi Eğilim raporları oluşturmak için

1. Rapor oluşturmadan önce bir yük testi çalıştırmanız gerekir.

2. Excel yük test raporlarını iki şekilde oluşturabilirsiniz:

   - İçinde bir yük testi tamamlandıktan sonra **yük testi sonuçlarını** sayfasında **Excel Raporu Oluştur** araç çubuğu düğmesi.

      > [!NOTE]
      > Varsa **Excel Raporu Oluştur** düğmesini devre dışı **Web Performans Test Sonuçları Görüntüleyicisi** araç, Microsoft Excel'i çalıştırmak gerekebilir ise, etkinleştirmeden önce zaman. Visual Studio Enterprise yük testi eklentisi bilgisayarınıza Visual Studio Enterprise yüklü olduğunda, Microsoft Excel için kopyalanır; Ancak, Microsoft Excel için eklenti yükleme işleminin tamamlanması için çalıştırmanız gerekir.

      Microsoft Excel açılır **bir yük testi Rapor Sihirbazı Oluştur**.

   **VEYA**

   1. Microsoft Excel'i açın, **yük testi** sekmesinde **Office** Şerit ve ardından **yük testi raporu**.

       **Bir yük testi Rapor Sihirbazı Oluştur** görünür.

   2. İçinde **yük testlerini içeren veritabanını Seç** sayfasındaki **sunucu adı**, yük testi sonuçlarını içeren sunucunun adını yazın.

   3. İçinde **Databasename** aşağı açılan listesinde, yük testi sonuçlarını içeren veritabanını seçin.

3. İçinde **nasıl raporunuzu oluşturmak istiyorsunuz** sayfasında, **rapor oluşturma** seçin ve seçilen **sonraki**.

4. İçinde **hangi türde rapor oluşturmak istiyorsanız** sayfasında, **eğilim** seçin ve seçilen **sonraki**.

5. İçinde **Enter yük testi rapor ayrıntılarını** sayfasında, rapor için bir ad yazın **rapor adı**.

6. Seçin ve raporunu oluşturmak istediğiniz yük testini seçin **sonraki**.

7. İçinde **raporunuz için çalıştırmaları seçin** sayfasındaki **rapora eklemek için bir veya daha fazla çalıştırma seçin**, seçin ve raporda karşılaştırmak istediğiniz yükleme testi sonuçlarını seçin **sonraki**.

8. İçinde **raporunuz için sayaçlar seçin** sayfasındaki **rapora eklenecek bir veya daha fazla sayaç seçin**, sayaçların Genişletilebilir listesi, raporunuzu özelleştirmek kullanılabilirdir. Seçin ve trend çözümlemesi için karşılaştırmak istediğiniz sayaçları seçin **son**.

9. Rapor raporda oluşturulan çeşitli Excel çalışma kitabı sekmeleri bağlantılara sahip olan bir içindekiler tablosu ile oluşturulur. Bağlantılar eğilim raporu için seçili sayaçları temel alır. 7. adımda seçtiğiniz varsayılan sayaçları bırakılırsa, örneğin, ardından raporun sunulan veri 7. adımda listelenen her sayaç için Excel'de ayrı sekmeler oluşturur. Her sayaç için oluşturulan veri, eğilim stili grafiklerde sunulur.

   > [!TIP]
   > Daha iyi raporlar için çeşitli özellikler, daha zengin raporlara olanak tanıyan bir web performans testleri ve yük testleri de kullanılabilir. Sayfa istekleri raporlarda sunulan iki özelliğe sahiptir: hedef ve raporlama adı. Sayfa yanıt zamanı hedefe yönelik bildirilir ve raporlama adı URL'nin raporlarında yerine kullanılacak. Sayaç Kümelerini Yönet altında çalıştırma ayarları yük testinde özelliği bilgisayar etiketleri rapor makina adlarında sunulur. Bu rapor belirli bir makinenin rolünü tanımlamak kullanışlıdır.

## <a name="net-framework-security"></a>.NET Framework güvenliği

Yük testi sonuçları ve raporları, bilgisayarınıza veya ağınıza yönelik bir atak yapılandırmak için kullanılabilen duyarlı bilgi içerir. Yük testi sonuçları ve raporları, bilgisayar adları ve bağlantı dizeleri içerir. Ne zaman bunun farkında olmalıdır yük testi raporlarını diğer kişilerle paylaşın.

## <a name="see-also"></a>Ayrıca bkz.

- [Rapor yük testi sonuçlarını test karşılaştırmaları veya eğilim analizi](../test/compare-load-test-results.md)