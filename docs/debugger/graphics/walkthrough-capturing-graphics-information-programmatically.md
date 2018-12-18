---
title: 'İzlenecek yol: Grafik bilgilerini programla yakalama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 659e370d664b3db2c3624d73164b4489cc2680a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933293"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>İzlenecek Yol: Grafik Bilgilerini Programla Yakalama
Kullanabileceğiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] grafik tanılama Direct3D uygulamadan grafik bilgilerini programla yakalama.  
  
 Programlı yakalama gibi senaryolarda kullanışlıdır:  
  
-   Grafik uygulamanızı swapchain doku için ne zaman işleyen gibi mevcut kullandığınızda değil yakalama programlı bir şekilde başlayın.  
  
-   Uygulamanızı, ne zaman DirectCompute hesaplamalar gerçekleştirmek için kullandığı gibi işlemesi yapmıyor açıldığında yakalama programlı olarak başlatılır.  
  
-   Çağrı `CaptureCurrentFrame`ne zaman bir işleme sorunuyla umuyor ve el ile testte yakalamak zor olduğunda ancak programlı olarak çalışma zamanında uygulamanın durumu hakkındaki bilgileri kullanarak tahmin.  
  
##  <a name="CaptureDX11_2"></a> Windows 10'daki programlı yakalama  
 Kılavuzun bu bölümü, sağlam yakalama yöntemi kullanan Windows 10 üzerinde DirectX 11.2 API kullanan uygulamalarda programlı yakalama gösterir.
  
 Bu bölümde bu görevlerin nasıl yapılacağını gösterir:  
  
-   Programlı yakalama kullanmak için uygulamanızı hazırlama  
  
-   IDXGraphicsAnalysis arabirimi alma  
  
-   Graf bilgilerini yakalama  
  
> [!NOTE]
>  Programlı yakalama önceki uygulamaları için Visual Studio için Uzak Araçlar'yararlandı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Yakalama işlevselliği sağlamak için.
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Programlı yakalama kullanmak için uygulamanızı hazırlama  
 Programlı yakalama uygulamanızda kullanmak için gereken üst bilgileri içermelidir. Bu üst bilgiler Windows 10 SDK'ın bir parçasıdır.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Programlı yakalama üst bilgilerini eklemek için  
  
-   Bu üst kaynak dosyanın IDXGraphicsAnalysis arabirimi burada tanımlayacaksınız şunlardır:  
  
    ```cpp
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Üst bilgi dosyası vsgcapture.h—which destekler programlı yakalama Windows 8.0 ve önceki sürümleri dahil değildir — Windows 10 uygulamalarınızda programlı yakalama gerçekleştirilecek. Bu üstbilginin DirectX 11.2 ile uyumlu değil. D3d11_2.h üst bilgisi dahil olduktan sonra bu dosyayı dahil ise, derleyici bir uyarı verir. Vsgcapture.h d3d11_2.h önce eklediyseniz, uygulamayı başlatılmaz.  
  
    > [!NOTE]
    >  Haziran 2010 DirectX SDK'sı, makinenizde yüklü olduğundan ve projenizin yoluna içeren `%DXSDK_DIR%includex86`, yoluna sonuna taşıyın. Bir kitaplık yolu için de aynısını yapın.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimi alma  
 DirectX 11.2 grafik bilgilerini yakalamak için önce DXGI hata ayıklama arabirimi almak sahip.  
  
> [!IMPORTANT]
>  Programlı yakalama kullanırken, yine de uygulamanızı grafik tanılama altında çalıştırmanız gerekir (Alt + F5 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) veya altında [komut satırı Yakalama aracı](command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimi almak için  
  
- DXGI hata ayıklama arabirimine IDXGraphicsAnalysis arabirimi bağlama için aşağıdaki kodu kullanın.  
  
  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;  
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
  ```  
  
   Kontrol ettiğinizden emin olun `HRESULT` tarafından döndürülen [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) kullanmadan önce geçerli bir arabirim başlamanızı sağlamak için:  
  
  ```cpp
  if (FAILED(getAnalysis))  
  {  
      // Abort program or disable programmatic capture in your app.  
  }  
  ```  
  
  > [!NOTE]
  >  Varsa `DXGIGetDebugInterface1` döndürür `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), uygulamayı grafik tanılama altında çalıştığından emin olun (Alt + F5 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
### <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama  
 Geçerli bir sahip olduğunuza göre `IDXGraphicsAnalysis` kullanabileceğiniz arabirimi `BeginCapture` ve `EndCapture` grafik bilgilerini yakalamak için.  
  
##### <a name="to-capture-graphics-information"></a>Grafik bilgilerini yakalamak için  
  
- Grafik bilgilerini yakalama başlatmak için kullanın `BeginCapture`:  
  
    ```cpp
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Yakalamaya başlar hemen olduğunda `BeginCapture` çağrılır; sonraki kare başlamak beklemez. Geçerli kare sunulduğunda veya çağırdığınızda durakları yakalama `EndCapture`:  
  
    ```cpp
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  

- Çağrısından sonra `EndCapture`, grafik nesnesini serbest bırakın. 
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu izlenecek yol, grafik bilgilerini programla yakalama gösterilmiştir. Sonraki adım olarak, bu seçenek göz önünde bulundurun:  
  
-   Grafik tanılama araçlarını kullanarak, yakalanan grafik bilgileri analiz etmeyi öğrenin. Bkz: [genel bakış](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Grafik bilgilerini yakalama](walkthrough-capturing-graphics-information.md)   
 [Grafik bilgilerini yakalama](capturing-graphics-information.md)   
 [Komut satırı Yakalama Aracı](command-line-capture-tool.md)
