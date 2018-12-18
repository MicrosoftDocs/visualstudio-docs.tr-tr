---
title: Visual Studio tümleştirmesi (MSBuild) | Microsoft Docs
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
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2b9591ebff8708d0cd63825854c31cf297d32ce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294859"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio Tümleştirmesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio ana [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] yönetilen projeleri yüklemek ve derlemek için. Çünkü [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projesi, neredeyse her her proje için sorumlu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] biçimi başarıyla kullanılabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]projeyi farklı bir araç ile yazılmış olsa ve özelleştirilmiş bir yapı işlemi olsa bile.  
  
 Bu konuda, belirli yönlerini anlatmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'s [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] barındıran sayılacağı projeleri ve yüklemek ve derlemek istediğiniz .targets dosyalarını özelleştirirken [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bu emin olmanıza yardımcı olacak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IntelliSense ve iş özel projenizde hata ayıklama gibi özellikleri.  
  
 C++ projeleri hakkında daha fazla bilgi için bkz. [proje dosyaları](http://msdn.microsoft.com/library/5261cf45-3136-40a6-899e-dc1339551401).  
  
## <a name="project-file-name-extensions"></a>Proje Dosya Adı Uzantıları  
 MSBuild.exe tanır desen ile eşleşen hiçbir proje dosyası adının uzantısını. * proj. Ancak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yalnızca bir alt kümesini projeyi yükleyecek olan dile özgü proje sistemini belirler bu proje dosya adı uzantılarını tanır. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir dilden yok [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] tabanlı bir proje sistemi.  
  
 Örneğin, [!INCLUDE[csprcs](../includes/csprcs-md.md)] proje sistemi .csproj dosyalarını yükler, ancak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir .xxproj dosyası mümkün değildir. Bir rastgele dil içindeki kaynak dosyaları için bir proje dosyası aynı uzantıya kullanmalısınız [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../includes/csprcs-md.md)] proje dosyaları içinde yüklenen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="well-known-target-names"></a>İyi Bilinen Hedef Adları  
 Tıklayarak **derleme** komutunu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projedeki varsayılan hedef yürütülecektir. Genellikle, bu hedef ayrıca adlı `Build`. Seçme **yeniden** veya **temiz** komut aynı ada sahip bir hedef proje yürütmek çalışır. Tıklayarak **Yayımla** adlı bir hedef yürütecektir `PublishOnly` projedeki.  
  
## <a name="configurations-and-platforms"></a>Yapılandırmalar ve Platformlar  
 Yapılandırmaları temsil edilir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projeleri özelliklere göre gruplandırılmış bir `PropertyGroup` öğesini içeren bir `Condition` özniteliği. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Proje yapılandırmaları ve görüntülemek için platformlar listesini oluşturmak için bu koşullara bakar. Bu listeyi başarıyla çıkarmak için koşulların aşağıdakine benzer bir biçimde olmalıdır:  
  
```  
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "  
Condition=" '$(Configuration)' == 'Release' "   
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "  
```  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] üzerindeki koşullara bakar `PropertyGroup`, `ItemGroup`, `Import`, özellik ve öğeler bu amaç için.  
  
## <a name="additional-build-actions"></a>Ek Yapı Eylemleri  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir proje dosyasında öğesi türü adını değiştirmenize izin verir **derleme eylemi** özelliği [dosya özelliklerini](http://msdn.microsoft.com/en-us/013c4aed-08d6-4dce-a124-ca807ca08959) penceresi. `Compile`, `EmbeddedResource`, `Content`, ve `None` öğe türü adları her zaman bu menüde, projenizde zaten başka bir öğe türü adları ile birlikte listelenir. Her özel öğe türü adları her zaman bu menüde kullanılabilir emin olmak için adlandırılmış bir öğe türü adları ekleyebilirsiniz. `AvailableItemName`. Örneğin, aşağıdaki proje dosyanıza ekleyerek özel bir tür ekler `JScript` aktarmadan tüm projelerde bu menüye:  
  
```  
<ItemGroup>  
    <AvailableItemName Include="JScript"/>  
</ItemGroup>  
```  
  
> [!NOTE]
>  Bazı öğe türü adları özel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ancak bu açılır menüde listelenmez.  
  
## <a name="in-process-compilers"></a>İşlem İçi Derleyiciler  
 Mümkün olduğunda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] işlemde sürümünü kullanmayı dener [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] performansı artırmak için derleyici. (Uygulanamaz [!INCLUDE[csprcs](../includes/csprcs-md.md)].) Bunun düzgün çalışması için aşağıdaki koşullar karşılanmalıdır:  
  
