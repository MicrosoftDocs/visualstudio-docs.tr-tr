---
title: 'İzlenecek yol: Kod parçacıkları uygulama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bd4a22dc63f0304cc8afa98e35c5f7afd6cac011
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922001"
---
# <a name="walkthrough-implement-code-snippets"></a>İzlenecek yol: Uygulama kod parçacıkları
Kod parçacıklarınızı oluşturmak ve uzantının kullanıcılar için kendi kod ekleyebilmeniz bunları bir düzenleyici uzantısına dahil etme.  
  
 Kod parçacığı, kod veya bir dosyada edilebilecek diğer metin bir parçası olan. Üzerinde belirli programlama dilleri için kaydedilen tüm parçacıkları görüntülemek için **Araçları** menüsünü tıklatın **kod parçacığı Yöneticisi**. Sağ tıklatın, kod parçacığı, istediğiniz bir dosyada bir kod parçacığını eklemek için kod parçacığı Ekle,'a tıklayın veya **Surround With**, istediğiniz kod parçacığı bulun ve çift tıklatın. Basın **sekmesini** veya **Shift**+**sekmesini** parçacığının ilgili bölümlerin değiştirin ve ENTER tuşuna basın **Enter** veya **Esc** kabul etmek. Daha fazla bilgi için [kod parçacıkları](../ide/code-snippets.md).  
  
 Kod parçacığı .snippet * dosya adı uzantısına sahip bir XML dosyasında yer alır. Bir kod parçacığı, kullanıcı bulabilir ve bunları değiştirmek için kod parçacığı eklendikten sonra vurgulanır alanlar içerebilir. Bir kod parçacığı dosyası için bilgi de sağlar **kod parçacığı Yöneticisi** kod parçacığı adı doğru kategorisinde görüntüleyebilmesi. Kod parçacığı şeması hakkında daha fazla bilgi için bkz: [kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md).  
  
 Bu izlenecek yol aşağıdaki görevlerin nasıl yerine getirileceğini öğretir:  
  
1. Oluşturun ve belirli bir dil için kod parçacıkları kaydedin.  
  
2. Ekleme **parçacık Ekle** kısayol menüsüne komut.  
  
