---
title: Üst kapsayıcı klasörleri oluşturma çözümleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87fbda8cb55d0d2a6ef9f21a2a7878d4babd3fe6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830698"
---
# <a name="create-parent-container-folders-for-solutions"></a>Üst kapsayıcı klasörleri çözümleri oluşturun
İçinde kaynak denetimi eklentisi API sürümü 1.2, bir kullanıcı bir çözüm içindeki tüm web projeleri için tek bir kök kaynak denetimi hedef belirtebilirsiniz. Bu tek köklü bir süper birleşik kök (SUR) olarak adlandırılır.  
  
 Kullanıcı çok projeli bir çözüm kaynak denetimi eklediyseniz kaynak denetimi eklentisi API sürüm 1.1, her bir web projesi için bir kaynak denetimi hedefini belirlemek için kullanıcı istendi.  
  
## <a name="new-capability-flags"></a>Yeni özellik bayrakları  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Yeni işlevleri  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE bir çözüm kaynak denetimine eklerken SUR klasör neredeyse her zaman oluşturur. Özellikle, bunu aşağıdaki durumlarda yapar:  
  
-   Bir dosya paylaşımı web projesi projedir.  
  
-   Proje ve çözüm dosyasını farklı sürücülere vardır.  
  
-   Proje ve çözüm dosyasını farklı paylaşımları vardır.  
  
-   Projeleri ayrı olarak (bir kaynak kontrol çözümünde) eklendi.  
  

İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], SUR klasörün adını uzantısı olmadan çözüm adı ile aynı olması önerilir. İki sürüm davranış aşağıdaki tabloda özetlenmiştir.  
  
|Özellik|Kaynak Denetimi Eklentisi API sürümü 1.1|Kaynak Denetimi Eklentisi API sürümü 1.2|  
|-------------| - | - |  
|SCC için çözüm ekleyin|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Kaynak-denetimli çözüme proje ekleme|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Not:** Visual Studio çözüm Sur doğrudan alt olduğunu varsayar|  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki tabloda, iki örnek listeler. Her iki durumda da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanıcı kadar kaynak denetimi altında bir çözüm için bir hedef konum istenir *user_choice* hedef olarak belirtilir. User_choice belirtildiğinde, çözüm ve iki proje kaynak denetimi hedefler için kullanıcıya sormadan eklenir.  
  
|Çözüm içeriyor|Disk konumları|Veritabanı varsayılan yapısı|  
|-----------------------|-----------------------|--------------------------------|  
|*sln1.sln*<br /><br /> Web1'i<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/ < user_choice > / sln1<br /><br /> $/ < user_choice >/C/Web1<br /><br /> $/ < user_choice > / Web2|  
|*sln1.sln*<br /><br /> Web1'i<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/ < user_choice > / sln1<br /><br /> $/ < user_choice >/D/Web1'i<br /><br /> $/ < user_choice >/sln1/win1|  
  
 Alt klasörleri ve klasör SUR işlemi iptal edildi veya bir hata nedeniyle başarısız bağımsız olarak oluşturulur. Bunlar iptal veya hata koşulları otomatik olarak kaldırılmaz.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kaynak Denetimi Eklentisi oluşmazsa sürüm 1.1 davranışı için varsayılan olarak `SCC_CAP_CREATESUBPROJECT` ve `SCC_CAP_GETPARENTPROJECT` özellik bayrakları. Ayrıca, kullanıcıları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aşağıdaki anahtarı değerini ayarlayarak sürüm 1.1 davranışa dönmek seçebilirsiniz *DWORD: 00000001*:  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *DWORD: 00000001*
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak Denetimi Eklentisi API sürümü 1.2 yenilikler nelerdir?](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)