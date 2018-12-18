---
title: Çözüm Gezgini filtresini genişletme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf43243abc361df6c5b32b0e71e966c61a501b52
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498794"
---
# <a name="extend-the-solution-explorer-filter"></a>Çözüm Gezgini filtresini genişletme
Genişletebileceğiniz **Çözüm Gezgini** işlevselliği göstermek veya gizlemek farklı dosyalar için filtre. Örneğin, yalnızca C# sınıf üreteci dosyalarında gösteren filtre oluşturabilir **Çözüm Gezgini**gibi bu izlenecek yol gösterir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="create-a-visual-studio-package-project"></a>Visual Studio Paket projesi oluşturun  
  
1.  Adlı bir VSIX projesi oluşturun `FileFilter`. Adlı bir özel komut öğesi şablonu ekleme **FileFilter**. Daha fazla bilgi için [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Bir başvuru ekleyin `System.ComponentModel.Composition` ve `Microsoft.VisualStudio.Utilities`.  
  
3.  Menü komutu görünür yapmak **Çözüm Gezgini** araç çubuğu. Açık *FileFilterPackage.vsct* dosya.  
  
4.  Değişiklik `<Button>` aşağıdaki engelle:  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### <a name="update-the-manifest-file"></a>Bildirim dosyasını güncelleştirme  
  
1.  İçinde *source.extension.vsixmanifest* dosyasında, bir MEF Bileşeni bir varlığı ekleyin.  
  
2.  Üzerinde **varlıklar** sekmesini, **yeni** düğmesi.  
  
3.  İçinde **türü** alan öğesini **Microsoft.VisualStudio.MefComponent**.  
  
4.  İçinde **kaynak** alan öğesini **mevcut çözümde bir proje**.  
  
5.  İçinde **proje** alan öğesini **FileFilter**ve ardından **Tamam** düğmesi.  
  
### <a name="add-the-filter-code"></a>Filtreleme kodunu ekleyin  
  
1.  Bazı GUID'lere ekleme *FileFilterPackageGuids.cs* dosyası:  
  
    ```csharp  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  Adlı FileFilter projeye bir sınıf dosyası ekleyin *FileNameFilter.cs*.  
  
3.  Boş ad alanı ve boş sınıf aşağıdaki kodla değiştirin.  
  
     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` Yöntemi çözümün kök içeren koleksiyonu alır (`rootItems`) ve filtreye dahil edilecek öğelerin koleksiyonunu döndürür.  
  
     `ShouldIncludeInFilter` Yöntemi öğeleri filtreler **Çözüm Gezgini** belirttiğiniz şartıyla göre hiyerarşisi.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Text.RegularExpressions;  
    using System.Threading.Tasks;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
  
    namespace FileFilter  
    {  
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component  
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]  
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider  
        {  
            SVsServiceProvider svcProvider;  
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
            // Constructor required for MEF composition  
            [ImportingConstructor]  
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)  
            {  
                this.svcProvider = serviceProvider;  
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
            }  
  
            // Returns an instance of Create filter class.  
            protected override HierarchyTreeFilter CreateFilter()  
            {  
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);  
            }  
  
            // Regex pattern for CSharp factory classes  
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";  
  
            // Implementation of file filtering  
            private sealed class FileNameFilter : HierarchyTreeFilter  
            {  
                private readonly Regex regexp;  
                private readonly IServiceProvider svcProvider;  
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
                public FileNameFilter(  
                    IServiceProvider serviceProvider,  
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,  
                    string fileNamePattern)  
                {  
                    this.svcProvider = serviceProvider;  
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);  
                }  
  
                // Gets the items to be included from this filter provider.   
                // rootItems is a collection that contains the root of your solution  
                // Returns a collection of items to be included as part of the filter  
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)  
                {  
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);  
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;  
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(  
                                        root.HierarchyIdentity.NestedHierarchy,  
                                        CancellationToken);  
  
                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(  
                        sourceItems,  
                        ShouldIncludeInFilter,  
                        CancellationToken);  
                    return includedItems;  
                }  
  
                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>  
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)  
                {  
                    if (hierarchyItem == null)  
                    {  
                        return false;  
                    }  
                    return this.regexp.IsMatch(hierarchyItem.Text);  
                }  
            }  
        }  
    }  
  
    ```  
  
4.  İçinde *FileFilter.cs*komut yerleştirme kaldırmak ve kod FileFilter oluşturucudan işleme. Sonuç şu şekilde görünmelidir:  
  
    ```csharp  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     Kaldırma `ShowMessageBox()` yöntemi de.  
  
5.  İçinde *FileFilterPackage.cs*, değiştirin `Initialize()` aşağıdaki yöntemi:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### <a name="test-your-code"></a>Kodunuzu test etme  
  
1.  Derleme ve projeyi çalıştırın. Visual Studio ikinci bir örneğini görünür. Bu, deneysel örneği olarak adlandırılır.  
  
2.  Bir C# projesi Visual Studio'nun deneysel örneğinde açın.  
  
3.  Üzerinde eklediğiniz düğmeyi bulun **Çözüm Gezgini** araç çubuğu. Sol dördüncü düğmesinden olmalıdır.  
  
4.  Düğmesine tıklayın, tüm dosyaları filtrelenmesi gereken ve görmelisiniz **tüm öğeler görünümden filtrelendi.** içinde **Çözüm Gezgini**.