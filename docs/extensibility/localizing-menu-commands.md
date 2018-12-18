---
title: Menü komutlarını yerelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c8eb9e566f4f5916961a95a1c61f8fdcbb689f1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876223"
---
# <a name="localize-menu-commands"></a>Menü komutlarını yerelleştirme
Yerelleştirilmiş oluşturarak menü ve araç çubuğu komutlarını yerelleştirilmiş metin sağlayabilir *.vsct* dosyaları ve yerelleştirilmiş *.resx* dosyaları, VSPackage'ı ve ardından Proje dosyalarını güncelleştirme eklemek için değiştirir.  
  
 Bir yükleme deneyimi yerelleştirmek hakkında daha fazla bilgi için bkz. [yerelleştirmek VSIX paketlerini](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localize-command-names"></a>Komut adlarını yerelleştirme  
 Vspackage'larda, menü komutlarını ve araç çubuğu düğmeleri tanımlanan *.vsct* dosya.  
  
1. İçinde **Çözüm Gezgini**, adını değiştirmek *.vsct* dosya *filename.vsct* için *filename.en US.vsct*.  
  
2. Bir kopyasını *filename.en US.vsct* her biri için yerelleştirme dili.  
  
    Her kopya adı *filename. { Yerel ayar} .vsct*burada *{yerel ayarı}* belirli bir kültür adı. Kültür adı değerleri listesi için bkz. [Microsoft tarafından atanan yerel kimlikler](/windows/uwp/publish/supported-languages).  
  
    Bunlar *dosya adı. Locale.vsct* paketiniz için menüsü yerelleştirilmiş metin dosyaları içerir.  
  
3. Her açın *dosya adı. Locale.vsct* metin yerelleştirmek için dosya.  
  
   1. Değiştirme [ButtonText](../extensibility/buttontext-element.md) öğe belirli bir dili için uygun değerleri.  
  
   2. Yerelleştirilmiş simgeler sağlayacaksa değiştirme [bit eşlem](../extensibility/bitmap-element.md) hedef dosyalarının olduğu noktaya değerleri.  
  
      Aşağıdaki örnek, bir Aile ağacı Gezgini araç penceresi açmak bir komut için İngilizce ve İspanyolca düğme metni gösterir.  
  
      [*FamilyTree.en US.vsct*]  
  
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
  
    [*FamilyTree.es ES.vsct*]  
  
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
  
## <a name="localize-other-text-resources"></a>Diğer metin kaynakları yerelleştirme  
 Komut adlarını dışında metin kaynakları kaynağında tanımlanmış (*.resx*) dosyaları.  
  
1.  Yeniden adlandırma *VSPackage.resx* için *VSPackage.en-US.resx*.  
  
2.  Bir kopyasını *VSPackage.en-US.resx* dosyası her bir yerelleştirme dili.  
  
     Her kopya adı *VSPackage'ı. { Yerel ayar} .resx*burada *{yerel ayarı}* belirli bir kültür adı.  
  
3.  Yeniden adlandırma *Resources.resx* için *Resources.en-US.resx*.  
  
4.  Bir kopyasını *Resources.en-US.resx* dosyası her bir yerelleştirme dili.  
  
     Her kopya adı *kaynaklar. { Yerel ayar} .resx*burada *{yerel ayarı}* belirli bir kültür adı.  
  
5.  Her açın *.resx* dizesini değiştirmek için dosya belirli bir dil ve kültür için uygun değerleri. Aşağıdaki örnek, bir araç penceresinin başlık çubuğu için yerelleştirilmiş kaynak tanımı gösterilmektedir.  
  
     [*Resources.en-US.resx*]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [*Resources.es ES.resx*]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporate-localized-resources-into-the-project"></a>Yerelleştirilmiş kaynaklar projeye dahil edilip derecelendirilir.  
 Değiştirmeniz gereken *AssemblyInfo.cs* dosya ve proje dosyası yerelleştirilmiş kaynakları dahil edilip derecelendirilir.  
  
1.  Gelen **özellikleri** düğümünde **Çözüm Gezgini**açın *AssemblyInfo.cs* veya *AssemblyInfo.vb* Düzenleyicisi.  
  
2.  Şu girişi ekleyin.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Bu ABD İngilizcesi varsayılan dili ayarlar.  
  
3.  Projeyi kaldırmak.  
  
4.  Proje Dosyası Düzenleyicisi'nde açın.  
  
5.  Bulun `ItemGroup` öğesini içeren `EmbeddedResource` öğeleri.  
  
6.  İçinde `EmbeddedResource` çağıran öğe *VSPackage.en-US.resx*, değiştirin `ManifestResourceName` öğesi ile bir `LogicalName` kümesine öğesini `VSPackage.en-US.Resources`aşağıdaki gibi.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Yerelleştirilen her dil için kopyalama `EmbeddedResource` öğesi için `VsPackage.en-US`ve **INCLUDE** özniteliği ve **LogicalName** aşağıda gösterildiği gibi hedef yerel kopyasının öğesi örnek.  
  
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
  
     Bu, bir ana derlemeye yanı sıra, her dil için kaynak grupları oluşturur. Dağıtım işlemi yerelleştirme hakkında daha fazla bilgi için bkz: [yerelleştirmek VSIX paketleri](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Menüler ve komutlar genişletme](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands vs. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [Globalize ve uygulamaları yerelleştirme](../ide/globalizing-and-localizing-applications.md)