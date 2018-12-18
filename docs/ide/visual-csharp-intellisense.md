---
title: C# IntelliSense
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 41a4dfa2a904f3fdc09671fd5e9afa0f29c2e9f3
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160146"
---
# <a name="c-intellisense"></a>C# IntelliSense

C# IntelliSense, kodlama Düzenleyicisi'nde ve hata ayıklama sırasında zaman kullanılabilir [anlık mod](../ide/reference/immediate-window.md) komut penceresi.

## <a name="completion-lists"></a>Tamamlanma listeleri

C# IntelliSense tamamlanma listelerinde belirteçleri üyeleri listeleme, tam sözcük ve daha fazlasını içerir. Hızlı erişim sağlar:

- Bir tür veya ad alanı üyeleri

- Değişkenleri, komutlar ve İşlevler adları

- Kod parçacıkları

- Dil anahtar sözcükleri

- Genişletme yöntemleri

Tamamlanma listesine dâhil C# ilgisiz belirteçleri filtrelemek ve bağlamına dayalı bir belirteç önceden seçmek akıllı. Daha fazla bilgi için [filtrelenmiş tamamlanma listeleri](#filtered-completion-lists).

### <a name="code-snippets-in-completion-lists"></a>Kod parçacıkları tamamlanma listeleri

C# kod parçacıkları, kod önceden tanımlanmış gövdeleri programınıza kolayca eklemenize yardımcı olmak için tamamlanma listesi içerir. Kod parçacığının olarak tamamlama listede görünür [kısayol metnini](../ide/code-snippets-schema-reference.md#shortcut-element). Varsayılan olarak C# ' ta kullanılabilir kod parçacıkları hakkında daha fazla bilgi için bkz: [C# kod parçacıkları](../ide/visual-csharp-code-snippets.md).

### <a name="language-keywords-in-completion-lists"></a>Tamamlanma listeleri dil anahtar sözcükleri

C# ' de içeren dil anahtar sözcükleri tamamlanma listesi. C# dil anahtar sözcükleri hakkında daha fazla bilgi için bkz: [C# anahtar sözcükleri](/dotnet/csharp/language-reference/keywords/index).

### <a name="extension-methods-in-completion-lists"></a>Tamamlama listelerinde genişletme yöntemleri

C# ' ta tamamlanma listesi kapsamındaki genişletme yöntemleri içerir.

> [!NOTE]
> Tamamlanma listesi için tüm genişletme yöntemleri görüntülemez <xref:System.String> nesneleri.

Genişletme yöntemleri örnek yöntemleri farklı bir simge kullanın. Liste simgesine başvuru kılavuzu için bkz. [sınıf görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md). Bir örnek yöntemi ve aynı ada sahip bir uzantı yöntemi kapsam içinde her ikisi de olduğunda tamamlanma listesi uzantısı yöntemi simgesi görüntüler.

### <a name="filtered-completion-lists"></a>Filtrelenmiş tamamlanma listeleri

IntelliSense, gereksiz üyeleri filtrelerini kullanarak tamamlama listesinden kaldırır. C# bu öğeler için görüntülenmesini tamamlanma listeleri filtreler:

- **Arabirimleri ve temel sınıflar**: IntelliSense arabirimi ve temel sınıf tamamlanma listeleri, sınıf bildiriminin temel ve arabirimi listeler, hem de kısıtlaması listeleri öğeleri otomatik olarak kaldırır. Örneğin, sabit listeleri için temel sınıflar kullanılamadığı için temel sınıflar için tamamlama listesinde numaralandırmalar görünmez. Taban sınıflar tamamlanma listesi yalnızca arabirimleri ve ad alanları içerir. Listeden bir öğe seçin ve ardından virgül girin, C#, birden çok devralma desteklemediği için IntelliSense temel sınıflar tamamlama listesinden kaldırır. Aynı davranışı için kısıtlama yan tümceleri de gerçekleşir.

- **Öznitelikleri**: Bir türe öznitelik uyguladığınızda, liste yalnızca bu türleri gibi içeren ad alanlarını Düzen bu türleri içeren tamamlanma listesi filtrelenir <xref:System.Attribute>.

- **Catch yan tümceleri**

- **Nesne başlatıcılarda**: Yalnızca başlatılabilir üyeleri tamamlama listesinde görünür.

- **Yeni anahtar sözcük**: Yazdığınızda `new` ve tuşuna **alanı**, tamamlanma listesi görüntülenir. Bir öğe, listede, kodunuzu bağlamda göre otomatik olarak seçilir. Örneğin, öğeleri yöntemleri return deyimleri ve bildirimler için tamamlama listesinde otomatik olarak seçilir.

- **enum anahtar sözcüğü**: Bastığınızda **alanı** enum atamanın bir eşittir işaretinden sonra tamamlanma listesi görüntülenir. Bir öğe, listede, kodunuzu bağlamda göre otomatik olarak seçilir. Örneğin, öğeleri otomatik olarak tamamlama listesinde dönüş anahtar sözcüğü yazın sonra ve bir bildirimi yaptığınızda seçilir.

