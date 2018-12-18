---
title: Üst kapsayıcı klasörleri oluşturma çözümleri | Microsoft Docs
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
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0a65595b7dabc28a6851820141a71460d84a4b73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762541"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Çözümler için Üst Kapsayıcı Klasörleri Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak Denetimi Eklentisi API sürümü 1.2, bir kullanıcı bir çözüm içindeki tüm Web projeleri için tek bir kök kaynak denetimi hedef olarak belirtebilirsiniz. Bu tek köklü bir süper birleşik kök (SUR) olarak adlandırılır.  
  
 Kullanıcı çok projeli bir çözüm kaynak denetimi eklediyseniz kaynak denetimi eklentisi API sürüm 1.1, her bir Web projesi için bir kaynak denetimi hedefini belirlemek için kullanıcı istendi.  
  
## <a name="new-capability-flags"></a>Yeni özellik bayrakları  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Yeni işlevleri  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE bir çözüm kaynak denetimine eklerken SUR klasör neredeyse her zaman oluşturur. Özellikle, bunu aşağıdaki durumlarda yapar:  
  
- Bir dosya paylaşımı Web projesi projedir.  
  
- Proje ve çözüm dosyasını farklı sürücülere vardır.  
  
- Proje ve çözüm dosyasını farklı paylaşımları vardır.  
  
- Projeleri ayrı olarak (bir kaynak kontrol çözümünde) eklendi.  
  
  İçinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] SUR klasörün adını uzantısı olmadan çözüm adı ile aynı olması önerilir. İki sürüm davranış aşağıdaki tabloda özetlenmiştir.  
  
|Özellik|Tkaynak denetimi eklentisi API sürüm 1.1|Kaynak Denetimi Eklentisi API sürümü 1.2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|SCC için çözüm ekleyin|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Kaynak-denetimli çözüme proje ekleme|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Not:** Visual Studio çözüm Sur doğrudan alt olduğunu varsayar|  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki tabloda, iki örnek listeler. Her iki durumda da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kullanıcı kadar kaynak denetimi altında bir çözüm için bir hedef konum istenir *user_choice* hedef olarak belirtilir. User_choice belirtildiğinde, çözüm ve iki proje kaynak denetimi hedefler için kullanıcıya sormadan eklenir.  
  
|Çözüm içeriyor|Disk konumları|Veritabanı varsayılan yapısı|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1'i<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1'i<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /D/web1<br /><br /> $/*user_choice*  /sln1/win1|  
  
 SUR klasör ve alt klasörleri işlemi iptal edildi veya bir hata nedeniyle başarısız bağımsız olarak oluşturulur. Bunlar iptal veya hata koşulları otomatik olarak kaldırılmaz.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kaynak Denetimi Eklentisi oluşmazsa sürüm 1.1 davranışı için varsayılan olarak `SCC_CAP_CREATESUBPROJECT` ve `SCC_CAP_GETPARENTPROJECT` özellik bayrakları. Ayrıca, kullanıcıları [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] için DWORD: 00000001 aşağıdaki anahtarının değerini ayarlayarak sürüm 1.1 davranışa dönmek seçebilirsiniz:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

