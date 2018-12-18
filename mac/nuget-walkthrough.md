---
title: Bir NuGet paketini projenize dahil
description: Bu belge, bir Xamarin projesinde bir NuGet paketi ekleme kapsar. Bulma ve bir paket indiriliyor, aynı zamanda aracılığıyla IDE tümleştirme özellikleri ile tanışın size yol gösterir.
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.openlocfilehash: 0a98425ba12ae7aba16a2bc6ffa29e701c1b9f11
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948628"
---
# <a name="include-a-nuget-package-in-your-project"></a>Bir NuGet paketini projenize dahil

NuGet, .NET geliştirme için en popüler Paket Yöneticisi olan ve Visual Studio Mac ve Windows üzerinde Visual Studio için yerleşik olan. Arayın ve paketler, Xamarin.iOS ve Xamarin.Android projenize ya da IDE kullanarak ekleyin.

Bu makalede, bir projede bir NuGet paketi ekleme açıklar ve sorunsuz bir hale getirir araç zincirinizi gösterir.

## <a name="nuget-in-visual-studio-for-mac"></a>Mac için Visual Studio'da NuGet

NuGet paket işlevselliğini göstermek için önce yeni bir uygulama oluşturma ve bir paket ekleme gösterilecektir. Ardından paketlerini yönetmenize yardımcı olmak IDE özelliklerini açıklayacağız.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

İlk olarak, adlı bir proje oluşturun `HelloNuget` aşağıda gösterildiği gibi. Bu örnekte iOS tek görünüm uygulaması şablonu gösterilmektedir, ancak herhangi bir desteklenen proje türü işe yarar:

