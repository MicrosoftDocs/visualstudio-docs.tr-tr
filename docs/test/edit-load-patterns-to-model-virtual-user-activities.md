---
title: Yük testi için yük düzenleri
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: a15f771d2afa2b5c8e02eed99b3168a537365a3f
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895307"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Model sanal kullanıcı etkinlikleri için yük desenlerini düzenleme

Yük deseni özellikleri benzetimli kullanıcı yükünün yük testi boyunca nasıl ayarlandığını belirtir. Visual Studio, üç yerleşik yükleme düzeni sağlar: Sabit, adım ve hedef temelli. Yük desenini seçin ve yük testi hedefleriniz için uygun düzeylere özellikleri ayarlayın.

Yük düzeni, bir senaryonun bir bileşenidir. Bir yük testi tanımlanmış yük düzenlerini birlikte senaryoları kapsar.

> [!NOTE]
> Tüm yükleme desenleri, Visual Studio oluşturduğu sanal kullanıcı benzetimi yapılmış bir yük yüktür.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Yük düzenleri

### <a name="constant"></a>Sabit

 Sabit yük düzeni, yük testi sırasında değişmez bir kullanıcı yükü belirtmek için kullanılır. Örneğin, bir web uygulamasında duman testi çalıştırdığınızda, bir ışık, sabit yük 10 kullanıcı ayarlamak isteyebilirsiniz.

#### <a name="constant-load-pattern-considerations"></a>Sabit yük düzeni konuları

 Bir sabit yük düzeni, bir yük testi çalıştırma sırasında aynı kullanıcı yükünü çalıştırmak için kullanılır. Yüksek kullanıcı sayısı olan bir sabit yük deseni kullanırken dikkatli olun; Bunun yapılması, sunucu veya sunucularda yük testinin başında mantıksız veya gerçekçi olmayan bir isteğe bağlı şekilde yerleştirebilirsiniz. Örneğin, Yük testiniz bir ana sayfa isteği ile başlayan bir web testi içeriyorsa ve yükleme testini 1.000 kullanıcı bir sabit yük ile ayarlarsanız yük testi giriş sayfasında ilk 1.000 isteği mümkün olduğunca hızlı gönderir. Bu, Web sitenizi gerçek girişin gerçekçi bir benzetimi olmayabilir. Bunu azaltmak için kademeli olarak 1,000 kullanıcıya Yükselen bir adım yükü düzenini kullanmayı deneyin veya yük testi çalışması Ayarları'nda bir Isınma dönemi belirleyin. Isınma Süresi belirtilirse, yük testi otomatik olarak yükü yavaş yavaş Isınma dönemi sırasında artacaktır. Daha fazla bilgi için [Senaryo Başlatma Gecikmelerini Yapılandırma](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Adım

 Adım yükü düzenini, zaman tanımlı en yüksek kullanıcı yükü en çok artıran bir kullanıcı yükü belirtmek için kullanılır. Belirttiğiniz Adımlama yükleri **ilk kullanıcı sayısı**, **en yüksek kullanıcı sayısı**, **adım süresi (saniye)**, ve **adım kullanıcı sayısı**.

 Örneğin bir adım yüklemesi ile bir **ilk kullanıcı sayısı** , **en yüksek kullanıcı sayısı** 100 **adım süresi (saniye)** 10 ve **adım kullanıcı sayısı** 1 / 1 artar 100 kullanıcı ulaşana kadar 10 saniyede 1 ile başlayan bir kullanıcı yük düzeni oluşturur.

> [!NOTE]
> Toplam test süresi en fazla kullanıcı yükü en fazla adım için gerekli olan süreden kısadır sonra test geçen süre durdurur ve değil ulaşın **en yüksek kullanıcı sayısı** hedef.


 Adım hedefi bir noktaya sunucu ulaşıncaya kadar yükünü artırmak için kullanabileceğiniz performansının önemli ölçüde azaldığı. Yük arttıkça sunucu sonunda kaynaklar yetersiz çalıştırın. Adım yükü bu gerçekleştiğinde kullanıcı sayısını belirlemek için iyi bir yoludur. Adımlama yükü ile ayrıca yakından aracıları istenen yükü oluşturmak emin olmak için aracı kaynakları izlemek vardır.

 Normalde, farklı adım sürelerine sahip birden fazla çalıştırma yürütmeniz gerekir ve belirli bir yükleme için iyi ölçümler alabilmesi adım kullanıcı sayısı. Sık sık kullanıcılar eklendikçe yükleri her adım için bir başlangıç depo gösterir. Yükleme hızı tutan, sistemin ilk depodan düzeldikten sonra sistem performansını ölçmek sağlar.

