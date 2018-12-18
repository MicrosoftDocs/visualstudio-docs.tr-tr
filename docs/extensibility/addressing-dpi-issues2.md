---
title: DPI Issues2 adresleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2c4ca03c932b86ad6f9907020b037abb1308a6f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918538"
---
# <a name="address-dpi-issues"></a>DPI sorunları
Giderek artan sayıda cihazları "yüksek çözünürlüklü" ekranlarla yayımlayan. Bu ekranları genellikle 200'den fazla inç başına piksel (ppi) sahiptir. Uygulamanın bu bilgisayarlarda çalışmak bir cihaz için normal görüntülemeye uzaklıkta içeriği görüntüleme gereksinimlerini karşılayacak şekilde ölçeklenmesine olanak içerik gerektirir. 2014'ten itibaren yüksek yoğunluklu görüntüler için birincil hedef mobil cihazlar (tabletler, clamshell dizüstü bilgisayarları ve telefonları) bilgi işlem.  
  
 Windows 8.1 ve üzeri ortamlar nerede makine hem de yüksek yoğunluklu eklenir ve aynı zamanda standart yoğunluklu görüntüler ve görüntüler ile çalışmak bu makineleri sağlamak için çeşitli özellikler içerir.  
  
- Windows izin verebilir, Ölçek içerik "olun metni ve diğer öğeleri daha büyük veya küçük" kullanarak cihazı ayarlama (Windows XP itibaren kullanılabilir).  
  
- Windows 8.1 ve üzeri farklı piksel densities, ekranlar arasında taşıdığınızda tutarlı olmasını uygulamalarının çoğu için içerik otomatik olarak ölçeklenir. Yüksek yoğunluklu (% 200 ölçeklendirme) birincil görüntülenir ve ikincil görüntü standart yoğunluk (% 100) olduğunda, Windows otomatik olarak uygulama penceresinin içeriği ikincil ekranda ölçeğini (1 piksel artımlı tarafından işlenen her 4 piksel görüntülenen Uygulama).  
  
- Windows için piksel yoğunluğu ölçeklendirme ve uzaklık (Windows 7 ve üzeri, OEM yapılandırılabilir) görüntülemek için görüntüleme hakkı Varsayılan olarak atar.  
  
- Otomatik olarak Windows (itibariyle, Windows 8.1 S14) 280 ppi aşan yeni cihazlarda % 250 içerik oluşturan ölçeklendirebilirsiniz.  
  
  Windows, artan piksel sayıları yararlanmak için UI'yi ölçeklendirme ile ilgilenen bir yolu vardır. Bir uygulama bu sisteme kendisini "sistemi DPI." bildirerek kabul eder Bunu yapmazsanız uygulama, sistem tarafından ölçeklenir. Bu, uygulamanın tamamı piksel esnetilmiş eşit olduğu bir "benzer öğe" kullanıcı deneyimine neden olabilir. Örneğin:  
  
  ![DPI sorunlarını belirsiz](../extensibility/media/dpi-issues-fuzzy.png "DPI sorunlarını belirsiz")  
  
  Visual Studio DPI ölçeklendirme uyumlu olarak kabul eder ve bu nedenle değil "sanallaştırılır."  
  
  Windows (ve Visual Studio) sistemi tarafından ayarlanan Etkenler ölçeklendirme ile ilgili farklı yöntemleri olan birkaç kullanıcı Arabirimi teknolojilerinden yararlanarak. Örneğin:  
  
- WPF denetimlerini bir CİHAZDAN bağımsız şekilde (birim, piksel değil) ölçer. WPF kullanıcı Arabirimi için geçerli DPI otomatik olarak ölçeklendirir.  
  
- UI çerçevesi bağımsız olarak tüm metin boyutları nokta olarak ifade edilir ve bu nedenle sisteminde DPI bağımsız olarak kabul edilir. Win32, WinForms ve WPF metin zaten ölçeği doğru görüntüleme cihazında çizilen olduğunda.  
  