![Yeni iOS projesi oluşturma](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Bir paketi ekleme

Mac için Visual Studio'da Aç projesiyle sağ **paketleri** klasöründe **çözüm bölmesi** seçip **paketleri Ekle**:

![Yeni NuGet paket bağlamı eylemi ekleme](media/nuget-walkthrough-PackagesMenu.png)

Böylece **paketleri Ekle** penceresi. Kaynak açılan listeyi ayarlandığından emin olun `nuget.org`:

![Kaynak listesi açılır](media/nuget-walkthrough-Source.png)

Penceresi açıldığında, varsayılan paket kaynağından paketlerin listesini yükler: nuget.org. İlk sonuçlar şöyle görünür:

![NuGet paketleri listesi](media/nuget-walkthrough-AddPackages1.png)

Örneğin, belirli bir paketi bulmak için sağ üst köşedeki arama kutusunu kullanın `azure`. Kullanmak istediğiniz bir paket buldunuz, seçin ve **Paketi Ekle** yüklemeye başlamak için düğme.

[Azure NuGet paketi ekleme](media/nuget-walkthrough-AddPackages2.png)

Paket İndirildikten sonra projenize eklenir. Çözüm aşağıdaki gibi değişir:

* **Başvuruları** düğümü bir NuGet paketinin parçası olan tüm derlemelerin bir listesini içerir.
* **Paketleri** düğümü yüklediğiniz her NuGet paketini gösterir. Güncelleştirin veya bu listeden bir paket kaldırın.
* A **packages.config** dosya projeye eklenecek. Bu XML dosyası IDE tarafından izlemek için bu projede hangi paket sürümlerini başvurulan kullanılır. Bu dosyayı elle düzenlenerek olmamalıdır, ancak sürüm denetiminde tutmanız gerekir. Project.json dosyası yerine packages.config dosyası kullanılabileceğini unutmayın. Geçişli geri yüklemeyi destekleyen NuGet 3 ile sunulan yeni bir paket dosyası biçimi project.json dosyasıdır. Project.json hakkında ayrıntılı bilgi bulunabilir [NuGet belgeleri](http://docs.microsoft.com/NuGet/Schema/Project-Json). Project.json dosyasını el ile eklenmesi gerekir ve proje kapatıldı ve project.json dosyasını Mac için Visual Studio'da kullanılmadan önce yeniden açıldı

## <a name="using-nuget-packages"></a>NuGet paketlerini kullanma

NuGet paketini eklenen ve güncelleştirilen proje başvuruları, API olarak programlayabileceğiniz sonra herhangi bir proje başvurusu ile olacaktır.

Gerekli eklemeyi `using` dosyanızın en üstüne yönergeleri:

```csharp
using Newtonsoft.Json;
```

Birçok NuGet Nuget kaynağı Benioku ya da proje sayfası bağlantısı gibi ek bilgileri sağlayın. Bu bağlantı normalde paket blurb paketleri Ekle sayfasında bulabilirsiniz:

[Görünüm proje sayfası bağlantısı](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Paket güncelleştirmeleri

Paket güncelleştirmelerini yapılabilir ya da tümünü tek seferde sağ tıklayarak **paketleri** düğümünde veya tek tek her bir bileşen.

Sağ **paketleri** bağlam menüsüne erişmek için:

![Paketleri menüsü](media/nuget-walkthrough-PackagesMenu.png)

*   **Paketleri ekleme** -daha fazla paket projeye eklemek için penceresi açılır.
*   **Güncelleştirme** - her paket için kaynak sunucunun denetler ve tüm yeni sürümlerini yükler.
*   **Geri yükleme** -(mevcut paketlerini yeni sürümlere güncelleştirmeden) tüm eksik paketleri indirir.

Güncelleştirme ve geri yükleme seçenekleri çözüm düzeyinde de mevcuttur ve Çözümdeki tüm projeleri etkiler.

Ayrıca bir bağlam menüsüne erişmek için tek paketler sağ tıklayabilir:

![Paketleri menüsü](media/nuget-walkthrough-PackageMenu.png)

*   **Sürüm numarası** -devre dışı menü öğesi sürüm numarasıdır - yalnızca bilgilendirme amacıyla verilmiştir.
*   **Güncelleştirme** - kaynak sunucu denetler ve (varsa) daha yeni bir sürümü indirir.
*   **Kaldırma** - paketi bu projeden kaldırır ve ilgili derlemeleri proje başvurularından kaldırır.

## <a name="adding-package-sources"></a>Paket kaynaklarını ekleme

Paketleri yükleme için kullanılabilir, başlangıçta nuget.org adresinden alınır. Ancak, diğer paket konumları için Visual Studio Mac için ekleyebilirsiniz Bu, geliştirme aşamasındaki ya da bir özel NuGet sunucusu, şirketiniz veya kuruluşunuz içinde kullanmak için kendi NuGet paketlerinizi test etmek için yararlı olabilir.

Mac için Visual Studio'da gidin **Visual Studio > Tercihler > NuGet > kaynakları** paket kaynakları listesini görüntülemek ve düzenlemek için. Kaynakları (bir URL ile belirtilir), uzak bir sunucu veya yerel dizin olabileceğini unutmayın.

![Paket kaynakları](media/nuget-walkthrough-PackageSource.png)

Tıklayın **Ekle** ayarlamak yeni bir kaynak. Paket kaynağı için bir kolay ad ve URL (veya dosya yolu) girin. Kaynak bir güvenli web sunucusu ise, kullanıcı adı ve parola da girin, bu girişleri Aksi halde boş bırakın:

![Paket kaynaklarını ekleme](media/nuget-walkthrough-PackageSource2.png)

Farklı kaynaklardan paketleri için arama yaparken seçilebilir:

![Paket kaynaklarını ekleme](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Sürüm Denetimi

NuGet belgeleri anlatılmaktadır [NuGet paketleri kaynak denetimine taahhüt vermek zorunda kalmadan kullanarak](/nuget/consume-packages/packages-and-source-control). Kaynak denetimine ikili dosyalar ve kullanılmayan bilgi depolamamayı tercih ederseniz, otomatik olarak sunucudan paketlerini geri yüklemek Mac için Visual Studio yapılandırabilirsiniz. Bu, bir geliştirici, projeyi kaynak denetiminden ilk kez aldığında, Mac için Visual Studio otomatik olarak yükle ve gerekli paketleri yükleyin, anlamına gelir.

![Otomatik olarak paketleri geri yükle](media/nuget-walkthrough-AutoRestore.png)

Dışlama hakkında ayrıntılar için belirli bir kaynak denetimi belgelerinize başvurun `packages` izlenmekte olan yer.

## <a name="see-also"></a>Ayrıca bkz.

* [Yükleme ve bir paket (Windows) Visual Studio kullanma](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
