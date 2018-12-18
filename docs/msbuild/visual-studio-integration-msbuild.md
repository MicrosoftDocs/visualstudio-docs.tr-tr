---
title: Visual Studio Tümleştirmesi (MSBuild)
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7449e8585cd9f1db8a4a43cddf8092f1a92c9758
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052429"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio tümleştirmesi (MSBuild)
Visual Studio ana [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] yönetilen projeleri yüklemek ve derlemek için. Çünkü [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projesi, neredeyse her her proje için sorumlu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] biçimi başarıyla kullanılabilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]projeyi farklı bir araç ile yazılmış olsa ve özelleştirilmiş bir yapı işlemi olsa bile.  
  
 Bu makalede belirli yönlerini [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'s [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] barındıran sayılacağı projeleri özelleştirirken ve *.targets* yüklemek ve derlemek istediğiniz dosyaları [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Bu emin olmanıza yardımcı olacak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IntelliSense ve iş özel projenizde hata ayıklama gibi özellikleri.  
  
 C++ projeleri hakkında daha fazla bilgi için bkz. [proje dosyalarını](/cpp/ide/project-files).  
  
## <a name="project-file-name-extensions"></a>Proje dosya adı uzantıları  
 *MSBuild.exe* desenle eşleşen proje dosya adı uzantısını tanır *.\* Proj*. Ancak, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yalnızca bir alt kümesini projeyi yükleyecek olan dile özgü proje sistemini belirler bu proje dosya adı uzantılarını tanır. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir dilden yok [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tabanlı bir proje sistemi.  
  
 Örneğin, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proje sistemi yüklenirken *.csproj* dosyaları, ancak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklemek mümkün değil bir *.xxproj* dosya. Bir rastgele dil içindeki kaynak dosyaları için bir proje dosyası aynı uzantıya kullanmalısınız [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] veya [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proje dosyaları içinde yüklenen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="well-known-target-names"></a>İyi bilinen hedef adları  
 Tıklayarak **derleme** komutunu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projedeki varsayılan hedef yürütülecektir. Genellikle, bu hedef ayrıca adlı `Build`. Seçme **yeniden** veya **temiz** komut aynı ada sahip bir hedef proje yürütmek çalışır. Tıklayarak **Yayımla** adlı bir hedef yürütecektir `PublishOnly` projedeki.  
  
## <a name="configurations-and-platforms"></a>Yapılandırmalar ve platformlar  
 Yapılandırmaları temsil edilir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projeleri özelliklere göre gruplandırılmış bir `PropertyGroup` öğesini içeren bir `Condition` özniteliği. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Proje yapılandırmaları ve görüntülemek için platformlar listesini oluşturmak için bu koşullara bakar. Bu listeyi başarıyla çıkarmak için koşulların aşağıdakine benzer bir biçimde olmalıdır:  
  
```xml  
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "  
Condition=" '$(Configuration)' == 'Release' "   
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "  
```  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] üzerindeki koşullara bakar `PropertyGroup`, `ItemGroup`, `Import`, özellik ve öğeler bu amaç için.  
  
## <a name="additional-build-actions"></a>Ek yapı eylemleri  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir proje dosyasında öğesi türü adını değiştirmenize izin verir **derleme eylemi** özelliği **dosya özellikleri** penceresi. **Derleme**, **EmbeddedResource**, **içerik**, ve **hiçbiri** öğe türü adları herhangi diğer öğe türü adları içinde birlikte bu menüde her zaman listelenir projenizi. Her özel öğe türü adları her zaman bu menüde kullanılabilir emin olmak için adlandırılmış bir öğe türü adları ekleyebilirsiniz. `AvailableItemName`. Örneğin, aşağıdaki proje dosyanıza ekleyerek özel bir tür ekler **JScript** aktarmadan tüm projelerde bu menüye:  
  
```xml  
<ItemGroup>  
    <AvailableItemName Include="JScript"/>  
</ItemGroup>  
```  
  
> [!NOTE]
>  Bazı öğe türü adları özel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ancak bu açılır menüde listelenmez.  
  
## <a name="in-process-compilers"></a>İşlem içi derleyiciler  
 Mümkün olduğunda, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] işlemde sürümünü kullanmayı dener [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] performansı artırmak için derleyici. (Uygulanamaz [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].) Bunun düzgün çalışması için aşağıdaki koşullar karşılanmalıdır:  
  
- Proje bir hedef olmalıdır adında bir görev `Vbc` için [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeleri.  
  
- `UseHostCompilerIfAvailable` Görev parametresi ayarlanmalıdır true.  
  
## <a name="design-time-intellisense"></a>Tasarım zamanı IntelliSense  
 IntelliSense desteği almak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir derleme bir çıktı derlemesi üretmeden önce aşağıdaki koşulların karşılanması gerekir:  
  
-   Adlı bir hedef olmalıdır `Compile`.  
  
-   Her iki `Compile` hedefi ya da bağımlılıklarından biri çağırmalıdır derleyici görevinin projesi için gibi `Csc` veya `Vbc`.  
  
-   Her iki `Compile` hedefi ya da bağımlılıklarından biri derleyicinin IntelliSense, özellikle tüm başvurular için gereken tüm parametreleri almasını sağlamalıdır.  
  
-   Listelenen koşulların [işlem içi derleyiciler](#in-process-compilers) bölüm sağlanmalıdır.  
  
## <a name="build-solutions"></a>Çözümleri oluşturun  
 İçinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], çözüm dosyası ve proje derleme sıralaması tarafından denetlenen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kendisi. Bir çözüm derlerken *msbuild.exe* komut satırında [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] çözüm dosyasını ayrıştırır ve proje derlemelerini sıralar. Her iki durumda da projeler ayrı olarak bağımlılık sırasında oluşturulur ve projeden projeye başvurular geçirilmez. Buna karşılık, ne zaman tek tek projeler derlendikten ile *msbuild.exe*, projeden projeye başvurular geçiş.  
  
 İçinde derlerken [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], özellik `$(BuildingInsideVisualStudio)` ayarlanır `true`. Bu, projenizdeki kullanılabilir veya *.targets* neden farklı davrandığını derleme dosyaları.  
  
## <a name="display-properties-and-items"></a>Özellikleri ve öğeleri görüntüleme  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] belirli özellik adlarını ve değerlerini tanır. Örneğin, bir projede aşağıdaki özellik neden olacak **Windows uygulama** görünmesini **uygulama türü** kutusunda **Proje Tasarımcısı**.  
  
```xml  
<OutputType>WinExe</OutputType>  
```  
  
 Özellik değeri içinde düzenlenmiş **Proje Tasarımcısı** ve proje dosyasına kaydedilebilir. Böyle bir özellik elle düzenlemeye tarafından geçersiz bir değer belirtilmezse [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proje yüklendiğinde bir uyarı gösterir ve geçersiz değeri varsayılan bir değerle değiştirin.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bazı özelliklerin varsayılan değerlerini anlar. Varsayılan olmayan değerleri sahip olmadıkları sürece bu özellik proje dosyasına kalıcı olmaz.  
  
 Rastgele adlara sahip özellikler içinde görüntülenmez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Rastgele özellikleri değiştirmek için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], proje dosyasını XML düzenleyicisinde açın ve bunları el ile düzenlemeniz gerekir. Daha fazla bilgi için [Visual Studio'daki proje dosyaları düzenleme](#edit-project-files-in-visual-studio) bu konunun ilerleyen bölümlerinde.  
  
 Projede rastgele öğe adları ile tanımlanan öğeler varsayılan olarak görüntülenen **Çözüm Gezgini** kendi proje düğümleri altında. Bir öğeyi görüntüden gizlemek için ayarlanmış `Visible` meta verileri `false`. Örneğin, aşağıdaki öğe yapı işlemine katılır ancak içinde görüntülenmez **Çözüm Gezgini**.  
  
```xml  
<ItemGroup>  
    <IntermediateFile Include="cache.temp">  
        <Visible>false</Visible>  
    </IntermediateFile>  
</ItemGroup>  
```  
  
 Projeye aktarılan dosyalarda bildirilen öğeler varsayılan olarak görüntülenmez. Derleme işlemi sırasında oluşturulan öğeleri hiçbir zaman görüntülenir **Çözüm Gezgini**.  
  
## <a name="conditions-on-items-and-properties"></a>Koşullara öğeleri ve özellikleri  
 Bir yapı sırasında tüm koşullar tam olarak dikkate alınır.  
  
 Görüntülenecek özellik değerlerini belirlerken, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yapılandırmaya bağımlı farklı değerlendirilir göz önünde bulundurur özellikleri yeniden yapılandırma bağımsız olarak kabul eder. İçin özellikleri yeniden yapılandırma bağımlı olarak kabul eder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayarlar `Configuration` ve `Platform` özellikleri uygun şekilde ve bildirir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projeyi yeniden değerlendirin. Özellikleri yeniden yapılandırma bağımsız olarak, koşulların nasıl değerlendirileceği belirsiz olarak kabul eder.  
  
 Öğesi içinde görüntülenip görüntülenmeyeceğini öğelerdeki koşullu ifadeler karar verme amacıyla her zaman yoksayıldı **Çözüm Gezgini**.  
  
## <a name="debugging"></a>Hata Ayıklama  
 Bul ve çıktı derlemesine başlatın ve hata ayıklayıcıyı eklemek amacıyla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] özelliklere sahip olması `OutputPath`, `AssemblyName`, ve `OutputType` doğru şekilde tanımlanmış. Derleme işlemi derleyicinin oluşturmasıyla iliştirmek hata ayıklayıcı başarısız olur bir *.pdb* dosya.  
  
## <a name="design-time-target-execution"></a>Tasarım zamanı hedef yürütme  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir projeyi yüklediğinde belirli adları olan hedefleri yürütmeyi dener. Bu hedefler arasında `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths`, ve `CopyRunEnvironmentFiles`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bu hedefleri derleyicinin IntelliSense sağlamak için başlatılabilir, hata ayıklayıcının başlatılabilmesi ve Çözüm Gezgini'nde gösterilen başvuruların çözümlenebilmesi için çalıştırır. Bu hedefler mevcut değilse projeyi yüklemek ve tasarım zamanı deneyimi ancak doğru şekilde derlenmesi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tam işlevsel olmayacaktır.  
  
##  <a name="edit-project-files-in-visual-studio"></a>Visual Studio'da proje dosyalarını düzenleme  
 Düzenlenecek bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] doğrudan projesi, proje dosyası Visual Studio XML düzenleyicisinde açabilirsiniz.  
  
#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Visual Studio'da bir proje dosyasının yüklemesini kaldırmak ve düzenlemek için  
  
1.  İçinde **Çözüm Gezgini**, proje için kısayol menüsünü açın ve ardından **projeyi**.  
  
     Proje işaretlenmiş **(kullanılamıyor)**.  
  
2.  İçinde **Çözüm Gezgini**, kullanılamayan projenin kısayol menüsünü açın ve ardından **Düzenle \<proje dosyası >**.  
  
     Proje dosyası Visual Studio XML Düzenleyicisi'nde açılır.  
  
3.  Düzenleyin, kaydedin ve ardından Proje dosyasını kapatın.  
  
4.  İçinde **Çözüm Gezgini**, kullanılamayan projenin kısayol menüsünü açın ve ardından **projeyi**.  
  
## <a name="intellisense-and-validation"></a>IntelliSense ve doğrulama  
 Proje dosyalarını düzenlemek için XML düzenleyicisini kullanırken, IntelliSense ve doğrulama tarafından yönlendirilir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] şema dosyaları. Bunlar bulunabilir şema önbelleğinde yüklü  *\<Visual Studio yükleme dizini > \Xml\Schemas\1033\MSBuild*.  
  
 Çekirdek [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] türleri *Microsoft.Build.Core.xsd'de* ve tarafından kullanılan ortak türler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tanımlanan *Microsoft.Build.CommonTypes.xsd*. Şemaları özel öğe türü adları, özellikler ve görevler için IntelliSense ve doğrulama edinecek olmanızdır özelleştirmek için düzenleme ya da olabilir. *kullanabilmek üzere*, veya CommonTypes veya Core içeren kendi şemanızı oluşturabilirsiniz şemalar. Düzenleyicisi'ni kullanarak bunu bulmanız XML yönlendirmek için sahip olacak kendi şemanızı oluşturursanız **özellikleri** penceresi.  
  