#### <a name="step-load-pattern-considerations"></a>Adım yük düzeni konuları

 Adım yük düzeni, kullanıcı yükü arttıkça performansın nasıl değişeceğini görebileceğiniz şekilde yük testi yapılırken sunucu veya sunucular üzerindeki yükü artırmak için kullanılabilir. Örneğin, sunucu veya sunucularınızın nasıl gerçekleştirmek görmek için kullanıcı yükü 2.000 kullanıcıya yükseldiğinde aşağıdaki özelliklere sahip bir adım yükü düzenini kullanarak 10 saatlik yük testi çalıştırabilirsiniz:

- **İlk kullanıcı sayısı**: 100

- **En yüksek kullanıcı sayısı**: 2.000

- **Adım Süresi (saniye)**: 1.800

- **Adım Rampa Süresi (saniye)**: 20

- **Adım kullanıcısı sayısı**: 100

  Bu ayarlar kullanıcı 30 dakika (1800 saniye) için yük testini çalıştırın, 100, 200, 300 ve 2.000 kullanıcıya kadar yükler. **Adım eğrisi süresi** özelliği olan özel olarak belirtilmelidir, çünkü bu seçim için kullanılabilir değil Bu özelliklerden yalnızca biri **Yeni Yük Testi Sihirbazı**. Bu özelliği artırma bir adımdan bir sonrakine (örneğin 100 kullanıcıdan 200 kullanıcıya) artışın hemen yerine olanak tanır. Örnekte, kullanıcı yükü 20 saniyelik bir süreçte 100 kullanıcıdan 200'e yükseltilmiştir (artış beş kullanıcı her saniye). Daha fazla bilgi için [nasıl yapılır: Adım yük düzeni için Adım Rampa Süresi özelliğini belirtme](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Hedef tabanlı

 Hedef tabanlı yük düzeni adım desenine benzer ancak kullanıcı yükünü düzenli kullanıcı yükü düzeltmeleri ve performans sayacı eşiklerine göre ayarlar. Hedefe dayalı yükler, çeşitli farklı amaçlar için kullanışlıdır:

- Aracılardan gelen çıkış en üst düzeye: ölçüm aracıların çıkış en üst düzeye çıkarmak için aracı sınırlama anahtarı ölçün. Genellikle, CPU olur. Ancak, bu bellek da olabilir.

- Hedef kaynak düzeyine ulaşmasını, genellikle CPU, hedef sunucuda, ardından o düzeyde üretilen iş ölçme. Bu, sunucu üzerindeki kaynak kullanımının tutarlı bir düzey verilen aktarım hızının çalıştıracak çalışma için karşılaştırmalar yapmak sağlar.

- Sunucuda bir hedef işleme düzeyine ulaşmasını.

  Aşağıdaki tabloda, aşağıdaki özellik ayarları hedef tabanlı bir desenle bir örnek gösterilmektedir:

|Özellik grubu|Özellik|Değer|
|-|--------------|-|
|Performans sayacı|Kategori|İşlemci|
|Performans sayacı|Bilgisayar|ContosoServer1|
|Performans sayacı|Sayaç|% İşlemci zamanı|
|Performans sayacı|Örnek|_Toplam|
|Performans sayacı'nın hedef aralığı|Üst uç|90|
|Performans sayacı'nın hedef aralığı|En düşük|70|
|Kullanıcı sayısı sınırları|İlk kullanıcı sayısı|1.|
|Kullanıcı sayısı sınırları|En yüksek kullanıcı sayısı|100|
|Kullanıcı sayısı sınırları|En yüksek kullanıcı sayısı azalması|5|
|Kullanıcı sayısı sınırları|En yüksek kullanıcı sayısı artması|5|
|Kullanıcı sayısı sınırları|En yüksek kullanıcı sayısı|1.|

 Bu ayarları neden **Yük Testi Çözümleyicisi** şekilde testi sırasında kullanıcı yükünü 1 ile 100 arasında ayarlamak için **sayacı** için `% Processor Time` WebServer01 eklenmemesi arasında`70%`ve `90%.`

 Her kullanıcı yükünü ayarlamayı boyutu tarafından belirlenir **maksimum kullanıcı sayısı artması** ve **maksimum kullanıcı sayısı azalması** ayarları. Kullanıcı sayısı sınırları belirlediği **en yüksek kullanıcı sayısı** ve **en yüksek kullanıcı sayısı** özellikleri.

