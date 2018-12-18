---
title: Kodlanmış UI testleri, kodlanmış UI Test günlüklerini kullanarak çözümleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: 15
ms.author: gewarren
manager: douge
ms.openlocfilehash: e492f3bfaf725c157060a23778e1f1725bb88ee3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188750"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Kodlanmış UI Test Günlüklerini Kullanarak Kodlanmış UI Testlerini Çözümleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI test günlüklerini filtre ve kayıt kodlanmış UI testleri hakkında önemli bilgiler çalıştırır.  
  
 **Gereksinimler**  
  
-   Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>Neden bunu yapmam gerekir?  
 Günlükler, sorunları hızlı bir şekilde hata ayıklama için izin veren bir biçiminde gösterilir.  
  
## <a name="how-do-i-do-this"></a>Bunu nasıl yapmalıyım?  
  
### <a name="step-1-enable-logging"></a>1. adım: günlük kaydını etkinleştirme  
 Senaryonuza bağlı olarak, günlüğü etkinleştirmek için aşağıdaki yöntemlerden birini kullanın.  
  
-   Hedef .NET Framework sürüm 4 ile test projesinde App.config dosyası yok  
  
    -   Açık **QTAgent32_40.exe.config** dosya.  
  
         Varsayılan olarak, bu dosya bulunan  **\<drvie >: \Program Files (x86) \Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         Değeri için gt;System.Diagnostics istediğiniz günlük düzeyine değiştirin.  
  
         Dosyayı kaydedin.  
  
-   Hedef .NET Framework sürüm 4.5 ile test projesinde App.config dosyası yok  
  
    -   Açık **QTAgent32.exe.config** dosya.  
  
         Varsayılan olarak, bu dosya bulunan  **\<drvie >: \Program Files (x86) \Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         İstediğiniz günlük düzeyine gt;System.Diagnostics değerini değiştirin.  
  
         Dosyayı kaydedin.  
  
-   App.config dosyasında test projesinde  
  
    -   Projede App.config dosyasını açın.  
  
         Yapılandırma düğümü altında aşağıdaki kodu ekleyin:  
  
         `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`  
  
-   Test kodu günlüğe yazmayı etkinleştir  
  
    -   <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;  
  
### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>2. adım: kodlanmış UI testleri çalıştırmak ve günlüğünü görüntüleyin  
 Yapılan değişiklikler ile kodlanmış UI testi çalıştırdığınızda **QTAgent32.exe.config** dosya yerinde Test Explorer sonuçları çıkış bağlantı olduğunu görürsünüz. Yalnızca, test, aynı zamanda için izleme düzeyi için "verbose." olarak ayarlandığında başarılı testleri başarısız olduğunda günlük dosyaları oluşturulur  
  
1.  Üzerinde **TEST** menüsünde seçin **Windows** seçip **Test Gezgini**.  
  
2.  Üzerinde **derleme** menüsünde seçin **Çözümü Derle**.  
  
3.  Kodlanmış UI testi çalıştırmak için kısayol menüsünü açın ve ardından istediğiniz test Gezgini'nde seçin **seçili Testleri Çalıştır**.  
  
     Otomatikleştirilmiş testleri çalıştırın ve geçti veya başarısız olmadığını gösterir.  
  
    > [!TIP]
    >  Test Gezgini'nden görüntülemek için **Test menüsü**, işaret **Windows** seçip **Test Gezgini**.  
  
4.  Seçin **çıkış** Test Gezgini sonuçlarında bağlantı.  
  
     ![Test Gezgininde çıkış bağlantı](../test/media/cuit-htmlactionlog1.png "CUIT_HTMLActionLog1")  
  
     Bu eylem günlüğü bağlantısını içeren bir test için çıktıyı görüntüler.  
  
     ![Sonuçları ve kodlanmış UI testi çıkış bağlantılarını](../test/media/cuit-htmlactionlog2.png "CUIT_HTMLActionLog2")  
  
5.  UITestActionLog.html bağlantıyı seçin.  
  
     Günlük, web tarayıcınızda görüntülenir.  
  
     ![Kodlanmış UI testi günlük dosyası](../test/media/cuit-htmlactionlog3.png "CUIT_HTMLActionLog3")  
  
## <a name="q--a"></a>Soru - Yanıt  
  
### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>S: EnableHtmlLogger anahtarına ne oldu?  
 Visual Studio'nun önceki sürümlerinde, vardı iki daha fazla yapılandırma ayarları içinde kodlanmış UI testi Html Günlükçü etkinleştirmek için:  
  
```  
  
<add key="EnableHtmlLogger" value="true"/>  
  
<add key="EnableSnapshotInfo" value="true"/>  
  
```  
  
 Bu ayarlar hem de Visual Studio 2012 sürümünden itibaren kullanım dışı bırakıldı. Gt;System.Diagnostics HtmlLogger etkinleştirmek için değiştirilmesi gereken tek bir ayardır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Nasıl yapılır: Microsoft Visual Studio'dan testler çalıştırma](http://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)



