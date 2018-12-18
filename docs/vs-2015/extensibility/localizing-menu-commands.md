---
title: Menü komutlarını yerelleştirme | Microsoft Docs
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
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b16771e4d47416f09774ce2f4765de9d6023e94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753888"
---
# <a name="localizing-menu-commands"></a>Menü Komutlarını Yerelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Menüsü yerelleştirilmiş metin sağlayabilir ve araç çubuğu yerelleştirilmiş .vsct dosyaları oluşturarak komutları ve .resx dosyaları, VSPackage'ı ve ardından Proje dosyalarını güncelleştirmek için değişiklikleri birleştirmek yerelleştirilmiş.  
  
 Bir yükleme deneyimi yerelleştirmek hakkında daha fazla bilgi için bkz. [VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Komut adlarını yerelleştirme  
 Vspackage'larda, menü komutlarını ve araç çubuğu düğmeleri .vsct dosyası içinde tanımlanır.  
  
1. İçinde **Çözüm Gezgini**, .vsct dosyanın adını değiştirmek *filename*için .vsct *filename*.en-US.vsct.  
  
2. Bir kopyasını *filename*.en-US.vsct her bir yerelleştirme dili.  
  
    Her kopya adı *filename*. *Yerel ayar*.vsct, burada *yerel ayar* belirli bir kültür adı. Kültür adı değerleri listesi için bkz. [Microsoft tarafından atanan yerel kimlikler](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Bunlar *filename*. *Yerel ayar*.vsct dosyaları paketiniz için yerelleştirilmiş menü metni içerir.  
  
3. Her açın *filename*. *Yerel ayar*metin yerelleştirmek için .vsct dosyası.  
  
   1. Değiştirme [ButtonText](../extensibility/buttontext-element.md) öğe belirli bir dili için uygun değerleri.  
  
   2. Yerelleştirilmiş simgeler sağlayacaksa değiştirme [bit eşlem](../extensibility/bitmap-element.md) hedef dosyalarının olduğu noktaya değerleri.  
  
      Aşağıdaki örnek, bir Aile ağacı Gezgini araç penceresi açmak bir komut için İngilizce ve İspanyolca düğme metni gösterir.  
  
      [US.vsct FamilyTree.en]  
  
   ```xml  
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <Icon guid="guidImages" id="bmpPic2" />  
     <Strings>  
       <CommandName>cmdidFamilyTree</CommandName>  
       <ButtonText>Family Tree Explorer</ButtonText>  
     </Strings>  
   </Button>  
   ```  
  
    [ES.vsct FamilyTree.es]  
  
   ```xml  
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <Icon guid="guidImages" id="bmpPic2" />  
     <Strings>  
       <CommandName>cmdidFamilyTree</CommandName>  
       <ButtonText>Explorar el arbol genealogico</ButtonText>  
     </Strings>  
   </Button>  
  
   ```  
  
## <a name="localizing-other-text-resources"></a>Diğer metin kaynakları yerelleştirme  
 Komut adlarını dışında metin kaynaklar kaynak (.resx) dosyalarını tanımlanır.  
  
1.  VSPackage.resx VSPackage.en-US.resx yeniden adlandırın.  
  
2.  Yerelleştirilmiş her dille VSPackage.en-US.resx dosyanın bir kopyasını oluşturun.  
  
     VSPackage'ı her kopya adı. *Yerel*.resx, burada *yerel ayar* belirli bir kültür adı.  
  
3.  Resources.resx Resources.en-US.resx yeniden adlandırın.  
  
4.  Yerelleştirilmiş her dille Resources.en-US.resx dosyanın bir kopyasını oluşturun.  
  
     Her kopya kaynak adı. *Yerel*.resx, burada *yerel ayar* belirli bir kültür adı.  
  
5.  Dize değerleri belirli dil ve kültür için uygun şekilde değiştirmek için her bir .resx dosyasını açın. Aşağıdaki örnek, bir araç penceresinin başlık çubuğu için yerelleştirilmiş kaynak tanımı gösterilmektedir.  
  
     [Resources.en-US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [ES.resx Resources.es]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Yerelleştirilmiş kaynaklar projeye ekleme  
 AssemblyInfo.cs dosyası ve yerelleştirilmiş kaynakları eklemek için proje dosyasını değiştirmeniz gerekir.  
  
1.  Gelen **özellikleri** düğümünde **Çözüm Gezgini**, AssemblyInfo.cs veya AssemblyInfo.vb Düzenleyicisi'nde açın.  
  
2.  Şu girişi ekleyin.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Bu ABD İngilizcesi varsayılan dili ayarlar.  
  
3.  Projeyi kaldırmak.  
  
4.  Proje Dosyası Düzenleyicisi'nde açın.  
  
5.  Bulun `ItemGroup` öğesini içeren `EmbeddedResource` öğeleri.  
  
6.  İçinde `EmbeddedResource` VSPackage.en-US.resx çağıran öğeyi değiştirin `ManifestResourceName` öğesi ile bir `LogicalName` kümesine öğesini `VSPackage.en-US.Resources`aşağıdaki gibi.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Yerelleştirilen her dil için kopyalama `EmbeddedResource` öğesi VsPackage.en ABD ve küme için **INCLUDE** özniteliği ve **LogicalName** aşağıda gösterildiği gibi hedef yerel kopyasının öğesi örnek.  
  
8.  Her yerelleştirilmiş `VSCTCompile` öğe, Ekle bir `ResourceName` işaret öğesi `Menus.ctmenu`, aşağıdaki örnekte gösterildiği gibi.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Proje dosyasını kaydedin ve projeyi yeniden yükleyin.  
  
10. Projeyi oluşturun.  
  
     Bu, bir ana derlemeye yanı sıra, her dil için kaynak grupları oluşturur. Dağıtım işlemi yerelleştirme hakkında daha fazla bilgi için bkz: [VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Menüleri ve komutlari genişletme komutları](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Genelleştirme ve Yerelleştirme](http://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)

