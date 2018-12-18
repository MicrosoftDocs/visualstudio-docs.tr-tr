---
title: 'Nasıl yapılır: nesne yöneticisine kitaplık kaydetme | Microsoft Docs'
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
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed547d82ccacec44383fed29a0c04bb363b10084
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732947"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Nasıl yapılır: nesne yöneticisine kitaplık kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sembol tarama araçlarını, gibi **sınıf görünümü**, **Nesne Tarayıcısı**, **çağrı tarayıcısı** ve **sembol sonuçları Bul**, etkinleştirdiğiniz görüntülemek Projenizdeki veya dış bileşenler semboller. Simgeler, ad alanları, sınıflar, arabirimler, yöntemleri ve diğer dil öğelerini içerir. Kitaplıkları bu sembolleri izlemek ve bunlara üzerinden kullanıma sunacaksınız [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] araçları verilerle dolduran Nesne Yöneticisi.  
  
 Nesne Yöneticisi, kullanılabilir tüm kitaplıkları izler. Her kitaplık nesne yöneticisine semboller için Sembol tarama araçlarını sağlamadan önce kaydetmeniz gerekir.  
  
 Genellikle, bir VSPackage'ı yüklerken bir kitaplık kaydedin. Ancak, bunu başka bir zaman gerektiği şekilde gerçekleştirebilirsiniz. VSPackage'ı kapatıldığında kitaplığı kaydını silin.  
  
 Kitaplığa kaydetmek için kullanın <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> yöntemi. Yönetilen kod kitaplığı söz konusu olduğunda <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemi.  
  
 Bir tür kitaplığının kaydını silmek için kullanın <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> yöntemi.  
  
 Nesne Yöneticisi ' ni bir başvuru almak <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, geçmesi <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> kimliği için hizmet `GetService` yöntemi.  
  
## <a name="registering-and-unregistering-a-library-with-the-object-manager"></a>Kaydetme ve bir kitaplık nesnesi Yöneticisi ile kaydı siliniyor  
  
#### <a name="to-register-a-library-with-the-object-manager"></a>Nesne yöneticisine kitaplık kaydetmek için  
  
1.  Bir kitaplığı oluşturun.  
  
    ```vb  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```csharp  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  Bir nesnenin bir başvuru elde <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> yazın ve arama <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemi.  
  
    ```vb  
    Private Sub RegisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            Throw New Exception("Library already registered with Object Manager")  
        End If  
  
        ' Obtain a reference to IVsObjectManager2 type object.  
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
        If objManager Is Nothing Then  
            Throw New NullReferenceException("GetService failed for SVsObjectManager")  
        End If  
  
        Try  
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)  
        Catch e As Exception  
            ' Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message)  
            Throw  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    private void RegisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
            throw new Exception("Library already registered with Object Manager");  
  
        // Obtain a reference to IVsObjectManager2 type object.  
        IVsObjectManager2 objManager =   
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
        if (objManager == null)  
            throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
        try  
        {  
            int hr =   
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,   
                                                 out m_nLibraryCookie);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
        }  
        catch (Exception e)  
        {  
            // Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message);  
            throw;  
        }  
    }  
  
    ```  
  
#### <a name="to-unregister-a-library-with-the-object-manager"></a>Nesne yöneticisine kitaplık kaydını kaldırmak için  
  
1.  Bir nesnenin bir başvuru elde <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> yazın ve arama <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> yöntemi.  
  
    ```vb  
    Private Sub UnregisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            ' Obtain a reference to IVsObjectManager2 type object.  
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
            If objManager Is Nothing Then  
                Throw New NullReferenceException("GetService failed for SVsObjectManager")  
            End If  
  
            Try  
                objManager.UnregisterLibrary(m_nLibraryCookie)  
            Catch e As Exception  
                ' Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message)  
                Throw  
            Finally  
                m_nLibraryCookie = 0  
            End Try  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UnregisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
        {  
            // Obtain a reference to IVsObjectManager2 type object.  
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
            if (objManager == null)  
                throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
            try  
            {  
                objManager.UnregisterLibrary(m_nLibraryCookie);  
            }  
            catch (Exception e)  
            {  
                // Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message);  
                throw;  
            }  
            finally  
            {  
                m_nLibraryCookie = 0;  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmeti genişletilebilirliği](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Sembol tarama araçlarını destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Nasıl Yapılır: Kitaplık Tarafından Sağlanan Sembollerin Listelerini Nesne Yöneticisine Sunma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)