#### <a name="goal-based-load-pattern-considerations"></a>Hedef tabanlı yük deseninde dikkat edilmesi gerekenler

 Hedef tabanlı yük düzeni, sistemin destekleyebileceği kullanıcı sayısını belirlemek istediğinizde yararlıdır bazı kaynak kullanımı düzeyine ulaşmadan önce. Bu seçenek, sisteminizdeki sınırlandıran kaynağın (performans sorunu) tanımladığınızda en iyi şekilde çalışır.

 Örneğin, sisteminizdeki sınırlandıran kaynağın veritabanı sunucunuz üzerindeki CPU olduğunu ve veritabanı sunucusundaki CPU % 75 meşgul olduğunda kaç kullanıcının desteklenebildiğini görmek istiyorsanız bildiğiniz varsayalım. Yüzde 80'i ve yüzde 70 arasında değeri performans sayacı "% işlemci zamanı" tutma amacı olan bir hedef tabanlı yük düzeni kullanabilirsiniz.

 Başka bir kaynak sistemin aktarım hızını sınırlayan, dikkat edilmesi gereken bir şey var. Bu kaynaklar, hiçbir zaman ulaşılamayabilir hedef tabanlı yük desenine göre belirtilen hedefe neden olabilir. Ayrıca, kullanıcı yükü için belirttiğiniz değeri kadar artmaya devam edecektir **en yüksek kullanıcı sayısı** ulaşıldı. Bu genellikle istenen yükleme değildir, bu nedenle dikkatli hedef tabanlı yük düzeni içindeki performans sayacı.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testiniz için ilk yük düzeni belirtme:** kullanarak yük testi oluşturduğunuzda **Yeni Yük Testi Sihirbazı**, yük düzeni seçin.|-   [Yük düzeni değiştirme](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Yük testiniz için yük düzeni düzenleme:** yük testinizi oluşturduktan sonra yük düzeni içindeki düzenleyebilirsiniz **Yük Testi Düzenleyicisi**.|-   [Nasıl yapılır: Adım yük düzeni için Adım Rampa Süresi özelliğini belirtme](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Sanal kullanıcı yük testi senaryosuna olup olmadığını belirten web önbellek verilerini içermelidir:** değiştirebileceğiniz **yeni kullanıcıların yüzdesini** yük testi, önbelleğe alma web benzetim şeklini etkileyen özelliği sanal kullanıcı için bir web tarayıcısı tarafından gerçekleştirilmesi.|-   [Nasıl yapılır: web önbellek verilerini kullanan sanal kullanıcıların yüzdesini belirtme](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Adım eğrisi süresi Adım yük düzeni için belirtme:** **adım eğrisi süresi** özelliği artırma bir adımdan bir sonrakine (örneğin 100 kullanıcıdan 200 kullanıcıya) artışın hemen yerine için sağlar.|-   [Nasıl yapılır: Adım yük düzeni için Adım Rampa Süresi özelliğini belirtme](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Yük düzeni değiştirme

 İle yükleme testinizi oluşturduktan sonra **Yeni Yük Testi Sihirbazı**, kullanabileceğiniz **Yük Testi Düzenleyicisi** test hedeflerinize uygun düzeylere bir senaryoyla ilişkili yük deseni özellikleri değiştirmek için.

> [!NOTE]
> Yük testi senaryosu özelliklerini ve açıklamalarının tam listesi için bkz [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).


 Yük düzeni, etkin bir yük testi ve yeni kullanıcıların eklendiği oranı sırasında sanal kullanıcıların sayısını belirtir. Üç kullanılabilir düzen arasından seçim yapabilirsiniz: adım düzeni, sabit ve hedef temelli. Daha fazla bilgi için [yük desenleriyle bir yük testi senaryosunda sanal kullanıcı sayısını belirtin](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
> Bir yük testi eklentisi kullanarak yükleme özelliklerini programlı olarak da değiştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md).


### <a name="to-change-the-load-pattern"></a>Yük Düzeni değiştirmek için

1.  Bir yük testi açın.

2.  İçinde **Yük Testi Düzenleyicisi**, *senaryoları* klasöründe yük düzeni için Düzenle ve senaryosu için yük desenini seçin istediğiniz senaryoyu genişletin.

    > [!NOTE]
    > Yük testiniz senaryo ağacında görüntülenen yük desen düğüm ifade yük oluştururken seçtiğiniz test yük profili yansıtır. Ya da olabilir **sabit yük profili** veya **Adım yük profili**.

3.  Tuşuna **F4** görüntülenecek **özellikleri** penceresi.

     **Yük düzeni** ve **parametreleri** kategorileri görüntülenir **özellikleri** penceresi.

4.  (İsteğe bağlı) Değişiklik **deseni** özelliğinde **yük düzeni** kategorisi.

     İlgili seçimlerinizi **deseni** özelliği olan **adım**, **sabit**, ve **hedefe dayalı**. Yük düzeni türleri hakkında daha fazla bilgi için bkz. [yük desenleriyle bir yük testi senaryosunda sanal kullanıcı sayısını belirtin](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5.  (İsteğe bağlı) İçinde **parametreleri** kategori değerleri değiştirin.

    > [!NOTE]
    > İçin ayarlanan değerlerle **parametreleri** için seçtiğiniz değere göre farklı **deseni** özelliği.

6.  Özelliklerini değiştirme işlemini tamamladıktan sonra seçin **Kaydet** üzerinde **dosya** menüsü. Sonra yeni yük düzeni ile yük testi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Nasıl yapılır: web önbellek verilerini kullanan sanal kullanıcıların yüzdesini belirtme](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Nasıl yapılır: Adım yük düzeni için Adım Rampa Süresi özelliğini belirtme](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)