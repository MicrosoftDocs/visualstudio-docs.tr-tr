---
title: Görüntü kitaplığı Görüntüleyicisi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c0e277a123fe24da9824fae94b13eee686f5663
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778026"
---
# <a name="image-library-viewer"></a>Görüntü Kitaplığı Görüntüleyicisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio görüntü kitaplığı Görüntüleyicisi araç, yüklemek ve görüntü bildirimler, bunları Visual Studio olduğu aynı şekilde yönetmek kullanıcının arayın. Kullanıcı, arka plan, boyutları, DPI, yüksek karşıtlık ve diğer ayarlarını değiştirebilirsiniz. Araç ayrıca her görüntü bildirimi yükleme bilgilerini görüntüler ve görüntü bildiriminde her görüntü kaynağı bilgilerini görüntüler. Bu araç için yararlıdır:  
  
1. Hataları tanılama  
  
2. Özel görüntü Bildirimlerde kalmasını sağlama öznitelikleri ayarlandığını  
  
3. Visual Studio uzantı Visual Studio stili uyan görüntüleri kullanabilmesi için Visual Studio görüntü kataloğunda görüntüleri için arama  
  
   ![Görüntü kitaplığı Görüntüleyicisi Hero](../../extensibility/internals/media/image-library-viewer-hero.png "görüntü kitaplığı Görüntüleyicisi Hero")  
  
   **Resim bilinen adı**  
  
   Bir resim bilinen adı (veya kısa için bilinen ad) bir resim varlığı veya Resim Kitaplığı'ndaki Görüntü listesi varlığı benzersiz olarak tanımlayan bir GUID:ID çiftidir.  
  
   **Görüntü bildirim dosyaları**  
  
   Görüntü bildirimi (.imagemanifest) dosyaları bu varlıkları ve gerçek görüntü veya her varlık temsil eden görüntüleri temsil eden bir takma ad, resim varlıkları kümesini tanımlayan XML dosyalarıdır. Tek başına resimler görüntü bildirimleri tanımlayabilirsiniz veya eski kullanıcı Arabirimi desteği görüntü listeler. Ayrıca, varlık veya ayrı ayrı görüntülere her varlık arkasında ne zaman ve bu varlıkları nasıl görüntüleneceğini değiştirmek için ayarlanabilen öznitelikleri vardır.  
  
   **Görüntü bildirim şeması**  
  
   Tam görüntü bildiriminin şöyle görünür:  
  
```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Guid, ID, or String elements -->  
      </Symbols>  
      <!-- zero or one Images elements -->  
      <Images>  
        <!-- zero or more Image elements -->  
      </Images>  
      <!-- zero or one ImageLists elements -->  
      <ImageLists>  
        <!-- zero or more ImageList elements -->  
      </ImageLists>  
</ImageManifest>  
```  
  
 **Semboller**  
  
 Okunabilirlik ve bakıma yardımcı olmak gibi görüntüsü bildirimine ait öznitelik değerleri simgeleri kullanabilirsiniz. Semboller şöyle tanımlanır:  
  
