---
title: Projeleri derlemek için birden çok işlemci kullanma | Microsoft Docs
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
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b873b8ab1668ea2fea3b3bf0487339a86c9ffe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199920"
---
# <a name="using-multiple-processors-to-build-projects"></a>Projeleri Derlemek için Birden Çok İşlemci Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild, birden çok işlemci veya birden çok çekirdekli işlemcilere sahip sistemler yararlanabilirsiniz. Bir yapı işlemi için kullanılabilir her işlemci oluşturulur. Sistem dört işlemci varsa, örneğin, ardından dört yapı işlemlerini oluşturulur. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Bu yapılar aynı anda işleyebilir ve bu nedenle genel derleme süresi azalır. Ancak, paralel yapı, yapı işlemlerini nasıl ortaya bazı değişiklikler ortaya çıkarır. Bu konu, bu değişiklikleri açıklamaktadır.  
  
## <a name="project-to-project-references"></a>Projeden Projeye Başvurular  
 Zaman [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] yalnızca bir kez başvuru yapıların karşılaşıyorsa, bir projeyi derlemek için paralel kullanırken bir projeden projeye (P2P) başvuru oluşturur. İki proje aynı P2P başvurusu varsa, başvuru her proje için yeniden değil. Bunun yerine, yapı altyapısının aynı bağımlı her iki proje P2P başvuru döndürür. Gelecekteki isteklerde oturum aynı hedef için aynı P2P başvuru sağlanır.  
  
## <a name="cycle-detection"></a>Döngü Algılama  
 Döngü algılama İşlevler, aynı, önceden olduğu gibi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0, tek farkı, artık [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] farklı bir saat veya yapı içinde döngüsü algılanması bildirebilirsiniz.  
  
## <a name="errors-and-exceptions-during-parallel-builds"></a>Paralel Yapılar Sırasında Hatalar ve Özel Durumlar  
 Paralel yapılar hatalar ve özel durumlar farklı zamanlarda, paralel olmayan bir derlemede yapın ve bir proje değil oluşturduğunuzda bir proje yapılarında devam ortaya çıkabilir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] başarısız bir paralel derleme herhangi bir proje yapı durdurmaz. Diğer projeler bunların başarılı veya başarısız kadar oluşturmaya devam edin. Ancak, varsa <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> hata oluşması durumunda hiçbir derleme durur etkinleştirildi.  
  
## <a name="visual-c-project-vcproj-and-solution-sln-files"></a>Visual C++ Projesi (.vcproj) ve Çözüm (.sln) Dosyaları  
 Her ikisi de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] için proje (.vcproj) ve çözüm (.sln) dosyaları geçirilebilir [MSBuild görevi](../msbuild/msbuild-task.md). İçin [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projeleri VCWrapperProject çağrılır, ardından iç [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje oluşturulur. İçin [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] çözümleri, bir SolutionWrapperProject oluşturulur ve ardından dahili [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje oluşturulur. Her iki durumda da elde edilen proje değerlendirilir diğer aynı [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje.  
  
## <a name="multi-process-execution"></a>Birden Çok İşlem Yürütme  
 Neredeyse tüm derlemeyle ilgili etkinlikler, geçerli dizin yolu ile ilgili hataları önlemek için derleme işlem süresince sabit kalması gerekir. Bu nedenle, farklı iş parçacıkları üzerinde projeleri çalıştırılamaz [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] çünkü birden çok dizin oluşturulmasına neden olur.  
  
 Bu sorundan kaçınmak, ancak yine de çok işlemcili yapılar etkinleştirmek için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] "işleminin kullandığı yalıtım." İşlem yalıtım kullanarak [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] en fazla oluşturabilirsiniz `n` işlemleri, burada `n` sistemde kullanılabilir işlemci sayısına eşittir. Örneğin, varsa [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] derlemeleri yapı süreçlerini, yapı yalnızca iki sonra iki işlemciye sahip bir sistemde bir çözüm oluşturulur. Bu işlemler Çözümdeki tüm projeleri derlemek için yeniden kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel birden çok proje derleme](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)   
 [Görevler](../msbuild/msbuild-tasks.md)



