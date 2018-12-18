---
title: Komut satırı Yakalama aracı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4cafc8c066025f87d233d8b6db8a97be1aa16f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770685"
---
# <a name="command-line-capture-tool"></a>Komut Satırı Yakalama Aracı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DXCap.exe, grafik tanılama yakalama ve kayıttan yürütme için bir komut satırı aracıdır. Bu, Direct3D 10 ila Direct3D 12 arasında tüm özellik düzeylerini destekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe –p [filename] –screenshot [-frame frames]  
DXCap.exe –p [filename] –toXML [xml_filename]  
DXCap.exe –v [–file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe –info  
```  
  
#### <a name="parameters"></a>Parametreler  
 `-file``filename`  
 Yakalama modu altında (`-c`), `filename` grafik bilgilerini kaydedilmiş için grafik günlük dosyasının adını belirtir. Varsa `filename` belirtilmezse, grafik bilgilerini adlı bir dosyaya kaydedilir `<appname>-<date>-<time>.vsglog` varsayılan olarak.  
  
 Doğrulama altında (-v) modunda `filename` doğrulanması için grafik günlük dosyasının adını belirtir. Varsa `filename` belirtilmezse, son doğrulandığı grafik günlüğü yeniden kullanılır.  
  
 `-frame``frames`  
 Yakalama modu altında `frames` yakalamak istediğiniz çerçeve belirtir. İlk çerçeve 1'dir. Birden çok karesi, virgül ve aralıkları kullanarak belirtebilirsiniz. Örneğin, varsa `frames` olduğu `2, 5, 7-9, 15`, ardından çerçeve `2`, `5`, `7`, `8`, `9`, ve `15` yakalanır.  
  
 `-period``periods`  
 Yakalama modu altında `periods` sırasında istediğiniz kareleri yakalayın saniye cinsinden zaman aralığı belirtir. Birden çok nokta, virgül ve aralıkları kullanarak belirtebilirsiniz. Örneğin, `periods` olduğu `2.1-5, 7.0-9.3`, ardından arasında işlenmiş çerçeveler `2.1` ve `5` saniye ve arasında`7` ve `9.3` saniye yakalanır.  
  
 `-manual`  
 Yakalama modu altında `-manual` çerçeveler el ile Print Screen tuşuna basarak yakalanmasını belirtir. Uygulama başlatıldığında yakalanan kareleri; kare Yakalamayı durdurmak için komut satırı arabirimine dönün ve enter tuşuna basın.  
  
 `-c` `app` [`args...`]  
 Yakalama modu. Yakalama modu altında `app` grafik bilgilerini; yakalamak istediğiniz uygulamanın adını belirtir. `args...` bu uygulama için ek komut satırı parametreleri belirtir.  
  
 `-p` [`filename`]  
 Kayıttan yürütme modu (`-p`). Kayıttan yürütme modu altında `filename` tekrarlanmasını grafik günlük dosyasının adını belirtir. Varsa `filename` belirtilmezse, en son geri yürütülmüş bir grafik günlüğü yeniden kullanılır.  
  
 `-debug`  
 Kayıttan yürütme modu altında `-debug` , kayıttan yürütme Direct3D hata ayıklama katmanının etkinleştirilip gerçekleştirilmelidir belirtir.  
  
 `-warp`  
 Kayıttan yürütme modu altında `-warp` WARP yazılım Oluşturucusu kullanarak bu kayıttan yürütme gerçekleştirilmelidir belirtir.  
  
 `-hw`  
 Kayıttan yürütme modu altında `-hw` GPU donanım kullanarak, kayıttan yürütme gerçekleştirilmelidir belirtir.  
  
 `-config`  
 Kayıttan yürütme modu altında `-config` bu bilgileri günlüğe kaydettiyse grafik günlük dosyasını yakalamak için kullanılan makine hakkındaki bilgileri görüntüler.  
  
 `-rawmode`  
 Kayıttan yürütme modu altında `-rawmode` , kayıttan yürütme, kayıtlı olayları değişiklik yapılmaksızın gerçekleştirilmelidir belirtir. Normal işlemlerde kayıttan yürütme modu, hata ayıklama basitleştirmek ve kayıttan yürütme hızı için kayıttan yürütme için küçük değişiklikler olun. Örneğin, bu takas zinciri komutları yürütülürken yerine takas zinciri çıkış benzetimini. Genelde bu bir sorun değildir ancak kaydedilen olaylara daha geçmişe bağlı bir şekilde gerçekleşmesini kayıttan yürütme gerekebilir; Örneğin, tam ekran modunda çalışırken yakalanan bir uygulama için tam ekran işleme davranışı geri yüklemek için bu seçeneği kullanın.  
  
 `-toXML` [`xml_filename`]  
 Kayıttan yürütme modu altında `xml_filename` için bir XML temsilini kayıttan yürütme yazıldığı dosyanın adını belirtir. Varsa `xml_filename` belirtilmezse, XML gösterimi, adlı bir dosyaya yazılır, dosya ile aynı kayıttan ancak verilen bir `.xml` uzantısı.  
  
 `-v`  
 Doğrulama modu. Doğrulama modu, hem donanım hem de WARP yakalanan kareleri yeniden oynatılır ve bir görüntü karşılaştırma işlevini kullanarak sonuçları karşılaştırılır. Bu özellik, işlemeyi etkileyen sürücü sorunları hızlı bir şekilde tanımlamak için kullanabilirsiniz.  
  
 `-examine``events`  
 Doğrulama modunda `events` grafik olaylarını anında sonuçlarını karşılaştırılır kümesini belirtir. Örneğin, `-examine present,draw,copy,clear` karşılaştırma yalnızca bu kategoriye ait olan olaylar için sınırlar.  
  
> [!TIP]
>  İle başlamanızı öneririz `-examine present,draw,copy,clear` çünkü bu çoğu sorunu ortaya ancak olaylar daha kapsamlı bir dizi daha önemli ölçüde daha az zaman alır. Gerekirse, bu olayları doğrulamak ve diğer türlerdeki sorunları ortaya çıkarmak için olayları daha büyük ya da farklı bir dizi belirtebilirsiniz.  
  
 `-haltonfail`  
 Doğrulama modunda `-haltonfail` WARP oluşturucusu ve donanım arasındaki farklar algılandığında doğrulama durdurur. Bir tuşa basıldığında sonra doğrulama devam eder.  
  
 `-exitonfail`  
 Doğrulama modunda `-exitonfail` WARP oluşturucusu ve donanım arasındaki farklar zaman algılandı hemen doğrulama çıkar. Program bu şekilde çıktığında üretebiliyorsa `0` ortamı; Aksi halde döndürür `1`.  
  
 `-showprogress`  
 Doğrulama modunda `-showprogress` doğrulama oturumu hakkındaki ilerleme bilgilerini görüntüler. WARP ilerleme durumu, sol tarafta gösterilir; Donanım ilerleme durumunu sağ tarafta görüntülenir.  
  
 `-e``search_string`  
 Yüklenen Windows Store apps numaralandırır. Bu bilgiler, Windows Store apps ile komut satırı yakalamaları gerçekleştirmek için kullanabilirsiniz.  
  
 `-info`  
 Makine ve yakalama DLL'leri hakkında bilgileri görüntüler.  
  
## <a name="remarks"></a>Açıklamalar  
 DXCap.exe üç modlarında çalışır:  
  
 Yakalama modu (-c)  
 Çalışan bir uygulamadan grafik bilgilerini yakalama ve grafik günlük dosyasını kaydedin. Yakalama özelliklerini ve dosya biçimi olan Visual Studio için aynıdır.  
  
 Kayıttan yürütme modu (-p)  
 Var olan bir grafik günlüğü dosyadan daha önce yakalanan grafik olaylarını kayıttan yürütme. Grafik bile oturum açtığınızda varsayılan olarak, bir pencerede kayıttan oluşur dosya bir tam ekran uygulamasından yakalanan. Kayıttan yürütme, grafik oturumu dosyası bir tam ekran uygulamasından yakalanan yalnızca tam ekran olarak gerçekleşir ve `–rawmode` belirtilir.  
  
 Doğrulama modunu (`-v`)  
 İşleme davranışını, yakalanan kareleri hem donanım hem de WARP kayıttan sonra bir görüntü karşılaştırma işlevini kullanarak sonuçları karşılaştırma doğrular. Bu özellik, işlemeyi etkileyen sürücü sorunları hızlı bir şekilde tanımlamak için kullanabilirsiniz.  
  
 Bu modlara ek olarak, yakalama veya grafik bilgilerini kayıttan gerçekleştirmeyin iki işlev dxcap.exe gerçekleştirir.  
  
 Numaralandırma işlevi (`-e`)  
 Makinede yüklü Windows Store apps hakkındaki ayrıntıları görüntüler. Paket adı ve bir Windows Store uygulaması yürütülebilir dosyayı tanımlayan AppID bu ayrıntıları içerir. Bir windows mağazası uygulamasından DXCap.exe kullanarak grafik bilgilerini yakalamak için bir masaüstü uygulaması yakaladığınızda, kullanılan yürütülebilir dosya adı yerine uygulama kimliği ve paket adı kullanın.  
  
 Bilgi işlevi)`-info)`  
 Makine ve yakalama DLL'leri hakkında ayrıntıları gösterir.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Masaüstü bir uygulamadan grafik bilgilerini yakalama  
 Kullanım `–c` grafik bilgilerini yakalamak istediğiniz uygulamayı belirtmek için.  
  
```ms-dos  
DXCap.exe –c BasicHLSL11.exe  
```  
  
 Varsayılan olarak, grafik bilgilerini adlı bir dosyaya kaydedilir `<appname>-<date>-<time>.vsglog`. Kullanım `–file` için kaydetmek için farklı bir dosya belirtmek için.  
  
```ms-dos  
DXCap.exe –file regression_test_12.vsglog –c BasicHLSL11.exe  
```  
  
 Öğesinden sonra uygulamanın dosya adı dahil ederek yakalayacağınızı uygulama için ek komut satırı parametrelerini belirtin.  
  
```ms-dos  
DXCap.exe –c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 Yukarıdaki örnekteki komut, 3B içeriği işlemek için WebGL API kullanan www.fishgl.com bulunan Web sayfası görüntülerken Internet Explorer'ın Masaüstü sürümünü grafik bilgileri yakalar.  
  
