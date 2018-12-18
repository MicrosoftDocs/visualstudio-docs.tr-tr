---
title: MSI ve VSIX dağıtımı DSL'nin | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 81b027e9834fccadcc572cad8fae4d721be9dd56
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922048"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL'nin MSI ve VSIX Dağıtımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir etki alanına özgü dil sizin kendi bilgisayarınız veya diğer bilgisayarlara yükleyebilirsiniz. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hedef bilgisayarda zaten yüklü gerekir.  
  
##  <a name="which"></a> VSIX ile MSI dağıtım arasında seçim yapma  
 Bir etki alanına özgü dil dağıtmak için iki yöntem vardır:  
  
|Yöntem|Yararları|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı)|Dağıtımı çok kolaydır: kopyalama ve yürütme **.vsix** DslPackage proje dosyası.<br /><br /> Daha fazla bilgi için [yükleme ve bir DSL VSX kullanarak kaldırma](#Installing).|  
|MSI (yükleyici dosyası)|-Açmasını sağlayan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DSL dosyası çift tıklayın.<br />-DSL dosya türü hedef bilgisayardaki bir simge ilişkilendirir.<br />-Bir XSD (XML Şeması) DSL dosya türü ile ilişkilendirir. İçine bir dosya yüklendiğinde bu uyarıları engeller [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].<br /><br /> Bir MSI oluşturmak için çözümünüze bir kurulum projesi eklemeniz gerekir.<br /><br /> Daha fazla bilgi için [DSL bir MSI dosyası kullanarak dağıtımı](#msi).|  
  
##  <a name="Installing"></a> Yükleme ve bir DSL VSX kullanarak kaldırma  
 Bu yöntem tarafından DSL'nizi yüklendiğinde, kullanıcı bir DSL dosyası içinden açabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ancak Windows Gezgini'nden dosya açılamıyor.  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Bir DSL VSX kullanarak yüklemek için  
  
1.  Bilgisayarınızda, bulma **.vsix** DSL paket projeniz tarafından oluşturulan dosya.  
  
    1.  İçinde **Çözüm Gezgini**, sağ **DslPackage** proje ve ardından **klasörü Windows Gezgini'nde Aç**.  
  
    2.  Dosyayı bulmak **bin\\\*\\**_projeniz_**. DslPackage.vsix**  
  
2.  Kopyalama **.vsix** DSL yüklemek istediğiniz hedef bilgisayara dosya. Bu sizin kendi bilgisayarınız veya başka bir tane olabilir.  
  
    -   Hedef bilgisayarda sürümlerinden biri olmalıdır [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , çalışma zamanında DSL'ler destekler. Daha fazla bilgi için [Görselleştirme ve modelleme SDK'sı için Visual Studio sürümleriyle desteklenen](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    -   Hedef bilgisayarda sürümlerinden biri olmalıdır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] belirtilen **DslPackage\source.extensions.manifest**.  
  
3.  Hedef bilgisayarda çift **.vsix** dosya.  
  
     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yükler.  
  
4.  Başlatın veya yeniden [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
5.  DSL test etmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DSL'nizi için tanımlanan uzantısına sahip yeni bir dosya oluşturmak için.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX kullanarak yüklenen bir DSL kaldırmak için  
  
1. Üzerinde **Araçları** menüsünde tıklatın **Uzantı Yöneticisi**.  
  
2. Genişletin **yüklü uzantıları**.  
  
3. DSL tanımlanır uzantısı ve ardından seçin **kaldırma**.  
  
   Nadiren, hatalı bir uzantı yüklemede başarısız olur ve hata penceresinde bir rapor oluşturur ancak Uzantı Yöneticisi'nde görünmez. Bu durumda, dosyayı şuradan silerek uzantıyı kaldırabilirsiniz:  
  
   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="msi"></a> Bir DSL içinde bir MSI dağıtma  
 Bir MSI (Windows Yükleyici) dosyası için DSL'nizi tanımlayarak, DSL dosyaları Windows Gezgini'nden açmasına izin verebilirsiniz. Ayrıca, dosya adı uzantısına sahip bir simge ve kısa açıklama ilişkilendirebilirsiniz. Ayrıca, MSI DSL dosyaları doğrulamak için kullanılan bir XSD yükleyebilirsiniz. İsterseniz, aynı anda yüklü MSI içine diğer bileşenleri ekleyebilirsiniz.  
  
 MSI dosyaları ve diğer dağıtım seçenekleri hakkında daha fazla bilgi için bkz. [uygulamaları dağıtma, hizmetleri ve bileşenleri](../deployment/deploying-applications-services-and-components.md).  
  
 Bir MSI oluşturmak için bir kurulum projesine eklemeniz, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözüm. İndirebilirsiniz CreateMsiSetupProject.tt şablonu kullanmak için bir kurulum projesi oluşturmanın en kolay yöntem olduğunu [VMSDK site](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>Bir DSL içinde bir MSI dağıtmak için  
  
1. Ayarlama `InstalledByMsi` uzantı bildiriminde. Bu VSX yüklü ve dışında bir MSI tarafından engeller. Bu, diğer Bileşenleri MSI'dahil edilecekse önemlidir.  
  
   1.  Open DslPackage\source.extension.tt  
  
   2.  Önce aşağıdaki satır ekler `<SupportedProducts>`:  
  
       ```  
       <InstalledByMsi>true</InstalledByMsi>  
       ```  
  
2. Oluşturun veya Windows Gezgini'nde DSL'nizi temsil edecek simge düzenleyin. Örneğin, Düzen **DslPackage\Resources\File.ico**  
  
3. Aşağıdaki öznitelikler, DSL'nin doğru olduğundan emin olun:  
  
   -   DSL Gezgini kök düğümüne tıklayın ve Özellikler penceresinde gözden geçirin:  
  
       -   Açıklama  
  
       -   Sürüm  
  
   -   Tıklayın **Düzenleyicisi** düğüm ve Özellikler penceresinde tıklayın **simgesi**. Bir simge dosyasına bir değere ayarlayın **DslPackage\Resources**, gibi **File.ico**  
  
   -   Üzerinde **derleme** menüsünde, açık **Configuration Manager**, gibi oluşturmak istediğiniz yapılandırma seçip **yayın** veya **hata ayıklama** .  
  
4. Git [Görselleştirme ve modelleme SDK'sı giriş sayfası](http://go.microsoft.com/fwlink/?LinkID=186128), gelen ve giden **indirir** sekmesinde, yükleme **CreateMsiSetupProject.tt**.  
  
5. Ekleme **CreateMsiSetupProject.tt** Dsl projenize.  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] adlı bir dosya oluşturacaksınız **CreateMsiSetupProject.vdproj**.  
  
6. Windows Gezgini'nde, Dsl kopyalama\\*.vdproj yeni bir klasöre adlı kurulumu.  
  
    (İsterseniz, artık CreateMsiSetupProject.tt Dsl projenizden hariç tutabilirsiniz.)  
  
7. İçinde **Çözüm Gezgini**, ekleme **Kurulum\\\*.vdproj** var olan bir projeyle.  
  
8. Üzerinde **proje** menüsünü tıklatın **proje bağımlılıkları**.  
  
    İçinde **proje bağımlılıkları** iletişim kutusunda, Kurulum projesini seçin.  
  
    Yanındaki kutuyu işaretleyin **DslPackage**.  
  
9. Çözümü yeniden derleyin.  
  
10. Windows Gezgini'nde, Kurulum projesinde oluşturulmuş MSI dosyasını bulun.  
  
     MSI dosyası DSL'nizi yüklemek istediğiniz bilgisayara kopyalayın. MSI dosyasını çift tıklayın. Yükleyiciyi çalıştırır.  
  
11. Hedef bilgisayarda, DSL'nin dosya uzantısına sahip yeni bir dosya oluşturun. Aşağıdakileri doğrulayın:  
  
    -   Windows Gezgini liste görünümünde dosya tanımladığınız açıklaması ve simge ile görünür.  
  
    -   Dosyayı çift tıkladığınızda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlar ve DSL dosyası DSL Düzenleyicisi'nde açılır.  
  
    Tercih ederseniz, metin şablonu kullanmak yerine Kurulum projesi el ile oluşturabilirsiniz. Bu yordam içeren bir kılavuz için bkz: Bölüm 5, [Görselleştirme ve modelleme SDK'sı Laboratuvar](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Konumundan bir MSI yüklü olduğu bir DSL kaldırmak için  
  
1.  Windows içinde açın **programlar ve Özellikler** Denetim Masası.  
  
2.  DSL kaldırın.  
  
3.  Visual Studio'yu yeniden başlatın.



