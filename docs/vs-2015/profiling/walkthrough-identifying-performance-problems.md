---
title: 'İzlenecek yol: Performans sorunlarını belirleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 58
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d26e6ccabcdff12b8f4d9839888e17dc1ab3ce4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745363"
---
# <a name="walkthrough-identifying-performance-problems"></a>İzlenecek yol: Performans sorunlarını tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, performans sorunlarını belirlemek için bir uygulamanın profilini gösterilmiştir.  
  
 Bu kılavuzda, yönetilen bir uygulama profili oluşturma ve uygulamada performans sorunlarını belirlemek ve ayırmak için örnekleme ve Araçları'nı kullanarak işlemi adım adım.  
  
 Bu kılavuzda, aşağıdaki adımları izler:  
  
-   Örnekleme yöntemini kullanarak bir uygulama profili.  
  
-   Bir performans sorunu bulup örneklenen profil oluşturma sonuçları analiz edin.  
  
-   Araçlar yöntemini kullanarak bir uygulama profili.  
  
-   Bulmak ve bir performans sorunu gidermek için izleme eklenmiş profil oluşturma sonuçları analiz edin.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
- C# Ara anlama.  
  
- Bir kopyasını [PeopleTrax örneği](../profiling/peopletrax-sample-profiling-tools.md).  
  
  Profil oluşturma tarafından sağlanan bilgiler ile çalışmak için hata ayıklama sembol bilgisi kullanılabilir olması en iyisidir.  
  
## <a name="profiling-by-using-the-sampling-method"></a>Örnekleme yöntemiyle profili oluşturma  
 Örnekleme tarafından söz konusu işlemi düzenli aralıklarla etkin işlev belirlemek için yoklanabileceği bir profil oluşturma yöntemidir. Sonuçta elde edilen veriler işlem örneklendiğinde ne sıklıkta söz konusu işlev çağrı yığının en üstünde olan sayısına sağlar.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak uygulamanın profilini çıkarmak için  
  
