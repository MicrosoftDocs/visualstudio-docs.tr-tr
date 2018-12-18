---
title: 'Nasıl yapılır: bir komut isteminden profil oluşturucu Karşılaştırma raporu oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 88fac8339491acbe73a4a446cde8afb54fa63143
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814657"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Nasıl yapılır: bir komut isteminden profil oluşturucu Karşılaştırma raporu oluşturma
Oluşturabileceğiniz bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma araçları rapor iki profil oluşturma veri performans verilerini karşılaştırır (. *Vsp* /ya da. *vsps*) dosyaları. Rapor farklar, performans gerileme ve diğer bir profil oluşturma oturumu oluştu iyileştirmeleri gösterir. Rapordaki değerler delta ya da değişiklik, belirttiğiniz dosyanın ilk taban çizgisiyle sunar. Bu delta yeni analiz temel değerdir, eski değer sonuç değeri arasındaki fark belirleyerek hesaplanır. Profil Oluşturucu veri karşılaştırmaları temel işlevleri kodda, uygulama, satırları, yönerge işaretçileri (IP) ve türleri modülleri alabilir.  
  
 Tanımlayıcıları karşılaştırma kategorileri ve alanların listesi için aşağıdaki komutu yazın:  
  
 **VSPerfReport /querydifftables***VspFileName1* *VspFileName2*  
  
 Karşılaştırma raporu oluşturmak için aşağıdaki sözdizimini kullanın:  
  
 **VSPerfReport /diff** `VspFileName1` *VspFileName2* [**/**`Options`]  
  
 Aşağıdaki tablodaki seçenekleri ekleyebilirsiniz **VSPerfReport /diff** komut satırı.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**DiffThreshold:**[*değeri*]|Bu yüzdesi Eşik değerin altına ise farkı dikkate. Ayrıca, bu eşiğin altında olan değerleri yeni verilerle görünmez.|  
|**DiffTable:** *TableName*|Dosyaları karşılaştırmak için bu tabloyu kullanın. Varsayılan olarak, İşlevler tablosuna kullanılır. Listede bir tanımlayıcı belirtin **VSPerfReport /querydifftables**.|  
|**DiffColumn:** *ColumnName*|Bu sütun değerleri karşılaştırmak için kullanın. Varsayılan olarak, özel örnekler Yüzde sütunu kullanılır. Listede bir tanımlayıcı belirtin **VSPerfReport /querydifftables**.|