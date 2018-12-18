---
title: Araç çubuğu ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a2888ab6fade4893389af23ff456a63ffc5fbc40
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151996"
---
# <a name="add-a-toolbar"></a>Araç çubuğu ekleme
Bu izlenecek yol, araç Visual Studio IDE ekleme işlemi gösterilmektedir.  
  
 Bir araç çubuğu komutları bağlanan bir düğme içeren bir yatay veya dikey çubuk bulunur. Uygulaması bağlı olarak, IDE içindeki araç yeniden konumlandırıldığında, ana IDE penceresi tarafında yerleştirilebilir ya da diğer pencerelerin önünde kalmak için yapılan.  
  
 Kullanıcılar ayrıca, araç çubuğuna komut ekleme veya bunları kullanarak kaldırabilirsiniz **Özelleştir** iletişim kutusu. Genellikle, araç çubukları vspackage'lardaki kullanıcı tarafından özelleştirilebilir. IDE, tüm özelleştirme işler ve VSPackage komutlarına yanıt verir. VSPackage'ı, bir komut fiziksel olarak bulunduğu yeri bilmek yok.  
  
 Menüler hakkında daha fazla bilgi için bkz: [komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-toolbar"></a>Araç çubuğu ile bir uzantı oluşturma  
 Adlı bir VSIX projesi oluşturun `IDEToolbar`. Adlı bir menü komutu öğesi şablonu ekleme **ToolbarTestCommand**. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="create-a-toolbar-for-the-ide"></a>IDE için bir araç çubuğu oluştur  
  
1.  İçinde *ToolbarTestCommandPackage.vsct*, semboller bölümüne bakın. GuidToolbarTestCommandPackageCmdSet adlı GuidSymbol öğesi içinde bildirimler için bir araç çubuğu ve araç çubuğu grubu, aşağıdaki şekilde ekleyin.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  Komutları bölümünün üstünde bir menü bölümü oluşturun. Bir menü öğesi menülerini bölümüne araç tanımlamak için ekleyin.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     Araç Çubukları alt menüler gibi iç içe olamaz. Bu nedenle, bir üst grup atama gerekmez. Ayrıca, kullanıcı araç çubukları taşıyabilirsiniz çünkü bir öncelikler gerekmez. Genellikle, ilk araç çubuğu yerleşimini programlı olarak tanımlanır, ancak kullanıcı tarafından sonraki değişiklikleri kalıcı.  
  
3.  İçinde [grupları](../extensibility/groups-element.md) bölümünde, mevcut Grup girişten sonra tanımlayan bir [grubu](../extensibility/group-element.md) araç için komutları içeren öğe.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  Araç çubuğunda görünen bir düğme olun. Düğmeler bölümünde, üst bloğu düğmenin araç değiştirin. Sonuçta elde edilen düğmesi bloğu gibi görünmelidir:  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Araç çubuğu hiçbir komut varsa, varsayılan olarak, bu görünmüyor.  
  
5.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği görüntülenmesi gerekir.  
  
6.  Araç çubukları listesini almak için Visual Studio menü çubuğunun sağ tıklayın. Seçin **Test araç**.  
  
7.  Şimdi, simge dosyaları simge Bul sağındaki araç görmeniz gerekir. Simgeye tıkladığında bildiren bir ileti kutusu görmeniz gerekir **ToolbarTestCommandPackage. İçinde IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)