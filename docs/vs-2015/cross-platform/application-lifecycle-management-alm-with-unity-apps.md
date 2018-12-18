---
title: Unity uygulamaları ile uygulama yaşam döngüsü yönetimi (ALM) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 0a39bee5517f0a4311613af336a5b8bc6e6fa00e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760701"
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Unity Uygulamaları ile Uygulama Yaşam Döngüsü Yönetimi (ALM)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Modern platformlar için uygulama geliştirme, hemen kod yazmaya daha pek çok daha fazla etkinlik içerir. DevOps (geliştirme ve işlemler), uygulamanın tam yaşam döngüsü span ve planlama ve izleme çalışması, tasarlama ve uygulama kodu, kaynak kodu deposu, yönetme, çalışan sürekli tümleştirme yönetme dahil bu etkinlikleri, adlandırılan dağıtımlar, test etme (dahil, birim testleri ve UI testleri) çeşitli türleri Tanılama, hem geliştirme hem de üretim ortamlarında çalışan ve uygulama performansı ve kullanıcı davranışlarını gerçek zamanlı olarak telemetri ve analiz izleme.  
  
 Visual Studio Team Services ve Team Foundation Server ile birlikte Visual Studio uygulama yaşam döngüsü yönetimi veya ALM da bilinir, DevOps özelliklerini çeşitli sağlar. Bunların çoğu oyunları ve Unity ile oluşturulan sürükleyici grafik uygulamaları dahil olmak üzere, platformlar arası projeler için geçerli olan — özellikle kullanarak C# bir komut dosyası dili. Ancak, kendi geliştirme ortamı ve çalışma zamanı altyapısı Unity sahip olduğundan, ALM özellikleri sayısı gibi diğer tür projelere Visual Studio'da yerleşik olarak için geçerli değildir.  
  
 Aşağıdaki tablolarda, Visual Studio ALM özelliklerini nasıl uygulamak veya Unity ile çalışırken, uygulama tanımlar. Özellikleri hakkında daha fazla ayrıntı için bağlantılı belgelerine bakın.  
  
