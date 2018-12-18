---
title: 'Nasıl yapılır: Tanılama Veri Bağdaştırıcısı Oluşturma'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 051f5ad7783271c2b0eea26bc3af5c0980f2c1fc
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068308"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Nasıl yapılır: tanılama veri bağdaştırıcısı oluşturma

Oluşturmak için bir *tanılama veri bağdaştırıcısı*, Visual Studio kullanarak bir sınıf kitaplığı oluşturun ve ardından Sınıf Kitaplığı'na Visual Studio Enterprise tarafından sağlanan tanılama veri bağdaştırıcısı API'leri ekleyin. Bir akış veya dosya olarak istediğiniz herhangi bir bilgi Gönder <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> testi çalıştırması sırasında oluşturulan olayları işlerken çerçeve tarafından sağlanan. Akışlar veya dosyalar gönderilen <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> testleriniz bittiğinde test sonuçlarına ekler olarak depolanır. Oluşturursanız bu hatadan test sonuçlarını veya kullandığınızda [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], dosyalar da hataya bağlanır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Burada testlerinizi çalıştırdığınız makineyi veya test altındaki uygulamanızı çalıştırmak için kullandığınız ortamın parçası olan makineyi etkileyen tanılama veri bağdaştırıcısı oluşturabilirsiniz. Örneğin, test makinenizde dosyalar burada testler toplama veya uygulamanız için web sunucusu rolündeki sunan makinedeki dosyaları toplama.

Tanılama veri bağdaştırıcısı Microsoft Test Yöneticisi'ni veya Visual Studio kullanarak test ayarlarınızı oluşturduğunuzda görüntüleyen bir kolay ad verebilirsiniz. Test ayarlarınızı testlerinizi çalıştırdığınızda, ortamınızda hangi makine rolünün belirli tanılama veri bağdaştırıcılarını çalıştıracağını tanımlamanıza olanak sağlar. Test ayarlarınızı oluşturduğunuzda, tanılama veri bağdaştırıcılarınızı yapılandırabilirsiniz. Örneğin, web sunucunuzdan özel günlükleri toplayan tanılama veri bağdaştırıcısı oluşturabilirsiniz. Test ayarlarınızı oluşturduğunuzda, makine veya bu web sunucu rolünü gerçekleştiren makineler üzerinde bu tanılama veri bağdaştırıcısını çalıştırmayı seçebilirsiniz ve oluşturulan son üç günlüğü toplamak üzere test ayarlarınız için yapılandırmayı değiştirebilirsiniz. Test ayarları hakkında daha fazla bilgi için bkz. [test ayarlarını kullanarak tanılama bilgi toplayan](../test/collect-diagnostic-information-using-test-settings.md).

Böylece tanılama veri bağdaştırıcınızın testte o noktada görevleri gerçekleştirebilirsiniz, testlerinizi çalıştırdığınızda olaylar oluşturulur.

> [!IMPORTANT]
> Özellikle, birden çok makina üzerinde test çalıştırmalarına sahip olduğunuzda, farklı iş parçacıkları üzerinde bu olaylar oluşturulabilir. Bu nedenle, olası iş parçacığı sorunlarından haberdar olmalı ve istemeden özel bağdaştırıcının iç verilerini bozuk. Tanılama veri bağdaştırıcınızın güvenli iş parçacığı olduğundan emin olun.

Tanılama veri bağdaştırıcınızı oluştururken kullanabileceğiniz anahtar olayların kısmi bir listesi verilmiştir. Tanılama veri bağdaştırıcısı olaylarının tam listesi için bakınız <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> sınıfı.

|Olay|Açıklama|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Test çalıştırmanızın Başlat|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Test çalıştırmanızın sonu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Test çalıştırmasındaki her testin başlatılması|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Test çalıştırmasındaki her testin sonlandırılması|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Testteki her test adımının Başlat|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Testteki her test adımı sonu|

> [!NOTE]
> El ile test tamamlandığında, hiçbir daha fazla veri koleksiyonu olayları için tanılama veri bağdaştırıcısı gönderilir. Bir test yeniden çalıştırıldığında yeni bir test durumu tanımlayıcısı olması. Bir kullanıcı test sırasında bir testi sıfırlandırırsa (oluşturursa <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> olay), ya değişiklikleri test adımı sonucunu, veri koleksiyonu olayı tanı veri bağdaştırıcısı için gönderilen, ancak test durumu tanımlayıcısı aynı kalır. Test çalışmasının sıfırlandığını belirlemek için tanılama veri bağdaştırıcınızda test çalışması tanımlayıcısını izlemelisiniz.

Test ayarlarınızı oluşturduğunuzda sınıflandırdığınız bilgiyi temel alan bir veri dosyası toplayan tanı veri bağdaştırıcısı oluşturmak için aşağıdaki yordamı kullanın.

