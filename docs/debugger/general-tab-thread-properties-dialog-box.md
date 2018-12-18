---
title: Genel sekmesi, iş parçacığı Özellikleri iletişim kutusu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe6eb87418671b9b070aebaf60d1bb9c84b3623a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474612"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Genel Sekmesi, İş Parçacığı Özellikleri İletişim Kutusu
Belirli bir iş parçacığı hakkında daha fazla bilgi için bu iletişim kutusunu kullanın. Bu iletişim kutusunu görüntülemek için odağı taşımak bir [iş parçacıkları görünümü](../debugger/threads-view.md) penceresi veya açık [iletiler görünümünü](../debugger/messages-view.md) ve bir ileti genişletin. Herhangi bir iş parçacığı düğüm ağaçta seçin, sonra seçin **özellikleri** gelen **Görünüm** menüsü.  
  
 **İş parçacığı özellikleri** iletişim kutusu içeren bir bölme **genel** sekmesi. Aşağıdaki ayarlar kullanılabilir:  
  
|Giriş|Açıklama|  
|-----------|-----------------|  
|**Modül adı**|Modül adı.|  
|**İş parçacığı kimliği**|Bu iş parçacığı benzersiz kimliği. İş parçacığı kimliği numaraları yeniden kullanılır unutmayın; Bunlar, yalnızca o iş parçacığı ömrü için bir iş parçacığı tanımlayın.|  
|**İşlem kimliği**|Bu işlemin benzersiz Kimliğidir. İşlem Kimliği numaraları yeniden kullanılır, bu nedenle bunlar yalnızca işlem süresi için bir işlemi tanımlar. Bir program çalıştırıldığında işlem nesne türü oluşturulur. Bir işlemin tüm iş parçacıklarının aynı adres alanını paylaşır ve aynı verilere erişimi. İşlem kimliği özelliklerini görüntülemek için bu değeri seçin|  
|**İş parçacığı durumu**|İş parçacığı geçerli durumu. Bir çalışan iş parçacığı bir işlemci kullanıyor; Bekleme iş parçacığının yaklaşık bir kullanmaktır. Bir boş olmadığından bir işlemci kullanmak için hazır bir iş parçacığı bekleniyor. Bir iş parçacığında geçiş, disk, disk belleğine alınacak kendi yürütme yığını bekleniyor gibi yürütmek bir kaynak için bekliyor. Bir çevre işleminin tamamlanması için ya da boş olmasını bir kaynak için beklediğinden bekleyen iş parçacığı işlemci gerekmez.|  
|**Neden bekleyin**|Yalnızca iş parçacığı bekleme durumunda olduğunda geçerlidir. Olay çiftleri, korumalı alt sistemleri ile iletişim kurmak için kullanılır.|  
|**CPU süresi**|Bu işlem ve parçacıklarını harcanan toplam CPU zaman. Kullanıcı süresi + ayrıcalıklı zaman eşit.|  
|**Kullanıcı Zamanı**|Bu iş parçacığı kullanıcı modunda kod çalıştırırken harcadığı toplam geçen süre. Pencere Yöneticisi ve grafik altyapısı gibi alt sistemleri gibi uygulamalar kullanıcı modunda çalışır.|  
|**Ayrıcalıklı Zaman**|Bu iş parçacığı ayrıcalıklı modda kod çalıştırırken harcadığı toplam geçen süre. Bir Windows sistem hizmeti çağrıldığında hizmet genellikle sisteme özel verilere erişmek için ayrıcalıklı modda çalışır. Bu tür veriler kullanıcı modunda çalışan iş parçacıklarının erişimden korunur. Sistem çağrıları açık veya örtülü bir sayfa hatası veya bir kesinti oluştuğunda gibi olabilir.|  
|**Geçen süre**|Bu iş parçacığı çalıştığı toplam geçen zaman (saniye cinsinden).|  
|**Geçerli önceliği**|Bu iş parçacığı geçerli dinamik önceliği. Bir işlemdeki iş parçacıkları yükseltmek ve kendi temel önceliği işleminin temel önceliği göre daha düşük.|  
|**Temel önceliği**|Bu iş parçacığının geçerli temel önceliği.|  
|**Başlangıç adresi**|Bu iş parçacığı için sanal adres başlatılıyor.|  
|**Kullanıcı PC**|İş parçacığı için kullanıcı programı sayacı.|  
|**İçerik Geçişi**|Bir iş parçacığından diğerine anahtarlara sayısı. İş parçacığı anahtarları, tek bir işlem içinde veya işlemler arasında gerçekleşebilir. Bir iş parçacığı anahtar başka için bilgi isteyen bir iş parçacığı tarafından ya da daha yüksek bir öncelik iş parçacığı çalışmaya hazır olduğunda boşaltılması bir iş parçacığı tarafından kaynaklanıyor olabilir.|