## <a name="edit-loaded-project-files"></a>Yüklenmiş proje dosyalarını düzenleme  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Proje dosyaları ve proje dosyaları tarafından içe aktarılan dosyaların içeriğini önbelleğe alır. Bir yüklenmiş proje dosyasını düzenliyorsanız, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otomatik olarak, değişikliklerin etkili olması için projeyi yeniden yüklemenizi ister. Ancak yüklenmiş bir proje tarafından içe aktarılan bir dosyayı düzenlerseniz, herhangi bir yeniden yükleme istemi olmayacaktır ve kaldırma ve değişikliklerin etkili el ile yapmak için projeyi yeniden yükleyin.  
  
## <a name="output-groups"></a>Çıkış grupları  
 İçinde tanımlanan çeşitli hedefler *Microsoft.Common.targets* sonlanan adlara sahip `OutputGroups` veya `OutputGroupDependencies`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bu hedefleri proje çıktılarının tam listelerini almak için çağırır. Örneğin, `SatelliteDllsProjectOutputGroup` hedef bir yapının oluşturacağı tüm uydu derlemelerin bir listesini oluşturur. Bu çıktı grupları yayımlama, dağıtım ve projeden projeye başvurular gibi özellikler tarafından kullanılır. Bunları tanımlamayan projeler yükleyecek ve oluşturacaktır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ancak bazı özellikler düzgün çalışmayabilir.  
  
