---
title: MarkupCompilePass2 görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 360a6c4d3e389583eece1adcc915f26091283653
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942393"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 görevi

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> Görevi gerçekleştiren ikinci geçiş işaretlemesi derleme üzerinde [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] başvuru türleri aynı projedeki dosyaları.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | İsteğe bağlı **Boole** parametresi.<br /><br /> Ayrı bir görevin çalıştırılıp çalıştırılmayacağını belirtir <xref:System.AppDomain>. Bu parametre döndürürse **false**, görev aynı şekilde çalışır <xref:System.AppDomain> olarak [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)], ve daha hızlı çalışır. Parametre döndürürse **true**, görev, bir saniye içinde çalışır <xref:System.AppDomain> olan gelen yalıtılmış [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] ve daha yavaş çalışır. |
| `AssembliesGeneratedDuringBuild` | İsteğe bağlı **String []** parametresi.<br /><br /> Derleme işlemi sırasında değiştirmek derlemelerin başvurularını belirtir. Örneğin, bir Visual Studio çözümü derlenmiş çıktısını başka bir projeye başvuran bir proje içerebilir. Bu durumda, ikinci projenizin derlenen Çıkışta eklenebilen **AssembliesGeneratedDuringBuild**.<br /><br /> Not: **AssembliesGeneratedDuringBuild** eksiksiz bir yapı çözümü tarafından oluşturulan derlemelere başvurular içermelidir. |
| `AssemblyName` | Gerekli **dize** parametresi.<br /><br /> Kısa bir proje için üretilen derleme adını belirtir. Örneğin, bir proje oluşturma bir [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] yürütülebilir dosya adı olan *WinExeAssembly.exe*, **AssemblyName** parametresinin değerini **WinExeAssembly**. |
| `GeneratedBaml` | İsteğe bağlı **Itaskıtem []** çıkış parametresi.<br /><br /> Oluşturulan dosyaların listesini içeren [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ikili biçimi. |
| `KnownReferencePaths` | İsteğe bağlı **String []** parametresi.<br /><br /> Hiç derleme işlemi sırasında değiştirilen derlemelerin başvurularını belirtir. Bulunan derlemeleri içerir [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], bir [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] yükleme dizinini ve benzeri. |
| `Language` | Gerekli **dize** parametresi.<br /><br /> Derleyici destekleyen yönetilen dilini belirtir. Geçerli seçenekler şunlardır **C#**, **VB**, **JScript**, ve **C++**. |
| `LocalizationDirectivesToLocFile` | İsteğe bağlı **dize** parametresi.<br /><br /> Her kaynak için yerelleştirme bilgisi oluşturmak nasıl belirtir [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosya. Geçerli seçenekler şunlardır **hiçbiri**, **CommentsOnly**, ve **tüm**. |
| `OutputPath` | Gerekli **dize** parametresi.<br /><br /> Dizini, belirtir oluşturulan [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ikili biçimi dosyalar oluşturulur. |
| `OutputType` | Gerekli **dize** parametresi.<br /><br /> Bir proje tarafından oluşturulan derleme türünü belirtir. Geçerli seçenekler şunlardır **winexe**, **exe**, **Kitaplığı**, ve **netmodule**. |
| `References` | İsteğe bağlı **Itaskıtem []** parametresi.<br /><br /> Kullanılan türleri içeren derlemeler için başvurular dosyalarından listesini belirtir [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyaları. Bir başvurudur tarafından oluşturulan derlemeye <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> önce çalıştırılması gereken görev <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> görev. |
| `RootNamespace` | İsteğe bağlı **dize** parametresi.<br /><br /> Projesi içinde olan sınıfları kök ad alanını belirtir. **RootNamespace** oluşturulmuş bir yönetilen kod varsayılan ad alanı olarak da kullanılan dosyası karşılık gelen [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosya içermez `x:Class` özniteliği. |
| `XAMLDebuggingInformation` | İsteğe bağlı **Boole** parametresi.<br /><br /> Zaman **true**, tanılama bilgilerini oluşturulur ve derlenmiş dahil [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] hata ayıklama yardımcı olmak için. |

## <a name="remarks"></a>Açıklamalar

Çalıştırmadan önce **MarkupCompilePass2**, tarafından kullanılan türler içeren geçici bir derleme oluşturmalıdır [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] , biçimlendirme derleme geçişi ertelenmiş dosyaları. Çalıştırarak geçici derlemesi oluştur **GenerateTemporaryTargetAssembly** görev.

Oluşturulan geçici derlemesine bir başvuru için sağlanan <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> çalıştığında izin vererek [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] , derleme, ilk biçimlendirme derlemede ertelenmiş dosyaları geçirmek için ikili biçimi artık derlenecek.

## <a name="example"></a>Örnek

Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> ikinci gerçekleştirmek için görev derleme geçirin.

```xml
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

## <a name="see-also"></a>Ayrıca bkz.

[WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)  
[WPF MSBuild görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)  
[MSBuild başvurusu](../msbuild/msbuild-reference.md)  
[MSBuild görev başvurusu](../msbuild/msbuild-task-reference.md)  
[Bir WPF uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
[WPF XAML tarayıcı uygulamalarına genel bakış](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)