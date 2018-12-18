---
title: IntelliTrace ile olayları görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46113365b66a75d3f9e149181637c79068645ab
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542331"
---
# <a name="view-events-with-intellitrace-in-visual-studio"></a>Visual Studio'da IntelliTrace ile olayları görüntüleme
Ayrı ayrı işlev çağrıları veya belirli olayları ya da olayların kategorilerini hakkında bilgi, ayrıca olayları toplamak için IntelliTrace'i kullanabilirsiniz. Aşağıdaki yordamlar, bunun nasıl yapılacağını gösterir.  
  
 IntelliTrace, Visual Studio Enterprise sürümünde, ancak değil Professional veya Community sürümlerini kullanabilirsiniz.  
  
##  <a name="GettingStarted"></a> IntelliTrace yapılandırma  
 Yalnızca IntelliTrace olayları ile hata ayıklama deneyebilirsiniz. IntelliTrace olayları hata ayıklayıcı olayları, özel durumlar, .NET Framework olayları ve diğer sistem olaylarıdır ' dir. Açın veya hatalarını ayıklamaya başlamadan önce Intellitrace'in kaydettiği olayları kontrol belirli olayları açmak. Daha fazla bilgi için [IntelliTrace özellikleri](../debugger/intellitrace-features.md).  
  
 - Dosya erişimi için IntelliTrace olayı kapatın. Git **Araçlar > Seçenekler > IntelliTrace > IntelliTrace olayları** sayfasında ve genişletin **dosya** kategorisi. Denetleme **dosya** olay kategorisi. Bu, Kontrol edilecek tüm dosya olayları (erişim, Kapat, silme) neden olur.

## <a name="create-your-app"></a>Uygulamanızı oluşturma
  
1.  Bir C# konsol uygulaması oluşturun. Program.cs dosyasında, aşağıdaki ekleyin `using` deyimi:  
  
    ```csharp  
    using System.IO;  
    ```  
  
2.  Oluşturma bir <xref:System.IO.FileStream> ana yöntemde, kendisinden okuma kapatın ve dosyayı silin. Yalnızca bir kesme noktası ayarlamak için bir yer olması için başka bir satır ekleyin:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        FileStream fs = File.Create("WordSearchInputs.txt");  
        fs.ReadByte();  
        fs.Close();  
        File.Delete("WordSearchInputs.txt");  
  
        Console.WriteLine("done");  
    }  
    ```  
  
3.  Bir kesme noktası ayarlayın `Console.WriteLine("done");`  

## <a name="start-debugging-and-view-intellitrace-events"></a>Hata ayıklamayı başlatmak ve IntelliTrace olaylarını görüntüleme
  
1.  Zamanki gibi hata ayıklamaya başlayın. (Tuşuna **F5** veya **hata ayıklama > hata ayıklamayı Başlat**.  
  
    > [!TIP]
    >  Tutun **Yereller** ve **Otolar** windows görmek ve bu pencerelerde değerlerini kaydetmek için hata ayıklarken açın.  
  
2.  Yürütme kesme noktasında durur. Görmüyorsanız, **tanılama araçları** penceresinde tıklayın **hata ayıklama > Windows > IntelliTrace olayları**.  
  
     İçinde **tanılama araçları** penceresinde Bul **olayları** sekme (3 sekme görmeniz gerekir **olayları**, **bellek kullanımı**, ve **CPU Kullanım**). **Olayları** sekmesi, olaylar, hata ayıklayıcı yürütmeyi kesmeden son olay ile biten kronolojik bir listesini gösterir. Adlı bir olay görmelisiniz **erişim WordSearchInputs.txt**.  
  
     Aşağıdaki ekran görüntüsünde, Visual Studio 2015 güncelleştirme 1 ' dir.  
  
     ![IntelliTrace&#45;güncelleştirme 1](../debugger/media/intellitrace-update1.png "IntelliTrace-güncelleştirme 1")  
  
3.  Ayrıntılarını genişletmek için olayı seçin.  
  
     Aşağıdaki ekran görüntüsünde, Visual Studio 2015 güncelleştirme 1 ' dir.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1 SingleEvent")  
  
     Dosyayı açmak için yol adı bağlantısını seçebilirsiniz. Tam yol adı kullanılabilir değilse, **açık dosya** iletişim kutusu görüntülenir.  
  
     Tıklayın **etkinleştirmek geçmiş hata ayıklama**, hangi ayarlar Hata Ayıklayıcı'nın bağlam seçili olay ne zaman zaman toplanan, gösteren geçmiş verileri **çağrı yığını**, **Yereller** ve diğer windows hata ayıklayıcı katılan. Kaynak kodu varsa, incelemeniz Visual Studio işaretçiyi kaynak penceresinde karşılık gelen koda taşır.  
  
     Aşağıdaki ekran görüntüsünde, Visual Studio 2015 güncelleştirme 1 ' dir.  
  
     ![HistoricalDebugging&#45;güncelleştirme 1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-güncelleştirme 1")  
  
4.  Hatayı bulamadıysanız, hataya diğer olayları İnceleme deneyin. İşlev çağrılarında gezinebilirsiniz girmek, IntelliTrace çağrı bilgileri kaydetmesini sağlayabilirsiniz. 
  
## <a name="next-steps"></a>Sonraki Adımlar

Bazı gelişmiş özellikleri IntelliTrace geçmiş hata ayıklama ile kullanabilirsiniz:

 - Anlık görüntüleri görüntülemek için bkz: [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md)
 - Değişkenleri incelemek ve koda gitmek öğrenmek için bkz: [geçmiş hata ayıklama ile uygulamanızı denetleyin](../debugger/historical-debugging-inspect-app.md)