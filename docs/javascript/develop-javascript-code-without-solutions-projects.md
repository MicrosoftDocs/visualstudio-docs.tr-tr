---
title: Bir çözüm veya proje Visual Studio'da JavaScript kodu yazma
titleSuffix: ''
description: Visual Studio kodu olmadan bir proje dosyası veya çözüm dosyası bir bağımlılık oluşturmak için destek sağlar.
ms.custom: seodec18
ms.date: 09/24/2018
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
ms.openlocfilehash: a68174fd9cc1efcdde068448445adcf68fe36f63
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058460"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Visual Studio'da JavaScript ve TypeScript kodu çözümlerin veya projelerin olmadan geliştirin

Visual Studio 2017'yi tanıtır yeteneği [projeler veya çözümler olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), kod klasörünü açın ve hemen yeniden düzenleme, IntelliSense, arama gibi zengin Düzenleyicisi desteği ile çalışmaya başlamak sağlar hata ayıklama ve daha fazlası.
Bu özelliklerin yanı sıra, Visual Studio için Node.js araçları npm betikleri çalıştırma TypeScript dosyaları oluşturma ve npm paketleri yönetme desteğini ekler.

Başlamak için seçin **klasörünü Aç** Başlat beliren sayfasından Visual Studio'yu açın veya seçebilirsiniz **dosya** > **açın**  >  **Klasör** araç çubuğundan. Çözüm Gezgini tüm dosyaları klasöründe görüntüler ve düzenlemeye başlamak için dosyalardan birini açın. Arka planda, Visual Studio hata ayıklama özelliklerini etkinleştirme npm ve derleme dosyaları dizinler.

> [!IMPORTANT]
> Birçok npm tümleştirmesi dahil olmak üzere bu makalede açıklanan özellikler, Visual Studio 2017 sürüm 15,8 gerektirir.

## <a name="npm-integration"></a>npm tümleştirmesi

Açtığınız klasör içeriyorsa bir *package.json* dosyası, sağ *package.json* npm için belirli bir bağlam menüsü (kısayol menüsü) göstermek için. 

![Çözüm Gezgini'nde npm menüsü](../javascript/media/solution-explorer-npm-ctx.png) 

Kısayol menüsünde, aynı npm yüklü paketleri yönetebilirsiniz şekilde [npm paketlerini yönetme](npm-package-management.md) bir proje dosyasını kullanırken.

Ayrıca, menü ayrıca tanımlanan betikleri çalıştırmanıza olanak tanır `scripts` öğesinde *package.json*. Bu betikler kullanılabilir Node.js sürümünü kullanacak `PATH` ortam değişkeni. Betikleri, yeni bir pencerede çalıştırın. Bu derleme yürütün veya komut dosyaları çalıştırmak için harika bir yoludur.

## <a name="build-and-debug"></a>Derleme ve hata ayıklama

### <a name="packagejson"></a>Package.JSON
Varsa *package.json* klasöründe belirtir bir `main` öğesi **hata ayıklama** komutu için sağ tıklama kısayol menüsünde kullanılabilir olacak *package.json*. Bu seçeneğe tıkladığınızda başlayacak *node.exe* kendi bağımsız değişkeni olarak belirtilen komut dosyası.

### <a name="javascript-files"></a>JavaScript dosyaları
Dosyaya sağ tıklayarak ve seçerek JavaScript dosyalarının hatalarını ayıklayabilir **hata ayıklama** kısayol menüsünden. Bu başlatır *node.exe* bağımsız değişken olarak bu JavaScript dosya ile.

### <a name="typescript-files-and-tsconfigjson"></a>TypeScript dosyaları ve tsconfig.json
Yoksa hiçbir *tsconfig.json* mevcut klasöründe bir TypeScript dosyası oluşturun ve bu dosyayı hata ayıklamak için bir kısayol menü komutları görmek için sağ. Bu komutları kullanmak, oluşturmadan veya ile hata ayıklama *tsc.exe* varsayılan seçeneklerle. (Derleme dosyası, hata ayıklama yapılabilmesi gerekir.)

> [!NOTE]
> TypeScript kodu oluştururken, en yeni sürümü yüklü kullandığımız `C:\Program Files (x86)\Microsoft SDKs\TypeScript`.

Varsa bir *tsconfig.json* klasörde mevcut dosya, bir TypeScript dosyası bu TypeScript dosyasında hata ayıklama için bir menü komutu görmek için sağ tıklayın. Yalnızca seçeneğin görünür hiçbir `outFile` belirtilen *tsconfig.json*. Varsa bir `outFile` belirtilirse, sağ tıklayarak bu dosyaya ayıklayabilir *tsconfig.json* ve doğru seçeneğini belirleyin. `tsconfig.json` Dosya Ayrıca, size bir derleme seçeneği derleyici seçenekleri belirtmenizi sağlar.

> [!NOTE]
> Hakkında daha fazla bilgi bulabilirsiniz *tsconfig.json* içinde [tsconfig.json TypeScript el kitabı sayfası](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="unit-tests"></a>Birim testleri
Bir test kök belirterek Visual Studio'da birim test tümleştirmesini etkinleştirebilirsiniz, *package.json*:

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

Test Çalıştırıcısını kullanmak için hangi test çerçevesini belirlemek için yerel olarak yüklü paketleri numaralandırır.
Test Çalıştırıcısı desteklenen çerçeveler hiçbiri tanınır, varsayılan *ExportRunner*. Desteklenen diğer çerçeveler şunlardır:
* Mocha ([mochajs.org](http://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Bant ([github.com/substack/tape](https://github.com/substack/tape))

Test Gezgini'ni açtıktan sonra (seçin **Test** > **Windows** > **Test Gezgini**), Visual Studio bulur ve testleri görüntüler.

> [!NOTE]
> Uygulamanız bu ilk uygulama oluşturmanızı sağlayacak TypeScript içinde yazılmışsa test Çalıştırıcısı yalnızca test kökü JavaScript dosyaları sıralar.
