---
title: Modelleme Uzantısı Tanımlama ve yükleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6f7895916cc4ee877c53b056f703d8e46b64b409
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805573"
---
# <a name="define-and-install-a-modeling-extension"></a>Modelleme uzantısı tanımlama ve yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da modelleme diyagramları için uzantı tanımlayabilirsiniz. Bu şekilde, kendi gereksinimlerine göre modelleri ve diyagramları uyarlayabilirsiniz. Örneğin, menü komutlarını, UML profilleri, doğrulama kısıtlamaları ve araç kutusu öğeleri tanımlayabilirsiniz. Çeşitli bileşenleri tek bir uzantı tanımlayabilirsiniz. Ayrıca bu uzantılar şeklinde diğer Visual Studio kullanıcılarına dağıtabilirsiniz bir [Visual Studio Tümleştirme Uzantısı (VSIX)](http://go.microsoft.com/fwlink/?LinkId=160780). Bir VSIX projesi kullanarak Visual Studio'da bir VSIX projesi oluşturabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 Bkz: [gereksinimleri](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="creating-a-modeling-extension-solution"></a>Modelleme Uzantısı çözümü oluşturma  
 Bir modelleme uzantısı tanımlamak için bu projeleri içeren bir çözüm oluşturmanız gerekir:  
  
- A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tümleştirme Uzantısı (VSIX) projesi. Bu, uzantınızın bileşenleri için yükleyici olarak davranan bir dosya oluşturur.  
  
- Gerekli bileşenleri için program kodunu içeren bir sınıf kitaplığı projesi.  
  
  Çeşitli bileşenlerini içeren bir uzantı yapmak istiyorsanız, tek bir çözümde geliştirebilirsiniz. Yalnızca bir VSIX projesi ihtiyacınız vardır.  
  
  Özel araç kutusu öğeleri ve özel UML profilleri gibi bir kod gerektirmeyen bileşenleri doğrudan VSIX projesine ayrı bir sınıf kitaplığı projeleri kullanmadan eklenebilir. Program kodu gerektiren bileşenler daha kolay bir ayrı bir sınıf kitaplığı projesinde tanımlanır. Kod gerektiren bileşenler hareket işleyicileri, menü komutlarını ve doğrulama kodu içerir.  
  
#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>Menü komutları, hareket işleyicileri veya doğrulama için bir sınıf kitaplığı projesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde seçin **yeni**, **proje**.  
  
2.  Altında **yüklü şablonlar**seçin **Visual C#** veya **Visual Basic**, ardından **sınıf kitaplığı**.  
  
#### <a name="to-create-a-vsix-project"></a>Bir VSIX projesi oluşturmak için  
  
1.  Kodu ile bir bileşeni oluşturuyorsanız, ilk sınıf kitaplığı projesi oluşturmak en kolayıdır. Bu proje için kod ekleyeceksiniz.  
  
2.  Bir VSIX projesi oluşturun.  
  
    1.  İçinde **Çözüm Gezgini**, çözümün kısayol menüsünde **Ekle**, **yeni proje**.  
  
    2.  Altında **yüklü şablonlar**, genişletme **Visual C#** veya **Visual Basic**, ardından **genişletilebilirlik**. Orta sütundaki seçin **VSIX projesi**.  
  
3.  VSIX projesinin çözümün başlangıç projesi olarak ayarlayın.  
  
    -   Çözüm Gezgini'nde VSIX projesinin kısayol menüsünden seçin **başlangıç projesi olarak ayarla**.  
  
4.  Açık **source.extension.vsixmanifest**. Dosyayı bildirim düzenleyicisinde açar.  
  
5.  Üzerinde **meta verileri** sekmesinde, VSIX açıklayıcı alanlarının ve adını belirleyin.  
  
6.  Üzerinde **hedefleri Yükle** sekmesini, **yeni** ve Visual Studio sürümlerini hedefler olarak ayarlayın.  
  
7.  Üzerinde **varlıklar** sekmesinde, bileşenleriniz için Visual Studio uzantısı ekleyin.  
  
    1.  Seçin **yeni**.  
  
    2.  Kod içeren bileşen için bu alanlar kümesinde **yeni varlık Ekle** iletişim kutusunda:  
  
        |||  
        |-|-|  
        |**Türü** =|**Microsoft.VisualStudio.MefComponent**|  
        |**Kaynak** =|**Mevcut çözümde bir proje**|  
        |**Proje** =|*Sınıf kitaplığı projenizi*|  
        |**Bu klasörde ekleme** =|*(boş)*|  
  
         Diğer bileşen türleri için sonraki bölümde bağlantılara bakın.  
  
