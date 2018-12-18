---
title: Pencere düzenlerini özelleştirme
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e37adb6296a805b8a0fd06196e7ccf1acf5bc32e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057574"
---
# <a name="customizing-window-layouts-in-visual-studio"></a>Visual Studio’da pencere düzenlerini özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da, konum, boyut ve çeşitli geliştirme iş akışları için en iyi pencere düzenlerini oluşturmak için windows davranışını özelleştirebilirsiniz. Düzen'nı özelleştirdiğinizde, IDE hatırlar. Örneğin, yerleştirme konumunu değiştirirseniz **Çözüm Gezgini** ve Visual Studio başka bir bilgisayarda çalışıyorsanız olsa bile, Başlat, sonraki açışınızda kapatın **Çözüm Gezgini** olacaktır aynı konuma sabitlenmiş. Ayrıca özel bir düzen bir ad verin ve kaydedin ve sonra tek bir komutla düzeni arasında geçiş yapın. Örneğin, düzenlemek için bir düzen ve hata ayıklama için başka oluşturup kullanarak aralarında geçiş **penceresi &#124; pencere düzenini Uygula** menü komutu.

## <a name="kinds-of-windows"></a>Pencere Cinsleri

### <a name="tool-and-document-windows"></a>Araç ve belge Windows
 İki temel pencere türleri, IDE olan *araç pencerelerini* ve *belge windows*. Araç pencereleri, Çözüm Gezgini, Sunucu Gezgini, çıkış penceresi, hata listesi, tasarımcılar, hata ayıklayıcı pencereleri vb. içerir. Belge pencereleri, kaynak kodu dosyaları, rastgele metin dosyaları, yapılandırma dosyaları vb. içerir. Araç pencereleri yeniden boyutlandırıldı ve bunların başlık çubuğundaki sürüklediğiniz. Belge pencereleri tarafından kendi sekme sürüklenebilir. Penceredeki diğer seçeneklerini ayarlamak için sekmesinde veya başlık çubuğunun sağ tıklayın.

 **Penceresi** kayan ve IDE'de pencereleri gizleme takma seçenekleri menüsü gösterir. Belirli bir pencere için ek seçenekleri görmek üzere bir penceresi sekme veya başlık çubuğunun sağ tıklayın. Aynı anda birden fazla örneğini belirli araç pencereleri görüntüleyebilirsiniz. Örneğin, birden fazla web tarayıcısı penceresi görüntüleyebilir ve bazı araç pencerelerinin ek örneklerini seçerek oluşturabilirsiniz **yeni pencere** üzerinde **penceresi** menüsü.

### <a name="preview-tab-document-windows"></a>Önizleme sekmesini (belge windows)
 Önizleme sekmesinde açmaya gerek kalmadan dosya Düzenleyicisi'nde görüntüleyebilirsiniz. Bunları seçerek dosyaları önizleyebilirsiniz **Çözüm Gezgini**, dosyaları, Tanıma Git üzerinde Adımlama yaptığınızda ve hata ayıklama sırasında bir arama sonuçlarını Gözat. Önizleme dosyalar bir sekmede iyi belge sekmesini sağ tarafında görünür. Dosyayı değiştirmek veya seçin, düzenleme için açar **açık**.

### <a name="tab-groups"></a>Sekme grupları
 Sekme grupları IDE içindeki iki veya daha fazla açık belgeler ile çalışırken, sınırlı çalışma alanını yönetme olanağı genişletin. Birden çok belge pencereleri ve araç pencerelerini, dikey veya yatay sekme grupları ve karışık belge sekme grubundan diğerine halinde düzenleyebilirsiniz.

### <a name="split-windows"></a>Windows Böl
 Bir belgede aynı anda iki konuma görüntüleyemez veya varsa, windows bölebilirsiniz. Belgenizi iki bağımsız olarak kaydırma bölümlere ayırmak için tıklayın **bölünmüş** üzerinde **penceresi** menüsü. Tıklayın **Bölmeyi Kaldır** üzerinde **penceresi** tek bir görünüm geri yüklemek için menü.

