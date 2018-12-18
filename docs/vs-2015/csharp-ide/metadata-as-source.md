---
title: Kaynak olarak meta veriler | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- Go To Definition command
- Code Definition window, viewing metadata as source
- metadata as source [C#]
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8bcac8071d0cc76c29a5b9d0478727fea0b59901
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232953"
---
# <a name="metadata-as-source"></a>Kaynak olarak Meta Veriler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak olarak meta veriler, C# kaynak kodu bir salt okunur arabellek olarak belirir meta verilerini görüntülemenizi sağlar. Bu türler ve üyeler (uygulamalar) olmadan bildirimlerini bir görünümünü sağlar. Çalıştırarak bir kaynak olarak meta verileri görüntüleyebilirsiniz **tanıma** komutunu türleri veya üyeleri kaynak kodu, proje veya çözüm kullanılabilir değil.  
  
> [!NOTE]
>  Çalıştırılacak çalıştığınızda **tanıma** komut türleri veya iç olarak işaretlenmiş üyeleri için tümleşik geliştirme ortamı (IDE) görüntülemiyor meta verilerinin bağımsız olarak bir kaynak olarak başvurulan derleme arkadaş veya olur.  
  
 Ya da Kod Düzenleyicisi'nde kaynak olarak meta verilerini görüntüleyin veya **kod tanımı** penceresi.  
  
## <a name="viewing-metadata-as-source-in-the-code-editor"></a>Kod Düzenleyicisi'nde kaynak olarak meta veri görüntüleme  
 Çalıştırdığınızda **tanıma** komut, kaynak kodu kullanılamaz bir öğe için bu öğeye ait meta veri kaynağı olarak görüntülenen bir görünümünü içeren sekmeli belge, Kod Düzenleyicisi'nde görünür. Türün adını ve ardından **[meta verilerden]**, belgenin sekmesinde görünür.  
  
 Örneğin çalıştırırsanız, **tanıma** komutunu <xref:System.Console>, meta verileri <xref:System.Console> bildiriminden benzeyen C# kaynak kodu, ancak bir uygulama olmadan Kod Düzenleyicisi'nde görünür.  
  
 ![Kaynak olarak meta veriler](../csharp-ide/media/metadatasource.png "MetadataSource")  
  
## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>Kod tanımı penceresinde kaynak olarak meta veri görüntüleme  
 Zaman **kod tanımı** penceresinde etkin veya görünür, IDE otomatik olarak yürütür **tanıma** içindeseçiliöğeleriveKodDüzenleyicisi'ndeimlecinaltındakiöğeleriçinkomutu **Sınıf Görünümü** veya **Nesne Tarayıcısı**. Kaynak kodu, bu öğe için kullanılabilir durumda değilse, IDE öğenin meta veri kaynağı olarak görüntüler. **kod tanımı** penceresi.  
  
 Örneğin, sözcük içindeki imlecinizi yerleştirdiğiniz <xref:System.Console> Kod Düzenleyicisi'nde, meta verileri <xref:System.Console> kaynağı olarak görünür **kod tanımı** penceresi. Kaynak benzer <xref:System.Console> bildirimi, ancak bir uygulama olmadan.  
  
 Görünür bir öğe bildirimi görmek istiyorsanız **kod tanımı** penceresinde öğeyi sağ tıklatıp **tanıma**.