## <a name="developing-the-component"></a>Bileşen geliştirme  
 Menü komut veya hareket işleyici gibi her bir bileşeni için ayrı bir işleyici tanımlamanız gerekir. Aynı sınıf kitaplığı projesinde birkaç işleyiciler koyabilirsiniz. Aşağıdaki tabloda, farklı türlerde işleyici özetlenmektedir.  
  
|Uzantı türü|Konu|Her bileşenin nasıl genellikle bildirildi|  
|--------------------|-----------|----------------------------------------------|  
|Menü komutu|[Modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|  
|Sürükle ve bırak veya çift tıklatın|[Modelleme diyagramında hareket işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|  
|Doğrulama kısıtlaması|[UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|  
|İş öğesi bağlantı olay işleyicisi|[İş öğesi bağlantı işleyicisi tanımlama](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|  
|UML profili|[UML’yi genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md)|(Tanımlanması için)|  
|Araç kutusu öğesi|[Özel bir modelleme araç kutusu öğesi tanımlama](../modeling/define-a-custom-modeling-toolbox-item.md)|(Tanımlanması için)|  
  
## <a name="running-an-extension-during-its-development"></a>Uzantı, geliştirme sırasında çalışan  
  
#### <a name="to-run-an-extension-during-its-development"></a>Geliştirme sırasında uzantı çalıştırmak için  
  
1.  İçinde [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **hata ayıklama** menüsünde seçin **hata ayıklamayı Başlat**.  
  
     Proje yapılarında ve yeni bir örneğini [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Deneysel modunda başlatılır.  
  
    -   Alternatif olarak seçebileceğiniz **hata ayıklama olmadan Başlat**. Bu programı başlatmak için geçen süreyi azaltır.  
  
2.  Oluşturun veya bir modelleme projesi Visual Studio'nun deneysel örneğinde açın ve oluşturabilir veya bir diyagramı açın.  
  
     Uzantınızı yüklenecek ve çalışacaktır.  
  
3.  Kullandıysanız **hata ayıklama olmadan Başlat** ancak istediğiniz hata ayıklayıcıyı kullanın, Visual Studio ana örneğine geri dönün. Üzerinde **hata ayıklama** menüsünü tıklatın **iliştirme**. İletişim kutusunda, program adı olan Visual Studio Deneysel örneğini seçin **devenv**.  
  
##  <a name="Installing"></a> Yükleme ve bir uzantıyı kaldırma  
 Uzantınızı ana Visual Studio örneğine kendi bilgisayarınıza veya diğer bilgisayarlarda çalıştırmak için aşağıdaki adımları gerçekleştirin.  
  
1.  Bilgisayarınızda, bulma **.vsix** uzantı projeniz tarafından oluşturulan dosya.  
  
    1.  İçinde **Çözüm Gezgini**, projenizin kısayol menüsünden seçin **klasörü Windows Gezgini'nde Aç**.  
  
    2.  Dosyayı bulmak **bin\\\*\\**_projeniz_**.vsix**  
  
2.  Kopyalama **.vsix** uzantıyı yüklemek istediğiniz hedef bilgisayarın bir dosyaya. Bu sizin kendi bilgisayarınız veya başka bir tane olabilir.  
  
    -   Hedef bilgisayarda belirttiğiniz Visual Studio sürümlerinden birini olmalıdır **yükleme hedeflerinden** sekmesinde **source.extension.vsixmanifest**.  
  
3.  Hedef bilgisayarda açın **.vsix** örneğin çift tıklayarak dosyayı.  
  
     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yükler.  
  
4.  Veya Visual Studio'yu yeniden başlatın.  
  
#### <a name="to-uninstall-an-extension"></a>Bir uzantıyı kaldırmak için  
  
1. Üzerinde **Araçları** menüsünü tıklatın **Uzantılar ve güncelleştirmeler**.  
  
2. Genişletin **yüklü uzantıları**.  
  
3. Uzantıyı seçin ve ardından **kaldırma**.  
  
   Nadiren, hatalı bir uzantı yüklemede başarısız olur ve hata penceresinde bir rapor oluşturur ancak Uzantı Yöneticisi'nde görünmez. Bu durumda, dosya şu konumdan silerek uzantıyı kaldırabilirsiniz burada *% LocalAppData %* genellikle *DriveName*: \Users\\*kullanıcıadı*\AppData\Local:  
  
   *% LocalAppData %* **\Microsoft\VisualStudio\\[sürüm] \Extensions**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md)   
 [Özel tanımlama Modelleme araç kutusu öğesi](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)   
 [Modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)



