---
title: Azure bulut hizmeti rollerini yapılandırma
description: Ayarlama ve rolleri Visual Studio kullanarak Azure bulut Hizmetleri için yapılandırma hakkında bilgi edinin.
author: ghogen
manager: douge
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e1b10fc38abaf497332746e1367f5727f0998023
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064805"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti rollerini yapılandırma
Azure bulut hizmeti çalışan veya web rollerinin bir veya daha fazla olabilir. Her rol için bu rolü nasıl ayarlandığı tanımlayın ve bu rolü nasıl çalıştığını da yapılandırmanız gerekir. Cloud Services rolleri hakkında daha fazla bilgi edinmek için videoyu bkz [Azure bulut hizmetlerine giriş](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services). 

Bulut hizmetiniz için bilgiler aşağıdaki dosyalarda saklanır:

- **ServiceDefinition.csdef** -Hizmet tanım dosyası hangi roller gereklidir dahil olmak üzere bulut hizmeti, uç noktaları ve sanal makine boyutu için çalışma zamanı ayarlarını tanımlar. Depolanan verilerin hiçbiri `ServiceDefinition.csdef` rolünüz çalışırken değiştirilebilir.
- **ServiceConfiguration.cscfg** - hizmet yapılandırma dosyasının kaç rol örneklerini çalıştırma yapılandırır ve ayarlarının değerleri, bir rol için tanımlanmış. Depolanan veriler `ServiceConfiguration.cscfg` rolünüz çalışırken değiştirilebilir.

Farklı değerler için bir rol nasıl çalıştığını denetleyen ayarları depolamak için birden çok hizmet yapılandırmaları tanımlayabilirsiniz. Her dağıtım ortamı için farklı hizmet yapılandırmasını kullanabilirsiniz. Örneğin, bir yerel hizmet yapılandırmasında yerel Azure depolama öykünücüsü kullanma ve bulutta Azure depolamanızı kullanmak için başka bir hizmet yapılandırması oluşturmak için depolama hesabı bağlantı dizesi ayarlayabilirsiniz.

