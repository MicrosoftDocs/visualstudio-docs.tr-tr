---
title: MenuCommands Vs. OleMenuCommands | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 46
manager: douge
ms.openlocfilehash: 3b548a43cabcb097250411c3475f47774c840511
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911921"
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommands Vs. OleMenuCommands
Öğesinden türetme, menü komutlarını oluşturabilirsiniz <xref:System.ComponentModel.Design.MenuCommand> veya <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> nesne ve impementling uygun olay işleyicileri. Çoğu durumda, kullanabileceğiniz <xref:System.ComponentModel.Design.MenuCommand>VSPackage proje şablonu yapar, ancak bazen kullanmanız gerekebilir gibi <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>.  
  
 IDE için kullanılabilir bir VSPackage yapar görünür ve etkin bir kullanıcı önce olması gerektiğini komutları bunları kullanabilirsiniz. Komutlar, Visual Studio Paketi proje şablonunu kullanarak .vsct dosyası içinde oluşturulduğunda, görünür ve varsayılan olarak etkindir. Bazı komut bayrakları gibi ayarlama `DynamicItemStart`, varsayılan davranışı değiştirebilirsiniz. Görünürlük, etkin durumunu ve diğer özellikleri komut da kod çalışma zamanında erişerek değiştirilebilir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> komut ile ilişkili olan nesne.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Visual Studio Paketi şablonu için şablon konumları  
 Visual Studio Paket şablon bulabilirsiniz **yeni proje** iletişim altında **Visual Basic / genişletilebilirlik**, **C# / genişletilebilirlik**, veya **diğer Proje türleri / genişletilebilirlik**.  
  
