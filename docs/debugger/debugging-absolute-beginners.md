---
title: Yeni başlayanlar için hata ayıklama kodu
description: İlk kez ayıklıyorsanız, Visual Studio ile hata ayıklama modunda uygulamanızı çalıştırmaya yardımcı olması için birkaç ilkelerini öğrenin
ms.custom: ''
ms.date: 07/06/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31b6812ec41aedd4e33eb0d043476365d3938767
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160029"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Yeni başlayanlar için hata ayıklama

Başarısız, biz geliştiricilerine yazma kod her zaman ne yapması beklenen yapmaz. Bazen bu tamamen farklı bir şey yok! Bu durumda, sonraki görev nedenini anlamak için ve biz yalnızca bizim kodu saatliğine başlamanızı tutmak fikri size cazip olabilir, ancak bu çok daha kolay ve verimli bir hata ayıklama aracı kullanın veya hata ayıklayıcı için.

Ne yazık ki bir hata ayıklayıcı Sihirli tüm sorunlar veya "hatalar" bizim kodu ortaya çıkarabilir, bir şey değildir. *Hata ayıklama* anlamına gelir, bir hata ayıklama aracı adım adım kodunuzu çalıştırmak için bir programlama hata burada yaptığınız tam noktasını bulmak için Visual Studio'yu, ister. Daha sonra kodunuzda yapmanız gereken hangi düzeltmeler anlamak ve hata ayıklama araçları genellikle programı çalıştırmaya devam etmek için geçici değişiklik yapmanızı sağlar.

Bir hata ayıklayıcı etkili bir şekilde kullanarak, zaman ve bilgi edinmek için uygulama ancak sonuçta her yazılım geliştiricisinin için temel bir görevi bir yetenek olduğu. Bu makalede daha sonra hata ayıklama temel ilkelerini tanıtan ve başlamanıza yardımcı olmak için ipuçları sağlar.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Sorunu doğru soruları kendinize sorarak açıklamak

Bu sorunu gidermek denemeden önce içine çalıştırdığınız sorunu açıklamak için yardımcı olur. Bir sorunla karşılaşırsanız zaten kodunuzda çalıştırıldığı bekliyoruz, aksi takdirde, buradan hata ayıklamak nasıl çalışıyor mıydı! Hata ayıklamaya başlamadan önce bu nedenle, çözmeye çalıştığınız sorunu tespit ettik emin olun:

* Ne yapmak için kodunuzu bekliyorsunuz?

* Bunun yerine ne oldu?

    Uygulamanız çalışırken bir hatayla (özel durum) çalıştırdıysanız, iyi bir şey olabilir! Bir özel durum kodu, genellikle bir tür hata çalışırken karşılaşılan beklenmeyen bir olaydır. Hata ayıklama aracı kodunuzda özel durumun oluştuğu tam yere alabilir ve olası düzeltmeleri araştırmanıza yardımcı olabilir.

    Başka bir sorun oluştu, sorunun belirtisi nedir? Kodunuzda sorun oluştuğu şüpheleniyorsanız zaten? Örneğin, metin kodunuzu görüntüler, ancak metin yanlış varsa, verilerinizi bozuk veya görüntülenecek metni ayarlamak kod hata tür sahip bilirsiniz. Kodda bir hata ayıklayıcı ile Adımlama tarafından tam olarak ne zaman ve hatalı değerler atanır nasıl keşfetmek için değişkenlerinizi her değişiklik inceleyebilirsiniz.

## <a name="examine-your-assumptions"></a>Bir varsayım inceleyin

Bir hata veya bir hata araştırma önce belirli bir sonucun yaptığınız özelliklerinin düşünün. Gizli veya bilinmeyen varsayımlar bile, bir hata ayıklayıcıda doğru sorunun nedenini düşünürken, bir sorunu tanımlama in the way of alabilirsiniz. Olası varsayımlar uzun listesi olabilir! Burada, kendinize meydan okuyun, varsayımlar istemek için bir kaç soru bulunmaktadır.

