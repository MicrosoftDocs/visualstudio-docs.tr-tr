---
title: Bir Windows Evrensel uygulaması CPU kullanımını analiz etme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 11e8587176ecc452f8f97132d296cff93b09b5ac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741293"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Bir Windows Evrensel uygulaması CPU kullanımını analiz etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Uygulamanızdaki performans sorunlarını araştırmak gerektiğinde başlatmak için iyi bir yerdir, CPU kullanma anlamaktır. **CPU kullanımı** aracı gösterir, burada CPU kodu yürütürken zaman harcadığı yerleri. Belirli senaryolara odaklanmak için CPU kullanımı ile çalıştırılabilir [XAML UI yanıtlama hızı](http://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480) aracı [enerji tüketimi](../profiling/analyze-energy-use-in-store-apps.md) aracı veya tanılama tek bir oturumda hem araçları.  
  
> [!NOTE]
>  **CPU kullanımı** aracı, Windows Phone Silverlight 8.1 uygulamaları ile kullanılamaz.  
  
 Bu izlenecek yol, toplama ve basit bir Windows Evrensel XAML uygulaması için CPU kullanımını analiz etme üzerinden alır.  
  
##  <a name="BKMK_Create_the_CpuUseDemo_project"></a> CpuUseDemo projesi oluşturma  
 **CpuUseDemo** CPU kullanımı verileri toplayıp Analiz işlemini göstermek için oluşturulmuş bir uygulamadır. Düğmeleri, en yüksek değer birden fazla işlev çağrıları seçer bir yöntemi çağırarak bir sayı oluşturur. Çağrılan işlev, rastgele bir değer çok büyük bir sayı oluşturur ve sonra sonuncu döndürür. Veriler, bir metin kutusunda görüntülenir.  
  