Visual Studio'da bir Azure bulut hizmeti oluşturduğunuzda, iki hizmet yapılandırması otomatik olarak oluşturulur ve Azure projenize eklenir:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Azure bulut hizmeti yapılandırın
Visual Studio'da Çözüm Gezgini'nden bir Azure bulut hizmeti aşağıdaki adımlarda gösterildiği gibi yapılandırabilirsiniz:

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünden seçin **özellikleri**.
   
    ![Çözüm Gezgini proje bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Proje özellikleri sayfasında seçin **geliştirme** sekmesi. 

    ![Proje Özellikleri sayfası - geliştirme sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. İçinde **hizmet yapılandırması** listesinde, düzenlemek istediğiniz hizmet yapılandırmasının adını seçin. (Bu rol için tüm hizmet yapılandırması değişiklik yapmak isteyip istemediğinizi seçin **yapılandırmalarında**.)
   
    > [!IMPORTANT]
    > Belirli hizmet yapılandırması seçerseniz, bazı özellikler tüm yapılandırmalar için yalnızca ayarlanabilir için devre dışı bırakıldı. Bu özelliklerini düzenlemek için seçmelisiniz **yapılandırmalarında**.
    > 
    > 
   
    ![Azure bulut hizmeti için hizmet yapılandırması listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Rol örnekleri sayısını değiştirin
Bulut hizmetinizin performansını artırmak için kullanıcı ya da belirli bir rol için beklenen yük sayısına dayalı olarak çalıştırılan bir rolün örnekleri sayısını değiştirebilirsiniz. Bulut hizmeti Azure içinde çalıştığında her bir rol örneği için ayrı bir sanal makine oluşturulur. Bu, bu bulut hizmeti dağıtımı için faturalandırma etkiler. Faturalama hakkında daha fazla bilgi için bkz. [Microsoft Azure için faturanızı anlayın bölümü](/azure/billing/billing-understand-your-bill).

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. İçinde **Çözüm Gezgini**, proje düğümünü genişletin. Altında **rolleri** düğümünü istediğiniz güncelleştirmek ve bağlam menüsünden seçmek için role sağ **özellikleri**.

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seçin **yapılandırma** sekmesi.

    ![Yapılandırma sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. İçinde **hizmet yapılandırması** listesinde, güncelleştirmek istediğiniz hizmet yapılandırması'nı seçin.
   
    ![Hizmet yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. İçinde **örnek sayısı** metin kutusunda, bu rol için başlatmak istediğiniz örnek sayısını girin. Bulut hizmeti Azure'da yayımlarken her örneği ayrı bir sanal makinede çalışır.

    ![Örnek sayısını güncelleştiriliyor](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Visual Studio araç, select **Kaydet**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Depolama hesapları için bağlantı dizelerini Yönet
Ekleyin, kaldırın veya bağlantı dizeleri, hizmet yapılandırması için değiştirin. Örneğin, bir değeri olan bir yerel hizmet yapılandırması için bir yerel bağlantı dizesi isteyebilirsiniz `UseDevelopmentStorage=true`. Azure'da bir depolama hesabını kullanan bir bulut hizmeti yapılandırması yapılandırmak isteyebilirsiniz.

> [!WARNING]
> Bir depolama hesabı bağlantı dizesi için Azure depolama hesabı anahtar bilgilerini girdiğinizde, bu bilgiler hizmet yapılandırma dosyasında yerel olarak depolanır. Ancak, bu bilgileri şu anda şifreli metin olarak depolanmaz.
> 
> 

Her hizmet yapılandırması için farklı bir değer kullanarak, bulut hizmetinizin farklı bağlantı dizelerini kullanma veya Bulut hizmetinizi Azure'da yayımlarken, kodunuzu değiştirmeniz gerekmez. Kodunuzda bağlantı dizesi için aynı adı kullanabilirsiniz ve bulut hizmetinizi oluşturma sırasında veya uygulamayı yayımladığınızda seçtiğiniz hizmet yapılandırmasına göre farklı değerdir.

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. İçinde **Çözüm Gezgini**, proje düğümünü genişletin. Altında **rolleri** düğümünü istediğiniz güncelleştirmek ve bağlam menüsünden seçmek için role sağ **özellikleri**.

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seçin **ayarları** sekmesi.

    ![Ayarlar sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. İçinde **hizmet yapılandırması** listesinde, güncelleştirmek istediğiniz hizmet yapılandırması'nı seçin.

    ![Hizmet yapılandırması](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Bir bağlantı dizesi eklemek için seçin **ayar Ekle**.

    ![Bağlantı dizesi Ekle](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Yeni ayar listesine eklendikten sonra listedeki satıra gerekli bilgilerle güncelleştirin.

    ![Yeni bağlantı dizesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Ad** -bağlantı dizesi için kullanmak istediğiniz adı girin.
    - **Tür** - seçin **bağlantı dizesi** aşağı açılan listeden.
    - **Değer** -ya da doğrudan bağlantı dizesini girebilirsiniz **değer** hücre veya iş için üç nokta (...) seçin **depolama bağlantı dizesi oluştur** iletişim.  

1. İçinde **depolama bağlantı dizesi oluştur** iletişim kutusunda bir seçenek için **bağlanırken**. Seçenek için yönergeleri izleyin:

    - **Microsoft Azure depolama öykünücüsü** -bu seçeneği seçerseniz, bunlar yalnızca Azure'da geçerli olan kalan Ayarları iletişim kutusundaki devre dışı bırakılır. Seçin **Tamam**.
    - **Aboneliğinizi** - bu seçeneği seçerseniz ya da seçin ve bir Microsoft hesabıyla oturum açılan listeyi kullanın veya bir Microsoft hesabı ekleyin. Bir Azure aboneliğini ve depolama hesabı seçin. Seçin **Tamam**.
    - **Kimlik bilgileri'el ile girilen** -depolama hesabı adı ve birincil veya ikinci anahtarı girin. Bir seçeneğini **bağlantı** (HTTPS çoğu senaryo için önerilir.) Seçin **Tamam**.

1. Bir bağlantı dizesi silmek için bağlantı dizesini seçin ve ardından **Kaldır ayarını**.

1. Visual Studio araç, select **Kaydet**.

## <a name="programmatically-access-a-connection-string"></a>Bir bağlantı dizesi programlamayla erişme

Aşağıdaki adımlarda, C# kullanarak bir bağlantı dizesi programlı olarak erişmek gösterilmektedir.

1. Aşağıdaki using yönergelerini nerede seçeceğiz ayarını kullanmak için bir C# dosyasına:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Aşağıdaki kod, bir bağlantı dizesi erişmeye ilişkin bir örnek göstermektedir. Değiştirin &lt;ConnectionStringName > yer tutucu uygun değere sahip. 

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Azure bulut hizmetinizde kullanmak için özel ayarlar Ekle
Hizmet yapılandırma dosyasında özel ayarlar bir ad ve bir özel hizmet yapılandırması için bir dize değeri eklemenize olanak sağlar. Bir ayarın değerini okumak ve kodunuzda mantığı denetlemek için bu değeri kullanarak bulut hizmetinizde bir özelliğini yapılandırmak için bu ayarı kullanmak seçebilirsiniz. Bu hizmet yapılandırma değerleri, hizmet paketi veya Bulut hizmetinizi çalışırken yeniden derlemeye gerek kalmadan değiştirebilirsiniz. Kodunuzu bildirimleri için bir ayar değiştiğinde kontrol edebilirsiniz. Bkz: [RoleEnvironment.Changing olay](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Ekleyin, kaldırın veya hizmet yapılandırmalarınız için özel ayarları değiştirin. Bu dizeler için farklı hizmet yapılandırması için farklı değerler isteyebilirsiniz.

Her hizmet yapılandırması için farklı bir değer kullanarak, bulut hizmetiniz farklı dizeleri kullanın veya Bulut hizmetinizi Azure'da yayımlarken, kodunuzu değiştirmeniz gerekmez. Kodunuzda dize için aynı adı kullanabilirsiniz ve bulut hizmetinizi oluşturma sırasında veya uygulamayı yayımladığınızda seçtiğiniz hizmet yapılandırmasına göre farklı değerdir.

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. İçinde **Çözüm Gezgini**, proje düğümünü genişletin. Altında **rolleri** düğümünü istediğiniz güncelleştirmek ve bağlam menüsünden seçmek için role sağ **özellikleri**.

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seçin **ayarları** sekmesi.

    ![Ayarlar sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. İçinde **hizmet yapılandırması** listesinde, güncelleştirmek istediğiniz hizmet yapılandırması'nı seçin.

    ![Hizmet yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Özel bir ayarı eklemek için seçin **ayar Ekle**.

    ![Özel ayar Ekle](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Yeni ayar listesine eklendikten sonra listedeki satıra gerekli bilgilerle güncelleştirin.

    ![Yeni özel ayarı](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Ad** -ayarının adı girin.
    - **Tür** - seçin **dize** aşağı açılan listeden.
    - **Değer** -ayarın değerini girin. Ya da doğrudan bir değer girebilirsiniz **değer** hücre ya da değer girmek için üç nokta (...) seçin **dize Düzenle** iletişim.  

1. Özel bir ayarı silmek için ayarı seçin ve ardından **Kaldır ayarını**.

1. Visual Studio araç, select **Kaydet**.

## <a name="programmatically-access-a-custom-settings-value"></a>Özel bir ayarın değerini programlamayla erişme
 
Aşağıdaki adımlarda, C# kullanarak özel bir ayarı programlı olarak erişmek gösterilmektedir.

1. Aşağıdaki using yönergelerini nerede seçeceğiz ayarını kullanmak için bir C# dosyasına:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Aşağıdaki kod bir özel ayarı erişmeye ilişkin bir örnek göstermektedir. Değiştirin &lt;SettingName > yer tutucu uygun değere sahip. 
    
    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Her rol örneği için yerel depolamayı yönetin
Her bir rol örneği için yerel dosya sistemi depolaması ekleyebilirsiniz. Depolama, erişilebilir değil. diğer verilerin depolandığı için rol örneklerini veya diğer rolleri tarafından depolanan veriler.  

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. İçinde **Çözüm Gezgini**, proje düğümünü genişletin. Altında **rolleri** düğümünü istediğiniz güncelleştirmek ve bağlam menüsünden seçmek için role sağ **özellikleri**.

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seçin **yerel depolama** sekmesi.

    ![Yerel depolama sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. İçinde **hizmet yapılandırması** listesinde **yapılandırmalarında** yerel depolama ayarlarını uygulamak için tüm hizmet yapılandırması olarak seçilidir. Başka bir değer devre dışı bırakılmasını sayfasında tüm giriş alanlarını sonuçlanır. 

    ![Hizmet yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Yerel depolama giriş eklemek için seçin **yerel depolama ekleyin**.

    ![Yerel depolama ekleyin](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Yerel depolama girişte listesine eklendikten sonra listedeki satıra gerekli bilgilerle güncelleştirin.

    ![Yerel depolama girişte](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Ad** -yeni yerel depolama için kullanmak istediğiniz adı girin.
    - **Boyut (MB)** -yeni yerel depolama alanı için gereksinim duyduğunuz MB boyutunu girin.
    - **Rol geri dönüşümü üzerinde temiz** -sanal makine rolü için geri dönüştürüldüğünde yeni bir yerel depolamadaki verileri kaldırmak için bu seçeneği belirleyin.

1. Yerel depolama girişi silmek için girişi seçin ve ardından **kaldırmak yerel depolama**.

1. Visual Studio araç, select **Kaydet**.

## <a name="programmatically-accessing-local-storage"></a>Yerel depolama program aracılığıyla erişme

Bu bölümde, bir test metin dosyası yazarak C# kullanarak yerel depolama programlı olarak erişmek verilmektedir `MyLocalStorageTest.txt`.  

### <a name="write-a-text-file-to-local-storage"></a>Yerel depolama alanına bir metin dosyasına yazma

Aşağıdaki kod, yerel depolama alanına bir metin dosyası yazmak nasıl bir örnek gösterir. Değiştirin &lt;LocalStorageName > yer tutucu uygun değere sahip. 

    ```csharp
    // Retrieve an object that points to the local storage resource
    LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");
    
    //Define the file name and path
    string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
    String filePath = Path.Combine(paths);
    
    using (FileStream writeStream = File.Create(filePath))
    {
        Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
        writeStream.Write(textToWrite, 0, textToWrite.Length);
    }

    ```

### <a name="find-a-file-written-to-local-storage"></a>Bir dosyayı yerel depolama alanına yazılan bulma

Önceki bölümde kod tarafından oluşturulan bir dosyayı görüntülemek için aşağıdaki adımları izleyin:
    
1.  Windows bildirim alanındaki Azure simgesine sağ tıklayın ve bağlam menüsünden seçin **Göster işlem öykünücüsü kullanıcı Arabiriminde**. 

    ![Azure işlem öykünücüsünü Göster](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Web rolü seçin.

    ![Azure işlem öykünücüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. Üzerinde **Microsoft Azure işlem öykünücüsü** menüsünde **Araçları** > **açık yerel depo**.

    ![Açık bir yerel depo menü öğesi](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Windows Gezgini penceresi açıldığında, girin ' MyLocalStorageTest.txt'' içine **arama** metin kutusu ve select **Enter** aramayı başlatmak için. 

## <a name="next-steps"></a>Sonraki adımlar
Visual Studio'da Azure projeleri hakkında daha fazla bilgi edinmek [bir Azure projesi yapılandırma](vs-azure-tools-configuring-an-azure-project.md). Bulut hizmet şeması hakkında daha fazla bilgi edinmek [şema başvurusu](https://msdn.microsoft.com/library/azure/dd179398).