-   Proje bir hedef olmalıdır adında bir görev `Vbc` için [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projeleri.  
  
-   `UseHostCompilerIfAvailable` Görev parametresi ayarlanmalıdır true.  
  
## <a name="design-time-intellisense"></a>Tasarım Zamanı IntelliSense  
 IntelliSense desteği almak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir derleme bir çıktı derlemesi üretmeden önce aşağıdaki koşulların karşılanması gerekir:  
  
-   Adlı bir hedef olmalıdır `Compile`.  
  
-   Her iki `Compile` hedefi ya da bağımlılıklarından biri çağırmalıdır derleyici görevinin projesi için gibi `Csc` veya `Vbc`.  
  
-   Her iki `Compile` hedefi ya da bağımlılıklarından biri derleyicinin IntelliSense, özellikle tüm başvurular için gereken tüm parametreleri almasını sağlamalıdır.  
  
-   "İşlem içi derleyiciler" bölümünde listelenen koşulların karşılanması gerekir.  
  
## <a name="building-solutions"></a>Çözümler Oluşturma  
 İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], çözüm dosyası ve proje derleme sıralaması tarafından denetlenen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kendisi. Komut satırında msbuild.exe ile bir çözüm derlerken [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] çözüm dosyasını ayrıştırır ve proje derlemelerini sıralar. Her iki durumda da projeler ayrı olarak bağımlılık sırasında oluşturulur ve projeden projeye başvurular geçirilmez. Buna karşılık, ayrı ayrı projeler msbuild.exe ile oluşturulduğunda, projeden projeye başvurular geçirilir.  
  
 İçinde derlerken [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], özellik `$(BuildingInsideVisualStudio)` ayarlanır `true`. Bu, projenizde veya .targets dosyalarında derlemenin farklı davranmasını sağlamak için kullanılabilir.  
  
## <a name="displaying-properties-and-items"></a>Özellikleri ve Öğeleri Görüntüleme  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] belirli özellik adlarını ve değerlerini tanır. Örneğin, bir projede aşağıdaki özellik neden olacak **Windows uygulama** görünmesini **uygulama türü** kutusunda **Proje Tasarımcısı**.  
  
```  
<OutputType>WinExe</OutputType>  
```  
  
 Özellik değeri içinde düzenlenmiş **Proje Tasarımcısı** ve proje dosyasına kaydedilebilir. Böyle bir özellik elle düzenlemeye tarafından geçersiz bir değer belirtilmezse [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje yüklendiğinde bir uyarı gösterir ve geçersiz değeri varsayılan bir değerle değiştirin.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bazı özelliklerin varsayılan değerlerini anlar. Varsayılan olmayan değerleri sahip olmadıkları sürece bu özellik proje dosyasına kalıcı olmaz.  
  
 Rastgele adlara sahip özellikler içinde görüntülenmez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Rastgele özellikleri değiştirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], proje dosyasını XML düzenleyicisinde açın ve bunları el ile düzenlemeniz gerekir. Daha fazla bilgi için [Visual Studio'daki proje dosyaları düzenleme](#BKMK_EditingProjects) bu konunun ilerleyen bölümlerinde.  
  
 Projede rastgele öğe adları ile tanımlanan öğeler, kendi proje düğümleri altında Çözüm Gezgini'nde görüntülenen varsayılan olarak alır. Bir öğeyi görüntüden gizlemek için ayarlanmış `Visible` meta verileri `false`. Örneğin, aşağıdaki öğe yapı işlemine katılır ancak Çözüm Gezgini'nde görüntülenmez.  
  
```  
<ItemGroup>  
    <IntermediateFile Include="cache.temp">  
        <Visible>false</Visible>  
    </IntermediateFile>  
</ItemGroup>  
```  
  
 Projeye aktarılan dosyalarda bildirilen öğeler varsayılan olarak görüntülenmez. Derleme işlemi sırasında oluşturulan öğeler, Çözüm Gezgini'nde hiçbir zaman görüntülenir.  
  
## <a name="conditions-on-items-and-properties"></a>Öğeler ve Özellikler İle İlgili Koşullar  
 Bir yapı sırasında tüm koşullar tam olarak dikkate alınır.  
  
 Görüntülenecek özellik değerlerini belirlerken, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yapılandırmaya bağımlı farklı değerlendirilir göz önünde bulundurur özellikleri yeniden yapılandırma bağımsız olarak kabul eder. İçin özellikleri yeniden yapılandırma bağımlı olarak kabul eder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ayarlar `Configuration` ve `Platform` özellikleri uygun şekilde ve bildirir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projeyi yeniden değerlendirin. Özellikleri yeniden yapılandırma bağımsız olarak, koşulların nasıl değerlendirileceği belirsiz olarak kabul eder.  
  
 Öğelerdeki koşullu ifadeler, öğenin Çözüm Gezgini'nde görüntülenip görüntülenmeyeceğini karar verme amacıyla her zaman sayılır.  
  
## <a name="debugging"></a>Hata Ayıklama  
 Bul ve çıktı derlemesine başlatın ve hata ayıklayıcıyı eklemek amacıyla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] özelliklere sahip olması `OutputPath`, `AssemblyName`, ve `OutputType` doğru şekilde tanımlanmış. Hata ayıklayıcı, derleme işlemi derleyicinin bir .pdb dosyası oluşturmasıyla eklemek başarısız olur.  
  
