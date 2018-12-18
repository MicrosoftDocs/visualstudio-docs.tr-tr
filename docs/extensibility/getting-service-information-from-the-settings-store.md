---
title: Ayarları Store ' hizmet bilgilerini alma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 947eb0fd25e57e00f355afac8dc993071859189c
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500494"
---
# <a name="get-service-information-from-the-settings-store"></a>Ayarlar Deposu'ndan hizmet bilgilerini alma
Ayarlar deposu, tüm kullanılabilir hizmetleri bulmak için veya belirli bir hizmet yüklü olup olmadığını belirlemek için kullanabilirsiniz. Hizmet sınıfı türünü bilmeniz gerekir.  
  
## <a name="to-list-the-available-services"></a>Kullanılabilir hizmetleri listeleyin  
  
1.  Adlı bir VSIX projesi oluşturun `FindServicesExtension` ve adlı özel bir komut ekleyin `FindServicesCommand`. Özel komut oluşturma hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  İçinde *FindServicesCommand.cs*, aşağıdaki using deyimlerini:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Yapılandırma ayarları deposu alın ve ardından Hizmetleri adlı koleksiyon bulunamadı. Bu koleksiyon, kullanılabilir hizmetlerin hepsini içerir. İçinde `MenuItemCommand` yöntemi, mevcut kodu kaldırın ve içerikleri şu kodla değiştirin:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string message = "Available services:\n";  
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");  
        int n = 0;  
        foreach (string service in collection)  
        {  
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";  
        }  
  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
5.  Deneysel örneğinde üzerinde **Araçları** menüsünde tıklatın **çağırma FindServicesCommand**.  
  
     Tüm hizmetler listeleyen bir ileti kutusu görmeniz gerekir.  
  
     Bu ayarları doğrulamak için Kayıt Defteri Düzenleyicisi'ni kullanabilirsiniz.  
  
## <a name="find-a-specific-service"></a>Belirli bir hizmet bulma  
 Ayrıca <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> belirli bir hizmet yüklü olup olmadığını belirlemek için yöntemi. Hizmet sınıfı türünü bilmeniz gerekir.  
  
1.  İçinde MenuItemCallback önceki yordamda oluşturduğunuz proje için yapılandırma ayarları deposu arama `Services` hizmetinin GUID ile adlı koleksiyon içeren koleksiyon. Bu durumda biz Yardım hizmeti için görünür.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();  
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);  
        string message = "Help Service Available: " + hasHelpService;  
  
        MessageBox.Show(message);  
    }  
    ```  
  
2.  Projeyi oluşturmak ve hata ayıklamaya başlayın.  
  
3.  Deneysel örneğinde üzerinde **Araçları** menüsünde tıklatın **çağırma FindServicesCommand**.  
  
     Metin içeren bir ileti görürsünüz **hizmet kullanılabilir Yardım:** ardından **True** veya **False**. Bu ayarı doğrulamak için önceki adımlarda gösterildiği gibi bir kayıt defteri düzenleyicisi kullanabilirsiniz.