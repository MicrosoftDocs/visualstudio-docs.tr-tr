---
title: Birim testi node.js'de
description: Visual Studio, Visual Studio için Node.js araçları kullanarak JavaScript koduna birim testi uygulama desteği sağlar.
ms.custom: ''
ms.date: 06/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 071f64c4239441d3c3fd2c111d1b912175e23316
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766552"
---
# <a name="unit-testing-in-nodejs"></a>Birim testi node.js'de

Node.js için Visual Studio Araçları, yazma ve komut istemine geçiş yapmak için bazı gerek kalmadan daha popüler JavaScript çerçevesini kullanarak birim testleri çalıştırmak izin verin.

Desteklenen çerçeveler şunlardır:
* Mocha ([mochajs.org](http://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Bant ([github.com/substack/tape](https://github.com/substack/tape))
* (Bu çerçeve Visual Studio için Node.js araçları özeldir) Çalıştırıcısı dışarı aktarma

> [!WARNING]
> Bant bir sorun, şu anda bant test çalışmasını engeller. Varsa [çekme isteği #361](https://github.com/substack/tape/pull/361) birleştirilmiş, sorunun çözülmesi gerekir.

Sık kullanılan Çerçevenizi desteklenmiyorsa bkz [birim testi çerçevesi için destek ekleme](#addingFramework) desteği ekleme hakkında bilgi için.

## <a name="write-unit-tests"></a>Birim testleri yazma

Birim testleri projenize eklemeden önce kullanmayı planladığınız framework projenizde yerel olarak yüklü olduğundan emin olun. Bunu yapmak kolaydır [npm paketini yükleme penceresi](npm-package-management.md#npmInstallWindow).

Birim testleri projenize eklemek için tercih edilen yolu oluşturmaktır bir *testleri* klasöründe projenize ve test olarak proje özelliklerinde kök ayarı. Ayrıca, kullanmak istediğiniz test çerçevesi'ı seçmeniz gerekir.

![Kök ve test kümesi test çerçevesi](../javascript/media/unit-test-project-properties.png)

Projenize boş basit testler ekleyebilirsiniz kullanarak **Yeni Öğe Ekle** iletişim kutusu. JavaScript ve TypeScript hem aynı proje içinde desteklenir.

![Yeni birim test Ekle](../javascript/media/unit-test-add-new-item.png)

Mocha birim testi için aşağıdaki kodu kullanın:

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

Birim test seçenekleri proje özelliklerinde belirlemediyseniz emin olmanız gerekir **Test Framework** özelliğinde **özellikleri** penceresindeki Birim test dosyaları için doğru test çerçevesine ayarlayın. Bu, birim testi dosyası şablonları tarafından otomatik olarak gerçekleştirilir.

![Test çerçevesi](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Birim test Seçenekleri tercih ayarlarını tek tek dosyaları öncelikli olacaktır.

Test Gezgini'ni açtıktan sonra (seçin **Test** > **Windows** > **Test Gezgini**), Visual Studio bulur ve testleri görüntüler. Ardından testleri başlangıçta görünür değilse listeyi yenilemek için projeyi yeniden derleyin.

![Test Gezgini](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Kullanmayın `outdir` veya `outfile` seçeneğini *tsconfig.json*, Test Gezgini, birim testleri TypeScript dosyalarda Bul mümkün olmayacaktır.

## <a name="run-tests"></a>Testleri çalıştırma

Visual Studio 2017'de veya komut satırından testleri çalıştırabilirsiniz.

### <a name="run-tests-in-visual-studio-2017"></a>Visual Studio 2017'de testler

Tıklayarak testler çalıştırabilirsiniz **tümünü Çalıştır** Test Gezgini'nde bağlantı. Veya, bir veya daha fazla testleri veya grupları'nı seçerek testleri çalıştırabilirsiniz sağ tıklatıp seçerek **seçili Testleri Çalıştır** kısayol menüsünden. Arka planda testleri çalıştırmak ve Test Gezgini, otomatik olarak güncelleştirir ve sonuçları gösterilmektedir. Ayrıca, ayrıca seçili testleri seçerek ayıklanabilmesi **seçilen Testlerde Hata Ayıkla**.

> [!Warning]
> Düğüm 8 + kullanarak birim testleri hata ayıklama JavaScript için şu anda yalnızca çalışır test dosyalarını kesme noktaları isabet yapamaz TypeScript dosyaları sınayın. Geçici bir çözüm olarak kullanın `debugger` anahtar sözcüğü.

> [!NOTE]
> Şu anda testleri profil oluşturma veya kod kapsamı desteklemiyoruz.

### <a name="run-tests-from-the-command-line"></a>Komut satırından test çalıştırma

Testleri çalıştırdığınız [Geliştirici komut istemi](/dotnet/framework/tools/developer-command-prompt-for-vs) aşağıdaki komutu kullanarak Visual Studio 2017 için:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

Bu komut aşağıdakine benzer bir çıktı gösterir:

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> Belirten bir hata alırsanız *vstest.console.exe* bulunamıyor, açık Geliştirici komut istemi ve normal bir komut istemi değil emin olun.

## <a name="addingFramework"></a>Bir birim testi çerçevesi için destek eklendi

JavaScript kullanarak bulma ve yürütme mantığını uygulama tarafından ek test çerçeveleri için destek ekleyebilirsiniz. Bunun için bir klasör adı altında test çerçevesi ile ekleyerek:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Aşağıdaki iki işlevi dışarı aktarır. aynı ada sahip bir JavaScript dosyasını içermek üzere bu klasör içerir:

* `find_tests`
* `run_tests`

İyi bir örneği için `find_tests` ve `run_tests` uygulamaları Mocha birim testi çerçevesi içindeki uygulamasını bakın:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Kullanılabilir test çerçevesini bulma, Visual Studio başlangıcında gerçekleşir. Visual Studio çalışırken bir çerçeve eklenirse, framework algılamak için Visual Studio'yu yeniden başlatın. Ancak uygulamasına değişiklikler yaparken yeniden başlatmanız gerekmez.

## <a name="unit-tests-in-other-project-types"></a>Birim testleri diğer proje türleri
Node.js projelerinizde yalnızca birim testleri yazma için sınırlı değildir. Eklediğinizde TestFramework ve TestRoot özelliklerinin herhangi biri C# veya Visual Basic projesi bu testlerin listelenmiş ve bunları Test Gezgini penceresini kullanarak çalıştırabilirsiniz.

Bunu etkinleştirmek için Çözüm Gezgini'nde proje düğümüne sağ tıklayın, **projeyi**ve ardından **Düzenle proje**. Ardından Proje dosyasında aşağıdaki iki öğeyi özellik grubuna ekleyin.

> [!NOTE]
> Öğelere ekliyoruz özellik grubunu belirtilen bir koşul sahip olmadığından emin olun.
> Bu, beklenmeyen davranışlara neden olabilir.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Ardından, testlerinizi belirttiğiniz test kök klasörüne ekleyin ve Test Gezgini penceresinden çalıştırmak kullanılabilir olacaktır. Başlangıçta görünmez, projeyi yeniden derleyin gerekebilir.

> [!NOTE]
> Bu, .NET Standard ve .NET Core projeleri için şu anda çalışmıyor.
