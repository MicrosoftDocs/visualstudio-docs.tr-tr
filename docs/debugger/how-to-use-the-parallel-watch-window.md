---
title: Paralel iş parçacıklarında değişkenleri bir izleme ayarlayın | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9381479fdfa3d64f3504e947f49411b99d53e2d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857958"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio"></a>Visual Studio'da paralel iş parçacıklarında değişkenleri bir izleme ayarlayın
Paralel İzleme penceresinde aynı anda birden çok iş parçacığında bir ifade tutan değerleri görüntüleyebilirsiniz. Her satır bir uygulama içinde çalışan bir iş parçacığını temsil eder, ancak bir iş parçacığı içinde birden çok satır gösterilebilir. Daha açık belirtmek gerekirse her satır, işlev imzası geçerli yığın çerçevesinde işlevi eşleşen bir işlev çağrısını temsil eder. Sıralama, yeniden sıralama, kaldırmak ve sütunları olan öğeleri gruplayın. Bayrak, işaretsiz dondurma, (askıya) ve (devam) iş parçacıklarını çözme. Aşağıdaki sütunlar görüntülenir **paralel izleme** penceresi:  
  
- Özel dikkat edilmesi gereken istediğiniz bir iş parçacığını işaretle Bayrak sütunu.  
  
- Sarı bir ok geçerli iş parçacığı gösterir geçerli iş parçacığı sütunu (kıvrık kuyruklu yeşil bir ok, geçerli olmayan bir iş parçacığı geçerli hata ayıklayıcı bağlam olduğunu gösterir).  
  
- Makine, işlem, döşeme, görev ve iş parçacığı görüntüleyebilirsiniz yapılandırılabilir bir sütun.  
  
  > [!TIP]
  >  Değiştirilen Görev bilgilerine **paralel izleme** penceresinde ilk açmanız gerektiğini **görev** penceresi.  
  
- Boş *izleme Ekle* izlemek için ifadeleri, girebileceğiniz sütun.  
  
  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Paralel İzleme penceresini görüntülemek için  
  
1.  Kodda bir kesme noktası ayarlayın.  
  
2.  Menü çubuğunda, **hata ayıklama**, **hata ayıklamayı Başlat**. Uygulama kesme noktasına ulaşmak bekler.  
  
3.  Menü çubuğunda, **hata ayıklama**, **Windows**, **paralel izleme**, Gözcü penceresi seçin. Dört adede kadar windows açabilirsiniz.  
  
### <a name="to-add-a-watch-expression"></a>Bir Gözcü ifadesini eklemek için  
  
-   Boş birini *izleme Ekle* sütunları ve ardından bir Gözcü ifadesini girin.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Bir iş parçacığını işaretleme veya işaretini kaldırma için  
  
-   Satır için bayrak sütunu seçin (ilk sütun) veya iş parçacığı için kısayol menüsünü açın ve seçin **bayrağı** veya **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını görüntülemek için  
  
-   Seçin **Göster bayrağı yalnızca** sol alt köşesindeki düğme **paralel izleme** penceresi.  
  
### <a name="to-switch-to-another-thread"></a>Başka bir iş parçacığına geçiş yapmak için  
  
-   Geçerli iş parçacığı sütunu çift tıklayın (ikinci sütun). (Klavye: satırı seçin ve Enter tuşuna basın.)  
  
### <a name="to-sort-a-column"></a>Bir sütunu sıralamak için  
  
-   Sütun başlığı seçin.  
  
### <a name="to-group-threads"></a>İş parçacıklarını gruplandırma  
  
-   Paralel İzleme penceresi kısayol menüsünü açın, **Group By**ve ardından uygun alt öğeyi seçin.  
  
### <a name="to-freeze-or-thaw-threads"></a>Dondurma veya çözme iş parçacığı  
  
-   Satır için kısayol menüsünü açın ve seçin **dondurma** veya **çözme**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Paralel İzleme penceresinde verileri dışarı aktarmak için  
  
-   Seçin **Excel'de Aç** düğmesine ve ardından **Excel'de Aç** veya **CSV'ye aktar**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Bir Boole ifadesine göre filtre uygulamak için  
  
-   Bir Boole ifadesi girin **Boole ifadesine göre filtrele** kutusu. Hata ayıklayıcı, her iş parçacığı bağlamı için ifadeyi hesaplar. Değeri satır `true` görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Nasıl yapılır: GPU iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-gpu-threads-window.md)   
 [İzlenecek yol: C++ AMP Uygulamasında Hata Ayıklama](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)