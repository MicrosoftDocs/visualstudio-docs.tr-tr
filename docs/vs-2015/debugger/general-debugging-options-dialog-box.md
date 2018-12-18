---
title: Genel, hata ayıklama, Seçenekler iletişim kutusu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e3a9e0b8008da5b648ae156235a20964fc0952b1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742776"
---
# <a name="general-debugging-options-dialog-box"></a>Genel, Hata Ayıklama, Seçenekler İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Araçlar / Seçenekler / hata ayıklama / genel** sayfasında aşağıdaki seçenekleri ayarlamanızı sağlar:  
  
 **Tüm kesme noktalarını silmeden önce sor**  
 Tamamlamadan önce onay gerektirir **tüm kesme noktalarını Sil** komutu.  
  
 **Bir işlem kesildiğinde tüm işlemleri Kes**  
 Bir kesme oluştuğunda, hata ayıklayıcı, bağlı olduğu tüm işlemler aynı anda keser.  
  
 **Özel durumlar, AppDomain veya yönetilen/yerel sınırları geçtiğinde Kes**  
 Yönetilen veya karma mod hata ayıklamada, ortak dil çalışma zamanı aşağıdaki koşullar doğru olduğunda, uygulama etki alanı sınırları veya yönetilen/yerel sınırları çapraz özel durumları yakalayabilir:  
  
 1\) yerel kod, COM birlikte çalışabilirliği kullanılarak yönetilen kodu çağırır ve yönetilen kod bir özel durum oluşturduğunda. Bkz: [COM birlikte çalışma'ya giriş](http://msdn.microsoft.com/library/8bd62e68-383d-407f-998b-29aa0ce0fd67).  
  
 2\) ne zaman 1 uygulama etki alanında çalışan yönetilen kod 2 uygulama etki alanındaki yönetilen kodu çağırır ve 2 uygulama etki alanındaki kod bir özel durum oluşturur. Bkz: [uygulama etki alanlarıyla programlama](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3\) zaman kod, yansıma kullanarak bir işlev çağırdığında ve işlev bir özel durum oluşturur. Bkz: [yansıma](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775).  
  
 2) ve 3), özel durum bazen yönetilen kodda'tarafından yakalandı `mscorlib` ortak dil çalışma zamanı yerine. Bu seçenek etkilemez tarafından yakalanan özel bozucu `mscorlib`.  
  
 **Adres seviyesinde hata ayıklamayı etkinleştir**  
 Gelişmiş adres düzeyinde hata ayıklama özellikleri etkinleştirir ( **ayrıştırılmış kodu** penceresinde **kaydeder** penceresi ve adres kesme noktaları).  
  
 **Kaynak kullanılamıyorsa ayrıştırılmış Kodu Göster**  
 Otomatik olarak gösterir **ayrıştırılmış kodu** için hangi kaynak kod hata ayıklamayı denediğinizde penceresi kullanılamıyor.  
  
 **Kesme noktası filtrelerini etkinleştir**  
 Böylece yalnızca belirli işlemleri, iş parçacıklarını veya bilgisayarları etkiler kesme noktalarında filtreler ayarlamanızı sağlar.  
  
 **Özel durum Yardımcısı'nı etkinleştir**  
 Yalnızca yönetilen kod için. Özel durumlar açık özel durum Yardımcısı iletişim kutusu yönetilen.  Bkz: [özel durum Yardımcısı'nı](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb).  
  
 **Çağrı yığınını işlenmeyen özel durumlar üzerinde bırakma**  
 Neden **çağrı yığını** çağrı yığınını işlenmeyen özel durum oluşmadan önceki noktaya geri almak için penceresi.  
  
 **Yalnızca kendi kodumu etkinleştir**  
 Hata ayıklayıcı görüntüler ve sistem kodunu ve iyileştirilen veya, hata ayıklama simgeleri olmayan diğer kodları yoksaymak içinde yalnızca, kullanıcı kodu ("kodum").  
  
 **Değişkenler pencerelerinde (yalnızca Visual Basic) kullanıcı dışındaki nesneler için tüm üyeleri Göster**  
 Genel olmayan üyeleri kullanıcı olmayan kod (değil "kodum") olan nesnelerde görüntülenmesini etkinleştirir.  
  
 **Hiçbir kullanıcı kodu yoksa uyar**  
 Hata ayıklama başladığında ile yalnızca kendi kodum etkin, bu seçenek, kullanıcı kodu ("kodum") olduğunda sizi uyarır.  
  
 **Etkinleştirme .NET Framework kaynak Adımlamayı**  
 Hata ayıklayıcının .NET Framework kaynağına ilerlemesine olanak sağlar. Bu seçeneği etkinleştirmek otomatik olarak yalnızca My Code .NET sembolleri bir önbellek konumuna karşıdan yüklenir Framework'ü devre dışı bırakır. Önbellek konumunu değiştirebilirsiniz **seçenekleri** iletişim kutusu, **hata ayıklama** kategori **sembolleri** sayfası.  
  
 **Özellikleri ve işleçleri (sadece yönetilen) üzerinden adımla**  
 Hata ayıklayıcı, yönetilen kod içindeki özellikler ve işleçlerin içine adımlamasını engeller.  
  
 **Özellik değerlendirmesini ve diğer örtük işlev çağrılarını ekinleştir**  
 Değişkenler pencerelerinde özelliklerin ve örtülü işlev otomatik olarak değerlendirilmesini etkinleştirir çağırır ve **QuickWatch** iletişim kutusu.  
  
 **(C# ve JavaScript yalnızca) değişken pencerelerindeki nesnelerde dize dönüştürme işlevini çağırma**  
 Değişken pencerelerinde nesneleri değerlendirirken bir örtük dize dönüştürmesi çağrısı yürütür. Bu nedenle, bu sonuç tür adı yerine bir dize olarak görüntülenir. Yalnızca C# kodunda hata ayıklama sırasında uygulanır. Bu ayar DebuggerDisplay özniteliği tarafından geçersiz kılınmış olabilir (bakın [DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
 **Kaynak sunucusu desteğini etkinleştir**  
 Visual Studio hata ayıklayıcıya SrcSrv uygulayan kaynak sunuculardan kaynak dosyaları almak için (`srcsrv.dll`) protokolü. Team Foundation Server ve Windows için hata ayıklama araçları protokol uygulayan iki kaynak sunucular olan. SrcSrv kurulumu hakkında daha fazla bilgi için Windows için hata ayıklama araçları belgelerine bakın. Ayrıca bkz [belirtin sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  .Pdb dosyaları okunduğunda rastgele kod dosyalarında yürütülebileceğinden sunucunun güvenilir olduğundan emin olun.  
  
 **Kaynak sunucusu tanılama iletilerini çıkış penceresine Yazdır**  
 Kaynak sunucu desteği etkinleştirildiğinde, bu ayar tanılama görüntüsünü etkinleştirir.  
  
 **Kısmi güven derlemeleri (sadece yönetilen) için kaynak sunucuya izin ver**  
 Kaynak sunucu desteği etkinleştirildiğinde, bu ayar kısmi güven derlemeleri için kaynakları almayarak varsayılan davranışını geçersiz kılar.  
  
 **Kesme noktaları ve geçerli deyim için satırın tamamını vurgulayın**  
 Hata ayıklayıcı bir kesme noktası veya geçerli ifadeyi vurguladığında, tüm satırı vurgular.  
  
 **Kaynak dosyaların özgün sürümle tam olarak eşleşmesi gerekir**  
 Bir kaynak dosyası hata ayıklaması yaptığınız çalıştırılabilir dosyayı oluşturmak için kullanılan kaynak kodu sürümüyle eşleşen doğrulamak için hata ayıklayıcıya bildirir. Sürüm eşleşmiyorsa, eşleşen bir kaynak bulmanız istenir. Eşleşen bir kaynak bulunamıyorsa, kaynak kodu hata ayıklama sırasında görüntülenmez.  
  
 **Tüm çıkış penceresi metnini yürütme penceresine yeniden yönlendir**  
 Hata ayıklayıcı tüm normalde içinde görünecek iletileri gönderir **çıkış** penceresine **hemen** penceresi yerine.  
  
 **Nesnelerin ham yapısını değişkenler pencerelerinde Göster**  
 Tüm nesne yapısı görünümü özelleştirmelerini devre dışı bırakır. Görünüm özelleştirmeleri hakkında daha fazla bilgi için bkz. [yönetilen nesnelerin özel görünümlerini oluşturma](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
 **Modül yükleme (sadece yönetilen) JIT iyileştirmesini bastır**  
 Hata ayıklayıcı JIT derlenir ve bir modül yüklendiğinde yönetilen kodun JIT iyileştirmesini devre dışı bırakır. İyileştirme devre dışı bırakma bazı sorunların hatalarını ayıklamak performans rağmen çoğaltamaz kolaylaştırabilir. Yalnızca kendi Kodum'u kullanıyorsanız, JIT gizleme kullanıcı kodu ("kodum") görüntülenecek kullanıcı olmayan kod iyileştirme neden olabilir.  
  
 **(Yalnızca yerel) sembol yoksa uyar**  
 Hata ayıklayıcı sembol bilgisi olduğu bir programdaki hataları ayıklamayı denediğinizde bir uyarı iletişim kutusu görüntüler.  
  
 **Hata ayıklamayı başlatma sırasında devre dışı bırakılıp bırakılmadığını uyar**  
 Hata ayıklayıcı komut dosyası ile hata ayıklaması devre dışı olarak başlatıldığında bir uyarı iletişim kutusu görüntüler.  
  
 **DLL dışarı aktarmaları yükle**  
 DLL dışa aktarma tablolarını yükler. Dll dışa aktarma tablolarının sembol bilgilerini Windows iletileri, Windows yordamları (WindowProcs), COM nesneleri veya sıralama veya sembolleri olmayan herhangi bir dll ile çalışıyorsanız yararlı olabilir. Dışa aktarma bilgilerini okuma dll bazı ek okumalar içerir. Bu nedenle, bu özellik varsayılan olarak kapalıdır.  
  
 Bir DLL'nin dışa aktarma tablosunda hangi sembollerin kullanılabilir görmek için `dumpbin /exports`. Semboller tüm 32-bit sistem dll için kullanılabilir. Okuyarak `dumpbin /exports` çıkışı, alfasayısal olmayan karakterler de dahil tam işlev adını görebilirsiniz. Bu, bir işlev bir kesme noktası ayarlamak için yararlıdır. Dll dışarı aktarma tablolarındaki işlev adları hata ayıklayıcıda başka bir yerde kesilmiş görünebilir. Aramalar geçerli işlev en üstte (en yoğun şekilde iç içe geçmiş) olacak şekilde arama sırasıyla listelenir. Daha fazla bilgi için [dumpbin/EXPORTS](http://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
 **Paralel Yığınlar diyagramını aşağıdan yukarı Göster**  
 Hangi görüntülenme yönünü denetler **Paralel Yığınlar** penceresi.  
  
 **Yazılan veriler değeri değiştirmiyorsa GPU bellek erişimi özel durumlarını yoksay**  
 Veri değişmediyse hata ayıklama sırasında algılanan yarış durumlarını yoksayar. Daha fazla bilgi için [GPU kodunda hata ayıklama](../debugger/debugging-gpu-code.md).  
  
 **Yönetilen Uyumluluk modunu kullan**  
 Varsayılan hata ayıklama altyapısı bu senaryoları sağlamak için eski bir sürüm ile değiştirir:  
  
- Dışında bir .NET Framework dili kullanıyorsunuz C#, VB veya F# kendi ifade değerlendiricisi sağlayan (buna C + dahildir +/ CLI).  
  
- Karışık modda hata ayıklarken C++ projeleri için Düzenle ve Devam Et'i etkinleştirmek istediğiniz.  
  
  Yönetilen uyumluluk modu yalnızca hata ayıklama altyapısı varsayılan uygulanan bazı özellikleri devre dışı olduğunu unutmayın.  
  
  **Yerel Uyumluluk modunu kullan**  
  Bu seçenek belirlendiğinde, hata ayıklayıcı, Visual Studio 2010 yerel hata ayıklayıcı yerine yeni yerel hata ayıklayıcı kullanır.  
  
  .NET C++ kodunu ayıklarken yeni hata ayıklama motoru değerlendirilirken .NET C++ deyimleri desteklemediğinden, bu seçeneği kullanmanız gerekir. Ancak, çalışması için geçerli hata ayıklayıcı mantığınız bağımlı birçok özelliği yerel uyumluluk modu etkinleştirme devre dışı bırakır. Örneğin, yerleşik türler ister için eski motoru birçok görselleştiriciler eksik `std::string` Visual Studio 2015 projelerinde.   Bu gibi durumlarda en iyi hata ayıklama deneyimi için lütfen Visual Studio 2013 projelerine kullanın.  
  
  **Eski C# ve VB ifade değerlendiricilerini kullan**  
  Hata ayıklayıcı, Visual Studio 2013'ün C# /VB ifade değerlendiricilerini yerine Visual Studio 2015 Roslyn tabanlı ifade değerlendiricilerini kullanacak.  
  
  **(Sadece yönetilen) güvenli olmayan işlemlere karşı özel hata ayıklama görselleştiricileri kullanıldığında uyar**  
  Güvenli olmayan kod çalıştırdığınızdan kod hata ayıklanan işlemde çalışan bir özel hata ayıklama görselleştiricisi kullanırken visual Studio, sizi uyarır.  
  
  **Windows hata ayıklama yığın ayırıcısını (yalnızca yerel) etkinleştir**  
  Yığın tanılamayı geliştirme amacıyla windows hata ayıklama yığınındaki sağlar. Bu seçenek etkinleştirildiğinde, hata ayıklama performansını etkiler.  
  
  **Kullanıcı Arabirimi için XAML hata ayıklama araçlarını etkinleştir**  
  Desteklenen proje türü (F5) hata ayıklaması başlattığınızda, Live Visual Tree ve Live özellik keşfedin windows görünür. Daha fazla bilgi için [hata ayıklama sırasında XAML İnceleme özellikleri](../debugger/inspect-xaml-properties-while-debugging.md).  
  
  **Seçilen öğeleri Canlı görsel ağaç Önizleme**  
  XAML öğesi bağlamı seçili de seçili olduğundan **Live Visual Tree** penceresi.  
  
  **Çalışma zamanı araçlarını uygulamada Göster**  
  Gösterir **Live Visual Tree** ayıklanmakta olan XAML uygulamanın ana pencere bir araç komutları. Bu seçenek, Visual Studio 2015 güncelleştirme 2'de sunulmuştur.  
  
  **Hata ayıklama sırasında tanılama araçlarını etkinleştir**  
  **Tanılama araçları** ayıklarken penceresi görüntülenir. Daha fazla bilgi için [hata ayıklayıcısıyla tümleştirilmiş profil oluşturma](http://msdn.microsoft.com/library/a1f40370-7b61-42c2-afc4-0e13eba98859).  
  
  **Hata ayıklama sırasında PerfTip geçen süresini göster**  
  Hata ayıklaması yapıyorsanız Kod penceresi belirtilen yöntem çağrısının geçen süreyi görüntüler.  
  
  **Etkinleştirme Düzenle ve devam et**  
  Düzenleme ve hata ayıklama sırasında işlevselliği devam kullanabilirsiniz.  
  
  **Yerel etkinleştirme Düzenle ve devam et**  
  Düzen ve yerel C++ kodunu ayıklarken İşlevselliği devam edebilirsiniz. Daha fazla bilgi için [Düzenle ve devam et (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
  **Değişiklikleri Uygula (yalnızca yerel) üzerinde devam**  
  Visual Studio otomatik olarak derler ve bir kesme durumuna işlemine devam etmek, yapmış olduğunuz tüm bekleyen kod değişiklikleri uygular. Seçilmezse, hata ayıklama menüsünün altında "Kod değişikliklerini uygulama" öğesini kullanarak değişiklikleri uygulamak seçebilirsiniz.  
  
  **(Yalnızca yerel) eski kod hakkında uyar**  
  Eski kod hakkında uyarı alın.  
  
  **İzin ver (yalnızca yerel) önceden derleme**  
  Önceden derleme izin verilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio’da hata ayıklama](../debugger/debugging-in-visual-studio.md)



