---
title: Kodlanmış UI Test Günlüklerini Kullanarak Kodlanmış UI Testlerini Çözümleme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9c31dd90981cf39f1de296b2c96d6064afc730b4
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896685"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Kodlanmış UI test günlüklerini çözümleme kodlanmış UI testleri kullanarak

Kodlanmış UI test günlüklerini filtre ve kayıt kodlanmış UI testleri hakkında önemli bilgiler çalıştırır. Günlükler, sorunları hızlı bir şekilde hata ayıklama için izin veren bir biçiminde gösterilir.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>1. adım: günlük kaydını etkinleştirme

Senaryonuza bağlı olarak, günlüğü etkinleştirmek için aşağıdaki yöntemlerden birini kullanın:

- Hedef .NET Framework sürüm 4 olmadan *App.config* test projesinde dosya:

   1. Açık *QTAgent32_40.exe.config* dosya. Varsayılan olarak, bu dosya bulunan *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

   2. Değeri için gt;System.Diagnostics istediğiniz günlük düzeyine değiştirin.

   3. Dosyayı kaydedin.

- Hedef .NET Framework sürüm 4.5 olmadan *App.config* test projesinde dosya:

   1. Açık *QTAgent32.exe.config* dosya. Varsayılan olarak, bu dosya bulunan *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

   2. İstediğiniz günlük düzeyine gt;System.Diagnostics değerini değiştirin.

   3. Dosyayı kaydedin.

- *App.config* dosyasıdır ve test projesinde mevcut:

    - Açık *App.config* dosya projede ve yapılandırma düğümü altında aşağıdaki kodu ekleyin:

      ```xml
      <system.diagnostics>
        <switches>
          <add name="EqtTraceLevel" value="4" />
        </switches>
      </system.diagnostics>`
      ```

- Test kodu günlüğünü etkinleştir:

   <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>2. adım: kodlanmış UI testleri çalıştırmak ve günlüğünü görüntüleyin

Yapılan değişiklikler ile kodlanmış UI testi çalıştırdığınızda *QTAgent32.exe.config* dosya, yerinde bağlantısını bir çıktı görmeniz **Test Gezgini** sonuçları. Yalnızca, test, aynı zamanda için izleme düzeyi için "verbose." olarak ayarlandığında başarılı testleri başarısız olduğunda günlük dosyaları oluşturulur

1.  Üzerinde **Test** menüsünde seçin **Windows** seçip **Test Gezgini**.

2.  Üzerinde **derleme** menüsünde seçin **Çözümü Derle**.

3.  İçinde **Test Gezgini**, kodlanmış UI testi çalıştırmak için kısayol menüsünü açın ve ardından istediğiniz seçin **seçili Testleri Çalıştır**.

     Otomatikleştirilmiş testleri çalıştırın ve geçti veya başarısız olmadığını gösterir.

    > [!TIP]
    > Görüntülenecek **Test Gezgini**, seçin **Test** > **Windows**ve ardından **Test Gezgini**.

4.  Seçin **çıkış** bağlantısını **Test Gezgini** sonuçları.

     ![Test Gezgininde çıkış bağlantı](../test/media/cuit_htmlactionlog1.png)

     Bu eylem günlüğü bağlantısını içeren test için çıktıyı görüntüler.

     ![Sonuçları ve kodlanmış UI testi çıkış bağlantıları](../test/media/cuit_htmlactionlog2.png)

5.  Seçin *UITestActionLog.html* bağlantı.

     Günlük, web tarayıcınızda görüntülenir.

     ![Kodlanmış UI testi günlüğü dosyası](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Ayrıca bkz.

- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Nasıl yapılır: Microsoft Visual Studio'dan testler çalıştırma](https://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)