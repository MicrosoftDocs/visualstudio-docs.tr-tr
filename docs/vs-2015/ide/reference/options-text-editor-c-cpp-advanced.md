---
title: Seçenekler, metin düzenleyici, C / C++, Gelişmiş | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aafa46e62af6eadb56d8cf53cb2190bc7403358b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285707"
---
# <a name="options-text-editor-cc-advanced"></a>Seçenekler, Metin Düzenleyici, C/C++, Gelişmiş
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Bu seçenekler değiştirerek, C veya C++ ortamında programlama, IntelliSense ve gözatma veritabanı ilgili davranışı değiştirebilirsiniz.  
  
 Bu sayfaya erişmek için **seçenekleri** iletişim kutusunda, sol bölmede, **metin düzenleyici**, genişletme **C/C++** ve ardından **Gelişmiş**.  
  
> [!NOTE]
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="browsingnavigation"></a>Gözatma Gezinti  
 Bu seçenekleri dışında hiçbir zaman bir çözüm veritabanı etkinliğini kabul edilemez bir sistem kaynaklarının miktarı tüketen çok büyük olduğu nadir durumlarda seçmeniz gerekir.  
  
 **Veritabanı devre dışı bırak**  
 Tüm kod gözatma veritabanı (SDF), diğer tüm gözatma/gezinti seçenekleri ve hariç tüm IntelliSense özelliklerini kullanımını #include otomatik tamamlamayı devre dışı bırakılır.  
  
 **Veritabanı güncelleştirmelerini devre dışı bırak**  
 Veritabanı salt okunur açılacak ve dosyaları düzenlediğiniz gibi hiçbir güncelleştirme gerçekleştirilmeyecek. Çoğu özellikleri çalışmaya devam edecektir. Ancak, düzenleme yaptığınız gibi verileri eski hale gelir ve hatalı sonuçlar elde edersiniz.  
  
 **Veritabanı otomatik güncelleştirmelerini devre dışı bırak**  
 Kaynak dosyalar değiştirildiğinde, kod gözatma veritabanını otomatik olarak güncelleştirilmez. Ancak, açarsanız **Çözüm Gezgini**, proje için kısayol menüsünü açın ve ardından **yeniden tarama çözüm**, tüm güncel olmayan dosyalar denetlenir ve veritabanı güncelleştirilir.  
  
 **Dahili dosyaları devre dışı bırak**  
 Kod gözatma veritabanını bir projede belirtilen olmayan dosyalar için veri toplamaz. Kaynak dosyaları ve üstbilgi dosyaları, açıkça belirtilen bir proje içerir. Dahili dosyaları (örneğin, afxwin.h windows.h ve atlbase.h) açık dosyaları dahil edilir. Normalde, sistem bu dosyaları bulur ve ayrıca çeşitli göz atma özellikleri (Git dahil) dizinini oluşturur. Bu seçeneği seçerseniz, bu dosyaları dizine alınmamış ve bazı özellikler için kullanılamaz. Bu seçeneği belirlerseniz, "Dahili temizlemeyi devre dışı bırak" ve "Dış bağımlılıklar'ı devre dışı bırak" da örtük olarak seçilir.  
  
 **Dahili temizlemeyi devre dışı bırak**  
 Kod gözatma veritabanını temizleme değil, artık referans verilmeyen örtük dosyaları yedekleme. Bu seçenek, artık kullanıldığında veritabanından kaldırılmasını örtük dosyaları önler. Örneğin, eklediğiniz bir `#include` yönergesi, kaynak dosyalarınızı birine mapi.h başvuran, mapi.h bulundu ve dizin. Daha sonra kaldırırsanız #include ve dosyayı başka bir yerde başvurulan değil, ilgili bilgileri, sonuçta bu seçeneği seçmezseniz kaldırılacak. (Bkz **yeniden tarama çözüm aralığını** seçeneği.) Açıkça çözümü yeniden tara olduğunda bu seçenek göz ardı edilir.  
  
 **Dış bağımlılıklar klasörlerini devre dışı bırak**  
 Her proje için dış bağımlılıklar klasörü oluşturuldu veya güncelleştirildi. İçinde **Çözüm Gezgini**, her proje, bu proje için tüm örtük dosyalarını içeren bir dış bağımlılıklar klasörü içerir. Bu seçeneği seçerseniz, bu klasöre görünmez.  
  
 **Veritabanını yeniden oluşturun**  
 Kod çözüm yüklendiğinde bir sonraki açışınızda hiçbir şey veritabanından gözatma yeniden oluşturun. Bu seçeneği seçerseniz, bu nedenle yeniden veritabanına neden çözümü yüklemek sonraki açışınızda SDF veritabanı dosyası silinir ve tüm dosyaları dizine.  
  
 **Yeniden tarama çözüm aralığını**  
 Bir 'Çözümü şimdi yeniden tara' işi belirttiğiniz aralığı için zamanlandı. 0 ile 5000 dakika arasında belirtmeniz gerekir. Varsayılan değer 60 dakikadır. Çözümü yeniden taranıp sırasında dosya zaman damgası IDE dışında bir dosyanın değiştirilip değiştirilmediğini saptamak için denetlenir. (IDE'de yapılan değişiklikleri otomatik olarak izlenir ve dosyaları güncelleştirilir.) Örtük olarak eklenen dosyalar, bunların tümü Başvurulmakta olup olmadığını belirlemek için denetlenir.  
  
## <a name="diagnostic-logging"></a>Tanılama günlüğüne kaydetme  
 Microsoft bir sorunu tanılamak için Gelişmiş bilgileri toplamak isteyen durumunda bu seçenekleri sunulur. Günlük bilgilerini kullanıcılar için kullanışlı değildir ve devre dışı bırakmanızı öneririz.  
  
 **Günlüğe kaydetmeyi etkinleştirme**  
 Çıkış penceresine tanılama günlük kaydını etkinleştirir.  
  
 **Günlük düzeyi**  
 0-5 günlük ayrıntı düzeyini ayarlayın.  
  
 **Filtre günlüğe kaydetme**  
 Filtreler bir bit maskesi kullanılarak olay türleri görüntülenir.  
  
 Aşağıdaki seçeneklerden herhangi birini toplamını kullanarak ayarlayın:  
  
-   0 - yok  
  
-   1 - genel  
  
-   2 - boş  
  
-   4 - iş öğesi  
  
-   8 - IntelliSense  
  
-   16 - ACPerf  
  
-   32 - ClassView  
  
## <a name="fallback-location"></a>Geri dönüş konumu  
 Birincil konum (Çözüm aynı dizin) kullanıldığında değil SDF ve IntelliSense destek dosyalarını (örneğin, iPCH) nereye yerleştirilir geri dönüş konumdur. Bu durum, kullanıcı çözüm dizinine yazma izni yok veya çözüm dizini yavaş bir cihaz kullandığını oluşabilir. Varsayılan geri dönüş kullanıcının temp dizininde konumdur.  
  
 **Her zaman geri dönüş konumu kullanın**  
 Kod gözatma veritabanı ile IntelliSense dosyaları her zaman, "geri dönüş konumu olarak", .sln dosyası değil yanındaki belirttiğiniz klasördeki saklanması gerektiğini gösterir. IDE, hiçbir zaman çözüm dizini yanındaki SDF veya iPCH dosyaları yerleştirmek deneyecek ve her zaman geri dönüş konumu olarak kullanır.  
  
 **Eğer temel konum kullanılırsa uyarma**  
 Hakkında bilgi sahibi olmak değil veya 'Temel konum' kullanıldığında istenir. Normalde, IDE geri dönüş konumu kullanmak zorunda bunu size bildirir. Bu seçenek, bu uyarı devre dışı bırakır.  
  
 **Geri dönüş konumu**  
 Bu değer, kod veritabanı veya IntelliSense dosyalarını saklamak için ikincil konum olarak kullanılır. Varsayılan olarak, geçici dizin, geri dönüş konumdur. IDE ile çözüm adları aynı olan sorunları önler çözüm tam yolunu karmasını yanı sıra çözümün adını içeren bir alt dizinde belirtilen yol (veya geçici dizin) oluşturur.  
  
## <a name="intellisense"></a>IntelliSense  
 **Otomatik hızlı bilgi**  
 Metin üzerinde işaretçiyi getirdiğinizde Hızlıbilgi araç ipuçlarını sağlar.  
  
 **IntelliSense'i devre dışı bırak**  
 Tüm IntelliSense özelliklerini devre dışı bırakır. IDE VCPkgSrv.exe işlemleri için IntelliSense isteklere hizmet oluşturmaz ve hiçbir IntelliSense özellikleri (Hızlıbilgi, üye listesi, otomatik tamamlama, parametre Yardım) çalışır. Anlam renklendirmeyi ve başvuru vurgulama da devre dışı bırakılır. Bu seçeneği yalnızca (gezinti çubuğunda, ClassView ve özellik penceresini dahil) veritabanı üzerinde kullanan göz atma özellikleri devre dışı değil.  
  
 **Otomatik güncelleştirme devre dışı bırak**  
 IntelliSense için fiili isteğe yapılana kadar IntelliSense güncelleştirme ertelendi. Bu gecikme bir uzun yürütme süresi bir dosya çubuğunda ilk IntelliSense işlemin neden olabilir, ancak çok yavaş ya da kaynak kısıtlı makinelerde bu seçeneği belirlemek yararlı olabilir. Bu seçeneği belirlerseniz, örtük olarak da "Hata raporlamayı devre dışı bırak" ve "Squiggles devre dışı bırakma" seçenekleri belirleyin.  
  
 **Hata raporlamayı devre dışı**  
 Dalgalı çizgiler ve Hata Listesi penceresi boyunca IntelliSense hatalarının raporlama, devre dışı bırakır. Ayrıca, hata raporlama ile ilişkili arka plan ayrıştırmayı devre dışı bırakır. Bu seçeneği seçerseniz, ayrıca dolaylı olarak "Squiggles devre dışı bırak" seçeneği seçin.  
  
 **Dalgalı çizgiler devre dışı bırak**  
 IntelliSense hata ilişkilendirmelerini devre dışı bırakır. Düzenleyici penceresinde kırmızı "squiggles" gösterme, ancak hata yine de hata Listesi penceresinde görünür.  
  
 **Devre dışı #include otomatik tamamlama**  
 Otomatik Tamamlama, devre dışı bırakır `#include` deyimleri.  
  
 **İleri eğik çizgi kullanın #include otomatik tamamlama**  
 Tetikleyiciler otomatik tamamlanmasını `#include` deyimleri, "/" kullanılır. Varsayılan sınırlayıcı ters eğik çizgidir ' \'. Derleyici, ya da kabul edin, ne, kod tabanının kullandığını belirtmek için bu seçeneği kullanın.  
  
 **Maksimum önbelleğe alınmış çeviri birimleri**  
 IntelliSense istekleri için herhangi bir zamanda etkin tutulacak çeviri birimlerinin maksimum sayısı. 2 ile 15 arasında bir değer belirtmeniz gerekir. Bu sayı, maksimum sayısına (belirli bir örneğini Visual Studio için) çalıştırılacak VCPkgSrv.exe işlemleri doğrudan ilgilidir. Varsayılan değer 2'dir, ancak kullanılabilir bellek varsa, bu değeri artırmak ve büyük olasılıkla IntelliSense biraz daha iyi performans elde edin.  
  
 Çeviri birimleri hakkında daha fazla bilgi için bkz: [çeviri aşamaları](http://msdn.microsoft.com/library/a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db).  
  
 **Israrlı üye listesi devre dışı bırak**  
 Üye listesi bir türü veya değişken adını yazarken görünmez. Yalnızca bir işleme karakterleri yazdıktan sonra sınıfında tanımlandığı gibi liste görünür **üye listesi işleme karakterleri** seçeneği.  
  
 **Üye listesi anahtar sözcükleri devre dışı bırak**  
 Dil anahtar sözcükleri gibi `void`, `class`, `switch` üye listesi önerilerine görünmez.  
  
 **Üye listesi kod parçacıklarını devre dışı bırak**  
 Kod parçacıkları üye listesi önerilerine görünmez.  
  
 **Anlam renklendirmeyi devre dışı bırak**  
 Dil anahtar sözcükleri, dizeleri ve açıklamaları dışında tüm kod renklendirme devre dışı bırakır.  
  
 **Akıllı üye listesi işleme**  
 Enter tuşuna basıldığında tam yazılmış sözcüğün sonuna seçtiğinizde bir satır ekler.  
  
 **Üye listesi filtre modu**  
 Eşleştirme algoritmasını türünü ayarlar. **Belirsiz** en olası eşleşmeleri bir yazım benzer, ancak aynı olan bulmaya denetleyicisi için benzer bir algoritma kullandığından bulur. **Akıllı filtreleme** bir sözcük başlangıcında olmasanız bile eşleşen alt dizeler. **Önek** sözcüğün başında başlaması aynı alt dizeler üzerinde yalnızca eşleşir.  
  
 **Üye listesi işleme karakterleri**  
 Kaydedilecek vurgulanmış geçerli üye listesi öneri neden karakterleri belirtir. Ekleyebilir veya karakterleri bu listeden kaldırın.  
  
## <a name="references"></a>Referanslar  
 **Çözümleme devre dışı bırak**  
 Performans nedeniyle, tüm başvuruları Bul' her adayı doğrulamak için IntelliSense kullanmak yerine varsayılan olarak ham metinsel arama sonuçlarını görüntüler. Tüm daha doğru sonuçlar işlemleri bulmak için bu onay kutusunu temizleyebilirsiniz. Arama başına temelinde filtre, sonuç listesi için kısayol menüsünü açın ve ardından "Çözümleme sonuçları."  
  
 **Onaylanmamış Gizle**  
 Onaylanmamış öğelerde 'Tüm başvuruları Bul' sonuçlarını gizle. Ayarlama "devre dışı bırak Çözümleme" seçeneği, bu seçenek sonuçlarında onaylanmamış öğeleri gizlemek için kullanabilirsiniz.  
  
 **Başvuru vurgulama devre dışı bırak**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dile Özgü Düzenleyici Seçeneklerini Ayarlama](../../ide/reference/setting-language-specific-editor-options.md)



