---
title: Yalıtılmış Kabuk giriş noktası parametreleri (C++) | Microsoft Docs
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
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 270a5c932429a518447d0029b05d3c9522db7387
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749158"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Yalıtılmış Kabuk giriş noktası parametreleri (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio shell tabanlı bir uygulama başladığında Visual Studio Kabuğu başlangıç giriş noktası çağırır. Aşağıdaki ayarlar, kabuk başlangıç giriş noktası çağrısında kılınabilir. Her ayarın bir açıklaması için bkz: [. Pkgdef dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
- CommandLineLogo  
  
- DefaultHomePage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- HideSolutionConcept  
  
- NewProjDlgInstalledTemplatesHdr  
  
- NewProjDlgSlnTreeNodeTitle  
  
- SolutionFileCreatorIdentifier  
  
- SolutionFileExt  
  
- UserFilesSubFolderName  
  
- UserOptsFileExt  
  
  Visual Studio Kabuğu yalıtılmış şablona bir kaynak dosyası oluşturur *solutionName*.cpp, burada *solutionName* uygulama için çözüm adı. Bu dosya _tWinMain işlevi uygulamanın ana giriş noktasını tanımlar. Bu işlev, kabuk başlangıç giriş noktası çağırır.  
  
  Uygulama davranışını, uygulama başlatıldığında, bu ayarları değiştirerek değiştirebilirsiniz.  
  
## <a name="parameters"></a>Parametreler  
 Visual Studio Kabuğu başlangıç giriş noktası beş parametreleri tanımlar. İlk dört parametre değiştirmeyin. Beşinci parametrenin ayarları geçersiz kılma listesini alır. Kabuk başlangıç giriş noktası bir uygulamanın ana giriş noktasından çağrılır.  
  
 Kabuk başlangıç giriş noktasını aşağıdaki imza içeriyor.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 İstemediğiniz herhangi bir uygulama ayarı geçersiz kılmak için ayarları bırakın parametresi null bir işaretçi olarak geçersiz kılın.  
  
 Bir veya daha fazla ayarlarını geçersiz kılmak için geçersiz kılınacak ayarlarını içeren bir Unicode dizesini geçirin. Ad-değer çiftleri noktalı virgülle ayrılmış bir listesini dizedir. Her çifti ayarını uygulamak için değer ardından eşittir (=), arkasından geçersiz kılmak için ayar adını içerir.  
  
> [!NOTE]
>  Boşluk, Unicode dizelerini içermez.  
  
 Boole ayarları için aşağıdaki dizelerden true değerini temsil eder; tüm dizeleri false değerini temsil eder. Bu dizeler büyük/küçük harfe duyarsızdır.  
  
-   \+  
  
-   1.  
  
-   -1  
  
-   on  
  
-   true  
  
-   Evet  
  
## <a name="example"></a>Örnek  
 Eklentileri devre dışı bırakın ve uygulamanız için varsayılan proje konumu değiştirmek için "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp" en son parametreye ayarlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yalıtılmış Kabuğu özelleştirme](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgdef Dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)