## <a name="design-time-target-execution"></a>Tasarım Zamanı Hedef Yürütme  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir projeyi yüklediğinde belirli adları olan hedefleri yürütmeyi dener. Bu hedefler arasında `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths`, ve `CopyRunEnvironmentFiles`. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bu hedefleri derleyicinin IntelliSense sağlamak için başlatılabilir, hata ayıklayıcının başlatılabilmesi ve Çözüm Gezgini'nde gösterilen başvuruların çözümlenebilmesi için çalıştırır. Bu hedefler mevcut değilse projeyi yüklemek ve tasarım zamanı deneyimi ancak doğru şekilde derlenmesi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tam işlevsel olmayacaktır.  
  
##  <a name="BKMK_EditingProjects"></a> Visual Studio'da proje dosyalarını düzenleme  
 Düzenlenecek bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] doğrudan projesi, proje dosyası Visual Studio XML düzenleyicisinde açabilirsiniz.  
  
#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Visual Studio'da bir proje dosyasının yüklemesini kaldırmak ve düzenlemek için  
  
1.  İçinde **Çözüm Gezgini**, proje için kısayol menüsünü açın ve ardından **projeyi**.  
  
     Proje işaretlenmiş **(kullanılamıyor)**.  
  
2.  İçinde **Çözüm Gezgini**, kullanılamayan projenin kısayol menüsünü açın ve ardından **Düzenle \<proje dosyası >**.  
  
     Proje dosyası Visual Studio XML Düzenleyicisi'nde açılır.  
  
3.  Düzenleyin, kaydedin ve ardından Proje dosyasını kapatın.  
  
4.  İçinde **Çözüm Gezgini**, kullanılamayan projenin kısayol menüsünü açın ve ardından **projeyi**.  
  
## <a name="intellisense-and-validation"></a>IntelliSense ve Doğrulama  
 Proje dosyalarını düzenlemek için XML düzenleyicisini kullanırken, IntelliSense ve doğrulama tarafından yönlendirilir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] şema dosyaları. Bunlar bulunabilir şema önbelleğinde yüklü  *\<Visual Studio yükleme dizini >* \Xml\Schemas\1033\MSBuild.  
  
 Çekirdek [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] türleri Microsoft.Build.Core.xsd'de ve tarafından kullanılan ortak türler tanımlanmış [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Microsoft.Build.commontypes.xsd'de tanımlanmıştır. Şemaları özel öğe türü adları, özellikler ve görevler için IntelliSense ve doğrulama edinecek olmanızdır özelleştirmek için kullanabilmek üzere düzenlemek veya CommonTypes veya Core şemalarını içeren kendi şemanızı oluşturabilirsiniz. Düzenleyicisi'ni kullanarak bunu bulmanız XML yönlendirmek için sahip olacak kendi şemanızı oluşturursanız **özellikleri** penceresi.  
  
## <a name="editing-loaded-project-files"></a>Yüklenmiş Proje Dosyalarını Düzenleme  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Proje dosyaları ve proje dosyaları tarafından içe aktarılan dosyaların içeriğini önbelleğe alır. Bir yüklenmiş proje dosyasını düzenliyorsanız, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otomatik olarak, değişikliklerin etkili olması için projeyi yeniden yüklemenizi ister. Ancak yüklenmiş bir proje tarafından içe aktarılan bir dosyayı düzenlerseniz, herhangi bir yeniden yükleme istemi olmayacaktır ve kaldırma ve değişikliklerin etkili el ile yapmak için projeyi yeniden yükleyin.  
  
## <a name="output-groups"></a>Çıkış Grupları  
 Microsoft.Common.targets içinde tanımlanan çeşitli hedefler sonlanan adlara sahip `OutputGroups` veya `OutputGroupDependencies`. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bu hedefleri proje çıktılarının tam listelerini almak için çağırır. Örneğin, `SatelliteDllsProjectOutputGroup` hedef bir yapının oluşturacağı tüm uydu derlemelerin bir listesini oluşturur. Bu çıktı grupları yayımlama, dağıtım ve projeden projeye başvurular gibi özellikler tarafından kullanılır. Bunları tanımlamayan projeler yükleyecek ve oluşturacaktır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ancak bazı özellikler düzgün çalışmayabilir.  
  
