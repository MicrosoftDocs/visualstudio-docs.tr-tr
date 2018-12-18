---
title: Linting R kodu
description: Visual Studio'nun yapı içinde linting lint seçenekleri dahil olmak üzere, R desteği ile çalışmayı öğrenin.
ms.date: 07/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 4eaeb0165c049b035555fa63130746baa5fa208f
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978303"
---
# <a name="lint-r-code-in-visual-studio"></a>Visual Studio'da lint R kodu

Bir lint alacaklardır boşluk gibi diğer kod gürültü olası hataları ve biçimlendirme sorunları ortaya çıkarmak için kod analiz eder. Bir lint kullanarak da tanımlayıcıları nasıl adlandırıldığı gibi belirli kodlama kurallarını teşvik yardımcı olur. Bu tür kuralları içinde takımlar ve işbirliğine dayalı diğer durumlarda yararlı olur.

R araçları için Visual Studio (RTVS) R davranışını çeşitli seçenekler ve bu makalede açıklanan aracılığıyla denetlenir, bir yerleşik lint sağlar. Bu seçenekler bulunan **Araçları** > **seçenekleri** > **metin düzenleyici** > **R**  >  **Lint**.

Lint, varsayılan olarak devre dışıdır. Povolit lint ayarlayın **tüm** > **etkinleştirme lint** seçeneğini **True**.

Siz yazarken etkin olduğunda, lint aracı Düzenleyicisi'nde çalışır. Sorunlar, yeşil dalgalı çizgiler olarak görüntülenir. Aşağıdaki grafikte, örneğin, RTVS kullanımı dahil olmak üzere altı lint sorunları belirlemiştir `=` yerine `<-` atama, işlev bağımsız değişkenlerinin etrafındaki boşluğu olmaması için baş harfleri büyük ve büyük harf tanımlayıcıları ve noktalı virgül kullanımını kullanın . Bir sorun geldiğinizde, bir açıklama sağlar.

![Lint çıkış R kodu örnekleri](media/linting-01.png)

Genellikle, bir proje veya dosya gereksinimlerine bağlı olarak lint seçenekleri de değiştirin. Örneğin, bir çevrimiçi kursu'nden örnek kodu kullanabilirsiniz `=` yerine `<-` Pascal harf tanımlayıcıları ile birlikte. Bu gibi durumlarda varsayılan lint seçenekleri bayrak çünkü bu tür kod sık kullanılan bir lint uyarılarını gösterir. Kodla çalışırken, daha sonra her örneği düzeltme zaman harcadığı yerine seçenekleri devre dışı bırakabilirsiniz.

## <a name="assignment-group"></a>Grup ataması

| Seçenek | Varsayılan değer | Lint etkisi |
| --- | --- | --- |
| **Zorla \<-** | **TRUE** | Ne zaman tanımlayan `<-` ataması için kullanılmaz. |

## <a name="naming-group"></a>Grup adlandırma

Bu seçenekler farklı adlandırma kurallarını kullanmasını tanımlayıcıları bayrağı:

| Seçenek | Varsayılan değer | Lint etkisi |
| --- | --- | --- |
| **CamelCase bayrak** | **False** | Bayrakları tanımlayıcıları camelCase kullanın. |
| **Bayrağı uzun adları** | **False** | Tanımlayıcı adları aşan bayrakları **en fazla ad uzunluğu** ayarı. |
| **Birden çok nokta bayrak** | **TRUE** | Birden çok nokta kullanmak bayrakları tanımlayıcıları. |
| **PascalCase bayrak** | **TRUE** | Bayrakları tanımlayıcıları PascalCase kullanın. |
| **Snake_case bayrak** | **False** | Bayrakları tanımlayıcılar alt çizgi kullanın. |
| **Büyük harfli bayrağı** | **TRUE** | Tümü büyük harf kullanın bayrakları tanımlayıcıları. |
| **En fazla ad uzunluğu** | **32** | İle uygulanan uzunluğu **bayrak uzun adları** ayarı. |

## <a name="spacing-group"></a>Aralık grubu

Her biri ayarlanmışsa, bu seçenekler **True** varsayılan olarak, burada lint aralığı sorunları tanımlar denetim: önce açma ve kapatma küme konumlarını işleçler etrafındaki virgülün yanındaki işlev adları boşluk sonra (ve iç boşluk ().

## <a name="statements-group"></a>Grup ifadeleri

| Seçenek | Varsayılan değer | Lint etkisi |
| --- | --- | --- |
| **Birden çok** | **TRUE** | Birden çok deyime aynı çizgi üzerinde olduğunda tanımlar. |
| **Noktalı virgül** | **TRUE** | Noktalı virgül kullanımları tanımlar. |

## <a name="text-group"></a>Metin grubu

| Seçenek | Varsayılan değer | Lint etkisi |
| --- | --- | --- |
| **Satır uzunluğu sınırı** | **False** | Daha uzun satırları lint bayraklar ayarlar **en fazla satır uzunluğu** seçeneği. |
| **En fazla satır uzunluğu** | **80** | Satır uzunluğu tarafından uygulanan ayarlar **satır uzunluğu sınırı** seçeneği. |

## <a name="whitespace-group"></a>Boşluk grubu

Her biri ayarlanmışsa, bu seçenekler **True** varsayılan olarak, burada lint boşluk sorunları tanımlar denetimi: kullanımı sekmeler, çift-tırnak, boş satırları öndeki ve sondaki kullanımı.