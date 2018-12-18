---
title: VSPackage sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad5ab8a337d790af8cd6d800c7bf36ea6ff01286
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348689"
---
# <a name="troubleshooting-vspackages"></a>VSPackage Sorunlarını Giderme
İle VSPackage olabilir ve bu sorunları çözmek için ipuçları yaygın sorunlar aşağıda verilmiştir.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Visual Studio başlatılmasını tutan bir VSPackage sorunlarını gidermek için  
  
- Başlangıç [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] güvenli modda.  
  
   Başlamak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] güvenli modda, bir komut istemine yazın **devenv.exe safemode**.  
  
   Bu işlem sırasında bulunan VSPackages dışında hiçbir VSPackages yüklenen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>VSPackage yükleme sorunlarını gidermek için  
  
1. Hangi VSPackage'ı çalıştırmak için genellikle Deneysel kayıt defteri kökü kayıtlı kayıt defteri kökü kullandığınızdan emin olun.  
  
    Daha fazla bilgi için [deneysel örneğinde](../extensibility/the-experimental-instance.md).  
  
2. VSPackage'ı Deneysel kayıt defteri kök dizininde çalıştırmak için henüz hedeflenmişse, Deneysel sürümüne çalışır durumda olduğundan emin olun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    Deneysel sürümünü çalıştırmak için bir komut penceresinde aşağıdaki komutu yazın: **devenv /rootsuffix exp**.  
  
3. VSPackage'ı kayıt defteri girişlerinizi kontrol edin.  
  
    Daha fazla bilgi için [VSPackage kaydetme](registering-and-unregistering-vspackages.md) ve [yönetme VSPackages](../extensibility/managing-vspackages.md).  
  
4. Açık **çıkış** penceresi örneğinin [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage'ı yüklemek başarısız. VSPackage'ı yüklemek neden başarısız olduğunu hakkında bilgi pencerede görüntülenebilir.  
  
   > [!NOTE]
   >  Deneysel sürümüne başlatıyorsanız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gelen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE), inceleme **çıkış** iki sürümünü penceresi.  
  
5. Etkinlik günlüğünü inceleyin.  
  
    Daha fazla bilgi için [nasıl yapılır: etkinlik günlüğü'nün](../extensibility/how-to-use-the-activity-log.md).  
  
6. IDE tarafından oluşturulan özel durumları hakkında daha fazla bilgi için tıklayın **özel durumları** üzerinde **hata ayıklama** özel durumlarını etkinleştirmek için menü. İçinde **özel durumları** iletişim kutusu hakkında daha fazla bilgi istediğiniz özel durum türlerini seçin.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Kaydetme bir VSPackage sorunlarını gidermek için  
  
1.  VSPackage derleme güvenilir bir konumda bulunduğundan emin emin olun. RegPkg derlemeleri varsayılan .net güvenlik yapılandırması ağ paylaşımına gibi bir güvenilmeyen veya kısmen güvenilen konumda kaydedilemiyor. Bir kullanıcı güvenilir olmayan bir konumda bir proje oluşturur. her bir uyarı görüntülenir, ancak "Bu iletiyi tekrar gösterme" onay kutusu bu uyarıyı yeniden oluşmasını öğesinden engelleyebilirsiniz.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Görünür değil veya bir komutu tıklattığınızda, bir hata oluşturur. komut sorunlarını gidermek için  
  
1. Yeni veya değiştirilmiş menü komutlarını ve IDE içinde zaten şu yazarak birleştirme [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komut istemi: **Exp/Setup devenv /rootsuffix**.  
  
2. Emin olun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] UI.dll, VSPackage için bulabilirsiniz.  
  
   1.  VSPackage'ı CLSID kayıt defteri paketleri bölümünü bulun:  
  
        HKLM\Software\Microsoft\Visual Studio\\*\<sürüm >* \Packages  
  
   2.  SatelliteDll alt tarafından verilen yolun doğru olduğundan emin olun.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Beklenmedik bir şekilde davranan VSPackage sorunlarını gidermek için  
  
1.  Kodunuzda kesme noktaları ayarlayın.  
  
     Hata ayıklama için iyi bir başlangıç noktası oluşturucusu ve başlatma yöntemi ' dir. Ayrıca, bir menü komutu gibi değerlendirmek istediğiniz alanı kesme noktaları ayarlayabilirsiniz. Kesme noktalarını etkinleştir, hata ayıklayıcı altında çalıştırmanız gerekir.  
  
    1.  Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
    2.  Üzerinde **özellik sayfaları** iletişim kutusunda **hata ayıklama** sekmesi.  
  
    3.  İçinde **komut satırı bağımsız değişkenleri** geliştirme ortamının kök sonekini yazın, VSPackage hedeflerinizi. Örneğin, deneysel yapı seçmek için şunu yazın: **RootSuffix Exp**.  
  
    4.  Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat** veya F5 tuşuna basın.  
  
        > [!NOTE]
        >  Bir proje hata ayıklaması yapıyorsanız veya projenize mevcut bir örneğini artık yüklenemiyor.  
  
2.  Etkinlik günlüğü'nü kullanın.  
  
     Temel etkinlik günlüğü bilgilerini yazarak VSPackage davranışını izleme. Bir perakende ortamında bir VSPackage'ı çalıştırdığınızda bu özellikle yararlı bir tekniktir. Daha fazla bilgi için [nasıl yapılır: etkinlik günlüğü'nün](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Ortak semboller kullanın.  
  
     Hata ayıklama sırasında okunabilirliği artırmak için hata ayıklayıcıya sembolleri ekleyebilirsiniz.  
  
    1.  Gelen **Araçlar/Seçenekler** menüsünde gidin **hata ayıklama/semboller** iletişim kutusu.  
  
    2.  Bu ekleme **sembol dosyası (.pdb) konumu**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Performansı artırmak için örneğin bir sembol Önbellek klasörü belirtin:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>VSPackage'ı eksik ya da bağımlılıklarından biri sorun giderme  
  
1. Yönetilen kod için başvuru yolları doğru olduğundan emin olun.  
  
   1.  Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
   2.  Seçin **başvuruları** sekmesinde **özellik sayfaları** iletişim kutusu ve emin tüm yolları doğru. Alternatif olarak, **Nesne Tarayıcısı** başvurulan nesneleri gidin.  
  
        Yönetilen kod için kullanabileceğiniz [Fuslogvw.exe (Derleme bağlaması Günlük Görüntüleyici)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) başarısız derleme yüklerini ayrıntılarını görüntülemek için.  
  
2. Yönetilmeyen kod için CLSID değeri içinde VSPackage'ı bulma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID kayıt defteri düğümü:  
  
    HKLM\Software\Microsoft\Visual Studio\\*\<sürüm >* \CLSID  
  
   Inprocserver32 giriş VSPackage dll'nin doğru yol olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage’lar](../extensibility/internals/vspackages.md)