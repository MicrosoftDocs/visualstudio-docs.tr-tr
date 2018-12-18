---
title: 'Nasıl yapılır: MSBuild.exe kullanarak çözümlerde belirli hedefleri derleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb1dc2885d64999ac9f4d12568fd7da29a783d8e
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880662"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Nasıl yapılır: MSBuild.exe kullanarak çözümlerde belirli hedefleri derleme
Kullanabileceğiniz *MSBuild.exe* belirli projelerin bir çözümde belirli hedefler oluşturmak için.  
  
#### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Belirli bir hedef bir çözümde belirli bir proje oluşturmak için  
  
1.  Komut satırında `MSBuild.exe <SolutionName>.sln`burada `<SolutionName>` yürütmek istediğiniz hedef içeren çözüm dosya adına karşılık gelir.  
  
2. Sonra hedef belirtmek `-target:` geçiş biçiminde \<ProjectName >:\<TargetName >. Proje adı bu karakterlerden herhangi birini içeriyorsa, `%`, `$`, `@`, `;`, `.`, `(`, `)`, veya `'`, bunları değiştirin bir `_` belirtilen Hedef adı.
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yürütür `Rebuild` hedefinin `NotInSlnFolder` proje ve sonra yürütür `Clean` hedefinin `InSolutionFolder` bulunan proje *Yeniklasör* Çözüm klasörü.  
  
```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Sorun giderme

Kullanabileceğiniz seçenekler incelemek isterseniz, bunu yapmak için MSBuild tarafından sağlanan bir hata ayıklama seçeneği kullanabilirsiniz. Ortam değişkenini ayarlamak `MSBUILDEMITSOLUTION=1` ve çözümünüzü oluşturun. Bu adlı bir MSBuild dosyası oluşturur  *\<SolutionName >. sln.metaproj* oluşturma zamanında çözümü MSBuild'ın iç görünümünü gösterir. Hangi hedeflerin oluşturmak kullanılabilir olduğunu belirlemek için bu görünümü inceleyebilirsiniz.

Bu ortam değişkeni bu iç görünüm gerekmedikçe kümesi oluşturun. Bu ayar, çözümünüzün proje derleme sorunlara neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.  
 [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [MSBuild](../msbuild/msbuild.md)  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)
