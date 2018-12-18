---
title: Npm paketlerini package.json ile yapılandırma
description: Npm paket sürümlerini Package.JSON kullanarak belirtin
ms.custom: ''
ms.date: 09/06/2018
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
ms.openlocfilehash: 711d7b65eb329e844fedb0148006cacb1c7a0ebf
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219101"
---
# <a name="packagejson-configuration"></a>package.json yapılandırması

Npm paketlerini birçok ile bir Node.js uygulaması geliştiriyorsanız uyarı veya hata bir veya daha fazla paket güncelleştirilmiş projenizi oluşturduğunuzda çalıştırılacak seyrek değil. Bazı durumlarda, bir sürüm çakışması sonuçları veya paket sürümü kullanım dışıdır. Birkaç Hızlı ipucu yapılandırmanıza yardımcı olması için [package.json](https://docs.npmjs.com/files/package.json) dosya ve uyarılar veya hatalar gördüğünüzde neler olduğunu anlama. Bu tam bir kılavuz değildir *package.json* ve yalnızca npm Paket sürümü oluşturma üzerinde odaklanmıştır.

Npm paket sürüm oluşturma sistemi katı kurallara sahiptir. Sürüm biçimi burada aşağıdaki gibidir:

    [major].[minor].[patch]

Bir paket 5.2.1 sürümü ile uygulamanızda sahip olduğunuz varsayalım. Ana sürüm 5'tir, alt sürüm 2'dir ve düzeltme eki 1'dir.

* Bir ana sürüm güncelleştirmesinde paketi geriye doğru-önemli değişiklikler olduğu gibi uyumsuz, yeni özellikler içerir.
* Geriye dönük uyumlu olan paket için bir ikincil sürüm güncelleştirmede yeni özellikler eklenmiştir önceki paket sürümleri.
* Bir düzeltme eki güncelleştirmede bir veya daha fazla hata düzeltmeleri dahil edilir. Hata düzeltmeleri, her zaman geriye dönük uyumlu olur.

Bu, bazı npm paket özelliklerini bağımlılıklara sahip olduğunu hatalarının ayıklanabileceğini belirtmekte yarar. Örneğin, Web ile yeni bir özellik TypeScript derleyici paket (Yükleyici ts) kullanmak için Ayrıca Web npm paketini ve Web CLI paketini güncelleştirmeniz gerekir mümkündür.

Npm Paket sürümü oluşturma yönetmenize yardımcı olmak için kullanabileceğiniz birkaç gösterimler destekler *package.json*. Bu gösterimler türü uygulamanızda kabul etmek istediğiniz paket güncelleştirmelerini denetlemek için kullanabilirsiniz.

Diyelim ki React kullanıyorsanız ve eklemeniz **react** ve **react dom** npm paketi. Çeşitli yöntemlerle belirtebilirsiniz, *package.json* dosya. Örneğin, bir paket'ün tam sürümünü kullanımı gibi belirtebilirsiniz.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Önceki gösterim kullanarak, npm, her zaman belirtilen tam sürümü 16.4.2 alırsınız.

Özel bir gösterimi, düzeltme eki güncelleştirmeleri (düzeltmeleri) için güncelleştirmeleri sınırlamak için kullanabilirsiniz. Bu örnekte:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

npm tek güncelleştirme için bu düzeltme eki paketi bildirebilen için tilde (~) karakteri kullanın. Bu nedenle, npm react 16.4.2 için 16.4.3 güncelleştirebilirsiniz (veya 16.4.4, vb.), ancak birincil veya ikincil sürüm için bir güncelleştirme kabul etmez. Bu nedenle, 16.4.2 16.5.0 için güncelleştirilmez.

Şapka (^) simgesi, ikincil sürüm numarası, npm güncelleştirebilirsiniz belirtmek için de kullanabilirsiniz.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Bu gösterimi kullanma, npm react 16.4.2 için 16.5.0 güncelleştirebilirsiniz (veya 16.5.1, 16.6.0, vb.), ancak ana sürüm için bir güncelleştirme kabul etmez. Bu nedenle, 16.4.2 17.0.0 için güncelleştirilmez.

Npm paketlerini güncelleştirdiğinde ürettiği bir *paket lock.json* dosya, tüm iç içe paketleri de dahil olmak üzere uygulamanızda kullanılan gerçek npm paket sürümlerini listeler. Sırada *package.json* denetimleri doğrudan bağımlılıkları uygulamanız için bunu denetlemez iç içe geçmiş bağımlılıkları (belirli bir npm paketi için gerekli diğer npm paketleri). Kullanabileceğiniz *paket lock.json* diğer geliştiriciler emin gerekiyorsa ve test ediciler, iç içe geçmiş paketleri de dahil olmak üzere, kullandığınız tam paketleri kullanarak geliştirme döngünüzün dosya. Daha fazla bilgi için [paket lock.json](https://docs.npmjs.com/files/package-lock.json) npm belgelerinde.

Visual Studio için *paket lock.json* dosyası projeye eklenemedi, ancak proje klasöründe bulabilirsiniz.