### <a name="toolbars"></a>Araç Çubukları
 Araç çubukları düzenlenmiş sürükleyerek ya da kullanarak **Özelleştir** iletişim kutusu. Getirin ve araç çubuklarını özelleştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: özelleştirme menüleri ve araç çubuklarını](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arranging-and-docking-windows"></a>Düzenleme ve Windows yerleştirme
 Her ikisi de windows belge ve araç pencerelerini olabilir *yerleştirilmiş*, konum ve boyut IDE pencere çerçevesi veya ayrı bir pencerede IDE'yi bağımsız değişken sahip olacak şekilde. Araç pencerelerini IDE çerçevesinin içinde her yerden yerleştirilmiş olabilir; Bazı araç pencerelerinin Düzenleyicisi çerçevesindeki sekmeli pencerelerin olarak sabitlenebilir. Belge pencereleri Düzenleyicisi çerçevesinde sabitlenebilir ve geçerli konumlarına sekme sırasını sabitlenebilir. Birlikte bir "raft" içinde veya dışında IDE içinde kaydırmak için birden çok windows sabitleyebilirsiniz. Araç pencerelerini de gizli veya simge.

 Aşağıdaki yollarla windows düzenleyebilirsiniz:

- Belge pencerelerini sekme soluna iyice sabitleyin.

- Düzenleme çerçevesindeki için sekmesinde dock windows.

- Araç Pencereleri IDE içinde bir çerçevenin kenarına yerleştir.

- Belge veya aracı windows üzerinde veya IDE dışında yüzdürün.

- Araç pencerelerini IDE kenarında gizleyin.

- Windows, farklı monitörlerde görüntüleyin.

- Pencere yerleşimini varsayılan düzene veya kaydedilen özel bir düzen sıfırlayın.

  Araç ve belge pencereleri düzenlenmiş, komutlar kullanılarak sürükleyerek **penceresi** menüsünde ve düzenlenmesini pencerenin başlık çubuğuna sağ tıklanarak.

> [!NOTE]
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

### <a name="docking-windows"></a>Windows yerleştirme
 ' A tıklayın ve bir araç penceresinin başlık çubuğunda veya belge penceresi için sekmesinde sürükleyin, kılavuz elmas görünür. Fare imleci üzerine elmas okları olduğunda sürükleme işlemi sırasında artık fare düğmesini serbest bırakırsanız penceresi nereye yerleştirilir gösteren gölgeli bir alanı görünür.

 Yerleştirilebilir bir pencereyi, yapıştırmadan taşımak için pencereyi sürüklerken Ctrl tuşunu seçin.

 Araç penceresi ya da belge penceresini en son sabitlenmiş konumuna geri dönmek için basın **CTRL** başlık çubuğunda veya pencerenin sekme çift tıklatırken aynı.

 Aşağıdaki çizimde, yalnızca düzenleme çerçevesinde yuvalanabilir belge windows için kılavuz elmas gösterir:

 ![Belge penceresi kılavuz elmas](../ide/media/documentwindowguidediamonds.png "Documentwindowguidediamonds")

 Araç Pencereleri IDE içinde veya düzenleme çerçevesindeki içinde bir çerçevenin bir tarafına sabitlenebilir. Araç penceresini pencereyi kolayca yeniden yerleştirmenize yardımcı olması için başka bir konuma sürüklediğinizde kılavuz elmas görünür.

 Araç pencereleri için kılavuz elmas

 ![Araç penceresi Kılavuzu Karo](../ide/media/vs10guidediamond.png "VS10GuideDiamond")

 Çözüm Gezgini mavi gölgeli alan tarafından gösterilen yeni bir konumda yerleştirilmiş aşağıda gösterilmiştir:

 ![Çözüm Gezgini içinde yeni bir konuma yerleştirme](../ide/media/vs2015-dock-diamond.png "VS2015_Dock_diamond")

### <a name="closing-and-auto-hiding-tool-windows"></a>Kapatma ve otomatik gizleme araç pencereleri
 Bir araç penceresinin başlık çubuğunun sağ üst köşesindeki X tıklayarak kapatabilirsiniz; pencereyi yeniden açmak için klavye kısayol ya da menü komutunu kullanın. Araç pencereleri, bir pencere farklı bir pencere kullandığınızda dışına kaymasına neden Otomatik Gizle, adlandırılmış bir özelliği destekler. Bir pencere otomatik olarak gizlendiğinde, adı IDE'nin kenarındaki sekmede görünür. Pencereyi tekrar kullanmak için sekmenin görünüme geri yönlendirebilmesi için sekmesinde gidin.

 ![Otomatik Gizle](../ide/media/vs2015-auto-hide.png "vs2015_auto_hide")

> [!NOTE]
>  Otomatik Gizle mi çalışacağını ayarlamak için windows ayrı ayrı veya sabitlenmiş gruplar halinde seçin veya temizleyin **otomatik gizle düğmesi sadece etkin araç pencerelerini etkiler** içinde **seçenekleri** iletişim kutusu. Daha fazla bilgi için [genel, ortam, Seçenekler iletişim kutusu](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
>  Pencere odaklandığında Otomatik Gizle özelliği etkin olan araç pencereleri geçici olarak görüntüye girebilir. Pencereyi yeniden gizlemek için geçerli pencere dışında bir öğe seçin. Pencere odağı kaybettiğinde, görünümden çıkar.

### <a name="specifying-a-monitor"></a>İzleyici belirtme
 İkinci bir monitörünüz varsa ve işletim sisteminizin destekliyorsa, hangi monitörün pencere görüntüleyeceğini seçebilirsiniz. Hatta birden fazla windows "rafts" içinde diğer monitörlerde gruplayabilirsiniz.

> [!TIP]
>  Birden çok örneğini oluşturduğunuz **Çözüm Gezgini** ve başka bir monitöre taşıyabilirsiniz. Pencereye sağ tıklatın ve seçin **Yeni Çözüm Gezgini görünümü**. Ctrl tuşunu seçip çift tıklayarak tüm windows özgün monitöre geri dönebilirsiniz.

### <a name="reset-name-and-switch-between-window-layouts"></a>Sıfırlama, adı ve pencere düzenlerini arasında geçiş yapma
 Kullanarak ayarlar koleksiyonunuz için özgün pencere düzenini IDE döndürebilir **pencere düzenini Sıfırla** komutu. Bu komutu çalıştırdığınızda, aşağıdaki eylemler gerçekleşir:

-   Tüm pencereler varsayılan konumlarına taşınır.

-   Varsayılan pencere düzeninde kapatılan Windows kapatılır.

-   Varsayılan pencere düzeninde Windows açılır.

### <a name="create-and-save-custom-layouts"></a>Oluşturun ve özel düzenler kaydedin
 Visual Studio 2015, en fazla 10 özel pencere düzenlerini ve ikisi arasında hızlıca geçiş sağlar. Aşağıdaki adımlarda, oluşturma, kaydetme, çağırma ve her iki yerleşik ve kayan araç pencereleri ile birden çok monitör yararlanan özel düzenler yönetmek gösterilmektedir.

 İlk olarak, iki proje içeren bir test çözümü her biri farklı bir en iyi düzen oluşturun.

##### <a name="create-a-ui-project-and-customize-the-layout"></a>Bir kullanıcı Arabirimi projesi oluşturun ve düzeni özelleştirme

1.  İçinde **yeni proje** iletişim kutusunda, bir Visual C# WPF masaüstü uygulaması oluşturun ve dilediğiniz çağırın. Bu proje alanı Tasarımcı penceresinin en üst düzeye çıkarmak ve diğer araç pencereleri dışına taşımak istediğimiz şekilde burada biz kullanıcı arabiriminde yoğun şekilde kullanacağınız olduğunu anlatabilirsiniz.

2.  Birden çok monitörü varsa, çekme **Çözüm Gezgini** penceresi ve **özellikleri** pencere üzerinde ikinci bir monitörünüz. Tek bir izleme sistemine, Tasarımcı dışındaki tüm windows kapatmayı deneyin.

3.  Tuşuna **Ctrl + Alt + X** araç kutusu görüntülenecek. Pencerenin yerleştirilmişse, böylece bir, iki monitörde konumlandırma için istediğiniz yerde gezinen sürükleyin.

4.  Visual Studio hata ayıklama modu içine yerleştirmek için F5 tuşuna basın. Otolar ve çağrı yığını windows bunları istediğiniz gibi hata ayıklama çıkış konumunu ayarlayın. Düzenleme modunda hem hata ayıklama modunda oluşturmak üzere olduğunuz düzeni uygulanır.

5.  Katmanlarınızı hem hata ayıklama modu, hem de düzenleme modunda olduğunda istediğiniz, ana menüden **penceresi > pencere düzenini Kaydet**. Bu düzen "adı Tasarımcı" çağrısı

     Ctrl + Alt + 1... ayrılmış listesinden yeni düzeninizi sonraki klavye kısayolunu atandığını dikkat edin. 0.

##### <a name="create-a-database-project-and-layout"></a>Bir veritabanı projesi oluşturup düzeni

1.  Yeni bir **SQL Server veritabanı** çözüme bir proje.

2.  Yeni Çözüm Gezgini'nde projeye sağ tıklayın ve seçin **Nesne Gezgini görünümünde**. Bu görüntüler **SQL Server Nesne Gezgini** access tabloları, görünümleri ve veritabanınızdaki diğer nesnelerin sağlayan bir pencere. Bu pencere float veya yerleşik bırakın. Diğer araç pencereleri, istediğiniz şekilde ayarlayın. Eklenen gerçekçilik için gerçek bir veritabanı ekleyebilirsiniz, ancak bu kılavuz için gerekli değildir.

3.  Düzeninizi nasıl istediğinizi olduğunda, ana menüden **penceresi > pencere düzenini Kaydet**. Bu düzen "DB proje" çağrısı (Biz bu proje için hata ayıklama modu Yerleşimli çıkarmaz.)

##### <a name="switch-between-the-layouts"></a>Düzeni arasında geçiş yapın

1.  Düzeni arasında geçiş yapmak için klavye kısayollarını kullanın veya ana menüden **penceresi > pencere düzenini Uygula**.

     ![Pencere düzeni menüsü uygulamak](../ide/media/vs2015-applywindowlayout.png "VS2015_ApplyWindowLayout")

     UI düzenini uyguladıktan sonra hem de düzenleme modunda hata ayıklama modunda düzenini nasıl korunur unutmayın.

     Çoklu monitör Kurulum ve tek bir izleyici dizüstü evde varsa, her makine için iyileştirilmiş düzenleri oluşturabilirsiniz.

     Not: bir çoklu monitör düzeni tek izleme sisteminde uygularsanız, ikinci monitörde yerleştirilen kayan windows artık Visual Studio penceresinin gizlenir. Alt + Sekme tuşuna basarak bu windows öne getirebilirsiniz. Daha sonra Visual Studio ile birden çok monitör açarsanız, düzenini yeniden uygulayarak windows belirtilen konumlarına geri yükleyebilirsiniz.

##### <a name="manage-and-roam-your-layouts"></a>Yönetme ve katmanlarınızı Dolaşımda

1.  Kaldırabilir, yeniden adlandırmak veya seçerek özel düzeninizi yeniden sıralama **penceresi > pencere düzenlerini Yönet**. Bir düzen taşırsanız, tuş bağlama listesinde yeni konumunu gösterecek şekilde otomatik olarak ayarlanır. Değiştirilen bağlamaları aksi olamaz ve bu nedenle aynı anda en fazla 10 düzenleri depolayabilirsiniz.

     ![Pencere düzenlerini Yönet](../ide/media/managewindowlayouts.png "ManageWindowLayouts")

     Öğesini kendiniz hatırlatan hangi klavye kısayol hangi düzene atanmış **penceresi > pencere düzenini Uygula**.

     Bu düzenleri otomatik olarak Visual Studio sürümleri arasında ve Blend örnekleri ayrı makinelerde ve tüm Express sürümleri için herhangi bir Express kuruluş arasında dolaşıma girer. Ancak, düzenleri Visual Studio, Blend ve Express Dolaşımda değil.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Windows türleri](../misc/kinds-of-windows.md)|IDE'de araç pencereleri ve belge pencereleri arasındaki farkları ele alır.|
|[Nasıl yapılır: pencereleri düzenleme ve yerleştirme Windows](../misc/how-to-arrange-and-dock-windows.md)|Pencereleri nasıl sabitleyeceğiniz, otomatik olarak gizleyeceğiniz, döşeyeceğiniz ve ayrıca pencere düzenini nasıl sıfırlayacağınız açıklanır.|
|[Nasıl Yapılır: IDE'de Gezinme](../ide/how-to-move-around-in-the-visual-studio-ide.md)|IDE'de, kullanım sırasına göre, açık pencereler arasında nasıl geçiş yapacağınız açıklanır. Ayrıca belirli belgelere nasıl atlayabileceğinizi açıklar.|
|[Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)|Ayar bileşimleri ve ayarların pencere düzenlerini, klavye kısayollarını ve IDE'deki diğer öğeleri nasıl etkilediği hakkında bilgi içerir.|
