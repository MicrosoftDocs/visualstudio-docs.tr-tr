---
title: MarkupCompilePass1 görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
ms.assetid: 693d6945-fd6f-4698-8f64-9dfcb71052d3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7db6923b0a729d909e22136bd3994af45dfe1da9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189364"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Görev dönüştürür yerelleştirilemeyen [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] proje dosyaları için derlenmiş ikili biçimi.  
  
## <a name="task-parameters"></a>Görev parametreleri  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AllGeneratedFiles`|İsteğe bağlı **Itaskıtem []** çıkış parametresi.<br /><br /> Tarafından oluşturulan dosyaların tam bir listesini içeren <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> görev.|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|İsteğe bağlı **Boole** parametresi.<br /><br /> Ayrı bir görevin çalıştırılıp çalıştırılmayacağını belirtir <xref:System.AppDomain>. Bu parametre döndürürse **false**, görev aynı şekilde çalışır <xref:System.AppDomain> olarak [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] ve daha hızlı çalışır. Parametre döndürürse **true**, görev, bir saniye içinde çalışır <xref:System.AppDomain> olan gelen yalıtılmış [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] ve daha yavaş çalışır.|  
|`ApplicationMarkup`|İsteğe bağlı **Itaskıtem []** parametresi.<br /><br /> Uygulama tanımının adını belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya.|  
|`AssembliesGeneratedDuringBuild`|İsteğe bağlı **String []** parametresi.<br /><br /> Derleme işlemi sırasında değiştirmek derlemelerin başvurularını belirtir. Örneğin, bir [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] çözüm derlenmiş çıktısını başka bir projeye başvuran bir proje içerebilir. Bu durumda, ikinci projenizin derlenen Çıkışta eklenebilen **AssembliesGeneratedDuringBuild** parametresi.<br /><br /> Not: **AssembliesGeneratedDuringBuild** parametresi, eksiksiz bir yapı çözümü tarafından oluşturulan derlemelere başvurular içermelidir.|  
|`AssemblyName`|Gerekli **dize** parametresi.<br /><br /> Kısa bir proje için üretilen derleme adını belirtir. Örneğin, bir proje oluşturma bir [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] yürütülebilir dosya adı olan **WinExeAssembly.exe**, **AssemblyName** parametresinin değerini **WinExeAssembly**.|  
|`AssemblyPublicKeyToken`|İsteğe bağlı **dize** parametresi.<br /><br /> Derleme için genel anahtar belirtecini belirtir.|  
|`AssemblyVersion`|İsteğe bağlı **dize** parametresi.<br /><br /> Derlemenin sürüm numarasını belirtir.|  
|`ContentFiles`|İsteğe bağlı **Itaskıtem []** parametresi.<br /><br /> Gevşek içerik dosyalarının listesini belirtir.|  
|`DefineConstants`|İsteğe bağlı **dize** parametresi.<br /><br /> Belirten geçerli değerini **DefineConstants**, tutulur. hedef derleme oluşturma etkiler; Bu parametre değiştirdiyseniz, hedef derleme genel API'de değiştirilebilir ve derlenmesini [!INCLUDE[TLA2#tla_titlexaml](../includes/tla2sharptla-titlexaml-md.md)] başvuru yerel türleri dosyaları etkilenebilir.|  
|`ExtraBuildControlFiles`|İsteğe bağlı **Itaskıtem []** parametresi.<br /><br /> Yeniden derleme olup olmadığını kontrol dosyaların listesini belirtir tetiklendiğinde <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> görev yeniden çalıştırır; bunlardan birini değişiklikleri dosyalarını yeniden derleme tetiklenecek.|  
|`GeneratedBamlFiles`|İsteğe bağlı **Itaskıtem []** çıkış parametresi.<br /><br /> Oluşturulan dosyaların listesini içeren [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçimi.|  
|`GeneratedCodeFiles`|İsteğe bağlı **Itaskıtem []** çıkış parametresi.<br /><br /> Oluşturulan yönetilen kod dosyalarının listesini içerir.|  
|`GeneratedLocalizationFiles`|İsteğe bağlı **Itaskıtem []** çıkış parametresi.<br /><br /> Her biri için üretilen yerelleştirme dosyalarının listesini içeren yerelleştirilebilir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya.|  
|`HostInBrowser`|İsteğe bağlı **dize** parametresi.<br /><br /> Oluşturulan derleme olup olmadığını belirten bir [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)]. Geçerli seçenekler şunlardır **true** ve **false**. Varsa **true**, kodu, tarayıcı barındırma desteklemek için oluşturulur.|  
|`KnownReferencePaths`|İsteğe bağlı **String []** parametresi.<br /><br /> Derleme işlemi sırasında değiştirmeyin derlemelerin başvurularını belirtir. Bulunan derlemeleri içerir [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)], bir [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)] yükleme dizinini ve benzeri.|  
|`Language`|Gerekli **dize** parametresi.<br /><br /> Derleyici destekleyen yönetilen dilini belirtir. Geçerli seçenekler şunlardır **C#**, **VB**, **JScript**, ve **C++**.|  
|`LanguageSourceExtension`|İsteğe bağlı **dize** parametresi.<br /><br /> Oluşturulan yönetilen kod dosyasının uzantısı eklenen uzantısı belirtir:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Varsa **LanguageSourceExtension** parametresi ile belirli bir değere ayarlı değil, bir dil için varsayılan kaynak dosya adı uzantısı kullanılır: **.vb** için [!INCLUDE[TLA#tla_visualb](../includes/tlasharptla-visualb-md.md)], **.csharp** için [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)].|  
|`LocalizationDirectivesToLocFile`|İsteğe bağlı **dize** parametresi.<br /><br /> Her kaynak için yerelleştirme bilgisi oluşturmak nasıl belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya. Geçerli seçenekler şunlardır **hiçbiri**, **CommentsOnly**, ve **tüm**.|  
|`OutputPath`|Gerekli **dize** parametresi.<br /><br /> Dizini, belirtir oluşturulan yönetilen kod dosyaları ve [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçimi dosyalar oluşturulur.|  
|`OutputType`|Gerekli **dize** parametresi.<br /><br /> Bir proje tarafından oluşturulan derleme türünü belirtir. Geçerli seçenekler şunlardır **winexe**, **exe**, **Kitaplığı**, ve **netmodule**.|  
|`PageMarkup`|İsteğe bağlı **Itaskıtem []** parametresi.<br /><br /> Bir listesini belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyalar işlenecek.|  
|`References`|İsteğe bağlı **Itaskıtem []** parametresi.<br /><br /> Kullanılan türleri içeren derlemeler için başvurular dosyalarından listesini belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyaları.|  
|`RequirePass2ForMainAssembly`|İsteğe bağlı **Boole** çıkış parametresi.<br /><br /> Proje yerelleştirilemeyen içerip içermediğini gösteren [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] başvuru ana derlemeye gömülü yerel türleri dosyaları.|  
|`RequirePass2ForSatelliteAssembly`|İsteğe bağlı **Boole** çıkış parametresi.<br /><br /> Proje yerelleştirilebilir içerip içermediğini gösteren [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] başvuru ana derlemede gömülü yerel türleri dosyaları.|  
|`RootNamespace`|İsteğe bağlı **dize** parametresi.<br /><br /> Projesi içinde olan sınıfları kök ad alanını belirtir. **RootNamespace** oluşturulmuş bir yönetilen kod varsayılan ad alanı olarak da kullanılan dosyası karşılık gelen [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya içermez `x:Class` özniteliği.|  
|`SourceCodeFiles`|İsteğe bağlı **Itaskıtem []** parametresi.<br /><br /> Geçerli proje için kod dosyaları listesini belirtir. Listenin oluşturulan dile özgü yönetilen kod dosyaları içermez.|  
|`UICulture`|İsteğe bağlı **dize** parametresi.<br /><br /> UI kültürü için uydu derleme içinde belirtir oluşturulan [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçimi dosyaları katıştırıldığı. Varsa **UICulture** ayarlı değil, oluşturulan [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçimi dosyaları ana derlemede gömülü.|  
|`XAMLDebuggingInformation`|İsteğe bağlı **Boole** parametresi.<br /><br /> Zaman **true**, tanılama bilgilerini oluşturulur ve derlenmiş dahil [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] hata ayıklama yardımcı olmak için.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Görev genellikle derler [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçime ve kod dosyaları oluşturur. Varsa bir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya aynı projede tanımlanan türlere başvuru içeriyorsa, kendi derleme için ikili biçimi tarafından Ertelenen **MarkupCompilePass1** ikinci bir biçimlendirme derleme geçişine ( **MarkupCompilePass2**). Bu tür dosyaları yerel olarak tanımlanan başvurulan tür derlenmiş kadar beklemeniz gerekir çünkü ertelenmiş kendi derleme olması gerekir. Ancak, bir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyasının bir `x:Class` özniteliği <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> dile özel kod dosyası üretir.  
  
 A [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyasıdır kullanan öğeler içeriyorsa, yerelleştirilebilir `x:Uid` özniteliği:  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 A [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyasına başvuran yerel olarak tanımlı bir tür, bildirir, bir [!INCLUDE[TLA#tla_xml](../includes/tlasharptla-xml-md.md)] kullanan ad alanı `clr-namespace` değeri, geçerli projedeki bir ad alanına başvuruda bulunmak için:  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"  
    >  
    <Grid>  
      <Grid.Resources>  
        <localNameSpace:LocalType x:Key="localType" />  
      </Grid.Resources>  
      ...  
    </Grid>  
</Page>  
```  
  
 Varsa [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya yerelleştirilebilir veya yerel olarak tanımlı bir türe başvuruyor, ikinci bir işaretleme derleme geçişi gereklidir çalışmasını gerektiren [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) ardından [ MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç dönüştürülecek gösterilmektedir `Page` [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyalarını ikili biçimi dosyalarına. `Page1` bir türe başvuru içeren `Class1`, projenin kök ad alanı ve bu nedenle, bu işaretleme derleme geçişi dosyalarında ikili biçimi dönüştürülmez. Bunun yerine, [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) çalıştırılır ve takip [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass1Task">  
    <MarkupCompilePass1   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      ApplicationMarkup="App.xaml"  
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"  
      SourceCodeFiles="Class1.cs"  
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)   
 [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [WPF uygulaması (WPF) oluşturma](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](http://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)



