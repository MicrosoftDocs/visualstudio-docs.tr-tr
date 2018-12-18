---
title: Profil oluşturma HPC (yüksek performanslı hesaplama) kümelerinde | Microsoft Docs
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
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6b0838a7fb3db86290647fadec9ca3572cbdf90
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809164"
---
# <a name="profiling-on-hpc-high-performance-computing-clusters"></a>HPC (Yüksek Performanslı Hesaplama) Kümelerinde Profil Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnekleme yöntemini kullanarak, Microsoft Windows HPC kümeleri işlem düğümlerinde profilini oluşturabilirsiniz [!INCLUDE[vsPreExt](../includes/vspreext-md.md)] veya [!INCLUDE[vsUltExt](../includes/vsultext-md.md)] profil oluşturma araçları. HPC hakkında daha fazla bilgi için bkz. [Windows HPC](http://go.microsoft.com/fwlink/?LinkId=165393) Microsoft Web sitesinde.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bir HPC işlem düğümünde profili oluşturmak için aşağıdakileri yapmanız gerekir:  
  
- Microsoft HPC Paketi 2008 aynı bilgisayara yükleme [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. HPC kümesinin parçası olacak bir bilgisayar yok. HPC paketini yükleyebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=177414).  
  
- Yükleme [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] ve tek başına bir HPC profil oluşturma araçları sürümünü işlem düğümü. Program için yükleme [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ve profil oluşturucuyu tek başına kullanılabilir [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] yükleme medyası. **Not** yükledikten sonra işlem yeniden [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ve profil oluşturma araçları yüklemeden önce.  
  
  Yüklenecek [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] ve tek başına profil oluşturma araçları etkin bir HPC bilgi işlem düğümü ve etkin küme makinede profil oluşturma, şu adımları izleyin:  
  
1.  HPC pack ile yüklü bir komut istemi penceresi açın.  
  
2.  Ayrı bir komut istemlerinde aşağıdaki komutları yazın:  
  
    1.  `clusrun /all /scheduler:` *% Baş ayıklaması FxPath %* `/q /norestart`  
  
    2.  `clusrun /all /scheduler:` *Baş düğüm %* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3.  `clusrun /all /scheduler:` *% Baş ayıklaması ProfilerPath %* `/q /norestart`  
  
|||  
|-|-|  
|*%HeadNode%*|Küme baş düğümü adı.|  
|*%FxPath%*|Yolu [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] yükleyici. Üzerinde [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] yolu yükleme medyası: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe|  
|*%ProfilerPath%*|Tek başına sürümü Profil Araçları Yükleyicisi'nin yolu. Üzerinde [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] yolu yükleme medyası: tek başına Profiler\x64\vs_profiler.exe|  
  
## <a name="profiling-on-an-hpc-compute-node"></a>Bir HPC işlem düğümünde profil oluşturma  
 Profil oluşturma oturumunu, HPC Kümesi ve hedef bilgileri belirtmek için HPC performans Sihirbazı'nı kullanarak yapılandırın. Performans oturumu özellik sayfaları'nda ek seçenekler ayarlayabilirsiniz. Profil oluşturma araçları, otomatik olarak gerekli hedef ikili dosyaları dağıttıktan ve profil oluşturucu ve HPC uygulaması başlatın.  
  
#### <a name="to-profile-on-an-hpc-compute-node"></a>Bir HPC işlem düğümünde profilini çıkarmak için  
  
1.  Üzerinde **Çözümle** menüsünü tıklatın **HPC performans Sihirbazını Başlat**. Komut kullanılabilir durumda değilse, yukarıda listelenen önkoşullara sahip olduğunuzdan emin olun.  
  
2.  Tıklayın **sonraki** sihirbazının ilk sayfasında.  
  
3.  Sihirbazın ikinci sayfasında, profil oluşturmak istediğiniz uygulamayı seçin.  
  
    -   Şu anda açık olan proje profilini [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]seçin **bir veya daha fazla kullanılabilir projeler** seçeneğini ve ardından listeden proje adını seçin.  
  
    -   Kullanımda olmayan bir ikili profilini çıkarmak için açık bir proje seçin **bir yürütülebilir dosya (. EXE dosyası)** seçeneği.  
  
4.  **İleri**'ye tıklayın.  
  
5.  Sihirbazın üçüncü sayfasında:  
  
    -   Açık bir projedeymiş değil bir yürütülebilir dosya profili oluşturuyorsanız, ikili dosyanın yolunu belirtin **yürütülebilir dosyanın tam yolunu nedir**.  
  
    -   Açık bir projedeymiş değil bir yürütülebilir dosya profili oluşturuyorsanız, işlem geçirilecek komut satırı bağımsız değişkenlerini belirtebilirsiniz **komut satırı bağımsız değişkenleri**.  
  
    -   İçinde **uzak çalışma dizini**, işlem düğümleri ayrı ayrı işlem örneklerinde tarafından kullanılan bir klasörün yolunu belirtin.  
  
    -   İçinde **dağıtım konumu**, HPC server görüntüleri aşama dağıtımı için kullanacağı dizinin yolunu belirtin.  
  
6.  **İleri**'ye tıklayın.  
  
7.  Sihirbazının dördüncü sayfasında:  
  
    -   İçinde **baş düğüm** listesinde, profil oluşturma çalışması içinde HPC baş düğümü görevi gören bilgisayarı tıklatın. Baş düğüm, profili bir küme gerek kalmadan yerel makinede olanak "localhost" olabilir.  
  
    -   İçinde **işlemlerin sayısı** listesinde, uygulamayı çalıştırmak için örnek sayısını tıklayın.  
  
    -   Gelen **seçenekleri profil oluşturma** listesinde, profil oluşturma hedefi seçin.  
  
         Küme içindeki belirli bir işlem profili oluşturmak için Seç **profilindeki boyut** seçeneğini ve ardından işlem sırasını aşağı açılan listeden seçin.  
  
         HPC küme içindeki belirli bir düğümde çalışan işlemler ve işlem profili oluşturmak için Seç **düğümde profili** seçeneğini ve ardından düğümü aşağı açılan listeden seçin.  
  
8.  **İleri**'ye tıklayın.  
  
9. Beşinci sihirbaz sayfasında, profil oluşturucu ve profil oluşturma işlemi hemen başlatmak için ya da daha sonra performans Gezgini kullanarak profil oluşturmayı başlatmak için seçebilirsiniz.  
  
    -   Seçin **Sihirbaz sonlandıktan sonra profil oluşturmayı Başlat** hemen profilini oluşturmaya başla veya el ile profil oluşturmayı başlatmak için onay kutusunu temizleyin.  
  
10. **Son**'a tıklayın.  
  
## <a name="setting-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Performans oturumu özellik sayfaları kullanarak HPC profil oluşturma özelliklerini ayarlama  
 HPC profili oluşturma Sihirbazı HPC başlatma özellikleri sayfasında performans oturumu özellikleri sayfasında, belirlediğiniz performans oturumu özellikleri değiştirebilirsiniz. HPC Gelişmiş Özellikler sayfasında ek seçeneklerini ayarlayın.  
  
#### <a name="to-open-the-performance-session-property-pages"></a>Performans oturumu özellik sayfalarını açmak için  
  
1.  Gerekirse, performans Gezgini içinde performans oturumu (.psess) dosyası açın. Üzerinde **dosya** menüsünde tıklatın **açık** ve dosyayı bulun.  
  
2.  Performans Gezgini, performans oturumu adına sağ tıklayın ve ardından **özellikleri**.  
  
3.  Özellik sayfaları iletişim kutusunda, aşağıdaki yöntemlerden birini kullanın:  
  
    -   Tıklayın **genel** seçip **HPC kümesinde toplamak** profil oluşturma HPC etkinleştirmek ya da HPC profili oluşturma devre dışı bırakmak için onay kutusunu temizleyin.  
  
    -   Tıklayın **HPC başlatma özellikleri** HPC uygulaması başlangıç özelliklerini değiştirmek için.  
  
    -   Tıklayın **HPC Gelişmiş Özellikler** ek seçeneklerini ayarlamak için  
  
### <a name="hpc-launch-properties"></a>HPC başlatma özellikleri  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**Baş düğüm**|Profil oluşturma çalıştırmasını HPC baş düğümü görevi gören bilgisayarı belirtir.|  
|**İşlem sayısı**|Profili oluşturulan uygulamada çalıştırmak için uygulamanın örnek sayısını belirtir.|  
|**Üzerinde boyut profili**|Küme içindeki belirli bir işlem profili oluşturmak için Seç **profilindeki boyut** seçeneğini ve ardından işlem sırasını aşağı açılan listeden seçin.|  
|**Düğümde profil**|HPC küme içindeki belirli bir düğümde çalışan işlemler ve işlem profili oluşturmak için Seç **düğümde profili** seçeneğini ve ardından düğümü aşağı açılan listeden seçin.|  
|**Uzak çalışma dizini**|İşlem düğümleri ayrı ayrı işlem örneklerinde tarafından kullanılan bir klasörün yolunu belirtir.|  
|**Dağıtım konumu**|HPC server görüntüleri aşama dağıtımı için kullanacağı dizinin yolunu belirtir.|  
  
### <a name="advanced-properties"></a>Gelişmiş Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**Proje adı**|Geçerli adını [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] proje veya çözüm.|  
|**Profil Oluşturucu durdurulduğunda temizleme**|TRUE olduğunda, yürütme dizine dağıtılan ikili dosyaları kaldırır. Bu adımda, dosya ve program kullanıcı tarafından oluşturulan dizinleri kaldırılmaz. Dağıtım dizini ve yürütme directory IDE tarafından oluşturulmuşsa, IDE bunları kaldırmak çalışır, ancak bunlar IDE tarafından dağıtılan dosyalar varsa bunu.|  
|**Dağıtılacak ek dosyalar**|İşlem düğümü üzerinde dağıtılacak ek dosyaların noktalı virgülle ayrılmış listesini belirtir. Üç nokta düğmesine tıklayabilirsiniz (**...** ) iletişim kutusunu kullanarak birden çok dosya seçin.|  
|**Mpiexec komutu**|MPI uygulama başladığında uygulamayı belirtir. Varsayılan değer **mpiexec.exe**|  
|**Mpiexec bağımsız değişkenleri**|Mpiexec.exe komutu geçirilecek bağımsız değişkenleri belirtir.|  
|**İstenen küme düğümlerinde**|Uygulamanın çalıştırılacağı kümedeki düğüm sayısını belirtir.|  
|**CRT dosyaları dağıtma**|TRUE olduğunda, C/C++ çalışma zamanı kümede dağıtır.|  
|**Önceden betik profili**|Profil oluşturma oturumu başlamadan önce yerel geliştirme bilgisayarınızda çalıştırılacak bir komut dosyası yolu ve dosya adını belirtir.|  
|**Profil öncesi betik bağımsız değişkenleri**|Ön profili betiğe geçirilecek bağımsız değişkenleri belirtir.|  
|**Sonrası komut dosyası profil**|Profil oluşturma oturumu sona erdikten sonra yerel geliştirme bilgisayarınızda çalıştırılacak bir komut dosyası yolu ve dosya adını belirtir.|  
|**Profil sonrası betik bağımsız değişkenleri**|Sonrası profili betiğe geçirilecek bağımsız değişkenleri belirtir.|



