---
title: 'Hata: bağımlılık &#39;dosya&#39; projesinde &#39;proje&#39; bağımlılığı ile çakışacağından çalıştırma dizinine kopyalanamıyor &#39;dosya&#39; | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4edf474cd67d21833743891eeeb75ce09decb87e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751940"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Hata: bağımlılık &#39;dosya&#39; projesinde &#39;proje&#39; bağımlılığı ile çakışacağından çalıştırma dizinine kopyalanamıyor &#39;dosyası&#39;
Başvuruları arasında bir çakışma yoktur; uygulamanın çalıştırılması bin dizinini kopyalanan aynı dosya adına sahip birden fazla ayrı bağımlılığı. Bağımlılıkları hiçbiri birincil başvurular olmadığından çalıştırma dizinine çakışması çözümlenemiyor.  
  
 Bu hata, yapı başarısız olmasına neden olur.  
  
 Bu görev listesine öğeyi çift çakışma ortaya çıktığını proje için başvurular düğümüne sürer.  
  
 **Bu hatayı düzeltmek için**  
  
-   Bir doğrudan başvuru projenizi biri olun. Bu yaklaşımın olası bir dezavantajı, seçtiğiniz derleme başvurulan derlemenin farklı bir sürümünü gerektiren derlemeleri ile çalışmak için garanti edilmez ' dir.  
  
     \- veya -  
  
-   Her iki kopyasında derlemenin tanımlayıcı adlı ve genel derleme önbelleğinde olduğundan emin olun. Bu derlemeler bin dizinine kopyalanması gereği ortadan kaldırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)   
 [Genel Derleme Önbelleği](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Tanımlayıcı adlı derlemeler](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Bütünleştirilmiş kod sürümü oluşturma](http://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)   
 [Nasıl Yapılır: Proje Bağımlılıklarını Oluşturma ve Kaldırma](../ide/how-to-create-and-remove-project-dependencies.md)