> [!NOTE]
>  Sonra uygulamayı görünen komut satırı bağımsız değişkenleri için geçirildiğinden, kullanmadan önce DXCap.exe için hedeflenen bağımsız değişkenleri belirtmeniz gerekir `–c` seçeneği.  
  
### <a name="capture-graphics-information-from-a-windows-store-app"></a>Windows Store uygulamadan grafik bilgilerini yakalama.  
 Windows Store uygulamadan grafik bilgilerini yakalayabilirsiniz.  
  
```ms-dos  
DXCap.exe –c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 Bir Windows Store uygulaması yakalamak için DXCap.exe kullanarak bir Windows Masaüstü uygulamasından yakalamak için kullanılacak benzer, ancak bunun yerine bir masaüstü uygulaması, dosya adı tarafından tanımlama, Windows Store uygulaması paketi tarafından belirleyin adı adı veya yürütülebilir dosyanın içinde bu paketi kimliği yakalamak istediğiniz yaş. Makinenizde yüklü Windows Store uygulamaları belirlemek nasıl kaydolacağınızı daha kolay hale getirmek için kullanın `–e` DXCap.exe seçeneğiyle bunları numaralandırmak için:  
  
```ms-dos  
DXCap.exe -e  
```  
  
 Aradığınız uygulamayı bulmak için bir isteğe bağlı arama dizesi sağlayabilirsiniz. Arama dizesi sağlandığında, paket adı, uygulama adı veya uygulama kimlikleri arama dizesiyle eşleşen Windows Store apps DXCap.exe numaralandırır. Arama büyük/küçük harfe duyarsızdır.  
  
```ms-dos  
DXCap.exe –e map  
```  
  
 Yukarıdaki komut eşleşen "harita"; Windows Store apps numaralandırır. Çıktı aşağıdaki gibidir:  
  
 **"Microsoft.BingMaps" paketi:**  
 **Installdirectory: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **FullName: Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID: S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Ad: Microsoft.BingMaps**  
 **Yayımcı: CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S = Washington, C = US**  
 **Sürüm: 2.1.2914.1734**  
 **Başlatılabilir uygulamalar:**  
 **ID: AppexMaps**  
 **Exe  : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA: Hayır**  
 **(Başlatmak için) AppSpec: DXCap.exe - c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps** , grafik bilgilerini yakalamak için kullanabileceğiniz komut çıktı numaralandırılmış her uygulama için son satırının görüntüler.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Belirli çerçeveleri ya da belirli zamanları arasında çerçeveleri yakalayın.  
 Kullanım `–frame` virgül ve aralıkları kullanarak yakalamak istediğiniz çerçeveleri belirlemek için:  
  
```ms-dos  
DXCap.exe –frame 2,5,7-9,15 –c SimpleBezier11.exe  
```  
  
 Ya da kullanmak `–period` sırasında çerçeveleri yakalamak istediğiniz zaman aralıkları kümesini belirtmek için. Zaman aralıkları saniye cinsinden belirtilir ve birden çok aralık belirtilebilir:  
  
```ms-dos  
DXCap.exe –period 2.1-5, 7.0-9.3 –c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Etkileşimli olarak kareleri yakalayın.  
 Kullanım `–manual` çerçeveleri etkileşimli olarak yakalamak için. Yakalama başlatmak için Enter tuşuna basın ve yeniden durdurmak için Enter tuşuna basın.  
  
