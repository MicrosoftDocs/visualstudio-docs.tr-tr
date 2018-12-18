---
title: Snapshot Debugger için başlangıç sayfası
ms.date: 07/14/2018
robots: noindex, nofollow
ms.technology: vs-ide-debug
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7b5b48aeeb0cfcaeed72a06bfb6709892c58de7
ms.sourcegitcommit: e2373d40ca9829cee63519152a97172763471e21
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "39310128"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Anlık görüntü hata ayıklayıcısı ile çalışmaya başlama

Visual Studio Snapshot Debugger artık hizmete bağlıdır ve hatalarını ayıklamaya yardımcı olmak için anlık görüntüleri başlayabilir.

Snapshot Debugger'ı kullanmak için kodunuzda bazı anlık görüntü noktaları ayarlayın, anlık görüntüleri başlatmak için düğmeye tıklayın ve ardından senaryonuzu çalıştırın. Çalıştırmaları kod, bir anlık görüntü noktası ayarladığınız, uygulamanızın bir anlık görüntü alınır. Sonra anlık görüntüyü Visual Studio tanılama araçları Penceresi'nde tıklayarak açın. Yalnızca yerel gibi hizmetinizde anlık görüntü artık ayıklayabilirsiniz. Ayrıntılı yönergeler için okumaya devam edin.

## <a name="collect-and-view-snapshots"></a>Toplama ve anlık görüntüleri görüntüleme

Snapshot Debugger, uygulamanızdan anlık görüntüleri toplar. Anlık görüntüleri gibi bir noktada, uygulama resimlerinin saati gösterir. Ne zaman ve nereye kodda bir anlık görüntü noktası ayarlayarak bir anlık görüntü toplamak Visual Studio söyleyin. Anlık görüntü noktası size, incelemekte sorun bir anlık görüntü elde emin olmak için gereken koşulları ayarlayın.

### <a name="set-a-snappoint"></a>Bir anlık görüntü noktası ayarlayın

1. Kod Düzenleyicisi'nde bir anlık görüntü noktası ayarlamak ilginizi çeken bir kod satırının yanındaki sol kanaldaki tıklayın. Bildiğiniz çalışacak kod olduğundan emin olun. 

    ![Düzenleyicide bir anlık görüntü noktası ayarlama](../media/snapshot-startpage-set-snappoint.png)

    Sol taraftaki tıklattığınız mor Altıgene görünür.

2. Tıklayın **toplamaya Başla** anlık görüntü noktasını etkinleştirmek için.

### <a name="open-a-snapshot"></a>Bir anlık görüntüsünü Aç

1. Anlık görüntü noktası isabet edildiğinde bir anlık görüntü sağdaki tanılama araçları penceresi görüntülenir. Penceresi açık değilse, bunu seçerek açabilirsiniz **hata ayıklama** > **Windows** > **tanılama araçlarını Göster**. 

    ![Tanılama Araçları penceresinde anlık görüntü](../media/snapshot-startpage-diagsession-window.png)

2. Anlık görüntü açmak için çift tıklayın.

### <a name="inspect-snapshot-data"></a>Anlık görüntü verileri İnceleme

Bu görünümden veri ipuçlarını görüntülemek, yerel öğeler, Gözcüler, kullanma ve çağırmak için değişkenlerden gelerek yığın windows ve ayrıca ifadeleri değerlendirin.

Web sitesinin kendisinde hala çalışıyor ve son kullanıcıların etkilenen değildir. Varsayılan olarak, anlık görüntü noktası yalnızca bir anlık görüntü olarak yakalanır. Anlık görüntü yakalandıktan sonra diğer bir deyişle, anlık görüntü noktası devre dışı bırakır. Anlık görüntü noktası başka bir anlık görüntü yakalamak istiyorsanız, anlık görüntü noktası tıklayarak tekrar açabilirsiniz **koleksiyonu Güncelleştir**.

### <a name="set-a-logpoint"></a>Bir günlüğe kaydetme noktası ayarlayın

1. Bir anlık görüntü noktası simgesi (mor Altıgene) sağ tıklatın ve seçin **ayarları**.

2. İçinde **anlık görüntü noktası ayarları** penceresinde **eylemleri**.

    ![Anlık görüntü noktası koşulları](../media/snapshot-startpage-logpoint.png)

3. İçinde **ileti** günlüğe kaydetmek istediğiniz bir günlük iletisi girin. Ayrıca, kaşlı ayraçlar içinde yerleştirerek değişkenleri, bir günlük iletisinde değerlendirebilirsiniz.

    Seçerseniz **çıkış penceresine Gönder**, günlüğe kaydetme noktası isabet edildiğinde tanılama araçları penceresinde bir ileti görüntülenir. 

    Seçerseniz **uygulama günlüğüne Gönder**, gelen iletileri görebilirsiniz herhangi bir ileti görüntülenir `System.Diagnostics.Trace` (veya `ILogger` .NET core'da), günlüğe kaydetme noktası isabet edildiğinde App Insights gibi.

## <a name="learn-more"></a>Daha fazla bilgi edinin

Snapshot Debugger hakkında daha fazla bilgi bulabilirsiniz [docs sayfasının](../debug-live-azure-applications.md). Hataları bulmak daha kolay hale getirmek için koşulları ayarlama hakkında daha fazla bilgi edinin.

## <a name="dont-show-me-this-again"></a>Yok ' Bu yeniden Göster

Hiç anlık görüntü hata ayıklayıcısı başlangıç sayfası yeniden Snapshot Debugger bağladığınızda göstermek için değiştirin **Göster 'Başlarken' sayfasında oturum başlangıcı** seçeneğini **Araçları**  >   **Seçenekleri** > **anlık görüntü hata ayıklayıcısı**. 

![Anlık görüntü hata ayıklayıcısı aracı seçeneği sayfası](../media/snapshot-startpage-tools-options.png)
