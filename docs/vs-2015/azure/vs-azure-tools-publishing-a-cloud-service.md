---
title: Azure araçlarını kullanarak bir bulut hizmeti yayımlama | Microsoft Docs
description: Visual Studio kullanarak Azure bulut hizmeti projelerini Microsoft Azure yayımlama hakkında bilgi edinin.
author: ghogen
manager: douge
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: cf29e1cdde71d2e8ef7caa9bc91bc31c30c7bc41
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003686"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Visual Studio kullanarak bulut hizmetini yayımlama

Visual Studio, Azure, bulut hizmetinin hazırlık ve üretim ortamları için destekle doğrudan uygulama yayımlayabilirsiniz. Yayımlama sırasında dağıtım ortamını ve dağıtım paketi için geçici olarak kullanılan depolama hesabı seçin.

Geliştirme ve test Azure uygulaması, değişiklikleri, web rolleri için artımlı olarak yayımlamak için Web Dağıtımı'ı kullanabilirsiniz. Dağıtım ortamı uygulamanızı yayımladıktan sonra Web dağıtımı, değişiklikler doğrudan sanal web rolü çalıştıran makineye dağıtmanızı sağlar. Paketleme ve yayımlama, tüm Azure uygulama değişiklikleri test etmek için web rolünüz güncelleştirmek istediğiniz her zaman gerekmez. Bu yaklaşımda, bir dağıtım ortamı için yayımlanan uygulama için beklemenize gerek kalmadan test etmek için bulutta web rolü değişikliklerinizi kullanılabilir olabilir.

Azure uygulamanızı yayımlayın ve Web dağıtımı kullanarak bir web rolü güncelleştirmek için aşağıdaki yordamları kullanın:

- Yayımlama veya Visual Studio'dan Azure uygulamaları paketleme
- Geliştirme ve Test döngüsünün bir parçası olarak bir web rolü güncelleştirme

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Yayımlama veya Visual Studio'dan Azure uygulamaları paketleme

Azure uygulamanızı yayımladığınızda, aşağıdaki görevlerden birini yapabilirsiniz:

