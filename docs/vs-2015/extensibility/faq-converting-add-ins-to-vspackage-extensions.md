---
title: 'SSS: Eklentileri VSPackage uzantılarına dönüştürme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2318ff719f51660b4cec0eec6b7a051ea54aa67
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817353"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>SSS: Eklentileri VSPackage Uzantılarına Dönüştürme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eklentileri artık kullanım dışı bırakılmıştır. Yeni bir Visual Studio uzantısı yapmak için bir VSIX uzantısı oluşturmak gerekir. Bir Visual Studio eklentisi, bir VSIX uzantısı dönüştürme hakkında sık sorulan soruların yanıtları aşağıdadır.  
  
> [!WARNING]
>  C# ve Visual Basic projeleri için Visual Studio 2015'te başlangıç VSIX projesi kullanın ve menü komutları, araç pencereleri ve VSPackages için öğe şablonları ekleyin. Daha fazla bilgi için [Visual Studio 2015 SDK'sındaki yenilikler](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
>  Çoğu durumda bir VSPackage proje öğesi ile bir VSIX projesine eklentisi kodunuzu yalnızca aktarabilirsiniz. Çağırarak DTE Otomasyon nesnesi alabilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> içinde <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi.  
>   
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
>  Daha fazla bilgi için [VSPackage içinde eklenti kodumu nasıl çalıştırırım?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) aşağıda.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>VSIX Uzantıları Geliştirme hangi yazılım gerekiyor?  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Uzantı belgeleri nerede?  
 İle başlayan [Visual Studio uzantıları geliştirmeye başlama](../extensibility/starting-to-develop-visual-studio-extensions.md). MSDN'de VSSDK uzantısı geliştirme hakkında diğer makaleler bir ' dir.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Bir VSIX projesine eklentisi Projem dönüştürebilir miyim?  
 VSIX projelerinde kullanılan mekanizma olarak eklentisi projeleri dışındaki aynı olmadığından, bir eklenti projesi doğrudan bir VSIX projesi dönüştürülemiyor. VSIX proje şablonunu yanı sıra, doğru proje öğesi şablonları görece getirmek kolay ve VSIX uzantısı olarak çalışan kolaylaştırır kod vardır.  
  
##  <a name="BKMK_StartDeveloping"></a> VSIX uzantılarını geliştirmeye nasıl başlarım?  
 Bir menü komutu içeren bir VSIX nasıl yaptığınız aşağıda verilmiştir:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Bir menü komutu içeren bir VSIX uzantısı yapmak için  
  
1.  Bir VSIX projesi oluşturun. (**Dosya**, **yeni**, **proje**, veya tür **proje** içinde **hızlı başlatma** pencere). Buna **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik** veya **Visual Basic / genişletilebilirlik** seçip **VSIX projesi**.) Projeyi adlandırın **TestExtension** ve bunun için bir konum belirtin.  
  
