---
title: Dağıtımdan sonra sorunları tanılama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
caps.latest.revision: 66
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6c4c60265fda66f7506fe6d886fa671527c1587
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785462"
---
# <a name="diagnose-problems-after-deployment"></a>Dağıtımdan sonra sorunları tanılama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliTrace kullanarak dağıtımdan sonra ASP.NET web uygulamanızdaki sorunları tanılamak için Visual Studio otomatik olarak doğru kaynak dosyalarını ve hata ayıklama IntelliTrace günlüğü için gerekli olan simge dosyalarını Bul izin vermek için sürümle yapı bilgilerini içerir.  
  
 IntelliTrace denetlemek için Microsoft Monitoring Agent'ı kullanıyorsanız, aynı zamanda uygulama performansı web sunucunuz üzerinde izleme ayarlama ayarlamanıza gerek. Uygulamanızı çalışır ve olayları bir IntelliTrace günlük dosyasına kaydeder. Bu tanılama olaylarını kaydeder. Ardından olayları Visual Studio Enterprise (ancak değil Professional veya Community sürümlerini) bakın, bir olayın gerçekleştiği koda gitmek kayıtlı değerlere zamandaki o noktada göz ve çalışan kod ileteceğini veya geriye doğru taşıyın. Bulup sorunu sonra derleme, sürüm ve gelecekteki olası sorunları önceden ve daha hızlı çözebilmek sürümünüzü izlemek için döngüyü tekrarlayın.  
  
 ![Kod, derleme, sürüm, izleyin, tanılayın, düzeltin](../debugger/media/ffr-cycle.png "FFR_Cycle")  
  
 **Şunları yapmanız gerekir:**  
  
-   Visual Studio 2015 veya Team Foundation Server 2015, 2013, 2012 veya 2010 'un yapınızı kurun  
  
-   Microsoft Monitoring Agent'ı uygulama ve kayıt tanılama verilerinizi izlemek için  
  
-   Tanılama verilerini gözden geçirmek ve kodunuzu IntelliTrace ile hata ayıklamak için Visual Studio Enterprise'ı (ancak Professional veya Community sürümlerini)  
  
##  <a name="SetUpBuild"></a> 1. adım: Dahil, sürüm bilgileri oluşturun  
 Web projeniz için bir derleme bildirimi (Buildınfo.config dosyası) oluşturmak için yapı işleminizi ayarlayın ve sürümünüzü ile bu bildirimi içerir. Bu bildirimi, proje, kaynak denetimi ve belirli bir yapı oluşturmak için kullanılan derleme sistemi hakkında bilgi içerir. Bu bilgiler, kayıtlı olayları gözden geçirmek için IntelliTrace günlük açtıktan sonra eşleşen kaynak ve simgeleri bulmak Visual Studio yardımcı olur.  
  
###  <a name="AutomatedBuild"></a> Team Foundation Server kullanarak otomatik bir yapı için derleme bildirimi oluşturma  
 Team Foundation sürüm denetimi veya Git kullanıp aşağıdaki adımları izleyin.  
  
####  <a name="TFS2013"></a> Team Foundation Server 2013  
 Derleme bildirimi (Buildınfo.config dosyası) için kaynak, yapı ve simge konumları eklemek için yapı tanımınızı ayarlayın. Team Foundation Yapısı otomatik olarak bu dosyayı oluşturur ve projenizin çıkış klasörüne yerleştirir.  
  
