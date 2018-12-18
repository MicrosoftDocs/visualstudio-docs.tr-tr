---
title: Xamarin uygulamalarıyla uygulama yaşam döngüsü yönetimi (ALM) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 16
ms.author: crdun
manager: crdun
ms.openlocfilehash: f2e7af8227e11d554a4f953593dad396d5543aca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745213"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Xamarin uygulamalarıyla Uygulama Yaşam Döngüsü Yönetimi (ALM)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Xamarin Android, iOS ve Windows C#, .NET ve Visual Studio kullanarak hedefleyen platformlar arası mobil uygulamalar oluşturmanıza olanak sağlar. Xamarin platformlarla yalnızca platforma özgü olmalarına gerek küçük bir yüzdesine arasında paylaşılan kod büyük bir kısmı sağlar. Xamarin kendisi hakkında daha fazla bilgi için bkz. [Visual Studio ve Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Modern platformlar için uygulama geliştirme, hemen kod yazmaya daha pek çok daha fazla etkinlik içerir. DevOps (geliştirme + işlem), uygulamanın tam yaşam döngüsü span ve planlama ve izleme çalışması, tasarlama ve uygulama kodu, kaynak kodu deposu, yönetme, çalışan sürekli tümleştirme yönetme dahil olarak başvurulan, bu etkinlikler dağıtımlar, test etme (dahil, birim testleri ve UI testleri) çeşitli türleri Tanılama, hem geliştirme hem de üretim ortamlarında çalışan ve uygulama performansı ve kullanıcı davranışlarını gerçek zamanlı olarak telemetri ve analiz izleme.  
  
 Visual Studio Team Services ve Team Foundation Server ile birlikte Visual Studio uygulama yaşam döngüsü yönetimi veya ALM da bilinir, DevOps özelliklerini çeşitli sağlar. Bunların çoğu, tamamen platformlar arası projeler için geçerlidir.  
  
 Bunlar C# ve .NET araçları bazı hangi ALM oluşturulmuştur, yerleşik olduğundan bu Xamarin uygulamaları ile özellikle doğrudur. Diğer araçları, derleme ve çalışma zamanı ortamları ile sıkı tümleştirme gerektirir. Xamarin uygulamaları Windows dışı platformlarda çalıştırın ve Mono .NET uygulaması içerdiğinden, Xamarin, belirli özel araçlar gerekir sağlar.  
  
 Aşağıdaki tablolarda, Visual Studio ALM özellikleri tanımlayan bir Xamarin projesi ile düzgün çalışması bekleyebilirsiniz ve hangilerinin sınırlamaları vardır. Özellikleri hakkında daha fazla ayrıntı için bağlantılı belgelerine bakın.  
  