2.  Ekleme bir **özel komut** proje öğesi şablon. ('nde proje düğümüne sağ **Çözüm Gezgini** seçip **Ekle / yeni öğe**. Buna **yeni proje** Visual C# veya Visual Basic seçin iletişim **genişletilebilirlik** düğümünü seçip alt **özel komut**.)  
  
3.  Yapı ve proje hata ayıklama modunda çalıştırmak için F5 tuşuna basın.  
  
     Visual Studio ikinci bir örneğini görünür. Bu ikinci bir örneği Deneysel örneği olarak adlandırılır ve Visual Studio'nun kod yazmak için kullandığınız örnekle aynı ayarları olmayabilir. İlk kez deneysel örneği çalıştırdığınızda VS Online'da oturum açın ve tema ve profil belirtmeniz istenir.  
  
     Üzerinde **Araçları** menü (deneysel örneğinde) adlı bir düğme görmeniz **My komut adı**. Bu düğmeyi seçtiğinizde, bir ileti şu şekilde görünmelidir: **içinde TestVSPackagePackage.MenuItemCallback()**.  
  
##  <a name="BKMK_RunAddin"></a> Eklenti kodum içinde bir VSPackage'ı nasıl çalıştırırım?  
 Eklenti kodu genellikle iki yöntemden biriyle çalıştırır:  
  
- Bir menü komutu tarafından tetiklenen (kod `IDTCommandTarget.Exec` yöntemi)  
  
- Otomatik olarak girişte (kod `OnConnection` olay işleyicisi.)  
  
  Vspackage'ta aynı şey yapabilirsiniz. Geri çağırma yöntemi eklenti kod ekleme şöyledir:  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>VSPackage'ı bir menü komutu uygulamak için  
  
1. Bir menü komutu içeren bir VSPackage'ı oluşturun. (Daha fazla bilgi için [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2. VSPackage'ı tanımını içeren dosyayı açın. (C# projesinde, sahip  <em>\<proje adınız ></em>Package.cs.)  
  
3. Aşağıdaki `using` deyimlerini dosyaya:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Bulma `MenuItemCallback` yöntemi. Bir çağrı ekleyin <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> almak için <xref:EnvDTE80.DTE2> nesnesi:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Eklentinizi olan kod ekleme, `IDTCommandTarget.Exec` yöntemi. Örneğin, yeni bir bölme ekler bazı kod işte **çıkış** penceresini açın ve yeni bölmesinde "Bazı Text" yazdırır.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));  
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
       outputWindowPane.OutputString("Some Text");  
   }  
  
   ```  
  
6. Oluşturun ve bu projeyi çalıştırın. F5 tuşuna basın veya seçin **Başlat** üzerinde **hata ayıklama** araç çubuğu. Visual Studio'nun deneysel örneğinde **Araçları** menü adlı bir düğme olmalıdır **My komut adı**. Bu düğme sözcükleri seçtiğinizde **bazı metin** gözükeceğini bir **çıkış** pencere bölmesi. (Açmak zorunda kalabilirsiniz **çıkış** penceresi.)  
  
   Başlangıçta Çalıştır kodunuzu da olabilir. Ancak, bu yaklaşım genellikle VSPackage uzantılarına için önerilmez. Çok fazla uzantıları Visual Studio başladığında yüklemeye çalışırsanız, başlangıç zamanı fark edilir derecede uzun olabilir. VSPackage'ı yalnızca (açılan bir çözüm gibi) bazı koşullar karşılandığında otomatik olarak yük daha iyi bir uygulamadır.  
  
   Bu yordamı, bir çözüm açıldığında otomatik olarak yükler VSPackage eklenti kodunu çalıştırma işlemi gösterilmektedir:  
  
#### <a name="to-autoload-a-vspackage"></a>VSPackage otomatik yükleme için  
  
1. Visual Studio Paket proje öğesi ile bir VSIX projesi oluşturun. (Bunu yapmak adımları için bkz. [nasıl geliştirme VSIX uzantılarını başlarım?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Eklemeniz yeterlidir **Visual Studio paket** bunun yerine proje öğesi.) VSIX projesi adı **TestAutoload**.  
  
2. TestAutoloadPackage.cs açın. Paket sınıfı burada bildirilir satırı bulun:  
  
   ```csharp  
   public sealed class <name of your package>Package : Package  
   ```  
  
3. Bu satırın üzerine öznitelikleri kümesidir. Bu öznitelik ekleyin:  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
   ```  
  
4. Bir kesim noktası `Initialize()` yöntem ve (F5) hata ayıklamayı başlatın.  
  
5. Deneysel örneğinde, bir projeyi açın. VSPackage'ı yüklemeli ve kesme noktasına isabet.  
  
   Alanları kullanarak, VSPackage'ı yüklemek için diğer bağlamlarda belirtebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Daha fazla bilgi için [VSPackage yükleme](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>DTE nesnesini nasıl alabilirim?  
 Kullanıcı Arabirimi eklentinizin görüntülemez, — örneğin, menü komutlarını, araç çubuğu düğmeleri veya araç pencereleri — kodunuzu olarak kullanmanız mümkün olabilir-VSPackage DTE Otomasyon nesnesini Al kadar uzun. İşte nasıl:  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Bir VSPackage'ı kullanarak DTE nesnesini almak için  
  
1. Visual Studio Paket öğe şablonu ile bir VSIX projesinde Ara  <em>\<proje adı ></em>Package.cs dosyasına. Bu, türetilen sınıftır <xref:Microsoft.VisualStudio.Shell.Package>; Visual Studio ile etkileşime yardımcı olabilir. Bu durumda, kullandığınız kendi <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> almak için <xref:EnvDTE80.DTE2> nesne.  
  
