---
title: Azure DevOps hizmetlerinde, Azure kaynak grubu projeleri kullanarak sürekli tümleştirme | Microsoft Docs
description: Azure kaynak grubu dağıtım projeleri Visual Studio kullanarak Azure DevOps Hizmetleri'nde sürekli tümleştirmeyi ayarlama açıklanır.
author: mlearned
manager: douge
ms.assetid: b81c172a-be87-4adc-861e-d20b94be9e38
ms.service: azure-resource-manager
ms.topic: article
ms.workload: azure-vs
ms.date: 08/01/2016
ms.author: mlearned
ms.openlocfilehash: b20a43181ad4d36377e61434b880b491543a6c47
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791611"
---
# <a name="continuous-integration-in-azure-devops-services-using-azure-resource-group-deployment-projects"></a>Azure DevOps hizmetlerinde, Azure kaynak grubu dağıtım projeleri kullanarak sürekli tümleştirme
Azure şablonu dağıtmak için çeşitli aşamalarda görevler: azure'a derleme, Test, kopyalama (aynı zamanda "Hazırlama" olarak adlandırılır) ve şablonu dağıtın. Azure DevOps hizmetler için şablonları dağıtmak için iki farklı yolu vardır. Her iki yöntem de aynı sonuçları sağlar, bu nedenle, iş akışınızı en uygun olanı seçin.

1. Azure kaynak grubu dağıtım projesi (AzureResourceGroup.ps1 dağıtma) dahil edilen PowerShell komut dosyasını çalıştırır, derleme işlem hattı için tek bir adım ekleyin. Betik yapıtları kopyalar ve ardından şablon dağıtır.
2. Birden çok Azure DevOps Hizmetleri derleme adımları, her bir aşama görevi gerçekleştiren ekleyin.

Bu makalede, iki seçenek de gösterilmektedir. İlk seçenek, geliştiricilere Visual Studio ve yaşam döngüsü boyunca sağlayan tutarlılık tarafından kullanılan aynı komut dosyasını kullanarak avantajına sahiptir. İkinci seçenek, yerleşik bir komut dosyası için uygun bir alternatif sunar. Her iki yordam Azure DevOps hizmetlerine işaretli bir Visual Studio dağıtım projesi zaten sahip olduğunuz varsayılır.

## <a name="copy-artifacts-to-azure"></a>Yapıtları Azure'a kopyalama
Şablon dağıtımı için gerekli olan herhangi bir yapı varsa senaryodan bağımsız olarak, Azure Resource Manager erişim kendisine vermeniz gerekir. Bu yapılar, dosyaları gibi dahil edebilirsiniz:

* İç içe şablonlar
* Yapılandırma ve DSC komut dosyaları
* Uygulama ikili dosyalarını