- **olarak ve is işleçlerini**: Filtrelenmiş tamamlanma listesini otomatik olarak tuşuna bastığınızda görüntülenen **alanı** yazdığınız sonra `as` veya `is` anahtar sözcüğü.

- **Olayları**: Anahtar sözcüğü yazdığınızda `event`, tamamlanma listesi yalnızca temsilci türleri içerir.

- **Parametre Yardımı** otomatik olarak onları girerken, parametrelerle eşleşen ilk yöntem aşırı yüklemesi için sıralar. Birden çok yöntem aşırı yükleme varsa, yukarı ve aşağı oklarını sonraki olası aşırı yükleme listesindeki gidin.

### <a name="most-recently-used-members"></a>En son kullanılan üyeler

IntelliSense, yakın zamanda açılır pencerede seçtiğiniz üyeleri hatırlar [üyeleri Listele](../ide/using-intellisense.md) kutusu otomatik nesne adı tamamlama. Bir sonraki kullandığınızda **üye listesi**, en son kullanılan üyeler en üstünde gösterilir. En son kullanılan üyeler geçmişi her Visual Studio oturumu arasında temizlenir.

### <a name="override"></a>override

Yazdığınızda [geçersiz kılma](/dotnet/csharp/language-reference/keywords/override) ve tuşuna **alanı**, IntelliSense tüm bir açılır liste kutusunda geçersiz kılma geçerli bir temel sınıf üyelerini görüntüler. Sonraki yöntemin dönüş türü yazarak `override` yalnızca aynı türü döndüren yöntemler göstermek için IntelliSense ister. IntelliSense herhangi bir eşleşme bulamazsa, tüm taban sınıfı üyelerini görüntüler.

### <a name="ai-enhanced-intellisense"></a>Yapay ZEKA destekli IntelliSense

Yükleyebileceğiniz bir Deneysel [Intellicode uzantısı](/visualstudio/intellicode/intellicode-visual-studio) yapay zeka destekli IntelliSense tamamlanma listelerinde sağlayan Visual Studio için. Bu uzantı üyeleri alfabetik listesi yalnızca sunmak yerine kullanmak için en olası doğru API tahmin eder. Dinamik listesi sağlamak için geçerli kod bağlamı ve desenleri kullanır.

## <a name="automatic-code-generation"></a>Otomatik kod oluşturma

### <a name="add-using"></a>using Ekle

**Ekleme** IntelliSense işlemi otomatik olarak ekler gerekli `using` kod dosyanıza yönergesi. Bu özellik, odağı yazmak yerine, kodun başka bir parçası, odağı gerek kodu tutmanıza olanak sağlar.

Başlatmak için **ekleme** işlemi, imleç türü başvuru konumu çözümlenemiyor. Örneğin, ne zaman, bir konsol uygulaması oluşturun ve ardından eklemek `XmlTextReader` body `Main` yöntemi, kırmızı dalgalı görünür kod satırdaki tür başvurusu çözümlenemiyor. Ardından çağırabilirsiniz **ekleme** aracılığıyla **hızlı Eylemler**. **Hızlı Eylemler** imleç bağlanmamış tür üzerinde konumlandırıldığında yalnızca görünür olur.

![Kullanarak, hızlı genişletilmiş görüntü eylem ekleme](../ide/media/addusing-quickaction.png)

Ampul simgesini tıklatın ve ardından **System.Xml; kullanarak** kullanarak otomatik olarak eklemek için yönergesi.

### <a name="remove-and-sort-usings"></a>Kullanımları Kaldır ve Sırala

**Kullanımları Kaldır ve Sırala** seçeneği sıralar ve kaldırır `using` ve `extern` kaynak kodu davranışını değiştirmeden bildirimleri. Zaman içinde kaynak dosyaları bloated ve gereksiz ve düzensiz nedeniyle okunması zor hale gelebilir `using` yönergeleri. **Kullanımları Kaldır ve Sırala** seçeneği sıkıştırır kaynak kodu kullanılmayan kaldırarak `using` yönergeleri ve sıralayarak okunabilirliğini artırır. Üzerinde **Düzenle** menüsünde seçin **IntelliSense**ve ardından **Using'leri düzenleme**.

### <a name="implement-interface"></a>Arabirim uygulama

