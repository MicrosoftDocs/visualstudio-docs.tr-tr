---
title: 'Nasıl yapılır: belge verilerine görünüm ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 46b41c9432970eb9373a80a4e42a92ce82fe9186
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821350"
---
# <a name="how-to-attach-views-to-document-data"></a>Nasıl yapılır: görünümleri ekleme belge verileri
Yeni bir belge görünümü varsa, var olan bir belge veri nesnesine iliştirme mümkün olabilir.  
  
## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Var olan bir belge veri nesnesine ekleyebilirsiniz görünüm belirlemek için  
  
1. Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2. Uygulamanızda `IVsEditorFactory::CreateEditorInstance`, çağrı `QueryInterface` IDE çağırdığında mevcut belge verileri nesne üzerinde `CreateEditorInstance` uygulaması.  
  
    Çağırma `QueryInterface` , belirtilen mevcut belge veri nesnesi incelemenize olanak sağlayan `punkDocDataExisting` parametresi.  
  
    Tam arabirimler sorgulaması gerekir ancak bağlıdır, belgeyi açmayı Düzenleyicisi üzerinde 4. adımında belirtilen şekilde.  
  
3. Mevcut belge veri nesnesi üzerinde uygun arabirimleri bulamazsanız, düzenleyiciniz belge veri nesnesi düzenleyiciniz ile uyumsuz olduğunu belirten bir hata kodu dönün.  
  
    IDE'nin uygulamasında <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, belge başka bir düzenleyicide açık durumda olan ve kapatmak isteyip istemediğinizi soran bir ileti kutusu size bildirir.  
  
4. Bu belge kapatırsanız, Visual Studio Düzenleyicisi Fabrika için ikinci bir kez çağırır. Bu çağrıda `DocDataExisting` parametresi NULL değerine eşittir. Düzenleyici fabrikası uygulamanız sonra belge veri nesnesi kendi Düzenleyicisi'nde açın.  
  
   > [!NOTE]
   >  Var olan bir belge veri nesnesi çalışıp çalışmadığını belirlemek için de arabirim uygulamasına özel bilgi gerçek bir işaretçiye atayarak kullanabilirsiniz [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] özel uygulamanızın sınıfı. Örneğin, tüm standart düzenleyicileri uygulamak `IVsPersistFileFormat`, işlevinden devralan <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Bu nedenle, çağırabilirsiniz `QueryInterface` için <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, sınıf kimliği ve mevcut belge veri nesnesi üzerinde sınıf kimliği uygulamanızın eşleşip eşleşmediğini ve belge veri nesnesi ile çalışabilirsiniz.  
  
## <a name="robust-programming"></a>Güçlü programlama  
 Visual Studio, uygulamanıza çağırdığında <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemi arabimini geri bir işaretçi ise mevcut belge veri nesnesine `punkDocDataExisting` varsa parametresi. Döndürülen belge veri nesnesini inceler `punkDocDataExisting` belge veri nesnesi bu konudaki yordamının 4. adımda not açıklandığı gibi düzenleyiciniz için uygun olup olmadığını belirlemek için. Uygun sonra Düzenleyici fabrikası ikinci bir görünüm için veriler açıklandığı şekilde sağlamalıdır [birden çok belge görünümünü desteklemek](../extensibility/supporting-multiple-document-views.md). Aksi durumda, ardından uygun bir hata iletisi görüntülenmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Birden çok belge görünümünü desteği](../extensibility/supporting-multiple-document-views.md)   
 [Belge verileri ve özel düzenleyicilerde belge görünümü](../extensibility/document-data-and-document-view-in-custom-editors.md)