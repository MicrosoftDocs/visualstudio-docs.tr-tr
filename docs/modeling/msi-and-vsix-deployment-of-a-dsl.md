---
title: DSL'nin MSI ve VSIX Dağıtımı
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2f5b8948d94c64d84b33714a4b432a46bfb73b59
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931551"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL'nin MSI ve VSIX Dağıtımı
Bir etki alanına özgü dil sizin kendi bilgisayarınız veya diğer bilgisayarlara yükleyebilirsiniz. Visual Studio, hedef bilgisayarda zaten yüklü olmalıdır.

## <a name="which"></a> VSIX ile MSI dağıtım arasında seçim yapma
 Bir etki alanına özgü dil dağıtmak için iki yöntem vardır:

|Yöntem|Yararları|
|-|-|
|VSX (Visual Studio uzantısı)|Dağıtımı çok kolaydır: kopyalama ve yürütme **.vsix** DslPackage proje dosyası.<br /><br /> Daha fazla bilgi için [yükleme ve bir DSL VSX kullanarak kaldırma](#Installing).|
|MSI (yükleyici dosyası)|-Visual Studio DSL dosyasına çift tıklayarak açın izin verir.<br />-DSL dosya türü hedef bilgisayardaki bir simge ilişkilendirir.<br />-Bir XSD (XML Şeması) DSL dosya türü ile ilişkilendirir. Dosya Visual Studio'ya yüklendiğinde bu uyarıları engeller.<br /><br /> Bir MSI oluşturmak için çözümünüze bir kurulum projesi eklemeniz gerekir.<br /><br /> Daha fazla bilgi için [DSL bir MSI dosyası kullanarak dağıtımı](#msi).|

## <a name="Installing"></a> Yükleme ve bir DSL VSX kullanarak kaldırma
 DSL'nizi bu yöntem tarafından yüklendiğinde, kullanıcı bir DSL dosyası Visual Studio içinden açabilirsiniz, ancak Windows Gezgini'nden dosya açılamıyor.

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Bir DSL VSX kullanarak yüklemek için

1. Bilgisayarınızda, bulma **.vsix** DSL paket projeniz tarafından oluşturulan dosya.

   1.  İçinde **Çözüm Gezgini**, sağ **DslPackage** proje ve ardından **klasörü Windows Gezgini'nde Aç**.

   2.  Dosyayı bulmak **bin\\\*\\**_projeniz_**. DslPackage.vsix**

2. Kopyalama **.vsix** DSL yüklemek istediğiniz hedef bilgisayara dosya. Bu sizin kendi bilgisayarınız veya başka bir tane olabilir.

   - Hedef bilgisayarda sürümlerinden biri olmalıdır [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , çalışma zamanında DSL'ler destekler. Daha fazla bilgi için [Görselleştirme ve modelleme SDK'sı için Visual Studio sürümleriyle desteklenen](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - Hedef bilgisayarın belirtilen Visual Studio sürümleri birine sahip olmalıdır **DslPackage\source.extensions.manifest**.

3. Hedef bilgisayarda çift **.vsix** dosya.

    **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yükler.

4. Başlatın veya yeniden [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

5. DSL test etmek için DSL için tanımlanan uzantısına sahip yeni bir dosya oluşturmak için Visual Studio kullanın.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX kullanarak yüklenen bir DSL kaldırmak için

1. Üzerinde **Araçları** menüsünde tıklatın **Uzantı Yöneticisi**.

2. Genişletin **yüklü uzantıları**.

3. DSL tanımlanır uzantısı ve ardından seçin **kaldırma**.

   Nadiren, hatalı bir uzantı yüklemede başarısız olur ve hata penceresinde bir rapor oluşturur ancak Uzantı Yöneticisi'nde görünmez. Bu durumda, dosyayı şuradan silerek uzantıyı kaldırabilirsiniz:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a> Bir DSL içinde bir MSI dağıtma
 Bir MSI (Windows Yükleyici) dosyası için DSL'nizi tanımlayarak, DSL dosyaları Windows Gezgini'nden açmasına izin verebilirsiniz. Ayrıca, dosya adı uzantısına sahip bir simge ve kısa açıklama ilişkilendirebilirsiniz. Ayrıca, MSI DSL dosyaları doğrulamak için kullanılan bir XSD yükleyebilirsiniz. İsterseniz, aynı anda yüklü MSI içine diğer bileşenleri ekleyebilirsiniz.

 MSI dosyaları ve diğer dağıtım seçenekleri hakkında daha fazla bilgi için bkz. [uygulamaları dağıtma, hizmetleri ve bileşenleri](../deployment/deploying-applications-services-and-components.md).

 Bir MSI oluşturmak için Visual Studio çözümünüze bir kurulum projesi ekleyin. İndirebilirsiniz CreateMsiSetupProject.tt şablonu kullanmak için bir kurulum projesi oluşturmanın en kolay yöntem olduğunu [VMSDK site](http://go.microsoft.com/fwlink/?LinkID=186128).

#### <a name="to-deploy-a-dsl-in-an-msi"></a>Bir DSL içinde bir MSI dağıtmak için

1. Ayarlama `InstalledByMsi` uzantı bildiriminde. Bu VSX yüklü ve dışında bir MSI tarafından engeller. Bu, diğer Bileşenleri MSI'dahil edilecekse önemlidir.

   1.  Open DslPackage\source.extension.tt

   2.  Önce aşağıdaki satır ekler `<SupportedProducts>`:

       ```xml
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

    Visual Studio adlı bir dosya oluşturur **CreateMsiSetupProject.vdproj**.

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

    -   Ne zaman çift tıklayın dosya, Visual Studio başlatılır ve DSL dosyası DSL Düzenleyicisi'nde açılır.

    Tercih ederseniz, metin şablonu kullanmak yerine Kurulum projesi el ile oluşturabilirsiniz. Bu yordam içeren bir kılavuz için bkz: Bölüm 5, [Görselleştirme ve modelleme SDK'sı Laboratuvar](http://go.microsoft.com/fwlink/?LinkId=208878).

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Konumundan bir MSI yüklü olduğu bir DSL kaldırmak için

1.  Windows içinde açın **programlar ve Özellikler** Denetim Masası.

2.  DSL kaldırın.

3.  Visual Studio'yu yeniden başlatın.