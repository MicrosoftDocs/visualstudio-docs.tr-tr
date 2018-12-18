---
title: Yazma. Vsct dosyaları | Microsoft Docs
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
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 50dc50aee377a4685527e57dc2af5d9946639946
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772176"
---
# <a name="authoring-vsct-files"></a>Yazma. Vsct dosyaları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu belge, menü öğeleri, araç çubukları ve diğer kullanıcı arabirimi (UI) öğeleri Visual Studio tümleşik geliştirme ortamı (IDE) eklemek için .vsct dosyası yazma işlemi gösterilmektedir. Visual Studio .vsct dosyası zaten sahip olmayan pakete (VSPackage'ı) kullanıcı Arabirimi öğeleri eklediğinizde, bu adımları kullanın.  
  
 Yeni projeler için seçimlerinizi bağlı olarak, bir menü komutu, bir araç penceresi ya da özel bir düzenleyici için gerekli öğeler zaten sahip olan bir .vsct dosyası oluşturur çünkü Visual Studio Paket şablon kullanmanızı öneririz. Bu .vsct dosyası, VSPackage gereksinimlerini karşılayacak şekilde değiştirebilirsiniz. Örneklerde .vsct dosyası değiştirme hakkında daha fazla bilgi için bkz. [genişletme menüler ve komutlar](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="authoring-the-file"></a>Dosya yazma  
 Bu aşamada .vsct dosyası Yazar: dosyalara ve kaynaklara yapısını oluşturmak, kullanıcı Arabirimi öğeleri bildirmek, IDE'de kullanıcı Arabirimi öğeleri yerleştirmek ve özel davranışları ekleyin.  
  
### <a name="file-structure"></a>Dosya yapısı  
 .Vsct dosyasının temel yapısı bir [CommandTable](../../extensibility/commandtable-element.md) içeren kök öğesi bir [komutları](../../extensibility/commands-element.md) öğesi ve bir [sembolleri](../../extensibility/symbols-element.md) öğesi.  
  
##### <a name="to-create-the-file-structure"></a>Dosya yapısı oluşturmak için  
  
1.  İçindeki adımları izleyerek .vsct dosyası projenize ekleyin [nasıl yapılır: oluşturma bir. Vsct dosya](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2.  Gerekli ad alanları için ekleme `CommandTable` öğesi, aşağıdaki örnekte gösterildiği gibi.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  İçinde `CommandTable` öğe, Ekle bir `Commands` tüm özel menüler, araç çubukları, komut gruplarını ve komutlarını barındırmak için öğesi. Böylece, özel kullanıcı Arabirimi öğeleri yükleyebilir `Commands` öğesi olmalı, `Package` özniteliği için paket adını ayarlayın.  
  
     Sonra `Commands` öğe, Ekle bir `Symbols` GUID'leri paketi ve adlarını tanımlamak ve komut kimlikleri için kullanıcı Arabirimi öğeleri için öğe.  
  
### <a name="including-visual-studio-resources"></a>Visual Studio kaynakları dahil olmak üzere  
 Kullanım [Extern](../../extensibility/extern-element.md) Visual Studio komutları ve IDE içinde kullanıcı Arabirimi öğeleri yerleştirmek için gereken menüleri tanımlayan dosyalara erişmek için öğesi. Paketiniz dışında tanımlanan komutlarının kullanacağı kullanırsanız [UsedCommands](../../extensibility/usedcommands-element.md) Visual Studio bildirmek için öğesi.  
  
##### <a name="to-include-visual-studio-resources"></a>Visual Studio kaynakları eklemek için  
  
1.  En üstündeki `CommandTable` öğesi ekleyin `Extern` başvurulan ayarlayın ve her bir dış dosya için öğe `href` dosyasının adı için öznitelik. Visual Studio kaynaklara erişmek için aşağıdaki üst bilgi dosyaları başvurabilirsiniz:  
  
    -   Stdidcmd.h, Visual Studio tarafından kullanıma sunulan tüm komutlar için kimlikleri tanımlar.  
  
    -   Vsshlids.h, komut kimlikleri için Visual Studio menü içerir.  
  
2.  Paketiniz diğer paketleri veya Visual Studio tarafından tanımlanan herhangi bir komut çağırırsa, ekleme bir `UsedCommands` öğeden sonra `Commands` öğesi. Bu öğe ile doldurmak bir [UsedCommand](../../extensibility/usedcommand-element.md) çağırmanızı diğer bir deyişle, paketin parçası olarak her komut için öğesi. Ayarlama `guid` ve `id` özniteliklerini `UsedCommand` öğelerine GUID ve ID değerleri çağrılacak komut. GUID'leri ve kimlikleri, Visual Studio komutları bulma hakkında daha fazla bilgi için bkz. [GUID'leri ve kimlikleri, Visual Studio komutları](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Diğer paketlerden komutları çağırmak için GUID ve bu paketleri için .vsct dosyası sınıfında tanımlandığı gibi komut Kimliği'ni kullanın.  
  
### <a name="declaring-ui-elements"></a>Kullanıcı Arabirimi öğeleri bildirme  
 Tüm yeni kullanıcı Arabirimi öğeleri bildirmek `Symbols` .vsct dosyası bölümünü.  
  
##### <a name="to-declare-ui-elements"></a>Kullanıcı Arabirimi öğeleri bildirmek için  
  
1.  İçinde `Symbols` öğesi üç ekleme [GuidSymbol](../../extensibility/guidsymbol-element.md) öğeleri. Her `GuidSymbol` öğeye sahip bir `name` özniteliği ve `value` özniteliği. Ayarlama `name` öğe amacı yansıtması adına, öznitelik. `value` Özniteliği bir GUID alır. (Bir GUID oluşturulacak **Araçları** menüsünde tıklayın **GUID Oluştur**ve ardından **biçimi kayıt defteri**.)  
  
     İlk `GuidSymbol` öğesi paketinizi temsil eder ve genellikle alt öğesi yok. İkinci `GuidSymbol` komut ayarlayın ve tüm, menüler, grupları ve komutları tanımlayan simgelerini içeren öğesi temsil eder. Üçüncü `GuidSymbol` öğesi, görüntü deposu temsil eder ve tüm simgeleri komutlarınız için simgeler içeriyor. Simgeleri kullanan herhangi bir komut varsa, üçüncü atlayabilirsiniz `GuidSymbol` öğesi.  
  
2.  İçinde `GuidSymbol` , komut kümesini temsil eden bir veya daha fazla Ekle [Idsymbol](../../extensibility/idsymbol-element.md) öğeleri. Bunların her biri bir menü, araç, Grup veya kullanıcı Arabirimine eklemekte olduğunuz komut gösterir.  
  
     Her `IDSymbol` öğe, ayarladığınız `name` öznitelik adına karşılık gelen menü, Grup veya komutu belirtmek için kullanın ve ardından `value` öğesi komut kimliğini temsil edecek bir onaltılık sayı. Hiçbir iki `IDSymbol` aynı üst öğeye sahip öğeleri aynı değere sahip olabilir.  
  
3.  Herhangi bir UI öğelerinizi simgeler gerektiriyorsa, ekleme bir `IDSymbol` öğe için her bir simgenin `GuidSymbol` , görüntü deposu temsil eden öğe.  
  
### <a name="putting-ui-elements-in-the-ide"></a>Kullanıcı Arabirimi öğeleri IDE'de koyma  
 [Menüleri](../../extensibility/menus-element.md) öğesi [grupları](../../extensibility/groups-element.md) öğesi ve [düğmeleri](../../extensibility/buttons-element.md) öğe tüm menüleri, grupları ve paketinizdeki tanımlanan komutları için tanımları içerir. Bu menü, gruplar ve komutlar kullanarak ya da IDE'de put bir [üst](../../extensibility/parent-element.md) kullanarak veya UI öğesi tanımının bir parçası olan öğenin bir [CommandPlacement](../../extensibility/commandplacement-element.md) öğesi başka bir yerde tanımlanmış.  
  
 Her `Menu`, `Group`, ve `Button` öğeye sahip bir `guid` özniteliğini ve bir `id` özniteliği. Her zaman `guid` adını eşleştirmek için öznitelik `GuidSymbol` komutu temsil eden öğe yapmak ve `id` öznitelik adına `IDSymbol` , menü, Grup veya komututemsiledenöğe`Symbols`bölümü.  
  
##### <a name="to-define-ui-elements"></a>Kullanıcı Arabirimi öğeleri tanımlamak için  
  
1. Yeni menü, alt menüler, kısayol menüleri veya araç çubukları tanımlıyorsanız, ekleme bir `Menus` öğesine `Commands` öğesi. Ardından, her menüye oluşturulacak ekleyin bir [menü](../../extensibility/menu-element.md) öğesine `Menus` öğesi.  
  
    Ayarlama `guid` ve `id` özniteliklerini `Menu` öğesini ve ardından `type` istediğiniz menü türü için öznitelik. Ayrıca ayarlayabilir `priority` menünün göreli konum üst grubu oluşturmak için öznitelik.  
  
   > [!NOTE]
   >  `priority` Özniteliği araç çubukları ve bağlam menüleri için geçerli değildir.  
  
2. Visual Studio IDE'deki tüm komutları menüleri ve araç çubuklarını doğrudan alt komut gruplarınca barındırılması gerekir. Yeni menü veya araç çubukları IDE ekliyorsanız, bu yeni komut grubu içermesi gerekir. Görsel olarak komutlarınızı gruplayabilirsiniz, böylece var olan menüleri ve araç çubuklarını komut gruplarıyla da ekleyebilirsiniz.  
  
    Yeni komut gruplarını eklediğinizde, önce oluşturmanız gerekir bir `Groups` öğesini ve ardından eklemek bir [grubu](../../extensibility/group-element.md) her komut grubu için öğesi.  
  
    Ayarlama `guid` ve `id` öznitelikleri her `Group` öğesini ve ardından `priority` göreli konumunu üst menüde grubu oluşturmak için öznitelik. Daha fazla bilgi için [, yeniden kullanılabilir grupları düğmeler oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3. IDE için yeni komutlar ekliyorsanız, ekleme bir `Buttons` öğesine `Commands` öğesi. Ardından, her komut için ekleme bir [düğmesi](../../extensibility/button-element.md) öğesine `Buttons` öğesi.  
  
   1. Ayarlama `guid` ve `id` öznitelikleri her `Button` öğesini ve ardından `type` istediğiniz düğme türü için öznitelik. Ayrıca ayarlayabilir `priority` komutu göreli konumunu üst grubu oluşturmak için öznitelik.  
  
      > [!NOTE]
      >  Kullanım `type="button"` standart menü komutları ve araç çubuğu düğmeleri için.  
  
   2. İçinde `Button` öğe, Ekle bir [dizeleri](../../extensibility/strings-element.md) öğesini içeren bir [ButtonText](../../extensibility/buttontext-element.md) öğesi ve bir [CommandName](../../extensibility/commandname-element.md) öğesi. `ButtonText` Öğesi için menü öğesi ya da araç çubuğu düğmesi için araç ipucu metin etiketi sağlar. `CommandName` Öğesi de komut içinde kullanmak için komutu adını sağlar.  
  
   3. Komutunuz bir simge varsa, oluşturun bir [simgesi](../../extensibility/icon-element.md) öğesinde `Button` öğesi ve kümesi kendi `guid` ve `id` özniteliklerini `Bitmap` öğesi simgesi.  
  
      > [!NOTE]
      >  Araç çubuğu düğmeleri simgeler olması gerekir.  
  
      Daha fazla bilgi için [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
4. Simgeler, komutlardan herhangi birine ihtiyacınız varsa ekleme bir [bit eşlemler](../../extensibility/bitmaps-element.md) öğesine `Commands` öğesi. Ardından, her bir simgeyi ekleyin bir [bit eşlem](../../extensibility/bitmap-element.md) öğesine `Bitmaps` öğesi. Bit eşlem kaynağının konumunu belirttiğiniz budur. Daha fazla bilgi için [menü komutları ekleme simgeleri](../../extensibility/adding-icons-to-menu-commands.md).  
  
   Çoğu menüler, gruplar ve komutlar doğru yerleştirmek için ana öğe yapıdaki güvenebilirsiniz. Çok büyük komut kümesi veya bir menü, Grup veya komut birden fazla yerde görünmelidir, belirttiğiniz komut yerleştirme öneririz.  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>IDE içinde kullanıcı Arabirimi öğeleri yerleştirmek için ana öğe etmenin  
  
1. Tipik ana öğe için oluşturma bir `Parent` her öğe `Menu`, `Group`, ve `Command` paketinizdeki tanımlanan öğe.  
  
    Hedefi `Parent` öğedir menü veya menü içerecek grup, Grup veya komutu.  
  
   1.  Ayarlama `guid` öznitelik adına `GuidSymbol` komut kümesini tanımlayan öğe. Hedef öğe paketinizin bir parçası değilse, GUID karşılık gelen .vsct dosyasında tanımlanan söz konusu komut kümesi için kullanın.  
  
   2.  Ayarlama `id` eşleşecek şekilde öznitelik `id` hedef menüsü veya grubun özniteliği. Menüler ve Visual Studio tarafından sunulan grupları listesi için bkz. [GUID'leri ve kimlikleri, Visual Studio menülerinin](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) veya [GUID'leri ve kimlikleri, Visual Studio araç çubuklarının](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
   Çok sayıda IDE'de yerleştirmek için kullanıcı Arabirimi öğeleri varsa veya birden fazla yerde görünmesi gereken öğeler varsa, bunların yerleşimi tanımlayın [CommandPlacements](../../extensibility/commandplacements-element.md) öğesi, aşağıdaki adımlarda gösterildiği gibi.  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>IDE içinde kullanıcı Arabirimi öğeleri yerleştirmek için komut yerleştirmeyi kullanmak için  
  
1. Sonra `Commands` öğe, Ekle bir `CommandPlacements` öğesi.  
  
2. İçinde `CommandPlacements` öğesi ekleme bir `CommandPlacement` öğesi her menü, Grup veya yerleştirmek için komutu.  
  
    Her `CommandPlacement` öğesi veya `Parent` öğesi, tek bir IDE konumda bir menü, Grup veya komut yerleştirir. Bir kullanıcı Arabirimi öğesi yalnızca bir üste sahip olabilir, ancak birden çok komut yerleşimi sahip olabilir. Bir kullanıcı Arabirimi öğesi birden fazla konumda yerleştirmek için eklemek bir `CommandPlacement` her konum için öğesi.  
  
3. Ayarlama `guid` ve `id` öznitelikleri her `CommandPlacement` barındırma menü veya grubu, olduğu gibi öğe olduğu için bir `Parent` öğesi. Ayrıca `priority` göreli konumunu UI öğesi oluşturmak için öznitelik.  
  
   Ana öğe tarafından yerleştirme ve komut yerleştirme karıştırabilirsiniz. Ancak, çok büyük komut kümeleri için yalnızca komut yerleştirme kullanmanızı öneririz.  
  
### <a name="adding-specialized-behaviors"></a>Özel davranışlar ekleme  
 Kullanabileceğiniz [CommandFlag](../../extensibility/command-flag-element.md) öğeler örneğin menüler ve komutlar davranışını değiştirmek için görünümlerini ve Görünürlüğü değiştirmek için. Kullanarak bir komut görüntülendiğinde de etkileyebilirsiniz [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), veya klavye kısayollarını kullanarak [KeyBindings](../../extensibility/keybindings-element.md). Menüler ve komutlar zaten belirli bir türdeki yerleşik davranışları özelleştirilmiş.  
  
##### <a name="to-add-specialized-behaviors"></a>Özel davranışlar eklemek için  
  
1. Bir çözüm yüklendiğinde bir kullanıcı Arabirimi öğesi gibi belirli kullanıcı Arabirimi bağlamları içinde yalnızca görünür yapmak için görünürlük kısıtlamaları kullanın.  
  
   1.  Sonra `Commands` öğe, Ekle bir `VisibilityConstraints` öğesi.  
  
   2.  Her kullanıcı Arabirimi öğesi sınırlamak ekleme bir [Visibilityıtem](../../extensibility/visibilityitem-element.md) öğesi.  
  
   3.  Her `VisibilityItem` öğe, ayarladığınız `guid` ve `id` öznitelikleri menü, grubu veya komut ve ardından `context` tanımlandığı gibi istediğiniz kullanıcı Arabirimi bağlamına özniteliği <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> sınıfı. Daha fazla bilgi için [Visibilityıtem öğesi](../../extensibility/visibilityitem-element.md).  
  
2. Kod görünürlüğünü ya da bir kullanıcı Arabirimi öğesi kullanılabilirliğini ayarlamak için bir veya daha fazla aşağıdaki komut bayrakları kullanın:  
  
   - DefaultDisabled  
  
   - DefaultInvisible  
  
   - DynamicItemStart  
  
   - DynamicVisibility  
  
   - NoShowOnMenuController  
  
   - NotInTBList  
  
     Daha fazla bilgi için [Command Flag öğesi](../../extensibility/command-flag-element.md).  
  
3. Nasıl bir öğe görünür veya görünümünü dinamik olarak değiştirmenize değiştirmek için bir veya daha fazla aşağıdaki komut bayrakları kullanın:  
  
   - AlwaysCreate  
  
   - CommandWellOnly  
  
   - DefaultDocked  
  
   - DontCache  
  
   - DynamicItemStart  
  
   - FixMenuController  
  
   - IconAndText  
  
   - PICT  
  
   - StretchHorizontally  
  
   - TextMenuUseButton  
  
   - TextChanges  
  
   - TextOnly  
  
     Daha fazla bilgi için [Command Flag öğesi](../../extensibility/command-flag-element.md).  
  
4. Komutları aldığında, bir öğenin nasıl tepki verdiğini değiştirmek için bir veya daha fazla aşağıdaki komut bayrakları kullanın:  
  
   - AllowParams  
  
   - CaseSensitive  
  
   - CommandWellOnly  
  
   - Süzme  
  
   - NoAutoComplete  
  
   - NoButtonCustomize  
  
   - NoKeyCustomize  
  
   - NoToolbarClose  
  
   - PostExec  
  
   - RouteToDocs  
  
   - TextIsAnchorCommand  
  
     Daha fazla bilgi için [Command Flag öğesi](../../extensibility/command-flag-element.md).  
  
5. Menü bağımlı klavye kısayolu bir menü veya menü bir öğe eklemek için bir ve işareti karakter ekleyin ('& ') içinde `ButtonText` menü veya menü öğesi için öğesi. Üst menü açık olduğunda ve işareti izleyen karakterin etkin klavye kısayolu'dir.  
  
6. Bir menü bağımsız klavye kısayol için bir komut eklemek için kullanın [KeyBindings](../../extensibility/keybindings-element.md). Daha fazla bilgi için [KeyBinding öğesi](../../extensibility/keybinding-element.md).  
  
7. Menü metni yerelleştirmek için kullanmak `LocCanonicalName` öğesi. Daha fazla bilgi için [Strings öğesi](../../extensibility/strings-element.md).  
  
   Bazı menü ve düğme türlerine özel davranışları içerir. Aşağıdaki tabloda, bazı özel menü ve düğme türleri açıklanmaktadır. Diğer türleri için bkz: `types` özniteliği açıklamasında [menü öğesi](../../extensibility/menu-element.md), [Button öğesi](../../extensibility/button-element.md), ve [Combos öğesi](../../extensibility/combo-element.md).  
  
   Birleşik giriş kutusu  
   Birleşik giriş kutusu araç çubuğunda kullanılabilir açılır bir listesidir. Birleşik giriş kutuları için kullanıcı Arabirimi eklemek için oluşturun bir [Combos](../../extensibility/combos-element.md) öğesinde `Commands` öğesi. Daha sonra ekleyin `Combos` öğesi bir `Combo` eklemek her bir birleşik giriş kutusu için öğesi. `Combo` öğelere sahip aynı öznitelikleri ve alt öğeleri olarak `Button` öğeleri ve ayrıca `DefaultWidth` ve `idCommandList` öznitelikleri. `DefaultWidth` Özniteliği genişliğini piksel cinsinden ayarlar ve `idCommandList` özniteliği işaret birleşik giriş kutusunu doldurmak için kullanılan bir komut kimliği. Daha fazla bilgi için `Combo` öğesi belgeleri.  
  
   MenuController  
   Bir menü denetleyicisi yanındaki ok bulunan bir düğme değil. Oka tıklayarak bir listesi açılır. Menü denetleyicisi için kullanıcı Arabirimi eklemek için oluşturun bir `Menu` öğesi ve kümesi kendi `type` özniteliğini **MenuController** veya **MenuControllerLatched**istediğiniz davranışı bağlı olarak. Menü denetleyicisi doldurmak için üst öğesi olarak ayarlanmış bir `Group` öğesi. Menü denetleyicisi bu grubun tüm alt öğeleri, aşağı açılan listede görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Menüleri ve komutlari genişletme komutları](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)

