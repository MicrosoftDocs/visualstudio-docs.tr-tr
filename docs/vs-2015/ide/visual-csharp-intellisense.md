---
title: Visual C# IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [J#]
- Visual C#, IntelliSense
- IntelliSense [C#]
ms.assetid: 79ca304d-dc1e-4dc9-a2a6-7808df2e588e
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d094a0272e5c90afa1a83a42543dd464f219a17
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862209"
---
# <a name="visual-c-intellisense"></a>Visual C# IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C# IntelliSense, kodlama Düzenleyicisi'nde ve siz hata ayıklama sırasında kullanılabilir [anlık mod](../ide/reference/immediate-window.md) komut penceresi.  
  
## <a name="completion-lists"></a>Tamamlanma listeleri  
 IntelliSense tamamlanma listelerinde Visual C# ' ta belirteçleri üyeleri listeleme, tam sözcük ve daha fazlasını içerir. Hızlı erişim sağlar:  
  
- Üyeleri bir tür veya ad alanı  
  
- Değişkenleri, komutlar ve İşlevler adları  
  
- [Kod parçacıkları](#CodeSnippets),  
  
- [Dil anahtar sözcükleri](#Keywords),  
  
- [Genişletme Yöntemleri](#ExtensionMethods)  
  
  Tamamlanma listesine dâhil C# ilgisiz belirteçleri filtrelemek ve bağlamına dayalı bir belirteç önceden seçmek akıllı. Daha fazla bilgi için [C# ' de filtrelenmiş tamamlanma listeleri](../misc/filtered-completion-lists-in-csharp.md) ve [Pre-selected tamamlanma listesi öğeleri, C#](../misc/pre-selected-completion-list-items-in-csharp.md).  
  
###  <a name="CodeSnippets"></a> Kod parçacıkları tamamlanma listeleri  
 Visual C# içinde önceden tanımlanmış gövdeleri kodu programınıza kolayca eklemenize yardımcı olmak için kod parçacıkları tamamlanma listesi içerir. Kod parçacığının olarak tamamlama listede görünür [Shortcut öğesi (IntelliSense kod parçacıkları)](http://msdn.microsoft.com/en-us/052cc97a-5c70-42f8-b398-4c3adf670cfa).  Varsayılan olarak Visual C# dilinde kullanılabilir kod parçacıkları hakkında daha fazla bilgi için bkz: [Visual C# kod parçacıkları](../ide/visual-csharp-code-snippets.md).  
  
###  <a name="Keywords"></a> Tamamlanma listeleri dil anahtar sözcükleri  
 Visual C# ' ta tamamlanma listesi dil anahtar sözcükleri de içerir. C# dil anahtar sözcükleri hakkında daha fazla bilgi için bkz: [C# anahtar sözcükleri](http://msdn.microsoft.com/library/e929b0f2-4b92-4d37-8060-23d323b098ad).  
  
###  <a name="ExtensionMethods"></a> Tamamlama listelerinde genişletme yöntemleri  
 Visual C# ' ta tamamlanma listesi kapsamlarındaki genişletme yöntemleri içerir.  
  
> [!NOTE]
>  Tamamlanma listesi için tüm genişletme yöntemleri görüntülemez <xref:System.String> nesneleri.  
  
 Genişletme yöntemleri örnek yöntemleri farklı bir simge kullanın. Liste simgelerin bir listesi için bkz: [sınıf görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md). Bir örnek yöntemi ve aynı ada sahip bir uzantı yöntemi kapsam içinde her ikisi de olduğunda tamamlanma listesi uzantısı yöntemi simgesi görüntüler.  
  
### <a name="filtered-completion-lists"></a>Filtrelenmiş tamamlanma listeleri  
 IntelliSense, gereksiz üyeleri filtrelerini kullanarak tamamlama listesinden kaldırır.  
  
 Visual C# bu öğeler için görüntülenmesini tamamlanma listeleri filtreler:  
  
-   **Arabirimleri ve temel sınıfları.** IntelliSense arabirimi ve temel sınıf tamamlanma listeleri, sınıf bildiriminin temel ve arabirimi listeler, hem de kısıtlaması listeleri öğeleri otomatik olarak kaldırır. Örneğin, sabit listeleri için temel sınıflar kullanılamadığı için temel sınıflar için tamamlama listesinde numaralandırmalar görünmez. Taban sınıflar tamamlanma listesi yalnızca arabirimleri ve ad alanları içerir. Listede bir öğe seçin ve ardından virgül girin, IntelliSense Visual C#, birden çok devralma desteklemediği için temel sınıflar tamamlama listesinden kaldırır. Aynı davranışı için kısıtlama yan tümceleri de gerçekleşir.  
  
-   **Öznitelikleri**: bir türe öznitelik uyguladığınızda, liste yalnızca bu türleri gibi içeren ad alanlarını Düzen bu türleri içeren tamamlanma listesi filtrelenir <xref:System.Attribute>.  
  
-   `as` ve `is` işleçleri.  
  
-   **Yan tümceleri yakalayın.**  
  
-   **Nesne başlatıcıları:** yalnızca başlatılabilir üyeleri tamamlama listesinde görünür.  
  
-   **Yeni anahtar sözcük**: yazdığınızda `new` ve tamamlanma listesi görünür boşluk tuşuna basın. Bir öğe, listede, kodunuzu bağlamda göre otomatik olarak seçilir. Örneğin, öğeleri yöntemleri return deyimleri ve bildirimler için tamamlama listesinde otomatik olarak seçilir.  
  
-   **olarak ve is işleçlerini:** filtrelenmiş tamamlanma listesini otomatik olarak yazdığınız sonra boşluk tuşuna bastığınızda görüntülenen `as` veya `is` anahtar sözcüğü.  
  
-   Olayları: Yazdığınızda anahtar sözcüğü `event`, tamamlanma listesi yalnızca temsilci türleri içerir.  
  
-   Parametre Yardımı, onları girerken, parametrelerle eşleşen ilk yöntem aşırı yüklemesi için otomatik olarak sıralar. Birden çok yöntem aşırı yükleme varsa, yukarı ve aşağı oklarını sonraki olası aşırı yükleme listesindeki gidin.  
  
## <a name="most-recently-used-members"></a>En son kullanılan üyeler  
 IntelliSense, yakın zamanda açılır pencerede seçtiğiniz üyeleri hatırlar [üyeleri Listele](../ide/using-intellisense.md) kutusu otomatik nesne adı tamamlama. Üye listesi, sonraki açışınızda, en son kullanılan üyeler en üstünde gösterilir. En son kullanılan üyeler geçmişi, her oturum IDE içindeki arasında temizlenir.  
  
## <a name="override"></a>override  
 Yazdığınızda [geçersiz kılma](http://msdn.microsoft.com/library/dd1907a8-acf8-46d3-80b9-c2ca4febada8) ve sürüklerken boşluk tuşuna basın, IntelliSense tüm bir açılır liste kutusunda geçersiz kılma geçerli bir temel sınıf üyelerini görüntüler. Sonraki yöntemin dönüş türü yazarak `override` yalnızca aynı türü döndüren yöntemler göstermek için IntelliSense ister. IntelliSense herhangi bir eşleşme bulamazsa, tüm temel sınıf üyelerinin görüntülenir.  
  
## <a name="automatic-code-generation"></a>Otomatik Kod Oluşturma  
  
### <a name="add-using"></a>using Ekle  
 IntelliSense işlemi kullanarak ekleme kodu yazmak yerine, kodun başka bir parçası, odağı gerek odaklanma tutmanıza olanak sağlar.  
  
 Ekleme işlemi kullanarak başlatmak için çözümlenemeyen bir tür başvurusu imleci getirin. Örneğin, ne zaman, bir konsol uygulaması oluşturun ve ardından eklemek `XmlTextReader` body `Main` yöntemi, bir akıllı etiket en sağdaki karakter altında görünür `XmlTextReader`, çözümlenemeyen bir tür başvurusu görüntülendiğinden.  
  
 ![Akıllı etiket görüntü kullanarak ekleyin](../ide/media/addusesmart.gif "AddUseSmart")  
  
 Ardından menüsünden seçim yaparak Ekle kullanarak çağırabilirsiniz **çözmek** alt **IntelliSense** menü veya bağlam menüsü akıllı etiket ekleme kullanarak çağırılarak veya. Akıllı etiket yalnızca, imleç üzerinde konumlandırılmış ya da bağlanmamış tür için bitişik olduğunda görülebilir.  
  
 ![Kullanarak ekleyin, akıllı etiket genişletilmiş resmi](../ide/media/addusesmartexp.gif "AddUseSmartExp")  
  
### <a name="organize-usings"></a>Using'leri düzenleme  
 **Using'leri düzenleme** seçenekleri Sırala ve Kaldır `using` ve `extern` kaynak kodu davranışını değiştirmeden bildirimleri. Zaman içinde kaynak dosyaları bloated ve gereksiz ve düzensiz nedeniyle okunması zor hale gelebilir `using` yönergeleri. **Using'leri düzenleme** seçenekleri kullanılmayan kaldırarak kaynak kodu compact `using` yönergeleri ve sıralayarak okunabilirliğini artırır.  
  
 Visual Studio IDE'de kullanılabilir seçenekleri görmek için **Düzenle** menüsünde **IntelliSense**, gelin ve ardından **Using'leri düzenleme**. IDE düzenlemek ve kaldırmak için aşağıdaki seçenekleri sağlar `usings` yönergeleri:  
  
### <a name="implement-interface"></a>Arabirimi Uygulama  
 IntelliSense sağlar, yardımcı bir seçenek bir [arabirimi](http://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) Kod Düzenleyicisi'nde çalışırken. Normalde, bir arabirim düzgün bir şekilde uygulamak için bir yöntem bildiriminde arabirimi her üyesi için sınıfınızda oluşturmanız gerekir. Bir sınıf bildiriminde bir arabirimin adını yazdıktan sonra IntelliSense'i kullanarak, bir akıllı etiket görüntülenir. Akıllı etiket açık veya örtülü adlandırma kullanarak arabirimi otomatik olarak uygulamak için seçeneği sunar. Açık adlandırma altında yöntem bildirimleri arabirimin adını taşıyan; örtük adlandırma altında yöntem bildirimleri ait oldukları arabirimi göstermez. Açıkça adlandırılmış arabirim yöntemi yalnızca bir sınıf örneği üzerinden değil ve bir arabirim örneği aracılığıyla erişilebilir. Daha fazla bilgi için [açık arabirim uygulaması](http://msdn.microsoft.com/library/181c901f-0d4c-4f29-97fc-895079617bf2).  
  
 Arabirim uygulama arabirimi karşılamak için gereken en az sayıda yöntem saptamalar oluşturur. Ardından bir temel sınıf arabirimi bölümlerini uyguluyorsa, bu saptamalar yeniden oluşturulmaz.  
  
### <a name="implement-abstract-base-class"></a>Soyut taban sınıfı uygulama  
 IntelliSense, Kod Düzenleyicisi'nde çalışırken Özet temel sınıf üyelerinin otomatik olarak Uygula yardımcı olması için bir seçenek sunar. Normalde, bir soyut üye uygulamak için temel sınıfı soyut temel sınıf yeni yöntem tanımının her bir yöntemin türetilmiş sınıfınızın oluşturmak gerekir. Bir sınıf bildiriminde bir soyut temel sınıf adını yazdıktan sonra IntelliSense'i kullanarak, bir akıllı etiket görüntülenir. Akıllı etiket otomatik olarak taban sınıf yöntemlerini uygulamak için seçeneği sunar.  
  
 Uygulama soyut temel sınıf özelliği tarafından oluşturulan yöntem saptamalar MethodStub.snippet dosyasında tanımlanan kod parçacığı tarafından modellenir. Kod parçacıkları değiştirilebilir. Daha fazla bilgi için [izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md).  
  
### <a name="generate-from-usage"></a>Kullanımdan oluştur  
 **Kullanımından Oluştur** özellik tanımlamadan önce sınıflar ve üyeler kullanmanıza olanak sağlar. Herhangi bir sınıfı, oluşturucu, yöntemi, özelliği, alan veya kullanabilirsiniz ancak henüz tanımlanmamış istediğiniz sabit listesi için bir saplama oluşturabilirsiniz. Yeni türler ve üyeler, kodun geçerli konumu çıkmadan oluşturabilirsiniz. Bu, iş akışınızdaki en aza indirir.  
  
 Dalgalı çizgi her tanımlanmamış tanımlayıcı altında görünür. Tanımlayıcının fare işaretçisini getirdiğinizde, bir araç ipucunda bir hata iletisi görüntülenir.  
  
 Uygun seçenekleri görüntülemek için aşağıdaki yordamlardan birini kullanabilirsiniz:  
  
- Tanımlanmamış tanımlayıcı tıklayın. Bir kısa çizgi, en soldaki karakterin altında görünür. Fare işaretçisini üzerinde kısa çizgi ve bir akıllı etiket (simge) görüntülenir. Akıllı etiket tıklayın.  
  
- Tanımlanmamış tanımlayıcı tıklayın ve ardından CTRL tuşuna basın. (nokta).  
  
- Tanımlanmamış tanımlayıcı sağ tıklayın ve ardından **Oluştur**.  
  
  Görünen seçenekler şunları içerebilir:  
  
- **Özellik taslağı oluşturmak**  
  
- **Alan taslağı üret**  
  
- **Metot taslağı üret**  
  
- **Sınıfı oluşturun**  
  
- **Yeni tür oluşturma** (için bir sınıf, yapı, arabirim veya numaralandırma)  
  
## <a name="generate-event-handlers"></a>Olay işleyicileri oluşturma  
 Kod düzenleyicisinde, IntelliSense yöntemleri (olay işleyicileri) olay alanlarını kanca yardımcı olabilir.  
  
 Yazdığınızda `+=` işleçten sonra IntelliSense .cs dosyası olay alanı sizden seçeneği SEKME tuşuna basın. Bu, yeni bir olay işleme yöntemine işaret eden bir temsilci örneğini ekler.  
  
 ![Yukarı düğme otomatik kanca](../ide/media/vxautohookup.gif "vxAutoHookUp")  
  
 Sekme tuşuna basarsanız, IntelliSense, otomatik olarak sizin için deyim tamamlanır ve olay işleyici başvurusu Kod Düzenleyicisi'nde seçilen metin olarak görüntüler. Otomatik olay birleştirme tamamlamak için IntelliSense, olay işleyicisi için boş bir saplama yeniden oluşturmak için SEKME tuşuna basın ister.  
  
 ![Olay işleyicisi oluşturmak](../ide/media/vxgenerateeventhandler.gif "vxGenerateEventHandler")  
  
> [!NOTE]
>  IntelliSense tarafından oluşturulan yeni bir temsilci, mevcut bir olay işleyicisi başvuruyorsa, IntelliSense araç ipucu için bu bilgiyi iletişim kurar. Ardından bu başvuruyu değiştirebilirsiniz; metin, Kod Düzenleyicisi'nde zaten seçildi. Aksi takdirde otomatik olay birleştirme bu noktada tamamlanmıştır.  
  
 Sekme tuşuna basarsanız, IntelliSense doğru imzaya sahip bir yöntemi çıkış Saplamaları ve imleç, olay işleyicisi gövdesinde koyar.  
  
> [!NOTE]
>  Kullanım **Navigate Backward** komutunu **görünümü** menü (CTRL +-) olay birleştirme deyimine geri dönmek için.  
  
 IntelliSense adlı bir olay işleyicisi otomatik olarak nasıl kancaları aşağıdaki görevleri gösterir `button1_Click` bir olayı alana adlı `button1.Click`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio IDE](../ide/visual-studio-ide.md)



