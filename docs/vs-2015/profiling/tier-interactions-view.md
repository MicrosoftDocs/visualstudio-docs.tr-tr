---
title: Katman etkileşimleri görünümü | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b69144569738dc09368453faef13f5f38428df2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726156"
---
# <a name="tier-interactions-view"></a>Katman Etkileşimleri Görünümü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Katman etkileşim profili oluşturma veritabanları ile iletişim kuran çok verili uygulamaların yürütme sürelerini işlevleri hakkında ek bilgi sağlayan [!INCLUDE[vstecado](../includes/vstecado-md.md)]. Verileri yalnızca zaman uyumlu işlev çağrıları için toplanır.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]  
  
  Etkileşimleri görünümü iki dosyada katman etkileşim verileri görüntüler:  
  
- Ana bölme bir hiyerarşik ağaç vardır. Veritabanı bağlantıları ilişkin birleşik veriler en üst düzey satır içeren bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] sayfası ya da işlem. Alt düğümler üst veritabanı bağlantıları ilişkin birleşik veriler içerir.  
  
- Bir veritabanı çağrısı düğüm ana bölmede tıkladığınızda, veriler veritabanı çağrısı örneği için Ayrıntılar bölmesinde görüntülenir.  
  
  Süre, milisaniye sayısını veya CPU saat işareti olarak görüntülenir. Görüntülenen zaman birimi değiştirmek için tıklayın **Araçları** menüsünde tıklayın **seçenekleri**ve ardından aşağıdakilerden birini seçin **zamanın gösterilme biçimi değerleri olarak** seçenekleri.  
  
## <a name="master-pane"></a>Ana bölmesi  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|-Bir üst düzey satır, profili oluşturulmuş işlem ya da Web sayfası adı için.<br />-Veritabanı bağlantısı için bir satır, veritabanını barındıran sunucunun adı.|  
|**Veritabanı**|(Yalnızca veritabanı bağlantı satırlar) veritabanının adı.|  
|**Sayısı**|İşlem, Web sayfası veya veritabanı bağlantısı tarafından oluşturulan isteklerinin toplam sayısı.|  
|**Toplam geçen süre**|İşlem, Web sayfası veya veritabanı bağlantısı herhangi bir isteği yürütmek için harcanan toplam süre.|  
|**Geçen maksimum süre**|İşlem, Web sayfası veya veritabanı bağlantısı herhangi bir istek yürütülürken harcanan maksimum süre.|  
|**Geçen minimum süre**|İşlem, Web sayfası veya veritabanı bağlantısı herhangi bir istek yürütülürken harcanan minimum süre.|  
|**Geçen ortalama süre**|İşlem, Web sayfası veya veritabanı bağlantısı isteği yürütmek için harcanan ortalama süre.|  
  
## <a name="database-connection-details-pane"></a>Veritabanı bağlantı ayrıntıları bölmesi  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Komut metni**|İsteğin SQL sorgusu.|  
|**Sorgu sayısı**|Sorgu çalıştırılma sayısı.|  
|**Toplam geçen süre**|Örnek sorgu yürütmek için harcanan toplam süre.|  
|**Geçen maksimum süre**|Herhangi bir örnek sorgu yürütmek için harcanan maksimum süre.|  
|**Geçen minimum süre**|Herhangi bir örnek sorgu yürütmek için harcanan minimum süre.|  
|**Geçen ortalama süre**|Bir örnek sorgu yürütmek için harcanan ortalama süre.|



