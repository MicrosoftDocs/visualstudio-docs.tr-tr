---
title: 'Nasıl yapılır: kısayol menüsüne komut ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: cd550399-05fc-4dbf-be4c-f5094bb752ce
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e7d15c1991ee70a0b1a163c8968e42fe450b7919
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833531"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Nasıl yapılır: Kısayol Menüsüne Komut Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıcılarınız için DSL'nizi özel görevleri gerçekleştirebilmeleri için menü komutlarını, etki alanına özgü dil (DSL) ekleyebilirsiniz. Kullanıcı diyagramda sağ tıkladığınızda komutlar (kısayol) bağlam menüsünde görünür. Böylece yalnızca belirli durumlarda menüsünde görünen komut tanımlayabilirsiniz. Yalnızca kullanıcı belirli türlerini öğenin veya öğelerin belirli durumlarda tıkladığında gibi komut görünür yapabilirsiniz.  
  
 Özet olarak, adımları DslPackage projesinde aşağıdaki gibi gerçekleştirilir:  
  
1. [Komut içinde Commands.vsct bildirme](#VSCT)  
  
2. [Package.tt paketinin sürüm numarasını güncelleştirmek](#version). Commands.vsct değiştirdiğinizde, bunu yapmak sahip olduğunuz  
  
3. [CommandSet sınıfı yöntemleri yazma](#CommandSet) komutu görünür yapmak ve komut yapmak istediğinizi tanımlayabilirsiniz.  
  
   Örnekler için bkz: [Görselleştirme ve modelleme SDK'sı Web sitesi](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
> [!NOTE]
>  Kesme, yapıştırma, Tümünü Seç ve yazdırma gibi bazı mevcut komutları davranışını CommandSet.cs yöntemleri geçersiz kılarak de değiştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="defining-a-command-using-mef"></a>MEF kullanarak bir komut tanımlama  
 Yönetilen uzantı çerçevesi (MEF) diyagram menüsünden menü komutlarını tanımlama alternatif bir yöntem sağlar. Birincil amacı, sizin tarafınızdan veya diğer üçüncü taraflarca genişletilmesi DSL etkinleştirmektir. Kullanıcılar yalnızca DSL yüklemeyi seçebilirsiniz veya DSL ve uzantılarını yükleyebilirsiniz. Ancak, MEF MEF DSL üzerinde etkinleştirmek için ilk iş sonra kısayol menü komutlarını tanımlama işlemlerini de azaltır.  
  
 Yöntemi, bu konudaki kullanın:  
  
1. Sağ tıklama kısayol menüsünü dışında menülerde menü komutları tanımlamak istersiniz.  
  
2. Komutları belirli gruplandırmalarını menüde tanımlamak istersiniz.  
  
3. Diğerleri kendi komutlarla DSL genişletmek etkinleştirmek istediğiniz değil.  
  
4. Yalnızca tek bir komutta tanımlamak istersiniz.  
  
   Aksi takdirde, komutları tanımlamak için MEF yöntemi kullanmayı düşünün. Daha fazla bilgi için [MEF kullanarak DSL'nizi genişletme](../modeling/extend-your-dsl-by-using-mef.md).  
  
##  <a name="VSCT"></a> Komut içinde Commands.Vsct bildirme  
 Menü komutları DslPackage\Commands.vsct bildirilir. Bu tanımları, etiket menü öğelerinin ve menülerde göründüğü belirtin.  
  
 Düzenleme, dosya Commands.vsct, tanımları dizininde yer alan çeşitli .h dosyaları alır *Visual Studio SDK'sını yükleme yolu*\VisualStudioIntegration\Common\Inc. Ayrıca, DSL tanımını oluşturan GeneratedVsct.vsct içerir.  
  
 .Vsct dosyaları hakkında daha fazla bilgi için bkz. [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
#### <a name="to-add-the-command"></a>Komut ekleme  
  
1.  İçinde **Çözüm Gezgini**altında **DslPackage** proje, Commands.vsct açın.  
  
2.  İçinde `Commands` öğesi, bir veya daha fazla düğme ve bir grup tanımlayın. A *düğmesi* menüsünde bir öğedir. A *grubu* menüde bir bölümdür. Bu öğeleri tanımlamak için aşağıdaki öğeleri ekleyin:  
  
    ```  
    <!-- Define a group - a section in the menu -->  
    <Groups>  
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">  
        <!-- These symbols are defined in GeneratedVSCT.vsct -->  
        <Parent guid="guidCmdSet" id="menuidContext" />  
      </Group>  
    </Groups>  
    <!-- Define a button - a menu item - inside the Group -->  
    <Buttons>  
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"  
        priority="0x0100" type="Button">  
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>  
        <!-- If you do not want to place the command in your own Group,   
             use Parent guid="guidCmdSet" id="grpidContextMain".  
             These symbols are defined in GeneratedVSCT.vsct -->  
        <CommandFlag>DynamicVisibility</CommandFlag>  
        <Strings>  
          <ButtonText>My Context Menu Command</ButtonText>  
        </Strings>  
      </Button>  
    </Buttons>  
    ```  
  
    > [!NOTE]
    >  Her bir düğme veya grubu bir tamsayı kimliği bir GUID ile tanımlanır Çeşitli gruplar ve düğmeleri aynı GUID ile oluşturabilirsiniz. Ancak, farklı kimlikleri olması gerekir. GUID adlarına ve kimliği adları gerçek GUID'leri ve kimlikleri sayısal çevrilir `<Symbols>` düğümü.  
  
3.  Komutu için görünürlük kısıtlama ekleyebilirsiniz, böylece yalnızca, etki alanına özgü dil bağlamında yüklenir. Daha fazla bilgi için [VisibilityConstraints öğesi](../extensibility/visibilityconstraints-element.md).  
  
     Bunu yapmak için aşağıdaki öğeleri ekleyin `CommandTable` öğeden sonra `Commands` öğesi.  
  
    ```  
    <VisibilityConstraints>  
      <!-- Ensures the command is only loaded for this DSL -->  
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"  
        context="guidEditor"/>  
    </VisibilityConstraints>  
    ```  
  
4.  GUID'leri ve kimlikleri için kullanılan adları tanımlayın. Bunu yapmak için bir `Symbols` öğesinde `CommandTable` öğeden sonra `Commands` öğesi.  
  
    ```  
    <Symbols>  
      <!-- Substitute a unique GUID for the placeholder: -->  
      <GuidSymbol name="guidCustomMenuCmdSet"  
        value="{00000000-0000-0000-0000-000000000000}" >  
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>  
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>  
      </GuidSymbol>  
    </Symbols>  
    ```  
  
5.  Değiştirin `{000...000}` grupları ve menü öğeleri tanımlayan GUID. Yeni bir GUID almak için kullanın **GUID Oluştur** aracındaki **Araçları** menüsü.  
  
    > [!NOTE]
    >  Daha fazla grup veya menü öğeleri eklerseniz, aynı GUID kullanabilirsiniz. İçin yeni değerler ancak kullanmalıdır `IDSymbols`.  
  
6.  Bu yordamdan kopyaladığınız kodunda kendi dizelerle aşağıdaki dizelerden her örneğini değiştirin:  
  
    -   `grpidMyMenuGroup`  
  
    -   `cmdidMyContextMenuCommand`  
  
    -   `guidCustomMenuCmdSet`  
  
    -   `My Context Menu Command`  
  
##  <a name="version"></a> Paket sürümünü Package.tt güncelleştirin  
 Eklediğinizde veya değiştirdiğinizde bir komutu her güncelleştirme `version` parametresinin <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> uygulanan paket sınıfına, etki alanına özgü dili yeni sürümünü yayımlamadan önce.  
  
 Paket sınıfı oluşturulan dosyada tanımlı olduğundan, öznitelik Package.cs dosyasını oluşturur ve metin şablon dosyasındaki güncelleştirin.  
  
#### <a name="to-update-the-packagett-file"></a>Package.tt dosyayı güncelleştirmek için  
  
1.  İçinde **Çözüm Gezgini**, **DslPackage** içinde proje **GeneratedCode** klasöründe Package.tt dosyasını açın.  
  
2.  Bulun `ProvideMenuResource` özniteliği.  
  
3.  Artırma `version` özniteliğinin ikinci parametresi, parametre. İsterseniz, kendi amacı, açıkça anımsatması için parametre adı yazabilirsiniz. Örneğin:  
  
     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`  
  
##  <a name="CommandSet"></a> Komutun davranışını tanımlayın  
 DSL'nizi DslPackage\GeneratedCode\CommandSet.cs içinde bildirilen kısmi bir sınıf içinde uygulanan bazı komutlar zaten var. Yeni komut eklemek için aynı sınıfın bir kısmi bildirimi içeren yeni bir dosya oluşturarak bu sınıfı genişletmeniz gerekir. Sınıf genellikle adıdır  *\<YourDslName >*`CommandSet`. Sınıfın adı doğrulanıyor ve içeriğini incelemek kullanışlıdır.  
  
 Komut kümesi sınıfı türetilen <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.  
  
#### <a name="to-extend-the-commandset-class"></a>CommandSet sınıfı genişletmek için  
  
1.  DslPackage projesindeki Çözüm Gezgini'nde GeneratedCode klasörü açın ve konum altında CommandSet.tt CommandSet.cs oluşturulan dosyasını açabilir. Ad alanı ve orada tanımladığınız ilk sınıf adını not edin. Örneğin, aşağıdaki görebilirsiniz:  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2.  İçinde **DslPackage**, adlı bir klasör oluşturma **özel kod**. Adlı yeni bir sınıf dosyası bu klasörde, oluşturma `CommandSet.cs`.  
  
3.  Yeni dosyanın, aynı ad alanı ve üretilen kısmi sınıf ada sahip bir kısmi bildirimi yazın. Örneğin:  
  
     `namespace Company.Language1 /* Make sure this is correct */`  
  
     `{ internal partial class Language1CommandSet { ...`  
  
     **Not** yeni dosyayı oluşturmak için bir sınıf şablonunda kullandıysanız, hem ad alanı ve sınıf adını düzeltmeniz gerekir.  
  
### <a name="extend-the-command-set-class"></a>Komut kümesi sınıfını genişletir  
 Komut kümesi kodunuz, genellikle aşağıdaki ad alanlarını içe aktarmanız gerekir:  
  
```  
using System;  
using System.Collections.Generic;  
using System.ComponentModel.Design;   
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Shell;  
```  
  
 Ad alanı ve oluşturulan CommandSet.cs içindeki alanlarla eşleşmesi için sınıf adını ayarlayın:  
  
```  
namespace Company.Language1 /* Make sure this is correct */  
{  
  // Same class as the generated class.  
  internal partial class Language1CommandSet   
  {  
```  
  
 Komut ne zaman bağlam menüsü ve diğer komutu gerçekleştirmeyi görünür olacağını belirlemek için iki yöntem tanımlamak zorunda. Bu yöntemler, geçersiz kılmalar değildir; Bunun yerine, bunları komutların listesini kaydedin.  
  
### <a name="define-when-the-command-will-be-visible"></a>Komut zaman görünür olacağını tanımlayın  
 Her komut için tanımlayan bir `OnStatus...` olup komut menüsünde görünür ve olup, etkinleştirilecek veya devre dışı belirleyen yöntemi. Ayarlama `Visible` ve `Enabled` özelliklerini `MenuCommand`aşağıdaki örnekte gösterildiği gibi. Bu yöntem, hızlı çalışması gerekir, böylece kullanıcı diyagramda sağ tıkladığı her seferinde kısayolunu oluşturmak için çağrılır.  
  
 Bu örnekte, yalnızca kullanıcı belirli bir tür şeklinin seçilmiş ve yalnızca seçilen öğeleri en az biri belirli bir durumda olduğunda etkin olduğunda komut görülebilir. Örneğin, sınıf diyagramı DSL şablonunu temel alıyorsa ve ClassShape ve ModelClass DSL içinde tanımlanan türleri şunlardır:  
  
```  
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)  
{  
  MenuCommand command = sender as MenuCommand;  
  command.Visible = command.Enabled = false;  
  foreach (object selectedObject in this.CurrentSelection)  
  {  
    ClassShape shape = selectedObject as ClassShape;  
    if (shape != null)  
    {  
      // Visibility depends on what is selected.  
      command.Visible = true;  
      ModelClass element = shape.ModelElement as ModelClass;  
      // Enabled depends on state of selection.  
      if (element != null && element.Comments.Count == 0)  
      {  
        command.Enabled = true;  
        return; // seen enough  
} } } }  
```  
  
 Aşağıdaki parçası sık OnStatus yöntemleri kullanışlıdır:  
  
- `this.CurrentSelection`. Kullanıcı sağ şekli, her zaman bu listede bulunuyor. Diyagram kullanıcı diyagramın boş bir kısmına tıklarsa, listeyi yalnızca üyesidir.  
  
- `this.IsDiagramSelected()` - `true` Kullanıcı diyagramın boş bir kısmına tıkladıysanız.  
  
- `this.IsCurrentDiagramEmpty()`  
  
- `this.IsSingleSelection()` -Kullanıcı birden çok nesne seçin  
  
- `this.SingleSelection` -Şekil veya kullanıcı sağ diyagramı  
  
- `shape.ModelElement as MyLanguageElement` -bir şekil tarafından temsil edilen model öğesi.  
  
  Genel bir kural olarak olun `Visible` özelliği ne seçili olursa bağlıdır ve olun `Enabled` özelliği, seçilen öğeleri durumuna bağlıdır.  
  
  OnStatus yöntemi Store durumunu değiştirmemesi gerekir.  
  
### <a name="define-what-the-command-does"></a>Komutun yaptığı tanımlayın  
 Her komut için tanımlayan bir `OnMenu...` kullanıcı komutu tıkladığında, gerekli bir eylem gerçekleştiren yöntemi.  
  
 Model öğelerine değişiklik yaparsanız, bir işlem içinde bunu yapmanız gerekir. Daha fazla bilgi için [nasıl yapılır: bir standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
 Bu örnekte, `ClassShape`, `ModelClass`, ve `Comment` sınıf diyagramı DSL şablondan türetilmiş DSL içinde tanımlanan türleridir.  
  
```  
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)  
{  
  MenuCommand command = sender as MenuCommand;  
  Store store = this.CurrentDocData.Store;  
  // Changes to elements and shapes must be performed in a Transaction.  
  using (Transaction transaction =  
       store.TransactionManager.BeginTransaction("My command"))  
  {  
    foreach (object selectedObject in this.CurrentSelection)  
    {  
      // ClassShape is defined in my DSL.  
      ClassShape shape = selectedObject as ClassShape;  
      if (shape != null)  
      {  
        // ModelClass is defined in my DSL.  
        ModelClass element = shape.ModelElement as ModelClass;  
        if (element != null)  
        {  
          // Do required action here - for example:  
  
          // Create a new element. Comment is defined in my DSL.  
          Comment newComment = new Comment(element.Partition);  
          // Every element must be the target of an embedding link.  
          element.ModelRoot.Comments.Add(newComment);  
          // Set properties of new element.  
          newComment.Text = "This is a comment";  
          // Create a reference link to existing object.  
          element.Comments.Add(newComment);  
        }  
      }  
    }  
    transaction.Commit(); // Don't forget this!  
  }  
}  
```  
  
 Nesne başka bir nesne modelde gezinme ve nesneler ve bağlantılar oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
### <a name="register-the-command"></a>Kayıt komutu  
 C# dilinde CommandSet.vsct sembolleri bölümde yaptığınız GUID ve ID değerleri bildirimlerini yineleyin:  
  
```  
private Guid guidCustomMenuCmdSet =   
    new Guid("00000000-0000-0000-0000-000000000000");  
private const int grpidMyMenuGroup = 0x01001;  
private const int cmdidMyContextMenuCommand = 1;  
```  
  
 Eklenen, aynı GUID değeri kullanın **Commands.vsct**.  
  
> [!NOTE]
>  VSCT dosyasının sembolleri bölümünü değiştirirseniz, ayrıca bu bildirimler eşleşecek şekilde değiştirmeniz gerekir. Ayrıca Package.tt sürüm numarası artmalıdır  
  
 Menü komutlarınızı bu komutu kümenin bir parçası olarak kaydedin. `GetMenuCommands()` Diyagram, başlatıldıktan sonra çağrılır:  
  
```  
protected override IList<MenuCommand> GetMenuCommands()  
{  
  // Get the list of generated commands.  
  IList<MenuCommand> commands = base.GetMenuCommands();  
  // Add a custom command:  
  DynamicStatusMenuCommand myContextMenuCommand =  
    new DynamicStatusMenuCommand(  
      new EventHandler(OnStatusMyContextMenuCommand),  
      new EventHandler(OnMenuMyContextMenuCommand),  
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));  
  commands.Add(myContextMenuCommand);  
  // Add more commands here.  
  return commands;  
}   
```  
  
## <a name="test-the-command"></a>Test et komutu  
 Yapı ve Visual Studio'nun deneysel örneğinde DSL çalıştırın. Komutu, belirttiğiniz durumlarda kısayol menüsünde görüntülenmelidir.  
  
#### <a name="to-exercise-the-command"></a>Komutunu kullanmak için  
  
1.  Üzerinde **Çözüm Gezgini** araç çubuğunda tıklatın **tüm Şablonları Dönüştür**.  
  
2.  Tuşuna **F5** çözümü yeniden oluşturun ve etki alanına özgü dil Deneysel derlemesinde hata ayıklama başlatılamıyor.  
  
3.  Deneysel derlemede bir örnek diyagramı açın.  
  
4.  Komut doğru etkin veya devre dışı bırakıldı ve uygun şekilde gösterilen veya gizli, seçili öğeye bağlı olarak doğrulamak için diyagram çeşitli öğelere sağ tıklayın.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 **Komutu, menüde görünmez:**  
  
- Komutu DSL paketini yüklemek kadar yalnızca Visual Studio örneklerini hata ayıklama içinde görünür. Daha fazla bilgi için [etki alanına özgü dil çözümlerini dağıtma](../modeling/deploying-domain-specific-language-solutions.md).  
  
- Deneysel örneğinizi bu DSL için doğru dosya adı uzantısına sahip olduğundan emin olun. Dosya adı uzantısı denetlemek için Visual Studio ana örneğine DslDefinition.dsl açın. Ardından Düzenleyici düğüm DSL Gezgini içinde sağ tıklayın ve ardından Özellikler seçeneğine tıklayın. Özellikler penceresinde FileExtension özelliğini inceleyin.  
  
- Yaptığınız [paketinin sürüm numarasını Artır](#version)?  
  
- OnStatus yönteminizin başlangıcında bir kesme noktası ayarlayın. Diyagram üzerinde herhangi bir bölümünü tıkladığında sonu.  
  
   **OnStatus yönteminin çağrılmaması**:  
  
  -   GUID'leri ve kimlikleri CommandSet kodunuzda Commands.vsct sembolleri bölümünde eşleştiğinden emin olun.  
  
  -   Commands.vsct içinde GUID ve ID her üst düğümünde doğru üst grup tanımlayın emin olun.  
  
  -   Bir Visual Studio komut istemi devenv /rootsuffix exp/Setup yazın. Ardından Visual Studio hata ayıklama örneğini yeniden başlatın.  
  
- Bu komut doğrulamak için OnStatus yöntemi aracılığıyla adım. Görünür ve komutu. Etkin ayarlanmıştır true.  
  
  **Yanlış menü metni görünür veya komut yanlış yere görünür**:  
  
- GUID ve ID birleşimi bu komut için benzersiz olduğundan emin olun.  
  
- Önceki paket sürümleri kaldırdığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Nasıl yapılır: standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)   
 [Etki alanına özgü dil çözümlerini dağıtma](../modeling/deploying-domain-specific-language-solutions.md)   
 [Örnek kod: bağlantı hattı diyagramları](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)



