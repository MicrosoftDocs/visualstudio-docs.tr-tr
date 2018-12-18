---
title: Uzaktan hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ac1bbe2cc1832d0b34706f88b4df583d117149c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799281"
---
# <a name="remote-debugging"></a>Uzaktan Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Farklı bir bilgisayara dağıtılan bir Visual Studio uygulamada hata ayıklaması yapabilirsiniz.  Bunu yapmak için Visual Studio uzaktan hata ayıklayıcıyı kullanın.  
  
 Buradaki bilgiler, Windows Masaüstü uygulamaları ve ASP.NET uygulamaları için geçerlidir.  Uzaktan hata ayıklama Windows Store uygulamaları ve Azure uygulamaları hakkında daha fazla bilgi için bkz. [Windows Store ve Azure uygulamalarında uzaktan hata ayıklama](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Uzak araçları edinin  
Uzak Araçlar cihaz veya hata ayıklama veya, kaydetmek istediğiniz sunucu üzerinde doğrudan uzak araçları Visual Studio yüklü konak makinenizden alabilirsiniz indirin kullanabilirsiniz.

### <a name="to-download-and-install-the-remote-tools"></a>Uzak araçları indirme ve yükleme için
  
1.  Cihaz veya sunucu, hata ayıklamak istediğiniz makine (yerine Visual Studio çalıştıran makinenin), uzak Araçlar'ın doğru sürümü alın.

    |Sürüm|Bağlantı|Notlar|
    |-|-|-|
    |Visual Studio 2015 Güncelleştirme 3|[Uzak Araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|İstenirse, ücretsiz Visual Studio Dev Essentials gruba katılın veya yalnızca geçerli Visual Studio aboneliği ile oturum açabilirsiniz. Ardından bağlantıyı gerekirse yeniden açın. Her zaman eşleştirme (x 86, x64 veya ARM sürümü), cihaz işletim sistemi sürümü indirin|
    |Visual Studio 2015 (eski)|[Uzak Araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|İstenirse, ücretsiz Visual Studio Dev Essentials gruba katılın veya yalnızca geçerli Visual Studio aboneliği ile oturum açabilirsiniz. Ardından bağlantıyı gerekirse yeniden açın.|
    |Visual Studio 2013|[Uzak Araçlar](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2013 belgeleri sayfasında indirin|
    |Visual Studio 2012|[Uzak Araçlar](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2012 belgeleri sayfasında indirin|
  
2.  İndirme sayfasında, işletim sistemiyle (x 86, x64 veya sürüm ARM) eşleşen araçları sürümünü seçin ve uzak araçları indirmek.
  
    > [!IMPORTANT]
    >  Visual Studio sürümünüzle eşleşen uzak Araçlar'ın en son sürümünü yüklemeniz önerilir. Eşleşmeyen sürümler önerilmez.  
    >   
    >  Ayrıca, yüklemek istediğiniz işletim sistemi olarak aynı mimariye sahip uzak araçları yüklemeniz gerekir. Diğer bir deyişle, bir 64-bit işletim sistemi çalıştıran bir uzak bilgisayarda bir 32 bit uygulama hata ayıklamak istiyorsanız, uzak bilgisayarda Uzak Araçlar'ın 64 bit sürümü yüklemeniz gerekir.  
  
3.  Yürütülebilir dosya indirme işlemini tamamladıktan sonra uygulamayı uzak bilgisayara yüklemek için yönergeleri izleyin. Bkz: [kurulum yönergeleri](#bkmk_setup)

Uzaktan hata ayıklayıcı (msvsmon.exe) uzak bilgisayara kopyalayın ve çalıştırmak çalışırsanız unutmayın, **uzaktan hata ayıklayıcı Yapılandırma Sihirbazı'nı** (**rdbgwiz.exe**) yalnızca karşıdan yüklenir Özellikle, bir hizmet olarak çalıştırmak için uzaktan hata ayıklayıcı istediğiniz araçları ve daha sonra Yapılandırma Sihirbazı'nı kullanmayı gerekebilir. Daha fazla bilgi için [(isteğe bağlı) yapılandırma hizmet olarak uzaktan hata ayıklayıcı](#bkmk_configureService) aşağıda.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırmak için

Uzaktan hata ayıklayıcıyı bulabilirsiniz (**msvsmon.exe**) bir bilgisayarda Visual Studio 2015 Community, Professional veya Enterprise zaten yüklü. Birçok senaryo için uzaktan hata ayıklamayı kurma en kolay yolu uzaktan hata ayıklayıcı (msvsmon.exe) bir dosya paylaşımından çalıştırmaktır. Kullanım kısıtlamaları için uzaktan hata ayıklayıcının yardım sayfasına bakın (**Yardım / kullanım** uzaktan hata ayıklayıcı).

1. Bulma **msvsmon.exe** Visual Studio sürümünüzle eşleşen dizinde. Visual Studio 2015 için:

      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Paylaşım **uzaktan hata ayıklayıcı** Visual Studio bilgisayardaki klasör.

3. Uzak bilgisayarda çalıştırmak **msvsmon.exe**. İzleyin [kurulum yönergeleri](#bkmk_setup).

> [!TIP] 
> Komut satırı yükleme ve komut satırı başvurusu için yardım sayfasına bakın **msvsmon.exe** yazarak ``msvsmon.exe /?`` Visual Studio'nun yüklü olan bilgisayarda bir komut satırında (veya Git **Yardım / kullanım**uzaktan hata ayıklayıcı).

  
## <a name="supported-operating-systems"></a>Supported Operating Systems  
 Uzak bilgisayarın aşağıdaki işletim sistemlerinden birini çalıştırmalıdır:  
  
-   Windows 10  
  
-   Windows 8 veya 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 veya Windows Server 2012 R2  
  
-   Windows Server 2008 hizmet paketi 2, Windows Server 2008 R2 hizmet paketi 1  
  
## <a name="supported-hardware-configurations"></a>Desteklenen donanım yapılandırmaları  
  
-   1,6 GHz veya daha hızlı işlemci  
  
-   1 GB RAM (sanal makinede çalıştırılıyorsa 1,5 GB)  
  
-   1 GB kullanılabilir sabit disk alanı  
  
-   5400 RPM sabit sürücü  
  
-   1024 x 768 veya daha yüksek görüntü çözünürlüğünde çalışan DirectX 9 uyumlu ekran kartı  
  
## <a name="network-configuration"></a>Ağ yapılandırması  
 Uzak bilgisayar ve Visual Studio bilgisayarı bir ağ, çalışma grubu veya ev grubu bağlı desteklemeli veya doğrudan Ethernet kablosu ile bağlı. Internet üzerinden hata ayıklama desteklenmiyor.  
  
## <a name="bkmk_setup"></a>Uzaktan hata ayıklayıcı ayarlayın  
 Uzak bilgisayarda yönetici izinlerinizin olması gerekir  
  
1. Uzaktan hata ayıklayıcı uygulamasını bulun. (Başlat menüsünü açın ve arama **uzaktan hata ayıklayıcı**.)
  
    Uzaktan hata ayıklayıcı uzak bir sunucuda çalışıyorsa, uzaktan hata ayıklayıcı uygulama sağ tıklatın ve seçin **yönetici olarak çalıştır** (veya, uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırmak). Uzak bir sunucuda, çalıştırmıyorsanız yalnızca başlatın normalde.
  
2. Başladığınızda uzak araçları ilk kez (veya yapılandırmış olduğunuz önce), **uzaktan hata ayıklama Yapılandırması** dalog kutusu görüntülenir.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Windows hizmeti API'si (yalnızca Windows Server 2008 R2 üzerinde gerçekleşen) yüklü değilse seçin **yükleme** düğmesi.  
  
4. Uzak araçları kullanmak istediğiniz ağ türlerini seçin. En az bir ağ türü seçilmelidir. Bilgisayarları bir etki alanına bağlıysanız, ilk öğe seçmeniz gerekir. Bilgisayar bir çalışma grubunda veya ev grubu bağlıysa, uygun şekilde ikinci veya üçüncü öğe seçmek gerekir.  
  
5. Seçin **uzaktan hata ayıklamayı Yapılandır** güvenlik duvarını ve Aracı'nı başlatın.  
  
6. Yapılandırma tamamlandıktan sonra uzaktan hata ayıklayıcı penceresi görüntülenir.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Uzaktan hata ayıklayıcı şimdi bir bağlantı için bekliyor. Sunucu adını not edin ve bunu daha sonra Visual Studio'da yapılandırması için ihtiyacınız olacağı için bağlantı noktası görüntülenir, numarası.  
  
   Hata ayıklama ve uzaktan hata ayıklayıcıyı gerek bittiğinde tıklatın **dosya / çıkış** penceresinde. Buradan yeniden **Başlat** menüsünden veya komut satırından:  
  
   **\<Visual Studio yükleme dizini > \Common7\IDE\Remote hata ayıklayıcı\\< x86, x64 veya Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Uzaktan hata ayıklayıcı yapılandırma  
 İlk kez başlattıktan sonra bazı yönleri uzaktan hata ayıklayıcı yapılandırmasını değiştirebilirsiniz.
  
- Uzaktan hata ayıklayıcıya bağlanmak diğer kullanıcılara etkinleştirmeyi seçerseniz **araçları / izinleri**. İzinleri vermek veya reddetmek için yönetici ayrıcalıklarınızın olması gerekir.

  > [!IMPORTANT]
  > Visual Studio bilgisayarda kullandığınız kullanıcı hesabına ait farklı bir kullanıcı hesabı altında uzaktan hata ayıklayıcı çalıştırabilirsiniz, ancak farklı bir kullanıcı hesabı için uzaktan hata ayıklayıcının izinleri eklemeniz gerekir. 

   Alternatif olarak, komut satırından uzaktan hata ayıklayıcıyı başlatabilirsiniz **/ allow \<kullanıcıadı >** parametresi: **msvsmon / allow \< username@computer>**.
  
- Kimlik doğrulama modunu veya bağlantı noktası numarasını değiştirmek veya uzak araçlar için bir zaman aşımı değeri belirtmek için: seçin **Araçlar / Seçenekler**.  
  
   Varsayılan olarak kullanılan bağlantı noktası numaraları listesi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  >  Uzak araçları Kimlik Doğrulaması Yok modunda çalıştırmayı seçebilirsiniz, fakat bu mod kesinlikle önerilmez. Bu modda çalıştırdığınızda, ağ güvenliği yoktur. Yalnızca ağ kötü amaçlı veya tehlikeli trafik karşı risk altında olduğunu eminseniz kimlik doğrulaması yok modu seçin.

##  <a name="bkmk_configureService"></a> (İsteğe bağlı) Uzaktan hata ayıklayıcıyı bir hizmet olarak yapılandırma
 ASP.NET ve diğer sunucu ortamlarında hata ayıklama için uzaktan hata ayıklayıcı yönetici olarak çalıştırın veya gerekir, her zaman çalışır, isterseniz, uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırın.
  
 Uzaktan hata ayıklayıcıyı bir hizmet olarak yapılandırmak istiyorsanız, aşağıdaki adımları izleyin.  
  
1. Bulma **uzaktan hata ayıklayıcı Yapılandırma Sihirbazı'nı** (rdbgwiz.exe). (Uzaktan hata ayıklayıcı ayrı bir uygulamadan budur.) Yalnızca uzak araçları yüklediğinizde kullanılabilir. Visual Studio ile yüklü değil.  
  
2. Yapılandırma Sihirbazı'nı çalıştırmaya başlayın İlk sayfasına geldiğinde tıklayın **sonraki**.  
  
3. Denetleme **Visual Studio 2015 uzaktan hata ayıklayıcı bir hizmet olarak çalıştırmak** onay kutusu.  
  
4. Parola ve hesap adını ekleyin.  
  
    Eklemeniz gerekebilir **hizmet oturum açma** bu hesap için doğru kullanıcı. (Bul **yerel güvenlik ilkesi** (secpol.msc) içinde **Başlat** sayfası veya pencere (veya türü **secpol** bir komut isteminde). Penceresi açıldığında, çift **kullanıcı hakları ataması**, ardından bulun **hizmet oturum açma** sağ bölmede. Çift tıklatın. Kullanıcı hesabına eklemek **özellikleri** penceresini açın ve **Tamam**.) **İleri**'ye tıklayın.  
  
5. Uzak araçların iletişim kurmak istediğiniz ağ türünü seçin. En az bir ağ türü seçilmelidir. Bilgisayarları bir etki alanına bağlıysanız, ilk öğe seçmeniz gerekir. Bilgisayar bir çalışma grubunda veya ev grubu bağlıysa, ikinci veya üçüncü öğe seçmeniz gerekir. **İleri**'ye tıklayın.  
  
6. Hizmetin başlatılması, görürsünüz **Visual Studio uzaktan hata ayıklayıcı Yapılandırma Sihirbazı başarıyla tamamladınız**. Hizmet başlatılamazsa göreceğiniz **Visual Studio uzaktan hata ayıklayıcı Yapılandırma Sihirbazı tamamlanamadı**. Sayfa aynı zamanda hizmetin başlatılması almak için izlemeniz gereken bazı ipuçları sağlar.  
  
7. **Son**'a tıklayın.  
  
   Bu noktada uzaktan hata ayıklayıcıyı bir hizmet olarak çalışıyor. Bu sayfasına giderek kontrol **Denetim Masası / Hizmetleri** ve örnek kod **Visual Studio 2015 uzaktan hata ayıklayıcı**.  
  
   Uzaktan hata ayıklayıcı hizmetini durdurup **Denetim Masası / Hizmetleri**.  

## <a name="remote-debug-an-aspnet-application"></a>Uzaktan hata ayıklama ASP.NET uygulaması  
 IIS çalıştıran bir uzak bilgisayara bir ASP.NET uygulaması dağıtma, IIS sürümü ve işletim sistemine bağlı olarak farklı adımlar vardır. IIS 7.5 veya sonraki bir sürümü yüklüyse lütfen bkz. Windows Server 2008 veya Windows Server 2012 çalıştıran uzak bilgisayarlar için [uzak bir IIS bilgisayarda uzaktan hata ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 ASP.NET Core uygulaması hata ayıklaması yapıyorsanız bkz [IIS yayımlama](https://docs.asp.net/en/latest/publishing/iis.html). IIS'de bir ASP.NET Core yayımlamak için farklı adımlar gerekir. ASP.NET Core uygulaması başarıyla yayımladıktan sonra uzaktan bağlanabilir, hata ayıklama [tıpkı diğer ASP.NET uygulamalarını olduğu gibi](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), w3wp.exe yerine dnx.exe eklemek için gereken işlem olması dışında.

## <a name="remote-debug-a-visual-c-project"></a>Visual C++ projesinin hatalarını uzaktan ayıklama  
 Aşağıdaki yordamda projesinin yolunu ve adını C:\remotetemp\MyMfc ve uzak bilgisayarın adını **MJO DL**.  
  
1. Adlı bir MFC uygulaması oluşturmak **mymfc.**  
  
2. Herhangi bir kolayca, örnekte için ulaşıldığında uygulamada bir kesme noktası ayarlayın **MainFrm.cpp**, başlangıcında `CMainFrame::OnCreate`.  
  
3. Çözüm Gezgini'nde sağ tıklatın ve proje **özellikleri**. Açık **hata ayıklama** sekmesi.  
  
4. Ayarlama **başlatmak için hata ayıklayıcı** için **uzaktan Windows hata ayıklayıcı**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Aşağıdaki özelliklerde değişiklik:  
  
   |Ayar|Değer|
   |-|-|  
   |Uzaktan komut|C:\remotetemp\mymfc.exe|  
   |Çalışma dizini|C:\remotetemp|  
   |Uzak sunucu adı|MJO DL:*BağlantıNoktasıNumarası*|  
   |bağlantı|Windows kimlik doğrulaması ile uzaktan|  
   |Hata ayıklayıcı türü|Yalnızca yerel|  
   |Dağıtım dizini|C:\remotetemp.|  
   |Dağıtılacak ek dosyalar|C:\data\mymfcdata.txt.|  
  
    (İsteğe bağlı) ek dosyaları dağıtmak istiyorsanız her iki makinelerde klasörü bulunmalıdır.  
  
6. Çözüm Gezgini'nde çözüme sağ tıklayıp seçin **Configuration Manager**.  
  
7. İçin **hata ayıklama** yapılandırma, select **Dağıt** onay kutusu.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Hata Ayıklamayı Başlat (**hata ayıklama / hata ayıklamayı Başlat**, veya **F5**).  
  
9. Yürütülebilir dosyayı uzak bilgisayara otomatik olarak dağıtılır.  
  
10. İstenirse, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.  
  
     Gerekli kimlik bilgilerinin, ağınızın güvenlik yapılandırması'nı özgüdür. Örneğin, bir etki alanı bilgisayarında güvenlik sertifikasını seçin veya etki alanı adınızı ve parolanızı girin. Bir etki alanı olmayan makinede, makine adı ve geçerli kullanıcı hesabı adı gibi girebilirsiniz <strong>MJO-DL\name@something.com</strong>, doğru parola ile birlikte.  
  
11. Visual Studio bilgisayarda yürütme kesme noktasında durdurulduğunu görmeniz gerekir.  
  
    > [!TIP]
    >  Alternatif olarak, dosyaların ayrı bir adım olarak dağıtabilirsiniz. İçinde **Çözüm Gezgini** sağ **mymfc** düğümünü seçip **Dağıt**.  
  
    Uygulama tarafından kullanılması gereken kod dışı dosyalara varsa, bunları Visual Studio projenize eklemeniz gerekir. Ek dosyalar için bir proje klasörü oluşturun (içinde **Çözüm Gezgini**, tıklayın **Ekle / yeni klasör**.) Dosyaları klasöre eklersiniz (içinde **Çözüm Gezgini**, tıklayın **Ekle / var olanı öğesi**, ardından dosyaları seçin.). Üzerinde **özellikleri** sayfasında her dosya için **çıkış dizinine Kopyala** için **her zaman Kopyala**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Uzaktan hata ayıklama Visual C# veya Visual Basic projesi  
 Hata ayıklayıcı uzak makinede Visual C# veya Visual Basic Masaüstü uygulamalar dağıtamazsınız, ancak yine de bunları aşağıdaki gösterildiği gibi uzaktan hata ayıklama. Aşağıdaki yordamda adlı bir bilgisayarda hata ayıklamak istediğiniz varsayılmaktadır **MJO DL**önceki resimde gösterildiği gibi.
  
1. Adlı bir WPF projesi oluşturma **MyWpf**.  
  
2. Bir kesme noktası herhangi bir kolayca ulaşıldığında kodda ayarlayın.  
  
    Örneğin, bir düğme işleyicisinde bir kesme noktası ayarlayabilirsiniz. Bunu yapmak için MainWindow.xaml açın ve araç kutusundan bir düğme denetimi ekleyin ve onun işleyicisi açmak için düğmeyi çift tıklatın.
  
3. Çözüm Gezgini'nde projeye sağ tıklayıp seçin **özellikleri**.  
  
4. Üzerinde **özellikleri** sayfasında **hata ayıklama** sekmesi.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Emin **çalışma dizini** metin kutusu boştur.  
  
6. Seçin **uzak makine**ve türü **MJO-DL:4020** metin kutusuna. (4020 uzaktan hata ayıklayıcı penceresinde gösterilen bağlantı noktası numarasıdır).  
  
7. Emin olun **yerel kod hata ayıklamayı** seçilmez.  
  
8. Projeyi oluşturun.  
  
9. Uzak bilgisayarda aynı yol üzerinde bir klasör oluşturun **hata ayıklama** Visual Studio'nun bilgisayarınızda klasörünü:  **\<kaynak yolu > \MyWPF\MyWPF\bin\Debug**.  
  
10. Yalnızca Visual Studio bilgisayarınızdan için yeni oluşturulan klasör uzak bilgisayarda oluşturulan yürütülebilir dosya kopyalayın.
  
    > [!CAUTION]
    >  Değişiklik kod veya yeniden yapmayın (veya bu adımı tekrarlamalısınız). Yerel kaynak ve simgeler, uzak makineye kopyaladığınız yürütülebilir dosyanın tam olarak eşleşmelidir.

    Projeyi el ile kopyalayın, Xcopy, Robocopy, Powershell veya diğer seçenekleri kullanın.
  
11. Uzaktan hata ayıklayıcı hedef makinede çalıştığından emin olun. (Yüklü değilse, arama **uzaktan hata ayıklayıcı** içinde **Başlat** menüsü. ) Uzaktan hata ayıklayıcı penceresini aşağıdaki gibi görünür.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Visual Studio'da hata ayıklamayı Başlat (**hata ayıklama / hata ayıklamayı Başlat**, veya **F5**).  
  
13. İstenirse, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.  
  
     Gerekli kimlik bilgilerinin, ağınızın güvenlik yapılandırmasına bağlı olarak farklılık gösterir. Örneğin, bir etki alanı bilgisayarında etki alanı adınızı ve parolanızı girebilirsiniz. Bir etki alanı olmayan makinede, makine adı ve geçerli kullanıcı hesabı adı gibi girebilirsiniz <strong>MJO-DL\name@something.com</strong>, doğru parola ile birlikte.

     WPF uygulamanın ana pencere uzak bilgisayarda açık olduğunu görmeniz gerekir.
  
14. Gerekirse, kesme noktasına isabet için gerekeni yapın. Kesme noktası etkin olduğunu görmeniz gerekir. Aksi takdirde, uygulama için semboller henüz. Yeniden deneyin ve bu işe yaramazsa, sembolleri yükleme hakkında bilgi edinin ve onları ilgili sorunları nasıl [sembol dosyalarını anlama ve Visual Studio'nun sembol ayarları](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).
  
15. Visual Studio makinede yürütme kesme noktasında durduruldu görmeniz gerekir.
  
    Uygulama tarafından kullanılması gereken kod dışı dosyalara varsa, bunları Visual Studio projenize eklemeniz gerekir. Ek dosyalar için bir proje klasörü oluşturun (içinde **Çözüm Gezgini**, tıklayın **Ekle / yeni klasör**.) Dosyaları klasöre eklersiniz (içinde **Çözüm Gezgini**, tıklayın **Ekle / var olanı öğesi**, ardından dosyaları seçin.). Üzerinde **özellikleri** sayfasında her dosya için **çıkış dizinine Kopyala** için **her zaman Kopyala**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Uzak simgeleri ile hata ayıklamayı kurma  
 Kodunuzu Visual Studio bilgisayar üzerinde oluşturmak simgelerle hata ayıklamanız mümkün olması gerekir. Uzaktan hata ayıklayıcı performansının çok yerel semboller kullandığınızda daha iyidir.  Uzak sembolleri kullanmanız gerekirse, uzak makinede simgeleri aramak için uzaktan hata ayıklama İzleyicisi söylemeniz gerekir.  
  
 Visual Studio 2013 güncelleştirme 2'de başlayarak, yönetilen kod için Uzak semboller kullanmak için aşağıdaki msvsmon komut satırı anahtarını kullanabilirsiniz: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Daha fazla bilgi için lütfen uzak hata ayıklama yardıma bakın (basın **F1** uzaktan hata ayıklayıcı penceresinde veya tıklatın **Yardım / kullanım**). Daha fazla bilgi bulabilirsiniz [.NET uzaktan sembolü yükleniyor Visual Studio 2012 ve 2013 değişiklikleri](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Windows Store ve Azure uygulamalarında uzaktan hata ayıklama  
 Windows Store apps ile uzaktan hata ayıklama hakkında daha fazla bilgi için bkz: [hata ayıklayın ve Visual Studio'dan uzak bir cihazdaki Windows Store uygulamalarında test](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Azure'da hata ayıklama hakkında daha fazla bilgi için aşağıdaki konulardan birine bakın:  
  
-   [Bir bulut hizmeti veya sanal makine Visual Studio'da hata ayıklama](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [.NET arka ucu Visual Studio'da hata ayıklama](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Azure Web sitelerinde uzaktan hata ayıklama giriş ([bölüm 1](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [2. bölüm](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [bölüm 3](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da hata ayıklama](../debugger/debugging-in-visual-studio.md)   
 [Uzaktan hata ayıklama için Windows Güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)   
 [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)



