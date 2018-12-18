---
title: VSTest.Console.exe komut satırı seçenekleri
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: gewarren
author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4394fe8d7920f4127f5043808003d400bc991590
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220976"
---
# <a name="vstestconsoleexe-command-line-options"></a>VSTest.Console.exe komut satırı seçenekleri

*VSTest.Console.exe* testleri çalıştırmak için komut satırı aracıdır. Komut satırında herhangi bir sırada çeşitli seçenekleri belirtebilirsiniz. Bu seçenekler listelenen [genel komut satırı seçenekleri](#general-command-line-options).

> [!NOTE]
> Visual Studio içindeki MSTest bağdaştırıcısı eski modda da çalışır (testleri çalıştırmak için eşdeğer *mstest.exe*) uyumluluk için. Eski modda da TestCaseFilter özellik yararlanamaz. Bağdaştırıcı eski moda geçebilir, bir *testsettings* dosya belirtilir, **forcelegacymode** ayarlanır **true** içinde bir *runsettings* Dosya ya da kullanarak öznitelikleri gibi **HostType**.
>
> ARM mimarisi tabanlı bir makinede otomatik testleri çalıştırmak için kullanmanız gerekir *VSTest.Console.exe*.

## <a name="general-command-line-options"></a>Genel komut satırı seçenekleri

İçin tüm seçenekleri aşağıdaki tabloda *VSTest.Console.exe* ve kısa açıklamalarını. Yazarak benzer bir özeti görebilirsiniz `VSTest.Console/?` komut satırına.

| Seçenek | Açıklama |
|---|---|
|**[*test dosya adları*]**|Belirtilen dosyalardan testleri çalıştırın. Birden çok test dosyası adlarının boşluklarla ayırın.<br />Örnekler: `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/ Settings: [*dosya adı*]**|Testleri veri toplayıcılar gibi ek ayarlar ile çalıştırın.<br />Örnek: `/Settings:Local.RunSettings`|
|**/ Tests: [*test adı*]**|Testleri sağlanan değerlerle içeren adları ile çalıştırın. Birden çok değer sağlamak için bunları virgüllerle ayırın.<br />Örnek: `/Tests:TestMethod1,testMethod2`<br />**/Test** komut satırı seçeneği ile kullanılamaz **/testcasefilter** komut satırı seçeneği.|
|**/ Parallel**|Testleri paralel olarak yürütüleceğini belirtir. Varsayılan olarak makine üzerindeki tüm mevcut çekirdekler kullanılabilir. Kullanılacak çekirdek sayısı bir ayar dosyası kullanılarak yapılandırılabilir.|
|**/ Enablecodecoverage**|Veri tanılama bağdaştırıcısı CodeCoverage'test çalıştırması sağlar.<br />Varsayılan ayarlar kullanılır belirtilmezse ayar dosyası kullanılarak.|
|**/ Inısolation**|Testleri yalıtılmış bir işlemde çalıştırır.<br />Bu yalıtım sağlar *vstest.console.exe* büyük olasılıkla daha az bir hata sırasında durdurulması işlemi, ancak testleri daha yavaş çalıştırabilirsiniz.|
|**/ UseVsixExtensions**|Bu seçenek yapar *vstest.console.exe* işlem kullanın veya (varsa) test çalıştırmasında yüklü VSIX uzantılarını atlayabilirsiniz.<br />Bu seçeneği kullanım dışı bırakılmıştır. Bu seçenek, Visual Studio'nun sonraki ana sürümüne başlangıç kaldırılabilir. Bir NuGet paketi olarak sunulan uzantıları kullanma için taşıyın.<br />Örnek: `/UseVsixExtensions:true`|
|**/ TestAdapterPath: [*yolu*]**|Zorlar *vstest.console.exe* işleminin test çalıştırmasında özel test bağdaştırıcılarını belirtilen yoldan (varsa) kullanın.<br />Örnek: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/ Platform: [*platform türü*]**|Test çalıştırması için kullanılacak hedef platform mimarisi.<br />Geçerli değerler şunlardır: x86, x64 ve ARM.|
|**/ Framework: [*framework sürümü*]**|Test çalıştırması için kullanılacak hedef .NET Framework sürümü.<br />Geçerli değerler Framework35, Framework40 framework45'tir ve FrameworkUap10:.<br />Hedef Framework'ü olarak belirtilmişse **Framework35**, CLR 4.0 "uyumlu olacak şekilde basitleştirip modu" testleri çalıştırın.<br />Örnek: `/Framework:framework40`|
|**/ TestCaseFilter: [*ifade*]**|Verili ifadeyle eşleşen testler çalıştırın.<br />< ifade\> biçimi, < özellik\>= < değer\>[\|< ifade\>].<br />Örnek: `/TestCaseFilter:"Priority=1"`<br />Örnek: ' / TestCaseFilter: "TestCategory = gece|FullyQualifiedName=Namespace.ClassName.MethodName"'<br />**/Testcasefilter** komut satırı seçeneği ile kullanılamaz **/test** komut satırı seçeneği. <br />Oluşturma ve ifadeleri kullanma hakkında daha fazla bilgi için bkz: [test çalıştırması filtresini](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Kullanım bilgilerini görüntüler.|
|**/ Logger: [*URI/friendlyname*]**|Test sonuçları için bir Günlükçü belirtin.<br />Örnek: sonuçları bir Visual Studio Test sonuçları dosyası (TRX) oturum açmak için kullanmak **/Logger:trx**.<br />Örnek: Team Foundation Server test sonuçlarını yayımlamak için TfsPublisher kullanın:<br />**/Logger:TfsPublisher;**<br />**Koleksiyon = < url proje\>;**<br />**BuildName = < yapı adı\>;**<br />**TeamProject = < proje adı\>;**<br />**[; Platform = < varsayılan değer: "Herhangi bir CPU" >]**<br />**[; Flavor = < varsayılan değer: "Debug" >]**<br />**[; RunTitle = < başlık\>]**|
|**/ ListTests: [*dosya adı*]**|Testleri verili test kapsayıcısından bulunan listeler.|
|**/ ListDiscoverers**|Yüklü test bulucuları listeler.|
|**/ ListExecutors**|Yüklü test yürütücüleri listeler.|
|**/ ListLoggers**|Yüklü test günlüğü oluşturucuları listeler.|
|**/ ListSettingsProviders**|Yüklü test ayar sağlayıcılarını listeler.|
|**/ Sorumlu**|Bunlar yürütüyorsunuz gibi testler izler ve test ana işlem kilitlenirse sıralarını yürütme testleri adları en fazla yayar ve kilitlenme zamanında çalıştıran belirli bir teste de dahil olmak üzere. Bu çıkış, sorunlu test yalıtmak ve daha iyi tanılamak kolaylaştırır. [Daha fazla bilgi](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/ Diag: [*dosya adı*]**|Belirtilen dosyaya Tanılama izleme günlüklerini yazar.|
|**/ ResultsDirectory: [*yolu*]**|Test sonuçları dizinini belirtilen yolda oluşturulur Aksi takdirde bulunmaktadır.<br />Örnek: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ ParentProcessId: [*ParentProcessId*]**|Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.|
|**/ Bağlantı noktası: [*bağlantı noktası*]**|Yuva bağlantısı ve olay iletileri almak için bağlantı noktası.|
|**/ Toplama: [*dataCollector friendlyName*]**|Test çalıştırması için veri toplayıcısını etkinleştirir. [Daha fazla bilgi](https://aka.ms/vstest-collect).|

> [!TIP]
> Seçenekler ve değerler büyük küçük harfe duyarlı değildir.

## <a name="examples"></a>Örnekler

Çalıştırmak için söz dizimi *VSTest.Console.exe* olan:

`Vstest.console.exe [TestFileNames] [Options]`

Aşağıdaki komutu çalıştırmaları *VSTest.Console.exe* test kitaplığının **Testprojem.dll**:

```cmd
vstest.console.exe myTestProject.dll
```

Aşağıdaki komutu çalıştırmaları *VSTest.Console.exe* birden çok test dosyalarıyla. Test dosyası adlarının boşluklarla ayırın:

```cmd
Vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Aşağıdaki komutu çalıştırmaları *VSTest.Console.exe* birçok seçeneği. Testleri çalıştırır *myTestFile.dll* belirtilen yalıtılmış bir işlem ve kullanımları ayarları dosyasında *Local.RunSettings* dosya. Ayrıca, işaretlenmiş testlerini yalnızca çalışır "Öncelik = 1" ve sonuçları bir *.trx* dosya.

```cmd
vstest.console.exe  myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```
