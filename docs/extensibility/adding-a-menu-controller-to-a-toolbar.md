---
title: Bir araç çubuğuna menü denetleyicisi ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 93bf6af51488b5609f24c5664dee040ea086c26c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867268"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Araç çubuğuna menü denetleyicisi ekleme
Bu izlenecek yolda yapılar [araç penceresine araç çubuğu eklemek](../extensibility/adding-a-toolbar-to-a-tool-window.md) gözden geçirme ve araç penceresi araç çubuğuna menü denetleyicisi ekleme işlemi gösterilmektedir. Burada gösterilen adımları da oluşturulan araç uygulanabilir [araç ekleme](../extensibility/adding-a-toolbar.md) gözden geçirme.  
  
 Menü denetleyicisi bölünmüş bir denetimdir. Son kullanılan komut menü denetleyicisi sol tarafındaki gösterir ve tıklayarak çalıştırabilirsiniz. Sağındaki menü denetleyicisi olan bir ok, tıklandığında, ek komutlar listesi açılır. Ne zaman bir komut listesindeki komut çalıştırmaları'a tıklayın ve sol tarafındaki menü denetleyicisi komut değiştirir. Bu şekilde, menü denetleyicisi her zaman son kullanılan komut listesini gösteren bir komut düğmesi gibi çalışır.  
  
 Menü denetleyicisi menülerde görünebilir, ancak çoğunlukla bir araç çubuklarında kullanılan.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-menu-controller"></a>Menü denetleyicisi oluşturma  
  
1. Açıklanan yordamları izleyin [araç penceresine araç çubuğu eklemek](../extensibility/adding-a-toolbar-to-a-tool-window.md) araç çubuğu içeren bir araç penceresi oluşturmak için.  
  
2. İçinde *TWTestCommandPackage.vsct*sembolleri bölümüne gidin. Adlı GuidSymbol öğesi içinde **guidTWTestCommandPackageCmdSet**, menü denetleyiciniz, menü denetleyicisi grubu ve üç menü öğelerini bildirin.  
  
   ```xml  
   <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
   ```  
  
3. Menüler bölümünde son menü girişten sonra menü denetleyicisi menü olarak tanımlayın.  
  
   ```xml  
   <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <CommandFlag>TextChanges</CommandFlag>  
       <CommandFlag>TextIsAnchorCommand</CommandFlag>  
       <Strings>  
           <ButtonText>Test Menu Controller</ButtonText>  
           <CommandName>Test Menu Controller</CommandName>  
       </Strings>  
   </Menu>  
   ```  
  
    `TextChanges` Ve `TextIsAnchorCommand` bayrakları son seçilen komut yansıtacak şekilde menü denetleyicisi etkinleştirmek için dahil edilen olmalıdır.  
  
4. Gruplarda bölümü, son grup girişten sonra menü denetleyicisi grubu ekleyin.  
  
   ```xml  
   <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
   </Group>  
   ```  
  
    Bu grupta herhangi bir komut üst menü denetleyicisi ayarlayarak menü denetleyicisi görünür. `priority` Özniteliği belirtilmemişse, varsayılan değeri 0 olarak ayarlar, yalnızca grup menü denetleyicisi üzerinde olduğundan.  
  
5. Düğmeler bölümünde son düğme girişten sonra düğme öğesi her, menü öğelerinin ekleyin.  
  
   ```xml  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPic1" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 1</ButtonText>  
           <CommandName>MC Item 1</CommandName>  
       </Strings>  
   </Button>  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPic2" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 2</ButtonText>  
           <CommandName>MC Item 2</CommandName>  
       </Strings>  
   </Button>  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPicSearch" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 3</ButtonText>  
           <CommandName>MC Item 3</CommandName>  
       </Strings>  
   </Button>  
   ```  
  
6. Bu noktada, menü denetleyicisinde bakabilirsiniz. Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği görmeniz gerekir.  
  
   1. Üzerinde **görünüm / diğer Windows** menüsünde, açık **Test ToolWindow**.  
  
   2. Menü denetleyicisi araç penceresindeki araç çubuğunda görünür.  
  
   3. Üç olası komutları görmek için menü denetleyicisi sağ tarafındaki oka tıklayın.  
  
      Bir komutu tıklattığınızda, menü denetleyicisi başlığının komut görüntülenecek değiştiğine dikkat edin. Sonraki bölümde, bu komutları etkinleştirmek için kod ekleyeceğiz.  
  
## <a name="implement-the-menu-controller-commands"></a>Menü denetleyicisi komutları uygulama  
  
1.  İçinde *TWTestCommandPackageGuids.cs*, komut kimlikleri, üç menü öğeleri için var olan komut kimlikleri sonra ekleyin.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  İçinde *TWTestCommand.cs*, üstüne aşağıdaki kodu ekleyin `TWTestCommand` sınıfı.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  Son çağrısından sonra TWTestCommand Oluşturucuda `AddCommand` yöntemi, aynı işleyicileri aracılığıyla her komut için olayları yönlendirmek için kod ekleyin.  
  
    ```csharp  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  Bir olay işleyici ekleme **TWTestCommand** seçili komut işaretli olarak işaretlemek için sınıf.  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Kullanıcı menü denetleyicisi komutu seçtiğinde bir MessageBox görüntüler bir olayı işleyicisi ekleyin:  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## <a name="testing-the-menu-controller"></a>Menü denetleyicisi test etme  
  
1.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği görmeniz gerekir.  
  
2.  Açık **Test ToolWindow** üzerinde **görünüm / diğer Windows** menüsü.  
  
     Menü denetleyicisi araç penceresindeki araç çubuğunda görünür ve görüntüler **MC madde 1**.  
  
3.  Sol Ok menü denetleyicisi düğmesine tıklayın.  
  
     İlki seçilir ve simgesini geçici olarak bir Vurgu kutusu olan üç öğe görmeniz gerekir. Tıklayın **MC madde 3**.  
  
     İletinin bir iletişim kutusu görünür **menü denetleyicisi madde 3 seçtiğiniz**. İleti metni menü denetleyicisi düğmesinde karşılık dikkat edin. Menü denetleyicisi düğmesi artık görüntüler **MC madde 3**.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Araç penceresine araç çubuğu ekleme](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Araç çubuğu ekleme](../extensibility/adding-a-toolbar.md)