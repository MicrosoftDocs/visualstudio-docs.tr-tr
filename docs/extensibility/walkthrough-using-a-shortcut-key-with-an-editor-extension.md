---
title: 'İzlenecek yol: Düzenleyici uzantısı ile kısayol tuşu kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d009351efdd36e0d415d0e2e457f7974608ab665
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886506"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>İzlenecek yol: Düzenleyici uzantısı ile kısayol tuşu kullanma
Kısayol tuşları için düzenleyici uzantı yanıt verebilir. Aşağıdaki örneklerde, bir kısayol tuşu kullanarak görünüm kenarlığı metin görünümü ekleme işlemi gösterilmektedir. Bu izlenecek yol, Görünüm penceresi kenarlığı Düzenleyicisi şablonunu temel alıyorsa ve kenarlığı kullanarak eklemek imkan + karakter.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik eklemiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) proje oluşturma  
  
1. Bir C# VSIX projesi oluşturun. (İçinde **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik**, ardından **VSIX projesi**.) Çözüm adı `KeyBindingTest`.  
  
2. Bir düzenleyici metin kenarlığı öğe şablonu projeye ekleyin ve adlandırın `KeyBindingTest`. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Aşağıdaki başvuruları ekleyin ve ayarlama **CopyLocal** için `false`:  
  
    Microsoft.VisualStudio.Editor  
  
    Microsoft.VisualStudio.OLE.Interop  
  
    Microsoft.VisualStudio.Shell.14.0  
  
    Microsoft.VisualStudio.TextManager.Interop  
  
   KeyBindingTest sınıf dosyasında PurpleCornerBox için sınıf adını değiştirin. Görüntülenen ampul sol kenar boşluğunda uygun bir değişiklik yapmak için kullanın. Oluşturucu içinde kenarlığı katmandan adını değiştirmek **KeyBindingTest** için **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  

KeyBindingTestTextViewCreationListener.cs sınıf dosyasında AdornmentLayer adını değiştirmek **KeyBindingTest** için **PurpleCornerBox**:
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  

## <a name="handle-typechar-command"></a>Tanıtıcı TYPECHAR komutu
Visual Studio 2017 sürüm 15.6 Düzenleyici uzantısı komutları işlemek için tek yolu uygulama önce bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> filtresine komutu. Visual Studio 2017 sürüm 15.6 Düzenleyicisi komut işleyicileri bağlı modern ve Basitleştirilmiş bir yaklaşım sunulmaktadır. Sonraki iki bölümde hem eski hem de modern yaklaşımı kullanarak bir komut nasıl ele alınacağını göstermektedir.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>(Visual Studio 2017 sürüm 15.6 önce) komut filtresini tanımlayın

 Komut filtre uygulamasıdır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, hangi işleme komut kenarlığı oluşturarak.  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `KeyBindingCommandFilter`.  
  
2.  Aşağıdaki using deyimlerini.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  KeyBindingCommandFilter adlı sınıfını alması gerektiğini <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Metin görünümü için özel alanlar, sonraki komutu komut zinciri ve komut filtresi zaten eklenmiş olup olmadığını göstermek için bir bayrak ekleyin.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Metin görünümünü ayarlayan bir oluşturucu ekleyin.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Uygulama `QueryStatus()` yöntemini aşağıdaki şekilde.  
  
    ```csharp  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Uygulama `Exec()` bir artı işareti, BT'nin mor kutusu görünümüne ekler, böylece yöntemi (**+**) karakter türü.  
  
    ```csharp  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>(Visual Studio 2017 sürüm 15.6 önce) komut Filtre Ekle
 Kenarlığı sağlayıcısı için metin görünümü bir komutu filtresi eklemeniz gerekiyor. Bu örnekte, sağlayıcı uygulayan <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> metni görünümü oluşturma olayları dinleyecek şekilde. Bu kenarlığı sağlayıcısı ayrıca kenarlığı Z-sıralamasını tanımlar kenarlığı katmanı dışa aktarır.  
  
1.  KeyBindingTestTextViewCreationListener dosyasına aşağıdakileri ekleyin using deyimlerini:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  Metin görünümü bağdaştırıcısı almak için aktarmalısınız <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
3.  Değişiklik <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> olan ekler için yöntemi `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
4.  `AddCommandFilter` İşleyicisi metin view bağdaştırıcısı alır ve komut filtre ekler.  
  
    ```csharp  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>(Visual Studio 2017 sürüm 15. 6'dan itibaren) bir komut işleyici uygulamak

İlk olarak, en son Düzenleyicisi API başvurmak için projenin Nuget başvuruları güncelleştirin:

1. Sağ tıklatın ve proje **Nuget paketlerini Yönet**.

2. İçinde **Nuget Paket Yöneticisi**seçin **güncelleştirmeleri** sekmesinde **tüm paketleri seçmek** onay kutusunu seçip **güncelleştirme**.

Komut işleyici uygulamasıdır <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, hangi işleme komut kenarlığı oluşturarak.  
  
1. Bir sınıf dosyası ekleyin ve adlandırın `KeyBindingCommandHandler`.  
  
2. Aşağıdaki using deyimlerini.  
  
   ```csharp  
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;   
   ```  
  
3. KeyBindingCommandHandler adlı sınıfını alması gerektiğini `ICommandHandler<TypeCharCommandArgs>`ve olarak dışarı aktarın <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:
  
   ```csharp  
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>  
   ```  
  
4. Komut işleyici görünen adını ekleyin:  
  
   ```csharp  
   public string DisplayName => "KeyBindingTest";
   ```  
    
5. Uygulama `GetCommandState()` yöntemini aşağıdaki şekilde. Bu komut işleyici çekirdek Düzenleyici TYPECHAR komutu gerçekleştirdiğinden, komut çekirdek düzenleyici için etkinleştirme devredebilirsiniz.
  
   ```csharp  
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   } 
   ```  
  
6. Uygulama `ExecuteCommand()` bir artı işareti, BT'nin mor kutusu görünümüne ekler, böylece yöntemi (**+**) karakter türü. 
  
   ```csharp  
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```  
   7. Kenarlığı katman tanımından kopyalama *KeyBindingTestTextViewCreationListener.cs* dosyasını *KeyBindingCommandHandler.cs* ve delete  *KeyBindingTestTextViewCreationListener.cs* dosyası:
 
   ```csharp  
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;    
   ```  

## <a name="make-the-adornment-appear-on-every-line"></a>Her satırda kenarlığı olun  

Her karakteri özgün kenarlığı görünen bir metin dosyasındaki ' bir'. Yanıt olarak kenarlığı eklenecek kodu değiştirdik göre **+** karakteri, yalnızca satırda kenarlığı ekler burada **+** karakter türü. Bir kez daha kenarlığı görüntülenir, böylece kenarlığı kod Değiştirebiliriz her 'bir'.  
  
İçinde *KeyBindingTest.cs* dosya, değişiklik `CreateVisuals()` 'bir' karakteri donatmak için görünümdeki tüm satırların yinelemek için yöntemi.  
  
```csharp  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="build-and-test-the-code"></a>Kod oluşturup test  
  
1.  KeyBindingTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
2.  Oluşturun veya bir metin dosyası açın. Karakter içeren bazı sözcükleri yazın 'a' ve ardından yazın **+** metni görünümü herhangi bir yerindeki.  
  
     Mor kare dosyasındaki 'bir' her bir karakter görünmelidir.
