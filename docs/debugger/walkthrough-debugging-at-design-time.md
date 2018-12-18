---
title: Tasarım zamanında hata ayıklama | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9c4b0996faf26279ff8018e0e072fd25a33d783
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063428"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio'da tasarım zamanında hata ayıklama (C#, C++, Visual Basic F#)

Tasarım zamanında yerine uygulama çalışırken kodda hata ayıklamak için çalışıyor, kullanabileceğiniz **hemen** penceresi. 

Veri bağlama kodunu gibi XAML Tasarımcısı'ndan bir uygulama arka plan XAML kod hatalarını ayıklamak için kullanabileceğiniz **hata ayıklama** > **iliştirme**.
  
## <a name="use-the-immediate-window"></a>Komut penceresi kullanın  

Visual Studio kullanabileceğiniz **hemen** uygulamanızı çalıştırmadan bir işlev veya alt yordamı yürütmek için penceresi. İşlev veya alt yordam bir kesme noktası içeriyorsa, Visual Studio kesme noktasında çalışmamasına neden olur. Ardından, programınızın durumunu incelemek için hata ayıklayıcı penceresini kullanabilirsiniz. Bu özelliğin adı *tasarım zamanında hata ayıklama*.  

Aşağıdaki örnek, Visual Basic'te. Ayrıca **hemen** tasarım zamanında penceresi C#, F#ve C++ uygulamaları.

1. Boş bir Visual Basic konsol uygulamasına aşağıdaki kodu yapıştırın:  
   
   ```vb  
   Module Module1
   
       Sub Main()
           MySub()
       End Sub
   
       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function
   
       Sub MySub()
           MyFunction()
   
       End Sub
   End Module
   ```  
   
1. Satırına bir kesme noktası ayarlamak **End işlevi**.  
   
1. Açık **hemen** penceresini seçerek **hata ayıklama** > **Windows** > **hemen**. Tür `?MyFunction` penceresi ve ENTER tuşuna **Enter**.   
   
   Kesme noktası isabet ve değeri olan **MyFunction** içinde **Yereller** penceresi **1**. Uygulama kesme modunda çalışırken, çağrı yığını ve diğer hata ayıklama windows inceleyebilirsiniz. 
   
1. Seçin **devam** Visual Studio araç. Uygulamanın sona erer ve **1** döndürülür **hemen** penceresi. Yine de tasarım modunda olduğundan emin olun.  
   
1. Tür `?MyFunction` içinde **hemen** penceresini tekrar ve tuşuna **Enter**. Kesme noktası isabet ve değeri olan **MyFunction** içinde **Yereller** penceresi **2**. 
   
1. Seçmeden **devam**, türü `?MySub()` içinde **hemen** penceresi ve ENTER tuşuna **Enter**. Kesme noktası isabet ve değeri olan **MyFunction** içinde **Yereller** penceresi **3**. Uygulama kesme modundayken, uygulama durumunu inceleyebilirsiniz. 
   
1. Seçin **devam**. Kesme noktası isabet yeniden ve değeri olan **MyFunction** içinde **Yereller** penceresi, artık **2**. **Hemen** pencereyi döndürür **ifade değerlendirildi ve değeri**.
   
1. Seçin **devam** yeniden. Uygulamanın sona erer ve **2** döndürülür **hemen** penceresi. Yine de tasarım modunda olduğundan emin olun.
   
1. İçeriğini temizlemek için **hemen** penceresi, pencere seçip sağ **Tümünü Temizle**. 

## <a name="attach-to-an-app-from-the-xaml-designer"></a>XAML Tasarımcısı'ndan bir uygulamaya ekleme

Bazı bildirim temelli veri bağlama senaryoları, XAML Tasarımcısı'nda arkasındaki kodda hata ayıklamak için yardımcı olur.

1. Visual Studio projesinde yeni bir XAML sayfası gibi ekleyin *temp.xaml*. Yeni XAML sayfası boş bırakın. 
   
1. Çözümü oluşturun.
   
1. Açık *temp.xaml*, XAML Tasarımcısı yükler *XDesProc.exe*, veya *UwpSurface.exe* bir UWP uygulamasında. 
   
1. Visual Studio'nun yeni bir örneğini açın. Yeni örnekte seçin **hata ayıklama** > **iliştirme**. 
   
1. İçinde **iliştirme** Tasarımcı işlem gelen iletişim kutusunda **kullanılabilir işlemler** listesi.
   
   UWP için Windows hedefleyen projeleri 16299 derleme veya üstü, Tasarımcı işlemi *UwpSurface.exe*. Önceki 16299 WPF veya UWP sürümleri için tasarımcı işlemidir *XDesProc.exe*.
   
1. Emin **ekleme** ayarlanmış .NET sürümünüz için doğru kod türü gibi **yönetilen kod (CoreCLR)**. 
   
1. Seçin **ekleme**.
   
1. İşleme bağlı olsa da diğer Visual Studio örneğine geçin ve uygulamanızın arkasındaki kodda hata ayıklamak istediğiniz kesme noktaları ayarlayın.
   
   Örneğin, tasarım zamanında bir TextBlock bağlar aşağıdaki XAML için tür dönüştürücüsü kodda bir kesme noktası ayarlayabilirsiniz.
   
    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Sayfa yüklendiğinde, kesme noktasına ulaşılır.
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Hata ayıklayıcısı temel bilgileri](../debugger/getting-started-with-the-debugger.md)
