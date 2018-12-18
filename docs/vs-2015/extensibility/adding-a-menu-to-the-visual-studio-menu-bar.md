---
title: Menü çubuğuna menü ekleme | Microsoft Docs
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
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 440bd2c8c7e1505b8d729274a06440d596690773
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065888"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Visual Studio Menü Çubuğuna Menü Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, Visual Studio tümleşik geliştirme ortamı (IDE) menü çubuğuna menü ekleme işlemi gösterilmektedir. Menü kategorileri gibi IDE menü çubuğu içeren **dosya**, **Düzenle**, **görünümü**, **penceresi**, ve **yardımcı** .

 Visual Studio menü çubuğunda yeni menü eklemeden önce komutlarınızı içinde varolan bir menüye yerleştirilmiş olup olmadığını göz önünde bulundurun. Komut yerleşimi hakkında daha fazla bilgi için bkz: [menüler ve komutlar için Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Menüleri projenin .vsct dosyasında bildirilir. Menüler ve .vsct dosyaları hakkında daha fazla bilgi için bkz: [komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).

 Bu izlenecek yolu tamamlayarak adlı bir menü oluşturabilirsiniz **TestMenu** , bir komut içerir.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Özel komut öğe şablonu bir VSIX projesi oluşturma

1.  Adlı bir VSIX projesi oluşturun `TopLevelMenu`. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C#** / **genişletilebilirlik**.  Daha fazla bilgi için [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

2.  Projeyi açtığında, adlı bir özel komut öğesi şablonu ekleme **TestCommand**. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. İçinde **Yeni Öğe Ekle** iletişim kutusunda, Git **Visual C# / genişletilebilirlik** seçip **özel komut**. İçinde **adı** alan penceresinin en altında komut dosyası adı için değiştirme **TestCommand.cs**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>IDE menü çubuğuna menü oluşturma

#### <a name="to-create-a-menu"></a>Bir menü oluşturmak için

1.  İçinde **Çözüm Gezgini**, TestCommandPackage.vsct açın.

     Dosyanın sonunda, var olan bir \<sembolleri > içeren birkaç düğüm \<GuidSymbol > düğümleri. GuidTestCommandPackageCmdSet adlı düğümünde, yeni bir sembol, aşağıdaki şekilde ekleyin:

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2.  Boş bir oluşturma \<menüleri > düğümünde \<komutları > düğümü hemen önce \<Gruplar >. İçinde \<menüleri > düğümü Ekle bir \<menüsü > düğümü, aşağıdaki gibi:

    ```xml
    <Menus>
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
            <Parent guid="guidSHLMainMenu"
                    id="IDG_VS_MM_TOOLSADDINS" />
            <Strings>
              <ButtonText>TestMenu</ButtonText>
              <CommandName>TestMenu</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     `guid` Ve `id` menü değerlerini komut kümesi ve belirli menü komut kümesinde belirtin.

     `guid` Ve `id` değerler üst menü Araçlar ve eklentiler menüleri içeren Visual Studio menü çubuğunun bölümüne getirin.

     Değerini `CommandName` dize menü öğesi metni görüntüleneceğini belirtir.

3.  İçinde \<grupları > bölümünde, bulma \<grubu > değiştirip \<üst > öğesini eklediğimiz yöntemlerin menüsünde:

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     Bu yeni menü grubunun parçası yapar.

4.  Bulma `Buttons` bölümü. Dikkat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paket Şablonu oluşturulan bir `Button` üst kümesine sahip öğe `MyMenuGroup`. Sonuç olarak, bu komut menünüzde görünür.

## <a name="building-and-testing-the-extension"></a>Oluşturma ve uzantıyı test etme

1.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Bir örneği deneysel örneğinde görüntülenmesi gerekir.

2.  Deneysel örneğinin menü çubuğunda içermesi gereken bir **TestMenu** menüsü.

3.  Üzerinde **TestMenu** menüsünde tıklatın **Test komutu çağırmak**.

     Bir ileti kutusu, görünür ve "TopLevelMenu.TestCommand.MenuItemCallback() içinde TestCommand paket" iletisini görüntüler. Bu, yeni bir komut çalıştığını gösterir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Komutlar, Menüler ve Araç Çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
