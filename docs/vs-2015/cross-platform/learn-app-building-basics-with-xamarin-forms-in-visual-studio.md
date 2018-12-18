---
title: Xamarin.Forms ile uygulama oluşturmaya yönelik temel bilgileri öğrenin
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 0cbc20bd714cabf9747145c114abfaa58a2e52a6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058330"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Visual Studio'da Xamarin.Forms ile uygulama oluşturmaya yönelik temel bilgileri öğrenin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Adımları yaptıktan sonra [Kurulum ve yükleme](../cross-platform/setup-and-install.md) ve [Xamarin ortamınızı doğrulama](../cross-platform/verify-your-xamarin-environment.md), bu izlenecek yol (aşağıda Xamarin.Forms ile gösterilen) bir temel uygulamasının nasıl oluşturulacağını gösterir. Xamarin.Forms ile UI kodunuzun tamamını kez taşınabilir sınıf kitaplığı (PCL) yazmanız. Xamarin sonra otomatik olarak işleme iOS, Android ve Windows için yerel kullanıcı Arabirimi denetimleri platformlar. Bu yaklaşım yalnızca bu .NET tüm hedef platformlar arasında desteklenen API'lerini kullanarak en iyi PCL seçeneğini desteklediği için önerilir ve Xamarin.Forms izin verdiğinden platformlar arasında UI kod paylaşın.

 ![Android, iOS ve Windows Phone hava durumu uygulaması örneği](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

 Derlemek için bu işlemleri yapmanız:

-   [Çözümünüzü ayarlama](#solution)

-   [Paylaşılan veri hizmeti kod yazma](#dataservice)

-   [Paylaşılan kullanıcı Arabirimi kod yazmaya başlayın](#uicode)

-   [Android için Visual Studio öykünücüsü'nü kullanarak uygulamanızı test edin](#test)

-   [Yerel bir görünüme kullanıcı Arabirimiyle platformlar arasında son](#finish)

> [!TIP]
>  Bu proje için tam kaynak kodunu bulabilirsiniz [xamarin forms örnekleri GitHub deposunda](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

##  <a name="solution"></a> Çözümünüzü ayarlama
 Bu adımlar paylaşılan kod için bir PCL ve iki eklenen NuGet paketlerini içeren bir Xamarin.Forms çözümü oluşturun.

1.  Visual Studio'da yeni bir oluşturma **boş uygulama (Xamarin.Forms taşınabilir)** çözüm ve adlandırın **WeatherApp**. Girerek bu şablon en bir kolayca bulabilirsiniz **Xamarin.Forms** arama alanına.

     Yoksa, olabilir Xamarin'i yükleyin veya Visual Studio 2015 özelliğini etkinleştirmek için bkz: [Kurulum ve yükleme](../cross-platform/setup-and-install.md).

     ![Yeni bir boş uygulama oluşturma &#40;Xamarin.Forms taşınabilir&#41; proje](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  Çözümü oluşturmak için Tamam'a tıkladıktan sonra bir dizi ayrı projeler gerekir:

    -   **WeatherApp (taşınabilir)**: Burada, dahil olmak üzere genel iş mantığı ve UI kodunu kullanarak Xamarin.Forms ile platformlar arasında paylaşılan kod yazma PCL.

    -   **WeatherApp.Droid**: projenin yerel Android kodunu içerir. Bu, varsayılan başlangıç projesi olarak ayarlanır.

    -   **WeatherApp.iOS**: yerel iOS kodu içeren bir proje.

    -   **WeatherApp.UWP**: Windows 10 UWP kodu içeren bir proje.

    -   **(Windows 8.1) WeatherApp.Windows**: yerel Windows 8.1 kod içeren bir proje.

    -   **(Windows Phone 8.1) WeatherApp.WinPhone**: yerel Windows Phone kod içeren bir proje.

    > [!NOTE]
    >  Projelerin değil hedeflediğiniz platform için silmek boş. Bu izlenecek yolda amacı doğrultusunda, biz Android, iOS ve Windows Phone 8.1 projeleri başvuran. UWP ve Windows 8.1 ile çalışma projeleri Windows Phone 8.1 projesiyle çalışmaya çok benzer.

     Her yerel proje içinde karşılık gelen bir platform için yerel Tasarımcı erişimi vardır ve platform belirli ekranları ve gerektiğinde işlevi uygulayabilirsiniz.

3.  Çözümünüzdeki Xamarin.Forms NuGet paketi gibi en son kararlı sürüme yükseltin. Yeni bir Xamarin çözümü oluşturduğunuzda bunu öneririz:

    -   Seçin **Araçlar > NuGet Paket Yöneticisi > çözüm için NuGet paketlerini Yönet**.

    -   Altında **güncelleştirmeleri** sekmesinde, onay **Xamarin.Forms** güncelleştirin ve çözümünüzdeki tüm projeleri güncelleştir denetleyin. (Not: tüm güncelleştirmeler için Xamarin.Android.Support işaretlemeden bırakın.)

    -   Güncelleştirme **sürüm** alanı **en son kararlı** kullanılabilir olan sürümü.

    -   Tıklayın **güncelleştirme**.

         ![Xamarin.Forms NuGet paketi güncelleştirme](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

4.  Ekleme **Newtonsoft.Json** ve hava durumu verileri hizmetten alınan bilgi işlem için kullanacağınız PCL projesine NuGet paketi:

    -   NuGet Paket Yöneticisi'nde (3. adımdaki hala açık) **Gözat** sekmesinde ve arama **Newtonsoft**.

    -   Seçin **Newtonsoft.Json**.

    -   Denetleme **WeatherApp** (Bu, gerektiği paketini yüklemek yalnızca proje) projesi.

    -   Olun **sürüm** ayarlanmış **en son kararlı** sürümü.

    -   **Yükle**'ye tıklatın.

    -   ![Bulma ve Newtonsoft.Json NuGet paketini yükleme](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

5.  Bulmak ve yüklemek için 4. adımı yineleyin **Microsoft.Net.Http** paket.

6.  Çözümünüzü oluşturun ve herhangi bir yapı hatası olmadığını doğrulayın.

##  <a name="dataservice"></a> Paylaşılan veri hizmeti kod yazma
 **WeatherApp (taşınabilir)** projedir burada tüm platformlar arasında paylaşılan taşınabilir sınıf kitaplığı (PCL) kod yazacaksınız. PCL otomatik olarak uygulamaya dahil edilen paketleri iOS, Android ve Windows Phone projeleri oluşturun.

 Gereken önce kaydolmanız boş bir API anahtarı için bu örneği çalıştırmak için [ http://openweathermap.org/appid ](http://openweathermap.org/appid).

 Aşağıdaki adımlar bu durumda, hava durumu hizmetinden veri depolamak ve erişmek için PCL kodu ekleyin:

1.  Sağ **WeatherApp** seçin ve proje **Ekle > sınıfı...** . İçinde **Yeni Öğe Ekle** iletişim kutusunda, dosya adı **Weather.cs**. Bu sınıf, hava durumu verileri hizmetten alınan verileri depolamak için kullanacaksınız.

2.  Tüm içeriğini değiştirin **Weather.cs** aşağıdaki:

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

3.  Başka bir sınıf adlı PCL projesine ekleyin **DataService.cs** içinde JSON verilerini işleme için hava durumu verileri hizmetten kullanacaksınız.

4.  Tüm içeriğini değiştirin **DataService.cs** aşağıdaki kod ile:

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

5.  Bir üçüncü sınıf adlı PCL ekleyin **çekirdek** bir posta kodu, bir sorgu dizesi forms mantıksal hava durumu verileri hizmet çağrıları ve örneğini doldurur gibi iş mantığını burada giriyorum paylaşılan **hava durumu**sınıfı.

6.  Öğesinin içeriğini değiştirin **Core.cs** aşağıdaki:

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

7.  Derleme **WeatherApp** PCL projeye kodu doğru olduğundan emin olun.

##  <a name="uicode"></a> Paylaşılan kullanıcı Arabirimi kod yazmaya başlayın
 Xamarin.Forms PCL'de paylaşılan kullanıcı Arabirimi kodunu uygulamak olanak tanır. Bu adımlarda PCL ile hizmet yazısının verilerle hava durumu verilerini tarafından döndürülen güncelleştirmeleri önceki bölümde eklediğiniz kodun bir düğme için bir ekran ekleyeceksiniz:

1.  Ekle bir **form Xaml sayfası** adlı **WeatherPage.cs** sağ tıklanarak **WeatherApp** proje ve seçerek **Ekle > Yeni öğe...** . İçinde **Yeni Öğe Ekle** iletişim kutusunda arama formlarında"," select **form Xaml sayfası**ve adlandırın **WeatherPage.cs**.

     Xamarin.Forms XAML tabanlı, bu adımı oluşturur bir **WeatherPage.xaml** dosya iç içe geçmiş arka plan kod dosyası ile birlikte **WeatherPage.xaml.cs**. Bu, kullanıcı Arabirimi XAML veya kod aracılığıyla oluşturmanıza olanak sağlar. Bu kılavuzda hem de bazı yaparsınız.

     ![Yeni bir Xamarin.Forms XAML sayfası ekleme](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

2.  WeatherPage ekranına bir düğme eklemek için WeatherPage.xaml içeriğini aşağıdakiyle değiştirin:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
    </ContentPage>
    ```

     Düğmenin adı kullanılarak tanımlanmalıdır fark **x: Name** bu düğme, arka plan kod dosyasında adıyla başvurabilir, böylece öznitelik.

3.  Düğme için bir olay işleyicisi eklemek için **tıklama** düğme metnini güncelleştirme içeriğini değiştirmek için olay **WeatherPage.xaml.cs** aşağıdaki kod ile. ("60601" değiştirmek için başka bir posta kodu çekinmeyin.)

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();
                this.Title = "Sample Weather App";
                getWeatherBtn.Clicked += GetWeatherBtn_Clicked;

                //Set the default binding to a default object for now
                this.BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4.  Açmak için **WeatherPage** uygulaması başlatıldığında ilk ekran varsayılan oluşturucu değiştirin **App.cs** aşağıdaki kod ile:

    ```csharp
    public App()
    {
        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5.  Kodu doğru olduğundan emin olmak için WeatherApp PCL projeyi derleyin.

##  <a name="test"></a> Android için Visual Studio öykünücüsü'nü kullanarak uygulamanızı test edin
 Uygulamayı çalıştırmak artık hazırsınız! Uygulama hava durumu hizmetinden veri alma doğrulamak şimdilik yalnızca Android sürümü çalıştıralım. Daha sonra daha fazla kullanıcı Arabirimi öğeleri ekledikten sonra da iOS ve Windows Phone sürümlerinde çalıştıracaksınız. (Not: Windows 7'de Visual Studio kullanıyorsanız, aynı adımları ancak bunun yerine Xamarin Player olur.)

1.  Ayarlama **WeatherApp.Droid** tıklayıp seçerek başlangıç projesi olarak proje **başlangıç projesi olarak ayarla**.

2.  Visual Studio araç çubuğunda, gördüğünüz **WeatherApp.Droid** hedef projesi olarak listelenir. Hata ayıklama için Android öykünücüleri birini seçin ve isabet **F5**. Aşağıdakilerden birini kullanmanızı öneririz **VS Öykünücüsünden** Android seçenekleri için Visual Studio öykünücüsü'nde uygulama çalıştırılır seçenekleri.

     ![VS Öykünücüsünden hata ayıklama hedef seçme](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

3.  Uygulamayı öykünücüde başlattığında tıklayın **hava durumunu alın** düğmesi. Düğmenin metni için güncelleştirilen görmelisiniz **Chicago, IL**, olduğu *başlık* verileri özelliği hava durumu hizmetinden alınan.

     ![Önce ve sonra bir düğmeye dokunarak uygulama hava durumu](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

##  <a name="finish"></a> Yerel bir görünüme kullanıcı Arabirimiyle platformlar arasında son
 Uygulamanızı otomatik olarak yerel bir görünümüne sahip olacak şekilde Xamarin.Forms her platform için yerel kullanıcı Arabirimi denetimleri oluşturur. Bunu görmek için daha net bir şekilde, bir posta kodu için giriş alanını kullanıcı Arabirimiyle şimdi son ve ardından hizmetten döndürülen hava durumu verilerini görüntüleyebilirsiniz.

1. Öğesinin içeriğini değiştirin **WeatherPage.xaml** aşağıdaki kod ile. Kullanarak, her öğe adlandırdığınız Not **x: Name** öznitelik öğe koddan başvurulabilir, böylece daha önce açıklandığı gibi. Xamarin.Forms da çok sayıda sunar [düzen seçeneklerini](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com); burada WeatherPage kullanıyor [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com).

   ```xaml
   <?xml version="1.0" encoding="utf-8" ?>
   <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
          xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
          x:Class="WeatherApp.WeatherPage">

     <ContentPage.Resources>
       <ResourceDictionary>
         <Style x:Key="labelStyle" TargetType="Label">
           <Setter Property="TextColor" Value="#a8a8a8" />
           <Setter Property="FontSize" Value="Small" />
         </Style>
         <Style x:Key="fieldStyle" TargetType="Label">
           <Setter Property="TextColor">
             <OnPlatform x:TypeArguments="Color" iOS="Black" Android="White" WinPhone="White" />
           </Setter>
           <Setter Property="FontSize" Value="Medium" />
         </Style>
         <Style x:Key="fieldView" TargetType="ContentView">
           <Setter Property="Padding" Value="10,0,0,0" />
         </Style>
       </ResourceDictionary>
     </ContentPage.Resources>

     <ContentPage.Content>
       <ScrollView>
         <StackLayout>
           <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand"
                 BackgroundColor="#545454">
             <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
               <Label Text="Search by Zip Code" TextColor="White" FontAttributes="Bold"
                   FontSize="Medium" />
               <Label x:Name="zipCodeLabel" Text="Zip Code" Style="{StaticResource labelStyle}" />
               <Entry x:Name="zipCodeEntry" />
             </StackLayout>
             <StackLayout Padding="0,0,0,10" VerticalOptions="End">
               <Button x:Name="getWeatherBtn" Text="Get Weather" WidthRequest="185" BorderWidth="1" >
                 <!-- Set iOS colors; use defaults on other platforms -->
                 <Button.TextColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.TextColor>
                 <Button.BorderColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.BorderColor>
               </Button>
             </StackLayout>
           </StackLayout>
           <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
             <Label Text="Location" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Temperature" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="tempLabel" Text="{Binding Temperature}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="windLabel" Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Humidity" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="humidityLabel" Text="{Binding Humidity}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Visibility" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="visibilitylabel" Text="{Binding Visibility}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunriseLabel" Text="{Binding Sunrise}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunsetLabel" Text="{Binding Sunset}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
           </StackLayout>
         </StackLayout>
       </ScrollView>
     </ContentPage.Content>
   </ContentPage>
   ```

    Kullanımına dikkat edin **OnPlatform** Xamarin.Forms etiketi. **OnPlatform** uygulamanın üzerinde çalıştığı geçerli platforma özgü bir özellik değeri seçer (bkz [dış XAML söz dizimi](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) (xamarin.com). Buraya bir veri alanları farklı metin rengini ayarlamak için kullanıyoruz: Android ve Windows Phone, iOS siyah beyaz. Kullanabileceğiniz **OnPlatform** özeliklerini ve tüm veri türleri, XAML içinde herhangi bir platforma özgü ayarlamaları yapmak için. Arka plan kod dosyasında kullanabileceğiniz [Device.OnPlatform API](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) aynı amaçla.

2. İçinde **WeatherPage.xaml.cs**, değiştirin **GetWeatherBtn_Clicked** aşağıdaki kod ile olay işleyicisi. Bu kod, girişi alanında bir posta kodu, posta kodu için verileri alır, sonuçta elde edilen hava durumu örneği için tam ekran bağlama bağlamı ayarlar ve ardından "Tekrar arama." düğme metnini ayarlar doğrular. Kullanıcı arabiriminde her etiket bir özelliğe hava durumu sınıfının şekilde ne zaman bağlar, Not ekranın bağlama bağlamını ayarlamak bir **hava durumu** etiketlerin örneği, güncelleştirme otomatik olarak.

   ```csharp
   private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
   {
       if (!String.IsNullOrEmpty(zipCodeEntry.Text))
       {
           Weather weather = await Core.GetWeather(zipCodeEntry.Text);
           this.BindingContext = weather;
           getWeatherBtn.Text = "Search Again";
       }
   }
   ```

3. Uygulamayı üç tüm platformlarda çalıştırın; Android, iOS ve Windows Phone — uygun projeye sağ, başlangıç projesi olarak Ayarla'i seçerek ve uygulamayı bir cihaz veya öykünücü veya benzetici başlatılıyor. Geçerli bir Amerika Birleşik Devletleri posta kodu (örneğin, 60601) girin ve aşağıda gösterildiği gibi bu bölge için hava durumu verileri görüntülemek için hava durumu Al düğmesine basın. Elbette, Visual Studio iOS projesi için ağınızdaki bir Mac OS X bilgisayara bağlı olması gerekir.

    ![Android, iOS ve Windows Phone hava durumu uygulaması örneği](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

   Bu proje için tam kaynak kodu [xamarin forms örnekleri GitHub deposunda](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).