```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  
  
|||  
|-|-|  
|**Alt öğe**|**Tanım**|  
|{1&gt;İçeri Aktar&lt;1}|Belirtilen bildirim dosyası geçerli bildirimde kullanmak için simgelerin içeri aktarır.|  
|Guid|Simgenin bir GUID temsil eder ve GUID biçimlendirme eşleşmesi gerekir.|  
|Kimlik|Simgenin bir kimliği temsil eder ve negatif olmayan bir tamsayı olmalıdır.|  
|Dize|Simgenin bir rastgele dize değeri temsil eder.|  
  
 Simgeler büyük/küçük harfe ve başvurulan $(symbol-name) söz dizimini kullanarak:  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Tüm bildirimler için önceden tanımlanmış bazı semboller. Bu URI özniteliğinde kullanılabilir \<kaynak > veya \<alma > yerel makinedeki başvuru yolları öğesine.  
  
|||  
|-|-|  
|**Sembol**|**Açıklama**|  
|CommonProgramFiles|% CommonProgramFiles % ortam değişkeninin değeri|  
|LocalAppData|% LocalAppData % ortam değişkeninin değeri|  
|ManifestFolder|Bildirim dosyasını içeren klasör|  
|MyDocuments|Geçerli kullanıcının Belgelerim klasörün tam yolu|  
|ProgramFiles|% ProgramFiles % ortam değişkeninin değeri|  
|Sistem|Windows\System32 klasöründe|  
|WinDir|% WinDir % ortam değişkeninin değeri|  
  
 **Görüntü**  
  
 \<Görüntü > öğe bilinen adı tarafından başvurulan bir görüntü tanımlar. GUID ve ID birlikte ele alındığında, görüntü bilinen adına oluşturur. Görüntü için bilinen ad tüm görüntü kitaplığı arasında benzersiz olması gerekir. Birden fazla görüntü belirli bir takma ad varsa, kitaplığı oluşturulurken karşılaşılan ilk korunur bir sağlayıcıdır.  
  
 En az bir kaynak içermelidir. Boyutu nötr kaynakları geniş bir grup boyutları arasında en iyi sonuçlar verir ancak bunlar gerekli değildir. Hizmet, görüntü içinde tanımlanmamış bir boyut istenirse \<Görüntü > öğesi ve boyutu nötr kaynağı yok, hizmetin en iyi boyut özgü kaynağını seçin ve istenen boyuta ölçeklendirin.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Guid|[Gerekli] Görüntü bilinen adına GUID kısmını|  
|Kimlik|[Gerekli] Resim bilinen adı kimliği bölümü|  
|AllowColorInversion|[İsteğe bağlı, varsayılan true] Görüntü programlı olarak koyu renkli bir arka plan üzerinde kullanıldığında ters renklerini olup olmadığını gösterir.|  
  
 **Kaynak**  
  
 \<Kaynak > öğesi (XAML ve PNG) tek bir görüntü kaynağı varlık tanımlar.  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|URI|[Gerekli] Gelen görüntü burada yüklenebilir tanımlayan URI. Aşağıdakilerden biri olabilir:<br /><br /> -A [paketi URI](http://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) kullanarak uygulama: / / / yetkilisi<br /><br /> -Bir mutlak bileşen kaynak başvurusu<br /><br /> -Yerel bir kaynak içeren bir dosya yolu|  
|Arka Plan|[İsteğe bağlı] Ne tür bir arka plan kaynak kullanılması amaçlanmıştır gösterir.<br /><br /> Aşağıdakilerden biri olabilir:<br /><br /> - *Işık*: kaynağı açık bir arka plan üzerinde kullanılabilir.<br /><br /> - *Koyu*: kaynağı koyu renkli bir arka plan üzerinde kullanılabilir.<br /><br /> - *Yüksek Karşıtlık*: kaynak, yüksek karşıtlık modunda herhangi bir arka plan üzerinde kullanılabilir.<br /><br /> - *HighContrastLight*: kaynak, yüksek karşıtlık modunda açık bir arka plan üzerinde kullanılabilir.<br /><br /> -*HighContrastDark*: kaynak, yüksek karşıtlık modunda koyu renkli arka plan üzerinde kullanılabilir.<br /><br /> Varsa **arka plan** özniteliği atlanırsa, kaynağı herhangi bir arka plan üzerinde kullanılabilir.<br /><br /> Varsa **arka plan** olduğu *ışık*, *koyu*, *HighContrastLight*, veya *HighContrastDark*, hiçbir zaman ters kaynağının renkler. Varsa **arka plan** yok sayıldıysa veya kümesine *Karşıtlık*, kaynağın renkleri ters çevirmeyi görüntünün tarafından denetlenir **AllowColorInversion** özniteliği.|  
  
 A \<kaynak > öğesi aşağıdaki isteğe bağlı alt öğeleri tam olarak birine sahip olabilir:  
  
||||  
|-|-|-|  
|**Öğe**|**Öznitelikler (tümü gereklidir)**|**Tanım**|  
|\<Boyutu >|Değer|Kaynak (cihaz birimlerindeki) verilen boyutta görüntüleri için kullanılacaktır. Görüntü, kare olur.|  
|\<SizeRange >|MinSize, Maxsıze|Kaynak MinSize (cihaz birimindeki) görüntülerini MaxSize aralığında kullanılacak. Görüntü, kare olur.|  
|\<Boyutlar >|Genişlik, yükseklik|Kaynak, belirtilen genişlik ve yükseklik (cihaz birimindeki) görüntülerini için kullanılır.|  
|\<DimensionRange >|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Kaynak için (cihaz birimlerindeki) maksimum genişliği/yüksekliğinin en küçük genişliği/yüksekliğinin tıempo'nun aralığında kullanılır.|  
  
 A \<kaynak > öğesi de isteğe bağlı olabilir \<NativeResource > alt öğe tanımlar bir \<kaynak > yönetilen bir derleme yerine yerel bir derleme yüklenir.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Tür|[Gerekli] XAML ya da PNG yerel kaynak türü|  
|Kimlik|[Gerekli] Yerel kaynak tamsayı kimliği bölümünü|  
  
 **ImageList**  
  
 \<ImageList > öğesi içinde tek bir Şerit döndürülebilecek görüntülerin koleksiyonu tanımlar. Şerit, gerektiğinde isteğe bağlı olarak oluşturulmuştur.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Guid|[Gerekli] Görüntü bilinen adına GUID kısmını|  
|Kimlik|[Gerekli] Resim bilinen adı kimliği bölümü|  
|Harici|[İsteğe bağlı, varsayılan false] Görüntünün geçerli bildiriminde görüntü bilinen adına başvuruda bulunup bulunmadığını gösterir.|  
  
 Kapsanan görüntü için bilinen ad geçerli bildiriminde tanımlanan görüntü başvurusu yok. Kapsanan görüntünün görüntü kitaplığı'nda bulunamazsa boş bir yer tutucu resminin onun yerine kullanılır.  
  
## <a name="how-to-use-the-tool"></a>Aracı'nı kullanma  
 **Özel görüntü bildirim doğrulanıyor**  
  
 Özel bir bildirim oluşturmak için otomatik olarak bildirim ManifestFromResources araca kullanmanızı öneririz. Özel bildirim doğrulamak için görüntü kitaplığı Görüntüleyicisi'ni başlatın ve dosyayı seçin > yolları belirle... Arama dizinlerinin iletişim kutusunu açmak için. Araç arama dizinleri görüntü bildirimlerini yüklemek için kullanın, ancak bunu ayrıca kullanacak, bir bildirim görüntüleri içeren .dll dosyaları bulmak için bunları bu nedenle bu iletişim kutusunda bildirim ve DLL dizinleri dahil emin olun.  
  
 ![Görüntü kitaplığı Görüntüleyicisi arama](../../extensibility/internals/media/image-library-viewer-search.png "görüntü kitaplığı Görüntüleyicisi arama")  
  
 Tıklayın **Ekle...** bildirimler ve bunların karşılık gelen dll için aranacak yeni arama dizinlerini seçmek için. Bu arama dizinleri araç hatırlanır ve bunlar açıp denetleme veya bir dizin işaretini kapatılabilir.  
  
 Varsayılan olarak, Visual Studio yükleme dizini bulmak ve bu dizin arama dizinleri listesine eklemek araç dener. El ile aracı bulmuyorsa dizinleri ekleyebilirsiniz.  
  
 Geçiş yapmak için tüm bildirimler yüklendikten sonra aracı kullanılabilir **arka plan** renkleri **DPI**, **Yüksek Karşıtlık**, veya **ölçeklendirme** için görüntüleri bir kullanıcı görüntü varlıkları bunlar işlenirken doğru çeşitli ayarlarını doğrulamak için görsel olarak inceleyebilmeniz adına.  
  
 ![Görüntü kitaplığı Görüntüleyicisi arka plan](../../extensibility/internals/media/image-library-viewer-background.png "görüntü kitaplığı Görüntüleyicisi arka plan")  
  
 Arka plan rengini açık, koyu veya özel bir değer ayarlanabilir. "Özel renk" seçerek bir renk seçimi iletişim kutusunu açın ve daha sonra kolayca hatırlanmalarını sağlayacak arka plan birleşik giriş kutusunun alt kısmındaki bu özel renk ekleyin.  
  
 ![Görüntü kitaplığı Görüntüleyicisi özel renk](../../extensibility/internals/media/image-library-viewer-custom-color.png "görüntü kitaplığı Görüntüleyicisi özel renk")  
  
 Bir resim bilinen adı seçerek, sağdaki resim Ayrıntılar bölmesinde, bilinen ad arkasında gerçek her görüntü bilgilerini görüntüler. Bölme bilinen adı adıyla veya ham GUID:ID değeri kopyalamak kullanıcıların de sağlar.  
  
 ![Görüntü kitaplığı Görüntüleyicisi görüntü ayrıntılarını](../../extensibility/internals/media/image-library-viewer-image-details.png "görüntü kitaplığı Görüntüleyicisi görüntü ayrıntıları")  
  
 Her bir görüntü kaynağı için görüntülenen bilgileri temalı olabilir, görüntülenecek arka plan ne tür içerir veya yüksek karşıtlık, hangi boyutları için geçerli olduğundan destekler veya boyutu nötr olup ve görüntünün yerel bir derleme mi gelir.  
  
 ![Görüntü kitaplığı Görüntüleyicisi için tema](../../extensibility/internals/media/image-library-viewer-can-theme.png "görüntü kitaplığı Görüntüleyicisi için tema")  
  
 Bir görüntü bildirimi doğrulanırken, bildirim ve görüntü gerçek konumlarına DLL'de dağıtmanızı öneririz. Bu işlem göreli yollar düzgün çalıştığından ve görüntü kitaplığı bulun ve bildirim ve görüntü DLL yükleme doğrulayın.  
  
 **Görüntü katalogda KnownMonikers için arama**  
  
 Visual Studio stil daha iyi eşleşecek şekilde, bir Visual Studio uzantı Visual Studio Görüntü Kataloğu yerine oluşturmak ve kendi kullanarak görüntüleri kullanabilirsiniz. Bu durum, bu görüntüleri bakımını yapmak zorunda avantajına sahiptir ve şuna Visual Studio'nun desteklediği tüm DPI ayarlarını doğru şekilde yüksek DPI yedekleme görüntü resmi sahip olacağını garanti eder.  
  
 Görüntü kitaplığı Görüntüleyicisi, bir kullanıcı bir resim varlığı temsil eden bir bilinen ad bulun ve kodu, bilinen adı kullanma çözümlenmesinde kullanılacak bir bildirim sağlar. Resimler için arama yapın, arama kutusuna istediğiniz arama terimini girin ve Enter tuşuna basın. Durum çubuğu altındaki ne kadar eşleşme toplam görüntüleri dışında tüm bildirimlerin bulunamadı görüntüler.  
  
 ![Görüntü kitaplığı Görüntüleyicisi filtre](../../extensibility/internals/media/image-library-viewer-filter.png "görüntü kitaplığı Görüntüleyicisi filtresi")  
  
 Görüntü bilinen Adlardaki niteleyiciyi varolan bildirimleri için arama yaparken, arayın ve yalnızca Visual Studio Görüntü Kataloğu'nun adlar, kasıtlı olarak genel olarak erişilebilir diğer adlar veya kendi özel adlar kullanmanızı öneririz. Ortak olmayan adlar kullanırsanız, özel kullanıcı Arabirimi bozuk olabilir veya bu ortak olmayan adlar ve görüntüleri değiştirildi veya güncelleştirildiğinde, görüntüleri beklenmedik bir şekilde ya da değiştirilmiştir.  
  
 Ayrıca, arama GUID ile mümkündür. Tek alt durumunda bildirim bildirimin birden çok guid'ler içeriyor veya bu arama türü tek bir bildirim listeyi filtreleme için yararlı olur.  
  
 ![Görüntü kitaplığı Görüntüleyicisi filtre GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "görüntü kitaplığı Görüntüleyicisi filtre GUID")  
  
 Son olarak, Kimliğine göre arama de mümkündür.  
  
 ![Görüntü kitaplığı Görüntüleyicisi filtre kimliği](../../extensibility/internals/media/image-library-viewer-filter-id.png "görüntü kitaplığı Görüntüleyicisi filtre kimliği")  
  
## <a name="notes"></a>Notlar  
  
-   Varsayılan olarak, araç, Visual Studio yükleme dizininde mevcut birkaç görüntü bildirimlerinde çeker. Genel olarak kullanılabilir takma ad olan tek **Microsoft.VisualStudio.ImageCatalog** bildirimi. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (yapmak **değil** bu GUID özel bildiriminde geçersiz kılma) türü: KnownMonikers  
  
-   Araç, uygulamanın gerçekten görünmesi birkaç saniye sürebilir şekilde bulduğu tüm görüntü bildirimler yük başlatmada çalışır. Ayrıca bildirimler yüklenirken yavaş veya yanıt vermeyen olabilir.  
  
## <a name="sample-output"></a>Örnek Çıktı  
 Bu araç, herhangi bir çıktı üretmez.

