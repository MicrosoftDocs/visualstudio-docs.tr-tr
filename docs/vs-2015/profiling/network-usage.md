---
title: Ağ kullanımı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3dd68bec55b53d1b4618e8ae1679603577daf295
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726842"
---
# <a name="network-usage"></a>Ağ kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio **ağ** Tanılama aracını kullanarak gerçekleştirilen ağ işlemleri hakkındaki verileri toplar [Windows.Web.Http API](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx). Verileri çözümleme, erişim ve kimlik doğrulaması ile ilgili sorunlar, yanlış önbellek kullanımı ve görüntü gibi sorunları çözmek ve indirme performansını yardımcı olabilir.  
  
 Ağ aracına yalnızca evrensel Windows platformu uygulamaları destekler. Diğer platformlar, şu anda desteklenmiyor.  
  
> [!NOTE]
>  Ağ aracına daha eksiksiz bir açıklaması için bkz. [Karşınızda Visual Studio'nun Ağ aracı](http://blogs.msdn.com/b/visualstudio/archive/2015/05/04/introducing-visual-studio-s-network-tool.aspx).  
  
## <a name="collecting-network-tool-data"></a>Ağ aracı verileri toplama  
 Çalıştırmalısınız **ağ** aracı ile Visual Studio bilgisayarda açık bir Visual Studio projesi.  
  
1. Projeyi Visual Studio'da açın.  
  
2. Menüsünde **hata ayıklama / performans Profiler...** . Seçin **ağ**ve ardından **Başlat**.  
  
3. Ağ aracına, uygulamanızın HTTP trafiğini toplamaya başlar.  
  
    Uygulamanızı çalıştırma gibi Özet görünümü sol bölmesinde otomatik olarak yakalanan HTTP işlemlerini listesini görüntüler. Özet görünümünde ayrıntılar bölmesini sağ bölmede, daha fazla bilgi görmek için bir öğe seçin.  
  
4. Seçin **Durdur** uygulamayı kapatmak için.  
  
   Rapor penceresini aşağıdaki gibi görünmelidir:  
  
   ![Ağ pencerenin](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Verileri çözümleme  
 Uygulamanız çalışırken veya bile uygulama, Özet görünümünde görüntülenen ağ işlemlerden birini seçerek kapatıldıktan sonra yakalanan HTTP trafiği analiz edebilirsiniz.  
  
 **Ağ** Özet görünümü, uygulamanızın çalıştırmada her ağ işlemi için verileri gösterilir. Listeyi sıralamak için sütun başlığını seçin ya da görüntülemek için içerik türlerini seçin **içerik türü** filtre görünümü.  
  
 Seçin **HAR olarak Kaydet** Fiddler gibi üçüncü taraf araçları tarafından tüketilebilecek bir JSON dosyası oluşturmak için.  
  
 **Ağ** ayrıntıları görünümlerini Özet görünümünde ağ işlemi hakkında daha fazla bilgi görüntüler.  
  
 ![Ağ aracı ayrıntıları bölmesinde](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|||  
|-|-|  
|**Üst bilgileri**|İstek üst bilgilerini ilgili olay bilgileri.|  
|**Gövde**|İstek ve yanıt yük verisi.|  
|**Parametreler**|Sorgu dizesi parametresi adları ve değerleri.|  
|**Çerezler**|Yanıt ve istek tanımlama bilgisi verisi.|  
|**Zamanlamaları**|Bir grafik, seçilen kaynaklar alınıyor aşamaları.|  
  
 Ağ **Özet** çubuğu gösterir ne kadar verinin aktarıldığı, belirli bir anda, görüntülenen ağ işlemlerinin sayısı ne kadar süre geçtiğini bunları ve kaç hatalar (istek yanıt veren 4xx veya 5xx) indirmek için görünür.  
  
### <a name="analysis-tips"></a>Çözümleme ipuçları  
 Bu aracı vurgular çalıştırırken, faydalı olabilecek bazı alanlarını ağ analiz ilgili:  
  
1.  Önbellekten tam olarak sunulan istekleri olarak gösterilen **(önbellekten)** içinde **alınan** sütun. Bu, önbelleğin etkili bir şekilde kullanıcı bant genişliğinden tasarruf etmek kullanmanıza veya yanlışlıkla yanıtları önbelleğe alma ve güncel olmayan verileri ile uygulamanızın son kullanıcı sağlama belirlemenize yardımcı olabilir.  
  
2.  Hata yanıtları (4xx veya 5xx) görüntülenir, **sonuçları** kırmızı bir duruma sahip sütun kod ve Özet çubuğunda ayrıca vurgulanır. Bu, birçok olası istekler arasında kolay nokta hataları uygulamanızı sağlar.  
  
3.  Yanıt düzgün yazdırmada düğme (içinde gövde sekmesi) JSON, XML, HTML, CSS, JavaScript ve TypeScript yanıt yükleri içeriğin okunabilirliği artırarak ayrıştırmanıza yardımcı olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama olmadan profil oluşturma araçları çalıştırma](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Visual Studio blogu: Karşınızda Visual Studio'nun ağ denetçisi](http://go.microsoft.com/fwlink/?LinkId=535022)   
 [Kanal 9 Video: VS tanılama araçları-yeni ağ Profiler](http://channel9.msdn.com/Series/ConnectOn-Demand/206)



