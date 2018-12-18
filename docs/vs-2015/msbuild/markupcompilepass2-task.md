---
title: MarkupCompilePass2 görevi | Microsoft Docs
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
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea61e827bfae47c3bea961cb15c208f585aa6ed9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179247"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> Görevi gerçekleştiren ikinci geçiş işaretlemesi derleme üzerinde [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] başvuru türleri aynı projedeki dosyaları.  
  
## <a name="task-parameters"></a>Görev parametreleri  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|İsteğe bağlı **Boole** parametresi.<br /><br /> Ayrı bir görevin çalıştırılıp çalıştırılmayacağını belirtir <xref:System.AppDomain>. Bu parametre döndürürse **false**, görev aynı şekilde çalışır <xref:System.AppDomain> olarak [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)], ve daha hızlı çalışır. Parametre döndürürse **true**, görev, bir saniye içinde çalışır <xref:System.AppDomain> olan gelen yalıtılmış [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] ve daha yavaş çalışır.|  
|`AssembliesGeneratedDuringBuild`|İsteğe bağlı **String []** parametresi.<br /><br /> Derleme işlemi sırasında değiştirmek derlemelerin başvurularını belirtir. Örneğin, bir [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] çözüm derlenmiş çıktısını başka bir projeye başvuran bir proje içerebilir. Bu durumda, ikinci projenizin derlenen Çıkışta eklenebilen **AssembliesGeneratedDuringBuild**.<br /><br /> Not: **AssembliesGeneratedDuringBuild** eksiksiz bir yapı çözümü tarafından oluşturulan derlemelere başvurular içermelidir.|  
|`AssemblyName`|Gerekli **dize** parametresi.<br /><br /> Kısa bir proje için üretilen derleme adını belirtir. Örneğin, bir proje oluşturma bir [!INCLUDE[TLA#tla_win](../includes/tlasharptla-win-md.md)] yürütülebilir dosya adı olan **WinExeAssembly.exe**, **AssemblyName** parametresinin değerini **WinExeAssembly**.|  
|`GeneratedBaml`|İsteğe bağlı **Itaskıtem []** çıkış parametresi.<br /><br /> Oluşturulan dosyaların listesini içeren [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçimi.|  
|`KnownReferencePaths`|İsteğe bağlı **String []** parametresi.<br /><br /> Hiç derleme işlemi sırasında değiştirilen derlemelerin başvurularını belirtir. Bulunan derlemeleri içerir [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)], bir [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)] yükleme dizinini ve benzeri.|  
|`Language`|Gerekli **dize** parametresi.<br /><br /> Derleyici destekleyen yönetilen dilini belirtir. Geçerli seçenekler şunlardır **C#**, **VB**, **JScript**, ve **C++**.|  
|`LocalizationDirectivesToLocFile`|İsteğe bağlı **dize** parametresi.<br /><br /> Her kaynak için yerelleştirme bilgisi oluşturmak nasıl belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya. Geçerli seçenekler şunlardır **hiçbiri**, **CommentsOnly**, ve **tüm**.|  
|`OutputPath`|Gerekli **dize** parametresi.<br /><br /> Dizini, belirtir oluşturulan [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçimi dosyalar oluşturulur.|  
|`OutputType`|Gerekli **dize** parametresi.<br /><br /> Bir proje tarafından oluşturulan derleme türünü belirtir. Geçerli seçenekler şunlardır **winexe**, **exe**, **Kitaplığı**, ve **netmodule**.|  
|`References`|İsteğe bağlı **Itaskıtem []** parametresi.<br /><br /> Kullanılan türleri içeren derlemeler için başvurular dosyalarından listesini belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyaları. Bir başvurudur tarafından oluşturulan derlemeye <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> önce çalıştırılması gereken görev <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> görev.|  
|`RootNamespace`|İsteğe bağlı **dize** parametresi.<br /><br /> Projesi içinde olan sınıfları kök ad alanını belirtir. **RootNamespace** oluşturulmuş bir yönetilen kod varsayılan ad alanı olarak da kullanılan dosyası karşılık gelen [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya içermez `x:Class` özniteliği.|  
|`XAMLDebuggingInformation`|İsteğe bağlı **Boole** parametresi.<br /><br /> Zaman **true**, tanılama bilgilerini oluşturulur ve derlenmiş dahil [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] hata ayıklama yardımcı olmak için.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çalıştırmadan önce **MarkupCompilePass2**, tarafından kullanılan türler içeren geçici bir derleme oluşturmalıdır [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] , biçimlendirme derleme geçişi ertelenmiş dosyaları. Çalıştırarak geçici derlemesi oluştur **GenerateTemporaryTargetAssembly** görev.  
  
 Oluşturulan geçici derlemesine bir başvuru için sağlanan <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> çalıştığında izin vererek [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] , derleme, ilk biçimlendirme derlemede ertelenmiş dosyaları geçirmek için ikili biçimi artık derlenecek.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> ikinci gerçekleştirmek için görev derleme geçirin.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass2Task">  
    <MarkupCompilePass2   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
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



