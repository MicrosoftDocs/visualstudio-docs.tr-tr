---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 276205ae2aab3c38ceb3d4f1419e0bac13ae626c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273500"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Geri yükler [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] varsayılan ayarları ve otomatik olarak başlatan [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. İsteğe bağlı olarak belirtilen .vssettings dosya ayarlarını sıfırlar.  
  
 Varsayılan ayarlar, profili tarafından belirlenir seçilen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] önce başlatıldı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Arguments  
 `SettingsFile`  
 Uygulanacak .vssettings dosyasının adını ve tam yolunu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Genel Geliştirme Ayarları profilini geri yüklemek için kullanın `General`.  
  
## <a name="remarks"></a>Açıklamalar  
 Hayır ise `SettingsFile` belirtilirse, sonraki başlatışınızda ayar varsayılan koleksiyonunu seçmek için istenir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut satırını dosyasında depolanan ayarları uygular `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv Komut Satırı Anahtarları](../../ide/reference/devenv-command-line-switches.md)