- Win32/WinForms iletişim kutuları ve windows metni (örneğin, aracılığıyla kılavuz, flow ve Tablo düzeni Panel) ile yeniden boyutlandırır Düzen etkinleştirmek için bir yola sahip. Bu yazı tipi boyutunu artırdık yükleyen ölçeklenmez sabit kodlanmış piksel konumları önleme etkinleştirin.  
  
- Sistem tarafından sağlanan simgeler veya kaynakları (örneğin, SM_CXICON ve SM_CXSMICON) sistemi ölçümlere göre zaten yukarı ölçeklendirilemez.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Eski bir Win32 (GDI, GDI + ') ve WinForms tabanlı kullanıcı Arabirimi  
 WPF zaten DPI kullanan yüksek olsa da, Win32/GDI tabanlı kodumuz çoğunu başlangıçta aklınızda DPI tanıma ile yazılmadı. Windows DPI ölçeklendirme API'leri sağlamıştır. Win32 sorunlar için düzeltmeler bu ürün genelinde tutarlı bir şekilde kullanmanız gerekir. Visual Studio bir yardımcı sağlanan işlevselliği çoğaltma ve ürün arasında tutarlılık sağlamaya önlemek için sınıf kitaplığı.  
  
## <a name="high-resolution-images"></a>Yüksek çözünürlüklü resimleri  
 Bu bölümde, öncelikli olarak Visual Studio 2013 genişletme geliştiriciler içindir. Visual Studio 2015 için Visual Studio'da yerleşik olarak bulunan görüntü hizmetini kullanın. Ayrıca, Visual Studio'nın birçok sürümü destek/hedef gerekiyorsa ve önceki sürümlerde olmadığından bu nedenle 2015'te Görüntü hizmeti kullanarak bir seçenek değil de bulabilirsiniz. Bu bölümde ayrıca sizin için ise.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Çok küçük görüntülerini ölçeklendirme  
 Çok küçük resimleri yukarı ölçeklendirilemez ve GDI ve bazı genel yöntemleri kullanarak WPF çizilir. Yönetilen DPI yardımcı sınıfları, iç ve dış Visual Studio tümleştiricileri simgeler, bit eşlemler, imagestrips ve imagelists ölçeklendirme adresine kullanılabilir. Win32 tabanlı yerel C / C ++ Yardımcıları HICON, HBITMAP HIMAGELIST ve VsUI::GdiplusImage ölçeklendirme için kullanılabilir. Bir bit eşlem genellikle ölçekleme, yalnızca bir yardımcı kitaplık başvuru dahil olmak üzere sonra bir satır değişikliği gerektirir. Örneğin:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Bir ImageList ölçeklendirme olup ImageList yükleme zamanında tamamlandıktan veya çalışma zamanında eklenir bağlıdır. Tam yükleme zamanında varsa, çağrı `LogicalToDeviceUnits()` bir bit eşlem ile ImageList aynı olur. Kod oluşturma ImageList önce tek bir bit eşlem yük gerektiğinde ImageList görüntü boyutu ölçeğini emin olun:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 Yerel kodda boyutları ImageList gibi oluştururken ölçeklendirilebilir:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Kitaplık işlevlerini yeniden boyutlandırma algoritması belirtme izin verin. Ne zaman imagelists içinde yerleştirilecek ölçeklendirme görüntüleri saydamlık için kullanılan arka plan rengi belirttiğinizden emin olun veya NearestNeighbor (Bu %125 ve % 150 deformasyonları çalışmamasına neden olur) ölçeklendirme kullanın.  
  
 Başvurun <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> MSDN'de belgelerin.  
  
 Aşağıdaki tabloda, faktörleri ölçeklendirme örnekleri görüntüleri karşılık gelen DPI nasıl ölçeklendirilmesi gerektiğini gösterir. Müşterilerimizin en iyi uygulama (% 100-%200 DPI ölçeklendirme) Visual Studio 2013'ten itibaren turuncu renkte özetlenen görüntülerini gösterin:  
  
 ![Ölçeklendirme, DPI sorunlarını](../extensibility/media/dpi-issues-scaling.png "DPI sorunlarını ölçeklendirme")  
  
## <a name="layout-issues"></a>Düzen sorunları  
 Yaygın bir düzen sorunları, öncelikle noktaları ölçeği kullanıcı arabiriminde ve birbirlerine göreli tutarak yerine Mutlak Konumlar (özellikle de piksel birimleri) kullanılarak önlenebilir. Örneğin:  
  
- Düzen/metin konumlarını hesabına ölçeği görüntüleri için ayarlamanız gerekir.  
  
- Izgara sütunları genişlikleri ölçeği metin için ayarlanmış olması gerekir.  
  
- Sabit kodlanmış boyutları veya öğeler arasındaki boşluk ölçeklendirilmesi gerekiyor da gerekir. Yalnızca metin boyutlarına göre boyutları genellikle iyi olduğu yazı tipleri otomatik olarak ölçeklenir.  
  
  Yardımcı işlevleri kullanılabilir <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> X ve Y Ekseninde ölçeklendirmeye izin vermek için sınıfı:  
  
- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (işlevler izin ölçeklendirme X / Y ekseni)  
  
- int alanı DpiHelper.LogicalToDeviceUnitsX (10); =  
  
- int yükseklik VsUI::DpiHelper::LogicalToDeviceUnitsY(5); =  
  
  Rect, nokta ve boyutu gibi nesneleri ölçeklendirmeye izin vermek için LogicalToDeviceUnits aşırı yüklemeleri vardır.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Ölçek görüntülerinin ve Düzen DPIHelper kitaplığı/sınıfını kullanma  
 Visual Studio DPI yardımcı kitaplık, yerel ve yönetilen biçimde sağlanır ve Visual Studio Kabuğu dışında diğer uygulamalar tarafından kullanılabilir.  
  
 Kitaplığı kullanmak için Git [Visual Studio VSSDK genişletilebilirlik örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples) ve yüksek DPI_Images_Icons örneği kopyalayın.  
  
 Kaynak dosyalarına dahil *VsUIDpiHelper.h* ve statik işlevlerini çağırma `VsUI::DpiHelper` sınıfı:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Yardımcı işlevleri Modül düzeyinde veya sınıf düzeyi statik değişkenler kullanmayın. Kitaplığı statikler iş parçacığı eşitleme için de kullanır ve başlatma sırası sorunlarla karşılaşabilirsiniz. Statik olmayan üye değişkenleri için bu statikler dönüştürün ya da (bunlar ilk erişimde oluşturulmuş için), bunları bir işleve kaydır.  
  
 Visual Studio ortamı içinde çalışır, yönetilen koddan DPI yardımcı işlevleri erişmek için:  
  
-   Kullanan projenin Kabuk MPF en son sürümünü başvurmalıdır. Örneğin:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Proje başvuruları olduğundan **System.Windows.Forms**, **PresentationCore**, ve **PresentationUI**.  
  
-   Kod içinde kullanma **Microsoft.VisualStudio.PlatformUI** DpiHelper sınıfının statik ad alanı ve arama işlevleri. Desteklenen türler için (noktaları, boyutları, dikdörtgenler ve benzeri) nesneleri döndürmek yeni uzantı işlevleri ölçeği sağlanan vardır. Örneğin:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>WPF görüntü belirsizlik yakınlaştırılabilir kullanıcı arabiriminde uğraşmanızı  
 WPF içinde bit eşlemler otomatik olarak WPF tarafından resimler veya büyük ekran görüntüleri için iyi çalışır, ancak algılanan belirsizlik oluşturduğundan menü öğesi simgeleri için uygun değil bir yüksek kaliteli çift kübik algoritması (varsayılan) kullanarak geçerli DPI yakınlaştırma düzeyini yeniden boyutlandırılıyor .  
  
 Öneriler:  
  
- Logo görüntüsü ve başlıklar resim, varsayılan için <xref:System.Windows.Media.BitmapScalingMode> modu yeniden boyutlandırma kullanılabilir.  
  
- Menü öğeleri ve yansır görüntüleri <xref:System.Windows.Media.BitmapScalingMode> (en % 200 ve %300) belirsizlik ortadan kaldırmak diğer bozulma yapıtları neden olmaz olduğunda kullanılmalıdır.  
  
- % 100 (örneğin, %250 veya % 350) birden çok büyük yakınlaştırma düzeyleri için çift kübik yansır görüntülerle ölçeklendirme belirsiz, soluk kullanıcı Arabiriminde sonuçlanır. İlk NearestNeighbor görüntüyle % 100 (örneğin, %200 veya % 300) en büyük birden fazla ölçekleme ve buradan çift kübik ile ölçeklendirme göre daha iyi bir sonuç elde edilir. Özel durum bakın: WPF görüntüleri için büyük DPI prescaling düzeyleri daha fazla bilgi için.  
  
  Üye DpiHelper SAX Microsoft.VisualStudio.PlatformUI ad alanındaki <xref:System.Windows.Media.BitmapScalingMode> bağlama için kullanılabilir. Bu modu üründe DPI Ölçeklendirme çarpanı bağlı olarak aynı şekilde, ölçeklendirme bit eşlem denetlemek Visual Studio Kabuğu izin verir.  
  
  XAML içinde kullanmak için aşağıdakileri ekleyin:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Visual Studio Kabuğu zaten en üst düzey pencereler ve iletişim kutuları üzerinde bu özelliği ayarlar. WPF tabanlı UI Visual Studio'da çalıştırma zaten bu devralır. Ayar, belirli kullanıcı Arabirimi parçası için dağıtılmaz, XAML/WPF UI kök öğe üzerinde ayarlanabilir. Win32 üst sahip öğelerde açılır pencereleri yerleri burada böyle içerir ve Blend gibi dışında çalışan Tasarımcı windows işlem.  
  
 Bazı kullanıcı Arabirimi tasarımcıları WPF tabanlı (WPF Masaüstü ve Windows Store) ve Visual Studio Metin Düzenleyicisi gibi sistem kümesi DPI yakınlaştırma düzeyini bağımsız olarak ölçeklendirebilirsiniz. Bu gibi durumlarda DpiHelper.BitmapScalingMode kullanılmamalıdır. Düzenleyicide bu sorunu gidermek için oluşturulan özel bir özellik IDE takım RenderOptions.BitmapScalingMode başlıklı. Bu özellik değeri, sistem ve kullanıcı Arabirimi, birleştirilmiş yakınlaştırma düzeyine bağlı olarak HighQuality veya NearestNeighbor ayarlayın.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Özel durum: WPF görüntüleri büyük DPI düzeyleri için prescaling  
 % 100 (örneğin, %250, %350 vb.) katları olan çok büyük yakınlaştırma düzeyleri için belirsiz, soluk kullanıcı arabiriminde çift kübik sonuçlarla yansır görüntüleri ölçeklendirilmesi. Bu görüntüler NET metin yanı sıra izlenimi, optik izlenimini gibi hemen hemen aynıdır. Görüntüleri daha yakından göz ve ilgili metin olarak odak dışında görünür. Büyütülmüş bu boyutta ölçeklendirme sonucu, ilk NearestNeighbor görüntüyle en büyük birden fazla (örneğin, %200 veya % 300) % 100 oranında ölçeklendirme ve çift kübik (ek %50) kalanı için ile ölçeklendirme tarafından geliştirilebilir.  
  
 Aşağıdaki sonuçları farklar burada ilk resim ölçeklendirilir örneğidir -> % 100 -> Gelişmiş çift ölçeklendirme algoritması ile %200 % 250 ve ikincisi yalnızca % çift kübik 100 ile -> % 250.  
  
 ![DPI sorunlarını çift ölçeklendirme örnek](../extensibility/media/dpi-issues-double-scaling-example.png "DPI ölçeklendirme çift örnek sorunları")  
  
 Her bir görüntü öğesi görüntülemek için bu çift ölçeklendirme, XAML biçimlendirmesi kullanılacak kullanıcı arabirimini etkinleştirmek için değiştirilmesi gerekir. Aşağıdaki örnekler, WPF içinde çift ölçeklendirme Shell.12/14 ve DpiHelper kitaplığı kullanarak Visual Studio'da kullanımını göstermektedir.  
  
 1. adım: görüntü % 200, %300 Prescale vb. NearestNeighbor kullanma.  
  
 XAML işaretleme uzantısı ile veya bir bağlama uygulanan dönüştürücü kullanarak görüntüyü prescale. Örneğin:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Görüntü ayrıca temalı gerekiyorsa (en değilse, gerekir), ilk Tema oluşturma görüntü ve sonra önceden ölçeklendirme yapar. farklı bir dönüştürücü biçimlendirme kullanabilirsiniz. Biçimlendirme kullanabilirsiniz <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> veya <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>istenen dönüştürme çıkış bağlı olarak.  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 2. adım: son boyutu için geçerli DPI doğru olduğundan emin olun.  
  
 WPF kullanıcı Arabirimi için üzerinde UIElement BitmapScalingMode özelliği kullanarak geçerli DPI ölçeklendirme olduğundan, iki veya üç kez büyük kaynağına nasıl görüneceğini prescaled bir görüntü kullanarak bir görüntü denetimi gerekir. Bu etkiyi sayaç birkaç yolu şunlardır:  
  
-   Boyut orijinal görüntünün % 100 biliyorsanız, tam görüntü denetiminin boyutunu belirtebilirsiniz. Bu boyutları ölçeklendirme önce kullanıcı arabiriminin boyutu uygulanan ücreti yansıtılır.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Özgün resmin boyutu bilinmiyorsa LayoutTransform son görüntü nesneyi ölçeklendirmek için kullanılabilir. Örneğin:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>Alma WebOC HDPI desteğini etkinleştirme  
 Varsayılan olarak, HDPI algılama ve destek alma WebOC denetimler (örneğin, WPF veya Iwebbrowser2 arabirimi WebBrowser denetimi) etkinleştirmeyin. Sonuç yüksek çözünürlüklü bir ekranda çok küçük görüntü içeriğe sahip katıştırılmış bir denetimi olacaktır. Belirli web alma WebOC örneğinde yüksek DPI desteğini nasıl etkinleştireceğinizi açıklar.  
  
 IDocHostUIHandler arabirimini uygular (MSDN makalesine bakın [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 İsteğe bağlı olarak ICustomDoc arabirimini uygular (MSDN makalesine bakın [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Alma WebOC'ın belgeyle IDocHostUIHandler uygulayan sınıf ilişkilendirin. Yukarıdaki ICustomDoc arabirimin uygulanan alma WebOC'ın belge özelliği geçerli duruma geldiği için bir ICustomDoc dönüştürün ve IDocHostUIHandler uygulayan sınıf SetUIHandler yöntemini çağırın.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 ICustomDoc arabirimini uygulamadı sonra alma WebOC'ın belge özelliği geçerli hemen sonra bir IOleObject ve çağrı için tür dönüştürme gerekecektir `SetClientSite` yöntemini IDocHostUIHandler uygulayan bir sınıf içinde. Geçirilen DOCHOSTUIINFO DOCHOSTUIFLAG_DPI_AWARE bayrağı ayarlayın `GetHostInfo` yöntem çağrısı:  
  
```csharp  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Bu, alma WebOC denetim HPDI desteklemek için ihtiyaç duyduğunuz tüm olmalıdır.  
  
## <a name="tips"></a>İpuçları  
  
1.  Belge özelliği alma WebOC denetimde değişirse, belge IDocHostUIHandler sınıfı ile yeniden ilişkilendirmeniz gerekebilir.  
  
2.  Yukarıdaki çalışmazsa, değişikliği DPI bayrağı için çekme değil alma WebOC bilinen bir sorun yoktur. Bu düzeltme en güvenilir yakınlaştırma yüzdesi için iki farklı değerlerle iki çağrıları anlamı alma WebOC optik Yakınlaştırması değiştirilecek yoludur. Ayrıca, bu geçici çözüm gerekiyorsa, her navigate çağrısında gerçekleştirmek gerekli olabilir.  
  
    ```csharp  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```
