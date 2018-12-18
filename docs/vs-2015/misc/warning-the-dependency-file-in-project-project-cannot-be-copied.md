---
title: 'Uyarı: bağımlılık &#39;dosya&#39; projesinde &#39;proje&#39; bunu başvurusunun üzerine yazacağından çalıştırma dizinine kopyalanamıyor &#39;dosya. &#39; | Microsoft Docs'
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
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3dad547664768247f7837b9d65797ffba15bbdf8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794822"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>Uyarı: bağımlılık &#39;dosya&#39; projesinde &#39;proje&#39; bunu başvurusunun üzerine yazacağından çalıştırma dizinine kopyalanamıyor &#39;dosya.&#39;
Bağımlılıkları arasında bir çakışma yoktur; aynı ada sahip birden fazla ayrı derleme dosyaları, uygulamayı çalıştırmak için bin dizinine kopyalanmalıdır. Çalıştırma dizinine Bağımlılıklardan biri birincil başvuru olduğundan çakışmayı kuramıyor.  
  
 Bu görev listesine öğeyi çift çakışan birincil başvuru düğümü sürer.  
  
 Bu uyarı bir bağımlılık olur ancak etrafında çakışan Bağımlılıklardan biri ile ilgili bir başvuru olarak eklemeye çalıştı oluşur. Ya bir sürüm 1 başvuru gerekiyordu ve ardından ikinci bir başvuru eklendi ilk başvurunun sürümü 2 hangi kendine başvuruyor.  
  
 Diğer bir deyişle, çözümünüzdeki projelerin birbirine başvurmuş ancak başvuruları dosya başvuruları oluşturulmuş olduğundan bu hata oluşur (kullanarak **Gözat** düğmesine [Başvuru Ekle](http://msdn.microsoft.com/en-us/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) iletişim kutusunda, projeden projeye başvurular yerine) (kullanarak **proje** sekmesinde **Başvuru Ekle** iletişim kutusunda). Projeden projeye başvuru avantajlarından başvuran proje oluşturulan son daraltılmasından değiştiyse bağımlı proje oluşturulacak böylece, yapı sistemindeki projeler arasında bir bağımlılık oluşturmasıdır. Bağımlı proje oluşturmadan başvuran projeyi oluşturmak olasıdır ve başvuru geçersiz olabilmesi için bir dosya başvurusu bir yapı bağımlılığı oluşturmaz; bir proje, projenin önceden oluşturulmuş bir sürümüne başvuruda bulunabilir. Bu mümkün değildir ve bu hata mesajıyla sonuçlanır bin dizininde gerekli tek bir DLL'nin çeşitli sürümleri neden olabilir.  
  
 Bu ileti, bin dizinindeki bir çakışma var ve uygulama düzgün çalışmayabilir her zaman görünür. Bu sorunu geçici olarak çalışmış olabilir, ancak proje sistemi bir bağımlılık sürümünü tüm bileşenleri doğru şekilde çalışıp çalışmayacağını belirleyemediğinden yine de bu uyarı görüntülenir.  
  
 **Bu hatayı düzeltmek için**  
  
-   Bir (veya sıfır) derleme dosyaları, genel derleme önbelleğine derleme dosyalarını koyarak yapılabilir bin dizinine kopyalayın. Genel derleme önbelleğini dosya adı çakışmaları çözer. Ortak dil çalışma zamanı genel derleme önbelleğinde derlemeleri bulmak nasıl bildiğinden hiçbir derleme dosyasını yerel kopyaları sunulacaktır. Daha fazla bilgi için [derlemeler ve genel derleme önbelleği ile çalışma](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) ve [hata: ' % s'bağımlılığı 'proje' projesindeki ' dosya' bağımlılığı ile çakışacağından çalıştırma dizinine kopyalanamıyor ' Dosya '](../misc/error-the-dependency-file-in-project-project-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-file.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)   
 [Genel Derleme Önbelleği](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Nasıl Yapılır: Proje Bağımlılıklarını Oluşturma ve Kaldırma](../ide/how-to-create-and-remove-project-dependencies.md)