### <a name="nested-templates-and-configuration-scripts"></a>İç içe geçmiş şablonlar ve yapılandırma betiklerini
Visual Studio tarafından sağlanan şablonları kullandığınızda (veya Visual Studio kod parçacıklarıyla yerleşik), PowerShell betiğini yapıtlar yalnızca aşamaları, ayrıca farklı dağıtımlar için kaynaklar için URI'yi parametreleştiren. Betik daha sonra yapıtları azure'da güvenli bir kapsayıcıya kopyalar, bu kapsayıcı için bir SaS belirteci oluşturur ve ardından şablon dağıtımı bu bilgileri geçirir. Bkz: [şablon dağıtımı oluşturma](https://msdn.microsoft.com/library/azure/dn790564.aspx) iç içe geçmiş Şablonlar hakkında daha fazla bilgi edinmek için.  Azure DevOps Hizmetleri'nde görevleri kullanırken, şablon dağıtımınız için uygun görevleri seçin ve gerekirse, parametre değerlerini şablon dağıtımı için hazırlama adımdan geçirmek gerekir.

## <a name="set-up-continuous-deployment-in-azure-pipelines"></a>Azure işlem hatları, sürekli dağıtım ayarlama
PowerShell Betiği, Azure işlem hatlarında çağırmak için derleme işlem hattı güncelleştirmeniz gerekiyor. Kısaca, adımlar şunlardır: 

1. Derleme işlem hattı düzenleyin.
2. Azure işlem hatları Azure yetkilendirmeyi ayarlayın.
3. PowerShell Betiği, Azure kaynak grubu dağıtım projesi başvuran bir Azure PowerShell derleme adımını ekleyin.
4. Değerini *- ArtifactsStagingDirectory* Azure işlem hatlarında yerleşik bir proje ile çalışmak için parametre.

### <a name="detailed-walkthrough-for-option-1"></a>1. seçenek için ayrıntılı kılavuz
Aşağıdaki yordamları, Azure DevOps Services projenizde PowerShell Betiği çalıştıran tek bir görevi kullanılarak sürekli dağıtımı yapılandırmak gereken adımlarda size yol. 

1. Azure DevOps Hizmetleri derleme işlem hattınızı düzenleyin ve bir Azure PowerShell derleme adımı ekleme. Derleme işlem hattı altında seçin **derleme işlem hatlarını** kategori seçip **Düzenle** bağlantı.
   
   ![Derleme işlem hattı Düzenle][0]
2. Yeni bir **Azure PowerShell** adım için derleme işlem hattı oluşturma ve ardından **derleme adımı Ekle...** düğmesi.
   
   ![Derleme adımı ekleme][1]
3. Seçin **dağıtma görevi** kategorisi, select **Azure PowerShell** görev ve ardından kendi **Ekle** düğmesi.
   
   ![Görev ekleme][2]
4. Seçin **Azure PowerShell** derleme adımı ve değerlerini doldurun.
   
   1. Azure DevOps hizmetlere eklenen bir Azure hizmet uç noktası zaten varsa, abonelikte seçin **Azure abonelik** aşağı açılan liste kutusunu ve ardından sonraki bölüme atlayın. 
      
      Azure DevOps Hizmetleri'nde bir Azure hizmet uç noktası sahip değilseniz, birini eklemeniz gerekir. Bu alt bölümde işlemine götürür. Azure hesabınızı bir Microsoft hesabı (örneğin, Hotmail) kullanıyorsa, hizmet sorumlusu kimlik doğrulaması almak için aşağıdaki adımları uygulamanız gerekir.

   2. Seçin **Yönet** yanındaki bağlantı **Azure abonelik** aşağı açılan liste kutusu.
      
      ![Azure aboneliklerini yönetme][3]
   3. Seçin **Azure** içinde **yeni hizmet uç noktası** aşağı açılan liste kutusu.
      
      ![Yeni hizmet uç noktası][4]
   4. İçinde **Azure aboneliği Ekle** iletişim kutusunda **hizmet sorumlusu** seçeneği.
      
      ![Hizmet sorumlusu seçeneği][5]
   5. Azure aboneliği bilgilerinizi ekleyin **Azure aboneliği Ekle** iletişim kutusu. Aşağıdaki öğeler sağlamanız gerekir:
      
      * Abonelik kimliği
      * Abonelik adı
      * Hizmet sorumlusu kimliği
      * Hizmet sorumlusu anahtarı
      * Kiracı kimliği
   6. İçin tercih ettiğiniz bir ad eklemek **abonelik** adı kutusuna. Bu değer daha sonra da görünür **Azure abonelik** aşağı açılan listeden Azure DevOps Hizmetleri. 

   7. Azure abonelik Kimliğinizi bilmiyorsanız, bu almak için aşağıdaki komutlardan birini kullanabilirsiniz.
      
      PowerShell betikleri için kullanın:
      
      `Get-AzureRmSubscription`
      
      Azure CLI için şunu kullanın:
      
      `azure account show`
   8. Bir hizmet sorumlusu kimliği ve hizmet sorumlusu anahtarı Kiracı kimliği, izleme yordamı almak için [oluşturma Active Directory uygulaması ve hizmet sorumlusu portalını kullanarak](/azure/azure-resource-manager/resource-group-create-service-principal-portal) veya [Azure hizmet sorumlusuyla kimlik doğrulaması Resource Manager](/azure/azure-resource-manager/resource-group-authenticate-service-principal).
   9. Hizmet sorumlusu kimliği ve hizmet sorumlusu anahtarı Kiracı kimliği değerlere Ekle **Azure aboneliği Ekle** iletişim kutusuna ve ardından **Tamam** düğmesi.
      
      Artık Azure PowerShell Betiği çalıştırmak için kullanılacak geçerli bir hizmet sorumlusuna sahipsiniz.
5. Derleme işlem hattı düzenleyin ve seçin **Azure PowerShell** derleme adımı. Aboneliği seçin **Azure abonelik** aşağı açılan liste kutusu. (Abonelik görünüp görünmediğini seçin **Yenile** düğmesinin yanındaki **Yönet** bağlantıyı.) 
   
   ![Azure PowerShell derleme görevi yapılandırma][8]
6. Dağıtma-AzureResourceGroup.ps1 PowerShell betiğini bir yol sağlayın. Seçin yanındaki üç nokta (...) düğmesini Bunu yapmak için **betik yolu** kutusunda, Dağıt AzureResourceGroup.ps1 PowerShell betik gidin **betikleri** , proje klasörünü seçin, ardından seçin **Tamam** düğmesi.    
   
   ![Betik yolu seçin][9]
7. Betik seçtikten sonra Build.StagingDirectory çalıştırılır, böylece yolu için betiği güncelleştir (aynı dizinde, *ArtifactsLocation* ayarlanır). "$("Betik yolu başlangıcına. Build.StagingDirectory)/ ekleyerek bunu yapabilirsiniz
   
    ![Betik yolu Düzenle][10]
