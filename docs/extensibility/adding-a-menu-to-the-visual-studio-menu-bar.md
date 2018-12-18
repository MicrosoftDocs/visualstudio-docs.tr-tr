---
title: Visual Studio menü çubuğuna menü ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 42c1a9cd2d1c9d1349b07e06d65a8da6a41b4245
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938233"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Visual Studio menü çubuğuna menü ekleme
Bu izlenecek yol, Visual Studio tümleşik geliştirme ortamı (IDE) menü çubuğuna menü ekleme işlemi gösterilmektedir. Menü kategorileri gibi IDE menü çubuğu içeren **dosya**, **Düzenle**, **görünümü**, **penceresi**, ve **yardımcı** .  
  
 Visual Studio menü çubuğunda yeni menü eklemeden önce komutlarınızı içinde varolan bir menüye yerleştirilmiş olup olmadığını göz önünde bulundurun. Komut yerleşimi hakkında daha fazla bilgi için bkz: [menüler ve komutlar için Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 Menüler içinde bildirilen *.vsct* proje dosyası. Menüler hakkında daha fazla bilgi ve *.vsct* dosyaları görmek [komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Bu izlenecek yolu tamamlayarak adlı bir menü oluşturabilirsiniz **TestMenu** , bir komut içerir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Bir özel komut öğesi şablona sahip bir VSIX projesi oluşturun  
  
1.  Adlı bir VSIX projesi oluşturun `TopLevelMenu`. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C#** / **genişletilebilirlik**.  Daha fazla bilgi için [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Projeyi açtığında, adlı bir özel komut öğesi şablonu ekleme **TestCommand**. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. İçinde **Yeni Öğe Ekle** iletişim kutusunda, Git **Visual C# / genişletilebilirlik** seçip **özel komut**. İçinde **adı** alan penceresinin en altında komut dosyası adı için değiştirme *TestCommand.cs*.  
  
## <a name="create-a-menu-on-the-ide-menu-bar"></a>IDE menü çubuğunda bir menü oluşturma  
  
1. İçinde **Çözüm Gezgini**açın *TestCommandPackage.vsct*.  
  
    Dosyanın sonunda, var olan bir \<sembolleri > içeren birkaç düğüm \<GuidSymbol > düğümleri. GuidTestCommandPackageCmdSet adlı düğümünde, yeni bir sembol, aşağıdaki şekilde ekleyin:  
  
   ```xml  
   <IDSymbol name="TopLevelMenu" value="0x1021"/>  
   ```  
  
2. Boş bir oluşturma \<menüleri > düğümünde \<komutları > düğümü hemen önce \<Gruplar >. İçinde \<menüleri > düğümü Ekle bir \<menüsü > düğümü, aşağıdaki gibi:  
  
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
  
3. İçinde \<grupları > bölümünde, bulma \<grubu > değiştirip \<üst > öğesini eklediğimiz yöntemlerin menüsünde:  
  
   ```csharp  
   <Groups>  
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
         </Group>  
       </Groups>  
   ```  
  
    Bu yeni menü grubunun parçası yapar.  
  
4. Bulma `Buttons` bölümü. Dikkat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paket Şablonu oluşturulan bir `Button` üst kümesine sahip öğe `MyMenuGroup`. Sonuç olarak, bu komut menünüzde görünür.  
  
## <a name="build-and-test-the-extension"></a>Uzantıyı test etmek ve derleme  
  
1.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Bir örneği deneysel örneğinde görüntülenmesi gerekir.  
  
2.  Deneysel örneğinin menü çubuğunda içermesi gereken bir **TestMenu** menüsü.  
  
3.  Üzerinde **TestMenu** menüsünde tıklatın **Test komutu çağırmak**.  
  
     Bir ileti kutusu, görünür ve "TopLevelMenu.TestCommand.MenuItemCallback() içinde TestCommand paket" iletisini görüntüler. Bu, yeni bir komut çalıştığını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)