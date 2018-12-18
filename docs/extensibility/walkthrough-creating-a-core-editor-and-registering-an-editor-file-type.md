---
title: Çekirdek düzenleyici oluşturma ve bir düzenleyici dosya türü kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e00b96d1f5361d3d5260296532be47636f430d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921463"
---
# <a name="walkthrough-create-a-core-editor-and-registering-an-editor-file-type"></a>İzlenecek yol: bir çekirdek Düzenleyicisi ve bir düzenleyici dosya türü kayıt oluşturma
Bu izlenecek yol başlatan bir VSPackage'ı oluşturma işlemini gösterir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çekirdek Düzenleyicisi ile bir dosya *.myext* dosya adı uzantısı yüklenir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio Paket projesi şablonu için konumları  
 Visual Studio Paket proje şablonu, üç farklı konumlarda bulunabilir **yeni proje** iletişim:  
  
1.  Altında **Visual Basic genişletilebilirliği**. Visual Basic proje varsayılan dildir.  
  
2.  Altında **C# genişletilebilirlik**. Varsayılan proje C# dilidir.  
  
3.  Altında **diğer proje türleri genişletilebilirlik**. C++ projesinin varsayılan dildir.  
  
### <a name="to-create-the-vspackage"></a>VSPackage'ı oluşturmak için  
  