## <a name="agile-tools"></a>Çevik Araçlar  
 Başvuru bağlantısı: **[iş](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (Visual Studio Team Services veya Team Explorer Everywhere dahil TFS'nin kullanarak)  
  
 Genel Açıklama: tüm planlama ve izleme özellikleri proje türü ve dilleri kodlama bağımsız olarak çalışır.  
  
|Özellik|Unity ile desteklenen|Ek Açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Kapsamlar ve sprint'ler yönetme|Evet||  
|İş izleme|Evet||  
|Takım odası işbirliği|Evet||  
|Kanban panoları|Evet||  
|Rapor ve ilerleme durumunu görselleştirin|Evet||  
  
## <a name="modeling"></a>Modelleme  
 Başvuru bağlantısı:  **[çözümleme ve modelleme mimarisi](../modeling/analyze-and-model-your-architecture.md)**  
  
 Genel Açıklama: Bu tasarım özellikleri kodlama dili ya da bağımsız olduğundan veya C# .NET dilleri ile çalışır, ancak bunlar bir geleneksel uygulama paradigma nesne hiyerarşileri ve sınıf ilişkiler üzerinde çalışır. İçinde Unity oyun tasarlama gerektirir farklı paradigma tamamen, yani ilişkileri grafik nesneleri, ses, gölgelendiricilerin, betikler ve benzeri. Bu nedenle, Visual Studio diyagramı modelleme araçları bir Unity proje bütün özellikle ilgili değildir. C# betiklerini içindeki ilişkileri yönetmek için büyük olasılıkla kullanılabilir, ancak tüm yalnızca bir parçası olan.  
  
|Özellik|Unity ile desteklenen|Ek Açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Sıralı diyagramlar|Hayır||  
|Bağımlılık grafikleri|Hayır||  
|Çağrı hiyerarşisi|Hayır||  
|Sınıf Tasarımcısı|Hayır||  
|Mimari Gezgini|Hayır||  
|UML diyagramlarını (durum, etkinlik, sınıf, bileşen, dizisi ve DSL kullanın)|Hayır||  
|Katman diyagramları|Hayır||  
|Katman doğrulama|Hayır||  
  
## <a name="code"></a>Kod  
  
|Özellik|Unity ile desteklenen|Ek Açıklamalar|  
|-------------|--------------------------|-------------------------|  
|[Team Foundation sürüm denetimi kullanın](http://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) veya Visual Studio Team Services|Evet|Unity projeleri yalnızca bir sürüm denetimi sistemleri gibi başka bir projeye yerleştirilip dosyaları koleksiyonunu, ancak sonra bu tabloda açıklandığı gibi birkaç özel nokta vardır.|  
|[Team Services'da Git ile çalışmaya başlama](http://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Evet|Notlar, sonra tabloya bakın.|  
|[Kod Analizi/artırma kod kalitesini (başvurular, önerilen değişiklikleri, vb.)](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Evet||  
|[Kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)|Evet||  
|[Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)|Evet||  
  
 Sürüm denetimi Unity ile ilgili özel konular:  
  
1.  Unity oyun varlıklarını varsayılan olarak gizli bir tek ve donuk kitaplıkta hakkındaki meta verileri izler. Dosyaları ve meta verilerini eşitlemek için bu meta veriler görünür hale getirmek ve daha yönetilebilir yığınlar halinde depolamak için gereklidir. Ayrıntılar için başvurmak [kullanarak dış sürüm denetim sistemleri ile Unity](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Unity belgeleri).  
  
2.  Tüm dosya ve klasörleri Unity proje kaynak denetimi için yukarıdaki bağlantıya de açıklandığı gibi uygun değildir. Varlıklar ve ProjectSettings klasörleri eklenmesi gerekir, ancak kitaplığı ve Temp klasörleri barındırmamalıdır. Kaynak denetimine geçmeyecek oluşturulan dosyaları ek bir listesi için tartışmalara bakın [Unity3D kaynak denetimi için Git kullanma?](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) StackOverflow üzerinde. Birçok geliştiricinin ayrıca işaretlerinize Bu konu üzerinde bağımsız olarak vardır.  
  
3.  Unity proje ikili varlıkları — dokular ya da ses dosyaları gibi — büyük miktarda depolama alabilir. Değişiklik dosyasının yalnızca küçük bir bölümünü etkileyen çeşitli Git gibi kaynak denetimi sistemlerini yapılmış her değişiklik için bir dosyanın benzersiz bir kopyasını depolar. Bu, Git deposu bloated olacak neden olabilir. Bunu ele almak için Unity geliştiricileri genellikle yalnızca son varlıklar, depoya ekleyebilir ve kendi varlıklar, OneDrive, DropBox veya git-annex gibi çalışma geçmişini tutmak farklı bir yol seçin. Bu yaklaşım çalışır, çünkü bu tür varlıklar genellikle kaynak kodu değişiklikleri birlikte tutulan olmanız gerekmez. Geliştiriciler ayrıca genellikle zorla kaynak denetiminde birleştirmeleri izin veren ikili biçimi yerine metin Sahne dosyaları depolamak için metin proje Düzenleyicisi'nin varlık serileştirme modunu ayarlayın. Ayrıntılar için bkz [Düzenleyici ayarları](http://docs.unity3d.com/Manual/class-EditorManager.html) (Unity belgeleri).  
  
## <a name="build"></a>Derleme  
 Başvuru bağlantısı:  **[oluşturun](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Özellik|Unity ile desteklenen|Ek Açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Şirket içi TFS sunucusu|Olası|Unity projeleri Unity ortamı üzerinden yerleşiktir ve Visual Studio aracılığıyla değil (Visual Studio Araçları içinde Unity betikleri derleme ancak bir yürütülebilir dosya üretmez oluşturma) sistem oluşturun. Filtrelenebilir [Unity projeleri komut satırından derleme](http://docs.unity3d.com/Manual/CommandLineArguments.html) (Unity belgeleri), Unity kendisini yüklenmiş olması koşuluyla, bir TFS sunucusuna uygun Unity yürütmek için bir MSBuild işlemi yapılandırmak mümkün, komutları için Bu bilgisayar.<br /><br /> Unity sunduğu [Unity bulut yapı](https://build.cloud.unity3d.com/landing/), Git veya SVN deposu izler ve düzenli çalıştırmaları oluşturur. Şu anda, Team Foundation sürüm denetimi veya Visual Studio Team Services ile çalışmaz.|  
|Visual Studio Team Services bağlı şirket içi yapı sunucusu|Olası|Aynı koşullarda, daha fazla Visual Studio Team bir şirket içi TFS bilgisayarını kullanmayı Services tetiklenen derlemeler yönlendirmek mümkündür.  Bkz: [yapı sunucusu](http://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) yönergeler için.|  
|Visual Studio Team Services, barındırılan denetleyici hizmeti|Hayır|Unity derlemeleri şu anda desteklenmez.|  
|Tanımlarla öncesi ve sonrası betikleri oluşturun|Evet|Bir yapıyı çalıştırmak için Unity komut satırı kullanan özel bir yapı tanımı öncesi ve sonrası betikler için de yapılandırılabilir.|  
|Sürekli Tümleştirme dahil olmak üzere Geçitli iade|Evet|TFVC için Geçitli iade yalnızca Git iadeler yerine bir çekme isteği model üzerinde çalışır.|  
  
## <a name="testing"></a>Sınama  
 Başvuru bağlantısı:  **[uygulamayı test etme](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Özellik|Unity ile desteklenen|Ek Açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Testleri planlama, test çalışmaları oluşturma ve test paketlerini düzenleme|Evet||  
|El ile test etme|Evet||  
|Test Yöneticisi'ni (kayıt ve kayıttan yürütme testleri)|Windows cihazları ve Android öykünücüleri yalnızca||  
|Kod kapsamı|yok|Birim olarak uygulanamaz test Unity ve Visual Studio değil içinde olur, aşağıya bakın.|  
|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|Unity, ancak değil Visual Studio içinde|Unity sağlayan bir parçası olarak kendi birim testi çerçevesi [Unity Test Araçları](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity varlık Store). Birim testi sonuçlarını Unity içinde bildirilen ve Visual Studio içinden ortaya değil.|  
|[Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)|Hayır|Kodlanmış UI testleri, uygulamanın kullanıcı arabiriminde okunabilir denetimleri dayanır; Unity uygulamaları doğası gereği grafik ve böylece içerik kodlanmış UI test araçları tarafından okunabilir değil.|  
  
## <a name="improve-code-quality"></a>Kod kalitesini geliştirme  
 Başvuru bağlantısı:  **[kod kalitesini iyileştirmek](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Özellik|Unity ile desteklenen|Ek Açıklamalar|  
|-------------|--------------------------|-------------------------|  
|[Yönetilen Kod Kalitesini Analiz Etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Evet|Visual Studio'da C# betik kodunu analiz edebilirsiniz.|  
|[Kod kopyası algılamayı kullanarak yinelenen kodları bulma](http://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Evet|Visual Studio'da C# betik kodunu analiz edebilirsiniz.|  
|[Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Evet|Visual Studio'da C# betik kodunu analiz edebilirsiniz.|  
|[Performans Gezgini](../profiling/performance-explorer.md)|Hayır|Kullanım [Unity Profiler](http://docs.unity3d.com/Manual/Profiler.html) (Unity Web sitesi).|  
|[.NET Framework bellek sorunlarını çözümleme](../misc/analyze-dotnet-framework-memory-issues.md)|Hayır|Visual Studio Araçları, profil oluşturma için Mono framework (olarak Unity tarafından kullanılan) içine kancaları yoktur. Kullanım [Unity Profiler](http://docs.unity3d.com/Manual/Profiler.html) (Unity belgeleri).|  
  
## <a name="release-management"></a>Yayın yönetimi  
 Başvuru bağlantısı:  **[sürüm yönetimi ile dağıtımları otomatikleştirme](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Özellik|Unity ile desteklenen|Ek Açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Sürüm işlemlerini yönetme|Evet||  
|Dağıtım için dışarıdan yükleme betikleri aracılığıyla sunucularına|Evet||  
|App Store'a yükle|Kısmi|Kullanılabilir uzantılar bazı uygulama mağazaları için bu işlemi otomatikleştirmek.  Bkz: [için Visual Studio Team Services uzantıları](https://marketplace.visualstudio.com/VSTS); Örneğin, [uzantısı için Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>HockeyApp ile izleme  
 Başvuru bağlantısı:  **[HockeyApp ile izleme](https://www.hockeyapp.net/features/)**  
  
|Özellik|Unity ile desteklenen|Ek Açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Kilitlenme analizi, telemetri ve beta dağıtım|Evet|HockeyApp, beta dağıtım işleme ve kilitlenme raporları elde etmek için özellikle yararlıdır.<br /><br /> C# komut dosyalarından daha fazla telemetri için koşuluyla Unity tarafından kullanılan .NET sürümünü çalıştıran herhangi bir analiz çerçeveyi kullanmak da mümkündür. Ancak, bu yalnızca içinde oyun betikleri ve Unity altyapısı içinde değil daha derin analizi sağlar. Şu anda hiçbir eklentisi için Application Insights yoktur, ancak diğer analiz çözümleri için kullanılabilir gibi olan eklentiler [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) ve [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Unity proje yapısını anlamak Unity analiz eder, Elbette gibi hizmetleri genel çerçeveleri daha çok daha anlamlı analizi sağlar.|



