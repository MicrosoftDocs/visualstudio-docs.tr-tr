---
title: 'İzlenecek yol: Düzenleyici uzantısı ile kısayol tuşu kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e68cf9d3e33ad07ab092de680078972dfaf2d70
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797461"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>İzlenecek Yol: Düzenleyici Uzantısı ile Kısayol Tuşu Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kısayol tuşları için düzenleyici uzantı yanıt verebilir. Aşağıdaki örneklerde, bir kısayol tuşu kullanarak görünüm kenarlığı metin görünümü ekleme işlemi gösterilmektedir. Bu izlenecek yol, Görünüm penceresi kenarlığı Düzenleyicisi şablonunu temel alıyorsa ve kenarlığı kullanarak eklemek imkan + karakter.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) proje oluşturma  
  
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
  
## <a name="defining-the-command-filter"></a>Komut filtre tanımlama  
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
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Metin görünümü için özel alanlar, sonraki komutu komut zinciri ve komut filtresi zaten eklenmiş olup olmadığını göstermek için bir bayrak ekleyin.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
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
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Uygulama `Exec()` , BT'nin mor kutusu görünümüne ekler için yöntemi bir + karakter türü.  
  
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
  
## <a name="adding-the-command-filter"></a>Komut filtre ekleme  
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
  
2.  Kenarlığı katman tanımında AdornmentLayer adını değiştirmek **KeyBindingTest** için **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Metin görünümü bağdaştırıcısı almak için aktarmalısınız <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Değişiklik <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> olan ekler için yöntemi `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  `AddCommandFilter` İşleyicisi metin view bağdaştırıcısı alır ve komut filtre ekler.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>Kenarlığı yaparak her satırında görünür  
 Her karakteri özgün kenarlığı görünen bir metin dosyasındaki ' bir'. Yanıt '+' karakter olarak kenarlığı eklenecek kodu değiştirdik, yalnızca satırda kenarlığı ekler burada '+' yazılır. Bir kez daha kenarlığı görüntülenir, böylece kenarlığı kod Değiştirebiliriz her 'bir'.  
  
 'Bir' karakteri donatmak için görünümdeki tüm satırların yinelemek için CreateVisuals() yöntemi KeyBindingTest.cs dosyasında değiştirin.  
  
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
  
## <a name="building-and-testing-the-code"></a>Oluşturma ve kod test etme  
  
1.  KeyBindingTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
2.  Oluşturun veya bir metin dosyası açın. Karakter içeren bazı sözcükleri yazın 'a', Anahtar'a tıklayın ve metin görünümünü herhangi bir yerindeki +.  
  
     Mor kare dosyasındaki 'bir' her bir karakter görünmelidir.

