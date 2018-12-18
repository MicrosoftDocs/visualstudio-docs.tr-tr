---
title: XML komut tablosu tasarlama (. Vsct) dosyaları | Microsoft Docs
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
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c7a4e07c45c5d651af057e1eb33c23d37601cb3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762812"
---
# <a name="designing-xml-command-table-vsct-files"></a>XML komut tablosu tasarlama (. Vsct) dosyaları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage için komut öğelerin Görünüm ve düzeninin bir XML komut tablosu (.vsct) dosyası açıklar. Düğmeler, birleşik giriş kutuları, menüler, araç çubukları ve grupları komut öğelerinin komut öğeler içerir. Bu konuda, XML komut tablosu dosyaları, komut öğeleri ve menüler nasıl etkilediklerini ve bunların nasıl oluşturulacağı açıklanmaktadır.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Komutlar, menüler, grupları ve .vsct dosyası  
 .vsct dosyaları komutlar, menüler ve komut gruplarını düzenlenmiştir. .Vsct dosyası XML etiketlerini komut düğmeleri, komut yerleştirme ve bit eşlemler gibi diğer ilişkili öğeleri ile birlikte bu öğelerin her birini temsil eder.  
  
 Çalıştırarak yeni bir VSPackage'ı oluşturduğunuzda [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] paketi şablonu şablon gerekli öğelerle .vsct dosyası için bir menü komutu, araç penceresi ya da özel bir düzenleyici, seçimlerinize bağlı olarak oluşturur. Bu .vsct dosyası, belirli bir VSPackage gereksinimlerini karşılamak için daha sonra değiştirilebilir. .Vsct dosyası değiştirme örnekleri görmek için örneklerde [genişletme menüler ve komutlar](../../extensibility/extending-menus-and-commands.md).  
  
 Yeni, boş .vsct dosyası oluşturma için bkz: [nasıl yapılır: oluşturma bir. Vsct dosya](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). XML öğeleri, öznitelikleri ve değerleri oluşturulduktan sonra komut öğesi düzeni tanımlamak için dosyaya ekleyin. Ayrıntılı bir XML şeması için bkz: [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc ve .vsct dosyaları arasındaki farklar  
 Şimdi de .ctc dosya biçimi kullanım dışı olarak anlamı .vsct dosyası XML etiketleri arkasındaki aynı olsa da, kendi uygulama biraz farklıdır.  
  
- Yeni  **\<extern >** etikettir yönelik olanlar gibi derlenecek diğer .h dosyaları burada başvuru [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] araç çubuğu.  
  
- .Vsct dosyaları desteği sırada **/ include** deyimi .ctc dosyalarında olduğu gibi ayrıca özelliklerine yeni \< **alma >** öğesi. Fark, **/ include** getirir **tüm** bilgileri ancak \< **Al >** adları yalnızca getirir.  
  
- Önişlemci yönergeleri, tanımladığınız bir üstbilgi dosyası .ctc dosyalar gerektirir, ancak bir .vsct dosyaları için gerekli değildir. Bunun yerine, yönergeleri bulunan sembol tablosu yerleştirin  **\<Sembol >** .vsct dosyası alt kısmında bulunan öğeleri.  
  
- .vsct dosyaları özelliği bir  **\<ek açıklama >** istediğiniz notları veya hatta resimler gibi herhangi bir bilgi eklemeye izin veren bir etiket.  
  
- Değerler, öğenin öznitelikleri olarak depolanır.  
  
- Komut bayrakları ayrı ayrı depolanır veya yığın.  Ancak, IntelliSense, yığılmış komut bayrakları çalışmaz. Komut bayrakları hakkında daha fazla bilgi için bkz: [Command Flag öğesi](../../extensibility/command-flag-element.md).  
  
- Bölünmüş bırakmalar, combos vb. gibi birden çok tür belirtebilirsiniz.  
  
- GUID'ler doğrulamaz.  
  
- Her kullanıcı Arabirimi öğesi ile görüntülenen metinleri temsil eden bir dize var.  
  
- Üst isteğe bağlıdır. Atlanırsa, "Grup Bilinmeyen" değeri kullanılır.  
  
- Simge bağımsız değişken isteğe bağlıdır.  
  
- Artık bir dosya adı tarafından vsct.exe derleyici derleme zamanında çekilir href aracılığıyla belirtebilirsiniz dışında bit eşlem bölüm--bir .ctc aynı dosya.  
  
- ResID--eski bit eşlemi kaynak kimliği, kullanılabilir ve hala aynı .ctc dosyaları olduğu gibi çalışır.  
  
- HRef--bit eşlem kaynağı için bir dosya adı belirtmek izin veren yeni bir yöntem. Kullanılan bölümüne atlayabilirsiniz. böylece tüm kullanılan olduğunu varsayar. Derleyici öncelikle yerel kaynakları için tüm ağ paylaşımları üzerinde dosya ve /ı anahtar tarafından tanımlanan tüm kaynakları arar.  
  
- Tuş--Artık bir öykünücü belirtmeniz gerekir. Bir belirtirseniz, derleyicinin düzenleyici ve öykünücü aynı olduğu varsayılır.  
  
- Keychord--bırakıldı. Yeni biçimi Key1, Değişiklik1, Key2, Mod2 şeklindedir.  Bir karakter, onaltılık veya VK sabiti belirtebilirsiniz.  
  
  Yeni derleyici, vsct.exe, .ctc hem .vsct dosyaları derler. Eski ctc.exe derleyicinin ancak tanımak ne .vsct dosyaları derleyin.  
  
  Varolan .cto dosyasını bir .vsct dosyasına dönüştürmek için vsct.exe derleyici kullanabilirsiniz. Bu konu hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma bir. Vsct mevcut bir dosya. Cto dosya](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>.Vsct dosyası öğeleri  
 Komut tablosu aşağıdaki hiyerarşi ve öğeleri sahiptir:  
  
 [CommandTable öğesi](../../extensibility/commandtable-element.md) — tüm komutlar, menü grupları ve menüler VSPackage'ı ile ilişkili temsil eder.  
  
 [Extern öğesi](../../extensibility/extern-element.md) — .vsct dosyası ile birleştirmek istediğiniz herhangi bir dış .h dosyaları başvuruyor.  
  
 [Öğe dahil](../../extensibility/include-element.md) — birlikte your.vsct dosyasını derlemek için istediğiniz herhangi bir ek üstbilgi (.h) dosyaları başvuruyor. .Vsct dosyası komutlarını, menü grupları ve menüler IDE veya başka bir VSPackage sağlayan tanımlayan sabitler içeren .h dosyaları dahil edebilirsiniz.  
  
 [Komutlar öğenin](../../extensibility/commands-element.md) — tüm yürütülebilecek tek tek komutlarla temsil eder. Her komut aşağıdaki dört alt öğeleri içerir:  
  
 [Menus öğesi](../../extensibility/menus-element.md) — tüm menüleri ve araç çubuklarını VSPackage'ı temsil eder. Menü komutları grupları için kapsayıcılardır.  
  
 [Öğe gruplandırır](../../extensibility/groups-element.md) — tüm grupları VSPackage'ı temsil eder. Grupları tek tek komutlarla koleksiyonlarıdır.  
  
 [Buttons öğesi](../../extensibility/buttons-element.md) — tüm komut düğmeleri ve menü öğeleri VSPackage'ı temsil eder. Düğme komutları ile ilişkilendirilebilen visual denetimlerdir.  
  
 [Bitmaps öğesi](../../extensibility/bitmaps-element.md) — tüm bit eşlemler tüm düğmelerin VSPackage'ı temsil eder. Bit eşlemler yanındaki veya bağlama komut düğmeleri görüntüleme resimleri ' dir.  
  
 [CommandPlacements öğesi](../../extensibility/commandplacements-element.md) — burada tek tek komutlarla tarihli, VSPackage menülerde ek konumları belirtir.  
  
 [VisibilityConstraints öğesi](../../extensibility/visibilityconstraints-element.md) — olup olmadığı bir komut görüntüler hiç zaman ya da belirli bir iletişim kutusu veya pencere görüntülendiğinde gibi yalnızca belirli bağlamlarda, belirtir. Belirtilen bağlamı etkin olduğunda, menüler ve bu öğe için bir değere sahip komutlar görüntülenir. Komutu her zaman görüntülemek için varsayılan davranıştır.  
  
 [KeyBindings öğesi](../../extensibility/keybindings-element.md) — komutlar için herhangi bir tuş bağlamaları belirtir. Gibi bir komut yürütmek için basılması gereken diğer bir deyişle, bir veya daha fazla anahtar birleşimlerini **CTRL + S**.  
  
 [UsedCommands öğesi](../../extensibility/usedcommands-element.md) — Informs [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ortamı geçerli VSPackage'ı etkin olduğunda belirtilen komut başka kod tarafından uygulanan olsa da, bu komutu uygulamasını sağlar.  
  
 `Symbols Element` — Komutlarınızın paketteki tüm GUID kimlikleri ve sembol adlarını içerir.  
  
## <a name="vsct-file-design-guidelines"></a>. Vsct dosya tasarım yönergeleri  
 .Vsct dosyası başarıyla tasarlamak için aşağıdaki yönergeleri izleyin.  
  
-   Komutları yalnızca gruplarda bulunabilecek gruplar yalnızca menülerde yerleştirilebilir ve menüler yalnızca gruplarında yerleştirilebilir. Yalnızca menüler IDE, gruplar aslında görüntülenir ve komutları değildir.  
  
-   Alt menüye doğrudan atanamaz ancak menüye sırayla atandığı bir gruba atanması gerekir.  
  
-   Bir ana öğe grubu veya üst alanın kendi tanımlayan yönergesi kullanarak menü komutları, alt menüler ve gruplar atanabilir.  
  
-   Bir komut tablosu yalnızca yönergeleri üst alanları düzenleme önemli sınırlama vardır. Nesneleri tanımlayan yönergeleri, yalnızca bir üst bağımsız değişken alabilir.  
  
-   Komutları, grupları veya alt menüler yeniden kullanmak, kendi ile nesnesinin yeni bir örneğini oluşturmak için yeni bir yönerge kullanılmasını gerektiren `GUID:ID` çifti.  
  
-   Her `GUID:ID` çifti benzersiz olmalıdır. Örneğin, bir araç çubuğunda bir menü veya bağlam menüsünde yerleştirilen bir komutu yeniden tarafından işlenir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi.  
  
-   Komutlar ve alt menülere de atanabilir birden çok gruba ve grupları kullanarak birden çok menüleri atanabilir [komutlar öğenin](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Vsct dosya notları  
 .Vsct dosyası için herhangi bir değişiklik yaparsanız, derlemeniz hem yerel bir uydu DLL yerleştirin sonra çalıştırmalısınız **devenv.exe/Setup /nosetupvstemplates**. Bunun yapılması, Deneysel kayıt defterini okunmasına ve açıklayan iç veritabanını belirtilen VSPackage kaynakları zorlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] derlenmeye.  
  
 Geliştirme sırasında oluşturulması ve IDE kafa karıştırıcı dağınıklığı açabilir Deneysel kayıt defteri kovanında kayıtlı VSPackage birden çok proje için mümkündür. Bu sorunu gidermek için Deneysel hive tüm kayıtlı VSPackages ve IDE yaptığınız değişiklikleri kaldırmak için varsayılan ayarları sıfırlayabilirsiniz. Deneysel hive sıfırlamak için Visual Studio SDK ile birlikte gelen CreateExpInstance.exe aracını kullanın. Konumunda bulabilirsiniz  
  
 **%PROGRAMFILES(x86)%\Visual Studio \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Komut satırını kullanarak aracı çalıştırın **Createexpınstance reset**. Bu araç normalde ile yüklenen tüm kayıtlı VSPackages Deneysel kovanından kaldırır unutmayın [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Menüleri ve Komutlari Genişletme](../../extensibility/extending-menus-and-commands.md)

