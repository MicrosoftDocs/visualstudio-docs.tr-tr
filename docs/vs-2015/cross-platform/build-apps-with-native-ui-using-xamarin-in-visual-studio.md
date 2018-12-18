---
title: Xamarin kullanılarak yerel UI ile uygulamalar oluşturun
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
caps.latest.revision: 33
ms.author: crdun
manager: crdun
ms.openlocfilehash: 7a17f8468eca37b5b977aa6b892e268bda5376ba
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066254"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Visual Studio’da Xamarin kullanarak yerel kullanıcı arabirimi ile uygulama oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Adımları yaptıktan sonra [Kurulum ve yükleme](../cross-platform/setup-and-install.md) ve [Xamarin ortamınızı doğrulama](../cross-platform/verify-your-xamarin-environment.md), bu izlenecek yol (aşağıda ile yerel UI Katmanlar gösterilmiştir) temel bir Xamarin uygulamasının nasıl oluşturulacağını gösterir. Yerel UI ile paylaşılan kodun bir taşınabilir sınıf kitaplığı (PCL) yer alıyor ve ayrı bir platform projeleri kullanıcı Arabirimi tanımları içerir.

 ![Xamarin uygulaması, Android ve Windows Phone](../cross-platform/media/cross-plat-xamarin-build-1.png "çapraz-Plat Xamarin derleme 1")

 Derlemek için bu işlemleri yapmanız:

-   [Çözümünüzü ayarlama](#solution)

-   [Paylaşılan veri hizmeti kod yazma](#dataservice)

-   [Android için kullanıcı Arabirimi tasarımı](#Android)

-   [Windows Phone için kullanıcı Arabirimi tasarımı](#Windows)

-   [Sonraki adımlar](#next)

> [!TIP]
>  Bu proje için tam kaynak kodunu bulabilirsiniz [github'daki mobil-samples deposuna](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
>   Güçlük veya hatalarla karşılaşırsanız lütfen hakkında sorularınızı [forums.xamarin.com](http://forums.xamarin.com). Birçok hataları açıklanan olan en son SDK Xamarin tarafından gerekli güncelleştirerek çözülebilir [Xamarin sürüm notları](https://developer.xamarin.com/releases/) her platform için.
>
> [!NOTE]
>  Xamarin Geliştirici belgeleri, aşağıda listelenen birkaç izlenecek yollar hem hızlı başlangıç hem de yakından bölümleri ile de sunar. Tüm bu sayfalarda "Visual Studio" Visual Studio özel Kılavuzlar görmek için sağ üst köşede sayfanın seçili olduğundan emin olun.
>
> - Xamarin uygulamaları yerel UI ile:
>
>   -   [Hello, Android](https://developer.xamarin.com/guides/android/getting_started/hello,android/) (tek ekranlı basit uygulama)
>   -   [Hello, Android çoklu ekranı](https://developer.xamarin.com/guides/android/getting_started/hello,android_multiscreen/) (ekranlar arasında gezintiyi uygulamayla)
>   -   [Android parçaları izlenecek](http://developer.xamarin.com/guides/android/platform_features/fragments/fragments_walkthrough/) (diğer özelliklerin yanı sıra ana/ayrıntı ekranları için kullanılır)
>   -   [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
>   -   [Çok Ekranlı Hello, iOS ](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS_multiscreen/)
>   -   Xamarin.Forms (paylaşılan UI) ile Xamarin uygulamaları
>
>   -   [Hello, Xamarin.Forms](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms/quickstart/)
>   -   [Hello, Xamarin.Forms Multiscreen](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms-multiscreen/)

##  <a name="solution"></a> Çözümünüzü ayarlama
 Bu adımlar paylaşılan kod için bir PCL ve iki eklenen NuGet paketi içeren yerel UI ile bir Xamarin çözümü oluşturun.

1. Visual Studio'da yeni bir oluşturma **boş uygulama (yerel taşınabilir)** çözüm ve adlandırın **WeatherApp**. Girerek bu şablon en bir kolayca bulabilirsiniz **yerel taşınabilir** arama alanına.

    Yoksa, olabilir Xamarin'i yükleyin veya Visual Studio 2015 özelliğini etkinleştirmek için bkz: [Kurulum ve yükleme](../cross-platform/setup-and-install.md).

2. Çözümü oluşturmak için Tamam'a tıkladıktan sonra bir dizi ayrı projeler gerekir:

   - **WeatherApp (taşınabilir)**: Burada, dahil olmak üzere genel iş mantığı ve UI kodunu kullanarak Xamarin.Forms ile platformlar arasında paylaşılan kod yazma PCL.

   - **WeatherApp.Droid**: projenin yerel Android kodunu içerir. Bu, varsayılan başlangıç projesi olarak ayarlanır.

   - **WeatherApp.iOS**: yerel iOS kodu içeren bir proje.

   - **(Windows Phone 8.1) WeatherApp.WinPhone**: yerel Windows Phone kod içeren bir proje.

     Her yerel proje içinde karşılık gelen bir platform için yerel Tasarımcı erişimi vardır ve platform belirli ekranları uygulayabilirsiniz.

3. Ekleme **Newtonsoft.Json** ve hava durumu verileri hizmetten alınan bilgi işlem için kullanacağınız PCL projesine NuGet paketi:

   -   Sağ **çözüm 'WeatherApp'** Çözüm Gezgini seçip **çözüm için NuGet paketlerini Yönet...** .

        NuGet penceresinde **Gözat** sekmesinde ve arama **Newtonsoft**.

   -   Seçin **Newtonsoft.Json**.

   -   Pencerenin sağ tarafında denetleyin **WeatherApp** (Bu, gerektiği paketini yüklemek yalnızca proje) projesi.

   -   Olun **sürüm** ayarlanmış **en son kararlı** sürümü.

   -   **Yükle**'ye tıklatın.

   -   ![Bulma ve Newtonsoft.Json NuGet paketini yükleme](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

4. Bulmak ve yüklemek için 3. adımı yineleyin **Microsoft.Net.Http** paket.

5. Çözümünüzü oluşturun ve herhangi bir yapı hatası olmadığını doğrulayın.

##  <a name="dataservice"></a> Paylaşılan veri hizmeti kod yazma
 **WeatherApp (taşınabilir)** projedir burada tüm platformlar arasında paylaşılan taşınabilir sınıf kitaplığı (PCL) kod yazacaksınız. PCL otomatik olarak derlenmiş iOS, Android ve Windows Phone uygulama paketleri dahil edilir.

 Aşağıdaki adımlar bu durumda, hava durumu hizmetinden veri depolamak ve erişmek için PCL kodu ekleyin:

1.  Gereken önce kaydolmanız boş bir API anahtarı için bu örneği çalıştırmak için [ http://openweathermap.org/appid ](http://openweathermap.org/appid).

2.  Sağ **WeatherApp** seçin ve proje **Ekle > sınıfı...** . İçinde **Yeni Öğe Ekle** iletişim kutusunda, dosya adı **Weather.cs**. Bu sınıf, hava durumu verileri hizmetten alınan verileri depolamak için kullanacaksınız.

3.  Tüm içeriğini değiştirin **Weather.cs** aşağıdaki:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

4.  Başka bir sınıf adlı PCL projesine ekleyin **DataService.cs** içinde JSON verilerini işleme için hava durumu verileri hizmetten kullanacaksınız.

5.  Tüm içeriğini değiştirin **DataService.cs** aşağıdaki kod ile:

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

6.  Bir üçüncü sınıf adlı PCL ekleyin **çekirdek** bir posta kodu, bir sorgu dizesi forms mantıksal hava durumu verileri hizmet çağrıları ve örneğini doldurur gibi iş mantığını burada giriyorum paylaşılan **hava durumu**sınıfı.

7.  Öğesinin içeriğini değiştirin **Core.cs** aşağıdaki:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

8.  Değiştirin *burada bilgisayarınızı anahtarı* elde ettiğiniz API anahtarını içeren kodu (hala ihtiyaç tırnak içine) 1. adım.

9. Biz bunu Loaded MyClass.cs PCL içinde silin.

10. Derleme **WeatherApp** PCL projeye kodu doğru olduğundan emin olun.

##  <a name="Android"></a> Android için kullanıcı Arabirimi tasarımı
 Şimdi biz kullanıcı arabirimini tasarlayabileceğiniz paylaşılan kodunuza bağlayın ve sonra uygulamayı çalıştırın.

### <a name="design-the-look-and-feel-of-your-app"></a>Tasarım görünümü uygulama

1.  İçinde **Çözüm Gezgini**, genişletme **WeatherApp.Droid**>**kaynakları**>**Düzen** klasörü ve Açık **Main.axml**. Bu dosya Görsel tasarımcıda açılır. (Java ile ilgili bir hata varsa, bkz. Bu [blog gönderisi](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)

    > [!TIP]
    >  Projede diğer birçok dosyası vardır. Bunları keşfetmeye biraz daha fazla, bir Android projesi yapısına başlamak istiyorsanız ancak bu konunun kapsamı dışında olup [Kısım 2 yakından](http://developer.xamarin.com/guides/android/getting_started/hello,android/hello,android_deepdive/) xamarin.com üzerinde Hello Android konu.

2.  Seçip Tasarımcısı'nda görüntülenen varsayılan düğme silin.

3.  Araç kutusu açın **Görünüm > diğer Windows > Araç kutusu**.

4.  Gelen **araç kutusu**, sürükleyin bir **RelativeLayout** tasarımcıya denetim. Bu denetim, diğer denetimler için üst kapsayıcı olarak kullanacaksınız.

    > [!TIP]
    >  Herhangi bir zamanda düzenini düzgün görüntülenmesi yaramadı, dosyayı kaydedin ve arasında geçiş yapma **tasarım** ve **kaynak** yenilemek için sekmeler.

5.  İçinde **özellikleri** penceresinde **arka plan** (stil grubunda) özelliğine `#545454`.

6.  Gelen **araç kutusu**, sürükleyin bir **TextView** denetimi **RelativeLayout** denetimi.

7.  İçinde **özellikleri** bu Özellikler penceresinde ayarlayın (Not: alfabetik olarak sırala düğmesine Özellikler penceresi araç kullanarak sıralamak için yardımcı olabilir):

    |Özellik|Değer|
    |--------------|-----------|
    |**Metin**|**Posta kodu göre ara**|
    |**id**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginLeft**|`10dp`|
    |**textColor**|`@android:color/white`|
    |**metin stili**|`bold`|

    > [!TIP]
    >  Pek çok özellik seçebileceğiniz değerler, aşağı açılan listesini içermeyen dikkat edin.  Belirli bir özellik için kullanılacak dize değeri tahmin etmek zor olabilir. Öneriler için bir özelliğin adını aramayı deneyin [R.attr](http://developer.android.com/reference/android/R.attr.html) sınıfı sayfası.
    >
    >  Ayrıca, hızlı web arama genellikle bir sayfaya müşteri adayları [ http://stackoverflow.com/ ](http://stackoverflow.com/) başkalarının kullanıldığı aynı özellik.

     Geçiş yaparsanız, başvuru için **kaynak** görünümü, bu öğe için şu kodu görürsünüz:

    ```xml
    <TextView
        android:text="Search by Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/ZipCodeSearchLabel"
        android:layout_centerVertical="true"
        android:layout_marginLeft="10dp"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    ```

8.  Gelen **araç kutusu**, sürükleyin bir **TextView** denetimi **RelativeLayout** denetlemek ve ZipCodeSearchLabel denetimi yerleştirin. Bunun için yeni denetimi varolan bir denetimi uygun kenarında bırakarak; Bunun için biraz tasarımcıda yakınlaştırmak için yardımcı olur.

9. İçinde **özellikleri** penceresinde bu özellikleri ayarlayın:

    |Özellik|Değer|
    |--------------|-----------|
    |**Metin**|**Posta Kodu**|
    |**id**|`@+id/ZipCodeLabel`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginTop**|`5dp`|

     Kodda **kaynak** görünümü, şu şekilde görünmelidir:

    ```xml
    <TextView
        android:text="Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeSearchLabel"
        android:id="@+id/ZipCodeLabel"
        android:layout_marginTop="5dp"
        android:layout_marginLeft="10dp" />
    ```

10. Gelen **araç kutusu**, sürükleyin bir **numarası** denetimi **RelativeLayout**, aşağıdaki konumlandırın **posta kodu** etiketi. Ardından aşağıdaki özellikleri ayarlayın:

    |Özellik|Değer|
    |--------------|-----------|
    |**id**|`@+id/zipCodeEntry`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**Genişlik**|`165dp`|

     Kodu yeniden:

    ```xml
    <EditText
        android:inputType="number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeLabel"
        android:id="@+id/zipCodeEntry"
        android:layout_marginLeft="10dp"
        android:layout_marginBottom="10dp"
        android:width="165dp" />
    ```

11. Gelen **araç kutusu**, sürükleyin bir **düğmesi** üzerine **RelativeLayout** denetlemek ve zipCodeEntry denetimi sağa konumlandırın. Bu özellikleri ayarlayın:

    |Özellik|Değer|
    |--------------|-----------|
    |**id**|`@+id/weatherBtn`|
    |**Metin**|**Hava durumunu alın**|
    |**layout_marginLeft**|`20dp`|
    |**layout_alignBottom**|`@id/zipCodeEntry`|
    |**Genişlik**|`165dp`|

    ```xml
    <Button    android:text="Get Weather"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/zipCodeEntry"
        android:id="@+id/weatherBtn"
        android:layout_marginLeft="20dp"
        android:layout_alignBottom="@id/zipCodeEntry"
        android:width="165dp" />
    ```

12. Artık Android designer kullanarak temel bir kullanıcı Arabirimi oluşturmak için yeterli bir deneyimi vardır. Biçimlendirme doğrudan sayfanın .asxml dosyasına ekleyerek, bir kullanıcı Arabirimi de oluşturabilirsiniz. Bu şekilde kullanıcı arabiriminin geri kalan oluşturmak için kaynağı görünümü Tasarımcısı'nı ve ardından aşağıdaki biçimlendirme geçmiş geçin *altındaki* `</RelativeLayout>` etiketi (etiketi altında... Bu Evet, bu öğeleri olmayan ReleativeLayout içinde yer alan).

    ```xml
    <TextView
            android:text="Location"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationLabel"
            android:layout_marginLeft="10dp"
            android:layout_marginTop="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationText"
            android:layout_marginLeft="20dp"
            android:layout_marginBottom="10dp" />
        <TextView
            android:text="Temperature"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Wind Speed"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Humidity"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidtyLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Visibility"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunrise"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunset"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />

    ```

13. Dosyayı kaydedin ve geçiş **tasarım** görünümü. Kullanıcı Arabirimi aşağıdaki gibi görünmelidir:

     ![Android uygulaması için kullanıcı Arabirimi](../cross-platform/media/xamarin-androidui.png "Xamarin_AndroidUI")

14. Açık **MainActivity.cs** ve satırları Sil *OnCreate* daha önce kaldırılan varsayılan düğme başvuran yöntemi. İşiniz bittiğinde, kod şu şekilde görünmelidir:

    ```
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

15. İş kontrol etmek için Android projesi oluşturun. Yapı ekler Not denetlemek için kimlikleri **Resource.Designer.cs** kod ada göre denetimlere başvurabilmeniz için dosya.

### <a name="consume-your-shared-code"></a>Paylaşılan kod kullanma

1.  Açık **MainActivity.cs** dosya **WeatherApp** Kod Düzenleyicisi'nde proje ve içeriğini aşağıdaki kodla değiştirin. Bu kod `GetWeather` paylaşılan kodunuzda tanımlanan yöntemi. Ardından kullanıcı Arabiriminde uygulamanın Bu yöntemden alınan verileri gösterir.

    ```csharp
    using System;
    using Android.App;
    using Android.Widget;
    using Android.OS;

    namespace WeatherApp.Droid
    {
        [Activity(Label = "Sample Weather App", MainLauncher = true, Icon = "@drawable/icon")]
        public class MainActivity : Activity
        {
            protected override void OnCreate(Bundle bundle)
            {
                base.OnCreate(bundle);

                SetContentView(Resource.Layout.Main);

                Button button = FindViewById<Button>(Resource.Id.weatherBtn);

                button.Click += Button_Click;
            }

            private async void Button_Click(object sender, EventArgs e)
            {
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);

                if (!String.IsNullOrEmpty(zipCodeEntry.Text))
                {
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;
                }
            }
        }
    }
    ```

### <a name="run-the-app-and-see-how-it-looks"></a>Uygulamayı çalıştırın ve nasıl göründüğüne bakın

1.  İçinde **Çözüm Gezgini**, emin **WeatherApp.Droid** projeyi başlangıç projesi olarak ayarlayın.

2.  Bir uygun cihaz veya öykünücü hedef seçin ve ardından F5 tuşuna basarak uygulamayı başlatın.

3.  Cihazda veya öykünücüde düzenleme kutusuna geçerli bir Amerika Birleşik Devletleri posta kodu yazın (örneğin: 60601) ve basın **hava durumunu alın**. Bu bölge için hava durumu verileri, ardından denetimleri görünür.

     ![Android ve Windows Phone için hava durumu uygulaması](../cross-platform/media/xamarin-getstarted-results.png "Xamarin_GetStarted_Results")

> [!TIP]
>  Bu proje için tam kaynak kodu [github'daki mobil-samples deposuna](https://github.com/xamarin/mobile-samples/tree/master/Weather).

##  <a name="Windows"></a> Windows Phone için kullanıcı Arabirimi tasarımı
 Şimdi biz Windows Phone için kullanıcı arabirimini tasarlayabileceğiniz paylaşılan kodunuza bağlayın ve sonra uygulamayı çalıştırın.

### <a name="design-the-look-and-feel-of-your-app"></a>Tasarım görünümü uygulama
 Yerel Windows Phone kullanıcı Arabiriminde bir Xamarin uygulaması tasarlama işlemi herhangi diğer yerel Windows Phone uygulamasından farklı değildir. Bu nedenle, biz ayrıntıları tasarımcıyı nasıl kullanacağınızı, burada gitmiyor. Bunun için başvurmak [XAML Tasarımcısını kullanarak kullanıcı Arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 Bunun yerine, basitçe mainpage.XAML dosyasını açın ve tüm XAML kodu aşağıdakiyle değiştirin:

```xaml
<Page
    x:Class="WeatherApp.WinPhone.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.WinPhone"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

    <Grid>
        <StackPanel HorizontalAlignment="Left" Height="40" Margin="10,0,0,0" VerticalAlignment="Top" Width="400">
            <TextBlock x:Name="pageTitle" Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left" Height="120" Margin="10,40,0,0" VerticalAlignment="Top" Width="400" Background="#FF545454">

            <TextBlock x:Name="zipCodeSearchLabel" TextWrapping="Wrap" Text="Search by Zip Code" FontSize="18" FontWeight="Bold" HorizontalAlignment="Left" Margin="10,10,0,0"/>
            <TextBlock x:Name="zipCodeLabel" TextWrapping="Wrap" Text="Zip Code" Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>
            <StackPanel Orientation="Horizontal">
                <TextBox x:Name="zipCodeEntry" Margin="10,10,0,0" Text="" VerticalAlignment="Top" InputScope="Number" Width="165" />
                <Button x:Name="weatherBtn" Content="Get Weather" Width="165" Margin="20,0,0,0" Height="60" Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>
        <StackPanel Margin="10,175,0,0">
            <TextBlock x:Name="locationLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Location" VerticalAlignment="Top"/>
            <TextBlock x:Name="locationText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="windLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Wind Speed" VerticalAlignment="Top"/>
            <TextBlock x:Name="windText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Humidity" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunriweatherse" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunset" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
        </StackPanel>
    </Grid>
</Page>
```

 Tasarım görünümünde, kullanıcı Arabirimi aşağıdaki gibi görünmelidir:

 ![Windows Phone Uygulama UI](../cross-platform/media/xamarin-winphone-finalui.png "Xamarin_WinPhone_FinalUI")

### <a name="consume-your-shared-code"></a>Paylaşılan kod kullanma

1.  Tasarımcıda seçin **hava durumunu alın** düğmesi.

2.  İçinde **özellikleri** penceresinde olay işleyicisi düğmesini seçin (![Visual Studio olay işleyicileri simgesi](../cross-platform/media/blend-vs-eventhandlers-icon.png "blend_VS_EventHandlers_icon")).

     Bu simge üst köşesinde görünür **özellikleri** penceresi.

3.  Yanındaki **tıklayın** olay, türü **GetWeatherButton_Click**ve ardından ENTER tuşuna basın.

     Bu adlı bir olay işleyicisi oluşturur. `GetWeatherButton_Click`. Kod Düzenleyicisi açılır ve imlecinizi olay işleyicisine kod bloğunun içine yerleştirir.  Not: düzenleyicide ENTER tuşuna basıldığında açık değilse, yalnızca olay adına çift tıklayın.

4.  Bu olay işleyicisi aşağıdaki kodla değiştirin.

    ```csharp
    private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)
    {
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))
        {
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);
            locationText.Text = weather.Title;
            tempText.Text = weather.Temperature;
            windText.Text = weather.Wind;
            visibilityText.Text = weather.Visibility;
            humidityText.Text = weather.Humidity;
            sunriseText.Text = weather.Sunrise;
            sunsetText.Text = weather.Sunset;

            weatherBtn.Content = "Search Again";
        }
    }
    ```

     Bu kod `GetWeather` paylaşılan kodunuzda tanımlanan yöntemi. Bu Android uygulamanızda çağrılan yöntem ile aynıdır. Bu kod Ayrıca, uygulamanızın kullanıcı Arabirimi denetimleri yönteminde alınan verileri gösterir.

5.  İçindeki tüm kodu açık olan MainPage.xaml.cs dosyasında Sil **OnNavigatedTo** yöntemi. Bu kod, sadece biz MainPage.xaml içeriği değiştirildiğinde kaldırılan varsayılan düğme işlenir.

### <a name="run-the-app-and-see-how-it-looks"></a>Uygulamayı çalıştırın ve nasıl göründüğüne bakın

1.  İçinde **Çözüm Gezgini**ayarlayın **WeatherApp.WinPhone** projeyi başlangıç projesi olarak.

2.  F5 tuşuna basarak uygulamayı başlatın.

3.  Windows Phone öykünücüsü'nde geçerli bir Amerika Birleşik Devletleri posta kodu düzenleme kutusuna yazın (örneğin: 60601) ve basın **hava durumunu alın**. Bu bölge için hava durumu verileri, ardından denetimleri görünür.

     ![Windows sürümü çalışan uygulamanın](../cross-platform/media/xamarin-getstarted-results-windows.png "Xamarin_GetStarted_Results_Windows")

> [!TIP]
>  Bu proje için tam kaynak kodu [github'daki mobil-samples deposuna](https://github.com/xamarin/mobile-samples/tree/master/Weather).

##  <a name="next"></a> Sonraki adımlar
 **Kullanıcı Arabirimi, iOS için çözüme ekleyin.**

 Bu örnek, iOS için yerel UI ekleyerek genişletin. Bunun için yerel ağınızda Xcode sahip bir mac'e bağlanmanız gerekir ve Xamarin yüklü. Bunu yaptığınızda, doğrudan Visual Studio'da iOS Tasarımcısı'nı kullanabilirsiniz. Bkz: [github'daki mobil-samples deposuna](https://github.com/xamarin/mobile-samples/tree/master/Weather) tamamlanan uygulama için.

 Ayrıca bkz [Hello, iOS](http://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/hello,iOS_quickstart/) (xamarin.com) Gözden geçirme. Yönerge kümesini doğru görünür, bu sayfada emin "Visual Studio" Not sağ üst köşesinde sayfaları xamarin.com üzerinde seçilir.

 **Paylaşılan projede platforma özgü kod ekleyin**

 PCL kez derlenir ve her platforma özgü uygulama paketinde bir PCL paylaşılan kodu platformdan bağımsız olmasıdır. Koşullu derleme platforma özgü kod yalıtmak için kullandığı paylaşılan kod yazmak istiyorsanız, kullanabileceğiniz bir *paylaşılan* proje. Daha fazla ayrıntı için [ode paylaşım seçeneklerini](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (xamarin.com).

## <a name="see-also"></a>Ayrıca Bkz.
 [Xamarin Geliştirici sitesinde](http://developer.xamarin.com/) [Windows Dev Center](https://dev.windows.com/en-us) [Swift ve C# hızlı başvuru posteri](http://aka.ms/scposter)