## <a name="reference-resolution"></a>Başvuru çözümleme  
 Başvuru çözümleme, gerçek derlemeleri bulmak için bir proje dosyasında depolanan başvuru öğelerini kullanma işlemidir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] içinde her başvurunun özelliklerini ayrıntılı göstermek için başvuru çözümlemesini tetiklemelidir **özellikleri** penceresi. Aşağıdaki liste, üç başvuru türünü ve bunların nasıl kullanıldığını açıklar.  
  
- Bütünleştirilmiş kod başvuruları:  
  
   Proje sistemi bir hedefi iyi bilinen adıyla çağırır `ResolveAssemblyReferences`. Bu hedef, öğe türü adı öğeleriyle üretmelidir `ReferencePath`. Bu öğelerin her biri bir öğe belirtimine sahip olmalıdır (değerini `Include` bir öğenin özniteliğini) içeren başvuru tam yolu. Öğeleri aracılığıyla aşağıdaki yeni meta veriler ek olarak geçirilen girdi öğelerinin tüm meta verilerine sahip olmanız gerekir:  
  
  - `CopyLocal`, derlemenin çıktı klasörüne kopyalanıp kopyalanmayacağını belirten true veya false ayarlayın.  
  
  - `OriginalItemSpec`, başvurunun Asıl öğe belirtimini içeren.  
  
  - `ResolvedFrom`, bunu çözümlenirse "{TargetFrameworkDirectory}" kümesi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dizin.  
  
