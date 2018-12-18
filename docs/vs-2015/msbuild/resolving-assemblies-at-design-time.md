---
title: Tasarım zamanında derlemeleri çözme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc10169ac07efdeded41a9bb2990bdc206a17435
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224659"
---
# <a name="resolving-assemblies-at-design-time"></a>Tasarım Zamanında Derlemeleri Çözme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Başvuru Başvuru Ekle iletişim kutusunun .NET sekmesinde aracılığıyla bir derlemeye bir başvuru eklediğinizde, bir ara başvuru bütünleştirilmiş kodu için diğer bir deyişle, derlemedeki tüm tür ve imza bilgileri içeren, ancak bu mutlaka içermiyor gösterir. kodu. .NET sekmesinde, .NET Framework çalışma zamanı derlemeleri karşılık gelen başvuru derlemelerini listeler. Ayrıca, çalışma zamanı derlemeleri üçüncü taraflar tarafından kullanılan kayıtlı AssemblyFoldersEx klasörlerdeki karşılık gelen başvuru derlemelerini listeler.  
  
## <a name="multi-targeting"></a>Çoklu Sürüm Desteği  
 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] Hedef ya da sürüm 2.0 ortak dil çalışma zamanı (CLR) üzerinde çalışan .NET Framework sürümlerinde veya sürüm sayesinde 4. Bu, .NET Framework sürümleri 2.0, 3.0, 3.5, 4, 4.5 ve 4.5.1 ve Silverlight sürümleri 1.0, 2.0 ve 3.0 içerir. Yeni bir .NET Framework sürümü, CLR Version 2.0 sürümü üzerinde temel veya sürüm 4 yayımlanır, Framework targeting pack kullanılarak yüklenebilir ve bu otomatik olarak Visual Studio'da hedefi olarak gösterilir.  
  
## <a name="how-type-resolution-works"></a>Tür Çözümlemesi Nasıl Çalışır?  
 Çalışma zamanında, bin dizini GAC'deki ve yoklama yollar bakarak bütünleştirilmiş kodundaki türler CLR çözümler. Bu fusion yükleyicisi tarafından işlenir. Ancak, ne, aradığı fusion yükleyici nasıl bilir? Bu, uygulamanın ne zaman oluşturulmuştur tasarım zamanında yapılan bir çözüm bağlıdır.  
  
 Derleme sırasında derleyici, başvuru bütünleştirilmiş kodları kullanarak uygulama türlerini çözümler. .NET Framework yüklendiğinde .NET Framework sürümlerinde 2.0, 3.0, 3.5, 4, 4.5 ve 4.5.1, başvuru bütünleştirilmiş kodları yüklenir.  
  
 Başvuru bütünleştirilmiş kodları, karşılık gelen .NET Framework SDK sürümüyle birlikte gönderilen hedefleme paketini tarafından sağlanır. Framework, yalnızca çalışma zamanı derlemeleri sağlar. Uygulamaları oluşturmak için hem .NET Framework hem de ilgili .NET Framework SDK'yı yüklemeniz gerekir.  
  
 Belirli bir .NET Framework hedefleme, derleme sistemi targeting pack başvuru derlemelerini kullanarak tüm türleri çözümler. Çalışma zamanında fusion Yükleyici bu aynı tür GAC genellikle bulunan çalışma zamanı derlemeleri çözümler.  
  
 Başvuru bütünleştirilmiş kodları mevcut değilse derleme sisteminin çalışma zamanı derlemeleri kullanarak derleme türlerini çözümler. GAC içindeki çalışma zamanı derlemeleri alt sürüm numaralarına göre ayırt değil çünkü çözüm yanlış derlemeye yapılan mümkündür. .NET Framework sürüm 3.5 tanıtılan yeni bir yöntem sürüm 3.0 hedefleyen sırasında başvuruluyorsa Bu, örneğin, meydana gelmiş olabilir. Derleme başarılı olur ve uygulama derleme makinesi üzerinde çalışır, ancak sürüm 3.5 yüklü olmayan bir makine dağıtıldığında başarısız olur.  
  
 Şimdi .NET Framework SDK ile birlikte gelen hedefleme paketini tüm çalışma zamanı derlemelerinin listesi (redist) yeniden dağıtım listesi olarak adlandırılan Framework'ün bu sürümünde içerir. Bu, yanlış derleme sürümüne karşı türleri çözümlemek için derleme sistemini mümkün kılar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş Kavramlar](../msbuild/msbuild-advanced-concepts.md)



