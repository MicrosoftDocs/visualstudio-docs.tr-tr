---
title: Kodlanmış UI Test Günlüklerini Kullanarak Kodlanmış UI Testlerini Çözümleme
description: Kodlanmış UI test çalıştırmaları hakkında önemli bilgileri filtreleyip kaydeden kodlanmış UI test günlükleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 41863ccc845b0f74c300e927708e238193f223ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934864"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini çözümleme

Kodlanmış UI test günlükleri, kodlanmış UI test çalışmalarınız hakkında önemli bilgileri filtreleyip kaydeder. Günlükler, hata ayıklama sorunlarını hızla sağlayan bir biçimde sunulur.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>1. Adım: günlüğü etkinleştirme

Senaryonuza bağlı olarak, günlüğü etkinleştirmek için aşağıdaki yöntemlerden birini kullanın:

- Test projenizde bir *App.config* dosyası yoksa:

   1. Testinizi çalıştırdığınızda hangi *QTAgent \* . exe* işleminin başlatılmayı saptayın. Bunu yapmanın bir yolu Windows **Görev Yöneticisi**'nde **Ayrıntılar** sekmesini izlerken.

   2. *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\IDE* klasöründe karşılık gelen *. config* dosyasını açın. Örneğin, çalıştıran işlem *QTAgent_40.exe*, *QTAgent_40.exe.config* açın.

   2. **EqtTraceLevel** değerini istediğiniz günlük düzeyi ile değiştirin.

      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Dosyayı kaydedin.

- Test projenizde bir *App.config* dosyası varsa:

  - Projede *App.config* dosyasını açın ve aşağıdaki kodu yapılandırma düğümü altına ekleyin:

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- Test kodundan günlük kaydını etkinleştirin:

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>2. Adım: kodlanmış UI testinizi çalıştırma ve günlüğü görüntüleme

*QTAgent \*.exe.config* dosyasında yapılan DEĞIŞIKLIKLERLE kodlanmış bir UI testi çalıştırdığınızda, **Test Gezgini** sonuçlarında bir çıkış bağlantısı görürsünüz. Günlük dosyaları yalnızca testiniz başarısız olduğunda değil, izleme düzeyi **verbose** olarak ayarlandığında de başarılı testler için değil.

1. **Test** menüsünde **Windows** ' u ve ardından **Test Gezgini**' ni seçin.

2. **Build** menüsünde **Build Solution** öğesini seçin.

3. **Test Gezgini**'nde, çalıştırmak ISTEDIĞINIZ kodlanmış UI testini seçin, kısayol menüsünü açın ve ardından **Testleri Seç**' i seçin.

     Otomatikleştirilmiş testler çalışır ve başarılı veya başarısız olup olmadığını gösterir.

    > [!TIP]
    > **Test Gezginini** görüntülemek için **Test**  >  **pencereleri**' ni ve ardından **Test Gezgini**' ni seçin.

4. **Test Gezgini** sonuçlarında **Çıkış** bağlantısını seçin.

     ![Test Gezgininde çıkış bağlantısı](../test/media/cuit_htmlactionlog1.png)

     Bu, eylem günlüğüne bir bağlantı içeren test için çıktıyı görüntüler.

     ![Kodlanmış UI testinin sonuçları ve çıkış bağlantıları](../test/media/cuit_htmlactionlog2.png)

5. *UITestActionLog.html* bağlantısını seçin.

     Günlük, Web tarayıcınızda görüntülenir.

     ![Kodlanmış UI testi günlük dosyası](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Nasıl yapılır: Microsoft Visual Studio Testleri çalıştırma](/previous-versions/ms182470(v=vs.140))