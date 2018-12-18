---
title: Bir komutun görünümünü değiştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61ba39bc8a312fb06499bed7ca94e33dc5e7153e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825997"
---
# <a name="change-the-appearance-of-a-command"></a>Bir komutun görünümünü değiştirme
Bir komutun görünümünü değiştirmek için kullanıcı geri bildirim sağlayabilirsiniz. Örneğin, kullanılabilir olmadığında farklı aramak için bir komut isteyebilirsiniz. Komutları kullanılabilir veya kullanılamaz hale, gizleme veya bunları gösterebilir veya denetleyin veya menüde seçeneğinin işaretini kaldırın.  
  
 Bir komutun görünümünü değiştirmek için aşağıdaki eylemlerden birini gerçekleştirin:  
  
- Uygun bayrakları komut tablosu dosyasındaki komut tanımı belirtin.  
  
- Kullanım <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> hizmeti.  
  
- Uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirim ve ham komut nesneleri değiştirebilirsiniz.  
  
  Aşağıdaki adımlarda, bulmak ve yönetilen paket Framework (MPF) kullanarak bir komutun görünümünü güncelleştirmek gösterilmektedir.  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Bir menü komutu görünümünü değiştirmek için  
  
1.  Bölümündeki yönergeleri [menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md) adlı menü öğesi oluşturmak için `New Text`.  
  
2.  İçinde *ChangeMenuText.cs* dosyasında, aşağıdaki using deyimi:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  İçinde *ChangeMenuTextPackageGuids.cs* dosyasında, aşağıdaki satırı ekleyin:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  İçinde *ChangeMenuText.cs* dosya, ShowMessageBox yöntemindeki kodu aşağıdakiyle değiştirin:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);
    }  
    ```  
  
5.  Güncelleştir istediğiniz komut elde <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> nesnesi ve ardından uygun özellikleri komut nesnesi üzerinde ayarlayın. Örneğin, aşağıdaki yöntemi bir VSPackage komut belirtilen komuttan kullanılabilir veya kullanılamaz hale getirir. Aşağıdaki kod öğesi adlı menü yapar `New Text` bunu tıklatıldıktan sonra kullanılamaz.  
  
    ```csharp  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;
    }  
    ```  
  
6.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneğinde görüntülenmesi gerekir.  
  
7.  Üzerinde **Araçları** menüsünde tıklatın **çağırma ChangeMenuText** komutu. Bu noktada komut addır **çağırma ChangeMenuText**, komut işleyicisi çağırma değil **ChangeMyCommand()**.  
  
8.  Üzerinde **Araçları** artık görmeniz menü **yeni metin**. Tıklayın **yeni metin**. Komutu şimdi gri.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)   
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Menüleri ve komutlari genişletme komutları](../extensibility/extending-menus-and-commands.md)   
 [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