- Başlangıç [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturup bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] adlı VSPackage `MyPackage`açıklandığı gibi [izlenecek yol: bir VSPackage menü komutu oluşturmak](https://msdn.microsoft.com/library/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Düzenleyici üreteci eklemek için  
  
1. Sağ **MyPackage** proje, işaret **Ekle**ve ardından **sınıfı**.  
  
2. İçinde **Yeni Öğe Ekle** iletişim kutusunda, emin **sınıfı** şablonu seçili türü `EditorFactory.cs` adı ve ardından **Ekle** sınıfı projenize eklemek için.  
  
    *EditorFactory.cs* dosya otomatik olarak açması gerekir.  
  
3. Aşağıdaki derlemelere de kodunuzdan başvurur.  
  
   ```vb  
   Imports System.Runtime.InteropServices  
   Imports Microsoft.VisualStudio  
   Imports Microsoft.VisualStudio.Shell  
   Imports Microsoft.VisualStudio.Shell.Interop  
   Imports Microsoft.VisualStudio.OLE.Interop  
   Imports Microsoft.VisualStudio.TextManager.Interop  
   Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
   ```  
  
   ```csharp  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio;  
   using Microsoft.VisualStudio.Shell;  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio.OLE.Interop;  
   using Microsoft.VisualStudio.TextManager.Interop;  
   using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
   ```  
  
4. Bir GUID değeri ekleyin `EditorFactory` ekleyerek sınıfı `Guid` özniteliği sınıf bildiriminden hemen önce.  
  
    Kullanarak yeni bir GUID oluşturabilirsiniz *guidgen.exe* , program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komut istemi veya tıklayarak komut **GUID Oluştur** üzerinde **Araçları** menüsü. Burada kullanılan GUID yalnızca bir örnektir; Projenizde kullanmayın.  
  
   ```vb  
   <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
   ```  
  
   ```csharp  
   [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
   ```  
  
5. Sınıf tanımında üst pakete ve bir hizmet sağlayıcısı içerecek şekilde iki özel değişkeni ekleyin.  
  
   ```vb  
   Class EditorFactory  
       Private parentPackage As Package  
       Private serviceProvider As IOleServiceProvider  
   ```  
  
   ```csharp  
   class EditorFactory  
   {  
       private Package parentPackage;  
       private IOleServiceProvider serviceProvider;  
   }  
  
   ```  
  
6. Türünden bir parametre alan bir genel sınıf oluşturucu Ekle <xref:Microsoft.VisualStudio.Shell.Package>:  
  
   ```vb  
   Public Sub New(ByVal parentPackage As Package)  
       Me.parentPackage = parentPackage  
   End Sub  
   ```  
  
   ```csharp  
   public EditorFactory(Package parentPackage)  
   {  
       this.parentPackage = parentPackage;  
   }  
   ```  
  
7. Değiştirme `EditorFactory` sınıf türetmek için bildirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> arabirimi.  
  
   ```vb  
   Class EditorFactory Implements IVsEditorFacto  
   ```  
  
   ```csharp  
   class EditorFactory : IVsEditorFactory  
  
   ```  
  
8. Sağ <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, tıklayın **arabirim uygulama**ve ardından **uygulama arabirimi açıkça**.  
  
    Bu adım, uygulanması gereken dört yöntemleri ekler <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> arabirimi.  
  
9. Öğesinin içeriğini değiştirin `IVsEditorFactory.Close` yöntemini aşağıdaki kod ile.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Öğesinin içeriğini değiştirin `IVsEditorFactory.SetSite` aşağıdaki kod ile.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Öğesinin içeriğini değiştirin `IVsEditorFactory.MapLogicalView` yöntemini aşağıdaki kod ile.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Öğesinin içeriğini değiştirin `IVsEditorFactory.CreateEditorInstance` yöntemini aşağıdaki kod ile.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Projeyi derleyin ve hiçbir hata olmadığından emin olun.  
  
### <a name="to-register-the-editor-factory"></a>Düzenleyici üreteci kaydetmek için  
  
1. İçinde **Çözüm Gezgini**, çift **Resources.resx** olan dize tablosuna açmak için dosyaya giriş **Dize1** seçili.  
  
2. Tanımlayıcı için adını değiştirmek `IDS_EDITORNAME` ve metni **MyPackage Düzenleyici.** Bu dize Düzenleyici adı olarak görünür.  
  
3. Açık **VSPackage.resx** dosya, yeni bir dize ekleyin, adı kümesine **101**ve değerine `IDS_EDITORNAME`. Bu adım, oluşturduğunuz dize erişmek için bir kaynak kimliği ile paket sağlar.  
  
   > [!NOTE]
   >  Varsa **VSPackage.resx** dosyasını içeren başka bir, dize `name` özniteliğini **101**, başka bir benzersiz, sayısal değer, burada ve aşağıdaki adımları değiştirin.  
  
4. İçinde **Çözüm Gezgini**açın **MyPackagePackage.cs** dosya.  
  
    Ana paket dosyası bu dosyadır.  
  
5. Aşağıdaki kullanıcı öznitelikleri hemen önüne ekleyin `Guid` özniteliği.  
  
   ```vb  
   <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
   <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
         ".myext", 32, NameResourceID:=101 )> _  
   ```  
  
   ```csharp  
   [ProvideEditorFactory(typeof(EditorFactory), 101)]  
   [ProvideEditorExtension(typeof(EditorFactory),   
         ".myext", 32, NameResourceID = 101)]   
   ```  
  
    <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> Özniteliği ilişkilendirir *.myext* uzantısı yüklenir, Düzenleyicisi Fabrika çağrılan sahip bir dosya için istediğiniz zaman, böylece dosya uzantısı, düzenleyici fabrikası ile.  
  
6. Özel bir değişken ekleyin `MyPackage` , sınıf oluşturucusu hemen önce ve türü verin `EditorFactory`.  
  
   ```vb  
   Private editorFactory As EditorFactory  
   ```  
  
   ```csharp  
   private EditorFactory editorFactory;  
   ```  
  
7. Bulma `Initialize` yöntemi (açmanız gerekebilir `Package Members` gizli bölge) ve çağrısından sonra aşağıdaki kodu ekleyin `base.Initialize()`.  
  
   ```vb  
   'Create our editor factory and register it.   
   Me.editorFactory = New EditorFactory(Me)  
   MyBase.RegisterEditorFactory(Me.editorFactory)  
   ```  
  
   ```csharp  
   // Create our editor factory and register it.  
   this.editorFactory = new EditorFactory(this);  
   base.RegisterEditorFactory(this.editorFactory);  
  
   ```  
  
8. Program derleyin ve hiçbir hata olmadığından emin olun.  
  
    Bu adım için Deneysel kayıt defteri kovanında Düzenleyici üreteci kaydeder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Geçersiz kılınacak istenirse *resource.h* dosyasına sağ tıklayıp **Tamam**.  
  
9. Adlandırılmış bir örnek dosyası oluşturma *TextFile1.myext*.  
  
10. Tuşuna **F5** Deneysel örneğini açmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
11. Deneysel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **dosya** menüsünde **açık** ve ardından **dosya**.  
  
12. Bulma **TextFile1.myext** ve ardından **açık**.  
  
     Dosya yüklemeniz gerekir.  
  
## <a name="robust-programming"></a>Güçlü programlama  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Çekirdek Düzenleyicisi çok çeşitli metin tabanlı dosya türleri ve dil Hizmetleri ile yakın bir tümleştirmede çalışır zengin bir söz dizimi vurgulama, ayraç eşleştirme ve IntelliSense Sözcük tamamlama gibi özellikleri sağlamak için işler ve üye tamamlama listeler. Metin tabanlı dosyaları ile çalışıyorsanız, çekirdek Düzenleyicisi, belirli dosya türlerini destekleyen özel dil hizmeti ile birlikte kullanabilirsiniz.  
  
 VSPackage çağırabilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çekirdek Düzenleyicisi tarafından bir düzenleyici fabrikası sağlama. Bu düzenleyici fabrikası, kendisiyle ilişkili bir dosyada her yüklendiğinde kullanılır. Dosya bir projesinin bir parçasıysa çekirdek Düzenleyicisi, VSPackage tarafından geçersiz kılınmadığı sürece otomatik olarak çağrılır. Ancak, dosya bir proje dışında yüklenirse, çekirdek Düzenleyici açıkça, VSPackage tarafından çağrılmalıdır.  
  
 Çekirdek Düzenleyicisi hakkında daha fazla bilgi için bkz: [çekirdek Düzenleyicisi içinde](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Çekirdek Düzenleyicisi içinde](../extensibility/inside-the-core-editor.md)   
 [Eski API'yi kullanarak çekirdek Düzenleyici örneği](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)