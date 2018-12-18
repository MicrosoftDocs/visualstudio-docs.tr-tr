---
title: Araç penceresine arama ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b060261bec61859f33d99ec3f666e1285413592
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498570"
---
# <a name="add-search-to-a-tool-window"></a>Araç penceresine arama ekleme
Uzantınızı bir araç penceresi güncelle, Visual Studio'da başka bir yerde görünür aynı arama işlevleri ekleyebilirsiniz. Bu işlev, aşağıdaki özellikleri içerir:  
  
-   Her zaman özel bir araç çubuğu alanında bulunan bir arama kutusu.  
  
-   Arama kutusuna kendisini yayılan bir İlerleme göstergesi.  
  
-   Her bir karakter (hızlı arama) girilmez veya yalnızca seçtiğiniz sonra sonuçları göster olanağı **Enter** anahtarı (isteğe bağlı arama).  
  
-   Koşulları, size en yakın zamanda araştırdık gösteren bir liste.  
  
-   Aramaları belirli alanlar veya arama hedefleri yönlerini göre filtreleme özelliği.  
  
Bu izlenecek yolu takip ederek, aşağıdaki görevlerin nasıl gerçekleştirileceğini öğreneceksiniz:  
  
1.  VSPackage projesi oluşturun.  
  
2.  Salt-okunur TextBox ile bir UserControl içeren bir araç penceresi oluşturun.  
  
3.  Araç penceresine arama kutusuna ekleyin.  
  
4.  Arama uygulaması ekleyin.  
  
5.  Hızlı arama ve bir ilerleme çubuğu görüntülenmesini sağlar.  
  
6.  Ekleme bir **eşleşen servis talebi** seçeneği.  
  
7.  Ekleme bir **arama yalnızca çift çizgileri** filtre.  
  
## <a name="to-create-a-vsix-project"></a>Bir VSIX projesi oluşturmak için  
  
