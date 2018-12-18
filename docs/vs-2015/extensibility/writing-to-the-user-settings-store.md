---
title: Kullanıcı ayarları Store için yazma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70522d8a291cad559a042dab7f4eeb3c3c4684ac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779729"
---
# <a name="writing-to-the-user-settings-store"></a>Kullanıcı Ayarları Deposuna Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıcı ayarları benzeyen yazılabilir ayarlarıdır **Araçlar / Seçenekler** iletişim ve özellikleri windows belirli bir iletişim kutusu. Visual Studio uzantıları bunlar küçük miktarlarda veri depolamak için kullanabilirsiniz. Bu izlenecek yolda not defteri için Visual Studio dış bir araç olarak okuma ve kullanıcı ayarları deposuna yazma tarafından nasıl ekleneceğini gösterir.  
  
### <a name="backing-up-your-user-settings"></a>Kullanıcı ayarlarınızı yedekleme  
  
1.  Hata ayıklama ve yordamı yineleyin dış Araçlar ayarlarına olması gerekir. Bunu yapmak için bunları gerektiği gibi geri yükleyebilirsiniz, böylece özgün ayarlarına kaydetmeniz gerekir.  
  
2.  Regedit.exe'yi açın.  
  
3.  HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External araçları gidin\\.  
  
    > [!NOTE]
    >  \14.0Exp\ ve değil \14.0 içeren anahtar baktığınızdan emin olun\\. Visual Studio'nun deneysel örneği çalıştırdığınızda, kullanıcı ayarlarınızı kayıt defteri kovanında "14.0Exp" dir.  
  
4.  \External Tools\ alt sağ tıklayın ve ardından **dışarı**. Emin olun **Seçili dal** seçilir.  
  
5.  Sonuçta elde edilen dış Tools.reg dosyayı kaydedin.  
  
6.  Daha sonra dış araçların ayarlarını sıfırlamak istediğiniz zaman HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\ içinde kayıt defteri anahtarı seçin ve tıklayın **Sil** bağlam menüsünde.  
  
7.  Zaman **Anahtar Silinmesini Onayla** iletişim kutusu görüntülendikten sonra **Evet**.  
  
8.  Daha önce kaydettiğiniz dış Tools.reg dosyaya sağ tıklayın, **birlikte Aç**ve ardından **Kayıt Defteri Düzenleyicisi'ni**.  
  
## <a name="writing-to-the-user-settings-store"></a>Kullanıcı Ayarları Deposuna Yazma  
  
1.  UserSettingsStoreExtension adlı bir VSIX projesi oluşturun ve ardından UserSettingsStoreCommand adlı özel bir komut ekleyin. Özel komut oluşturma hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  UserSettingsStoreCommand.cs içinde aşağıdaki ekleme using deyimlerini:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  MenuItemCallback, yöntem gövdesi silme ve kullanıcı ayarlarını depolamak, aşağıdaki gibi alır:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Artık, Not Defteri zaten dış bir araç olarak ayarlanmasına bulun. İle tüm dış araçları ToolCmd ayarı "Not", şu şekilde olup olmadığını belirlemek için yineleme yapmanız gerekir:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already an External Tool.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
    }  
  
    ```  
  
5.  Not Defteri'ni dış bir araç olarak ayarlanmamışsa, aşağıdaki gibi ayarlayın:  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already installed.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
  
        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";  
         if (!hasNotepad)  
        {  
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");  
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");  
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");  
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");  
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");  
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);  
  
            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);  
        }  
    }  
    ```  
  
6.  Kodu test edin. İkinci kez çalıştırmadan önce kayıt defterini geri alma işlemleri gerekir böylece onu dış bir araç olarak not defteri ekler unutmayın.  
  
7.  Kodu derlemek ve hata ayıklamaya başlayın.  
  
8.  Üzerinde **Araçları** menüsünde tıklatın **çağırma UserSettingsStoreCommand**. Bu Not Defteri'ne ekler **Araçları** menüsü.  
  
9. Not Defteri'ni araçları görürsünüz / Seçenekler menüsü ve tıklayarak **not defteri** bir not defteri örneği ayarlama duruma getirmeniz gerekir.