## <a name="creating-a-command"></a>Bir komut oluşturma  
 Tüm komutlar, komut gruplarını, menüler, araç çubukları ve araç pencerelerini .vsct dosyası içinde tanımlanır. Daha fazla bilgi için [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Paket şablonu kullanarak bir VSPackage oluşturuyorsanız seçin **menü komutu** .vsct dosyası oluşturma ve varsayılan menü komutu tanımlama. Daha fazla bilgi için [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>IDE komut ekleme  
  
1. .Vsct dosyası açın.  
  
2. İçinde `Symbols` bölümünde, bulma [GuidSymbol](../extensibility/guidsymbol-element.md) grupları ve komutları içeren öğe.  
  
3. Oluşturma bir [Idsymbol](../extensibility/idsymbol-element.md) her menü, Grup veya komutu eklemek için aşağıdaki örnekte gösterildiği gibi istediğiniz için öğesi.  
  
   ```xml
   <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
     <IDSymbol name="MyMenuGroup" value="0x1020" />
     <IDSymbol name="cmdidMyCommand" value="0x0100" />
   </GuidSymbol>
   ```
      
    `name` Özniteliklerini `GuidSymbol` ve `IDSymbol` öğeleri her yeni menü, Grup veya komut GUID:ID çifti belirtin. `guid` , VSPackage için tanımlanmış bir komut kümesini temsil eder. Birden çok komut kümesi tanımlayabilirsiniz. Her GUID:ID çifti benzersiz olması gerekir.  
  
4. İçinde [düğmeleri](../extensibility/buttons-element.md) bölümünde, oluşturun bir [düğmesi](../extensibility/button-element.md) komutu aşağıdaki örnekte gösterildiği şekilde tanımlamak için.  
  
   ```xml
   <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
     <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
       <CommandName>cmdidMyCommand</CommandName>
       <ButtonText>My Command name</ButtonText>
     </Strings>
   </Button>
   ``` 
     
   1.  Ayarlama `guid` ve `id` yeni komut GUID:ID eşleşecek alanları.  
  
   2.  Ayarlama `priority` özniteliği.  
  
        `priority` Özniteliği tarafından .vsct kendi üst grubundaki diğer nesneler arasında düğmenin konumu belirlemek için kullanılır.  
  
        Düşük öncelikli değerlere sahip komutları üstüne ya da sol tarafında, daha yüksek öncelik değerine sahip komutlar görüntülenir. Yinelenen öncelik değerlere izin verilir, ancak eşit önceliğe sahip komutları göreli konumunu VSPackages çalışma zamanında işlenme sırasını tarafından belirlenir ve bu sıraya göre belirlenmiş olamaz.  
  
        Atlama `priority` öznitelik değerini 0 olarak ayarlar.  
  
   3.  Ayarlama `type` özniteliği. Çoğu durumda, değeri olacak `"Button"`. Diğer geçerli düğmesi türlerinin açıklamaları için bkz. [Button öğesi](../extensibility/button-element.md).  
  
5. Düğme tanımındaki oluşturmak bir [dizeleri](../extensibility/strings-element.md) öğesini içeren bir [ButtonText](../extensibility/buttontext-element.md) IDE içinde göründüğü gibi menünün adını içerecek şekilde öğesi ve bir [CommandName](../extensibility/commandname-element.md) menüde erişmek için kullanılan komut adını içerecek şekilde öğesi **komut** penceresi.  
  
    Düğme metin dizesi, '&' karakteri içerir, kullanıcı Alt tuşunu basılı tutarak menüsünü açabilir ve karakteri, hemen izleyen, '&'.  
  
    Ekleme bir `Tooltip` öğesi, bir kullanıcı düğmenin üzerine işaretçiyi geldiğinde görünmesini kapsanan metin neden olur.  
  
6. Ekleme bir [simgesi](../extensibility/icon-element.md) varsa komutuyla görüntülenecek simge belirtmek için öğesi. Simgeler araç çubuğu düğmeleri için menü öğeleri ancak gerekli değildir. `guid` Ve `id` , `Icon` öğe içeriğiyle eşleşmesi gereken bir [bit eşlem](../extensibility/bitmap-element.md) tanımlanan öğe `Bitmaps` bölümü.  
  
7. Uygun bir şekilde düğmesinin davranışını ve görünümünü değiştirmek, komut bayrakları ekleyin. Bunu yapmak için bir [CommandFlag](../extensibility/command-flag-element.md) menü tanımındaki öğesi.  
  
8. Komutu, üst grup olarak ayarlayın. Üst grup, oluşturduğunuz bir grubu, bir grubu başka bir paketten veya IDE grubundan olabilir. Örneğin, komutunuz Visual Studio düzenleme araç çubuğuna yanındaki eklemek için **yorum** ve **Yorumu Kaldır** düğmeleri, üst guidStdEditor:IDG_VS_EDITTOOLBAR_COMMENT için ayarlayın. Kullanıcı tanımlı bir grup üst ise alt menü, araç veya IDE içinde görünen araç penceresi olması gerekir.  
  
    Tasarımınızı bağlı olarak bu iki yoldan biriyle yapabilirsiniz:  
  
   -   İçinde `Button` öğesi oluşturmak bir [üst](../extensibility/parent-element.md) öğesi ve set kendi `guid` ve `id` GUID ve ID komutu olarak da bilinen barındıracak grubunun alanlarına *birincilüstgrup*.  
  
        Aşağıdaki örnek, kullanıcı tanımlı bir menüsünde görünür bir komut tanımlar.  
  
       ```xml
       <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
         <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
         <Icon guid="guidImages" id="bmpPic1" />
         <Strings>
           <CommandName>cmdidTestCommand</CommandName>
           <ButtonText>Test Command</ButtonText>
             </Strings>
       </Button>
       ```
      
   -   Atlasa `Parent` komutu komut yerleştirme kullanarak konumlandırılan ise öğe. Oluşturma bir [CommandPlacements](../extensibility/commandplacements-element.md) öğeden önce `Symbols` bölümünde ve ekleme bir [CommandPlacement](../extensibility/commandplacement-element.md) sahip öğe `guid` ve `id` komutunun, bir `priority`ve aşağıdaki örnekte gösterildiği gibi bir üst.  
  
   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
       <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     </CommandPlacement>
   </CommandPlacements>
   ```
      
        Creating multiple command placements that have the same GUID:ID and have different parents causes a menu to appear in multiple locations. For more information, see [CommandPlacements](../extensibility/commandplacements-element.md) element.  
  
    Komut grupları ve ana öğe hakkında daha fazla bilgi için bkz. [, yeniden kullanılabilir grupları düğmeler oluşturma](../extensibility/creating-reusable-groups-of-buttons.md).  
  
   Bu noktada, komutu IDE içerisinde görünür, ancak hiçbir işlevselliğine sahip olurlar. Varsayılan olarak komut paket şablon tarafından oluşturulmuş olsa bile, bir ileti görüntüler bir tıklama işleyicisi bulunur.  
  
## <a name="handling-the-new-command"></a>Yeni bir komut işleme  
 Yönetilen kodda çoğu komutu komutu ile ilişkilendirerek yönetilen paket Framework'tarafından (MPF) işlenebilen bir <xref:System.ComponentModel.Design.MenuCommand> nesne veya <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> nesne ve onun olay işleyicileri uygulama.  
  
 Kullanan kod için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirim doğrudan komut işlemesi için uygulanmalı <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi ve yöntemleri. İki en önemli yöntemlerdir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>.  
  
1.  Alma <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> , aşağıdaki örnekte gösterildiği gibi örnek.  
  
     [!code-csharp[ButtonGroup#21](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#21)]  
  
2.  Oluşturma bir <xref:System.ComponentModel.Design.CommandID> GUID ve ID işlemek için komut olan aşağıdaki örnekte gösterildiği gibi parametre olarak nesne.  
  
     [!code-csharp[ButtonGroup#22](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#22)]  
  
     Visual Studio Paket şablon iki koleksiyon sağlar `GuidList` ve `PkgCmdIDList`, GUID'leri ve kimlikleri komutları tutacak. Bu şablon tarafından eklenen komutları için otomatik olarak doldurulur ancak el ile eklemeniz komutları da kimliği girişe eklemelisiniz `PkgCmdIdList` sınıfı.  
  
     Alternatif olarak, doldurabilirsiniz <xref:System.ComponentModel.Design.CommandID> GUID'yi ham dize değeri ve kimliği tamsayı değerini kullanarak nesne  
  
3.  Ya da örneği bir <xref:System.ComponentModel.Design.MenuCommand> veya <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ile birlikte komutu işleyen yöntem belirten nesne <xref:System.ComponentModel.Design.CommandID>aşağıdaki örnekte gösterildiği gibi.  
  
     [!code-csharp[ButtonGroup#23](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#23)]  
  
     <xref:System.ComponentModel.Design.MenuCommand> Statik komutları için uygundur. Dinamik menü öğesi görüntüler QueryStatus olay işleyicileri gerektirir. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Ekler <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> ana menü komut açılmış ve başka bazı özellikleri gibi olduğunda oluşan olay <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Paket şablon tarafından oluşturulan komutlar için varsayılan olarak geçirilir bir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> nesnesine `Initialize()` paket sınıfının yöntemi.  
  
4.  <xref:System.ComponentModel.Design.MenuCommand> Statik komutları için uygundur. Dinamik menü öğesi görüntüler QueryStatus olay işleyicileri gerektirir. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Ekler <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> ana menü komut açılmış ve başka bazı özellikleri gibi olduğunda oluşan olay <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Paket şablon tarafından oluşturulan komutlar için varsayılan olarak geçirilir bir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> nesnesine `Initialize()` paket sınıfının yöntemi. Visual Studio Sihirbazı'nı uygulayan `Initialize` yöntemi kullanarak `MenuCommand`. Dinamik menü öğesi görüntüler için bu değiştirmelisiniz `OleMenuCommand`sonraki adımda gösterildiği gibi. Ayrıca, menü öğesi metni değiştirmek için bir TextChanges komut bayrak .vsct dosyası menü komut düğmesine aşağıdaki örnekte gösterildiği gibi eklemeniz gerekir  
  
    ```xml
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
      
5.  Yeni menü Command'e <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> yönteminde <xref:System.ComponentModel.Design.IMenuCommandService> arabirimi. Bu paket şablon tarafından oluşturulan komutlar için varsayılan olarak aşağıdaki örnekte gösterildiği gibi gerçekleştirilir  
  
     [!code-csharp[ButtonGroup#24](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#24)]  
  
6.  Komutu işleyen yöntem uygulayın.  
  
#### <a name="to-implement-querystatus"></a>QueryStatus uygulamak için  
  
1. QueryStatus olay, bir komut görüntülenmeden önce oluşur. Bu kullanıcı ulaşmadan önce olay işleyicisi ayarlamak için bu komutu özelliklerini sağlar. Olarak eklenen komutları <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> nesneleri, bu yöntem erişebilir.  
  
    Ekleme bir `EventHandler` nesnesini <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> olayında <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> komutunu işlemek için aşağıdaki örnekte gösterildiği gibi oluşturulan nesne (`menuItem` olduğu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> örnek).  
  
    [!code-csharp[MenuText#14](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#14)]
    [!code-vb[MenuText#14](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#14)]  
  
    `EventHandler` Nesne, menü komutunu durumunu sorgulandığında çağrılan yöntemin adı verilir.  
  
2. Sorgu durumu işleyicisi yöntemi'komutu için uygulayın. `object` `sender` Parametre değerine bir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> menü komutu metni dahil olmak üzere çeşitli özniteliklerini ayarlamak için kullanılan nesne. Aşağıdaki tabloda temel özelliklerini gösterir. <xref:System.ComponentModel.Design.MenuCommand> sınıfı (hangi MPF sınıfı <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> türetildiği) karşılık gelen için <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> bayrakları.  
  
   |MenuCommand özelliği|OLECMDF bayrağı|  
   |--------------------------|------------------|  
   |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
    Bir menü komutunun metnini değiştirmek için kullanın <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> özelliği <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> aşağıdaki örnekte gösterildiği gibi nesne.  
  
    [!code-csharp[MenuText#11](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#11)]
    [!code-vb[MenuText#11](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#11)]  
  
   MPF desteklenmeyen veya bilinmeyen gruplarının durum otomatik olarak işler. Komutu eklendi sürece <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> kullanarak <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> yöntemi, komutu desteklenmiyor.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>IOleCommandTarget arabirimi kullanarak komutları işleme  
 Kullanan kod için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> doğrudan arabirim, her ikisi de VSPackage'ı uygulamalıdır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemlerinin <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi. VSPackage'ı bir proje hiyerarşisi uyguluyorsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> yöntemlerinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> arabirimi uygulanmasını yerine.  
  
 Hem <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemleri, tek bir komut kümesi almak için tasarlanmıştır `GUID` ve komut kimlikleri bir dizi girişi olarak. Öneririz VSPackages tek çağrıda tam olarak bu kavramı birden çok kimliği destekler. VSPackage diğer VSPackages çağrılmaz sürece, ancak, komut dizisi için tek bir komut kimliği içerdiğini varsayabilirsiniz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemleri, iyi tanımlanmış bir sırayla yürütülür. Yönlendirme hakkında daha fazla bilgi için bkz. [vspackage'larda komut yönlendirme](../extensibility/internals/command-routing-in-vspackages.md).  
  
 Kullanan kod için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirim doğrudan komut işlemesi için uygulanmalı <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage'ı aşağıdaki gibi komutları işlemek için yöntemi.  
  
##### <a name="to-implement-the-querystatus-method"></a>QueryStatus yöntemi uygulamak için  
  
1. Dönüş <xref:Microsoft.VisualStudio.VSConstants.S_OK> geçerli komutları için.  
  
2. Ayarlama `cmdf` öğesinin `prgCmds` parametresi.  
  
    Değerini `cmdf` öğedir mantıksal değerleri birleşimi <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> numaralandırma, mantıksal OR kullanarak (`|`) işleci.  
  
    Komutun durumu temelinde uygun numaralandırma kullanın:  
  
   - Komut destekleniyorsa:  
  
      `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
   - Komut şu anda görünmez olması gerekiyorsa:  
  
      `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
   - Komut çubuğunda açılıp ve tıklanan görünür değilse:  
  
      `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
      Tür menüde barındırılan komutlarının işlenmesi durumunda `MenuControllerLatched`, tarafından işaretlenen ilk komut `OLECMDF_LATCHED` bayrağı tarafından başlangıç menüsünde görüntülenen varsayılan komutu verilmiştir. Hakkında daha fazla bilgi için `MenuController` menü türlerini görmek [menü öğesi](../extensibility/menu-element.md).  
  
   - Komut şu anda etkin olduğunda:  
  
      `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
   - Komutu bir kısayol menüsüne bir parçasıdır ve varsayılan olarak gizlidir:  
  
      `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
   - Komut kullanıyorsa `TEXTCHANGES` bayrak olarak ayarlayın `rgwz` öğesinin `pCmdText` parametre kümesi ve komut yeni metin `cwActual` öğesinin `pCmdText` komut dize boyutu parametresi.  
  
     Hata koşulları için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi, aşağıdaki durumlarda hata işleme gerekir:  
  
   - Bilinmeyen veya desteklenmeyen GUID ise, dönüş `OLECMDERR_E_UNKNOWNGROUP`.  
  
   - GUID verilir, ancak komut kimliği bilinmiyor veya desteklenmiyor. dönüş `OLECMDERR_E_NOTSUPPORTED`.  
  
   VSPackage uygulamasını <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi komutu desteklenip ve komut başarıyla işlenen bağlı olarak belirli hata kodlarıyla aynı zamanda döndürmesi gerekir.  
  
##### <a name="to-implement-the-exec-method"></a>Exec yöntemi uygulamak için  
  
-   Komut `GUID` bilinmiyor, iade `OLECMDERR_E_UNKNOWNGROUP`.  
  
-   Varsa `GUID` bilinen ancak komut kimliği bilinmiyor, iade `OLECMDERR_E_NOTSUPPORTED`.  
  
-   Varsa `GUID` ve kimliği ile aynı komutta .vsct dosyası tarafından kullanılan GUID:ID çifti komut, komut ve iade ile ilişkili kod yürütmesine <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSCT XML Şeması Başvurusu](../extensibility/vsct-xml-schema-reference.md)   
 [Menüleri ve Komutlari Genişletme](../extensibility/extending-menus-and-commands.md)