1.  Açık [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yönetici ayrıcalıklarına sahip. Bir yönetici olarak, profil oluşturma için gereklidir.  
  
2.  PeopleTrax çözümü açın.  
  
     PeopleTrax çözümü, Çözüm Gezgini artık doldurur.  
  
3.  Proje yapılandırma ayarı **yayın**.  
  
     Bir yayın yapısı, uygulamanızda performans sorunlarını algılamak için kullanmanız gerekir. Yayın derlemesi profil oluşturma, hata ayıklama derlemesi performansı olumsuz etkileyebilir ve performans sorunlarını doğru bir şekilde açıklamak değildir içine derlenmiş ek bilgilere sahip olduğu için önerilir.  
  
4.  Üzerinde **Çözümle** menüsünü tıklatın **performans Sihirbazını Başlat**.  
  
     Performans Sihirbazı görünür.  
  
5.  Emin **CPU örnekleme (önerilir)** seçilir ve ardından **sonraki**.  
  
6.  İçinde **hangi uygulamanın profilini oluşturmak için hedeflemek istiyorsunuz**PeopleTrax seçin ve ardından **sonraki**.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Projeyi oluşturur ve uygulamanın profilini başlar. **PeopleTrax** uygulama penceresi görünür.  
  
7.  Tıklayın **kişileri Al**.  
  
8.  Tıklayın **ExportData**.  
  
     Notepad açılır ve dışarı aktarılan verileri içeren yeni bir dosya görüntüler **PeopleTrax**.  
  
9. Not Defteri'ni kapatın ve ardından kapatın **PeopleTrax** uygulama.  
  
     Profil Oluşturucu profil oluşturma verilerini oluşturur (\*.vsp) dosyasının dosya adı performans Gezgini penceresi Raporlar bölümünde listeler ve otomatik olarak yükler **özeti** anapencereninveridosyasındagörünümünü[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-analyze-sampled-profiling-results"></a>Çözümlemek için profil oluşturma sonuçlarının örneklenir  
  
1.  Özet görünümü, CPU kullanımı bir zaman çizelgesi profil oluşturma çalıştırmasını kursunda görüntüler **etkin yolu** en aktif olan uygulamanın çağrı ağacının dalını temsil eden bir listesi ve listesini  **En bireysel işleri yapan işlevler** en yoğun bir şekilde kendi işlev gövdesinde kod yürütürken örneklenen işlevleri gösterir.  
  
     İnceleme **etkin yolu** listelemek ve PeopleNS.People.GetNames yöntemi PeopleTrax işlevi listenin sonuna yakın olduğuna dikkat edin. Konumuna analiz için iyi bir adaydır kolaylaştırır. GetNames ayrıntılarını görüntülemek için işlevin adını tıklayarak **işlev ayrıntıları** görünümü.  
  
2.  **İşlev ayrıntıları** iki windows görünümü içerir. Maliyet dağıtımı penceresi çalışmanın işlevi tarafından çağrıldığında fonksiyonların çalışmanın ve örneklenen örneklerinin işleve çağıran işlevler katkısını grafik bir görünümünü sağlar. Görünümün odağını bir işlev adına tıklayarak, işlev değiştirebilirsiniz. Örneğin, GetPeople seçili işlev yapmak PeopleNS.People.GetPeople tıklayabilirsiniz.  
  
     **İşlev kod görünümü** penceresi gösterir, işlev için kaynak kodu varsa ve seçili işlev en pahalı satırları vurgulanmaktadır. GetNames seçildiğinde, bu işlev bir dize uygulama kaynaklarından okur ve kullanır görebilirsiniz bir <xref:System.IO.StringReader> dizesindeki her bir satır eklemek için bir <xref:System.Collections.ArrayList>. Bu işlev iyileştirmek için belirgin bir yolu yoktur.  
  
3.  GetNames yalnızca çağıran PeopleNS.People.GetPeople olduğu için kodunu incelemek için maliyet dağıtım penceresinde GetPeople tıklayın. Bu yöntem döndürür bir <xref:System.Collections.ArrayList> kişileri ve şirketleri GetNames tarafından üretilen adlarından PersonInformationNS.PersonInformation nesne. Ancak, GetNames iki kez PersonInformation nesne oluşturulan her zaman çağrılır. Yöntemi yalnızca bir kez listeler yönteminin başlangıcında oluşturup PersonInformation oluşturma döngüsü sırasında bu listeye dizin kolayca iyileştirilebilir görebilirsiniz.  
  
4.  GetPeople alternatif bir sürümü ile örnek uygulama kodu sağlanır ve derleme özellikleri için bir koşullu derleme sembol ekleyerek en iyi duruma getirilmiş işlevi çağırabilir. Çözüm Gezgini penceresinde kişiler projeye sağ tıklayın ve ardından **özellikleri**. Tıklayın **derleme** özellik sayfası menüsünü ve sonra türü **OPTIMIZED_GETPEOPLE** koşullu derleme sembol metin kutusuna. En iyi duruma getirilmiş sürümünü GetPeople sonraki derleme özgün yöntemi değiştirir.  
  
5.  Performans oturumu yeniden çalıştırın. Performans Gezgini araç çubuğunda **profil ile Başlat**. Tıklayın **kişileri Al** ve ardından **verileri dışarı aktarma**. Görünen ve kişiler Trax uygulamayı kapatın Not Defteri penceresini kapatın.  
  
     Yeni bir profil oluşturma veri dosyası oluşturulur ve **özeti** görünür yeni veri görünümü [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ana penceresi.  
  
6.  İki profil oluşturma çalışması karşılaştırmak, performans Gezgini içinde iki veri dosyaları seçin, dosyaları sağ tıklayın ve ardından **Performans raporlarını Karşılaştır**. Karşılaştırma raporu bir pencere [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ana penceresi. **Delta** sütun önceki işlevlerin performans değerindeki değişikliği gösterir **temel** sonraki değerine **karşılaştırma** değeri. Değerleri karşılaştırmak için seçebileceğiniz **sütun** açılan liste. Seçin **kapsamlı örnek yüzdesi**.  
  
     GetPeople ve GetNames yöntemi önemli ölçüde performans artışı Göster dikkat edin.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>Araçlar yöntemini kullanarak profil oluşturma  
 İzleme ve profil oluşturucu araştırma işlevleri profili oluşturulan ikili dosyalarının özel olarak oluşturulmuş sürümlere ekler bir profil oluşturma yöntemidir. Araştırmaları giriş ve çıkış Araçlı modüllerdeki işlevlerin ve işlevlerden tüm çağrı sitede zamanlama bilgilerini toplayın. İzleme işlemi, diske yazma ve bir ağ üzerinden iletişim kurma gibi giriş/çıkış işlemleri ile ilgili sorunları araştırmak için yararlıdır. Örnekleme daha ayrıntılı bilgi, ancak işlem yürütme daha kapsayıcıdır ve büyük miktarda bir ek yük doğurur araçları sağlar. İzlenen ikili dosyaların hatalarını ayıklama veya ikili dosyaları sürüm ve dağıtım için hedeflenmemiş büyük.  
  
 Kılavuzun bu bölümünde, size daha önce profili PeopleTrax uygulamada iyileştirebilirsiniz daha fazla kod bulmak için izleme metodunu kullanacağız. Özet görünümü zaman çizelgesi kısmındaki filtreyi kullanarak, biz çözümlememiz dışarı aktarma veri senaryoya kişilerin listesini bir not defteri dosyasına yazılır profili oluşturulmuş uygulamamızdaki odaklanır.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>Araçlar yöntemini kullanarak mevcut bir uygulama profiline  
  
1.  Gerekirse, PeopleTrax uygulamayı Visual Studio'da açın.  
  
     Çözüm yapı yapılandırması ayarlanır ve yönetici olarak çalıştırdığınızdan emin olun **yayın**.  
  
2.  Performans Gezgini tıklayın **izleme**.  
  
3.  Performans Gezgini araç çubuğunda **profil ile Başlat**.  
  
     Profil Oluşturucu, projeyi oluşturur ve uygulamanın profilini başlar. PeopleTrax uygulama penceresi görünür.  
  
4.  Tıklayın **kişileri Al**.  
  
     PeopleTrax veri kılavuzu verilerle doldurur.  
  
5.  Yaklaşık 10 saniye bekleyin ve ardından **verileri dışarı aktarma**.  
  
     **Not Defteri'ni** başlar ve PeopleTrax kişilerden listesini içeren yeni bir dosyayı görüntüler. Bekleyen etkinleştirir, verileri daha kolay tanımlamak için filtre yordamı dışarı aktarın.  
  
6.  Kapatma **not defteri**ve ardından kapatın **PeopleTrax** uygulama.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] bir performans oturumu raporu (*.vsp) oluşturur.  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>İzleme eklenmiş profil oluşturma sonuçları analiz etmek için  
  
1. Zaman Çizelgesi grafiği **özeti** rapor görünümünü programının CPU kullanımı, profil oluşturma süresi boyunca çalışma gösterir. Verileri dışarı aktarma işlemi, büyük yoğun veya grafiğin sağ tarafında bir platoya olması gerekir. Biz görüntülemek ve dışarı aktarma işleminde toplanan verileri çözümlemek için performans oturumu filtreleyebilirsiniz. Noktası solundaki veri dışarı aktarma işleminin başladığı grafiğe tıklayın. İşlemi sağ tarafına tekrar tıklayın. Ardından **seçime göre filtre** zaman çizelgesinin sağdaki bağlantılar listesinde.  
  
    **Etkin yolu** ağacını Göster <xref:System.String.Concat%2A> PeopleTrax.Form1.ExportData yöntemi tarafından çağrılan yöntem zaman büyük bir yüzdesini kullanıyor. Çünkü **System.String.Concat** ayrıca üst kısmında, **işlevleri ile en bireysel işleri** işlevde harcanan zamanı azaltmak listesinde olan büyük olasılıkla bir nokta iyileştirme.  
  
2. Çift **System.String.Concat** işlev Ayrıntıları görünümünde daha fazla bilgi için Özet tabloların her ikisinde.  
  
3. PeopleTrax.Form1.ExportData Concat çağıran tek bir yöntem olduğunu görebilirsiniz. Tıklayın **PeopleTrax.Form1.ExportData** içinde **çağıran fonksiyonları** olan işlev Ayrıntıları görünümünde hedefi olarak yöntemi seçin.  
  
4. İşlev kod Görünümü penceresi yönteminde inceleyin. Değişmez değer çağrı olduğunu fark **System.String.Concat**. Bunun yerine, derleyici çağrıları değiştirir işlenenin += çeşitli kullanımları vardır **System.String.Concat**. .NET Framework içindeki dize herhangi bir değişiklik, ayrılması yeni bir dize neden. .NET Framework'ü içeren bir <xref:System.Text.StringBuilder> dize birleştirme için en iyi duruma getirilmiş sınıfı  
  
5. Bu sorunun görüldüğü alan ile en iyi duruma getirilmiş kodu değiştirmek için bir koşullu derleme simgesi olarak OPTIMIZED_EXPORTDATA PeopleTrax projeye ekleyin.  
  
6. Çözüm Gezgini'nde PeopleTrax projeye sağ tıklayın ve ardından **özellikleri**.  
  
    PeopleTrax proje özellikleri formu görüntülenir.  
  
7. Tıklayın **derleme** sekmesi.  
  
8. İçinde **koşullu derleme simgeleri** metin kutusunda, **OPTIMIZED_EXPORTDATA**.  
  
9. Proje özelliği formu kapatmak ve seçin **Tümünü Kaydet** sorulduğunda.  
  
   Uygulamayı yeniden çalıştırdığınızda, işaretli performans geliştirmeleri göreceksiniz. Görünür kullanıcı performans iyileştirmeleri olsa bile, profil oluşturma oturumunu yeniden çalıştırmanız önerilir. Bir sorunu düzelttikten sonra verileri gözden geçirmek, ilk sorun başka bir sorun gizlememeniz çünkü önemlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel bakış](../profiling/overviews-performance-tools.md)   
 [Çalışmaya başlama](../profiling/getting-started-with-performance-tools.md)   
 [/Z7, /Zi, /ZI (Hata Ayıklama Bilgileri Biçimi)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)



