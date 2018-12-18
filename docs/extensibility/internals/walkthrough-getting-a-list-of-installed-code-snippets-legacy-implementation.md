---
title: Kod parçacıkları (eski) yüklü bir listesini alma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4b09968ea178869dd9a4c6f1caeee83f60f667e3
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513250"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>İzlenecek Yol: Yüklü Kod Parçacıklarının Listesini Alma (Eski Uygulama)
Kod parçacığı bir kaynak arabelleği (yüklü kod parçacıklarının listesini arasında seçmeye olanak tanır) bir menü komutu ile veya bunun eklenen kod parçasıdır. bir IntelliSense tamamlanma listeden bir kod parçacığı kısayol.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> Tüm kod parçacıkları GUID belirli bir dil için yöntemi alır. Bu kod parçacıkları kısayolları bir IntelliSense tamamlanma listesine eklenebilir.  
  
 Bkz: [eski dil hizmetinde kod parçacıkları için destek](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) yönetilen paket framework (MPF) dil hizmetinde kod parçacıkları uygulama hakkında ayrıntılar için.  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Kod parçacıkları listesini almak için  
  
1.  Aşağıdaki kod, belirli bir dil için kod parçacıkları listesini almak nasıl gösterir. Sonuçları bir dizide depolanan <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> yapıları. Bu yöntemde statik <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> almak için yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> alanından arabirim <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> hizmeti. Ancak VSPackage ve arama hizmeti sağlayıcısı ayrıca kullanabileceğiniz <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> yöntemi.  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Package;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service  
    namespace TestLanguage  
    {  
        class TestLanguageService : LanguageService  
        {  
            private void GetSnippets(Guid languageGuid,  
                                     ref ArrayList expansionsList)  
            {  
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));  
                if (textManager != null)  
                {  
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;  
                    if (textManager2 != null)  
                    {  
                        IVsExpansionManager expansionManager = null;  
                        textManager2.GetExpansionManager(out expansionManager);  
                        if (expansionManager != null)  
                        {  
                            // Tell the environment to fetch all of our snippets.  
                            IVsExpansionEnumeration expansionEnumerator = null;  
                            expansionManager.EnumerateExpansions(languageGuid,  
                            0,     // return all info  
                            null,    // return all types  
                            0,     // return all types  
                            1,     // include snippets without types  
                            0,     // do not include duplicates  
                            out expansionEnumerator);  
                            if (expansionEnumerator != null)  
                            {  
                                // Cache our expansions in a VsExpansion array   
                                uint count   = 0;  
                                uint fetched = 0;  
                                VsExpansion expansionInfo = new VsExpansion();  
                                IntPtr[] pExpansionInfo   = new IntPtr[1];  
  
                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.  
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));  
  
                                expansionEnumerator.GetCount(out count);  
                                for (uint i = 0; i < count; i++)  
                                {  
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);  
                                    if (fetched > 0)  
                                    {  
                                        // Convert the returned blob of data into a structure that can be read in managed code.  
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));  
  
                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))  
                                        {  
                                            expansionsList.Add(expansionInfo);  
                                        }  
                                    }  
                                }  
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
### <a name="to-call-the-getsnippets-method"></a>GetSnippets yöntemini çağırmak için  
  
1.  Aşağıdaki yöntemin nasıl çağrılacağı gösterilmektedir `GetSnippets` ayrıştırma işleminin tamamlanma yöntemi. <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> Nedeni ile başlatılan bir ayrıştırma işlemi sonrasında yöntemi çağrıldığında <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
> [!NOTE]
>  `expansionsList` Dizi listesi performansla ilgili nedenlerden dolayı önbelleğe alınır. Kod değişiklikleri değil yansıtılır listesinde dil hizmeti durduruldu yeniden yüklenene kadar (örneğin, durdurup tarafından [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
```csharp  
class TestLanguageService : LanguageService  
{  
    private ArrayList expansionsList;  
  
    public override void OnParseComplete(ParseRequest req)  
    {  
        if (this.expansionsList == null)  
        {  
            this.expansionsList = new ArrayList();  
            GetSnippets(this.GetLanguageServiceGuid(),  
                ref this.expansionsList);  
        }  
    }  
}  
```  
  
### <a name="to-use-the-snippet-information"></a>Kod parçacığı bilgileri kullanmak için  
  
1.  Aşağıdaki kod parçacığı tarafından döndürülen bilgileri işlemi gösterilir `GetSnippets` yöntemi. `AddSnippets` Ayrıştırıcı yanıt olarak kod parçacıkları listesini doldurmak için kullanılan herhangi bir ayrıştırma nedenle yöntemi çağrılır. İlk kez tam ayrıştırma üzere tamamladıktan sonra bu yer almalıdır.  
  
     `AddDeclaration` Yöntemi daha sonra tamamlama listesinde görüntülenen bildirimleri listesini oluşturur.  
  
     `TestDeclaration` Sınıf türü bildiriminin yanı sıra tamamlanma listesi içinde görüntülenen tüm bilgileri içerir.  
  
    ```csharp  
    class TestAuthoringScope : AuthoringScope  
    {  
        public void AddDeclarations(TestDeclaration declaration)  
        {  
            if (m_declarations == null)  
                m_declarations = new List<TestDeclaration>();  
            m_declarations.Add(declaration);  
         }  
    }  
    class TestDeclaration   
    {  
        private string m_name;  
        private string m_description;  
        private string m_type;  
  
        public TestDeclaration(string name, string desc, string type)  
        {  
            m_name = name;  
            m_description = desc;  
            m_type = type;  
        }  
  
    class TestLanguageService : LanguageService  
    {  
        internal void AddSnippets(ref TestAuthoringScope scope)  
        {  
            if (this.expansionsList != null && this.expansionsList.Count > 0)  
            {  
                int count = this.expansionsList.Count;  
                for (int i = 0; i < count; i++)  
                {  
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];  
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,  
                         expansionInfo.description,  
                         "snippet"));  
                }  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski Dil Hizmetinde Kod Parçacıkları için Destek](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)