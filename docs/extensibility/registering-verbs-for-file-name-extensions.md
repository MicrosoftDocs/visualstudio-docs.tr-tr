---
title: Dosya adı uzantıları için fiil kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd42bc89eb853a5d65f8e15eab3fdf2cd054f278
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927807"
---
# <a name="register-verbs-for-file-name-extensions"></a>Dosya adı uzantıları için fiil kaydetme
Bir uygulama bir dosya adı uzantısı ilişkilendirme genellikle bir kullanıcı bir dosyayı çift tıkladığında gerçekleşen tercih edilen bir eylem vardır. Bu eyleme karşılık gelen bir fiil, örneğin açık eylem bağlandığı tercih edilir.  
  
 Kabuk anahtar kullanarak bir uzantı raporu için bir programlı tanımlayıcısı (ProgID) ile ilişkili fiilleri kaydedebilirsiniz **HKEY_CLASSES_ROOT\{ProgID} \shell**. Daha fazla bilgi için [dosya türleri](/windows/desktop/shell/fa-file-types).  
  
## <a name="register-standard-verbs"></a>Standart fiiller kaydetme  
 İşletim sistemi, aşağıdaki standart fiiller tanır:  
  
- Open  
  
- Düzenle  
  
- Yürütme  
  
- Yazdırma  
  
- Önizleme  
  
  Mümkün olduğunda, standart bir fiil kaydedin. Açık bir fiil en yaygın seçenektir. Dosyayı açıp dosyayı düzenlemeye arasında NET bir fark varsa düzenleme fiili kullanın. Örneğin, açma bir *.htm* dosyayı görüntüler, tarayıcı içinde düzenleme ise bir *.htm* dosyasını bir HTML Düzenleyicisi'ni başlatır. Standart fiiller ile işletim sistemi yerel yerelleştirilmiştir.  
  
> [!NOTE]
>  Standart fiiller kaydederken açık anahtar için varsayılan değer ayarlı değil. Varsayılan değer menüsünde görüntü dizesini içerir. Bu dize standart fiiller için işletim sistemi sağlar.  
  
 Proje dosyaları, yeni bir örneğini başlatmak için kaydedilmelidir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dosya açıldığında bir kullanıcı. Standart fiili kayıt için aşağıdaki örnekte bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proje.  
  
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
  
 Mevcut bir örneğini içinde bir dosyayı açmaya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], DDEEXEC anahtarını kaydedin. Standart fiili kayıt için aşağıdaki örnekte bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *.cs* dosya.  
  
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
  
## <a name="set-the-default-verb"></a>Varsayılan fiili ayarlayın  
 Varsayılan fiili bir kullanıcı bir dosyayı Windows Gezgini'nde çift tıkladığında çalıştırılan bir eylemdir. İçin varsayılan değer olarak belirtilen eylem varsayılan eylem olan **HKEY_CLASSES_ROOT\\*ProgID*\Shell** anahtarı. Hiçbir değer belirtilmemişse, varsayılan eylem içinde belirtilen ilk fiili olan **HKEY_CLASSES_ROOT\\*ProgID*\Shell** anahtar listesi.  
  
> [!NOTE]
>  Varsayılan fiil için uzantı yan yana dağıtım olarak değiştirmeyi planlıyorsanız, yükleme ve kaldırma üzerindeki etkisini göz önünde bulundurun. Yükleme sırasında özgün varsayılan değerin üzerine yazılır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yan yana dosya ilişkilendirmelerini yönetme](../extensibility/managing-side-by-side-file-associations.md)