2. Bu ekleme `using` ifadeleri:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
3. Bulma `Initialize` yöntemi. Bu yöntem paket sihirbazında belirttiğiniz komutu işleyen. Bir çağrı ekleyin <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> DTE nesnesini almak için:  
  
   ```csharp  
   DTE dte = (DTE)GetService(typeof(DTE));  
   ```  
  
   Sonra <xref:EnvDTE.DTE> Otomasyon nesnesi, eklenti kodunuzun kalanını projeye ekleyebilirsiniz. Gerekirse <xref:EnvDTE80.DTE2> nesnesi aynı şeyi yapabilir.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Nasıl menü komutları ve araç çubuğu düğmeleri my eklentisinde VSPackage stil değiştirebilirim?  
 VSPackage uzantılarına .vsct dosyası çoğu menü komutları, araç çubukları, araç çubuğu düğmeleri ve diğer kullanıcı Arabirimi oluşturmak için kullanın. **Özel komut** proje öğesi şablonu size bir komut oluşturmak için seçeneği **Araçları** menüsü. Daha fazla bilgi için [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 .Vsct dosyaları hakkında daha fazla bilgi için bkz. [nasıl VSPackages Ekle kullanıcı arabirimi öğeleri](../extensibility/internals/how-vspackages-add-user-interface-elements.md). .Vsct dosyası menü öğeleri, araç çubukları ve araç çubuğu düğmeleri eklemek için nasıl kullanılacağını gösteren izlenecek yollar için bkz. [genişletme menüler ve komutlar](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Özel araç pencereleri VSPackage şekilde nasıl ekleyebilirim?  
 Özel araç penceresi proje öğesi şablon araç penceresi oluşturma seçeneğini sunar. Bu proje öğesi şablon hakkında daha fazla bilgi için bkz: [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md). Araç pencereleri hakkında daha fazla bilgi için bkz. [genişletme ve özelleştirme araç Windows](../extensibility/extending-and-customizing-tool-windows.md) ve makaleleri altında özellikle [araç penceresi ekleme](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Visual Studio windows VSPackage şekilde nasıl yönetebilirim?  
 Eklentinizi Visual Studio windows yönetiliyorsa, eklenti kodu VSPackage içinde çalışması gerekir. Örneğin, bu yordamı yöneten kodun nasıl ekleneceği gösterilmektedir **görev listesi** için `MenuItemCallback` VSPackage yöntemi.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Pencere Yönetimi kod bir eklentiyi Vspackage'a eklemek için  
  
1. Bir menü komutu olarak içeren bir VSPackage'ı oluşturma [nasıl geliştirme VSIX uzantılarını başlarım?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) bölümü.  
  
2. VSPackage'ı tanımını içeren dosyayı açın. (C# projesinde, sahip  <em>\<proje adınız ></em>Package.cs.)  
  
3. Bu ekleme `using` ifadeleri:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Bulma `MenuItemCallback` yöntemi. Bir çağrı ekleyin <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> almak için <xref:EnvDTE80.DTE2> nesnesi:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Eklentinizi kodu ekleyin. Örneğin, yeni görevler ekler bazı kod işte **görev listesi**, görevlerin sayısını listeler ve bir görevi siler.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)   
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
       TaskList tl = (TaskList)dte.ToolWindows.TaskList;   
       askItem tlItem;   
  
       // Add a couple of tasks to the Task List.   
       tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",    
           vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,   
           true, "", 10, true, true);  
       tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",   
           vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);  
  
       // List the total number of task list items after adding the new task items.  
       System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);  
       System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
  
       // Remove the second task item. The items list in reverse numeric order.   
       System.Windows.Forms.MessageBox.Show("Deleting the second task item");  
       tl.TaskItems.Item(2).Delete();  
       System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
   }  
   ```  
  
## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>Projeler ve çözümler vspackage'ta nasıl yönetebilirim?  
 Eklenti kodu, eklenti projeler ve çözümler yönetiliyorsa, içinde bir VSPackage'ı çalışması gerekir. Örneğin, bu yordamı başlangıç projesi alır kodun nasıl ekleneceği gösterilmektedir.  
  
1. Bir menü komutu olarak içeren bir VSPackage'ı oluşturma [nasıl geliştirme VSIX uzantılarını başlarım?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) bölümü.  
  
2. VSPackage'ı tanımını içeren dosyayı açın. (C# projesinde, sahip  <em>\<proje adınız ></em>Package.cs.)  
  
3. Bu ekleme `using` ifadeleri:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Bulma `MenuItemCallback` yöntemi. Bir çağrı ekleyin <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> almak için <xref:EnvDTE80.DTE2> nesnesi:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Eklentinizi kodu ekleyin. Örneğin, aşağıdaki kod, bir çözümde başlangıç projesinin adını alır. (Bu paketi çalıştığında çok projeli bir çözüm açık olması gerekir.)  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
       SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;   
       Project startupProj;   
       string msg = "";  
  
       foreach (String item in (Array)sb.StartupProjects)   
       {  
           msg += item;   
       }  
       System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);   
       startupProj = dte.Solution.Item(msg);   
       System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);   
   }  
   ```  
  
## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>Klavye kısayolları içinde bir VSPackage'ı nasıl ayarlayabilirim?  
 Kullandığınız `<KeyBindings>` .vsct dosyası öğesidir. Aşağıdaki örnekte, komut için klavye kısayolunu `idCommand1` Alt + A ve komut için klavye kısayolunu `idCommand2` Alt + Ctrl + a. Anahtar adları için söz dizimi dikkat edin.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>Vspackage'ta Otomasyon olaylarına nasıl yapabilirim?  
 Eklentinizi olduğu gibi aynı şekilde vspackage'ta Otomasyon olayları işleyin. Aşağıdaki kod nasıl işleneceğini gösterir `OnItemRenamed` olay. (Bu örnekte, DTE nesnesi zaten yönettiniz varsayılır.)  
  
```csharp  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```