- COM başvuruları:  
  
   Proje sistemi bir hedefi iyi bilinen adıyla çağırır `ResolveCOMReferences`. Bu hedef, öğe türü adı öğeleriyle üretmelidir `ComReferenceWrappers`. Bu öğelerin her biri, COM başvurusu için birlikte çalışabilirlik derlemesine giden tam yolu içeren bir öğe belirtimine sahip olmalıdır. Öğeleri girdi öğelerinin geçilen, ayrıca yeni meta veri adı ile tüm meta verilerine de sahip `CopyLocal`, derlemenin çıktı klasörüne kopyalanıp kopyalanmayacağını belirten true veya false ayarlayın.  
  
- Yerel başvurular  
  
   Proje sistemi bir hedefi iyi bilinen adıyla çağırır `ResolveNativeReferences`. Bu hedef, öğe türü adı öğeleriyle üretmelidir `NativeReferenceFile`. Öğeleri geçtiğini, meta verilerin adlı yeni bir ek girdi öğelerinin tüm meta verilerine olmalıdır `OriginalItemSpec`, başvurunun Asıl öğe belirtimini içeren.  
  
## <a name="performance-shortcuts"></a>Performans kısayolları  
 Visual Studio UI'de hata ayıklamayı başlatırsanız (F5 tuşunu seçerek veya seçerek **hata ayıklama** > **hata ayıklamayı Başlat** menü çubuğundaki), yapı işlemi hızlı bir güncelleştirme kontrolü geliştirmek için kullanır. performans. Burada özelleştirilmiş yapıların dahili hale gelen dosyalar oluşturma bazı durumlarda, hızlı güncelleştirme kontrolü değiştirilen dosyaları düzgün tanımlamaz. Daha kapsamlı güncelleme kontrolleri gereken projeleri hızlı denetimi ortam değişkenini ayarlayarak devre dışı kapatabilir `DISABLEFASTUPTODATECHECK=1`. Alternatif olarak, proje bu projeye ya da projenin içe aktardığı bir dosya bir MSBuild özelliği olarak ayarlayabilirsiniz.  
  
 Visual Studio'daki normal yapılarda, hızlı güncelleştirme denetimleri geçerli değildir ve bir komut isteminde derlemenin çağırdığınız gibi Proje derlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Visual Studio derleme işlemini genişletme](../msbuild/how-to-extend-the-visual-studio-build-process.md)   
 [IDE içinden derleme Başlat](../msbuild/starting-a-build-from-within-the-ide.md)   
 [.NET Framework uzantılarını kaydetme](../msbuild/registering-extensions-of-the-dotnet-framework.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [Öğe unsuru (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Özellik öğesi (MSBuild)](../msbuild/property-element-msbuild.md)   
 [Hedef öğe (MSBuild)](../msbuild/target-element-msbuild.md)   
 [CSC görevi](../msbuild/csc-task.md)   
 [Vbc görevi](../msbuild/vbc-task.md)