## <a name="reference-resolution"></a>Başvuru Çözümleme  
 Başvuru çözümleme, gerçek derlemeleri bulmak için bir proje dosyasında depolanan başvuru öğelerini kullanma işlemidir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] içinde her başvurunun özelliklerini ayrıntılı göstermek için başvuru çözümlemesini tetiklemelidir **özellikleri** penceresi. Aşağıdaki liste, üç başvuru türünü ve bunların nasıl kullanıldığını açıklar.  
  
-   Bütünleştirilmiş kod başvuruları:  
  
     Proje sistemi bir hedefi iyi bilinen adıyla çağırır `ResolveAssemblyReferences`. Bu hedef, öğe türü adı öğeleriyle üretmelidir `ReferencePath`. Bu öğelerin her biri bir öğe belirtimine sahip olmalıdır (değerini `Include` bir öğenin özniteliğini) içeren başvuru tam yolu. Öğeleri aracılığıyla aşağıdaki yeni meta veriler ek olarak geçirilen girdi öğelerinin tüm meta verilerine sahip olmanız gerekir:  
  
    -   `CopyLocal`, derlemenin çıktı klasörüne kopyalanıp kopyalanmayacağını belirten true veya false ayarlayın.  
  
    -   `OriginalItemSpec`, başvurunun Asıl öğe belirtimini içeren.  
  
    -   `ResolvedFrom`, bunu çözümlenirse "{TargetFrameworkDirectory}" kümesi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dizin.  
  
-   COM başvuruları:  
  
     Proje sistemi bir hedefi iyi bilinen adıyla çağırır `ResolveCOMReferences`. Bu hedef, öğe türü adı öğeleriyle üretmelidir `ComReferenceWrappers`. Bu öğelerin her biri, COM başvurusu için birlikte çalışabilirlik derlemesine giden tam yolu içeren bir öğe belirtimine sahip olmalıdır. Öğeleri girdi öğelerinin geçilen, ayrıca yeni meta veri adı ile tüm meta verilerine de sahip `CopyLocal`, derlemenin çıktı klasörüne kopyalanıp kopyalanmayacağını belirten true veya false ayarlayın  
  
-   Yerel başvurular  
  
     Proje sistemi bir hedefi iyi bilinen adıyla çağırır `ResolveNativeReferences`. Bu hedef, öğe türü adı öğeleriyle üretmelidir `NativeReferenceFile`. Öğeleri geçtiğini, meta verilerin adlı yeni bir ek girdi öğelerinin tüm meta verilerine olmalıdır `OriginalItemSpec`, başvurunun Asıl öğe belirtimini içeren.  
  
## <a name="performance-shortcuts"></a>Performans Kısayolları  
 Visual Studio UI'de hata ayıklamayı başlatırsanız (F5 tuşunu seçerek veya seçerek **hata ayıklama**, **hata ayıklamayı Başlat** menü çubuğundaki), yapı işlemi performansı artırmak için hızlı bir güncelleştirme kontrolü kullanır. Burada özelleştirilmiş yapıların dahili hale gelen dosyalar oluşturma bazı durumlarda, hızlı güncelleştirme kontrolü değiştirilen dosyaları düzgün tanımlamaz. Daha kapsamlı güncelleme kontrolleri gereken projeleri hızlı denetimi ortam değişkenini ayarlayarak devre dışı kapatabilir `DISABLEFASTUPTODATECHECK=1`. Alternatif olarak, proje bu projeye ya da projenin içe aktardığı bir dosya bir MSBuild özelliği olarak ayarlayabilirsiniz.  
  
 Visual Studio'daki normal yapılarda, hızlı güncelleştirme denetimleri geçerli değildir ve bir komut isteminde derlemenin çağırdığınız gibi Proje derlenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Visual Studio derleme işlemini genişletme](../msbuild/how-to-extend-the-visual-studio-build-process.md)   
 [IDE içinden derleme başlatma](../msbuild/starting-a-build-from-within-the-ide.md)   
 [.NET Framework uzantılarını kaydetme](../msbuild/registering-extensions-of-the-dotnet-framework.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [Öğe unsuru (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Özellik öğesi (MSBuild)](../msbuild/property-element-msbuild.md)   
 [Hedef öğe (MSBuild)](../msbuild/target-element-msbuild.md)   
 [CSC görevi](../msbuild/csc-task.md)   
 [Vbc Görevi](../msbuild/vbc-task.md)



