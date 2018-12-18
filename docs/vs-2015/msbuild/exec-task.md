---
title: Yürütme görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3d092a6d69f668ef48ca2f586494f848795c178
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300540"
---
# <a name="exec-task"></a>Yürütme Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Belirtilen program veya komut belirtilen bağımsız değişkenler kullanılarak çalıştırır.  
  
## <a name="parameters"></a>Parametreler  
 Parametreler için aşağıdaki tabloda açıklanmıştır `Exec` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Command`|Gerekli `String` parametresi.<br /><br /> Çalıştırılacak komut. Bunlar, attrib gibi sistem komutlarını veya program.exe, runprogram.bat veya setup.msi gibi bir yürütülebilir dosya olabilir.<br /><br /> Bu parametre, komutları birden fazla satır içerebilir. Alternatif olarak, bir toplu iş dosyasında birden çok komut yerleştirin ve bu parametre kullanarak çalıştırabilirsiniz.|  
|`CustomErrorRegularExpression`|İsteğe bağlı `String` parametresi.<br /><br /> Araç çıktısı nokta hatası satırlarda kullanılacak normal bir ifade belirtir. Bu, olağan dışı derecede biçimlendirilmiş çıktı oluşturmak için Araçlar kullanışlıdır.|  
|`CustomWarningRegularExpression`|İsteğe bağlı `String` parametresi.<br /><br /> Araç çıktısı nokta uyarı satırları için kullanılan normal bir ifade belirtir. Bu, olağan dışı derecede biçimlendirilmiş çıktı oluşturmak için Araçlar kullanışlıdır.|  
|`ExitCode`|İsteğe bağlı `Int32` çıkış parametresi salt okunur.<br /><br /> Yürütülen komutun tarafından sağlanan çıkış kodu belirtir.|  
|`IgnoreExitCode`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev tarafından yürütülen komutun sağlanan çıkış kodu yoksayar. Aksi halde, bir görev döndürür `false` Yürütülen komutun bir sıfır olmayan çıkış kodu döndürmesi durumunda.|  
|`IgnoreStandardErrorWarningFormat`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `false`, standart hata/uyarı biçim ile eşleşmesi çıktısında satırları seçer ve bunları hataları/uyarıları günlüğe kaydeder. Varsa `true`, bu davranışı devre dışı.|  
|`Outputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Görev çıktısı öğeleri içerir. `Exec` Görev bu kendisini ayarlamaz. Bunları ayarlamak gibi böylece daha sonra projede kullanılan bunun yerine, bunları sağlayabilirsiniz.|  
|`StdErrEncoding`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yakalanan görev standart hata akışı kodlamasını belirtir. Geçerli varsayılandır konsol çıktı kodlaması.|  
|`StdOutEncoding`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yakalanan görev standart çıkış akışına kodlamasını belirtir. Geçerli varsayılandır konsol çıktı kodlaması.|  
|`WorkingDirectory`|İsteğe bağlı `String` parametresi.<br /><br /> Komutun yürütüleceği dizini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görevi, belirli bir zaman yararlı [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] gerçekleştirmek istediğiniz işlemi kullanılabilir değil görev. Ancak, `Exec` daha belirli bir görevin farklı bir görev çıkış aracından toplamak veya çalıştırdığını komutu.  
  
 `Exec` Görev doğrudan bir işlem çağırmak yerine cmd.exe çağırır.  
  
 Bu belgede listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.ToolTask> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Exec` bir komutu çalıştırmak için görev.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



