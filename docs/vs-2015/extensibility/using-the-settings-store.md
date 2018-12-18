---
title: Ayarları Store kullanarak | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 421ae479d2c25fc6b01ae63083f18c2b1c55c69d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749920"
---
# <a name="using-the-settings-store"></a>Ayarlar Deposu Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ayarları depolar iki tür vardır:  
  
- Salt okunur Visual Studio ve VSPackage ayarları yapılandırma ayarları. Visual Studio bu depoya tüm bilinen .pkgdef dosyalarından ayarları birleştirir.  
  
- Yazılabilir ayarları sayfalarında görüntülenen olanlar gibi kullanıcı ayarlarını da **seçenekleri** iletişim kutusunda, özellik sayfaları ve belirli bir iletişim kutusu. Visual Studio uzantıları bunlar küçük miktarda verilerin yerel depolama için kullanabilir.  
  
  Bu izlenecek yol, yapılandırma ayarı Mağazası'ndan veri okuma işlemi gösterilmektedir. Bkz: [yazmak için kullanıcı ayarları Store](../extensibility/writing-to-the-user-settings-store.md) için kullanıcı ayarları deposuna yazma bir açıklama.  
  
## <a name="creating-the-example-project"></a>Örnek Proje oluşturma  
 Bu bölümde, Tanıtım amaçlı bir menü komutu ile bir basit uzantı projesi oluşturma işlemi gösterilmektedir.  
  
1.  Her Visual Studio uzantısı, uzantı varlıkları içeren bir VSIX dağıtım projesi ile başlar. Oluşturma bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] adlı VSIX projesi `SettingsStoreExtension`. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C# / genişletilebilirlik**.  
  
2.  Şimdi adlı bir özel komut öğe şablonu ekleyin **SettingsStoreCommand**. İçinde **Yeni Öğe Ekle** iletişim kutusunda, Git **Visual C# / genişletilebilirlik** seçip **özel komut**. İçinde **adı** alan penceresinin en altında komut dosyası adı için değiştirme **SettingsStoreCommand.cs**. Özel komut oluşturma hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>Yapılandırma ayarları Store kullanma  
 Bu bölümde, algılamak ve yapılandırma ayarlarını görüntülemek gösterilmektedir.  
  
1. SettingsStorageCommand.cs dosyasına aşağıdakileri ekleyin using deyimlerini:  
  
   ```  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Settings;  
   using Microsoft.VisualStudio.Shell.Settings;  
   using System.Windows.Forms;  
   ```  
  
2. İçinde `MenuItemCallback`, yöntemin gövdesi kaldırın ve bu satırları Al yapılandırma ayarları deposu ekleyin:  
  
   ```  
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
   ```  
  
    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> Üzerinden yönetilen bir yardımcı sınıfıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> hizmeti.  
  
3. Artık Windows Phone araçları yüklü olan çıkış bulun. Kod gibi görünmelidir:  
  
   ```  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
       MessageBox.Show(message);  
   }  
   ```  
  
4. Kodu test edin. Projeyi oluşturmak ve hata ayıklamaya başlayın.  
  
5. Deneysel örneğinde üzerinde **Araçları** menüsünde tıklatın **çağırma SettingsStoreCommand**.  
  
    Kutusu iletisini görmeniz gerekir **Microsoft Windows Phone geliştirici araçları:** ardından **True** veya **False**.  
  
   Visual Studio ayarlar deposu, sistem kayıt defterinde tutar.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Yapılandırma ayarlarını doğrulamak için bir kayıt defteri Düzenleyicisi'ni kullanmak için  
  
1.  Regedit.exe'yi açın.  
  
2.  Gezinmek için HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  \14.0Exp_Config\ ve değil \14.0_Config içeren anahtar baktığınızdan emin olun\\. Visual Studio'nun deneysel örneği çalıştırdığınızda, yapılandırma kayıt defteri kovanında "14.0Exp_Config" ayarlarıdır.  
  
3.  \Installed Products\ düğümünü genişletin. İleti, önceki adımlarda ise **Microsoft Windows Phone geliştirici araçları yüklü: True**, \Installed Products\ bir Microsoft Windows Phone geliştirici araçları düğüm içermelidir. İleti ise **Microsoft Windows Phone geliştirici araçları yüklü: False**, sonra da bir Microsoft Windows Phone geliştirici araçları düğüm \Installed Products\ içermemelidir.

