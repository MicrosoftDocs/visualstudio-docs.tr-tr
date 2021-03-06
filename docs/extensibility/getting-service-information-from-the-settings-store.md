---
title: Ayarlar deposundan hizmet bilgileri alınıyor | Microsoft Docs
description: Tüm kullanılabilir hizmetleri bulmak veya belirli bir hizmetin yüklenip yüklenmediğini öğrenmek için ayarlar deposunu nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb014803945ea88cd6c2c27eee8c120059014a18
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900653"
---
# <a name="get-service-information-from-the-settings-store"></a>Ayarlar deposundan hizmet bilgilerini al
Tüm kullanılabilir hizmetleri bulmak veya belirli bir hizmetin yüklenip yüklenmediğini öğrenmek için ayarlar deposunu kullanabilirsiniz. Hizmet sınıfının türünü bilmeniz gerekir.

## <a name="to-list-the-available-services"></a>Kullanılabilir hizmetleri listelemek için

1. Adlı bir VSıX projesi oluşturun `FindServicesExtension` ve ardından adlı özel bir komut ekleyin `FindServicesCommand` . Özel bir komut oluşturma hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

2. *Findservicescommand. cs* dosyasında aşağıdaki yönergeleri kullanarak aşağıdakileri ekleyin:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Yapılandırma ayarları deposunu alın ve ardından hizmet adlı alt koleksiyonu bulun. Bu koleksiyon, kullanılabilir tüm hizmetleri içerir. `MenuItemCommand`Yönteminde, var olan kodu kaldırın ve aşağıdaki kodla değiştirin:

    ```csharp
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

4. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

5. Deneysel örnekte, **Araçlar** menüsünde **Findservicescommand komutunu çağır**' a tıklayın.

     Tüm hizmetlerin listelendiği bir ileti kutusu görmeniz gerekir.

     Bu ayarları doğrulamak için kayıt defteri düzenleyicisini kullanabilirsiniz.

## <a name="find-a-specific-service"></a>Belirli bir hizmeti bulma
 Ayrıca, <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> belirli bir hizmetin yüklenip yüklenmediğini anlamak için yöntemini de kullanabilirsiniz. Hizmet sınıfının türünü bilmeniz gerekir.

1. Önceki yordamda oluşturduğunuz projenin MenuItemCallback öğesinde, `Services` hizmet GUID 'si tarafından adlandırılan alt koleksiyonun bulunduğu koleksiyon için yapılandırma ayarları deposunda arama yapın. Bu durumda, yardım hizmetine bakacağız.

    ```csharp
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

2. Projeyi derleyin ve hata ayıklamayı başlatın.

3. Deneysel örnekte, **Araçlar** menüsünde **Findservicescommand komutunu çağır**' a tıklayın.

     Metin **yardım hizmeti kullanılabilir**  bir ileti görmeniz gerekir: **true** veya **false**. Bu ayarı doğrulamak için, önceki adımlarda gösterildiği gibi bir kayıt defteri düzenleyici kullanabilirsiniz.
