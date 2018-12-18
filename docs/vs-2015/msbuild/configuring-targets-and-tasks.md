---
title: Hedefleri ve görevleri yapılandırma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1bb82483b0adef6343423984e3b0d6fa21d0d678
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263522"
---
# <a name="configuring-targets-and-tasks"></a>Hedefleri ve Görevleri Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild hedefleri ve görevleri çalıştırmak için yapılandırabilirsiniz giden işlem MSBuild ile böylece üzerinde çalıştığını olandan farklı Bağlamlar hedefleyebilirsiniz. Örneğin, geliştirme bilgisayarında .NET Framework 4.5 64-bit işletim sisteminde çalışırken bir 32 bitlik .NET Framework 2.0 uygulama hedefleyebilirsiniz. .NET Framework 4 veya önceki sürümleri çalıştıran bilgisayarlar ayrıca hedefleyebilirsiniz. 32 veya 64 bit ve belirli bir .NET Framework sürüm birleşimi olarak da bilinen *hedef bağlam*.  
  
## <a name="installation"></a>Yükleme  
 .NET Framework 4.5 ve 4.5.1 yeniden adlandırma olmadan ortak dil çalışma zamanı (CLR), hedefler, görevleri ve araçlar .NET Framework 4'ün değiştirin. .NET Framework 4.5.1 parçası olarak yüklenir [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].  
  
 MSBuild Visual Studio'dan ayrı olarak yüklemek istiyorsanız, yükleme paketinden indirebilirsiniz [MSBuild indirme](http://go.microsoft.com/fwlink/?LinkId=309745). Ayrıca, ayrıca kullanmak istediğiniz .NET Framework sürümleri yüklemeniz gerekir.  
  
## <a name="targets-and-tasks"></a>Hedefler ve Görevler  
 MSBuild çalıştırmaları belirli bağlamları daha büyük bir hedef için işlem dışı Görevler oluşturun.  Örneğin, 32-bit MSBuild 64 bit bilgisayar hedeflemek için 64-bit işlem içinde derleme görevi çalışabilir. Bu tarafından denetlenir `UsingTask` bağımsız değişkenleri ve `Task` parametreleri. Bu bağımsız değişkenleri ve parametreleri tarafından .NET Framework 4.5 yüklü hedeflerini ayarlayın ve değişiklik çeşitli hedef bağlamları yönelik uygulamalar oluşturmak için gerekli değildir.  
  
 Kendi hedef bağlam oluşturmak istiyorsanız, bu bağımsız değişkenleri ve parametreleri uygun şekilde ayarlamanız gerekir. .NET Framework 4.5 Microsoft.Common.targets dosyasına ve örnekler için Microsoft.Common.Tasks dosyasına bakın.  Birden fazla hedef bağlamı ile çalışabilmeniz için özel bir görev oluşturma veya var olan görevleri değişiklik yapma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma hedefleri ve görevleri](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)



