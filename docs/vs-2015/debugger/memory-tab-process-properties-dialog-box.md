---
title: Bellek sekmesi, işlem özellikleri iletişim kutusu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92718a20f5deb19890a58d68af85e7f897f2440a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785150"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Bellek Sekmesi, İşlem Özellikleri İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanım **bellek** nasıl bir işlem bellek kullanıyor göstermek için sekmesinde. Görüntülenecek [işlem özellikleri iletişim kutusu](../debugger/process-properties-dialog-box.md), odağı Taşı bir [işlemler görünümü](../debugger/processes-view.md) penceresi. Herhangi bir işlem düğümü ağacında seçin ve ardından **özellikleri** gelen **görünümü** menüsü.  
  
 Aşağıdaki ayarlar kullanılabilir **bellek** sekmesinde:  
  
|Giriş|Açıklama|  
|-----------|-----------------|  
|**Sanal bayt sayısı**|İşlemin kullandığı sanal adres alanının geçerli boyutunu (bayt cinsinden). Sanal adres alanının kullanılması ilgili disk veya ana bellek sayfalarının kullanımını göstermez. Ancak, sanal adres alanı sınırlıdır ve kullanarak kitaplık yükleme olanağı işleminin çok sınırlayabilir.|  
|**Tepedeki sanal baytlar**|İşlemin sanal adres alanının bayt sayısı, herhangi bir zamanda kullandı.|  
|**Çalışma kümesi**|İşlemdeki iş parçacıkları tarafından yakın zamanda dokunulan bellek sayfası kümesidir. Bilgisayardaki boş bellek eşiğin üzerinde ise, kullanım olmasa bile sayfaları işlemin çalışma kümesinde bir işlemin bırakılır. Boş bellek eşiğin altına düştüğünde, sayfalar çalışma kümesinden atılır. Gerekirse, bunlar ana bellekten ayrılmadan önce bunlar geçici hatalı-çalışma kümesine geri olacaktır.|  
|**En yüksek çalışma kümesi**|Herhangi bir noktada bu işlemin çalışma kümesindeki sayfaları maksimum sayısı.|  
|**Disk belleğine alınan havuz baytları**|Havuzda işlem ayırdığı miktarı. Disk belleğine alınan havuz nerede bunlar kaldırmasını görevlerini tamamlaması gibi alanı işletim sistemi bileşenlerin alımını bir sistem bellek alanıdır. Disk belleğine alınan havuz sayfaları sistem tarafından sürdürülen sürelerle erişilemeyen disk belleği dosyasına belleğine.|  
|**Disk belleği olmayan havuz bayt sayısı**|Geçerli işlem tarafından ayrılan disk belleği olmayan havuz bayt sayısı. Disk belleğine alınmayan havuz nerede bunlar kaldırmasını görevlerini tamamlaması gibi alanı işletim sistemi bileşenleri tarafından alındığını bir sistem bellek alanıdır. Disk belleğine alınmayan havuz sayfaları için disk belleği dosyası belleğine olamaz; Bunlar, ayrıldıkları sürece ana bellekte kalır.|  
|**Özel bayt sayısı**|Bu işlem, ayrılan bayt geçerli sayısı, diğer işlemlerle paylaşılamaz.|  
|**Boş baytlar**|Bu işlemin toplam kullanılmayan sanal adres alanı.|  
|**Ayrılan baytlar**|Bu işlem tarafından kullanılmak üzere ayrılmış sanal bellek miktarı.|  
|**Boş görüntü baytları**|Kullanımda olmayan ya da bu işlem yansımalar tarafından ayrılan sanal adres alanı miktarı.|  
|**Ayrılmış görüntü baytları**|Tüm sanal görüntüleri tarafından ayrılan bellek toplam bu işlem içinde çalıştırın.|



