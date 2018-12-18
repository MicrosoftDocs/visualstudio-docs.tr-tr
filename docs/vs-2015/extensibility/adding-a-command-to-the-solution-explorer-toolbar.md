---
title: Çözüm Gezgini araç çubuğuna komut ekleme | Microsoft Docs
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
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 40
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 52e963a202d75c29c65521729e70e062a579d479
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753639"
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Çözüm Gezgini Araç Çubuğuna Komut Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bir düğme ekleme işlemi açıklanır **Çözüm Gezgini** araç çubuğu.  
  
 Herhangi bir araç çubuğunu veya menüyü komutunda Visual Studio'da bir düğme olarak adlandırılır. Düğme tıklandığında komut işleyici kod yürütülür. Genellikle, ilgili komutları bir grup oluşturmak için birlikte gruplandırılır. Menüleri ve araç çubukları grupları için kapsayıcı işlevi görür. Öncelik grubundaki tek tek komutlarla menü veya araç çubuğunda görüntülenme sırasını belirler. Bir düğme araç çubuğunu veya menüyü görünürlüğünü denetleme tarafından görüntülenmesini engelleyebilirsiniz. Listelenen bir komutu bir `<VisibilityConstraints>` .vsct dosyası bölümünü yalnızca ilişkili bağlam içinde görünür. Gruplara görünürlük uygulanamaz.  
  
 Menüleri ve araç çubuğu komutlarını .vsct dosyaları hakkında daha fazla bilgi için bkz: [komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  XML komut tablosu (.vsct) dosyaları, menüler ve komutlar, Vspackage'larda nasıl görüneceğini tanımlamak için komut tablosu (.ctc) yapılandırma dosyaları yerine kullanın. Daha fazla bilgi için [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Bir Menü Komutuyla Uzantı Oluşturma  
 Adlı bir VSIX projesi oluşturun `SolutionToolbar`. Adlı bir menü komutu öğesi şablonu ekleme **ToolbarButton**. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Çözüm Gezgini araç çubuğuna bir düğme ekleme  
 Kılavuzun bu bölümünde, bir düğmeye ekleme işlemi açıklanır **Çözüm Gezgini** araç çubuğu. Düğmeye tıklandığında geri çağırma yöntemi kod çalıştırılır.  
  
1.  ToolbarButtonPackage.vsct dosyasında Git `<Symbols>` bölümü. `<GuidSymbol>` Paketi şablonu tarafından oluşturulan komut ve menü grubu düğüm içeriyor. Ekleme bir `<IDSymbol>` komutunuz tutacak bir grup bildirmek için bu düğümü öğesi.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  İçinde `<Groups>` bölümünde, mevcut Grup girişten sonra tanımlayın, bildirilen yeni grubu önceki adımda.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Üst GUID:ID çifti ayarını `guidSHLMainMenu` ve `IDM_VS_TOOL_PROJWIN` bu Grup koyar **Çözüm Gezgini** araç çubuğu ve yüksek öncelikli değeri onu koyar sonra diğer komut grupları.  
  
3.  İçinde `<Buttons>` bölümünde, oluşturulan üst Kimliğini değiştirme `<Button>` önceki adımda tanımladığınız grubunu yansıtacak şekilde girişi. Değiştirilmiş `<Button>` öğesi şu şekilde görünmelidir:  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
     **Çözüm Gezgini** mevcut düğmeleri sağındaki araç yeni komut düğmesi görüntülemelidir. Strikethrough düğmesi simgesi bulunuyor.  
  
5.  Yeni düğmesine tıklayın.  
  
     İletiyi içeren bir iletişim kutusu **ToolbarButtonPackage içinde SolutionToolbar.ToolbarButton.MenuItemCallback()** görüntülenmesi gerekir.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Bir düğmesinin görünürlüğünü denetleme  
 Kılavuzun bu bölümünde, bir araç çubuğu üzerindeki bir düğme görünürlüğünü denetleme işlemi gösterilmektedir. İçinde bir veya daha fazla proje için bir bağlam ayarlayarak `<VisibilityConstraints>` bölümü SolutionToolbar.vsct dosyasının yalnızca bir projede veya projelerde açık olduğunda görüntülenecek bir düğme kısıtlayın.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Bir veya daha fazla proje açıkken bir düğme görüntülemek için  
  
1. İçinde `<Buttons>` bölümü ToolbarButtonPackage.vsct varolan iki komut bayrakları ekleme `<Button>` öğesi, arasında `<Strings>` ve `<Icons>` etiketler.  
  
   ```xml  
   <CommandFlag>DefaultInvisible</CommandFlag>  
   <CommandFlag>DynamicVisibility</CommandFlag>  
   ```  
  
    `DefaultInvisible` Ve `DynamicVisibility` bayrakları bunu ayarlanmalıdır Bu girdiler `<VisibilityConstraints>` bölüm etkisi alabilir.  
  
2. Oluşturma bir `<VisibilityConstraints>` iki bölüm `<VisibilityItem>` girdileri. Yeni bir bölüm kapattıktan sonra put `</Commands>` etiketi.  
  
   ```xml  
   <VisibilityConstraints>  
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
             id="ToolbarButtonId"  
             context="UICONTEXT_SolutionHasSingleProject" />  
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
             id="ToolbarButtonId"  
             context="UICONTEXT_SolutionHasMultipleProjects" />  
   </VisibilityConstraints>  
   ```  
  
    Her görünürlük öğesi, belirtilen düğmenin görüntülendiği bir koşulunu temsil eder. Birden çok koşul uygulamak için aynı düğme için birden çok girişi oluşturmanız gerekir.  
  
3. Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
    **Çözüm Gezgini** araç üstü çizili düğmesini içermiyor.  
  
4. Bir proje içeren herhangi bir çözümü açın.  
  
    Strikethrough düğmesi, varolan düğmeleri sağındaki araç çubuğunda görünür.  
  
5. Üzerinde **dosya** menüsünü tıklatın **çözümü Kapat**. Düğme araç çubuğundan kaybolur.  
  
   Düğmesinin görünürlüğünü tarafından denetlenir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSPackage yüklenene kadar. VSPackage'ı yüklendikten sonra düğmesinin görünürlüğünü VSPackage'ı tarafından denetlenir.  Daha fazla bilgi için [MenuCommands Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komutlar, Menüler ve Araç Çubukları](../extensibility/internals/commands-menus-and-toolbars.md)