1. [Yapı tanımını düzenleyin veya yeni bir yapı tanımı oluşturun.](http://msdn.microsoft.com/library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)  
  
    ![Görünüm derleme tanımını TFS 2013'te](../debugger/media/ffr-tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")  
  
2. Varsayılan şablon (TfvcTemplate.12.xaml) veya kendi özel şablonunuzu seçin.  
  
    ![Derleme işlem şablonu seçme &#45; TFS 2013'ün](../debugger/media/ffr-tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  
  
3. Sembol (PDB) dosyası, kaynağınız otomatik olarak endeksleyen kaydedileceği yeri belirtin.  
  
    Özel bir şablon kullanırsanız, şablonun kaynağınızı dizinleyecek bir aktivitesi olduğundan emin olun. Daha sonra semboller dosyalarının kaydedileceği yeri belirtmek için bir MSBuild bağımsız değişkeni de ekleyeceksiniz.  
  
    ![TFS 2013 yapı tanımı içindeki semboller yolu ayarlama](../debugger/media/ffr-tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  
  
    Simgeler hakkında daha fazla bilgi için bkz. [sembol verilerini yayımlama](http://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6).  
  
4. Yapı bildirim dosyası, TFS ve simge konumları eklemek için bu MSBuild bağımsız değişkenini ekleyin:  
  
    **/p:IncludeServerNameInBuildInfo = true**  
  
    Web sunucunuza erişebilen herkes bu konumlar derleme bildiriminde görebilirsiniz. Kaynak sunucunuzun güvenli olduğundan emin olun.  
  
5. Özel bir şablon kullanırsanız, sembol dosyası kaydedileceği yeri belirtmek için bu MSBuild bağımsız değişkenini ekleyin:  
  
    **buildsymbolstorepath =**\<*sembol yolu*>  
  
    ![Derleme def TFS 2013 yapı sunucu bilgisi dahil](../debugger/media/ffr-tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")  
  
    Ve web proje dosyanıza (.csproj, .vbproj) bu satırları ekleyin:  
  
   ```  
   <!-- Import the targets file. Change the folder location as necessary. -->  
      <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />  
  
   ```  
  
6. Yeni bir yapı çalıştırın.  
  
   **2. adım:** [2. adım: uygulamanızı dağıtın](#DeployRelease)  
  
####  <a name="TFS2012_2010"></a> Team Foundation Server 2012 veya 2010  
 Otomatik olarak projeniz için derleme bildirimini (Buildınfo.config dosyası) oluşturun ve dosyayı projenizin çıkış klasörüne yerleştirmek için aşağıdaki adımları izleyin. Dosya olarak görünür "*ProjectName*. "Çıktı klasöründe Buildınfo.config ancak olan uygulamanızı yayımladıktan sonra dağıtım klasörü" Buildınfo.config"olarak yeniden adlandırıldı.  
  
1. Visual Studio 2013 (herhangi bir sürümü), Team Foundation Yapı sunucusuna yükleyin.  
  
2. Yapı tanımınızda, kaynağı otomatik olarak endeksleyen simgelerin kaydedileceği konumu belirtin.  
  
    Özel bir şablon kullanırsanız, şablonun kaynağınızı dizinleyecek bir aktivitesi olduğundan emin olun.  
  
3. Yapı tanımınıza bu MSBuild bağımsız değişkenlerini ekleyin:  
  
   -   **/p:VisualStudioVersion 12.0 =**  
  
   -   **/p:MSBuildAssemblyVersion 12.0 =**  
  
   -   **/TV:12.0**  
  
   -   **/p:IncludeServerNameInBuildInfo = true**  
  
   -   **buildsymbolstorepath =**\<*sembol yolu*>  
  
4. Yeni bir yapı çalıştırın.  
  
   **2. adım:** [2. adım: uygulamanızı dağıtın](#DeployRelease)  
  
###  <a name="ManualBuild"></a> Visual Studio kullanarak el ile bir derleme için derleme bildirimi oluşturma  
 Otomatik olarak projeniz için derleme bildirimini (Buildınfo.config dosyası) oluşturun ve dosyayı projenizin çıkış klasörüne yerleştirmek için aşağıdaki adımları izleyin. Dosya olarak görünür "*ProjectName*. "Çıktı klasöründe Buildınfo.config ancak olan uygulamanızı yayımladıktan sonra dağıtım klasörü" Buildınfo.config"olarak yeniden adlandırıldı.  
  
1. İçinde **Çözüm Gezgini**, web projenizi kaldırın.  
  
2. Proje (.csproj, .vbproj) dosyasını açın. Bu satırları ekleyin:  
  
   ```xml  
   <!-- **************************************************** -->  
   <!-- Build info -->  
   <PropertyGroup>  
      <!-- Generate the BuildInfo.config file -->  
      <GenerateBuildInfoConfigFile>True</GenerateBuildInfoConfigFile>  
      <!-- Include server name in build info -->   
      <IncludeServerNameInBuildInfo>True</IncludeServerNameInBuildInfo>   
      <!-- Include the symbols path so Visual Studio can find the matching deployed code when you start debugging. -->  
      <BuildSymbolStorePath><path to symbols></BuildSymbolStorePath>  
   </PropertyGroup>  
   <!-- **************************************************** -->  
   ```  
  
3. Güncelleştirilen proje dosyasında denetleyin.  
  
4. Yeni bir yapı çalıştırın.  
  
   **2. adım:** [2. adım: uygulamanızı dağıtın](#DeployRelease)  
  
###  <a name="MSBuild"></a> MSBuild.exe kullanarak elle bir yapı için derleme bildirimi oluşturma  
 Bir yapı çalıştırdığınızda bu bağımsız değişkenleri ekleyin:  
  
 **/p:GenerateBuildInfoConfigFile = true**  
  
 **/p:IncludeServerNameInBuildInfo = true**  
  
 **buildsymbolstorepath =**\<*sembol yolu*>  
  
##  <a name="DeployRelease"></a> 2. adım: uygulamanızı dağıtın  
 Kullanırsanız [Web.Deploy paketini](http://msdn.microsoft.com/library/dd394698.aspx) gelen derleme bildirimi otomatik olarak yeniden adlandırılır, uygulamanızı dağıtmak için derleme işleminiz tarafından oluşturulan "*ProjectName*. "Buildınfo.config" için "Buildınfo.config ve web sunucunuz üzerinde uygulamanızın Web.config dosyasıyla aynı klasöre yerleştirin.  
  
 Uygulamanızı dağıtmak için diğer yöntemleri kullanıyorsanız, derleme bildirimi gelen adlandırılır emin olun "*ProjectName*. "Buildınfo.config" için "Buildınfo.config ve web sunucusundaki uygulamanızın Web.config dosyasıyla aynı klasöre yerleştirin.  
  
## <a name="step-3-monitor-your-app"></a>Adım 3: Uygulamanızı izleyin  
 Uygulamanızı sorunlarını izleme, tanılama olaylarını kaydedin ve bu olayları bir IntelliTrace günlük dosyasına kaydetmek için uygulama performans web sunucunuzda izlemeyi ayarlayın. Bkz: [sürümünüzü dağıtım sorunları için izleme](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
##  <a name="InvestigateEvents"></a> Adım 4: sorunu bulma  
 Visual Studio Enterprise geliştirme bilgisayarınıza veya başka bir bilgisayarda kayıtlı olayları gözden geçirmek ve kodunuzu IntelliTrace kullanarak hata ayıklama için gerekir. CodeLens, hata ayıklayıcı eşlemleri gibi araçları da kullanabilirsiniz ve sorunu tanılamanıza yardımcı olacak kod eşlemeleri.  
  
### <a name="open-the-intellitrace-log-and-matching-solution"></a>IntelliTrace günlüğünü ve eşleşen çözümü açın  
  
1.  Visual Studio Enterprise IntelliTrace günlük (.iTrace dosyası) açın. Veya yalnızca aynı bilgisayarda Visual Studio Enterprise varsa dosyasına çift tıklayın.  
  
2.  Seçin **açık çözüm** projeyi bir çözümün bir parçası oluşturulmadıysa Visual Studio'nun eşleştirme çözümünü veya projeyi otomatik olarak açılmasını sağlamak için. [S: IntelliTrace günlük dağıtılan Uygulamam hakkında bilgiler eksik. Neden bu ortaya çıktı? Ne yapmalıyım?](#InvalidConfigFile)  
  
     Eşleştirme çözümünü veya projeyi açtığında, visual Studio tüm bekleyen değişiklikleri otomatik olarak kaldırır. Bu raf kümesi hakkında daha fazla bilgi edinmek için konum **çıkış** penceresi veya **Takım Gezgini**.  
  
     Herhangi bir değişiklik yapmadan önce doğru kaynağa sahip olduğunuzu onaylayın. Dallanma kullanıyorsanız, burada Visual Studio, yayın dalı gibi eşleşen kaynak bulduğu değerinden farklı bir dalda çalışıyor olabilirsiniz.  
  
     ![IntelliTrace günlüğünden çözümü açın](../debugger/media/ffr-itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")  
  
     Bu çözüm veya proje eşlenmiş mevcut bir çalışma alanı varsa, Visual Studio, bulunan kaynağı yerleştirmek için bu çalışma alanını seçer.  
  
     ![Açık kaynak denetiminden eşleşmiş bir çalışma alanı](../debugger/media/ffr-openprojectfromsourcecontrol-mapped.png "FFR_OpenProjectFromSourceControl_Mapped")  
  
     Aksi halde, zaten eşleşmiş başka bir çalışma alanı seçin veya yeni bir çalışma alanı oluşturun. Visual Studio tüm dalı bu çalışma alanına eşleyecektir.  
  
     ![Kaynak Denetiminden Aç &#45; yeni çalışma alanı oluşturma](../debugger/media/ffr-openprojectfromsourcecontrol-createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")  
  
     Belirli eşleşmeler veya bilgisayarınızın adı olmayan bir ad ile bir çalışma alanı oluşturmak için seçin **Yönet**.  
  
     [S: neden Visual Studio seçili çalışma alanımın uygun olmadığını söylüyor?](#IneligibleWorkspace)  
  
     [S: Ben bir takım koleksiyonu veya farklı bir koleksiyon seçinceye kadar niçin devam edemiyorum?](#ChooseTeamProject)  
  
### <a name="diagnose-a-performance-problem"></a>Performans sorunu tanıla  
  
1.  Altında **performans ihlallerinin**, kaydedilen performans olaylarını, bunların toplam yürütme sürelerini ve diğer olay bilgilerini gözden geçirin. Sonra belirli performans olayı sırasında çağrılan yöntemlerde fazla araştırma yapın.  
  
     ![Performans Olay Ayrıntıları Görüntüle](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     Ayrıca, olayı çift tıklatabilirsiniz.  
  
2.  Olay sayfasında, bu çağrılar için yürütme zamanını gözden geçirin. Yürütme ağacında yavaş bir çağrı bulun.  
  
     İç içe ya da başka şekilde birden fazla çağrınız varsa, en yavaş çağrılar kendi bölümünde görüntülenir.  
  
     Yuvalanmış çağrıları ve zamanın o anında kaydedilmiş değerleri gözden geçirmek için o çağrıyı genişletin. Sonra o çağrıdan hata ayıklamayı başlatın.  
  
     ![Yöntem çağrısından hata ayıklamayı Başlat](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     Ayrıca, aramayı çift tıklatabilirsiniz.  
  
     Yöntem uygulama kodunuzda ise, Visual Studio bu yönteme gider.  
  
     ![Performans olayından uygulama koduna gidin](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     Kaydedilmiş diğer değerleri çağrı yığını gözden geçirebilir kodunuzda adım adım veya kullanın **IntelliTrace** penceresine [geriye veya ileten diğer yöntemler arasında "zamanda" taşıma](../debugger/intellitrace.md) sırasında çağırılan Bu performans olayı. [Bu diğer tüm olayları ve IntelliTrace günlüğünde bilgi nedir? ](../debugger/using-saved-intellitrace-data.md) [Buradan başka ne yapabilirim?](#WhatElse) [Performans olayları hakkında daha fazla bilgi istiyor?](http://blogs.msdn.com/b/visualstudioalm/archive/2013/09/20/performance-details-in-intellitrace.aspx)  
  
### <a name="diagnose-an-exception"></a>Bir özel durumu tanıla  
  
1.  Altında **özel durum verileri**, kaydedilen özel durum olaylarını, türleri, iletileri gözden geçirin ve özel durumların ne zaman oluştuğunu. Kodu daha ayrıntılı incelemek için özel durumlar grubu içindeki en son olaydan başlayın.  
  
     ![Özel durum bir olaydan hata ayıklamaya başlamak](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     Ayrıca, olayı çift tıklatabilirsiniz.  
  
     Uygulama kodunuzda bir özel durum oluştuysa, Visual Studio özel durumun olduğu yere gider.  
  
     ![Gelen bir özel durum olayı uygulama koduna gidin](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     Kaydedilmiş diğer değerleri çağrı yığını gözden geçirin veya kullanmak artık **IntelliTrace** penceresine [geriye veya ileten diğer kaydedilen olaylar arasında "zamanda" taşıma](../debugger/intellitrace.md), ilgili kod ve sırasında kaydedilmiş değerler Bu zaman noktaları. [Bu diğer tüm olayları ve IntelliTrace günlüğünde bilgi nedir?](../debugger/using-saved-intellitrace-data.md)  
  
###  <a name="WhatElse"></a> Buradan başka ne yapabilirim?  
  
-   [Bu kod hakkında daha fazla bilgi edinin](../ide/find-code-changes-and-other-history-with-codelens.md). Bu kod başvurularını bulmak için Düzenleyicisi'nde CodeLens göstergeleri değişiklik geçmişi, ilgili hatalar, iş öğeleri, kod incelemeleri veya birim testleri – tüm düzenleyicisinden çıkmadan - kullanın.  
  
     ![CodeLens &#45; görüntülemek için bu kodu başvuruları](../debugger/media/ffr-itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")  
  
     ![CodeLens &#45; görünümü değiştirmek için bu kod geçmişini](../debugger/media/ffr-itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")  
  
-   [Hata ayıklarken koddaki yerinizi eşleyin.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) Hata ayıklama sırasında aranan yöntemleri görsel izlemek için çağrı yığınını eşleyin.  
  
     ![Hata ayıklarken çağrı yığınında eşleştirme](../debugger/media/ffr-itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")  
  
###  <a name="FAQ"></a> SORU- CEVAP  
  
####  <a name="WhyInclude"></a> S: neden proje, kaynak denetimi, derleme ve sürümüm sembolleriyle hakkında bilgi dahil edilsin mi?  
 Visual Studio, kaynak ve eşleşen çözümü, hata ayıklama çalıştığınız sürümü bulmak için bu bilgileri kullanır. IntelliTrace günlüğünü açın ve hata ayıklamayı başlatmak için bir olay seçin sonra Visual Studio sembolleri bulun ve olayın gerçekleştiği kodu göstermek için kullanır. Ardından, kaydedilmiş değerlere göz ve kodunuzun yürütme ileteceğini veya geriye doğru bir şekilde taşıyabilirsiniz.  
  
 TFS ve bu bilgileri kullanıyorsanız, derleme bildirimi (Buildınfo.config dosyası), Visual Studio arar eşleşen kaynağa ve sembollere şu anda bağlı TFS üzerinde değil. Visual Studio doğru TFS veya eşleşen kaynağı bulamıyorsanız, farklı bir TFS seçmenizi istenir.  
  
####  <a name="InvalidConfigFile"></a> S: IntelliTrace günlük dağıtılan Uygulamam hakkında bilgiler eksik. Neden bu ortaya çıktı? Ne yapmam gerekir?  
 Bu geliştirme bilgisayarınızdan dağıttığınızda veya dağıtım sırasında TFS'ye bağlı değilseniz gerçekleşebilir.  
  
1.  Projenizin dağıtım klasörüne gidin.  
  
2.  Bul ve derleme bildirimi (Buildınfo.config dosyası) açın.  
  
3.  Dosyanın gerekli bilgileri içerdiğinden emin olun:  
  
- **projectName**  
  
   Projenizi Visual Studio'da adı. Örneğin:  
  
  ```  
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>  
  ```  
  
- **SourceControl**  
  
- Kaynak Denetim sisteminizle ve bunlar hakkında bilgi özellikleri gerekli:  
  
  - **TFS**  
  
    - **ProjectCollectionUri**: Team Foundation Server ve proje koleksiyonunuz için URI  
  
    - **Projectıtemspec**: uygulamanızın proje dosyasına (.csproj veya .vbproj) yolu  
  
    - **ProjectVersionSpec**: projeniz için yeni sürümü  
  
      Örneğin:  
  
    ```  
    <SourceControl type="TFS">  
       <TfsSourceControl>  
          <ProjectCollectionUri>http://fabrikamfiber:8080/tfs/FabrikamFiber</ProjectCollectionUri>  
          <ProjectItemSpec>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectItemSpec>  
          <ProjectVersionSpec>LFabrikamFiber_BuildAndPublish_20130813@$/WorkInProgress</ProjectVersionSpec>  
       </TfsSourceControl>  
    </SourceControl>  
    ```  
  
  - **Git**  
  
    - **GitSourceControl**: konumunu **GitSourceControl** şeması  
  
    - **RepositoryUrl**: Team Foundation Server, proje koleksiyonu ve Git deposu için URI  
  
    - **ProjectPath**: uygulamanızın proje dosyasına (.csproj veya .vbproj) yolu  
  
    - **Commitıd**: kaydınızı kimliği  
  
      Örneğin:  
  
    ```  
    <SourceControl type="Git">   
       <GitSourceControl xmlns="http://schemas.microsoft.com/visualstudio/deploymentevent_git/2013/09">  
          <RepositoryUrl>http://gittf:8080/tfs/defaultcollection/_git/FabrikamFiber</RepositoryUrl>  
          <ProjectPath>/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectPath>  
          <CommitId>50662c96502dddaae5cd5ced962d9f14ec5bc64d</CommitId>  
       </GitSourceControl>  
    </SourceControl>  
    ```  
  
- **Derleme**  
  
   Yapı sisteminizi hakkında bilgi ya da `"TeamBuild"` veya `"MSBuild"`, ve bunlar gerekli özellikler:  
  
  - **BuildLabel** (TeamBuild için için): derleme adı ve numarası. Bu etiket, ayrıca dağıtım olay adı olarak kullanılır. Derleme numaraları hakkında daha fazla bilgi için bkz. [kullanılan yapı numaralarını tamamlanan yapılara anlamlı adlar vermek için](http://msdn.microsoft.com/library/1f302e9d-4b0a-40b5-8009-b69ca6f988c3).  
  
  - **SymbolPath** (önerilen): URI listesi için Sembol (PDB dosyası) konumlarınıza noktalı virgüllerle ayrılmış. Bu URI'ler URL'ler veya UNC olabilir. Bu, hatalarını ayıklamaya yardımcı olmak için eşleşen simgeleri bulmak Visual Studio için kolaylaştırır.  
  
  - **BuildReportUrl** (için TeamBuild için): TFS'de yapı raporunun konumu  
  
  - **Buildıd** (için TeamBuild için): TFS'de yapı için URI ayrıntıları. Bu URI, ayrıca dağıtım Olay No olarak kullanılır. Bu kimliği TeamBuild kullanmıyorsanız, benzersiz olmalıdır gerekir.  
  
  - **BuiltSolution**: Visual Studio çözüm dosyasının yolu bulmak ve eşleşen çözümü açmak için kullanır. Bu içeriği, **SolutionPath** MsBuild özelliği.  
  
    Örneğin:  
  
  - **TFS**  
  
    ```  
    <Build type="TeamBuild">  
       <MsBuild>  
          <BuildLabel kind="label">FabrikamFiber_BuildAndPublish_20130813.1</BuildLabel>  
          <SymbolPath>\\fabrikamfiber\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuildReportUrl kind="informative, url" url="http://fabrikamfiber:8080/tfs/FabrikamFiber/_releasePipeline/FindRelease?buildUri=fabrikamfiber%3a%2f%2f%2fBuild%2fBuild%2f448">Build Report Url</BuildReportUrl>  
          <BuildId kind="id">1c4444d2-518d-4673-a590-dce2773c7744,fabrikamfiber:///Build/Build/448</BuildId>  
          <BuiltSolution>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MsBuild>  
    </Build>  
    ```  
  
  - **Git**  
  
    ```  
    <Build type="MSBuild">   
       <MSBuild>  
          <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MSBuild>  
    </Build>  
    ```  
  
####  <a name="IneligibleWorkspace"></a> S: neden Visual Studio seçili çalışma alanımın uygun olmadığını söylüyor?  
 **Y:** seçilen çalışma alanı, kaynak denetim klasörü ve yerel klasör arasında herhangi bir eşlemeye sahip değil. Bu çalışma alanına ilişkin bir eşleme oluşturmak için seçin **Yönet**. Aksi halde, zaten eşleşmiş bir çalışma alanı seçin veya yeni bir çalışma alanı oluşturun.  
  
 ![Eşleşmiş bir çalışma alanı ile kaynak denetiminden Aç](../debugger/media/ffr-openprojectfromsourcecontrol-notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")  
  
####  <a name="ChooseTeamProject"></a> S: Ben bir takım koleksiyonu veya farklı bir koleksiyon seçinceye kadar niçin devam edemiyorum?  
 **Y:** Bu nedenlerden biriyle gerçekleşebilir:  
  
-   Visual Studio TFS'ye bağlı değildir.  
  
     ![Kaynak Denetiminden Aç &#45; bağlı](../debugger/media/ffr-openprojectfromsourcecontrol-notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")  
  
-   Visual Studio geçerli takım koleksiyonunuzda çözüm ya da proje bulamadı.  
  
     Yapı bildirim dosyası (\<*ProjectName*>. Buildınfo.config) Visual Studio'nun eşleşen kaynağı nerede belirlemek değil Visual Studio eşleşen çözümü veya projeyi bulmak için şu anda bağlı olan TFS'nizi kullanır. Geçerli takım koleksiyonunuzda eşleşen kaynak yoksa, Visual Studio farklı takım koleksiyonuna bağlanmanızı ister.  
  
-   Visual Studio bulamadı çözüm veya projeyi yapı bildirim dosyası tarafından belirlenmiş koleksiyonda (\<*ProjectName*>. Buildınfo.config).  
  
     Belirtilen TFS artık eşleşen kaynağa sahip olmayabilir, hatta yeni bir TFS'ye geçtiğiniz için hiç varolmayabilir. Belirtilen TFS mevcut değilse Visual Studio bir dakika ya da sonrasında zaman aşımına uğrayabilir ve bu durumda sizden farklı bir koleksiyona bağlanmanız istenebilir. Devam etmek için doğru TFS sunucusuna bağlanın.  
  
     ![Kaynak Denetiminden Aç &#45; geçişi](../debugger/media/ffr-openprojectfromsourcecontrol-migrated.png "FFR_OpenProjectFromSourceControl_Migrated")  
  
####  <a name="WhatWorkspace"></a> S: bir çalışma alanı nedir?  
 **Y:** , [çalışma alanı, kaynak kopyasını depoladığından](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a) geliştirebilir ve bunu ayrı olarak önce onay çalışmanızı test edebilirsiniz. Bulunan çözümle veya projeyle özel olarak eşleşen bir çalışma alanı yoksa, Visual Studio varsayılan çalışma alanı adı olarak bilgisayar adınızla birlikte yeni bir çalışma alanı oluşturmanızı veya mevcut bir çalışma alanı seçmenizi ister.  
  
####  <a name="UntrustedSymbols"></a> Güvenilmeyen simgeler hakkında bu iletiyi neden alıyorum?  
 ![Güvenilmeyen simgeler yolu ile hata ayıklama? ](../debugger/media/ffr-ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")  
  
 **Y:** bu ileti görüntülenir yapı bildirim dosyası içindeki semboller yolu (\<*ProjectName*>. Buildınfo.config) güvenilir sembol yolları listesine dahil değildir. Hata ayıklama seçeneklerindeki sembol yolu listesine yolu ekleyebilirsiniz.





