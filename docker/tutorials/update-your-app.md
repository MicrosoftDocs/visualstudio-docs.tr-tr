---
title: 'Docker öğreticisi - 2. Bölüm: Uygulamalarınızı güncelleştirme'
description: Docker uygulamasının nasıl güncelleştirilmelerini açıklar.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 43034ff2e65564cc8af2710b796b76996f21f4c8
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222779"
---
# <a name="update-the-app"></a>Uygulamayı güncelleştirme

Küçük bir özellik isteği olarak, herhangi bir todo listesi öğeniz olduğunda ürün ekibi tarafından "boş metni" değiştirmeniz istendi. Bunu aşağıdakine geçiş yapmak için:

> Henüz todo öğelerine sahip değilsiniz! Yukarıya bir tane ekleyin!

Oldukça basit, değil mi? Şimdi bu değişikliği gidelim.

## <a name="update-the-source-code"></a>Kaynak kodu güncelleştirme

1. dosyasında, `src/static/js/app.js` 56. satırı yeni boş metni kullanmak için güncelleştirin.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Daha önce kullanılan komutu kullanarak görüntünün güncelleştirilmiş sürümünü derleme.

    ```bash
    docker build -t getting-started .
    ```

1. Güncelleştirilmiş kodu kullanarak yeni bir kapsayıcı başlatma.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**İşte bu kadar!** Büyük olasılıkla bunun gibi bir hata görmüş olursanız (kimlikler farklı olur):

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

Peki ne oldu? Eski kapsayıcınız hala çalışıyor olduğundan yeni kapsayıcı başlatılamadı. Bunun bir soruna neden olan nedeni, kapsayıcının ana bilgisayar bağlantı noktası 3000'i kullanması ve makinede yalnızca bir işlem (kapsayıcılar dahil) belirli bir bağlantı noktasını dinlemesidir. Bunu düzeltmek için eski kapsayıcıyı kaldırın.

## <a name="replace-the-old-container"></a>Eski kapsayıcıyı değiştirme

Bir kapsayıcıyı kaldırmak için önce durdurulmuş olması gerekir. Durdurulduktan sonra kaldırılabilir. Eski kapsayıcıyı kaldırmanın iki yolu vardır. En rahat yolunu seçebilirsiniz.

### <a name="remove-a-container-using-the-cli"></a>CLI kullanarak kapsayıcıyı kaldırma

1. komutunu kullanarak kapsayıcının kimliğini `docker ps` elde edin.

    ```bash
    docker ps
    ```

1. Kapsayıcıyı `docker stop` durdurmak için komutunu kullanın.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Kapsayıcı durdurulduktan sonra komutunu kullanarak kapsayıcıyı `docker rm` kaldırabilirsiniz.

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> Komuta "zorla" bayrağını ekleyerek kapsayıcıyı tek bir komutta durdurabilir ve `docker rm` kaldırabilirsiniz. Örnek: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-view"></a>Docker görünümünü kullanarak kapsayıcıyı kaldırma

uzantı uzantısını VS Code, iki tıklamayla kapsayıcıyı kaldırabilirsiniz! Kapsayıcı kimliğini aramadan kaldırmaktan kesinlikle çok daha kolaydır.

1. Uzantı açıkken kapsayıcıya gidin ve sağ tıklayın.

1. Kaldır **seçeneğine** tıklayın.

1. Kaldırma işlemini onaylayın ve işlemi tamamlayın!

![Docker görünümü - kapsayıcıyı kaldırma](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Güncelleştirilmiş uygulama kapsayıcısı başlatma

1. Şimdi güncelleştirilmiş uygulamanıza başlayabilirsiniz.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Tarayıcınızı [http://localhost:3000](http://localhost:3000) yenileyin; güncelleştirilmiş yardım metninizi görüyor olun!

![Güncelleştirilmiş boş metinle güncelleştirilmiş uygulama](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Özet

Bir güncelleştirme derlemeyi tamamlaya kadar fark etmiş olabileceğiniz iki şey vardı:

- Todo listenizin tüm mevcut öğeleri kayboldu! Bu çok iyi bir uygulama değil! Kısa süre içinde bu konu hakkında konuşacağız.
- Böyle *küçük bir değişiklik* için birçok adım vardı. Yaklaşan bir bölümde, her değişiklikte yeni bir kapsayıcıyı yeniden oluşturmanıza ve başlatmaya gerek kalmadan kod güncelleştirmelerini nasıl göreceğinizi öğrenirsiniz.

Kalıcılık hakkında bilgi öğrenmeden önce bu görüntüleri diğerleriyle nasıl paylaşabilirsiniz?

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Uygulamanızı paylaşma](share-your-app.md)
