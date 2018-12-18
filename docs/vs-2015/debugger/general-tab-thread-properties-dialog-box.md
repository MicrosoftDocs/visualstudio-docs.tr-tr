---
title: Genel sekmesi, iş parçacığı Özellikleri iletişim kutusu | Microsoft Docs
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
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2777096e13ef649f2a340d3b3cae92d050d9531f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728980"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Genel Sekmesi, İş Parçacığı Özellikleri İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirli bir iş parçacığı hakkında daha fazla bilgi için bu iletişim kutusunu kullanın. Bu iletişim kutusunu görüntülemek için odağı taşıyın. bir [iş parçacıkları görünümü](../debugger/threads-view.md) penceresi veya açık [iletiler görünümünü](../debugger/messages-view.md) ve bir ileti genişletin. Herhangi bir iş parçacığı düğüm ağaçta seçin ve ardından **özellikleri** gelen **görünümü** menüsü.  
  
 **İş parçacığı özellikleri** iletişim kutusu içeren bir bölme **genel** sekmesi. Aşağıdaki ayarlar kullanılabilir:  
  
|Giriş|Açıklama|  
|-----------|-----------------|  
|**Modül adı**|Modülün adı.|  
|**İş parçacığı kimliği**|Bu iş parçacığının benzersiz kimliği. Not; iş parçacığı kimliği numaraları yeniden kullanılır Bunlar, bu iş parçacığının ömrü boyunca yalnızca bir iş parçacığı belirleyin.|  
|**İşlem kimliği**|Bu işlem benzersiz kimliği. Bunlar işlem ömrü boyunca yalnızca bir işlemi tanımlamak için işlem kimliği numaraları yeniden kullanılır. İşlem nesnesi türü, bir program çalıştırıldığında oluşturulur. Bir işlemdeki tüm iş parçacıkları, aynı adres alanı paylaşabilir ve aynı verilere erişebilir. İşlem kimliği özelliklerini görüntülemek için bu değeri seçin|  
|**İş parçacığı durumu**|İş parçacığının geçerli durumu. Bir çalışan iş parçacığı bir işlemci kullanıyor; bir bekleme kullanmak için iş parçacığıdır. Bir boş olmadığı için bir işlemci kullanacak şekilde bir hazır iş parçacığı bekleniyor. Bir iş parçacığı geçişi, yürütme, içinde diskten disk belleğine alınacak yürütme yığınını beklediğiniz gibi bir kaynak için bekliyor. Bekleyen iş parçacığı, çevre bir işlemin tamamlanması ya da boş olacak bir kaynak için beklediği işlemci gerekmez.|  
|**Bekleme nedeni**|Bu, yalnızca iş parçacığı bekleme durumunda olduğunda geçerlidir. Olay çifti, korumalı alt sistemleri ile iletişim kurmak için kullanılır.|  
|**CPU süresi**|Bu işlem ve kendi iş parçacığı üzerinde harcanan toplam CPU süresi. Kullanıcı zaman + ayrıcalıklı zaman eşit.|  
|**Kullanıcı Zamanı**|Bu iş parçacığı kullanıcı modunda kod çalıştırırken harcadığı geçen toplam geçen süre. Alt pencere yöneticisi ve grafik altyapısı gibi gibi uygulamalar kullanıcı modunda yürütün.|  
|**Ayrıcalıklı Zaman**|Bu iş parçacığı ayrıcalıklı modda kod çalıştırırken harcadığı geçen toplam geçen süre. Bir Windows sistem hizmeti çağrıldığında, hizmet genellikle sisteme özel verilere erişim elde etmek için ayrıcalıklı modda çalışır. Bu tür veriler kullanıcı modunda çalışan iş parçacıklarının erişimden korunur. Sistem çağrıları açık veya örtük bir sayfa hatasını veya bir kesme oluştuğunda gibi olabilir.|  
|**Geçen süre**|İş parçacığının çalıştığı toplam geçen süre (saniye cinsinden).|  
|**Geçerli öncelik**|Bu iş parçacığı geçerli dinamik önceliği. Bir işlemdeki iş parçacıkları, yükseltmek ve kendi temel öncelik işleminin temel öncelik göre daha düşük.|  
|**Temel öncelik**|Bu iş parçacığının geçerli temel öncelik.|  
|**Başlangıç adresi**|Bu iş parçacığı için sanal adres başlatılıyor.|  
|**Kullanıcı PC'si**|İş parçacığı için kullanıcı program sayacının.|  
|**Bağlam geçişleri**|Bir iş parçacığından anahtarlara sayısı. İş parçacığı anahtarlar, tek bir işlem içinde veya işlemler arasında ortaya çıkabilir. Bir iş parçacığı anahtarı bilgilerini soran başka bir iş parçacığı tarafından ya da daha yüksek öncelikli iş parçacığı çalışmaya hazır hale geldiğinde boşaltılması bir iş parçacığı tarafından kaynaklanabilir.|