```ms-dos  
DXCap.exe –manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphics-log-file"></a>Grafik günlük dosyasını kayıttan yürütme  
 Kullanım `-p` daha önce yakalanan grafik günlük dosyasını kayıttan yürütmek için.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog  
```  
  
 En son yakalanan grafik günlüğü kayıttan yürütmek için dosya adı bırakın.  
  
```ms-dos  
DXCap.exe –p  
```  
  
### <a name="play-back-in-raw-mode"></a>Ham modunda kayıttan yürütme  
 Kullanım `-rawmode` gerçekleştiğine tam olarak yakalanan komutları yürütme işlemi. Normal kayıttan oynatım altında belirli komutları benzetilmiş değildir, örneğin, bir tam ekran uygulamasından yakalanan bir grafik günlük dosyası bir pencerede kayıttan; Ham modunun etkin olduğu aynı dosyanın tam ekran modunda kayıttan yürütme dener.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>WARP veya bir donanım cihazı kullanarak yeniden Yürüt  
 Zorlamak isteyebilirsiniz WARP kullanmak için bir donanım aygıtında yakalanan bir grafik günlüğü dosyası arkasına yürütmek ya da bir donanım cihazı kullanmak için WARP üzerinde yakalanan günlük kayıttan yürütme zorla. Kullanım `-warp` WARP kullanarak yeniden yürütülecek.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -warp  
