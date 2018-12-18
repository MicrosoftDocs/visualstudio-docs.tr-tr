---
title: "İzlenecek yol: IntelliTrace'i kullanma | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc1e2b40e16a14da505243aeb11542df3adfb18d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781315"
---
# <a name="walkthrough-using-intellitrace"></a>İnceleme: IntelliTrace’i Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ayrı ayrı işlev çağrıları veya belirli olayları ya da olayların kategorilerini hakkında bilgi, ayrıca olayları toplamak için IntelliTrace'i kullanabilirsiniz. Aşağıdaki yordamlar, bunun nasıl yapılacağını gösterir.  
  
 IntelliTrace, Visual Studio Enterprise edition (ancak Professional veya Community sürümlerini değil) kullanabilirsiniz.  
  
##  <a name="GettingStarted"></a> IntelliTrace olayları ile kullanma  
 Yalnızca IntelliTrace olayları ile hata ayıklama deneyebilirsiniz. IntelliTrace olayları hata ayıklayıcı olayları, özel durumlar, .NET Framework olayları ve diğer sistem olaylarıdır ' dir. Açın veya hatalarını ayıklamaya başlamadan önce Intellitrace'in kaydettiği olayları kontrol belirli olayları açmak. Daha fazla bilgi için [IntelliTrace özellikleri](../debugger/intellitrace-features.md).  
  
 Aşağıdaki adımlar, yalnızca IntelliTrace olayları ile hata ayıklama işlemini gösterir:  
  
1.  Dosya erişimi için IntelliTrace olayı kapatın. Git **Araçlar / Seçenekler / IntelliTrace / IntelliTrace olayları** sayfasında ve genişletin **dosya** kategorisi. Denetleme **dosya** olay kategorisi. Bu, Kontrol edilecek tüm dosya olayları (erişim, Kapat, silme) neden olur.  
  
2.  Bir C# konsol uygulaması oluşturun. Program.cs dosyasında, aşağıdaki ekleyin `using` deyimi:  
  
    ```csharp  
    using System.IO;  
    ```  
  
3.  Oluşturma bir <xref:System.IO.FileStream> ana yöntemde, kendisinden okuma kapatın ve dosyayı silin. Yalnızca bir kesme noktası ayarlamak için bir yer olması için başka bir satır ekleyin:  
  
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
  
4.  Bir kesme noktası ayarlayın `Console.WriteLine("done");`  
  