* Doğru API (diğer bir deyişle, doğru nesne, işlevi, yöntemi veya özelliği) kullanıyor musunuz? Kullanmakta olduğunuz API mevcut düşüncelerinizi bunu yapmanız gerekebilir. (Hata ayıklayıcısı API çağrısı inceledikten sonra düzeltme doğru API'ye belirlemenize yardımcı olması için belgeler etmek gerekebilir.)

* Bir API doğru kullanıyorsunuz? Belki de API sağ kullanılan ancak doğru şekilde kullanmadı.

* Kodunuzu herhangi bir yazım hatası içeriyor mu? Bir değişken adı basit bir yazım hatası gibi bazı yazım hataları, özellikle kullanıldıklarından önce bildirilmesi için değişkenleri gerektirmeyen dilleriyle çalışırken görmek zor olabilir.

* Kodunuzda değişiklik ve sizin gördüğünüz sorunla ilgisi olduğu varsayılır?

* Bir nesne veya belirli bir değere (veya belirli bir tür değeri) içeren değişkeni bekliyorsunuz farklı ne gerçekten oldu?

* Kodun amacı biliyor musunuz? Daha fazla genellikle olduğu kod başkası hata ayıklaması zor. Kodunuzu değilse, etkili bir şekilde ayıklayabilirsiniz önce tam olarak ne yaptığını zaman öğrenme harcama gerekebilir mümkündür.

    > [!TIP]
    > Kod yazarken küçükten başlayabilir ve çalışan kodla başlayın! (İyi örnek kodu buraya yararlı olur.) Bazı durumlarda, kod büyük veya karmaşık bir dizi küçük elde etmek çalıştığınız temel göreviyle gösteren kod parçasını ile başlatarak düzeltmek kolaydır. Ardından, değiştirebilir veya hatalar için her bir noktada test kodu kademeli olarak ekleyin.

Bir varsayım sormasını tarafından kodunuzda bir sorunu bulmak için gereken süreyi azaltabilir. Ayrıca, bir sorunu gidermek için gereken süreyi azaltabilir.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Hata ayıklama modunda sorunun gerçekleştiği bulmak için kodunuzu adım adım

Normal bir uygulama çalıştırdığınızda, yalnızca kod çalıştırıldıktan sonra hataları ve hatalı sonuçlar görürsünüz. Bir program ayrıca beklenmedik bir şekilde nedenini belirten olmadan sonlandırabilir.

Bir hata ayıklayıcısı içinde bir uygulamayı çalıştıran olarak da adlandırılır *hata ayıklama modu*, hata ayıklayıcı etkin bir şekilde program çalışırken gerçekleştiği her şeyi izlediğini anlamına gelir. Ayrıca uygulamayı herhangi bir noktada durumunu inceleyin ve sonra da olduğu sürece her ayrıntısını izlemek için satır kodunuzda adım adım ilerleyin duraklatmanıza da olanak sağlar.

Visual Studio'da hata ayıklama modunu kullanarak girdiğiniz **F5** (veya **hata ayıklama** > **hata ayıklamayı Başlat** menü komutu veya **hata ayıklamayı Başlat**  düğmesi ![hata ayıklamayı Başlat](../debugger/media/dbg-tour-start-debugging.png "hata ayıklamayı Başlat") hata ayıklama araç çubuğundaki). Özel durumlar oluşursa, Visual Studio'nun özel durum Yardımcısı burada özel durum oluştu ve başka yararlı bilgiler sağlayan tam noktasına götürür.

Bir özel durum almadıysanız, kodunuzda sorunun aranacağı büyük olasılıkla iyi bir fikir sahip. Bu, kullandığınız *kesme noktaları* kendiniz kodunuzu daha dikkatli bir şekilde incelemek için bir fırsat vermek için hata ayıklayıcısı ile. Kesme noktaları güvenilir hata ayıklama en temel hem de temel özelliğidir. Bir kesme noktası, değişkenlerin değerleri veya bellek davranışını veya kod çalıştığı dizisi göz olabilmesi için Visual Studio çalışan kodunuzu nerede duraklatmak gösterir.

Visual Studio'da kod satırının yanındaki sol kenar boşluğunu tıklatarak hızlı bir şekilde bir kesme noktası ayarlayabilirsiniz. Veya bir satır ve ENTER tuşuna imleci **F9**.

Bu kavramları göstermeye yardımcı olmak için size çeşitli hatalar zaten bazı örnek kod göz önüne almanız. Kullanıyoruz C#, ancak hata ayıklama özellikleri için Visual Basic, C++, JavaScript, Python ve diğer desteklenen dilleri geçerlidir.

### <a name="create-a-sample-app-with-some-bugs"></a>(Bazı hatalar ile) örnek bir uygulama oluşturun

Ardından, bazı hataları olan bir uygulama oluşturacağız.

1. Visual Studio yüklü ve ya da sahip **.NET masaüstü geliştirme** iş yükü veya **.NET Core çoklu platform geliştirme** iş yükü yüklenmiş, oluşturmak istediğiniz hangi uygulama türü üzerinde bağlı olarak.

    Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ücretsiz yüklemek için sayfa.

    İş yükünü yükleyin, ancak Visual Studio'a tıklayın, zaten gerektiğinde **Araçları** > **araçları ve özellikleri Al**. Visual Studio Yükleyicisi'ni başlatır. Seçin **.NET masaüstü geliştirme** (veya **.NET Core çoklu platform geliştirme**) iş yükü, ardından **Değiştir**.

1. Visual Studio'yu açın ve ardından **dosya** > **yeni** > **proje**.

1. Uygulama kodunuz için bir şablon seçin.

    .NET Framework içinde **yeni proje** iletişim kutusunda **Visual C#**, **Windows Masaüstü** Yüklü Şablonlar bölümünden ve Ortabölmedeseçin **Konsol uygulaması (.NET Framework)**.

    .NET Core için de **yeni proje** iletişim kutusunda **Visual C#**, **.NET Core** Yüklü Şablonlar bölümünden ve Orta bölmede seçin  **Konsol uygulaması (.NET Core)**.

    Bu şablonlar görmüyorsanız, uygun iş yükü yüklemeniz gerekir (önceki adımlara bakın).

1. İçinde **adı** alanına **ConsoleApp FirstApp** tıklatıp **Tamam**.

    Visual Studio Çözüm Gezgini'nde sağ bölmede görünür konsol projesi oluşturur.

1. İçinde *Program.cs*, tüm varsayılan kodu aşağıdaki kodla değiştirin:

    ```csharp
    using System;
    using System.Collections.Generic;
    
    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }
    
            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };
    
                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }
    
                // Expected Output:  
                //  Tadpole  400,  Spiral 
                //  Pinwheel  25,  Spiral 
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }
    
        public class Galaxy
        {
            public string Name { get; set; }
    
            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }
    
        }
    
        public class GType
        { 
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    Amacımız bu kodun bir listedeki tüm galaxy ve galaxy türü uzaklık galaxy adı görüntülemektir. Hata ayıklamak için kodun amacı anlamak önemlidir. Çıkışta göstermek istiyoruz listesinden bir satır için biçim şu şekildedir:

    *galaxy adı*, *uzaklık*, *galaxy türü*.

### <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Tuşuna **F5** veya **hata ayıklamayı Başlat** düğmesi ![hata ayıklamayı Başlat](../debugger/media/dbg-tour-start-debugging.png "hata ayıklamayı Başlat") hata ayıklama araç çubuğunda, Kod Düzenleyicisi'ni bulunan.

    Uygulama başlatılır ve bize hata ayıklayıcı tarafından gösterilen özel durum vardır. Ancak, çıktıyı konsol penceresinde beklediğiniz olabilir. Beklenen çıktı aşağıdaki gibidir:

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Ancak, bunun yerine görürüz:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Çıkış ve kodumuz bakarak, biliyoruz `GType` galaxy türü depolayan sınıf adıdır. Gerçek galaxy türlerinin (örneğin, "Gönderilerinizi") göstermek çalışıyoruz sınıf adını değil!

### <a name="debug-the-app"></a>Uygulamasında hata ayıklama

1. Hala çalışıyor uygulamayla yanındaki sol kenar boşluğunu tıklayarak kesme noktası ayarlamak `Console.WriteLine` yöntem çağrısında Bu kod satırı.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    Kesme noktası ayarlarsanız, kırmızı bir nokta sol kenar boşluğunda görünür.

    Bir sorun çıktı görüyoruz olduğundan, hata ayıklayıcıya çıktı ayarlar önceki kod bakarak hata ayıklama başlayacağız.

1. Tıklayın **yeniden** ![yeniden uygulama](../debugger/media/dbg-tour-restart.png "RestartApp") hata ayıklama araç çubuğu düğmesini (**Ctrl** + **kaydırma**   +  **F5**).

    Uygulama, ayarladığınız kesme noktasında duraklatır. Sarı Vurgu, hata ayıklayıcı burada duraklatıldı belirtir (kod satırının sarı henüz çalıştırılmadı).

1. Üzerine `GalaxyType` sağdaki ve ardından sol tarafındaki İngiliz anahtarı simgesine değişkeni genişletin `theGalaxy.GalaxyType`. Gördüğünüz `GalaxyType` bir özellik içeriyor `MyGType`, ve özellik değerini ayarlamak `Spiral`.

    ![Bir değişken inceleyin](../debugger/media/beginners-inspect-variable.png)

    "Gönderilerinizi" aslında konsola yazdırmak için görmeyi beklediğiniz doğru değer olan! Dolayısıyla, uygulama çalıştırılırken bu değer bu kodda erişebilirsiniz iyi bir başlangıç noktasıdır. Bu senaryoda, yanlış API'sini kullanıyoruz. Biz bu hata ayıklayıcıda kod çalıştırılırken düzeltmeyi göreceğiz.

1. Aynı kod içinde hala hata ayıklama sırasında imlecinizi sonunda put `theGalaxy.GalaxyType` ve değiştirmek için `theGalaxy.GalaxyType.MyGType`. Bu değişiklik yapabileceğiniz rağmen Kod Düzenleyicisi, bu kodu derleyebilir belirten bir hata gösterir.

    ![Sözdizimi hatası](../debugger/media/beginners-edit.png)

1. Tıklayın **Düzenle** içinde **Düzenle ve devam et** ileti kutusu. Bir hata iletisi artık bkz **hata listesi** penceresi. Hatayı bildiren `'object'` için bir tanım içermiyor `MyGType`.

    ![Sözdizimi hatası](../debugger/media/beginners-no-definition.png)

    Türünde bir nesne ile her galaxy ayarladığımız olsa bile `GType` (sahip `MyGType` özelliği), hata ayıklayıcı tanımıyor `theGalaxy` nesne türünde bir nesne olarak `GType`. Ne var ne yok? Galaxy türünü ayarlar herhangi bir kod görünmesini istediğiniz. Bunu yaptığınızda gördüğünüz `GType` sınıfı kesinlikle bir özelliğine sahip `MyGType`, ancak bir şey doğru değildir. İlgili hata iletisi `object` ; ipucu olmasını ettik dil yorumlayıcısı türü bir nesne türü görünmektedir `object` türünde bir nesne yerine `GType`.

1. Bulduğunuz galaxy türü ayarlamakla ilgili kodunuzu aramak, `GalaxyType` özelliği `Galaxy` sınıfı olarak belirtilen `object` yerine `GType`.

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. Yukarıdaki kod şuna değiştirin:

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. Tıklayın **yeniden** ![yeniden uygulama](../debugger/media/dbg-tour-restart.png "RestartApp") hata ayıklama araç çubuğu düğmesini (**Ctrl** + **kaydırma**   +  **F5**) kodu yeniden derlemeniz ve yeniden başlatın.

    Artık, hata ayıklayıcı duraklatır üzerinde `Console.WriteLine`, üzerine gelerek `theGalaxy.GalaxyType.MyGType`ve değer düzgün şekilde ayarlandığını bakın.

1. Sol kenar boşluğunda kesme noktası daireye tıklayarak kesme noktasını Kaldır (veya sağ tıklayıp seçin **kesme noktası** > **Sil kesme noktası**) ve tuşuna **F5** devam etmek için.

    Uygulama çalışır ve çıktıyı görüntüler. Artık oldukça iyi görünüyor, ancak bir şey dikkat edin. Konsol çıkışında düzensiz bir galaxy olarak görünmesi küçük Magellanic bulut galaxy bekleniyordu ancak hiç galaxy tür gösterir.

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Bu kod satırında bir kesme noktası ayarlayın.

    ```csharp
    public GType(char type)
    ```

    Bu kod galaxy türü ayarlandığı daha yakından göz atın istiyoruz olduğundan.

1. Tıklayın **yeniden** ![yeniden uygulama](../debugger/media/dbg-tour-restart.png "RestartApp") hata ayıklama araç çubuğu düğmesini (**Ctrl** + **kaydırma**   +  **F5**) yeniden başlatmak için.

    Hata ayıklayıcı, Kesme noktasının ayarlandığı kod satırında duraklatır.  

1. Üzerine `type` değişkeni. Değerini gördüğünüz `S` (karakter kodunu izleyerek). Değerini ilgilendiğiniz `I`, düzensiz galaxy türü olduğunu bildiğiniz.

1. Tuşuna **F5** ve üzerine `type` yeniden değişkeni. Değerini görene kadar bu adımı yineleyin `I` içinde `type` değişkeni.

    ![Bir değişken inceleyin](../debugger/media/beginners-inspecting-data.png)

1. Şimdi, basın **F11** (**hata ayıklama** > **içine adımla** veya **içine adımla** hata ayıklama araç çubuğu düğmesi).

    **F11** aynı anda bir deyim hata ayıklayıcı ilerler (ve kodu çalıştırır). **F10** (**Step Over**) benzer bir komutu ve hem de hata ayıklayıcı kullanmayı öğrenirken son derece yararlıdır.

1. Tuşuna **F11** kod satırında durduruncaya kadar `switch` 'I' değeri ifadesi. Burada, bir yazım yanlışı kaynaklanan sorununu Temizle bakın. Burada ayarlar ilerlemek için kod beklenen `MyGType` bir düzensiz galaxy türü, ancak hata ayıklayıcı bunun yerine bu kod tamamen atlar ve üzerinde duraklatır `default` bölümünü `switch` deyimi.

    ![Bir yazım yanlışı Bul](../debugger/media/beginners-typo.png)

    Koda baktığınızda, bir yazım yanlışı bkz `case 'l'` deyimi. Olmalıdır `case 'I'`.

1. Tıklayın kodunda `case 'l'` değiştirin `case 'I'`.

1. Kesme noktasına kaldırın ve ardından **yeniden** düğmesini uygulamayı yeniden başlatın.

    Artık düzeltilen hatalar ve beklediğiniz bir çıktı görmeniz!

    Uygulama tamamlamak için herhangi bir tuşa basın.

## <a name="summary"></a>Özet

Bir sorun gördüğünüzde, hata ayıklayıcıyı kullanın ve [adım komutları](../debugger/navigating-through-code-with-the-debugger.md) gibi **F10** ve **F11** sorunlu kod bölgesi bulunamadı.

> [!NOTE]
> Sorunun gerçekleştiği bölge kodu belirlenmesi zordur, sorun oluşmadan önce çalışan kod içinde bir kesme noktası ayarlayın ve sorun görene kadar adım komutları kullanın bildirimi. Ayrıca [izleme noktaları](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) oturum iletileri **çıkış** penceresi. Tarafından günlüğe kaydedilen iletilere bakarak (ve iletileri henüz günlüğe kaydedilmiyordu tercihinize!), bölge kodu ile sorun genellikle ayırabilirsiniz. Bunu daraltmak için birkaç kez bu işlemi tekrarlamanız gerekebilir.

Bölge kodu ile sorun bulduğunuzda araştırmak için hata ayıklayıcı'yı kullanın. Bir sorunun nedenini bulmak için hata ayıklayıcıda uygulamanız çalışırken sorun kodu inceleyin:

* [Değişkenleri İnceleme](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) ve türü içermesi gereken değerler içeren olup olmadığını denetleyin. Hatalı bir değer görürseniz, hatalı değeri burada ayarlandı bulun (değere ayarlandığı bulmak için ihtiyacınız olabilecek ya da hata ayıklayıcıyı yeniden başlatın, bakmak [çağrı yığını](../debugger/how-to-use-the-call-stack-window.md), veya her ikisi de).

* Uygulamanızın beklediğiniz kodu yürüten olup olmadığını denetleyin. (Örneğin, örnek uygulamada, galaxy türü düzensiz için ayarlanacak switch deyimi için kod bekliyorduk, ancak uygulama kodu yazım hatası nedeniyle atlandı.)

> [!TIP]
> Bir hata ayıklayıcısı, hataları bulmanıza yardımcı olması için kullanın. Hata ayıklama aracı hataları bulabilirsiniz *sizin için* yalnızca kodunuzun amacı biliyorsa. Bu amacı, geliştirici olarak size express, bir aracı yalnızca, kodun amacı bilemez. Yazma [birim testleri](../test/improve-code-quality.md) bunu nasıl olduğu. 

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, birkaç genel hata ayıklama kavramları öğrendiniz. Ardından, hata ayıklayıcısı hakkında daha fazla bilgi edinmeye başlayabilirsiniz.

> [!div class="nextstepaction"]
> [Visual Studio kullanarak hata ayıklamayı öğrenin](../debugger/getting-started-with-the-debugger.md)
