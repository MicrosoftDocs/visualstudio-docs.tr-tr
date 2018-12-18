---
title: Tasarım zamanında derlemeleri çözme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad24bcf461dab05444f0e26ffd4e0c826f3f2bed
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153468"
---
# <a name="resolve-assemblies-at-design-time"></a>Tasarım zamanında derlemeleri çözme
Bir derlemeye bir başvuru eklediğinizde **.NET** sekmesinde **Başvuru Ekle** iletişim kutusunda, bir ara başvuru bütünleştirilmiş kodu başvuru işaret eder; diğer bir deyişle, tüm türü içeren bir bütünleştirilmiş kod ve imza bilgilerini ancak mutlaka içermediğinden herhangi bir kod. **.NET** sekmesi, .NET Framework çalışma zamanı derlemeleri karşılık gelen başvuru derlemelerini listeler. Ayrıca, çalışma zamanı derlemeleri üçüncü taraflar tarafından kullanılan kayıtlı AssemblyFoldersEx klasörlerdeki karşılık gelen başvuru derlemelerini listeler.  
  
## <a name="multi-targeting"></a>Çoklu sürüm desteği  
 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] Hedef ya da sürüm 2.0 ortak dil çalışma zamanı (CLR) üzerinde çalışan .NET Framework sürümlerinde veya sürüm sayesinde 4. Bu sürümler, .NET Framework sürümleri 2.0, 3.0, 3.5, 4, 4.5 ve 4.5.1 ve Silverlight sürüm 1.0, 2.0 ve 3.0 içerir. Yeni bir .NET Framework sürümü, CLR Version 2.0 sürümü üzerinde temel veya sürüm 4 yayımlanır, Framework targeting pack kullanılarak yüklenebilir ve bu otomatik olarak Visual Studio'da hedefi olarak gösterilir.  
  
## <a name="how-type-resolution-works"></a>Çözüm works nasıl yazın  
 Çalışma zamanında CLR bütünleştirilmiş kodundaki türler GAC'de bakarak çözümler *bin* dizin ve yoklama yollar. Bu fusion yükleyicisi tarafından işlenir. Ancak, ne, aradığı fusion yükleyici nasıl bilir? Uygulama zaman oluşturulmadan tasarım zamanında yapılan bir çözüm bağlıdır.  
  
 Derleme sırasında derleyici, başvuru bütünleştirilmiş kodları kullanarak uygulama türlerini çözümler. .NET Framework yüklendiğinde .NET Framework sürümlerinde 2.0, 3.0, 3.5, 4, 4.5 ve 4.5.1, başvuru bütünleştirilmiş kodları yükleyin.  
  
 Başvuru bütünleştirilmiş kodları, karşılık gelen .NET Framework SDK sürümüyle birlikte gönderilen hedefleme paketini tarafından sağlanır. Framework, yalnızca çalışma zamanı derlemeleri sağlar. Uygulamaları oluşturmak için hem .NET Framework hem de ilgili .NET Framework SDK'yı yüklemeniz gerekir.  
  
 Belirli bir .NET Framework hedefleme, derleme sistemi targeting pack başvuru derlemelerini kullanarak tüm türleri çözümler. Çalışma zamanında fusion Yükleyici bu aynı tür GAC genellikle bulunan çalışma zamanı derlemeleri çözümler.  
  
 Başvuru bütünleştirilmiş kodları mevcut değilse derleme sisteminin çalışma zamanı derlemeleri kullanarak derleme türlerini çözümler. GAC içindeki çalışma zamanı derlemeleri alt sürüm numaralarına göre ayırt edilen değildir çünkü çözüm yanlış derlemeye yapılan mümkündür. .NET Framework sürüm 3.5 tanıtılan yeni bir yöntem sürüm 3.0 hedefleyen sırasında başvuruluyorsa Bu, örneğin, meydana gelmiş olabilir. Derleme başarılı olur ve uygulama derleme makinesi üzerinde çalışır, ancak sürüm 3.5 yüklü olmayan bir makine dağıtıldığında başarısız olur.  
  
 Artık .NET Framework SDK ile birlikte gelen hedefleme paketini Framework'ün yanlış karşı türleri çözümlemek için derleme sistemini imkansızdır (redist) yeniden dağıtım listesi olarak adlandırılan bu sürümünde tüm çalışma zamanının derlemelerin bir listesini içerir. bütünleştirilmiş kod sürümü.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)