## <a name="agile-tools"></a>Çevik Araçlar  
 Başvuru bağlantısı: **[iş](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (Visual Studio Team Services veya Team Explorer Everywhere dahil TFS'nin kullanarak)  
  
 Genel Açıklama: tüm planlama ve izleme özellikleri proje türü ve dilleri kodlama bağımsız olarak çalışır.  
  
|Özellik|Xamarin ile desteklenen|Ek Açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Kapsamlar ve sprint'ler yönetme|Evet||  
|İş izleme|Evet||  
|Takım odası işbirliği|Evet||  
|Kanban panoları|Evet||  
|Rapor ve ilerleme durumunu görselleştirin|Evet||  
  
## <a name="modeling"></a>Modelleme  
 Başvuru bağlantısı:  **[çözümleme ve modelleme mimarisi](../modeling/analyze-and-model-your-architecture.md)**  
  
 Tasarım özellikleri kodlama dilini bağımsız veya C# .NET dilleri ile çalışır. Bkz: [rolleri mimari ve modelleme diyagramları yazılım geliştirmede](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) hangi yönlerini kodla ilişkili için.  
  
|Özellik|Xamarin ile desteklenen|Ek Açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Sıralı diyagramlar|Evet||  
|Bağımlılık grafikleri|Evet||  
|Çağrı hiyerarşisi|Evet||  
|Sınıf Tasarımcısı|Evet||  
|Mimari Gezgini|Evet||  
|UML diyagramlarını (durum, etkinlik, sınıf, bileşen, dizisi ve DSL kullanın)|Evet||  
|Katman diyagramları|Evet||  
|Katman doğrulama|Evet||  
  
## <a name="code"></a>Kod  
  
|Özellik|Xamarin ile desteklenen|Ek Açıklamalar|  
|-------------|----------------------------|-------------------------|  
|[Team Foundation sürüm denetimi kullanın](http://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) veya Visual Studio Team Services|Evet||  
|[Team Services'da Git ile çalışmaya başlama](http://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Evet||  
|[Kod Analizi/artırma kod kalitesini (başvurular, önerilen değişiklikleri, vb.)](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Evet||  
|[Kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)|Evet|Uygulama çalışma zamanına kadar çözülmüş değildir burada platforma özgü sınırları dışında.|  
|[Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)|Evet||  
  
## <a name="build"></a>Derleme  
 Başvuru bağlantısı:  **[oluşturun](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Özellik|Xamarin ile desteklenen|Ek Açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Şirket içi TFS sunucusu|Evet|Derleme makinesi Xamarin yüklü olması ve iOS için oluşturmak için bir OSX bilgisayara bağlanabilir. Bkz: [Xamarin için TFS Yapılandırma](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (Xamarin Web sitesi)|  
|Visual Studio Team Services bağlı şirket içi yapı sunucusu|Evet|Bkz: [yapı sunucusu](http://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) yönergeler için.|  
|Visual Studio Team Services, barındırılan denetleyici hizmeti|Evet|Bkz: [Xamarin uygulamanızı derleyin](https://www.visualstudio.com/en-us/docs/build/apps/mobile/xamarin).|  
|Tanımlarla öncesi ve sonrası betikleri oluşturun|Evet||  
|Sürekli Tümleştirme dahil olmak üzere Geçitli iade|Evet|TFVC için Geçitli iade yalnızca Git iadeler yerine bir çekme isteği model üzerinde çalışır.|  
  
## <a name="testing"></a>Sınama  
 Başvuru bağlantısı:  **[uygulamayı test etme](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Özellik|Xamarin ile desteklenen|Ek Açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Testleri planlama, test çalışmaları oluşturma ve test paketlerini düzenleme|Evet||  
|El ile test etme|Evet||  
|Test Yöneticisi'ni (kayıt ve kayıttan yürütme testleri)|Evet|Windows cihazları ve Android öykünücüleri Visual Studio'dan yalnızca. Tüm cihazlar için kaydı ile mümkündür [Xamarin Test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
|Kod kapsamı|yok||  
|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|Evet|Windows ve Android hedefleri için yerleşik MSTest Araçlar kullanılabilir. Windows, Android ve iOS üzerinde birim testlerini çalıştırmak için Xamarin NUnit önerir. Bkz: [Xamarin için TFS Yapılandırma](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (Xamarin Web sitesi).|  
|[Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)|Yalnızca Windows|Visual Studio'nun kullanıcı Arabirimi Testi Kaydedicisi, yalnızca Windows olur. Tüm platformlar için bkz [Xamarin Test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Kod kalitesini geliştirme  
 Başvuru bağlantısı:  **[kod kalitesini iyileştirmek](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Özellik|Xamarin ile desteklenen|Ek Açıklamalar|  
|-------------|----------------------------|-------------------------|  
|[Yönetilen Kod Kalitesini Analiz Etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Evet||  
|[Kod kopyası algılamayı kullanarak yinelenen kodları bulma](http://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Evet||  
|[Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Evet||  
|[Performans Gezgini](../profiling/performance-explorer.md)|Hayır|Kullanım [Xamarin Profiler](http://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/) Xamarin Studio üzerinden yerine. Xamarin Profiler şu anda önizlemededir ve henüz Windows hedefleri için çalışmaz unutmayın.|  
|[.NET Framework bellek sorunlarını çözümleme](../misc/analyze-dotnet-framework-memory-issues.md)|Hayır|Visual Studio Araçları, profil oluşturma için Mono framework uygulamasına kancaları yoktur.|  
  
## <a name="release-management"></a>Yayın yönetimi  
 Başvuru bağlantısı:  **[sürüm yönetimi ile dağıtımları otomatikleştirme](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Özellik|Xamarin ile desteklenen|Ek Açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Sürüm işlemlerini yönetme|Evet||  
|Dağıtım için dışarıdan yükleme betikleri aracılığıyla sunucularına|Evet||  
|App Store'a yükle|Kısmi|Kullanılabilir uzantılar bazı uygulama mağazaları için bu işlemi otomatikleştirmek.  Bkz: [için Visual Studio Team Services uzantıları](https://marketplace.visualstudio.com/VSTS); Örneğin, [uzantısı için Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>HockeyApp ile izleme  
 Başvuru bağlantısı:  **[HockeyApp ile izleme](https://www.hockeyapp.net/features/)**  
  
|Özellik|Xamarin ile desteklenen|Ek Açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Kilitlenme analizi, telemetri ve beta dağıtım|Evet||