Özel yapılandırma Düzenleyicisi içeren tam bir örnek tanılama veri bağdaştırıcısı için bir proje, bkz: [tanılama veri bağdaştırıcısı oluşturmak için örnek proje](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

##  <a name="create-and-install-a-diagnostic-data-adapter"></a>Oluşturma ve tanılama veri bağdaştırıcısı yükleme

### <a name="to-create-and-install-a-diagnostic-data-adapter"></a>Tanılama veri bağdaştırıcısı oluşturmak ve yüklemek için

1. Yeni bir sınıf kitaplığı oluşturun.

   1.  Üzerinde **dosya** menüsünde seçin **yeni**, gelin ve ardından **yeni proje**.

   2.  Gelen **proje türleri**, kullanacağınız dili seçin.

   3.  Gelen **Visual Studio yüklenmiş şablonlar**seçin **sınıf kitaplığı**.

   4.  Tanılama veri bağdaştırıcınız için bir ad yazın.

   5.  Seçin **Tamam**.

2. Bütünleştirilmiş kod Ekle **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

   1.  İçinde **Çözüm Gezgini**, sağ **başvuruları** ve **Başvuru Ekle** komutu.

   2.  Seçin **.NET** bulun **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

   3.  Seçin **Tamam**.

3. Bütünleştirilmiş kod Ekle **Microsoft.VisualStudio.QualityTools.Common**.

   1.  İçinde **Çözüm Gezgini**, sağ **başvuruları** seçip **Başvuru Ekle** komutu.

   2.  Seçin **/.NET**, bulun **Microsoft.VisualStudio.QualityTools.Common.dll**.

   3.  Seçin **Tamam**.

4. Aşağıdaki `using` deyimlerini Sınıf dosyanıza:

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. Ekleme <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> bir tanılama veri bağdaştırıcınız olarak tanımlamak üzere tanı veri bağdaştırıcınız için sınıfa değiştirerek **şirket**, **ürün**, ve **sürüm** ile Tanılama veri bağdaştırıcınız için uygun bilgileri:

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. Ekleme <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> parametreleri tanı veri bağdaştırıcınız için uygun bilgi ile değiştirerek sınıfa özniteliği:

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Bu kolay adı, test ayarları etkinliğinde görüntülenir.

   > [!NOTE]
   > Ayrıca ekleyebilirsiniz <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> belirtmek için `Type` , düzenleyici için kullanılacak özel yapılandırma düzenleyicinizin bu veri bağdaştırıcısı için ve isteğe bağlı olarak Yardım dosyasını belirtmek için.
   >
   > Ayrıca uygulayabilirsiniz <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> , her zaman etkin olması gerektiğini belirtmek için.

7. Tanılama veri bağdaştırıcısı sınıfınız devralmalıdır <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> sınıfına aşağıdaki gibi:

   ```csharp
   public class MyDiagnosticDataAdapter : DataCollector
   ```

8. Yerel değişkenler aşağıdaki şekilde ekleyin:

   ```csharp
   private DataCollectionEvents dataEvents;
   private DataCollectionLogger dataLogger;
   private DataCollectionSink dataSink;
   private XmlElement configurationSettings;
   ```

9. Ekleme <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> yöntemi ve bir **Dispose** yöntemi. İçinde `Initialize` , Initialize yöntemi, veri havuzu, tüm yapılandırma verilerini test ayarları ve istediğiniz olay işleyicileri gibi kaydedersiniz:

    ```csharp
    public override void Initialize(
        XmlElement configurationElement,
        DataCollectionEvents events,
        DataCollectionSink sink,
        DataCollectionLogger logger,
        DataCollectionEnvironmentContext environmentContext)
    {
           dataEvents = events;  // The test events
           dataLogger = logger;  // The error and warning log
           dataSink = sink;      // Saves collected data
           // Configuration from the test settings
           configurationSettings = configurationElement;

           // Register common events for the data collector
           // Not all of the events are used in this class
        dataEvents.SessionStart +=
            new EventHandler<SessionStartEventArgs>(OnSessionStart);
        dataEvents.SessionEnd +=
            new EventHandler<SessionEndEventArgs>(OnSessionEnd);
        dataEvents.TestCaseStart +=
            new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
        dataEvents.TestCaseEnd +=
            new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
    }

    public override void Dispose(bool disposing)
    {
        if (disposing)
        {
            // Unregister the registered events
            dataEvents.SessionStart -=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd -=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart -=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd -=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
        }
    }
    ```

10. Test sırasında üretilen günlük dosyasını toplamak için aşağıdaki olay işleyicisini ve özel yöntemi kullanın:

    ```csharp
    public void OnTestCaseEnd(sender, TestCaseEndEventArgs e)
    {
        // Get any files to be collected that are
        // configured in your test settings
        List<string> files = getFilesToCollect();

        // For each of the files, send the file to the data sink
        // which will attach it to the test results or to a bug
        foreach (string file in files)
        {
            dataSink.SendFileAsync(e.Context, file, false);
        }
    }

    // A private method that returns the file names
    private List<string> getFilesToCollect()
    {
        // Get a namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                configurationSettings.OwnerDocument.NameTable);
        nsmgr.AddNamespace("ns",
            "http://MyCompany/schemas/MyDataCollector/1.0");

        // Find all of the "File" elements under our configuration
        XmlNodeList files =
            configurationSettings.SelectNodes(
                "//ns:MyDataCollector/ns:File");

        // Build the list of files to collect from the
        // "FullPath" attributes of the "File" nodes.
        List<string> result = new List<string>();
        foreach (XmlNode fileNode in files)
        {
            XmlAttribute pathAttribute =
                fileNode.Attributes["FullPath"];
            if (pathAttribute != null &&
                !String.IsNullOrEmpty(pathAttribute.Value))
            {
                result.Add(pathAttribute.Value);
            }
        }

        return result;
    }
    ```

     Bu dosyalar test sonuçlarına eklenir. Oluşturursanız bu hatadan test sonuçlarını veya kullandığınızda [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], dosyalar hataya eklenir.

     Test ayarlarınızda kullanmak üzere veri toplamak üzere kendi düzenleyicinizi kullanmak isterseniz [nasıl yapılır: tanılama veri bağdaştırıcınızın verileri için özel bir düzenleyici oluşturmak](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md).

11. Bir test test ayarlarında yapılandırdığınız kullanıcı göre sona erdiğinde bir günlük dosyasını toplamak için oluşturmalısınız bir *App.config* dosya ve çözümünüze ekleyin. Bu dosya aşağıdaki biçime sahiptir ve tanımlamak tanı veri bağdaştırıcınızın URI'sini içermelidir. "Şirket/ProductName/Version" için gerçek değerleri değiştirin.

    > [!NOTE]
    > Ardından, tanılama veri bağdaştırıcınız için herhangi bir bilgi yapılandırmak ihtiyacınız yoksa, bir yapılandırma dosyası oluşturmak gerekmez.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <configSections>
        <section name="DataCollectorConfiguration" type="Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationSection, Microsoft.VisualStudio.QualityTools.ExecutionCommon, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a "/>
      </configSections>
      <DataCollectorConfiguration xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010">
        <DataCollector typeUri="datacollector://MyCompany/MyProduct/1.0">
          <DefaultConfiguration>
            <!-- Your default config settings -->
            <Binaries>
              <Binary FullPath="C:\Example\Example.dll"/>
              <Binary FullPath="\\Server2\Example2.dll"/>
            </Binaries>
            <Symbols>
              <Symbol FullPath="\\ExampleServer\ExampleSymbol.pdb"/>
            </Symbols>
          </DefaultConfiguration>
        </DataCollector>
      </DataCollectorConfiguration>
    </configuration>
    ```

    > [!NOTE]
    > Varsayılan yapılandırma öğesi, ihtiyaç duyduğunuz herhangi bir veri içerebilir. Kullanıcı test ayarlarında tanı veri bağdaştırıcısı yapılandırmazsa çalıştırıldığında sonra varsayılan veri tanılama veri bağdaştırıcınızı geçirilecektir. Eklediğiniz XML, çünkü `<DefaultConfigurations>` bölümü, bildirilen şemanın parçası olması olası değildir, ürettiği herhangi bir XML hatasını yoksayabilirsiniz.
    >
    > Yapılandırma dosyalarını, yükleme dizinine dayanan aşağıdaki yolda diğer örnekleri vardır: *Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors*.

     Test ayarlarınızı testlerinizi çalıştırdığınızda kullanacağınız ortam için yapılandırma hakkında daha fazla bilgi için bkz. [el ile testlerde (Azure Test planları) tanılama verilerini toplama](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

     Yapılandırma dosyasını yükleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel tanılama veri bağdaştırıcısı yükleme](../test/how-to-install-a-custom-diagnostic-data-adapter.md)

12. Tanılama veri bağdaştırıcı derlemenizi oluşturmak için çözümünüzü derleyin.

13. Özel düzenleyicinizi yükleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel tanılama veri bağdaştırıcısı yükleme](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

14. Test ayarlarınızı testlerinizi çalıştırdığınızda kullanacağınız ortam için yapılandırma hakkında daha fazla bilgi için bkz. [el ile testlerde (Azure Test planları) tanılama verilerini toplama](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

15. Tanılama veri bağdaştırıcınızı seçmek için önce varolan test ayarlarını seçin veya Microsoft Test Yöneticisi ya da Visual Studio yeni bir tane oluşturmanız gerekir. Bağdaştırıcı görüntülenir **veri ve tanılama** test ayarlarınızı sınıfa atadığınız yakın ad ile sekmesindeki.

16. Bu test ayarları etkin olarak ayarlanmış. Test ayarları hakkında daha fazla bilgi için bkz. [test ayarlarını kullanarak tanılama bilgi toplayan](../test/collect-diagnostic-information-using-test-settings.md).

17. Seçilen tanılama veri bağdaştırıcısıyla test ayarlarını kullanarak testlerinizi çalıştırın.

    Belirttiğiniz veri dosyası test sonuçlarınıza eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Test ayarlarını kullanarak tanılama bilgileri Topla](../test/collect-diagnostic-information-using-test-settings.md)
- [El ile testlerde (Azure Test planları) tanılama verilerini toplayın](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [(Azure Test planları) test sırasında tanılama verilerini toplayın](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Nasıl yapılır: tanılama veri bağdaştırıcınızın verileri için özel bir düzenleyici oluşturma](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)