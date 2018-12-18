---
title: Komutları kullanılabilir yapma | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1292dc3879effa53f3b4a41b87374a3a5f46ff0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857139"
---
# <a name="making-commands-available"></a>Komutları Kullanılabilir Yapma
Visual Studio için birden çok VSPackages eklendiğinde, kullanıcı arabirimi (UI) komutları ile overcrowded haline gelir. Bu sorun şu şekilde azaltmaya yardımcı olmak için paket programlama yapabilirsiniz:

-   Program paket yalnızca bir kullanıcı yüklenmesi gerekir.

-   Yalnızca geçerli durumu tümleşik geliştirme ortamının (IDE) bağlamında bunlar gerekebilir, kendi komutlar böylece paket program.

## <a name="delayed-loading"></a>Gecikmeli yükleme
 Etkinleştirmek için tipik Gecikmeli yükleme VSPackage'ı, komutları kullanıcı Arabiriminde görüntülenir, ancak bir kullanıcı komutlardan birini tıklayana kadar paketi yüklenmedi olacağı şekilde tasarlayın yöntemdir. .Vsct dosyası içinde bunu gerçekleştirmek için komut bayraklarınız komutları oluşturun.

 Aşağıdaki örnek, bir menü komutu .vsct dosyası tanımı gösterilmektedir. Bu, Visual Studio Paket şablon tarafından oluşturulan komuttur olduğunda **menü komutu** şablondaki seçeneğinin işaretli.

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

Örnekte, üst grup `MyMenuGroup`, olduğu gibi bir alt öğesi bir üst düzey menü **Araçları** menüsünde, komut, menüde görünmez, ancak komut tıklanana kadar komutu yürütür paketi yüklü değil bir kullanıcı tarafından. Ancak, programlama uygulamak için komutu tarafından <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi, menü komutu içeren ilk genişletildiğinde yüklenecek paket etkinleştirebilirsiniz.

Gecikmeli yüklemeyi başlatma performansını iyileştirebilir dikkat edin.

## <a name="current-context-and-the-visibility-of-commands"></a>Geçerli bağlamı ve komutların görünürlüğünü
 VSPackage komutları görünür veya gizli VSPackage veri veya şu anda ilgili eylemleri geçerli durumuna bağlı olarak olmasını bildirebilirsiniz. VSPackage'ı, komutları durumunu genellikle bir uygulaması kullanarak ayarlamak etkinleştirebilirsiniz <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> yönteminden <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi, ancak bu kodu yürütmeden önce yüklenecek VSPackage'ı gerektirir. Bunun yerine, paketi yüklenmeden komutların görünürlüğünü yönetmek IDE etkinleştirmenizi öneririz. .Vsct dosyası içinde Bunu yapmak için bir veya daha fazla özel kullanıcı Arabirimi bağlamlarla komutları ilişkilendirin. Bu UI bağlamı olarak bilinen bir GUID tanımlanır bir *komut bağlam GUID*.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir proje yüklenirken veya oluşturmaya devam düzenlemesini gibi kullanıcı eylemlerini sonucunda değişiklikleri izler. Değişiklikler oldukça IDE görünümünü otomatik olarak değiştirilir. Aşağıdaki tabloda, IDE'nin dört ana bağlamları değiştirme gösterilmektedir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] izleyiciler.


| İçerik türü | Açıklama |
|-------------------------| - |
| Etkin proje türü | Çoğu proje türleri için bu `GUID` değer: Proje uygulayan VSPackage GUID ile aynı. Ancak, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projeler, proje türü kullanmak `GUID` değeri. |
| Etkin pencere | Genellikle, tuş bağlamaları geçerli UI bağlamı oluşturur son etkin belge penceresini budur. Ancak, iç Web tarayıcısı benzer bir anahtar bağlaması tablo içeren bir araç penceresi da kaynaklanıyor olabilir. HTML düzenleyicisi gibi birden çok sekmeli belge pencereleri için farklı komut bağlam her sekme sahip `GUID`. |
| Etkin dil hizmeti | Bir metin düzenleyicisinde görüntülenmekte dosya ile ilişkilendirilmiş dil hizmeti. |
| Etkin araç penceresi | Açıksa ve odaktaysa araç penceresi. |

 Beşinci bir ana içerik alanı IDE'nin UI durumudur. UI bağlamı etkin komut bağlam tarafından tanımlanan `GUID`s, aşağıdaki gibi:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

Bu Guıd'lar, etkin veya devre dışı, IDE geçerli durumuna bağlı olarak işaretlenir. Aynı anda birden fazla UI bağlamı etkin olabilir.

### <a name="hiding-and-displaying-commands-based-on-context"></a>Bağlama göre komutları görüntüleme ve gizleme
 Görüntüleyebilir ya da bir paket komut IDE'de paketi yüklenmeden gizleyebilirsiniz. Bunu yapmak için komut içinde paket .vsct dosyası kullanarak tanımlarsınız `DefaultDisabled`, `DefaultInvisible`, ve `DynamicVisibility` komut bayrakları ve ekleyerek bir veya daha fazla [Visibilityıtem](../../extensibility/visibilityitem-element.md) öğelerine [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) bölümü. Belirtilen komut bağlam olduğunda `GUID` olur etkin komut paketi yüklenmeden görüntülenir.

### <a name="custom-context-guids"></a>Özel bağlam GUID'leri
 GUID zaten tanımlı değil bir uygun komut bağlamı ise, VSPackage birinde tanımlayabilir ve etkin veya etkin değil olarak komutlarınızı görünürlüğünü denetleme için gerekli olması için program. Kullanım <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> hizmet için:

-   Bağlam GUID'leri kaydetme (çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> yöntemi).

-   Bir bağlam durumunu alma `GUID` (çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> yöntemi).

-   Bağlam kapatma `GUID`s açma ve kapatma (çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> yöntemi).

    > [!CAUTION]
    > Diğer VSPackage'ları bunlara bağımlı çünkü, VSPackage'ı tüm mevcut bir bağlamı GUID durumunu etkilemez emin olun.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bir VSPackage komutunun VSPackage'ı yüklemeden komut bağlamları tarafından yönetilen bir komut dinamik görünürlüğünü gösterir.

 Komutu, etkinleştirilmeli ve çözüm bulunduğunda gösterilen şekilde ayarlayın; diğer bir deyişle, zaman, aşağıdaki komut bağlam GUID'leri biridir etkin:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Örnekte, her komut bayrağı ayrı bir fark [komut bayrağı](../../extensibility/command-flag-element.md) öğesi.

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

Ayrıca her UI bağlamı ayrı bir verilmelidir bildirimi `VisibilityItem` aşağıdaki gibi bir öğe.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VSPackage’larda Komut Yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)
- [Dinamik Olarak Menü Öğeleri Ekleme](../../extensibility/dynamically-adding-menu-items.md)