5.  Zamanki gibi hata ayıklamaya başlayın. (Tuşuna **F5** veya **hata ayıklama / hata ayıklamayı Başlat**.  
  
    > [!TIP]
    >  Tutun **Yereller** ve **Otolar** windows görmek ve bu pencerelerde değerlerini kaydetmek için hata ayıklarken açın.  
  
6.  Yürütme kesme noktasında durur. Görmüyorsanız, **tanılama araçları** penceresinde tıklayın **hata ayıklama / Windows / IntelliTrace olayları**.  
  
     İçinde **tanılama araçları** penceresinde Bul **olayları** sekme (3 sekme görmeniz gerekir **olayları**, **bellek kullanımı**, ve **CPU Kullanım**). **Olayları** sekmesi, olaylar, hata ayıklayıcı yürütmeyi kesmeden son olay ile biten kronolojik bir listesini gösterir. Adlı bir olay görmelisiniz **erişim WordSearchInputs.txt**.  
  
     Aşağıdaki ekran görüntüsünde, Visual Studio 2015 güncelleştirme 1 ' dir.  
  
     ![IntelliTrace&#45;güncelleştirme 1](../debugger/media/intellitrace-update1.png "IntelliTrace-güncelleştirme 1")  
  
7.  Ayrıntılarını genişletmek için olayı seçin.  
  
     Aşağıdaki ekran görüntüsünde, Visual Studio 2015 güncelleştirme 1 ' dir.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1 SingleEvent")  
  
     Dosyayı açmak için yol adı bağlantısını seçebilirsiniz. Tam yol adı kullanılabilir değilse, **açık dosya** iletişim kutusu görüntülenir.  
  
     Tıklayın **etkinleştirmek geçmiş hata ayıklama**, hangi ayarlar Hata Ayıklayıcı'nın bağlam seçili olay ne zaman zaman toplanan, gösteren geçmiş verileri **çağrı yığını**, **Yereller** ve diğer windows hata ayıklayıcı katılan. Kaynak kodu varsa, incelemeniz Visual Studio işaretçiyi kaynak penceresinde karşılık gelen koda taşır.  
  
     Aşağıdaki ekran görüntüsünde, Visual Studio 2015 güncelleştirme 1 ' dir.  
  
     ![HistoricalDebugging&#45;güncelleştirme 1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-güncelleştirme 1")  
  
8.  Hatayı bulamadıysanız, hataya diğer olayları İnceleme deneyin. İşlev çağrılarında gezinebilirsiniz girmek, IntelliTrace çağrı bilgileri kaydetmesini sağlayabilirsiniz.  
  
## <a name="using-intellitrace-with-events-and-function-calls"></a>IntelliTrace olayları ve işlev çağrıları ile kullanma  
 IntelliTrace işlev çağrılarını olaylarla birlikte kaydedebilir. Bu, çağrı yığını geçmişini görmenizi ve kodunuzdaki çağrılar arasında ileri geri adım sağlar. IntelliTrace işlev adlarını, işlev giriş ve çıkış noktaları ve belirli parametre değerleri ve dönüş değerleri gibi verileri kaydeder. Bkz: [IntelliTrace özellikleri](../debugger/intellitrace-features.md).  
  
1.  Çağrı koleksiyonunu açın. (Üzerinde **Araçlar / Seçenekler / IntelliTrace / genel**seçin **IntelliTrace olayları ve çağrı bilgileri**. IntelliTrace sonraki hata ayıklama oturumu başladığında bu bilgileri toplamaya başlar.  
  
    > [!TIP]
    >  Bu sizin uygulamanızı yavaşlatabilir ve diske kaydettiğiniz herhangi IntelliTrace günlük dosyasının (.iTrace dosyaları) boyutunu artırın. Çoğu arama verilerini almak ancak etkilerini en aza indirmek için ilginizi çeken modüllerden veri kaydedin. .İTrace dosyalarınızın en büyük boyutunu değiştirmek için Git **Araçlar / Seçenekler / IntelliTrace / Gelişmiş**ve en fazla disk alanı miktarını belirtin. Varsayılan değer 250 MB ' dir.  
  
2.  C# konsol uygulaması önceki bölümde oluşturduğunuz hatalarını ayıklamaya başlayın. Yürütme kesme noktasında durur. Görmüyorsanız, **tanılama araçları** penceresinde tıklayın **hata ayıklama / Windows / IntelliTrace olayları**.  
  
3.  Geçiş **çağrıları** sekmesi.  
  
     Uygulamanızın işlev çağrıları görmek şimdi kök çağrısında (geçerli çözümü, ana giriş noktası) ile başlayan ve hangi yürütme konumu ile biten kesildi.  
  
     İşlev çağrıları birini seçin ve çift tıklayın. İşlev giriş ve çıkış noktaları yanı sıra geçerli çağrının diğer işlevlere ve çağrı tarafından tetiklenen IntelliTrace olayları için yapılan çağrıları görmeniz gerekir. Açık geçmiş hata ayıklama yoksa, bu eylem, açar. Geçmiş hata ayıklama hakkında daha fazla bilgi için bkz: [geçmiş hata ayıklama](../debugger/historical-debugging.md).  
  
    > [!NOTE]
    >  Bazı çağrıları soluklaştırılır görebilirsiniz. IntelliTrace karşılık gelen modüllerden veri kaydetmediği için budur. Bu verileri görmek için bu modüllerden veri toplamak IntelliTrace sahip. Modüller belirtme hakkında daha fazla bilgi için bkz: [IntelliTrace özellikleri](../debugger/intellitrace-features.md).  
  
## <a name="next-steps"></a>Sonraki Adımlar






