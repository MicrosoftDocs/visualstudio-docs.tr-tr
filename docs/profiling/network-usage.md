---
title: UWP uygulamalarında ağ kullanımını analiz etme
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06546e3d36e0568c27e4160342ad271a026b7b9e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062250"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>UWP uygulamalarında ağ kullanımını analiz etme
Visual Studio **ağ** Tanılama aracını kullanarak gerçekleştirilen ağ işlemleri hakkındaki verileri toplar [Windows.Web.Http API](/uwp/api/windows.web.http). Verileri çözümleme, erişim ve kimlik doğrulaması ile ilgili sorunlar, yanlış önbellek kullanımı ve görüntü gibi sorunları çözmek ve indirme performansını yardımcı olabilir.  
  
 Ağ aracına yalnızca UWP uygulamaları destekler. Diğer platformlar, şu anda desteklenmiyor.  
  
> [!NOTE]
>  Ağ aracına daha eksiksiz bir açıklaması için bkz. [Karşınızda Visual Studio'nun Ağ aracı](https://blogs.msdn.microsoft.com/visualstudio/2015/05/04/introducing-visual-studios-network-tool/).  
  
## <a name="collect-network-tool-data"></a>Ağ aracı verilerini topla  
 Çalıştırmalısınız **ağ** aracı ile Visual Studio bilgisayarda açık bir Visual Studio projesi.  
  
1. Projeyi Visual Studio'da açın.  
  
2. Menüsünde **hata ayıklama / performans Profiler**. Seçin **ağ**ve ardından **Başlat**.  
  
3. Ağ aracına, uygulamanızın HTTP trafiğini toplamaya başlar.  
  
    Uygulamanızı çalıştırma gibi Özet görünümü sol bölmesinde otomatik olarak yakalanan HTTP işlemlerini listesini görüntüler. Özet görünümünde ayrıntılar bölmesini sağ bölmede, daha fazla bilgi görmek için bir öğe seçin.  
  
4. Seçin **Durdur** uygulamayı kapatmak için.  
  
   Rapor penceresini aşağıdaki gibi görünmelidir:  
  
   ![Ağ pencerenin](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyze-data"></a>Verileri analiz etme  
 Uygulamanız çalışırken veya bile uygulama, Özet görünümünde görüntülenen ağ işlemlerden birini seçerek kapatıldıktan sonra yakalanan HTTP trafiği analiz edebilirsiniz.  
  
 **Ağ** Özet görünümü, uygulamanızın çalıştırmada her ağ işlemi için verileri gösterilir. Listeyi sıralamak için sütun başlığını seçin ya da görüntülemek için içerik türlerini seçin **içerik türü** filtre görünümü.  
  
 Seçin **HAR olarak Kaydet** Fiddler gibi üçüncü taraf araçları tarafından tüketilebilecek bir JSON dosyası oluşturmak için.  
  
 **Ağ** ayrıntıları görünümlerini Özet görünümünde ağ işlemi hakkında daha fazla bilgi görüntüler.  
  
 ![Ağ aracı ayrıntıları bölmesinde](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|||  
|-|-|  
|**Üst bilgileri**|İstek üst bilgilerini ilgili olay bilgileri.|  
|**Gövde**|İstek ve yanıt yük verisi.|  
|**Parametreler**|Sorgu dizesi parametresi adları ve değerleri.|  
|**Çerezler**|Yanıt ve istek tanımlama bilgisi verisi.|  
|**Zamanlamaları**|Bir grafik, seçilen kaynaklar alınıyor aşamaları.|  
  
 Ağ **Özet** çubuğu gösterir ne kadar verinin aktarıldığı, belirli bir anda, görüntülenen ağ işlemlerinin sayısı ne kadar süre geçtiğini bunları ve kaç hatalar (istek yanıt veren 4xx veya 5xx) indirmek için görünür.  
  
### <a name="analysis-tips"></a>Çözümleme ipuçları  
 Bu araç, ağla ilgili analizi çalıştırırken, yararlı olabilecek bazı alanları vurgular:  
  
1.  Önbellekten tam olarak sunulan istekleri olarak gösterilen **(önbellekten)** içinde **alınan** sütun. Bu, önbelleğin etkili bir şekilde kullanıcı bant genişliğinden tasarruf etmek kullanmanıza veya yanlışlıkla yanıtları önbelleğe alma ve güncel olmayan verileri ile uygulamanızın son kullanıcı sağlama belirlemenize yardımcı olabilir.  
  
2.  Hata yanıtları (4xx veya 5xx) görüntülenir **sonuçları** kırmızı bir duruma sahip sütun kod ve Özet çubuğunda ayrıca vurgulanır. Bu, birçok olası istekler arasında kolay nokta hataları uygulamanızı sağlar.  
  
3.  Yanıt düzgün yazdırmada düğme (içinde gövde sekmesi) JSON, XML, HTML, CSS, JavaScript ve TypeScript yanıt yükleri içeriğin okunabilirliği artırarak ayrıştırmanıza yardımcı olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçları çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md)  
 [Visual Studio blogu: Karşınızda Visual Studio'nun ağ denetçisi](http://go.microsoft.com/fwlink/?LinkId=535022)   
 [Kanal 9 Video: VS tanılama araçları - yeni ağ Profiler](https://channel9.msdn.com/Series/ConnectOn-Demand/206)  
 [Visual Studio profil oluşturma](../profiling/index.md)  
 [Araçlar profil oluşturmaya ilk bakış](../profiling/profiling-feature-tour.md)
