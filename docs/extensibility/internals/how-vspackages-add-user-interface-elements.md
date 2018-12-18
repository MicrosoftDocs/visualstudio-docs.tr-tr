---
title: Nasıl VSPackages kullanıcı arabirimi öğeleri eklemesi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b498f9df752fd5ac1f1212649aa5b8bb62d27fb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839121"
---
# <a name="how-vspackages-add-user-interface-elements"></a>VSPackage kullanıcı arabirimi öğelerini nasıl eklenir
VSPackage örnek, menüleri ve araç çubukları için kullanıcı arabirimi (UI) öğeleri ekleyebilir ve araç penceresi, Visual Studio yoluyla *.vsct* dosya.  
  
 Kullanıcı Arabirimi öğeleri için tasarım yönergeleri bulabilirsiniz [Visual Studio kullanıcı deneyimi yönergeleri](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio komut tablosu mimarisi  
 Belirtildiği gibi komut tablosu mimarisi hükümlerde mimari ilkeleri destekler. Soyutlamalar, veri yapılarını ve araçlar komut tablosu mimarisinin arkasında sacayakları aşağıdaki gibidir:  
  
-   Üç temel türlerde öğeler vardır: menü komutları ve gruplar. Menüleri kullanıcı Arabiriminde, menüleri, alt menüler, araç çubukları ve araç pencereleri sunulabilir. Kullanıcı IDE içinde yürütülebilir, ve menü öğeleri, düğmeler, liste kutuları veya diğer denetimleri sunulabilir yordamları komutlardır. Grupları, menüler ve komutlar kapsayıcılardır.  
  
-   Her öğe, öğe diğer öğeleri ve davranışını değiştirmek bayrakları göreli önceliğini açıklayan tanımı tarafından belirtilir.  
  
-   Her öğenin üst öğesinin açıklayan bir yerleştirme vardır. Böylece kullanıcı arabiriminde birden fazla konumda görünebilir bir öğe birden çok üst öğeye sahip olabilir.  
  
     Bu gruptaki yalnızca alt olsa bile, her komut kendi üst öğesi olarak bir grup olmalıdır. Her standart menü, ayrıca bir üst grubu olmalıdır. Araç çubukları ve araç pencerelerini, kendi üst davranır. Bir grup ana Visual Studio menü çubuğunda, üst veya tüm menü, araç çubuğunda veya araç penceresi olabilir.  
  
### <a name="how-items-are-defined"></a>Öğeleri nasıl tanımlanır  
 A *.vsct* biçimlendirilmiş XML dosyası. Bir paket için kullanıcı Arabirimi öğelerini tanımlar ve bu öğeleri IDE'de nerede görüneceğini belirler. Her menü, Grup veya paketteki komutu bir GUID ve ID, ilk atanan `Symbols` bölümü. Geri kalanında *.vsct* dosyası, her menüsü, komut ve grup, GUID ve ID bileşimiyle tanımlanır. Aşağıdaki örnekte gösterilmektedir `Symbols` bölümünde Visual Studio Paket şablon tarafından oluşturulan olduğunda bir **menü komutu** şablonu seçilir.  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 Üst düzey öğesi `Symbols` bölüm [GuidSymbol öğesi](../../extensibility/guidsymbol-element.md). `GuidSymbol` öğe adları IDE tarafından paketleri ve bunların bileşen parçalarına tanımlamak için kullanılan GUID'lere eşleyin.  
  
> [!NOTE]
>  GUID'ler, Visual Studio Paket şablon tarafından otomatik olarak oluşturulur. Tıklayarak benzersiz bir GUID oluşturabilirsiniz **GUID Oluştur** üzerinde **Araçları** menüsü.  
  
 İlk `GuidSymbol` öğesi `guid<PackageName>Pkg`, paketin GUID'dir. Paketi yüklemek için Visual Studio tarafından kullanılan GUID budur. Genellikle, alt öğe yok.  
  
 Kural gereği, menüler ve komutlar saniyenin altında gruplandırılır `GuidSymbol` öğesi `guid<PackageName>CmdSet`, ve bit eşlemler altında üçüncü `GuidSymbol` öğesi `guidImages`. Bu kurala uymayan gerekmez, ancak her bir menü, Grup, komut ve bit eşlem alt öğesi olmalıdır bir `GuidSymbol` öğesi.  
  
 İkinci `GuidSymbol` paket komut kümesini temsil eden öğe çok sayıda `IDSymbol` öğeleri. Her [Idsymbol öğesi](../../extensibility/idsymbol-element.md) sayısal bir değer için bir ad eşler ve menü, Grup veya komut kümesinin bir parçası olan komutu temsil edebilir. `IDSymbol` Üçüncü öğeleri `GuidSymbol` simgelerle komutları için kullanılabilir öğe temsil bit eşlemler. GUID/ID çiftleri uygulamada iki alt aynı benzersiz olması gerektiğinden `GuidSymbol` öğesi aynı değere sahip olabilir.  
  
### <a name="menus-groups-and-commands"></a>Menüleri, gruplar ve komutlar  
 Bir menü, Grup veya komut bir GUID ve ID olduğunda, IDE eklenebilir. Her kullanıcı Arabirimi öğesi şunları içermelidir:  
  
-   A `guid` adıyla eşleşen öznitelik `GuidSymbol` UI öğesi altında tanımlanmış bir öğe.  
  
-   Bir `id` ilişkili adıyla eşleşen öznitelik `IDSymbol` öğesi.  
  
     Birlikte `guid` ve `id` öznitelikleri compose *imza* UI öğesi.  
  
-   A `priority` UI öğesi kendi üst menü ya da Grup yerleşimini belirler özniteliği.  
  
-   A [üst öğe](../../extensibility/parent-element.md) olan `guid` ve `id` imza üst menü veya grubun belirten öznitelikleri.  
  
#### <a name="menus"></a>Menüler  
 Her menüye olarak tanımlanan bir [menü öğesi](../../extensibility/menu-element.md) içinde `Menus` bölümü. Menüler olmalıdır `guid`, `id`, ve `priority` öznitelikleri ve `Parent` öğesini ve ayrıca aşağıdaki ek öznitelikleri ve alt öğeleri:  
  
- A `type` menü IDE'deki bir menü veya araç çubuğu olarak görüntülenip görüntülenmeyeceğini belirten özniteliği.  
  
- A [Strings öğesi](../../extensibility/strings-element.md) içeren bir [ButtonText öğesi](../../extensibility/buttontext-element.md), IDE'de menünün başlığını belirtir ve bir [CommandName öğesi](../../extensibility/commandname-element.md), adını belirtir kullanılan **komut** menüye erişmek için penceresi.  
  
- İsteğe bağlı bayraklar. A [CommandFlag öğesi](../../extensibility/command-flag-element.md) görünüşünü veya IDE'de davranışını değiştirmek için bir menü tanımı görünebilir.  
  
  Her `Menu` öğesi içermelidir bir grubu kendi üst öğesi olarak gibi bir araç çubuğunun yerleştirilebilir bir öğesi olmadığı sürece. Yerleştirilebilir bir menü kendi üst öğesidir. Menüler ve değerleri hakkında daha fazla bilgi için `type` özniteliği için bkz: [menü öğesi](../../extensibility/menu-element.md) belgeleri.  
  
  Aşağıdaki örnek, Visual Studio menü çubuğunda, yanındaki açılan menü gösterir **Araçları** menüsü.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>Gruplar  
 Bir grubu içinde tanımlanan bir öğedir `Groups` bölümünü *.vsct* dosya. Gruplar yalnızca kapsayıcılardır. IDE dışında bir menüdeki bir çizgi olarak görünmezler. Bu nedenle, bir [Group öğesi](../../extensibility/group-element.md) yalnızca kendi imzası, öncelik ve üst tarafından tanımlanır.  
  
 Bir grupta, üst öğe olarak menü, başka bir grup veya kendisi olabilir. Ancak, üst genellikle bir menü veya araç olur. Önceki örnekte menüde bir alt öğesidir `IDG_VS_MM_TOOLSADDINS` grubu ve bu grubu Visual Studio menü çubuğunda alt öğesi olan. Aşağıdaki örnekte önceki örnekte menünün alt grubudur.  
  
```xml  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Bir menü bir parçası olduğundan, bu Grup genellikle komutları içerir. Ancak, diğer menülere de içerebilir. Alt menüler nasıl tanımlanır, aşağıdaki örnekte gösterildiği gibi budur.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>Komutlar  
 IDE için sağlanan bir komut olarak tanımlanan bir [Button öğesi](../../extensibility/button-element.md) veya [Combos öğesi](../../extensibility/combo-element.md). Bir menü veya araç çubuğu üzerinde görünmesi için komut kendi üst öğesi olarak bir grup olmalıdır.  
  
##### <a name="buttons"></a>Düğmeleri  
 Düğmeler tanımlanmış `Buttons` bölümü. Tüm menü öğesi, düğme veya tek bir komut çalıştırmak için bir kullanıcı tıkladığında başka bir öğenin bir düğme olarak kabul edilir. Bazı düğme türleri listesi işlevselliği de içerebilir. Düğmeleri aynı gerekli ve menüler olan isteğe bağlı öznitelikleri vardır ve ayrıca olabilir bir [Icon öğesi](../../extensibility/icon-element.md) GUID ve IDE'de düğmesi nesnesini temsil eden bir bit eşlem Kimliğini belirtir. Düğmeler ve onların öznitelikleri hakkında daha fazla bilgi için bkz: [Buttons öğesi](../../extensibility/buttons-element.md) belgeleri.  
  
 Düğme aşağıdaki örnekte önceki örnekte grubunun bir alt öğesidir ve IDE'de menü öğesi o grubun üst menüsünde görünür.  
  
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
  
##### <a name="combos"></a>Combos  
 Combos tanımlanmış `Combos` bölümü. Her `Combo` öğesi, IDE'yi bir açılan liste kutusunda temsil eder. Liste kutusu olabilir veya değerine bağlı olarak, kullanıcılar tarafından yazılabilir olmayabilir `type` birleşik giriş özniteliği. Combos aynı öğeleri varsa ve düğme davranışı sahip ve aşağıdaki ek öznitelikleri de sahip olabilir:  
  
- A `defaultWidth` piksel genişliği belirten özniteliği.  
  
- Bir `idCommandList` liste kutusunda görüntülenen öğeler içeren bir liste belirten özniteliği. Komut listesi aynı şekilde bildirilmelidir `GuidSymbol` birleşik giriş içeren düğümü.  
  
  Aşağıdaki örnek, bir combos öğesi tanımlar.  
  
```xml  
<Combos>  
  <Combo guid="guidFirstToolWinCmdSet"  
         id="cmdidWindowsMediaFilename"  
         priority="0x0100" type="DynamicCombo"  
         idCommandList="cmdidWindowsMediaFilenameGetList"  
         defaultWidth="130">  
    <Parent guid="guidFirstToolWinCmdSet"  
            id="ToolbarGroupID" />  
    <CommandFlag>IconAndText</CommandFlag>  
    <CommandFlag>CommandWellOnly</CommandFlag>  
    <CommandFlag>StretchHorizontally</CommandFlag>  
    <Strings>  
      <CommandName>Filename</CommandName>  
      <ButtonText>Enter a Filename</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
##### <a name="bitmaps"></a>Bit eşlemler  
 Bir simge ile birlikte görüntülenir komutları içermelidir bir `Icon` kendi GUID ve Kimliği'ni kullanarak bir bit eşleme başvurduğu öğesi Her bir bit eşlem olarak tanımlanan bir [Bitmap öğesi](../../extensibility/bitmap-element.md) içinde `Bitmaps` bölümü. Öznitelikler için yalnızca gerekli bir `Bitmap` definition `guid` ve `href`, kaynak dosyaya işaret eder. Bir kaynak Şerit kaynak dosyası ise, bir **usedList** özniteliktir Ayrıca Şerit kullanılabilir görüntüleri listelemek için gerekli. Daha fazla bilgi için [Bitmap öğesi](../../extensibility/bitmap-element.md) belgeleri.  
  
### <a name="parenting"></a>Üst öğe oluşturma  
 Aşağıdaki kurallar, bir öğe başka bir öğe üst öğe olarak nasıl çağırabilirsiniz kapsar.  
  
|Öğe|Bu komut tablosu bölümünde tanımlanan|Bulunabilecek (üst öğe olarak veya yerleşimden `CommandPlacements` bölüm veya her ikisi)|İçerebilir (üst öğe olarak adlandırılır)|  
|-------------| - | - | - |  
|Grup|[Groups öğesi](../../extensibility/groups-element.md), IDE, diğer VSPackage'ları|Bir menü, bir Grup öğesi|Menüleri, gruplar ve komutlar|  
|Menü|[Menus öğesi](../../extensibility/menus-element.md), IDE, diğer VSPackage'ları|1 *n* grupları|0 olarak *n* grupları|  
|Araç Çubuğu|[Menus öğesi](../../extensibility/menus-element.md), IDE, diğer VSPackage'ları|Öğesi|0 olarak *n* grupları|  
|Menü Öğesi|[Buttons öğesi](../../extensibility/buttons-element.md), IDE, diğer VSPackage'ları|1 *n* öğe gruplandırır|-0 olarak *n* grupları|  
|Düğme|[Buttons öğesi](../../extensibility/buttons-element.md), IDE, diğer VSPackage'ları|1 *n* öğe gruplandırır||  
|Birleşik giriş|[Combos öğesi](../../extensibility/combos-element.md), IDE, diğer VSPackage'ları|1 *n* öğe gruplandırır||  
  
### <a name="menu-command-and-group-placement"></a>Menü ve komut grubunu yerleştirme  
 Bir menü, Grup veya komut IDE içindeki birden fazla yerde görünebilir. Bir öğenin birden fazla konumda görünmesini eklenmesi gerekir `CommandPlacements` bölümü bir [CommandPlacement öğesi](../../extensibility/commandplacement-element.md). Herhangi bir menü, Grup veya komutu bir komut yerleşimi eklenebilir. Ancak, bağlama duyarlı birden fazla konumda yer alamaz çünkü araç çubukları bu şekilde yerleştirilmiş olamaz.  
  
 Komut yerleştirme özgürlüğünü sahip `guid`, `id`, ve `priority` öznitelikleri. GUID ve ID konumlandırılmış öğesinin eşleşmelidir. `priority` Öznitelik öğe diğer öğeleri onaylamaz yerleşimini yönetir. IDE aynı önceliğe sahip iki veya daha fazla öğeyi birleştirir, IDE paket oluşturulan her zaman aynı sırada paket kaynakları okuma garantisi vermez çünkü bunların yerleşimi tanımsızdır.  
  
 Bir menü veya grup birden fazla konumda görünürse, her örneğinde tüm alt öğeleri bu menü veya grup görünür.  
  
## <a name="command-visibility-and-context"></a>Komutunu görünürlük ve bağlam  
 Birden çok VSPackages yüklendiğinde bir bolluk menüleri ve menü öğeleri araç çubukları, IDE dağıtmayı. Bu sorunu önlemek için tek tek kullanıcı Arabirimi öğeleri görünürlüğünü kullanarak denetleyebilirsiniz *görünürlük kısıtlamaları* ve komut bayrakları.  
  
### <a name="visibility-constraints"></a>Görünürlük kısıtlamaları  
 Görünürlüğü kısıtlama olarak ayarlanmış bir [Visibilityıtem öğesi](../../extensibility/visibilityitem-element.md) içinde `VisibilityConstraints` bölümü. Görünürlüğü kısıtlama hedef öğe görülebilir belirli UI bağlamı tanımlar. Yalnızca tanımlanmış bağlamları birini etkinken bir menü veya bu bölümünde yer alan komut görülebilir. Bu bölümde bir menü veya komut başvurulmuyorsa her zaman varsayılan olarak görünürdür. Bu bölüm grupları için geçerli değildir.  
  
 `VisibilityItem` öğeleri olmalıdır üç öznitelikleri gibi: `guid` ve `id` hedef UI öğesinin ve `context`. `context` Zaman hedef öğe görünür ve değeri olarak geçerli bir kullanıcı Arabirimi bağlamı alan özniteliğini belirtir. Visual Studio UI bağlamı sabitleri üyeleri <xref:Microsoft.VisualStudio.VSConstants> sınıfı. Her `VisibilityItem` öğesi yalnızca bir bağlam değeri alabilir. İkinci bağlam uygulamak için ikinci bir oluşturma `VisibilityItem` aşağıdaki örnekte gösterildiği gibi aynı öğeye işaret eden bir öğe.  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
```  
  
### <a name="command-flags"></a>Komut bayrakları  
 Aşağıdaki komut bayrakları, uygulandıkları komutlar ve menüler görünürlüğünü etkileyebilir.  
  
 `AlwaysCreate`  
 Herhangi bir düğme veya grupları sahip olsa bile menü oluşturulur.  
  
 Geçerlilik süresi: `Menu`  
  
 `CommandWellOnly`  
 Bu bayrak komutu üst düzey menüsünde görünmez ve ek Kabuğu özelleştirme için kullanılabilir hale getirmek istiyorsanız, bir anahtara bağlama uygulayın. VSPackage'ı yükledikten sonra bir kullanıcı bu komutları açarak özelleştirebilirsiniz **seçenekleri** iletişim kutusunu ve ardından komut yerleştirme altında düzenleme **klavye ortam** kategorisi. Kısayol menüleri, araç çubukları, menü denetleyicisi veya alt menüler yerleştirme etkilemez.  
  
 İçin geçerli: `Button`, `Combo`  
  
 `DefaultDisabled`  
 Varsayılan olarak, komut, komut uygulayan VSPackage yüklenmedi veya QueryStatus yöntemi çağrılmadı devre dışıdır.  
  
 İçin geçerli: `Button`, `Combo`  
  
 `DefaultInvisible`  
 Varsayılan olarak, komut uygulayan VSPackage yüklenmedi veya QueryStatus yöntemi çağrılmadı komutu görünmez durumdadır.  
  
 İle birleştirilmelidir `DynamicVisibility` bayrağı.  
  
 İçin geçerli: `Button`, `Combo`, `Menu`  
  
 `DynamicVisibility`  
 Komut görünürlüğünü kullanarak değiştirilebilir `QueryStatus` yöntemi veya bir bağlam eklenmiştir GUID `VisibilityConstraints` bölümü.  
  
 Menüleri, araç çubukları üzerinde görünmesini komutları için geçerlidir. Üst düzey araç çubuğu öğelerini devre dışı ancak, ne zaman gizlenmesi `OLECMDF_INVISIBLE` bayrağı döndürülmez `QueryStatus` yöntemi.  
  
 Menüde üyelerini gizli olduğunda bunu otomatik olarak gizlenmelidir bu bayrağı da gösterir. Üst düzey menüler bu davranışı olduğundan bu bayrağı için alt menüler genellikle atanır.  
  
 İle birleştirilmelidir `DefaultInvisible` bayrağı.  
  
 İçin geçerli: `Button`, `Combo`, `Menu`  
  
 `NoShowOnMenuController`  
 Bu bayrak sahip bir komut menü denetleyicisi üzerinde konumlandırılmış, komutu aşağı açılan listede görünmez.  
  
 Geçerlilik süresi: `Button`  
  
 Komut bayrakları hakkında daha fazla bilgi için bkz: [CommandFlag öğesi](../../extensibility/command-flag-element.md) belgeleri.  
  
#### <a name="general-requirements"></a>Genel gereksinimler  
 Önce görüntülenen ve etkin, komut aşağıdaki dizi test geçirilmelidir:  
  
-   Komutu, doğru yerleştirilir.  
  
-   `DefaultInvisible` Bayrağı ayarlı değil.  
  
-   Üst menü veya araç çubuğu görünür olur.  
  
-   Komut bir bağlam giriş nedeniyle görünmez değil [VisibilityConstraints öğesi](../../extensibility/visibilityconstraints-element.md) bölümü.  
  
-   VSPackage'ı uygulayan kodu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi görüntüler ve komutunuzu sağlar. Hiçbir arabirimi kodu, bunu engelledik ve üzerinde işlem.  
  
-   Kullanıcı komutu tıkladığında, ana hatlarıyla açıklanan yordamı tabi olur [yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="call-pre-defined-commands"></a>Önceden tanımlanmış komutlarını çağıran  
 [UsedCommands öğesi](../../extensibility/usedcommands-element.md) VSPackages IDE veya diğer VSPackage'ları tarafından sağlanan erişim komutlarını sağlar. Bunu yapmak için oluşturun bir [UsedCommand öğesi](../../extensibility/usedcommand-element.md) GUID ve kullanmak için komutu kimliği vardır. Geçerli Visual Studio yapılandırmasının bir parçası olmasa bile bu komutu Visual Studio tarafından yüklenen sağlar. Daha fazla bilgi için [UsedCommand öğesi](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Arabirim öğesi görünümü  
 Seçme ve komut öğeleri konumlandırma konuları aşağıdaki gibidir:  
  
- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] farklı yerleştirme bağlı olarak görünen birçok kullanıcı Arabirimi öğeleri sunar.  
  
- Tarafından tanımlanan bir kullanıcı Arabirimi öğesi `DefaultInvisible` bayrağı görüntülenmeyecek IDE'de ya da kendi VSPackage uygulaması tarafından görüntülenen olmadığı sürece <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> yöntemi veya belirli bir kullanıcı Arabirimi bağlamda ilişkili `VisibilityConstraints` bölümü.  
  
- Başarıyla konumlandırılmış bir komut görüntülenmeyebilir. Bu IDE otomatik olarak gizler veya VSPackage'ı (veya değil) arabirimler bağlı olarak bazı komutlar görüntüler için uygulanır. Örneğin, bazı VSPackage'nın uygulama yapı arabirimleri nedenleri derlemeyle ilgili menü öğeleri otomatik olarak gösterilecek.  
  
- Uygulama `CommandWellOnly` UI öğesinin tanımını bayrağı anlamına gelir komutu yalnızca özelleştirme tarafından eklenebilir.  
  
- IDE Tasarım görünümünde olduğunda yalnızca bir iletişim kutusu görüntülendiğinde, komutları yalnızca belirli kullanıcı Arabirimi bağlamlarda Bu, örneğin, kullanılabilir olabilir.  
  
- IDE içinde görüntülenecek belirli UI öğeleri neden olmak için bir veya daha fazla arabirimi uygulayan veya biraz kod yazalım.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Menüler ve komutlar genişletme](../../extensibility/extending-menus-and-commands.md)