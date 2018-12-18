---
title: Bir en son kullanılan bir alt listeye ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d140fed32ac3816b75e13496dc3507fc728f7d26
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916536"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Bir en son kullanılan bir alt menüye listesi Ekle
Bu izlenecek yol tanıtımlar geliştirir [menüye alt menü ekleme](../extensibility/adding-a-submenu-to-a-menu.md)ve dinamik bir listesi için bir alt menü ekleme işlemi gösterilmektedir. Dinamik listesi en son kullanılanlar (MRU) listesini oluşturmak için temelini oluşturur.  
  
 Dinamik menü listesi menüsünde yer tutucu ile başlar. Menü gösterilen her zaman Visual Studio tümleşik geliştirme ortamı (IDE) yer tutucuyu gösterilen tüm komutlar için VSPackage ister. Dinamik bir listesi, herhangi bir yere menüde ortaya çıkabilir. Ancak, dinamik listeler genellikle tutulur ve başlarına alt menüler ya da menü altlarındaki görüntülenir. Bu tasarım desenleri kullanarak dinamik genişletin ve diğer komutlar menüsünde konumunu etkilemeden sözleşme komutların listesini sağlar. Bu izlenecek yolda, alt geri kalanından satırla ayrılan, var olan bir alt kısmındaki dinamik MRU listesi görüntülenir.  
  
 Teknik olarak, dinamik bir listesi için bir araç çubuğu uygulanabilir. Ancak, kullanıcı değiştirmek için belirli adımlar sürece bir araç çubuğu değişmeden kalmalıdır, çünkü Biz bu kullanım önerilmemektedir.  
  
 Bu izlenecek yol, bir tanesi seçili her zaman sırayı değiştirmek dört öğelerin bir MRU listesi oluşturur (Seçili öğe listesinin üstüne taşınır).  
  
 Menüler hakkında daha fazla bilgi ve *.vsct* dosyaları görmek [komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="create-an-extension"></a>Bir uzantı oluşturma  
  
- Konusundaki yordamları izleyin [menüye alt menü ekleme](../extensibility/adding-a-submenu-to-a-menu.md) değiştirilen alt aşağıdaki yordamlarda oluşturmak için.  
  
  Bu kılavuzdaki yordamları VSPackage'ı adı olduğunu varsayın `TopLevelMenu`, kullanılan adı [Visual Studio menü çubuğuna menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="create-a-dynamic-item-list-command"></a>Bir dinamik öğe listesi komutu oluştur  
  
1.  Açık *TestCommandPackage.vsct*.  
  
2.  İçinde `Symbols` bölümünde `GuidSymbol` guidTestCommandPackageCmdSet, adlı düğüm eklemek için Sembol `MRUListGroup` grubu ve `cmdidMRUList` gibi komutu.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  İçinde `Groups` bölümünde, mevcut grup girdilerini sonra bildirilen gruba ekleyin.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  İçinde `Buttons` bölümünde, mevcut düğmesi girişleri sonra yeni bildirilen komutu temsil etmek için bir düğüm ekleyin.  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     `DynamicItemStart` Bayrağı dinamik olarak oluşturulması için komutu sağlar.  
  
5.  Projeyi oluşturmak ve yeni komutu test etmek için hata ayıklama başlatılamıyor.  
  
     Üzerinde **TestMenu** menü, yeni alt tıklayın **alt menü**, yeni komut görüntülenecek **MRU yer tutucu**. Sonraki yordamda komutları dinamik MRU Listesi uygulandıktan sonra bu komut etiketi alt açıldığında her zaman bu listeyi değiştirilecek.  
  
## <a name="filling-the-mru-list"></a>MRU Listesi doldurma  
  
1.  İçinde *TestCommandPackageGuids.cs*, mevcut komut kimlikleri sonra aşağıdaki satırları ekleyin `TestCommandPackageGuids` sınıf tanımını.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  İçinde *TestCommand.cs* aşağıdaki using deyimi.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  Aşağıdaki kodu TestCommand oluşturucuda son AddCommand çağrısından sonra ekleyin. `InitMRUMenu` Daha sonra tanımlanır  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  TestCommand sınıfında aşağıdaki kodu ekleyin. Bu kod MRU listesinde gösterilecek öğeler temsil eden dizeleri listesini başlatır.  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  Sonra `InitializeMRUList` yöntemi ekleme `InitMRUMenu` yöntemi. Bu, MRU Listesi menü komutları başlatır.  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     MRU listesindeki olası her öğe için bir menü komutu nesnesi oluşturmanız gerekir. IDE çağrıları `OnMRUQueryStatus` kalmayana kadar daha fazla öğe MRU listesindeki her bir öğe için yöntemi. Yönetilen kodda, daha fazla öğe olduğunu bilmek IDE için tek yolu tüm olası öğeleri ilk oluşturmaktır. İsterseniz, ek öğeleri görünür olarak ilk kullanarak işaretleyebilirsiniz `mc.Visible = false;` menü komutunu oluşturulduktan sonra. Bu öğeleri ardından daha sonra kullanarak görünür hale getirilebilir `mc.Visible = true;` içinde `OnMRUQueryStatus` yöntemi.  
  
6.  Sonra `InitMRUMenu` yöntemi, aşağıdaki `OnMRUQueryStatus` yöntemi. Metnin her MRU öğe için ayarlar işleyicisidir.  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  Sonra `OnMRUQueryStatus` yöntemi, aşağıdaki `OnMRUExec` yöntemi. MRU öğe seçmek için işleyici budur. Bu yöntem, seçili öğe listesinin en üstüne taşır ve ardından seçilen öğe bir ileti kutusunda görüntüler.  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>MRU Listesi test etme  
  
1.  Projeyi oluşturmak ve hata ayıklamaya başlayın.
  
2.  Üzerinde **TestMenu** menüsünde tıklatın **çağırma TestCommand**. Bunun yapılması, komut seçilmiş olduğunu belirten bir ileti kutusu görüntüler.  
  
    > [!NOTE]
    >  VSPackage'ı yüklemek ve doğru şekilde MRU listesi görüntülemek için zorlamak için bu adım gereklidir. Bu adımı atlarsanız MRU listesi görüntülenmez.  
  
3.  Üzerinde **Test menüsü** menüsünde tıklatın **alt menü**. Dört öğe listesini bir ayırıcı aşağıdaki alt sonunda görüntülenir. Tıkladığınızda **madde 3**, bir ileti kutusu görünür ve metnini **seçili öğe 3**. (Dört öğe listesini görüntülenmiyorsa, önceki adımda'ndaki yönergeleri izlediğinizden emin olun.)  
  
4.  Alt yeniden açın. Dikkat **madde 3** listenin en üstünde sunulmuştur ve diğer öğeler bir konum aşağı gönderildi. Tıklayın **madde 3** yeniden ve hala ileti kutusunda görüntüler bildirimi **seçili öğe 3**, metin komut etiketi ile birlikte yeni bir konuma doğru bir şekilde taşındığını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Dinamik olarak menü öğeleri ekleme](../extensibility/dynamically-adding-menu-items.md)