```  
  
 Kullanım `-hw` donanım kullanarak yeniden yürütülecek.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Grafik günlük dosyasını WARP karşı doğrulama  
 Doğrulama modu için grafik günlük dosyasını kayıttan hem donanım hem de WARP yürütülebilir ve sonuçları karşılaştırılır. Bu sürücü tarafından neden olduğu işleme hataları belirlemenize yardımcı olabilir. – V grafik donanımı, WARP karşı doğru davranışını doğrulamak için kullanın.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Karşılaştırmalar miktarını azaltmak için karşılaştırmak doğrulama için komutları kümesini belirtebilirsiniz ve diğer komutlar yoksayılacak. Kullanın – sonuçları karşılaştırmak istediğiniz komut belirtmek için inceleyin.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog –examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Grafik günlük dosyası için PNG'ler Dönüştür  
 Görüntüleme veya çözümleme bir grafik günlüğü dosyasından çerçeveler için DXCap.exe yakalanan kareleri .png görüntü dosyaları (Taşınabilir Ağ Grafikleri) kaydedebilirsiniz. Kullanım `-screenshot` çıktısını almak için kayıttan yürütme modu altında yakalanan kareleri .png dosyaları için.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 Kullanım `–frame` ile `–screenshot` çıktısını almak istediğiniz çerçeveleri belirlemek için.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot –frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Bir grafik günlüğü dosyası XML'ye dönüştürür.  
 DXCap.exe işlemek ve FindStr veya XSLT gibi tanıdık araçları kullanarak grafik günlüklerini çözümleme için bir grafik günlüğü dosyası XML dönüştürebilirsiniz. Kullanım `-toXML` oynatmadan yerine günlük XML'ye dönüştürülecek kayıttan yürütme modu altında yedekleme.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML  
```  
  
 Varsayılan olarak, XML çıktısı, grafik günlüğü aynı ada sahip bir dosyaya yazılır, ancak bir .xml uzantısı atanmıştır. Yukarıdaki örnekte, XML dosyasını yeniden adlandırılacak **regression_test_12.xml**. XML dosyasını farklı bir ad vermek için bundan sonra belirtin `-toXML`.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML temp.xml  
```  
  
 Sonuç dosyası aşağıdakine benzer XML içerir:  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## <a name="requirements"></a>Gereksinimler



