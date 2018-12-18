---
title: 'İzlenecek yol: Kod parçacıkları uygulama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6fe91fd4e80c14e9b4cf59136fa6d3e0e003f554
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752056"
---
# <a name="walkthrough-implementing-code-snippets"></a>İzlenecek Yol: Kod Parçacıkları Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod parçacıklarınızı oluşturmak ve uzantının kullanıcılar için kendi kod ekleyebilmeniz bunları bir düzenleyici uzantısına dahil etme.  
  
 Kod parçacığı, kod veya bir dosyada edilebilecek diğer metin bir parçası olan. Üzerinde belirli programlama dilleri için kaydedilen tüm parçacıkları görüntülemek için **Araçları** menüsünü tıklatın **kod parçacığı Yöneticisi**. Sağ tıklatın, kod parçacığı, istediğiniz bir dosyada bir kod parçacığını eklemek için tıklatın **parçacık Ekle** veya **Surround With**, istediğiniz kod parçacığı bulun ve çift tıklatın. SEKME veya SHIFT + TAB ilgili bölümlerini kod parçacığını değiştirmek ve kabul etmek için ENTER veya ESC tuşuna basın. Daha fazla bilgi için [kod parçacıkları](../ide/code-snippets.md).  
  
 Kod parçacığı .snippet dosya adı uzantısına sahip bir XML dosyasında yer alır. Bir kod parçacığı, kullanıcı bulabilir ve bunları değiştirmek için kod parçacığı eklendikten sonra vurgulanır alanlar içerebilir. Bir kod parçacığı dosyası için bilgi de sağlar **kod parçacığı Yöneticisi** kod parçacığı adı doğru kategorisinde görüntüleyebilmesi. Kod parçacığı şeması hakkında daha fazla bilgi için bkz: [kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md).  
  
 Bu izlenecek yol aşağıdaki görevlerin nasıl yerine getirileceğini öğretir:  
  
1. Oluşturun ve belirli bir dil için kod parçacıkları kaydedin.  
  
2. Ekleme **parçacık Ekle** kısayol menüsüne komut.  
  