- Hizmet paketi oluştur: bir dağıtım ortamından uygulamanızı yayımlamak için bu paketin ve hizmet yapılandırma dosyasını kullanabilirsiniz [Azure portalında](https://portal.azure.com).

- Visual Studio'dan Azure projenizi yayımlamak: uygulamanızı doğrudan Azure'da yayımlamak için Yayımla Sihirbazı'nı kullanın. Bilgi için [Azure uygulaması Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Visual Studio'dan bir hizmet paketi oluşturmak için

1. Uygulamanızı yayımlamaya hazır olduğunuzda, Çözüm Gezgini'ni açın, rolleriniz içeren Azure projesinin kısayol menüsünü açın ve Yayımla'ı seçin.

1. Yalnızca bir hizmet paketi oluşturmak için aşağıdaki adımları izleyin:

   a. Azure projesinin kısayol menüsünde **paket**.

   b. İçinde **paket Azure uygulaması** iletişim kutusunda, bir paket oluşturmak istediğiniz hizmet yapılandırması'nı seçin ve yapı yapılandırma öğesini seçin.

   c. (İsteğe bağlı) Yayımladıktan sonra bulut hizmeti için Uzak Masaüstü'nü etkinleştirmek için işaretleyin **tüm roller için Uzak masaüstünü etkinleştir**ve ardından **ayarları** Uzak Masaüstü kimlik bilgilerini yapılandırmak için. Daha fazla bilgi için [Visual Studio kullanarak Azure Cloud Services'ta bir rol için Uzak Masaüstü Bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Bulut hizmetinizin yayımladıktan sonra hata ayıklamak istiyorsanız, uzak seçerek hata ayıklama etkinleştirme **etkinleştirme uzaktan hata ayıklayıcı tüm roller için**.

   d. Paketi oluşturmak için Seç **paket** bağlantı.

      Dosya Gezgini'nde, yeni oluşturulan paket dosyasının konumunu gösterir. Azure portalından kullanabilirsiniz, böylece bu konuma kopyalayabilirsiniz.

   e. Bu paket için bir dağıtım ortamı yayımlamak için bir bulut hizmeti oluşturma ve bu paketin Azure portalıyla bir ortama dağıtırken kullanabileceğiniz bu konuma paket konumu olarak kullanmanız gerekir.

1. (İsteğe bağlı) Dağıtım işlemi, etkinlik günlüğü ' nde satır öğesi için kısayol menüsünden iptal etmeyi seçmediğiniz **iptal edip Kaldır**. Bu komut, dağıtım işlemi durdurur ve Azure'dan dağıtım ortamı siler. Dağıtım sonrasında ortamın kaldırmak için Azure portalını kullanın.

1. (İsteğe bağlı) Rol örneklerinizin başlattıktan sonra Visual Studio dağıtım ortamı otomatik olarak gösterir. **bulut Hizmetleri** Sunucu Gezgininde. Buradan, tek tek rol örneklerini durumunu görebilirsiniz. Bkz: [Cloud Explorer ile yönetme Azure kaynaklarını](vs-azure-tools-resources-managing-with-cloud-explorer.md). Bunlar hala başlatılıyor durumda olduğu zamanlar rol örnekleri aşağıda gösterilmiştir:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Geliştirme ve Test döngüsünün bir parçası olarak bir web rolü güncelleştirme

Uygulamanızın arka uç altyapısı kararlı olduğundan, ancak web rollerinin daha sık güncelleştirilmesi gereken yalnızca bir web rolü projenizde güncelleştirmek için Web Dağıtımı'ı kullanabilirsiniz. Web dağıtımı istemediğinizde yeniden oluşturun ve arka uç çalışan rolleri dağıtın veya birden çok web rol varsa ve web rollerinin yalnızca birini güncelleştirmek istiyorsanız kullanışlıdır.

### <a name="requirements-for-using-web-deploy"></a>Web Dağıtımı'nı kullanma gereksinimleri

- **Geliştirme ve test amacıyla yalnızca**: web rolü çalıştığı sanal makineye doğrudan yapılan değişiklikler. Bu sanal makineyi geri dönüştürülmesi gerekiyorsa, yayımladığınız özgün paketi sanal makine rolü için yeniden oluşturmak için kullanıldığından değişiklikler kaybolur. Web rolü için en son değişiklikleri almak için uygulamanızı yeniden yayımlayın.

- **Yalnızca web rolleri güncelleştirilebilir**: çalışan rolleri güncelleştirilemiyor. Ayrıca, güncelleştirilemiyor `RoleEntryPoint` içinde `web role.cs`.

- **Yalnızca tek bir örnek bir web rolünün destekleyebilir**: dağıtım ortamınızda birden çok örneğini herhangi bir web rolü olamaz. Ancak, birden çok web rolleri her tek bir örnekle desteklenir.

- **Uzak Masaüstü bağlantılarını etkinleştirin**: Bu gereksinim, değişiklikler Internet Information Services (IIS) çalıştıran bir sunucuya dağıtmak için sanal makineye bağlanmak için kullanıcı adı ve parola kullanmak Web dağıtımı sağlar. Ayrıca, bu sanal makinede IIS'ye güvenilen bir sertifika eklemek için bu sanal makineye bağlanmak gerekebilir. (Bu sertifika, Web dağıtımı tarafından kullanılan IIS için Uzak bağlantı güvenli olmasını sağlar.)

Aşağıdaki yordam, kullandığınızı varsayar **Azure uygulamasını Yayımla** Sihirbazı.

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Uygulamanızı yeniden yayımladığınızda, Web dağıtımı etkinleştir

1. Etkinleştirmek için **tüm web rolleri için Web dağıtımını etkinleştirin** seçeneği, Uzak Masaüstü bağlantılarını yapılandır. Seçin **Uzak Masaüstü'nü etkinleştirme** tüm roller için ve ardından buna uzaktan bağlanmak için kullanılan kimlik bilgilerini sağlamanız **uzak masaüstü yapılandırması** açılan kutusunda. Bkz: [Visual Studio kullanarak Azure Cloud Services'ta bir rol için Uzak Masaüstü Bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Uygulamanızdaki tüm web rolleri için Web Dağıtımı'nı etkinleştirmek için seçin **tüm web rolleri için Web dağıtımını etkinleştirin**.

    Uyarı sarı bir üçgen olarak görünür. Web dağıtımı, hassas verileri yüklemek için önerilen varsayılan olarak, güvenilmeyen, otomatik olarak imzalanan bir sertifika kullanır. Bu işlem için hassas verilerin güvenliğini sağlamak ihtiyacınız varsa, Web dağıtımı bağlantılar için kullanılacak bir SSL sertifikası ekleyebilirsiniz. Bu sertifika, güvenilen bir sertifika olması gerekiyor. Daha fazla bilgi için [dağıtma web güvenli hale getirin](#make-web-deploy-secure).

1. Seçin **sonraki** gösterilecek **özeti** ekran ve ardından **Yayımla** bulut hizmeti dağıtmak için.

    Bulut hizmeti yayımlanır. Oluşturulan sanal makine, Web dağıtımı yeniden yayımlanması olmadan web rollerinizin güncelleştirmek için kullanılabilir olacak şekilde, IIS için etkin olan uzak bağlantılar vardır.

   > [!NOTE]
   > Bir web rolü için yapılandırılmış birden fazla örnek varsa, her web rolüyle uygulamanızı yayımlamak için oluşturulan paketi tek örneği sınırlı olduğunu belirten bir uyarı iletisi görüntülenir. Seçin **Tamam** devam etmek için. Gereksinimleri bölümünde belirtildiği gibi her rolün yalnızca bir örneğine ancak birden fazla web rolüne sahip olabilir.

### <a name="update-your-web-role-by-using-web-deploy"></a>Web dağıtımı kullanarak web rolünüz güncelleştir

1. Web dağıtımı kullanabilmeniz için projenin tüm yayımlama, çözümünüzdeki bu proje düğümüne sağ tıklayın ve fareyle istediğiniz Visual Studio'da web rolünüz için kod değişiklikleri yapabilir **Yayımla**. **Web'i Yayımla** iletişim kutusu görüntülenir.

1. (İsteğe bağlı) IIS için Uzak bağlantılar için kullanılacak güvenilir bir SSL sertifikası eklediyseniz temizleyebilirsiniz **izin Güvenilmeyen sertifika** onay kutusu. Web dağıtımı güvenli hale getirmek için bir sertifika ekleme hakkında daha fazla bilgi için bkz **olun Web dağıtma güvenli** bu makalenin ilerleyen bölümlerinde.

1. Web dağıtımı kullanabilmeniz için kullanıcı adını ve paket ilk kez yayımlandığında, Uzak Masaüstü bağlantısı için ayarladığınız parolayı Yayımla mekanizma gerekir.

   a. İçinde **kullanıcı adı**, kullanıcı adını girin.

   b. İçinde **parola**, parolayı girin.

   c. (İsteğe bağlı) Bu profilde bu parola kaydetmek istiyorsanız, seçin **Parolayı Kaydet**.

1. Web rolünüz değişiklikleri yayımlamak için **Yayımla**.

    Durum satırı görüntüler **yayımlama başlatıldı**. Yayımlama tamamlandığında **başarılı Yayımla** görünür. Sanal makinenizde web rolü için şimdi değişiklikleri dağıtılan yok. Artık Azure uygulamanızı değişikliklerinizi test etmek için Azure ortamında başlayabilirsiniz.

### <a name="make-web-deploy-secure"></a>Web dağıtımı güvenli hale getirmek

1. Web dağıtımı, hassas verileri yüklemek için önerilen varsayılan olarak, güvenilmeyen, otomatik olarak imzalanan bir sertifika kullanır. Bu işlem için hassas verilerin güvenliğini sağlamak ihtiyacınız varsa, Web dağıtımı bağlantılar için kullanılacak bir SSL sertifikası ekleyebilirsiniz. Bu sertifika bir sertifika yetkilisinden (CA) elde güvenilen bir sertifika gerekir.

    Web dağıtımı her sanal makine için güvenli her web rolünüz için yapmak için web için kullanmak istediğiniz güvenilen bir sertifika yükleyin Azure Portalı'na dağıtma. Bu sertifika, sertifika uygulamanızı yayımladığınızda, web rolü için oluşturduğunuz sanal makineye eklendikten emin olur.

1. IIS, Uzaktan bağlantılar için kullanılacak güvenilir bir SSL sertifikası eklemek için aşağıdaki adımları izleyin:

   a. Web rolü çalıştıran sanal makineye bağlanmak için web rolünde örneğini seçin **Cloud Explorer** veya **Sunucu Gezgini**ve ardından **Uzak Masaüstü kullanarak bağlan**  komutu. Sanal makineye bağlanma hakkında ayrıntılı adımlar için bkz: [Visual Studio kullanarak Azure Cloud Services'ta bir rol için Uzak Masaüstü Bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). Tarayıcınız indirmek ister bir `.rdp` dosya.

   b. Bir SSL sertifikası eklemek için yönetim hizmeti, IIS Yöneticisi'nde açın. IIS Yöneticisi'nde açarak SSL'yi **bağlamaları** bağlantısını **eylem** bölmesi. **Site bağlaması Ekle** iletişim kutusu görüntülenir. Seçin **Ekle**, HTTPS seçin **türü** aşağı açılan listesi. İçinde **SSL sertifikası** listesinde, bir CA tarafından imzalanmış ve Azure portalına yüklediğiniz SSL sertifikasını seçin. Daha fazla bilgi için [yönetim hizmeti için bağlantı ayarlarını yapılandırma](http://go.microsoft.com/fwlink/?LinkId=215824).

      > [!NOTE]
      > Güvenilir bir SSL sertifikası ekleme sarı uyarı üçgen artık görünür **Yayımlama Sihirbazı**.

## <a name="include-files-in-the-service-package"></a>Hizmet paketinde dosyaları Ekle

Belirli dosyaları, bunlar bir rol için oluşturulan sanal makinede kullanılabilir olacak şekilde, hizmet paketinize dahil etmek gerekebilir. Örneğin, eklemek isteyebilirsiniz bir `.exe` veya `.msi` hizmet paketi bir başlangıç betiği tarafından kullanılan dosya. Veya bir web rolü veya çalışan rolü projesi gerektiren bir derleme eklemeniz gerekebilir. Dosyaları eklemek için Azure uygulamanız için çözümü eklenmesi gerekir.

1. Bir derleme için bir hizmet paketi eklemek için aşağıdaki adımları kullanın:

   a. İçinde **Çözüm Gezgini**, başvurulan derleme eksik olan proje için proje düğümünü açın.
   b. Bütünleştirilmiş kod projesine eklemek için kısayol menüsünü açın **başvuruları** klasörünü ve ardından **Başvuru Ekle**. Başvuru Ekle iletişim kutusu görüntülenir.
   c. Ekleyin ve ardından istediğiniz başvuruyu seçin **Tamam**. Başvuru altındaki listeye eklenen **başvuruları** klasör.
   d. Eklediğiniz bir derleme için kısayol menüsünü açın ve seçin **özellikleri**. **Özellikleri** penceresi görüntülenir.

      Hizmet paketi bu derlemede eklenecek **Yereli Kopyala listesi** seçin **True**.
1. İçinde **Çözüm Gezgini** başvurulan derleme eksik olan proje için proje düğümünü açın.

1. Bütünleştirilmiş kod projesine eklemek için kısayol menüsünü açın **başvuruları** klasörünü ve ardından **Başvuru Ekle**. **Başvuru Ekle** iletişim kutusu görüntülenir.

1. Ekleyin ve ardından istediğiniz başvuruyu seçin **Tamam** düğmesi.

    Başvuru altındaki listeye eklenen **başvuruları** klasör.

1. Eklediğiniz bir derleme için kısayol menüsünü açın ve seçin **özellikleri**. Özellikler penceresinde görünür.

1. Hizmet paketi bu derlemede eklenecek **Yereli Kopyala** listesinde **True**.

1. Hizmet paketi, web rolü projesine eklenen dosyaları eklemek için dosya için kısayol menüsünü açın ve ardından **özellikleri**. Gelen **özellikleri** penceresinde seçin **içerik** gelen **derleme eylemi** liste kutusu.

1. Çalışan rolü projeniz eklenmiş olan hizmet paketi dosyaları eklemek için dosya için kısayol menüsünü açın ve ardından **özellikleri**. Gelen **özellikleri** penceresinde seçin **yeniyse Kopyala** gelen **çıkış dizinine Kopyala** liste kutusu.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio'dan Azure'a yayımlama hakkında daha fazla bilgi için bkz [Azure uygulaması Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md).
