---
title: Dosya adı uzantıları için fiil kaydetme | Microsoft Docs
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
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a1300f7f66e9c3e9e9cebe3a7b0c7c84e7df4c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782433"
---
# <a name="registering-verbs-for-file-name-extensions"></a>Dosya Adı Uzantıları için Fiil Kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir uygulama bir dosya adı uzantısı ilişkilendirme genellikle bir kullanıcı bir dosyayı çift tıkladığında gerçekleşen tercih edilen bir eylem vardır. Bu eyleme karşılık gelen bir fiil, örneğin açık eylem bağlandığı tercih edilir.  
  
 HKEY_CLASSES_ROOT bulunan Kabuk anahtarı kullanarak bir uzantı için bir programlı tanımlayıcısı (ProgID) ile ilişkili olan fiiller kaydedebilirsiniz\\*ProgID*\shell. Daha fazla bilgi için [dosya türleri](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Standart fiiller kaydediliyor  
 İşletim sistemi, aşağıdaki standart fiiller tanır:  
  
- Open  
  
- Düzenle  
  
- Yürütme  
  
- Yazdırma  
  
- Önizleme  
  
  Mümkün olduğunda, standart bir fiil kaydedin. Açık bir fiil en yaygın seçenektir. Dosyayı açıp dosyayı düzenlemeye arasında NET bir fark varsa düzenleme fiili kullanın. Bir .htm dosyasının düzenleme bir HTML Düzenleyicisi başlatılır ancak örneğin, bir .htm dosyasının açma tarayıcı içinde görüntüler. Standart fiiller ile işletim sistemi yerel yerelleştirilmiştir.  
  
> [!NOTE]
>  Standart fiiller kaydederken açık anahtar için varsayılan değer ayarlı değil. Varsayılan değer menüsünde görüntü dizesini içerir. Bu dize standart fiiller için işletim sistemi sağlar.  
  
 Proje dosyaları, yeni bir örneğini başlatmak için kaydedilmelidir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dosya açıldığında bir kullanıcı. Standart fiili kayıt için aşağıdaki örnekte bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] proje.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 Mevcut bir örneğini içinde bir dosyayı açmaya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], DDEEXEC anahtarını kaydedin. Standart fiili kayıt için aşağıdaki örnekte bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] .cs dosyası.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="setting-the-default-verb"></a>Varsayılan fiili ayarlama  
 Varsayılan fiili bir kullanıcı bir dosyayı Windows Gezgini'nde çift tıkladığında çalıştırılan bir eylemdir. Varsayılan fiili HKEY_CLASSES_ROOT için varsayılan değer olarak belirtilen eylem olan\\*ProgID*\Shell anahtarı. Hiçbir değer belirtilmemişse, varsayılan fiili HKEY_CLASSES_ROOT içinde belirtilen ilk fiil olan\\*ProgID*\Shell anahtar listesi.  
  
> [!NOTE]
>  Varsayılan fiil için uzantı yan yana dağıtım olarak değiştirmeyi planlıyorsanız, yükleme ve kaldırma üzerindeki etkisini göz önünde bulundurun. Yükleme sırasında özgün varsayılan değerin üzerine yazılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yan Yana Dosya İlişkilendirmelerini Yönetme](../extensibility/managing-side-by-side-file-associations.md)

