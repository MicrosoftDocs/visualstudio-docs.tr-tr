---
title: Alan sekmesi, işlem özellikleri iletişim kutusu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee4b5a416c7d3eb466498e7cf4ff727134c0f20f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476087"
---
# <a name="space-tab-process-properties-dialog-box"></a>Alan Sekmesi, İşlem Özellikleri İletişim Kutusu
Kullanım **alanı** adres alanı, bir işlemin incelemek için sekmesi. Görüntülenecek [işlem özellikleri iletişim kutusu](../debugger/process-properties-dialog-box.md), odağı taşımak bir [işlemler görünümü](../debugger/processes-view.md) penceresi. Ağaçta herhangi bir işlem düğümü seçin ve ardından **özellikleri** gelen **Görünüm** menüsü.  
  
 Aşağıdaki ayarlar kullanılabilir **alanı** sekmesi:  
  
|Giriş|Açıklama|  
|-----------|-----------------|  
|**Alanı olarak işaretlenmiş Göster**|Kategori alanı (görüntü, eşlenen, ayrılmış veya atanmamış) seçmek için bu liste kutusunu kullanın.|  
|**Yürütülebilir bayt**|Seçilen kategori, bu işlemi kullanan tüm adres alanı toplamı. Yürütülebilir bellek programlar tarafından çalıştırılabilir, ancak değil okunur veya olabilir yazılmış bellektir.|  
|**Exec salt okunur bayt**|Seçilen kategori, bu süreç kullanılarak salt okunur özellikler ile kullanmak üzere tüm adres alanında toplamı. Exec salt okunur bellek yürütülen okuma yanı sıra bellektir.|  
|**Exec okuma yazma bayt**|Seçilen kategori, bu süreç kullanılarak okuma-yazma özelliklerini kullanmaya tüm adres alanında toplamı. Exec okuma yazma bellek programlar tarafından yürütülen yanı sıra okunabilir ve değiştiren bellektir.|  
|**Exec-Kopyala baytları yazma**|Seçilen kategori, programlar tarafından yürütülen yanı sıra okunabilir ve yazılan tüm adres alanı toplamı. Bu tür koruma bellek işlemler arasında paylaşılmak üzere gerektiğinde kullanılır. Ardından bunlar paylaşan işlemler bellek salt okunur, tüm aynı bellek kullanır. Paylaşan bir işlem yazma erişimi isterse bir kopyasını bu bellek için işlem yapılacaktır.|  
|**Erişim yok bayt**|Seçilen kategori, bir işlem bunu kullanmanızı engelliyor tüm adres alanı toplamı. Erişim ihlali yazma ise oluşturulur veya okuma denenir.|  
|**Salt okunur bayt**|Seçilen kategori, yürütülen okuma yanı sıra tüm adres alanı toplamı.|  
|**Okuma-yazma bayt**|Seçilen kategori, okuma ve yazma sağlayan tüm adres alanı toplamı.|  
|**Yazma kopyası bayt**|Seçilen kategori için tüm adres alanının toplam bellek okumak için ancak yazma için paylaşımı sağlayan. İşlemler bu belleği okurken, bunlar aynı bellek paylaşabilirsiniz. Ancak, bu paylaşılan bellek, okuma/yazma erişimi bir paylaşım işlem istediği zaman, belleğin kopyası yazma için yapılır.|