1.  Adlı bir VSIX projesi oluşturun `TestToolWindowSearch` adlı bir araç penceresi ile **TestSearch**. Bunun yapılması yardıma ihtiyacınız varsa bkz [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Araç penceresi oluşturma  
  
1.  İçinde `TestToolWindowSearch` projesini açarsanız *TestSearchControl.xaml* dosya.  
  
2.  Varolan `<StackPanel>` salt okunur ekleyen aşağıdaki blok blok <xref:System.Windows.Controls.TextBox> için <xref:System.Windows.Controls.UserControl> araç penceresindeki.  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  İçinde *TestSearchControl.xaml.cs* dosyasında, aşağıdaki using deyimi:  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  Kaldırma `button1_Click()` yöntemi.  
  
     İçinde **TestSearchControl** sınıfında, aşağıdaki kodu ekleyin.  
  
     Bu kod, bir ortak ekler <xref:System.Windows.Controls.TextBox> adlı özellik **SearchResultsTextBox** ve adlı bir genel dize özelliği **SearchContent**. Oluşturucu, metin kutusuna SearchResultsTextBox ayarlanır ve SearchContent dizeler yeni satır-ayrılmış kümesi için başlatılır. Metin kutusunun içeriğini de dizeler kümesi için başlatılır.  
  
     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneğinde görünür.  
  
6.  Menü çubuğunda, **görünümü** > **diğer Windows** > **TestSearch**.  
  
     Araç penceresi görünür, ancak henüz arama denetimi görünür değil.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Araç penceresine arama kutusunu eklemek için  
  
1.  İçinde *TestSearch.cs* dosyasında, aşağıdaki kodu ekleyin `TestSearch` sınıfı. Kodu geçersiz kılmalar <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> özellik get erişimcisine döndürür, böylece `true`.  
  
     Aramayı etkinleştirmek için geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> özelliği. <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Sınıfının Implements <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> ve arama sağlamaz bir varsayılan uygulamasını sağlar.  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
3.  Visual Studio'nun deneysel örneğinde açın **TestSearch**.  
  
     Arama denetimi görünür araç penceresinin en üstünde bir **arama** Filigran ve büyütme cam simgesi. Ancak, arama işlemi uygulanmadı çünkü arama henüz işe yaramaz.  
  
## <a name="to-add-the-search-implementation"></a>Arama uygulaması eklemek için  
 Üzerinde arama etkinleştirdiğinizde bir <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>gibi önceki yordamda bir konak araç penceresi oluşturur. Bu konak, ayarlar ve her zaman bir arka plan iş parçacığında ortaya çıkan arama işlemlerini yönetir. Çünkü <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> sınıfı arama ana ve ayarı oluşturulmasını arama yukarı yönetir, yalnızca bir arama görevi oluşturma ve arama yöntemi sağlar. Arama işlemi bir arka plan iş parçacığında oluşur ve araç penceresi denetimini çağrıları UI iş parçacığı üzerinde oluşur. Bu nedenle, kullanmalısınız <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> denetimi ile ilgili yaptığınız çağrıları yönetmek için yöntemi.  
  
1.  İçinde *TestSearch.cs* dosyasında, aşağıdaki ekleyin `using` ifadeleri:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Runtime.InteropServices;  
    using System.Text;  
    using System.Windows.Controls;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
2.  İçinde `TestSearch` sınıfında, aşağıdaki eylemleri gerçekleştirir aşağıdaki kodu ekleyin:  
  
    -   Geçersiz kılmalar <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> arama görevi oluşturmak için yöntemi.  
  
    -   Geçersiz kılmalar <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> metin kutusunun durumunu geri yüklemek için yöntemi. Bir kullanıcı arama görevi ve ne zaman bir kullanıcı ayarlar veya seçenekleri veya filtreleri dağıtır iptal ettiğinde, bu yöntem çağrılır. Her ikisi de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> UI iş parçacığı üzerinde çağrılır. Bu nedenle, metin kutusu yoluyla erişmeye ihtiyacınız yoksa <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> yöntemi.  
  
    -   Adlı bir sınıf oluşturur `TestSearchTask` öğesinden devralan <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, varsayılan bir uygulama sağlayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.  
  
         İçinde `TestSearchTask`, araç penceresi başvuran özel bir alan oluşturucu ayarlar. Arama yöntemi sağlamak için geçersiz kılma <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> ve <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> yöntemleri. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Yöntemdir burada arama işlemi uygulayabilir. Bu işlem, araması yaparak, metin kutusuna arama sonuçlarını görüntüleme ve arama tamamlandığını bildirmek için bu yöntemin temel sınıf uygulamasını çağırma içerir.  
  
    ```csharp  
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)  
    {  
        if (pSearchQuery == null || pSearchCallback == null)  
            return null;  
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);  
    }  
  
    public override void ClearSearch()  
    {  
        TestSearchControl control = (TestSearchControl)this.Content;  
        control.SearchResultsTextBox.Text = control.SearchContent;  
    }  
  
    internal class TestSearchTask : VsSearchTask  
    {  
        private TestSearch m_toolWindow;  
  
        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)  
            : base(dwCookie, pSearchQuery, pSearchCallback)  
        {  
            m_toolWindow = toolwindow;  
        }  
  
        protected override void OnStartSearch()  
        {  
            // Use the original content of the text box as the target of the search.   
            var separator = new string[] { Environment.NewLine };  
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;  
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);  
  
            // Get the search option.   
            bool matchCase = false;  
            // matchCase = m_toolWindow.MatchCaseOption.Value;   
  
                // Set variables that are used in the finally block.  
                StringBuilder sb = new StringBuilder("");  
                uint resultCount = 0;  
                this.ErrorCode = VSConstants.S_OK;  
  
                try  
                {  
                    string searchString = this.SearchQuery.SearchString;  
  
                    // Determine the results.   
                    uint progress = 0;  
                    foreach (string line in contentArr)  
                    {  
                        if (matchCase == true)  
                        {  
                            if (line.Contains(searchString))  
                            {  
                                sb.AppendLine(line);  
                                resultCount++;  
                            }  
                        }  
                        else  
                            {  
                                if (line.ToLower().Contains(searchString.ToLower()))  
                                {  
                                    sb.AppendLine(line);  
                                    resultCount++;  
                                }  
                            }  
  
                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));   
  
                            // Uncomment the following line to demonstrate the progress bar.   
                            // System.Threading.Thread.Sleep(100);  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        this.ErrorCode = VSConstants.E_FAIL;  
                    }  
                    finally  
                    {  
                        ThreadHelper.Generic.Invoke(() =>  
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
                        this.SearchResults = resultCount;  
                    }  
  
            // Call the implementation of this method in the base class.   
            // This sets the task status to complete and reports task completion.   
            base.OnStartSearch();  
        }  
  
        protected override void OnStopSearch()  
        {  
            this.SearchResults = 0;  
        }  
    }  
    ```  
  
3.  Aşağıdaki adımları gerçekleştirerek arama uygulamanızı test edin:  
  
    1.  Projeyi yeniden derleyin ve hata ayıklamaya başlayın.  
  
    2.  Visual Studio'nun deneysel örneğinde araç penceresini yeniden açın, arama penceresinde bazı arama metni girin ve tıklayın **ENTER**.  
  
         Doğru sonuçlar görüntülenmesi gerekir.  
  
## <a name="to-customize-the-search-behavior"></a>Arama davranışını özelleştirmek için  
 Arama ayarları değiştirerek arama denetiminin nasıl göründüğünü ve nasıl arama gerçekleştirilir çeşitli değişiklikler yapabilirsiniz. Örneğin, (arama kutusuna görünen varsayılan metni) Filigran, en düşük ve en fazla arama denetiminin genişliğini ve bir ilerleme çubuğu gösterilip gösterilmeyeceğini değiştirebilirsiniz. (İsteğe bağlı veya hızlı arama) görünmesini hangi arama sonuçları başlatmak ve koşulları için son arama listesi gösterilip gösterilmeyeceğini noktada da değiştirebilirsiniz. Ayarlarında tam listesini bulabilirsiniz <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> sınıfı.  
  
1.  İçinde * TestSearch.cs* dosyasında, aşağıdaki kodu ekleyin `TestSearch` sınıfı. Bu kodu isteğe bağlı arama yerine hızlı arama sağlayan (yani kullanıcı tıklayın gerekmez **ENTER**). Kodu geçersiz kılmalar `ProvideSearchSettings` yönteminde `TestSearch` varsayılan ayarları değiştirmek gerekli olan sınıf.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Yeni test çözümün yeniden derlenmesi ve hata ayıklayıcıyı yeniden başlatılıyor.  
  
     Arama sonuçları her zaman bir karakter arama kutusuna girin görüntülenir.  
  
3.  İçinde `ProvideSearchSettings` yöntemi, bir ilerleme çubuğu görüntülenmesini sağlar aşağıdaki satırı ekleyin.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,   
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);  
    }  
    ```  
  
     İlerleme çubuğu görünmesini ilerleme bildirilmelidir. İlerleme durumunu bildirmek için aşağıdaki kod açıklamasını kaldırın `OnStartSearch` yöntemi `TestSearchTask` sınıfı:  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Yeterli, işleme ilerleme durumu yavaş çubuğu görünür dosyasında aşağıdaki satırı açıklamadan çıkarın `OnStartSearch` yöntemi `TestSearchTask` sınıfı:  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Yeni ayarları, çözümün yeniden derlenmesi ve hata ayıklamayı başlatma test edin.  
  
     İlerleme çubuğu arama penceresinde (olarak, arama metin kutusu altında mavi bir çizgi) her zaman araması yaptığınızda görünür.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Kendi aramaları iyileştirmek kullanıcıları etkinleştirmek için  
 Kullanıcılar kendi aramaları gibi seçenekleri daraltmak izin verebilirsiniz **eşleşen servis talebi** veya **eşleşen tam sözcük**. Onay kutuları veya düğme olarak görüntülenen komutları olarak görünen seçenekleri boolean, olabilir. Bu kılavuz için bir boolean seçeneği oluşturacaksınız.  
  
1.  İçinde *TestSearch.cs* dosyasında, aşağıdaki kodu ekleyin `TestSearch` sınıfı. Kodu geçersiz kılmalar `SearchOptionsEnum` yöntemi belirli bir seçeneği açıp olup olmadığını algılamak, aramanın uygulanmasını sağlar. Kodda `SearchOptionsEnum` ekler seçeneği için büyük küçük harf duyarlı bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> Numaralandırıcı. Büyük küçük harf duyarlı seçeneğine de olarak kullanılabilir hale getirileceğini `MatchCaseOption` özelliği.  
  
    ```csharp  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
        {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
2.  İçinde `TestSearchTask` aşağıdaki açıklama durumundan çıkarın, sınıf içinde satır `OnStartSearch` yöntemi:  
  
    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```
  
3.  Seçeneğini test edin:  
  
    1.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
    2.  Araç penceresinde metin kutusunun sağ tarafındaki aşağı oku seçin.  
  
         **Eşleşen servis talebi** onay kutusu görüntülenir.  
  
    3.  Seçin **eşleşen servis talebi** onay kutusunu işaretleyin ve ardından bazı aramaları gerçekleştirin.  
  
## <a name="to-add-a-search-filter"></a>Arama filtre eklemek için  
 Kullanıcıların arama hedefleri kümesini iyileştirmek arama filtreleri ekleyebilirsiniz. Örneğin, dosya Gezgini'nde dosyalar üzerinde en son değiştirildikleri tarihleri ve bunların dosya adı uzantıları tarafından filtre uygulayabilirsiniz. Bu kılavuzda, yalnızca çift çizgileri için bir filtre ekleyeceksiniz. Kullanıcı Bu filtre seçtiğinde, arama ana belirttiğiniz dizeleri arama sorgusuna eklenir. Bu dizeler arama yönteminizi belirlemek ve arama hedeflerini buna göre filtreleyin.  
  
1.  İçinde *TestSearch.cs* dosyasında, aşağıdaki kodu ekleyin `TestSearch` sınıfı. Kod uygulayan `SearchFiltersEnum` ekleyerek bir <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> yalnızca satırlar da görünecek biçimde arama sonuçlarını filtrelemek için belirtir.  
  
    ```csharp  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     Arama filtresi arama denetimi görüntüler artık `Search even lines only`. Ne zaman, kullanıcının seçtiği filtre dizesi `lines:"even"` arama kutusunda görünür. Diğer arama ölçütleri filtre olarak aynı anda görünebilir. Arama dizelerini filtre önce Filtre veya her ikisi de sonra görünebilir.  
  
2.  İçinde *TestSearch.cs* dosyasında, aşağıdaki yöntemi ekleyin `TestSearchTask` bulunduğu sınıfı `TestSearch` sınıfı. Şu yöntemleri destekler `OnStartSearch` yöntemi bir sonraki adımda değiştireceksiniz.  
  
    ```csharp  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  İçinde `TestSearchTask` sınıfı, güncelleştirme `OnStartSearch` yöntemini aşağıdaki kod ile. Bu değişiklik, filtre desteklemek için kodu güncelleştirir.  
  
    ```csharp  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);  
  
        // Get the search option.   
        bool matchCase = false;  
        matchCase = m_toolWindow.MatchCaseOption.Value;  
  
        // Set variables that are used in the finally block.  
        StringBuilder sb = new StringBuilder("");  
        uint resultCount = 0;  
        this.ErrorCode = VSConstants.S_OK;  
  
        try  
        {  
            string searchString = this.SearchQuery.SearchString;  
  
            // If the search string contains the filter string, filter the content array.   
            string filterString = "lines:\"even\"";  
  
            if (this.SearchQuery.SearchString.Contains(filterString))  
            {  
                // Retain only the even items in the array.  
                contentArr = GetEvenItems(contentArr);  
  
                // Remove 'lines:"even"' from the search string.  
                searchString = RemoveFromString(searchString, filterString);  
            }  
  
            // Determine the results.   
            uint progress = 0;  
            foreach (string line in contentArr)  
            {  
                if (matchCase == true)  
                {  
                    if (line.Contains(searchString))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
                else  
                {  
                    if (line.ToLower().Contains(searchString.ToLower()))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
  
                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
  
                // Uncomment the following line to demonstrate the progress bar.   
                // System.Threading.Thread.Sleep(100);  
            }  
        }  
        catch (Exception e)  
        {  
            this.ErrorCode = VSConstants.E_FAIL;  
        }  
        finally  
        {  
            ThreadHelper.Generic.Invoke(() =>  
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
            this.SearchResults = resultCount;  
        }  
  
        // Call the implementation of this method in the base class.   
        // This sets the task status to complete and reports task completion.   
        base.OnStartSearch();  
    }  
    ```  
  
4.  Kodunuzu test edin.  
  
5.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneğinde, araç penceresi açın ve ardından arama denetimi aşağı oku seçin.  
  
     **Eşleşen servis talebi** onay kutusunu ve **arama yalnızca çift çizgileri** filtre görünür.  
  
6.  Filtreyi seçin.  
  
     Arama kutusuna içeren **satırlar: "da"**, ve aşağıdaki sonuçlar gösterilir:  
  
     iyi 2  
  
     4 iyi  
  
     6 güle güle  
  
7.  Silme `lines:"even"` arama kutusundan **eşleşen servis talebi** onay kutusunu işaretleyin ve ardından girin `g` arama kutusuna.  
  
     Aşağıdaki sonuçlar görüntülenir:  
  
     1'e  
  
     iyi 2  
  
     5 güle güle  
  
8.  Arama kutusunun sağındaki X seçin.  
  
     Arama temizlenir ve özgün içeriği görüntülenir. Ancak, **eşleşen servis talebi** onay kutusu seçili durumdayken.