3. Kod parçacığı genişletme uygulayın.  
  
   Bu izlenecek yolda dayanır [izlenecek yol: deyim tamamlamayı görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Oluşturma ve kod parçacıkları kaydediliyor  
 Genellikle, kod parçacıkları kayıtlı dil hizmeti ile ilişkilidir. Ancak, uygulamanız gerekmez bir <xref:Microsoft.VisualStudio.Package.LanguageService> kod parçacıkları kaydedilecek. Bunun yerine, yalnızca kod parçacığı dizin dosyasında bir GUID belirtin ve ardından aynı GUID <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , projenize ekleyin.  
  
 Aşağıdaki adımlar, kod parçacıkları oluşturmak ve bunları belirli bir GUID ile ilişkilendirmek nasıl ekleyebileceğiniz gösterilmektedir.  
  
1. Aşağıdaki dizin yapısını oluşturun:  
  
    **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
    Burada *Installdır %* Visual Studio yükleme klasörüdür. (Bu yol genellikle kod parçacıkları yüklemek için kullanılsa da, herhangi bir yolu belirtebilirsiniz.)  
  
2. \1033\ klasördeki bir .xml dosyası oluşturun ve adlandırın **TestSnippets.xml**. (Bu ad, genellikle bir kod parçacığı dizin dosyası kullanılıyor olsa da, bir .xml dosya adı uzantısına sahip olduğu sürece herhangi bir ad belirtebilirsiniz.) Aşağıdaki metni ekleyin ve yer tutucu GUID silin ve kendi uygulamanızı ekleyin.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8" ?>  
   <SnippetCollection>  
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">  
           <SnippetDir>  
               <OnOff>On</OnOff>  
               <Installed>true</Installed>  
               <Locale>1033</Locale>  
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>  
               <LocalizedName>Snippets</LocalizedName>  
           </SnippetDir>  
       </Language>  
   </SnippetCollection>  
   ```  
  
3. Kod parçacığı klasörüne bir dosya oluşturun, adlandırın **test**`.snippet`ve ardından aşağıdaki metni ekleyin:  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8" ?>  
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
       <CodeSnippet Format="1.0.0">  
           <Header>  
               <Title>Test replacement fields</Title>  
               <Shortcut>test</Shortcut>  
               <Description>Code snippet for testing replacement fields</Description>  
               <Author>MSIT</Author>  
               <SnippetTypes>  
                   <SnippetType>Expansion</SnippetType>  
               </SnippetTypes>  
           </Header>  
           <Snippet>  
               <Declarations>  
                   <Literal>  
                     <ID>param1</ID>  
                       <ToolTip>First field</ToolTip>  
                       <Default>first</Default>  
                   </Literal>  
                   <Literal>  
                       <ID>param2</ID>  
                       <ToolTip>Second field</ToolTip>  
                       <Default>second</Default>  
                   </Literal>  
               </Declarations>  
               <References>  
                  <Reference>  
                      <Assembly>System.Windows.Forms.dll</Assembly>  
                  </Reference>  
               </References>  
               <Code Language="TestSnippets">  
                   <![CDATA[MessageBox.Show("$param1$");  
        MessageBox.Show("$param2$");]]>  
               </Code>    
           </Snippet>  
       </CodeSnippet>  
   </CodeSnippets>  
   ```  
  
   Aşağıdaki adımlarda, kod parçacıkları kaydettirmek gösterilmektedir.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>Kod parçacıkları için belirli bir GUID kaydetmek için  
  
1.  Açık **CompletionTest** proje. Bu proje oluşturma hakkında daha fazla bilgi için bkz: [izlenecek yol: deyim tamamlamayı görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  Projede aşağıdaki derlemelere başvurular ekleyin:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  Projede source.extension.vsixmanifest dosyasını açın.  
  
4.  Emin olun **varlıklar** sekmesini içeren bir **VsPackage** içerik türü ve, **proje** proje adına ayarlanır.  
  
5.  CompletionTest projeyi seçin ve Özellikler penceresinde ayarlayın **Pkgdef dosyası oluştur** için **true**. Projeyi kaydedin.  
  
6.  Statik bir ekleme `SnippetUtilities` projeye sınıfı.  
  
     [!code-csharp[VSSDKCompletionTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#22)]
     [!code-vb[VSSDKCompletionTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#22)]  
  
7.  SnippetUtilities sınıfındaki bir GUID tanımlayın ve SnippetsIndex.xml dosyada kullanılan değer verin.  
  
     [!code-csharp[VSSDKCompletionTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#23)]
     [!code-vb[VSSDKCompletionTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#23)]  
  
8.  Ekleme <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> için `TestCompletionHandler` sınıfı. Bu öznitelik, projedeki tüm public veya internal (statik olmayan) sınıfı için eklenebilir. (Eklemek zorunda bir `using` Microsoft.VisualStudio.Shell ad alanı bildirimi.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#24)]
     [!code-vb[VSSDKCompletionTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#24)]  
  
9. Derleme ve projeyi çalıştırın. Projeyi çalıştırdığınızda başlatan Visual Studio deneysel örneğinde yeni kaydettiğiniz kod parçacığı görüntüleneceğini **kod parçacıkları Yöneticisi** altında **TestSnippets** dili.  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Kısayol menüsüne INSERT kod parçacığı komutu ekleme  
 **Parçacık Ekle** komutunu bir metin dosyası için kısayol menüsündeki dahil değildir. Bu nedenle, komut etkinleştirmeniz gerekir.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kod parçacığı Ekle komutu kısayol menüsüne eklemek için  
  
1.  Açık `TestCompletionCommandHandler` sınıf dosyası.  
  
     Bu sınıf uyguladığından <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, etkinleştirebilir **parçacık Ekle** komutunu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi. Bu yöntem bir Otomasyon işlevinin içinde olduğundan çağrıldığından değildir komut etkinleştirmeden önce denetleyin, **parçacık Ekle** komutu tıklandığında, kod parçacığı Seçici kullanıcı arabirimi (UI) görüntülenir.  
  
     [!code-csharp[VSSDKCompletionTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#25)]
     [!code-vb[VSSDKCompletionTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#25)]  
  
2.  Derleme ve projeyi çalıştırın. Deneysel örneğinde .zzz dosya adı uzantısına sahip bir dosya açın ve ardından herhangi bir yeri içinde sağ tıklayın. **Parçacık Ekle** komutu kısayol menüsünde görüntülenmelidir.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Kod parçacığı genişletme kod parçacığı Seçici kullanıcı Arabirimi uygulama  
 Bu bölümde, böylece kod parçacığı Seçici UI kod parçacığı genişletme uygulamak gösterilmektedir olduğunda görüntülenen **parçacık Ekle** kısayol menüsünde tıkladı. Kod parçacığı, bir kullanıcı kod parçacığı kısayol türleri ve ardından SEKME tuşuna bastığında ayrıca genişletilir.  
  
 Kod parçacığı Seçici'yi kullanıcı arabirimini görüntüleyin ve gezinti ve sonrası ekleme parçacığı kabul etkinleştirmek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi. Ekleme tarafından işlenen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> yöntemi.  
  
 Eski kod parçacığı genişletme uyarlamasını kullanır <xref:Microsoft.VisualStudio.TextManager.Interop> arabirimleri. Eski kod için geçerli Düzenleyici sınıflardan Çevir metin arabelleğinde konumları belirtmek için satır numaralarını ve sütun numaralarının eski arabirimleri kullanır, ancak bir dizini geçerli sınıfları kullanması unutmayın. Bu nedenle, her biri on karakter sahip üç satır (+ 1 karakter olarak sayılır bir yeni satır) bir arabellek sahip, üçüncü satır dördüncü karakteri geçerli uygulama 27 konumunda, ancak satır 2, 3 eski uygulama getirin.  
  
#### <a name="to-implement-snippet-expansion"></a>Kod parçacığı genişletme uygulamak için  
  
1.  İçeren dosyaya `TestCompletionCommandHandler` sınıfında, aşağıdaki `using` deyimleri.  
  
     [!code-csharp[VSSDKCompletionTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#26)]
     [!code-vb[VSSDKCompletionTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#26)]  
  
2.  Olun `TestCompletionCommandHandler` sınıfı uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> arabirimi.  
  
     [!code-csharp[VSSDKCompletionTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#27)]
     [!code-vb[VSSDKCompletionTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#27)]  
  
3.  İçinde `TestCompletionCommandHandlerProvider` sınıfı, içeri aktarma <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-csharp[VSSDKCompletionTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#28)]
     [!code-vb[VSSDKCompletionTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#28)]  
  
4.  Kod genişletmesi arabirimleri için bazı özel alanlar ekleyin ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#29)]
     [!code-vb[VSSDKCompletionTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#29)]  
  
5.  Oluşturucusunun içinde `TestCompletionCommandHandler` sınıfında, aşağıdaki alanları ayarlayın.  
  
     [!code-csharp[VSSDKCompletionTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#30)]
     [!code-vb[VSSDKCompletionTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#30)]  
  
6.  Kod parçacığı Seçici kullanıcı tıkladığında görüntülenecek **parçacık Ekle** komutu, aşağıdaki kodu ekleyin <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi. (Bu açıklama daha okunabilir yapmak için deyim tamamlama için kullanılan Exec() kod gösterilmiyor; bunun yerine, kod blokları için varolan bir yöntem eklenir.) Aşağıdaki kod bloğunu karakteri denetleyen koddan sonra ekleyin.  
  
     [!code-csharp[VSSDKCompletionTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#31)]
     [!code-vb[VSSDKCompletionTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#31)]  
  
7.  Bir kod parçacığı geçtiğiniz alanlar varsa, genişletme açıkça kabul edilinceye kadar genişletme oturumu açık tutulur; kod parçacığı, hiçbir alan varsa, oturumu kapatılır ve olarak döndürülen `null` tarafından <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> yöntemi. İçinde <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi, önceki adımda eklediğiniz bir kullanıcı Arabirimi kod parçacığı Seçici sonra (kullanıcının sekme veya SHIFT + SEKME kod parçacığı eklemeden sonra bastığında) kod parçacığı Gezinti işlemek için aşağıdaki kodu ekleyin.  
  
     [!code-csharp[VSSDKCompletionTest#32](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#32)]
     [!code-vb[VSSDKCompletionTest#32](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#32)]  
  
8.  Kullanıcı türleri karşılık gelen kısayol ve ardından SEKME tuşuna bastığında kod parçacığını eklemek için kod ekleyin. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi. Kod parçacığı ekler özel yöntem daha sonraki bir adımda gösterilir. Önceki adımda eklediğiniz Gezinti koddan sonra aşağıdaki kodu ekleyin.  
  
     [!code-csharp[VSSDKCompletionTest#33](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#33)]
     [!code-vb[VSSDKCompletionTest#33](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#33)]  
  
9. Yöntemlerini uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> arabirimi. Bu uygulama, ilgilenilen yalnızca yöntemlerdir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Diğer yöntemler yalnızca döndürmelidir <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-csharp[VSSDKCompletionTest#34](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#34)]
     [!code-vb[VSSDKCompletionTest#34](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#34)]  
  
10. Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> yöntemi. Genişletmeleri eklediği yardımcı yöntemi, bir sonraki adımda ele alınmaktadır. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Sayfasından edinebilirsiniz, satır ve sütun bilgisi sağlar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#35)]
     [!code-vb[VSSDKCompletionTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#35)]  
  
11. Aşağıdaki gizli yöntemi kısayol veya başlık ve yol tabanlı bir kod parçacığı ekler. Ardından <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> parçacığıyla yöntemi.  
  
     [!code-csharp[VSSDKCompletionTest#36](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#36)]
     [!code-vb[VSSDKCompletionTest#36](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#36)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Oluşturma ve kod parçacığı genişletme test etme  
 Kod parçacığı genişletme projenizde çalışıp çalışmadığını test edebilirsiniz.  
  
1.  Çözümü oluşturun. Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
2.  Bir metin dosyasını açın ve bir metin yazın.  
  
3.  Metni bir yere sağ tıklayın ve ardından **parçacık Ekle**.  
  
4.  UI bildiren bir açılır pencere ile görünmelidir kod parçacığı Seçici **Test değiştirilen alanları**. Açılır pencere çift tıklayın.  
  
     Aşağıdaki kod parçacığı eklenmelidir.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     ENTER veya ESC tuşuna basmayın.  
  
5.  SEKME ve SHIFT + SEKME açıp kapatmak için basın "first" ve "saniye" arasında.  
  
6.  Ekleme ENTER veya ESC tuşuna basarak kabul edin.  
  
7.  Metni farklı bir parçası, "test" yazın ve sonra SEKME tuşuna basın. "Test" kod parçacığı kısayol olduğundan, kod parçacığı yeniden eklenmelidir.  
  
## <a name="next-steps"></a>Sonraki Adımlar