8. İçinde **betik bağımsız değişkenleri** kutusunda, aşağıdaki parametreleri (tek satır) girin. Visual Studio'da komut dosyasını çalıştırdığınızda, VS parametrelerinde nasıl kullandığını görebilirsiniz **çıkış** penceresi. Bu, derleme adımında parametre değerlerini ayarlamak için bir başlangıç noktası olarak kullanabilirsiniz.
   
   | Parametre | Açıklama |
   | --- | --- |
   | -ResourceGroupLocation |Kaynak grubunun bulunduğu, gibi coğrafi konum değeri **eastus** veya **'Doğu ABD'**. (Adın bir boşluk ise tek tırnak işareti ekleyin.) Bkz: [Azure bölgeleri](https://azure.microsoft.com/regions/) daha fazla bilgi için. |
   | -ResourceGroupName |Bu dağıtım için kullanılan kaynak grubunun adı. |
   | -UploadArtifacts |Bu parametre, mevcut olduğunda belirten yapıtlarını Azure'a yerel sistemden yüklenmesi gerekir. Bu anahtar, şablon dağıtımı hazırlama (örneğin, yapılandırma betiklerini veya iç içe geçmiş şablonlar) PowerShell betiğini kullanarak istediğiniz ek yapıtları gerektiriyorsa ayarlamak yeterlidir. |
   | -StorageAccountName |Aşama yapıtları için bu dağıtım için kullanılan depolama hesabı adı. Yapıtlar dağıtım için hazırlama, bu parametre yalnızca kullanılır. Bu parametre sağlanmazsa betik önceki dağıtım sırasında bir oluşturmuş olmayan yeni bir depolama hesabı oluşturulur. Parametre belirtilmezse, depolama hesabı zaten mevcut olmalıdır. |
   | -StorageAccountResourceGroupName |Depolama hesabı ile ilişkili kaynak grubunun adı. StorageAccountName parametresi için bir değer belirtirseniz, bu parametre gereklidir. |
   | -TemplateFile |Azure kaynak grubu dağıtım projesi içinde şablon dosyasının yolu. Esnekliği artırmak için mutlak bir yol yerine PowerShell betiğini konumuna olan bu parametre için bir yol kullanın. |
   | -TemplateParametersFile |Azure kaynak grubu dağıtım projesi, parametreleri dosyasının yolu. Esnekliği artırmak için mutlak bir yol yerine PowerShell betiğini konumuna olan bu parametre için bir yol kullanın. |
   | -ArtifactStagingDirectory |Bu parametre, PowerShell Betiği, projenin ikili dosyaları burada kopyalanacağı klasörü bilmeniz olanak tanır. Bu değer, PowerShell betiği tarafından kullanılan varsayılan değer geçersiz kılar. Azure DevOps hizmetlerini kullanmak için değeri ayarlamak: - ArtifactStagingDirectory $(Build.StagingDirectory) |
   
   Bir betik bağımsız değişkenleri örneğin (okunabilirlik açısından bozuk satır) aşağıdadır:
   
   ```    
   -ResourceGroupName 'MyGroup' -ResourceGroupLocation 'eastus' -TemplateFile '..\templates\azuredeploy.json' 
   -TemplateParametersFile '..\templates\azuredeploy.parameters.json' -UploadArtifacts -StorageAccountName 'mystorageacct' 
   –StorageAccountResourceGroupName 'Default-Storage-EastUS' -ArtifactStagingDirectory '$(Build.StagingDirectory)'    
   ```
   
   İşiniz bittiğinde, **betik bağımsız değişkenleri** kutusunda, aşağıdaki listede benzemelidir:
   
   ![Betik bağımsız değişkenleri][11]
9. Azure PowerShell derleme adımı için gereken tüm öğeleri ekledikten sonra seçin **kuyruk** Projeyi derlemek için düğme oluşturun. **Derleme** ekran PowerShell betiğinin çıktısını gösterir.

### <a name="detailed-walkthrough-for-option-2"></a>Seçenek 2 için ayrıntılı kılavuz
Aşağıdaki yordamları, Azure DevOps yerleşik görevleri kullanarak Hizmetleri'nde sürekli dağıtımını yapılandırmak gereken adımlarda size yol.

1. İki yeni derleme adımları eklemek için Azure DevOps Hizmetleri derleme işlem hattı düzenleyin. Derleme işlem hattı altında seçin **yapı tanımları** kategori seçip **Düzenle** bağlantı.
   
   ![Yapı tanımını düzenleme][12]
2. Yeni derleme adımları kullanarak derleme işlem hattı ekleyin **derleme adımı Ekle...** düğmesi.
   
   ![Derleme adımı ekleme][13]
3. Seçin **Dağıt** görev kategorisi, select **Azure dosya kopyalama** görev ve ardından kendi **Ekle** düğmesi.
   
   ![Azure dosya kopyalama görevi ekleyin][14]
4. Seçin **Azure kaynak grubu dağıtımı** görev'ı seçin, **Ekle** düğmesine ve ardından **Kapat** **görev kataloğundaki**.
   
   ![Azure kaynak grubu dağıtımı görevi ekleyin][15]
5. Seçin **Azure dosya kopyalama** görev ve değerlerini doldurun.
   
   Azure DevOps hizmetlere eklenen bir Azure hizmet uç noktası zaten varsa, abonelikte seçin **Azure abonelik** aşağı açılan liste kutusu. Bir abonelik yoksa bkz [1. seçenek](#detailed-walkthrough-for-option-1) bir Azure DevOps Hizmetleri'nde ayarlama hakkında yönergeler için.
   
   * Kaynak - girin **$(Build.StagingDirectory)**
   * Azure bağlantı türü - select **Azure Resource Manager**
   * Azure RM aboneliği - abonelik için kullanmak istediğiniz depolama hesabını seçin **Azure abonelik** aşağı açılan liste kutusu. Abonelik görünüp görünmediğini seçin **Yenile** düğmesinin yanındaki **Yönet** bağlantı.
   * Hedef türü - select **Azure Blob**
   * Depolama hesabı RM depolama hesabı - select yapıtları hazırlama için kullanmak istediğiniz
   * Kapsayıcı adı - hazırlama için; kullanmak istediğiniz kapsayıcının adını girin herhangi bir geçerli kapsayıcı adı olabilir ancak bu derleme işlem hattı için ayrılmış kullanın
   
   Çıkış değerleri için:
   
   * URI - depolama kapsayıcısını girin **artifactsLocation**
   * Depolama kapsayıcısı SAS belirteci - girin **artifactsLocationSasToken**
   
   ![Azure dosya kopyalama görevi yapılandırma][16]
6. Seçin **Azure kaynak grubu dağıtımı** derleme adımı ve değerlerini doldurun.
   
   * Azure bağlantı türü - select **Azure Resource Manager**
   * Azure RM aboneliği - dağıtım için bir abonelik seçin **Azure abonelik** aşağı açılan liste kutusu. Bu genellikle önceki adımda kullanılan aynı abonelik olacaktır
   * Eylem - select **oluşturma veya güncelleştirme kaynak grubu**
   * Kaynak grubu - kaynak grubunu seçin veya dağıtım için yeni bir kaynak grubu adını girin
   * Konum - kaynak grubunun konumunu seçin
   * Şablon - dağıtılacak şablonunun adını ve yolunu girin eklenmesini **$(Build.StagingDirectory)**, örneğin: **$(Build.StagingDirectory/DSC-CI/azuredeploy.json)**
   * Şablon parametreleri - girin kullanılacak parametre adı ve yolu eklenmesini **$(Build.StagingDirectory)**, örneğin: **$(Build.StagingDirectory/DSC-CI/azuredeploy.parameters.json)**
   * Şablon parametrelerini geçersiz kıl - girin veya aşağıdaki kodu kopyalayıp yapıştırın:
     
     ```    
     -_artifactsLocation $(artifactsLocation) -_artifactsLocationSasToken (ConvertTo-SecureString -String "$(artifactsLocationSasToken)" -AsPlainText -Force)
     ```
     ![Azure kaynak grubu dağıtım görevine yapılandırın][17]
7. Gereken tüm öğeleri ekledikten sonra derleme işlem hattı kaydedip seçin **yeni derlemeyi kuyruğa al** en üstünde.

## <a name="next-steps"></a>Sonraki adımlar
Okuma [Azure Resource Manager'a genel bakış](/azure-resource-manager/resource-group-overview.md) Azure Resource Manager ve Azure kaynak grupları hakkında daha fazla bilgi edinmek için.

[0]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough1.png
[1]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough2.png
[2]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough3.png
[3]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough4.png
[4]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough5.png
[5]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough6.png
[8]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough9.png
[9]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough10.png
[10]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough11b.png
[11]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough12.png
[12]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough13.png
[13]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough14.png
[14]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough15.png
[15]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough16.png
[16]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough17.png
[17]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough18.png