1.  Adlı yeni bir C# Windows Evrensel uygulama projesi oluşturma **CpuUseDemo** kullanarak **BlankApp** şablonu.  
  
     ![CpuUseDemoProject oluşturma](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2.  MainPage.xaml ile değiştirin [bu kodu](#BKMK_MainPage_xaml).  
  
3.  MainPage.xaml.cs ile değiştirin [bu kodu](#BKMK_MainPage_xaml_cs).  
  
4.  Uygulamayı oluşturun ve deneyin. Uygulama, bazı genel örnekleri CPU kullanım verileri analiz göstermek basit bir işlemdir.  
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> CPU kullanım verileri toplama  
 ![Uygulamanın bir yayın derlemesinin simulator'da çalıştırmak](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1. Visual Studio'da dağıtım hedefini ayarlamak **simülatör** ve çözüm yapılandırması için **yayın**.  
  
   -   Uygulama simülatörde çalıştırılan uygulama ve Visual Studio IDE arasında kolayca geçiş olanak tanır.  
  
   -   Bu uygulamayı çalışır durumda **yayın** modu gerçek uygulamanızın performansını daha iyi bir görünümünü sağlar.  
  
2. Üzerinde **hata ayıklama** menüsünde seçin **performans Profiler...** .  
  
3. Performans ve tanılama hub'ı seçin **CPU kullanımı** seçip **Başlat**.  
  
    ![CpuUsage Tanılama oturumu başlatmak](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4. Uygulama başlatıldığında tıklayın **alma sınırı**. Çıkış görüntülendikten sonra ikinci bir bekleyin ve ardından **alma en fazla sayı Async**. Düğme tıklamaları yapar bekleyen düğme yalıtmak daha kolay tıklayın tanılama raporu yordamları.  
  
5. İkinci çıktı satırı göründükten sonra seçin **toplamasını Durdur** performans ve tanılama hub'ında.  
  
   ![CpuUsage veri toplamayı Durdur](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   CPU kullanımı aracı verileri çözümler ve rapor görüntüler.  
  
   ![CpuUsage rapor](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
##  <a name="BKMK_Analyze_the_CPU_Usage_report"></a> CPU kullanımı raporunu analiz etme  
  
###  <a name="BKMK_CPU_utilization_timeline_graph"></a> CPU kullanım zaman çizelgesi grafiği  
 ![CpuUtilization &#40;%&#41; zaman çizelgesi grafiği](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 CPU kullanım grafiği, cihazda uygulama tüm işlemci çekirdeği gelen tüm CPU süresi yüzdesi olarak CPU etkinliği gösterir. Bu rapor verileri, bir çift çekirdekli makine üzerinde toplanmadı. İki büyük depoları iki düğme tıklamaları CPU etkinliği temsil eder. `GetMaxNumberButton_Click` Böylece yöntemin grafik yüksekliği hiçbir zaman % 50 aştığını mantıklı eş zamanlı olarak tek bir çekirdek üzerinde gerçekleştirir. `GetMaxNumberAsycButton_Click` zaman uyumsuz olarak bunu yeniden sağ, görünüyor için kendi depo tüm iki çekirdek CPU kaynakları kullanarak daha yakından alır, böylece her iki Çekirdekte çalıştırır.  
  
####  <a name="BKMK_Select_timeline_segments_to_view_details"></a> Ayrıntılarını görüntülemek için zaman çizelgesi Segment seçin  
 Seçim çubuklarını kullanın **Tanılama oturumu** GetMaxNumberButton_Click verilere odaklanmak için zaman çizelgesi:  
  
 ![GetMaxNumberButton&#95;seçili tıklatın](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 **Tanılama oturumu** zaman çizelgesi artık seçili Segmentte (bit 2 saniyeden fazla Bu raporda) için harcanan süreyi görüntüler ve seçimdeki çalışan bu yöntemlere yapılan çağrı ağacını filtreler.  
  
 Şimdi seçtiğiniz `GetMaxNumberAsyncButton_Click` kesimi.  
  
 ![GetMaxNumberAsyncButton&#95;tıklayın rapor seçim](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Bu yöntem hakkında ikinci tamamlandıktan daha hızlı bir şekilde `GetMaxNumberButton_Click`, ancak çağrı ağacı girişleri anlamını daha az belirgin.  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> CPU kullanımı çağrı ağacı  
 Çağrı ağacı bilgileri anlama kullanmaya başlamak için yeniden `GetMaxNumberButton_Click` segmentlere ayırın ve çağrı ağacı ayrıntılarını inceleyin.  
  
####  <a name="BKMK_Call_tree_structure"></a> Çağrı ağacı yapısı  
 ![GetMaxNumberButton&#95;tıklayın çağrı ağacı](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![1. adım](../profiling/media/procguid-1.png "ProcGuid_1")|CPU kullanımı çağrı ağaçları en üst düzey düğüm sözde düğümüdür|  
|![2. adım](../profiling/media/procguid-2.png "ProcGuid_2")|Çoğu uygulama, zaman **harici kodu Göster** seçeneği devre dışıdır, ikinci düzey düğüm bir **[harici kod]** başlatır ve durdurur, uygulamanın sistem ve framework kodu içeren bir düğüm UI çizer iş parçacığı zamanlama denetler ve uygulamayı diğer alt düzey hizmetler sağlar.|  
|![3. adım](../profiling/media/procguid-3.png "ProcGuid_3")|İkinci düzey düğümünün alt öğeleri, kullanıcı kodu yöntemleri ve çağrılan veya framework kodu ve ikinci düzey sistem tarafından oluşturulan zaman uyumsuz yordamlarını verilmiştir.|  
|![4. adım](../profiling/media/procguid-4.png "ProcGuid_4")|Bir yöntemin alt düğümleri yalnızca üst yöntem çağrıları için veri içerir. Zaman **harici kodu Göster** olduğundan devre dışı, uygulama yöntemlerini de içerebilir bir **[harici kod]** düğümü.|  
  
####  <a name="BKMK_External_Code"></a> Dış kod  
 Dış kod yazdığınız kod tarafından çalıştırılan sistem ve framework bileşenleri işlevlerde oluşur. Dış kod Başlat ve uygulamayı durdurun, UI çizme, iş parçacığı oluşturma denetleyen ve uygulama diğer alt düzey hizmetler sağlayan işlevler içerir. Çoğu durumda, dış kod içinde olacak ve bu nedenle CPU kullanımı çağırma ağacı toplar harici işlevler kullanıcı yöntemi birine **[harici kod]** düğümü.  
  
 Dış kod arama yollarını görüntülemek istediğinizde seçin **harici kodu Göster** gelen **filtre görünümü** listeleyin ve ardından **Uygula**.  
  
 ![Filtre görünümü seçin, ardından dış Kodu Göster](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Böylece işlev adı sütun genişliğini tüm bilgisayar monitörü en büyük görüntü genişliğini aşabilir birçok dış kod arama zincirleri iç içe girmiş olduğunu, unutmayın. Bu durumda, işlev adları olarak gösterilir **[...]** :  
  
 ![Çağrı ağacında dış kod iç içe geçmiş](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Aradığınız bir düğüm bulmak için arama kutusunu kullanın ve ardından verilerin görüntülenebilmesi için yatay kaydırma çubuğunu kullanın:  
  
 ![İç içe geçmiş bir dış kod arama](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a> Ağaç veri sütunları arayın  
  
|||  
|-|-|  
|**Toplam CPU (%)**|![Toplam % veri Denklem](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Seçili zaman aralığındaki işlevi ve işlev tarafından çağırılan işlevlerde yapılan çağrılar tarafından kullanılan uygulamanın CPU etkinliği yüzdesi. Bu farklı olduğunu unutmayın **CPU kullanımı** toplam etkinlik uygulamanın toplam kullanılabilir CPU kapasitesi için bir zaman aralığında karşılaştıran zaman çizelgesi grafiği.|  
|**Kendi kendine CPU (%)**|![Kendi kendine % Denklem](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> İşlev tarafından çağırılan işlevlerdeki etkinlik hariç bu işleve yapılan çağrılar tarafından kullanılan seçili zaman aralığındaki uygulamanın CPU etkinliği yüzdesi.|  
|**Toplam CPU (ms)**|Seçili zaman aralığındaki işlevi ve işlev tarafından çağrılan işlevler çağrılarında harcanan milisaniye sayısı.|  
|**Kendi kendine CPU (ms)**|Seçili zaman aralığındaki işlevi ve işlev tarafından çağrılan işlevler çağrılarında harcanan milisaniye sayısı.|  
|**Module**|İşlev veya bir [harici kod] düğümünde işlevler içeren modül sayısı içeren modül adı.|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Zaman uyumsuz işlevleri CPU kullanımına çağrı ağacı  
 Derleyici, zaman uyumsuz bir yöntem karşılaştığında, yöntemin yürütmesini denetlemek için gizli bir sınıf oluşturur. Kavramsal olarak, derleyicinin ürettiği işlevleri, özgün metodun işlemlerini zaman uyumsuz olarak çağırın ve geri çağırmaları, Zamanlayıcı ve bunları doğru gerekli yineleyiciler listesini içeren bir durum makinesindeki bir sınıftır. Özgün yöntemi tarafından bir üst yöntem çağrıldığında, çalışma zamanı üst yürütme bağlamında yöntemi kaldırır ve gizli sınıfı yöntemleri uygulamanın yürütmesini denetlemek sistem ve framework kod bağlamında çalışır. Zaman uyumsuz yöntemler genellikle, ancak her zaman, bir veya daha fazla farklı iş parçacıkları üzerinde yürütülür. Bu kod CPU kullanımı çağrı ağacında altı olarak gösterilen **[harici kod]** düğümünün üst ağaç düğümünü hemen altındaki.  
  
 Bu örneğimizde görmek için yeniden seçin `GetMaxNumberAsyncButton_Click` zaman çizelgesi segmenti.  
  
 ![GetMaxNumberAsyncButton&#95;tıklayın rapor seçim](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 İlk iki düğüm altında **[harici kod]** durum makine sınıfın derleyici tarafından oluşturulan yöntemler. Üçüncü özgün yöntem çağrısı var. Oluşturulan yöntemler genişletme neler olduğunu gösterir.  
  
 ![GetMaxNumberAsyncButton Genişletilmiş&#95;tıklayın çağrı ağacı](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` çok az yapar; Görev değerlerin bir listesini yönetir, en fazla sonuçları hesaplar ve çıktıyı görüntüler.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` zamanlama ve çağrısını sarmalamak 48 görevleri başlatmak için gereken etkinlik gösterir `GetNumberAsync`.  
  
-   `MainPage::<GetNumberAsync>b__b` çağıran görevler etkinliğini gösterir `GetNumber`.  
  
##  <a name="BKMK_Next_steps"></a> Sonraki adımlar  
 CpuUseDemo uygulama uygulamaları en parlak değildir ancak zaman uyumsuz işlem ve diğer araçlar performans ve tanılama hub'ındaki denemek için kullanarak, yardımcı program genişletebilirsiniz.  
  
-   Unutmayın `MainPage::<GetNumberAsync>b__b` [harici kod] GetNumber yöntemi yürütmeyi sağladığından daha fazla zaman harcadığını. Bu süre çoğunu, zaman uyumsuz işlemlerin bir ek yüktür. Görevlerin sayısını artırmayı deneyin (kümesinde `NUM_TASKS` MainPage.xaml.cs, sabit) ve yineleme sayısını azaltmayı `GetNumber` (değiştirme `MIN_ITERATIONS` değeri). Koleksiyon senaryosu çalıştırabilirsiniz ve CPU etkinliği karşılaştırın `MainPage::<GetNumberAsync>b__b`, özgün CPU kullanımı Tanılama oturumu için. Deneyin görevleri azaltarak ve yinelemeleri artırır.  
  
-   Kullanıcılar, genellikle gerçek uygulamanızın performansını hakkında düşünmeniz gerekmez; Algılanan performans ve uygulama yanıt verme hızını hakkında bunlar dikkat edin. XAML UI yanıt araç etkisi yanıt hızını algılanan UI iş parçacığı üzerinde etkinlik ayrıntılarını gösterir.  
  
     Tanılama ve performans hub'ında yeni bir oturum oluşturun ve hem XAML UI yanıt araç hem de CPU kullanımı aracı ekleyin. Koleksiyon senaryo çalıştırın. Bu makaleyi okudunuz, şimdiye kadar rapor büyük olasılıkla, size zaten dışarı farklılıkları ancak yapacağınızı bilmiyorsanız herhangi bir şey sunmayacaktır **UI iş parçacığı kullanımı** iki yöntem için zaman çizelgesi grafiği çarpıcı. Karmaşık, gerçek dünyadaki uygulamalarda araçları birleşimi çok yararlı olabilir.  
  
##  <a name="BKMK_MainPage_xaml"></a> MainPage.xaml  
  
```csharp  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
##  <a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```



