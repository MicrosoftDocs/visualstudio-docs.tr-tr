---
title: Proje dosyalarında verileri kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adc7d06b8479da4aef7042fd64702cff5ca3be60
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900663"
---
# <a name="save-data-in-project-files"></a>Proje dosyalarında verileri kaydetme
Proje alt kaydedebilir ve proje dosyasındaki alt özgü verileri alma. Yönetilen paket Framework (MPF), bu görevi gerçekleştirmek için iki arabirim sağlar:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Erişim özellik değerleri için arabirim sağlar **MSBuild** proje dosyasının. Tarafından sağlanan yöntemleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> yüklemek veya kaydetmek için kullanıcı gereksinimlerini ilgili verileri oluşturduğunuzda, herhangi bir kullanıcı tarafından çağrılabilir.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Serbest biçimli XML olmayan derleme ilgili verileri kalıcı hale getirmek için kullanılır. Tarafından sağlanan yöntemleri <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> tarafından aranır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] her [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] derleme olmayan proje dosyasındaki ilgili verileri kalıcı hale getirilmesi.  
  
  Derleme ve ilgili derleme olmayan verileri kalıcı hale getirmek nasıl hakkında daha fazla bilgi için bkz. [MSBuild proje dosyasında verileri kalıcı hale getirmenize](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## <a name="save-and-retrieve-build-related-data"></a>İlgili verileri Kaydet ve Al oluşturun  
  
### <a name="to-save-a-build-related-data-in-the-project-file"></a>İlgili verileri proje dosyasındaki bir yapı kaydetmek için  
  
-   Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> proje dosyasının tam yol kaydetmek için yöntemi.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string newFullPath = GetNewFullPath();  
    // Set a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));  
    ```  
  
### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Proje dosyasından ilgili verileri derleme almak için  
  
-   Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> proje dosyasının tam yol almak için yöntemi.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string fullPath;  
    // Get a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));  
    ```  
  
## <a name="save-and-retrieve-non-build-related-data"></a>Kaydet ve derleme olmayan ilgili verileri alma  
  
### <a name="to-save-non-build-related-data-in-the-project-file"></a>İlgili verileri proje dosyasındaki derleme olmayan kaydetmek için  
  
1.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> kendi geçerli dosyasını bir XML parçası son başlatıldığından beri değiştirilip değiştirilmediğini saptamak için yönteminin kaydedildi.  
  
    ```  
    public int IsFragmentDirty(uint storage, out int pfDirty)  
    {  
        pfDirty = 0;  
        switch (storage)  
        {  
            case (uint)_PersistStorageType.PST_PROJECT_FILE:  
            {  
                if (isDirty)  
                    pfDirty |= 1;  
                break;  
            }  
            case (uint)_PersistStorageType.PST_USER_FILE:  
            {  
                // We do not store anything in the user file.  
                break;  
            }  
        }  
  
        // Forward the call to inner flavor(s)   
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);  
  
        return VSConstants.S_OK;  
  
    }  
    ```  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> proje dosyasında XML verileri kaydetmek için yöntemi.  
  
    ```  
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)  
    {  
        pbstrXMLFragment = null;  
  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Create XML for our data.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode root = doc.CreateElement(this.GetType().Name);  
  
                    XmlNode node = doc.CreateElement(targetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));  
                    root.AppendChild(node);  
  
                    node = doc.CreateElement(updateTargetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));  
                    root.AppendChild(node);  
  
                    doc.AppendChild(root);  
                    // Get XML fragment representing our data  
                    pbstrXMLFragment = doc.InnerXml;  
  
                    if (fClearDirty != 0)  
                        isDirty = false;  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Derleme olmayan proje dosyasındaki ilgili verileri almak için  
  
1.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> proje uzantısı özellikleri ve diğer yapı bağımsız veri başlatmak için yöntemi. XML yapılandırma verilerini proje dosyasında mevcut değilse bu yöntem çağrılır.  
  
    ```  
    public int InitNew(ref Guid guidFlavor, uint storage)  
    {  
        //Return,if it is our guid.  
        if (IsMyFlavorGuid(ref guidFlavor))  
            return VSConstants.S_OK;  
  
        //Forward the call to inner flavor(s).  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);  
  
        return VSConstants.S_OK;  
    ```  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> proje dosyasından XML verileri yüklemek için yöntemi.  
  
    ```  
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)  
    {  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Load our data from the XML fragment.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode node = doc.CreateElement(this.GetType().Name);  
                    node.InnerXml = pszXMLFragment;  
                    if (node == null  
                        || node.FirstChild == null  
                        || node.FirstChild.ChildNodes.Count == 0  
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)  
                        break;  
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;  
  
                    if (node.FirstChild.ChildNodes.Count <= 1  
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)  
                        break;  
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
> [!NOTE]
>  Bu konuda sağlanan tüm kod örnekleri daha büyük bir örneğin bölümlerdir [VSSDK örnekleri](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [MSBuild proje dosyasında verileri kalıcı hale getirmenize](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)