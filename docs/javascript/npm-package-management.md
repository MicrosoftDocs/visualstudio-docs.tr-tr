---
title: npm paketlerini yönetme
description: Visual Studio Node.js paket yöneticisini (npm) kullanarak paketleri yönetmenize yardımcı olur.
ms.custom: seodec18
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
ms.openlocfilehash: 297bad186c7f3412e56a5a59f65b82ab9cd35a03
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049661"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Visual Studio'da npm paketlerini yönetme

npm yükleme ve Node.js uygulamalarınızda kullanım için paketleri yönetme sağlar. Npm ile daha fazla bilgi edinmek istiyorsanız bilmiyorsanız, Git [npm belgeleri](https://docs.npmjs.com/).

Visual Studio, npm ve sorunu npm komutları ile kullanıcı Arabirimi aracılığıyla ya da doğrudan etkileşim kurmak kolaylaştırır. Aşağıdaki yöntemleri kullanabilirsiniz:
* [Paketleri Çözüm Gezgini'nden yükleyin.](#npmInstallWindow)
* [Yüklü paketleri Çözüm Gezgini'nden yönetme](#solutionExplorer)
* [Kullanım `.npm` Node.js etkileşimli pencerede komutu](#interactive)

Bu özellikler birlikte çalışır ve proje sistemi ile eşitler ve *package.json* proje dosyasında.

## <a name="npmInstallWindow"></a> Paketleri Çözüm Gezgini'nden yükleyin.

Npm paket yükleme penceresi npm paketlerini yüklemek için en kolay yoludur. Bu pencereye erişmek için sağ **npm** seçin ve proje düğümünde **yükleme yeni npm paketleri**.

![Çözüm Gezgini'nden yeni npm paketini yükleme](../javascript/media/solution-explorer-install-package.png)

Bu pencerede bir paket için arama seçenekleri belirtin ve yükleyin. 

![Arama npm paketi](../javascript/media/search-package.png)

* **Bağımlılık türü** -arasında seçtiğiniz **standart**, **geliştirme**, ve **isteğe bağlı** paketleri. Standart belirtir paketi bir çalışma zamanı bağımlılık olduğunu geliştirme paket yalnızca olduğunu belirten ancak geliştirme sırasında gerekli.
* **Package.JSON dosyasına Ekle** -bu seçeneği kullanım dışı
* **Seçilen sürüm** -yüklemek istediğiniz sürümü seçin.
* **Diğer npm bağımsız değişkenleri** -diğer standart npm bağımsız değişkenleri belirtin. Örneğin, bir sürüm değeri gibi girebilirsiniz `@~0.8` sürümleri listesinde kullanılabilir değil, belirli bir sürümünü yüklemek için.

Çıktı penceresinde npm sekmesinde Yükleme ilerlemesini görebilirsiniz. Bu işlem biraz zaman alabilir.

> [!TIP]
> Örneğin, ilgilendiğiniz, arama sorgusu kapsamlı eklenmesini tarafından kapsamlı paket türü için arama yapabilirsiniz `@types/mocha` mocha için TypeScript tanım dosyalarını aramak için. Ayrıca, TypeScript için tür tanımları yüklerken, TypeScript sürümü belirtebilirsiniz ekleyerek hedefleyen olduğunuz `@ts2.6` npm bağımsız değişken alanında.

## <a name="solutionExplorer"></a>Çözüm Gezgini'nde yüklü paketleri yönetin

npm paketlerini, Çözüm Gezgini'nde gösterilir. Girişler altında **npm** düğüm taklit bağımlılıkları *package.json* dosya.

![Arama npm paketi](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Paket durumu
* ![Yüklü paketleri](../javascript/media/installed-npm.png) -Yüklü ve listelenen package.json
* ![Fazlalık paket](../javascript/media/extraneous-npm.png) - yüklü, ancak açıkça Package.json'da listelenen
* ![Paket eksik](../javascript/media/missing-npm.png) -Not yüklendi, ancak listelenen Package.json'da

Bir paket düğümünü sağ tıklatın veya **npm** düğümünü aşağıdaki eylemlerden birini gerçekleştirin:
* **Eksik paketleri Yükle** içinde listelenen *package.json*
* **Güncelleştirme paketleri** en son sürüme
* **Paket kaldırma** ve kaldırma *package.json*

## <a name="interactive"></a>Node.js etkileşimli pencerede .npm komutu kullanın

Ayrıca `.npm` npm komutları yürütmek için Node.js etkileşimli penceresini komutu. Pencereyi açmak için Çözüm Gezgini'nde projeye sağ tıklayıp seçin **Node.js etkileşimli penceresini aç**.

Pencerede, paketi yüklemek için aşağıdaki gibi komutları kullanabilirsiniz:

`.npm install azure@4.2.3`
 
 > [!Tip]
 > Varsayılan olarak, projenizin giriş dizininde npm yürütülür. Çözümünüz içinde birden çok proje varsa, köşeli ayraç içinde adı veya projesinin yolunu belirtin. 
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Projenize bir package.json dosyası içermiyor kullanırsanız `.npm init -y` varsayılan girişleri ile yeni bir package.json dosyası oluşturmak için. 