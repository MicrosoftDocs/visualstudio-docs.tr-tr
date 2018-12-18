---
title: 'İzlenecek yol: Grafik bilgilerini programla yakalama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: feff1af744bd9f42d2fe8af67a72ec4856a09acc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747674"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>İzlenecek Yol: Grafik Bilgilerini Programla Yakalama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanabileceğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] grafik tanılama Direct3D uygulamadan grafik bilgilerini programla yakalama.  
  
 Programlı yakalama gibi senaryolarda kullanışlıdır:  
  
-   Grafik uygulamanızı swapchain doku için ne zaman işleyen gibi mevcut kullandığınızda değil yakalama programlı bir şekilde başlayın.  
  
-   Uygulamanızı, ne zaman DirectCompute hesaplamalar gerçekleştirmek için kullandığı gibi işlemesi yapmıyor açıldığında yakalama programlı olarak başlatılır.  
  
-   Çağrı `CaptureCurrentFrame`ne zaman bir işleme sorunuyla umuyor ve el ile testte yakalamak zor olduğunda ancak programlı olarak çalışma zamanında uygulamanın durumu hakkındaki bilgileri kullanarak tahmin.  
  
##  <a name="CaptureDX11_2"></a> Windows 8.1 programlı yakalama  
 Kılavuzun bu bölümü sağlam yakalama yöntemini kullanan Windows 8.1 üzerinde DirectX 11.2 API kullanan uygulamaları programlı yakalama gösterir. Programlı yakalama DirectX önceki sürümlerinde Windows 8.0 üzerinde kullanan uygulamalar kullanma hakkında daha fazla bilgi için bkz. [Windows 8.0 ve daha önce programlı yakalama](#CaptureDX11_1) bu kılavuzda daha sonra.  
  
 Bu bölümde bu görevlerin nasıl yapılacağını gösterir:  
  
-   Programlı yakalama kullanmak için uygulamanızı hazırlama  
  
-   IDXGraphicsAnalysis arabirimi alma  
  
-   Graf bilgilerini yakalama  
  
> [!NOTE]
>  Programlı yakalama önceki uygulamaları yararlandı için Uzak Araçlar üzerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Yakalama işlevselliği sağlamak için Windows 8.1 Direct3D 11.2 aracılığıyla doğrudan yakalamayı destekler. Sonuç olarak, artık Windows 8.1 üzerinde programlı yakalama için Uzak Araçlar'ı yüklemek gerekmez.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Programlı yakalama kullanmak için uygulamanızı hazırlama  
 Programlı yakalama uygulamanızda kullanmak için gereken üst bilgileri içermelidir. Bu üst bilgiler Windows 8.1 SDK'ın bir parçasıdır.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Programlı yakalama üst bilgilerini eklemek için  
  
-   Bu üst kaynak dosyanın IDXGraphicsAnalysis arabirimi burada tanımlayacaksınız şunlardır:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Üst bilgi dosyası vsgcapture.h—which destekler programlı yakalama Windows 8.0 ve önceki sürümleri dahil değildir — Windows 8.1 uygulamalarınızda programlı yakalama gerçekleştirilecek. Bu üstbilginin DirectX 11.2 ile uyumlu değil. D3d11_2.h üst bilgisi dahil olduktan sonra bu dosyayı dahil ise, derleyici bir uyarı verir. Vsgcapture.h d3d11_2.h önce eklediyseniz, uygulamayı başlatılmaz.  
  
    > [!NOTE]
    >  Haziran 2010 DirectX SDK'sı, makinenizde yüklü olduğundan ve projenizin yoluna içeren `%DXSDK_DIR%includex86`, yoluna sonuna taşıyın. Bir kitaplık yolu için de aynısını yapın.  
  
#### <a name="windows-phone-81"></a>Windows Phone 8.1  
 Windows Phone 8.1 SDK'sı DXProgrammableCapture.h üst bilgi içermediği için tanımlamanız gerekir `IDXGraphicsAnalysis` kullanabilirsiniz, böylece kendiniz arabirim `BeginCapture()` ve `EndCapture()` yöntemleri. Önceki bölümde açıklandığı gibi diğer üst bilgilerini içerir.  
  
###### <a name="to-define-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimi tanımlamak için  
  
- Aynı dosyada, üstbilgi dosyaları dahil IDXGraphicsAnalysis arabirimi tanımlayın.  
  
  ```  
  interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
  IDXGraphicsAnalysis : public IUnknown  
  {  
      STDMETHOD_(void, BeginCapture)() PURE;  
      STDMETHOD_(void, EndCapture)() PURE;  
  };  
  ```  
  
  Kolaylık olması için bu adımları izleyerek yeni bir üstbilgi dosyasında ve onu duyulduğu uygulamanıza dahil edin.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimi alma  
 DirectX 11.2 grafik bilgilerini yakalamak için önce DXGI hata ayıklama arabirimi almak sahip.  
  
> [!IMPORTANT]
>  Programlı yakalama kullanırken, yine de uygulamanızı grafik tanılama altında çalıştırmanız gerekir (Alt + F5 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]) veya altında [komut satırı Yakalama aracı](../debugger/command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimi almak için  
  
-   DXGI hata ayıklama arabirimine IDXGraphicsAnalysis arabirimi bağlama için aşağıdaki kodu kullanın.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Kontrol ettiğinizden emin olun `HRESULT` tarafından döndürülen `DXGIGetDebugInterface1` kullanmadan önce geçerli bir arabirim başlamanızı sağlamak için:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  Varsa `DXGIGetDebugInterface1` döndürür `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), uygulamayı grafik tanılama altında çalıştığından emin olun (Alt + F5 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]).  
  
### <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama  
 Geçerli bir sahip olduğunuza göre `IDXGraphicsAnalysis` kullanabileceğiniz arabirimi `BeginCapture` ve `EndCapture` grafik bilgilerini yakalamak için.  
  
##### <a name="to-capture-graphics-information"></a>Grafik bilgilerini yakalamak için  
  
-   Grafik bilgilerini yakalama başlatmak için kullanın `BeginCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Yakalamaya başlar hemen olduğunda `BeginCapture` çağrılır; sonraki kare başlamak beklemez. Geçerli kare sunulduğunda veya çağırdığınızda durakları yakalama `EndCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
##  <a name="CaptureDX11_1"></a> Windows 8.0 ve daha önce programlı yakalama  
 Kılavuzun bu bölümü eski yakalama yöntemini kullanan DirectX 11.1 API kullanan uygulamalar ve önceki sürümler için Windows 8.0 programlı yakalama gösterir. Windows 8.1 üzerinde DirectX 11.2 kullanan uygulamaları programlı yakalama kullanma hakkında daha fazla bilgi için bkz. [programlama yakalama Windows 8.1](#CaptureDX11_2) bu kılavuzda önceki.  
  
 Bu bölüm, bu görevleri gösterir:  
  
-   Bilgisayarınızı programlı yakalama kullanmak üzere hazırlama  
  
-   Programlı yakalama kullanmak için uygulamanızı hazırlama  
  
-   Grafik günlük dosyasının konumunu ve adını yapılandırma  
  
-   Kullanarak `CaptureCurrentFrame` API  
  
### <a name="preparing-your-computer-to-use-programmatic-capture"></a>Bilgisayarınızı programlı yakalama kullanmak üzere hazırlama  
 Programlı yakalama bir API için Uzak Araçlar kullanan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Yakalama işlevselliği sağlamak için. Uygulamanın çalışacağı bilgisayarda Uzak araçları bile yerel bilgisayarınızda programlı yakalama kullanırken, yüklü olması gerekir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] programlı yakalama yerel bir bilgisayara gerçekleştirdiğinizde çalıştırılması gerekmez.  
  
 Bir bilgisayar üzerinde çalışan bir uygulamada uzaktan yakalama API'leri kullanmak için öncelikle için Uzak Araçlar'ı yüklemek olması [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bu bilgisayarda. Uzak Araçlar'ın farklı sürümleri, farklı donanım platformları destekler. Uzak araçların nasıl yükleneceği hakkında daha fazla bilgi için bkz. [uzak araçları indirme sayfasına](http://go.microsoft.com/fwlink/p/?LinkId=246691) Microsoft Web sitesi indirir.  
  
 Alternatif olarak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 32-bit uygulamalar için uzaktan yakalama gerçekleştirmek için gerekli bileşenleri yükler.  
  
> [!NOTE]
>  Çünkü çoğu Windows Masaüstü uygulamaları — dahil olmak üzere [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]— desteklenmez [!INCLUDE[win8](../includes/win8-md.md)] cihazlarda ARM için Uzak araçlar kullanarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] programlı yakalama ile birlikte tek yolu ARM cihazlarda grafik tanılama yakalama API'dir.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Programlı yakalama kullanmak için uygulamanızı hazırlama  
 Grafik tanılama araçlarını kullanmak için öncelikle kullanır grafik bilgilerini yakalama olması. Program aracılığıyla kullanarak bilgileri yakalayabilirsiniz `CaptureCurrentFrame` API.  
  
##### <a name="to-prepare-your-app-to-capture-graphics-information-programmatically"></a>Grafik bilgilerini programla yakalama için uygulamanızı hazırlamak için  
  
1.  Emin olun `vsgcapture.h` üstbilgi uygulama kaynak kodunu dahil edilir. Yalnızca tek bir yerde bulunan — Örneğin, API kaynak kodu dosyasında çağırdığınız programlı yakalama — veya kod dosyaları birden çok kaynaktan API'sini çağırmak için önceden derlenmiş üst bilgi dosyası.  
  
2.  Geçerli çerçevenin geri kalanında yakalamak istediğiniz her uygulama için kaynak kodu çağırın `g_pVsgDbg->CaptureCurrentFrame()`. Bu yöntem parametre almaz ve bir değer döndürmüyor.  
  
### <a name="configuring-the-name-and-location-of-the-graphics-log-file"></a>Grafik günlük dosyasının konumunu ve adını yapılandırma  
 Grafik günlüğü tarafından tanımlanan konumda oluşturulur `DONT_SAVE_VSGLOG_TO_TEMP` ve `VSG_DEFAULT_RUN_FILENAME` makroları.  
  
##### <a name="to-configure-the-name-and-location-of-the-graphics-log-file"></a>Grafik günlük dosyasının konumunu ve adını yapılandırmak için  
  
- Grafik günlüğü temp dizinine yazılır önce önlemek için `#include <vsgcapture.h>` satır, bunu ekleyin:  
  
  ```  
  #define DONT_SAVE_VSGLOG_TO_TEMP  
  ```  
  
   Çalışma dizinine göreli bir konum veya mutlak bir yol için grafik günlüğüne yazmak için bu değeri tanımlayabilirsiniz, tanımını `VSG_DEFAULT_RUN_FILENAME` mutlak yoldur.  
  
- Grafik günlüğü farklı bir konuma kaydedin veya farklı bir dosya adı, önce vermek için `#include <vsgcapture.h>` satır, bunu ekleyin:  
  
  ```  
  #define VSG_DEFAULT_RUN_FILENAME <filename>  
  ```  
  
   Bu adım gerçekleştirme, dosya default.vsglog adıdır. Siz tanımlarsanız `DONT_SAVE_VSGLOG_TO_TEMP`, ardından dosyasının konumunu geçici dizine göre; mutlak dosya adı belirtilmişse Aksi takdirde, çalışma dizinine göre veya başka bir konumda.  
  
  İçin [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaları, geçici dizin konumunu her kullanıcı ve uygulamanın özgüdür ve genellikle C:\users gibi bir konumda bulunan\\*kullanıcıadı*\AppData\Local\Packages\\ *paket ailesi adı*\TempState\\. Masaüstü uygulamaları için geçici dizin konumunu her kullanıcı için özeldir ve genellikle C:\Users gibi bir konumda bulunan\\*kullanıcıadı*\AppData\Local\Temp\\.  
  
> [!NOTE]
>  Belirli bir konuma yazmak için bu konuma yazma izniniz olması gerekir; Aksi takdirde hata oluşur. Aklınızda [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaları, Masaüstü uygulamaları, veri yazabilirsiniz ve burada belirli konumlara yazma için ek yapılandırma gerektirebilir hakkında daha fazla kısıtlanmış.  
  
### <a name="capturing-the-graphics-information"></a>Grafik bilgilerini yakalama  
 Sonra uygulamayı programlı yakalama için hazırlanmış ve isteğe bağlı olarak yapılandırılmış grafik adını ve konumunu günlük dosyası, uygulama derleme ve ardından çalıştırın veya bu verileri yakalamak için hata ayıklama; Grafik Tanılama'ya başlatmayın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] programlı yakalama API kullandığınızda. Grafik günlüğü, belirttiğiniz konuma yazılır. Bu günlük sürümünü kullanmaya devam etmek istiyorsanız, başka bir konuma taşıyın; Aksi takdirde, uygulamayı yeniden çalıştırdığınızda yazılır.  
  
> [!TIP]
>  Programlı yakalama kullanırken, yine de grafik bilgilerini elle yakalayabilir — odak uygulamayla tuşuna basarak **Print Screen**. Programlı yakalama API tarafından yakalanmaz ek grafik bilgilerini yakalamak için bu tekniği kullanabilirsiniz.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu izlenecek yol, grafik bilgilerini programla yakalama gösterilmiştir. Sonraki adım olarak, bu seçenek göz önünde bulundurun:  
  
-   Grafik tanılama araçlarını kullanarak, yakalanan grafik bilgileri analiz etmeyi öğrenin. Bkz: [genel bakış](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Grafik bilgilerini yakalama](../debugger/walkthrough-capturing-graphics-information.md)   
 [Grafik bilgilerini yakalama](../debugger/capturing-graphics-information.md)   
 [Komut satırı Yakalama Aracı](../debugger/command-line-capture-tool.md)