IntelliSense sağlar, yardımcı bir seçenek bir [arabirimi](/dotnet/csharp/language-reference/keywords/interface) Kod Düzenleyicisi'nde çalışırken. Normalde, bir arabirimi düzgün bir şekilde uygulamak için bir yöntem bildiriminde arabirimi her üyesi için sınıfınızda oluşturmanız gerekir. Bir sınıf bildiriminde bir arabirimin adını yazdıktan sonra IntelliSense'i kullanarak bir **hızlı Eylemler** ampul görüntülenir. Ampul açık veya örtülü adlandırma kullanarak arabirimi otomatik olarak uygulamak için seçeneği sunar. Açık adlandırma altında yöntem bildirimleri arabirimin adını taşır. Örtük adlandırma altında yöntem bildirimleri ait oldukları arabirimi göstermez. Açıkça adlandırılmış arabirim yöntemi yalnızca bir sınıf örneği üzerinden değil ve bir arabirim örneği aracılığıyla erişilebilir. Daha fazla bilgi için [açık arabirim uygulaması](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Arabirim uygulama arabirimi karşılamak için gerekli olan en az sayıda yöntem saptamalar oluşturur. Bir temel sınıf arabirimi bölümlerini uyguluyorsa, bu saptamalar yeniden değildir.

### <a name="implement-abstract-base-class"></a>Soyut taban sınıfı uygulama

IntelliSense, Kod Düzenleyicisi'nde çalışırken Özet temel sınıf üyelerinin otomatik olarak Uygula yardımcı olması için bir seçenek sunar. Normalde, bir soyut üye uygulamak için temel sınıfı soyut temel sınıf yeni yöntem tanımının her bir yöntemin türetilmiş sınıfınızın oluşturmak gerekir. Bir sınıf bildiriminde bir soyut temel sınıf adını yazdıktan sonra IntelliSense'i kullanarak bir **hızlı Eylemler** ampul görüntülenir. Ampul, otomatik olarak taban sınıf yöntemlerini uygulamak için seçeneği sunar.

Tarafından oluşturulan yöntem saptamalar **uygulama soyut temel sınıf** özelliği dosyasında tanımlanan kod parçacığı tarafından modellenir *MethodStub.snippet*. Kod parçacıkları değiştirilebilir. Daha fazla bilgi için [izlenecek yol: Kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Kullanımdan oluştur

**Kullanımından Oluştur** özellik tanımlamadan önce sınıflar ve üyeler kullanmanıza olanak sağlar. Herhangi bir sınıfı, oluşturucu, yöntemi, özelliği, alan veya kullanabilirsiniz ancak henüz tanımlanmamış istediğiniz sabit listesi için bir saplama oluşturabilirsiniz. Yeni türler ve üyeler, kodun geçerli konumu çıkmadan oluşturabilirsiniz. Bu, iş akışınızdaki en aza indirir.

Dalgalı kırmızı alt çizgiyle her tanımlanmamış tanımlayıcı altında görünür. Tanımlayıcının fare işaretçisini getirdiğinizde, bir araç ipucunda bir hata iletisi görüntülenir. Uygun seçenekleri görüntülemek için aşağıdaki yordamlardan birini kullanabilirsiniz:

- Tanımlanmamış tanımlayıcı tıklayın. A **hızlı Eylemler** ampul altında tanımlayıcı olarak görünür. Ampul tıklayın.

- Tanımlanmamış tanımlayıcı tıklatın ve sonra basın **Ctrl**+**.** (**Ctrl** + nokta).

- Tanımlanmamış tanımlayıcı sağ tıklayın ve ardından **hızlı Eylemler ve yeniden düzenlemeler**.

Görünen seçenekler şunları içerebilir:

- **Özelliğini üret**

- **Alanını üret**

- **Metot oluşturma**

- **Sınıfı oluşturun**

- **Yeni tür oluşturma** (için bir sınıf, yapı, arabirim veya numaralandırma)

## <a name="generate-event-handlers"></a>Olay işleyicileri oluşturma

Kod düzenleyicisinde, IntelliSense yöntemleri (olay işleyicileri) olay alanlarını kanca yardımcı olabilir.

Yazdığınızda `+=` işleçten sonra bir olay alanında bir *.cs* dosya, IntelliSense sizden basın seçeneği ile **sekmesini** anahtarı. Bu, yeni bir olay işleme yöntemine işaret eden bir temsilci örneğini ekler.

![Düğme otomatik kanca ayarlama](../ide/media/vxautohookup.gif)

Basarsanız **sekmesini**, IntelliSense otomatik olarak sizin için deyimi sonlanır ve olay işleyici başvurusu Kod Düzenleyicisi'nde seçili metni görüntüler. Otomatik olay birleştirme tamamlamak için IntelliSense basın ister **sekmesini** olay işleyicisi için boş bir saplama yeniden oluşturulacak anahtar.

![Olay işleyicisi oluşturun](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> IntelliSense tarafından oluşturulan yeni bir temsilci, mevcut bir olay işleyicisi başvuruyorsa, IntelliSense araç ipucu için bu bilgiyi iletişim kurar. Ardından bu başvuruyu değiştirebilirsiniz; metin, Kod Düzenleyicisi'nde zaten seçildi. Aksi takdirde otomatik olay birleştirme bu noktada tamamlanmıştır.

Basarsanız **sekmesini**, IntelliSense doğru imzaya sahip bir yöntemi çıkış Saplamaları ve imleci, olay işleyicisi gövdesinde koyar.

> [!NOTE]
> Kullanım **Navigate Backward** komutunu **görünümü** menü (**Ctrl**+**-**) olaya geri dönmek için Birleştirme ifadesi.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense kullanma](../ide/using-intellisense.md)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)