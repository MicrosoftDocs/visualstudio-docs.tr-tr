---
title: Office çözümü dağıtımında sorunlarını giderme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bba978da26a2aa7b7263fa5d2e88fa8acdc272f0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886009"
---
# <a name="troubleshoot-office-solution-deployment"></a>Office çözümü dağıtımında sorunlarını giderme
  Bu konuda, Office çözümleri dağıtırken karşılaşabileceğiniz genel sorunları nasıl çözeceğinizi hakkında bilgi içerir.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Olay Görüntüleyicisi'ni kullanarak, Office çözümlerinde sorun giderme  
 Tarafından yakalanan hata iletilerini görmek için Windows Olay Görüntüleyicisi'ni kullanabilirsiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yüklediğinizde veya Office çözümleri kaldırın. Olay günlüğü ileti, yükleme ve dağıtım sorunlarını gidermek için kullanabilirsiniz. Daha fazla bilgi için [Office çözümleri için olay günlüğü](../vsto/event-logging-for-office-solutions.md).  
  
## <a name="change-the-assembly-name-causes-conflicts"></a>Değişiklik derleme adı çakışmalarına neden olur.  
 Değiştirirseniz **derleme adı** değerini **uygulama** sayfasının **Proje Tasarımcısı** zaten bir çözüm dağıttıktan sonra yayımlama araçları değiştirir İçin bir Kurulum paketini *Setup.exe* dosya ve iki dağıtım bildirimleri. İki bildirim dosyalarını dağıtırsanız, aşağıdaki durumlardan ortaya çıkabilir:  
  
- Son kullanıcı her iki sürümü yüklerse, uygulama her iki VSTO eklentileri yükler.  
  
- VSTO eklenti bütünleştirilmiş kod adı değiştirilmeden önce yüklenmişse, son kullanıcı asla güncelleştirmeleri alırsınız.  
  
  Bu koşullar önlemek için çözümün değişmez **derleme adı** çözümü dağıttıktan sonra değeri.  
  
## <a name="check-for-updates-takes-a-long-time"></a>Güncelleştirmeleri alan uzun olup olmadığını denetleyin  
 Visual Studio 2010 Tools for Office runtime Yöneticiler için bildirimler ve çözümü indirme zaman aşımı değerini ayarlamak için kullanabileceğiniz bir kayıt defteri girişi sağlar.  
  
#### <a name="to-set-the-time-out-value"></a>Zaman aşımı değerini ayarlamak için  
  
1.  Kayıt defterinde şu anahtara gidin:  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**  
  
2.  İçinde **AddInTimeout** alt anahtarını, zaman aşımı değerini milisaniye cinsinden ayarlayın.  
  
     Varsa **AddInTimeout** alt değil, mevcut bir DWORD olarak oluşturun.  
  
## <a name="cant-update-or-publish-to-a-network-file-share"></a>Güncelleştirilemiyor veya ağ dosya paylaşımına yayımlayın  
 Bir ağ dosya paylaşımında bulunan office çözümlerini görüntülenebilir yanıltıcı bir ileti güncelleştirirken, çözümün *Setup.exe* dosya güncelleştirme yayımlanırken bir işlem kilitlenmiş. Aşağıdaki ileti diyebilirsiniz: "'setup.exe' Web'de eklenemiyor. "Setup.exe' dosyası zaten bu Web var."  
  
 Dosya kilitleme önlemeye yardımcı olmak için paylaşımın salt okunur son kullanıcılara yapabilirsiniz. Belgeler paylaşımındaysa, ancak bunlar Ayrıca son kullanıcılara salt okunur hale gelir.  
  
## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Microsoft Office için Önkoşullar yüklü değil  
 .NET Framework, eklediğiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]ve Office birincil birlikte çalışma derlemelerini kurulum paketi Office çözümünüzü ile dağıtılan bir önkoşul olarak. Birincil birlikte çalışma derlemelerini yükleme hakkında daha fazla bilgi için bkz: [Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md) ve [nasıl yapılır: yükleme Office birincil birlikte çalışma derlemelerini](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
## <a name="publish-using-localhost-can-cause-installation-problems"></a>Kullanarak Yayımla 'Localhost' yükleme sorunlara neden olabilir  
 Kullandığınızda, "<http://localhost>" için belge düzeyi çözümleri yayımlama ya da yükleme konumu olarak **Yayımlama Sihirbazı** dize gerçek bilgisayar adını dönüştürmez. Bu durumda, çözüm geliştirme bilgisayarına yüklenmesi gerekir. Geliştirme bilgisayarınızda IIS kullanan dağıtılmış çözümlere yapmak için localhost yerine tüm HTTP/HTTPS/FTP konumlar için tam ad kullanın.  
  
## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Önbelleğe alınmış derlemeler yerine güncelleştirilmiş derlemeleri yüklenir  
 Fusion, .NET Framework derleme yükleyicisi, proje çıktı yolu bir ağ dosya paylaşımında olduğunda, derleme, tanımlayıcı ad ile imzalanması ve özelleştirmenin derleme sürümünü değiştirmez derlemeleri önbelleğe alınmış kopyasını yükler. Bu koşullara uyan bir derlemeyi güncelleştirirseniz, güncelleştirme, önbelleğe alınmış kopyayı yüklendiği için projeyi çalıştırın sonraki sefer görünmez.  
  
 Visual Studio projeyi her çalıştırıldığında Fusion derlemeleri karşıdan yükler yapılandırabilirsiniz.  
  
### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Önbelleğe alınan kopyaları yükleme yerine derlemeleri yüklemek için  
  
1. Menü çubuğunda, **proje**, _ProjectName_**özellikleri**.  
  
2. Üzerinde **uygulama** sayfasında **derleme bilgileri**.  
  
3. İlk **derleme sürümü** kutusunda, bir yıldız işareti girin (\*) ve ardından **Tamam** düğmesi.  
  
   Derleme sürümü değiştirdikten sonra derlemeyi bir katı adla imzalamak devam edebilirsiniz ve Fusion özelleştirme en son sürümünü yükler.  
  
## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>URI US-ASCII olmayan karakterler içeriyorsa yüklemesi başarısız olur.  
 Yolu, HTTP/HTTPS/FTP konumu için bir Office çözümü yayımladığınızda, US-ASCII olmayan Unicode karakterlerini sahip olamaz. Bu tür karakterler, Kurulum programına tutarsız davranışa neden olabilir. US-ASCII karakterlerini, yükleme yolu için kullanın.  
  
## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Yayımlama ve bir çözüm geliştirme bilgisayarına el ile kaldırmak için istemi görünür  
 Office çözüm derlerken, derleme sürümü otomatik olarak kaydedilir. Önceden yayımlanan ve aynı çözüm geliştirme bilgisayarınıza yüklü değilse [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yükleme yolu çözümü sonraki oluşturulduktan sonra yayımlanmış sürüm ve derleme sürümü farklıdır yeniden veya yayımlanan olduğunu algılar. Hata iletisi "başka bir sürümü yüklü olan ve bu konumdan yükseltilemez özelleştirme yüklenemez." diyor. Kayıt defteri anahtarlarını bir çözümün yeniden her güncelleştirilir. Bu nedenle, yayımlama, hata ayıklama veya yeni sürümü çalıştıran önce önceki sürümü kaldırmanız gerekir.  
  
 İletinin görüntülenmesini engellemek için dağıtımınızı test etmek için geliştirme bilgisayarınızda başka bir kullanıcı hesabı oluşturun. Sonraki yayımlama, hata ayıklama veya çözümü yeniden önce alternatif olarak, sürümü bilgisayarda yüklü programlar listesinde kaldırabilirsiniz.  
  
## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Bir çözüm yüklediğinizde Yakalanmayan Özel durum veya yöntem bulunamadı hatası  
 Dağıtım bildirimini açarak Office çözümleri yüklerken (bir *.vsto* dosyası), aşağıdaki koşulların Office uygulama, belge veya çalışma kitabı, hata iletileri görünebilir:  
  
- Metoda nebyla nalezena.  
  
- MissingMethodException.  
  
- Yakalanmayan Özel durum.  
  
  Bu hata iletilerini önlemek için Kurulum programını çalıştırarak çözümü yükleyin.  
  
  Kurulum programını çalıştırmadan çözüm yüklediğinizde, yükleyici değil olup olmadığını denetleyin veya önkoşulları yükleyin. Kurulum programı, Önkoşullar için doğru sürümünü denetler ve bunları gerektiği şekilde yükler.  
  
## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Bir InstallShield Limited Edition projesi oluşturulduktan sonra kayıt defteri anahtarları için Add-Ins değişiklik bildirimi  
 Bir VSTO eklenti kurulumunun bir parçası olan bildirim kayıt defteri anahtarı program bazen değişikliklerden *.vsto* için *. dll.manifest* bir InstallShield Limited Edition projesi oluşturduğunuzda.  
  
 Bu sorunu geçici olarak çözmek için farklı bir çözümde InstallShield Limited Edition projesi oluşturun veya ŞirketAdı.EklentiAdı'nı VSTO eklentisi adını içeren bir kayıt defteri anahtarı değeri olarak kullanın.  
  
## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>ClickOnce yükleyicisi Office çözümünüz için birincil birlikte çalışma derlemelerini yüklemez  
 Office çözümünüz için ClickOnce'ı oluşturan kurulum programını çalıştırdığınızda, yalnızca hiçbir PIA'ların zaten yüklüyse yükleyici için Office birincil birlikte çalışma derlemeleri (PIA) çalıştırır.  
  
 Kurulum programı PIA'ların düzgün yüklenmiyorsa, bunları el ile adlı yükleyici dosyasını çalıştırarak yükleyin *o2007pia.msi* yükleme dizininden.  
  
## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Office çözümleri nedenleri aralığı özel durum dışında bir bağımsız değişken yeniden yükleyin.  
 Bir Office çözümü yeniden yüklerken bir <xref:System.ArgumentOutOfRangeException> özel durum, şu hata iletisiyle görünebilir: Belirtilen bağımsız değişken geçerli değerler aralığının dışında.  
  
 Yükleme konumu için URL için büyük küçük harfleri farklı olduğunda bu durum meydana gelir. Örneğin, Office çözümünü yüklü değilse bu hata görüneceği [ http://fabrikam.com/ExcelSolution.vsto ](http://fabrikam.com/ExcelSolution.vsto) ilk kez ve ardından kullanılan [ http://fabrikam.com/excelsolution.vsto ](http://fabrikam.com/excelsolution.vsto) ikinci kez.  
  
 İletinin görüntülenmesini engellemek için Office çözümleri yüklediğinizde aynı büyük/küçük harf kullanın.  
  
## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>ClickOnce çözüm Web'den dağıtım bildirimini açarak yükleyemezsiniz.  
 Kullanıcılar, web dağıtım bildirimini açarak Office çözümleri yükleyebilir. Ancak, bazı Internet Information Services (IIS) engelleyecek *.vsto* dosya adı uzantısı. Office çözümünü dağıtmak için kullanmadan önce MIME türü IIS'de tanımlamanız gerekir.  
  
 IIS 7'de aynı zamanda MIME türü tanımlama hakkında daha fazla bilgi için bkz: [MIME türü (IIS7) eklemek](http://technet.microsoft.com/library/cc725608(WS.10).aspx).  
  
 Uzantı kümesine **.vsto** ve MIME tür **application/x-ms-vsto**.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce dağıtım sorunlarını giderme](/visualstudio/deployment/troubleshooting-clickonce-deployments)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)  
  
  