3. Kod parçacığı genişletme uygulayın.  
  
   Bu izlenecek yolda temel alır [izlenecek yol: deyim tamamlamayı görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik eklemiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-and-register-code-snippets"></a>Oluşturma ve kod parçacıkları kaydetme  
 Genellikle, kod parçacıkları kayıtlı dil hizmeti ile ilişkilidir. Ancak, uygulamanız gerekmez bir <xref:Microsoft.VisualStudio.Package.LanguageService> kod parçacıkları kaydedilecek. Bunun yerine, yalnızca kod parçacığı dizin dosyasında bir GUID belirtin ve ardından aynı GUID <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , projenize ekleyin.  
  
 Aşağıdaki adımlar, kod parçacıkları oluşturmak ve bunları belirli bir GUID ile ilişkilendirmek nasıl ekleyebileceğiniz gösterilmektedir.  
  
1. Aşağıdaki dizin yapısını oluşturun:  
  
    **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
    Burada *Installdır %* Visual Studio yükleme klasörüdür. (Bu yol genellikle kod parçacıkları yüklemek için kullanılsa da, herhangi bir yolu belirtebilirsiniz.)  
  
2. \1033\ klasöründe, oluşturun bir *.xml* adlandırın ve dosya **TestSnippets.xml**. (Bu adı genellikle bir kod parçacığı dizin dosyası için kullanılsa da, sahip olduğu sürece herhangi bir ad belirtebilirsiniz bir *.xml* dosya adı uzantısı.) Aşağıdaki metni ekleyin ve yer tutucu GUID silin ve kendi uygulamanızı ekleyin.  
  
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
  
### <a name="to-register-code-snippets-for-a-specific-guid"></a>Kod parçacıkları için belirli bir GUID kaydetmek için  
  
1.  Açık **CompletionTest** proje. Bu proje oluşturma hakkında daha fazla bilgi için bkz [izlenecek yol: deyim tamamlamayı görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  Projede aşağıdaki derlemelere başvurular ekleyin:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  Project'te Aç **source.extension.vsixmanifest** dosya.  
  
4.  Emin olun **varlıklar** sekmesini içeren bir **VsPackage** içerik türü ve, **proje** proje adına ayarlanır.  
  
5.  CompletionTest projeyi seçin ve Özellikler penceresinde ayarlayın **Pkgdef dosyası oluştur** için **true**. Projeyi kaydedin.  
  
6.  Statik bir ekleme `SnippetUtilities` projeye sınıfı.  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  SnippetUtilities sınıfı tanımlayan bir GUID ve içinde kullanılan değeri vermek *SnippetsIndex.xml* dosya.  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Ekleme <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> için `TestCompletionHandler` sınıfı. Bu öznitelik, projedeki tüm public veya internal (statik olmayan) sınıfı için eklenebilir. (Eklemek zorunda bir `using` Microsoft.VisualStudio.Shell ad alanı bildirimi.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Derleme ve projeyi çalıştırın. Projeyi çalıştırdığınızda başlatan Visual Studio deneysel örneğinde yeni kaydettiğiniz kod parçacığı görüntüleneceğini **kod parçacıkları Yöneticisi** altında **TestSnippets** dili.  
  
## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kod parçacığı Ekle komutu kısayol menüsüne ekleyin  
 **Parçacık Ekle** komutunu bir metin dosyası için kısayol menüsündeki dahil değildir. Bu nedenle, komut etkinleştirmeniz gerekir.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kod parçacığı Ekle komutu kısayol menüsüne eklemek için  
  
1.  Açık `TestCompletionCommandHandler` sınıf dosyası.  
  
     Bu sınıf uyguladığından <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, etkinleştirebilir **parçacık Ekle** komutunu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi. Bu yöntem bir Otomasyon işlevinin içinde olduğundan çağrıldığından değildir komut etkinleştirmeden önce denetleyin, **parçacık Ekle** komutu tıklandığında, kod parçacığı Seçici kullanıcı arabirimi (UI) görüntüler.  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Derleme ve projeyi çalıştırın. Deneysel örneğinde sahip bir dosyayı açan *.zzz* dosya adı uzantısı ve herhangi bir projeyi sağ tıklatın. **Parçacık Ekle** komutu kısayol menüsünde görüntülenmelidir.  
  
## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Kod parçacığı genişletme kod parçacığı Seçici Arabiriminde uygulayın  
 Bu bölümde, böylece kod parçacığı Seçici UI kod parçacığı genişletme uygulamak gösterilmektedir olduğunda görüntülenen **parçacık Ekle** kısayol menüsünde tıkladı. Bir kullanıcı kod parçacığı kısayol türleri ve ardından bastığında bir kod parçacığı da Genişletilmiş **sekmesini**.  
  
 Kod parçacığı Seçici'yi kullanıcı arabirimini görüntüleyin ve gezinti ve sonrası ekleme parçacığı kabul etkinleştirmek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi. Ekleme tarafından işlenen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> yöntemi.  
  
 Eski kod parçacığı genişletme uyarlamasını kullanır <xref:Microsoft.VisualStudio.TextManager.Interop> arabirimleri. Eski kod için geçerli Düzenleyici sınıflardan Çevir metin arabelleğinde konumları belirtmek için satır numaralarını ve sütun numaralarının eski arabirimleri kullanır, ancak bir dizini geçerli sınıfları kullanması unutmayın. Bu nedenle, her biri 10 karakter sahip üç satır (artı bir karakter sayılır bir yeni satır) bir arabellek sahip, üçüncü satır dördüncü karakteri geçerli uygulama 27 konumunda, ancak satır 2, 3 eski uygulama getirin.  
  
#### <a name="to-implement-snippet-expansion"></a>Kod parçacığı genişletme uygulamak için  
  
1.  İçeren dosyaya `TestCompletionCommandHandler` sınıfında, aşağıdaki `using` deyimleri.  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Olun `TestCompletionCommandHandler` sınıfı uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> arabirimi.  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  İçinde `TestCompletionCommandHandlerProvider` sınıfı, içeri aktarma <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Kod genişletmesi arabirimleri için bazı özel alanlar ekleyin ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  Oluşturucusunun içinde `TestCompletionCommandHandler` sınıfında, aşağıdaki alanları ayarlayın.  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Kod parçacığı Seçici kullanıcı tıkladığında görüntülenecek **parçacık Ekle** komutu, aşağıdaki kodu ekleyin <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi. (Bu açıklama daha okunaklı hale getirmek için `Exec()`deyim tamamlama için kullanılan kod gösterilmez; bunun yerine, kod blokları için varolan bir yöntem eklenir.) Aşağıdaki kod bloğunu karakteri denetleyen koddan sonra ekleyin.  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Bir kod parçacığı geçtiğiniz alanlar varsa, genişletme açıkça kabul edilinceye kadar genişletme oturumu açık tutulur; kod parçacığı, hiçbir alan varsa, oturumu kapatılır ve olarak döndürülen `null` tarafından <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> yöntemi. İçinde <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi, önceki adımda eklediğiniz bir kullanıcı Arabirimi kod parçacığı Seçici sonra kod parçacığı Gezinti işlemek için aşağıdaki kodu ekleyin (kullanıcının bastığında **sekmesini** veya **Shift** + **Sekmesini** kod parçacığı ekleme sonra).  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Kullanıcı karşılık gelen kısayol türleri ve ardından bastığında kod parçacığını eklemek için **sekmesini**, kodu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi. Kod parçacığı ekler özel yöntem daha sonraki bir adımda gösterilir. Önceki adımda eklediğiniz Gezinti koddan sonra aşağıdaki kodu ekleyin.  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Yöntemlerini uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> arabirimi. Bu uygulama, ilgilenilen yalnızca yöntemlerdir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Diğer yöntemler yalnızca döndürmelidir <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> yöntemi. Genişletmeler eklediği yardımcı yöntemi, bir sonraki adımda ele alınmıştır. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Sayfasından edinebilirsiniz, satır ve sütun bilgisi sağlar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. Aşağıdaki gizli yöntemi kısayol veya başlık ve yol tabanlı bir kod parçacığı ekler. Ardından <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> parçacığıyla yöntemi.  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="build-and-test-code-snippet-expansion"></a>Yapı ve test kod parçacığı genişletme  
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
  
     Basın yoksa **Enter** veya **Esc**.  
  
5.  Tuşuna **sekmesini** ve **Shift**+**sekmesini** "first" ve "saniye" arasında geçiş için.  
  
6.  Ekleme ya da tuşlarına basarak kabul **Enter** veya **Esc**.  
  
7.  Metni farklı bir parçası, "test" yazın ve sonra basın **sekmesini**. "Test" kod parçacığı kısayol olduğundan, kod parçacığı yeniden eklenmelidir.  
  
## <a name="next-steps"></a>Sonraki adımlar