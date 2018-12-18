---
title: Menu öğesi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3120a64db5c493f8e49ddeac42be0b2e89a40c45
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908866"
---
# <a name="menu-element"></a>Menü öğesi
Bir menü öğesini tanımlar. Menüler altı türleri şunlardır: bağlam menüsü, MenuController, MenuControllerLatched, araç ve ToolWindowToolbar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|GUID|Gerekli. GUID/ID komut tanımlayıcısı GUİD'si.|  
|kimlik|Gerekli. Kimliği bir GUID/ID komut tanımlayıcısı.|  
|önceliği|İsteğe bağlı. Menü grubunda bir menü göreli konumunu belirten bir sayısal değer.|  
|ToolbarPriorityInBand|İsteğe bağlı. Pencerede Yuvalandığında bir bant araç göreli konumunu belirleyen bir sayısal değer.|  
|türü|İsteğe bağlı. Öğe türünü belirten bir numaralandırılmış değeri.<br /><br /> Yoksa, varsayılan menü türüdür.<br /><br /> Bağlam<br /> Bir kullanıcı bir pencere tıklattığında gösterilen bir kısayol menüsü. Kısayol menüsünde, aşağıdaki özelliklere sahiptir:<br /><br /> -Kullanmaz **üst** ve **öncelik** alanları menüsünde bir kısayol menüsü olarak görüntülenecek olduğunda.<br />-Alt menü ve ayrıca bir kısayol menüsü olarak kullanılan. Bu durumda, her ikisi de **Grup Kimliği** ve **öncelik** alanlar dikkate.<br />-Olduğundan her zaman kullanılabilir.<br /><br /> Yalnızca aşağıdaki koşullar geçerli olduğunda, bir kısayol menüsü görüntülenir:<br /><br /> -Barındırdığı penceresi görüntülenir.<br />-VSPackage'ı bir fare işleyicisinde, bir pencerenin sağ algılar ve ardından komutu işleyen bir yöntemi çağırır.<br />-Kısayol menüsünü çağrılarak görüntülenen <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> yöntemi (önerilen yaklaşım) veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> yöntemi.<br /><br /> Menü<br /> Bir açılan menü sağlar. Bir açılan menü aşağıdaki özelliklere sahiptir:<br /><br /> -Üst tanımında dikkate alır.<br />-Bir üst grubu veya bir gruba bir CommandPlacement sahip olmalıdır.<br />-Bir alt menü diğer tür içinde olması.<br />-Her onun üst menü görüntülendiğinde otomatik olarak görüntülenen.<br />-Görüntülenmesini sağlamak için herhangi bir VSPackage kod yürütmesinin gerektirmez.<br /><br /> MenuController<br /> Araç çubuklarında kullanılan genellikle bir Bölünmüş düğme açılan menü sağlar. MenuController menü aşağıdaki özelliklere sahiptir:<br /><br /> -Üst veya CommandPlacement aracılığıyla başka bir menüde bulunan gerekir.<br />-Üst tanımında dikkate alır.<br />-Herhangi bir türden menü, kendi üst öğesi olarak sahip olabilir.<br />-Her onun üst menü görüntülendiğinde otomatik olarak kullanıma sunulmaktadır.<br />-Görüntülenen menüyü yapmak için programlama desteği gerektirmez.<br /><br /> Bölünmüş düğme menüsünden bir komut menüsünde düğmesinde görüntülenir. Görüntülenen komut aşağıdaki özelliklere sahiptir:<br /><br /> -Bu komutu yine de görüntülenir ve etkinse, kullanılan son bir komuttur.<br />-Bu ilk görüntülenen komutudur.<br /><br /> MenuControllerLatched<br /> Kendisi için bir komut varsayılan seçim komut kilitli olarak işaretlemek için belirtilebilir Bölünmüş düğme açılan menü sağlar.<br /><br /> Mandallanmış komut menüsünde olarak seçili, genellikle bir onay işareti görüntüleyerek işaretlenmiş bir komuttur. Bir komut OLECMDF_LATCHED varsa kilitli olarak işaretlenebilir bayrak uygulaması üzerindeki kümesinde `QueryStatus` yöntemi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi. MenuControllerLatched menü aşağıdaki özelliklere sahiptir:<br /><br /> -Bir üst grubu veya CommandPlacement üzerinden başka bir menüde bulunan gerekir.<br />-Üst tanımında dikkate alır.<br />-Herhangi bir türden menü, kendi üst öğesi olarak sahip olabilir.<br />-Her onun üst menü görüntülendiğinde, kullanılabilir hale getirileceğini.<br />-Görüntülenen menüyü yapmak için programlama desteği gerektirmez.<br /><br /> Bölünmüş düğme menüsünden bir komut menüsünde düğmesinde görüntülenir. Görüntülenen komut aşağıdaki özelliklere sahiptir:<br /><br /> -Kilitli ilk görüntülenen komut olduğu.<br />-Bu ilk görüntülenen komutudur.<br /><br /> Araç Çubuğu<br /> Bir araç çubuğu sağlar. Araç, aşağıdaki özelliklere sahiptir:<br /><br /> -Üst tanımında yok sayar.<br />-Herhangi bir grubu bir alt bile CommandPlacement kullanılarak yapılan olamaz.<br />-Her zaman tıklayarak görüntülenebilen **araç çubukları** üzerinde **görünümü** menüsü.<br />-Kullanarak görüntülenebilen bir [Visibilityıtem](../extensibility/visibilityitem-element.md).<br />-Oluşturmak için herhangi bir kod gerektirmez. Araç çubuğu oluşturma hakkında bir örnek için bkz. [araç ekleme](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Yalnızca bir araç çubuğu geliştirme ortamına bağlı olarak belirli bir araç penceresine, bağlı bir araç sağlar.<br /><br /> -Üst tanımında yok sayar.<br />-Herhangi bir grubu bir alt bile CommandPlacement kullanılarak yapılan olamaz.<br />-Yalnızca bir araç çubuğu barındıran araç penceresi görüntülenir ve VSPackage açıkça araç penceresine araç çubuğu ekler görüntülenir. Araç penceresi araç çubuğu konak özelliğine elde ederek oluşturulduğunda bu genellikle gerçekleştirilir (tarafından temsil edilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> arabirimi) aracını pencere çerçevesi ve ardından arama <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> yöntemi.|  
|Koşul|İsteğe bağlı. Bkz: [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt öğeleri  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Üst|İsteğe bağlı. Menü öğesinin üst öğesi.|  
|CommandFlag|Gerekli. Bkz: [Command flag öğesi](../extensibility/command-flag-element.md). Bir menü için geçerli CommandFlag değerler aşağıdaki gibidir:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -Bu bayrak, araç çubukları görünümünü etkilemez.<br />-   **DontCache**<br />-   **DynamicVisibility** -Bu bayrak, araç çubukları görünümünü etkilemez.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|Dizeler|Gerekli. Bkz: [Strings öğesi](../extensibility/strings-element.md). Alt `ButtonText` öğesi tanımlanmalıdır.|  
|Ek Açıklama|İsteğe bağlı bir açıklama.|  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Menus öğesi](../extensibility/menus-element.md)|VSPackage'ı uygulayan tüm menüleri tanımlar.|  
  
## <a name="example"></a>Örnek  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"  
  priority="0x0002" type="Menu">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>AlwaysCreate</CommandFlag>  
    <Strings>  
      <ButtonText>Edit Widget</ButtonText>  
    </Strings>  
    </Parent>  
</Menu>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)