---
title: 'Nasıl yapılır: GPU iş parçacıkları penceresini kullanma | Microsoft Docs'
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
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8afd9cd09cf5977f58ee3a48b891f5291869b49c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799177"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Nasıl Yapılır: GPU İş Parçacıkları Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

GPU iş parçacıkları penceresinde inceleyin ve uygulamada hata ayıklaması yaptığınız GPU üzerinde çalışan iş parçacıklarının çalışın. GPU üzerinde çalışan uygulamalar hakkında daha fazla bilgi için bkz: [C++ AMP'ye genel bakış](http://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc).  
  
 GPU iş parçacıkları penceresi, her satır tüm sütunları aynı değerleri içeren GPU iş parçacıkları kümesini temsil eden bir tablo içeriyor. Sıralama, yeniden sıralama, kaldırmak ve sütunları olan öğeleri gruplayın. Bayrak, işaretsiz dondurma, (askıya alma) ve GPU iş parçacıkları penceresinden (devam) iş parçacıklarını çözme. Aşağıdaki sütunlar, GPU iş parçacıkları penceresinde görüntülenir:  
  
- Özel dikkat edilmesi gereken istediğiniz bir iş parçacığını işaretle Bayrak sütunu.  
  
- Sarı okun etkin bir iş parçacığı gösteren etkin iş parçacığı sütunu. Bir ok, burada hata ayıklayıcıya yürütmeyi kesmeden bir iş parçacığı belirtir.  
  
- **İş parçacığı sayısı** sütunuyla aynı konumda iş parçacığı sayısını görüntüler.  
  
- **Satırı** her iş parçacığı grubunun bulunduğu kod satırını görüntülüyor sütunu.  
  
- **Adresi** her iş parçacığı grubunun bulunduğu yönerge adresini görüntüleyen bir sütun. Bu sütun varsayılan olarak gizlidir.  
  
- **Konumu** kaynak kodu konumu olan sütun.  
  
- **Durumu** iş parçacığının etkin, engellenmiş, başlatılmamış veya tam olup olmadığını gösteren bir sütun.  
  
- **Döşeme** satırdaki iş parçacıkları için döşeme dizinini gösteren sütunu.  
  
  Tablo üstbilgisinin kutucuğu ve iş parçacığı görüntülenmesini gösterir.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>GPU iş parçacıkları penceresini görüntülemek için  
  
1.  İçinde **Çözüm Gezgini**, proje için kısayol menüsünü açın ve ardından **özellikleri**.  
  
2.  İçinde **özellik sayfaları** proje penceresi altında **yapılandırma özellikleri**, seçin **hata ayıklama**.  
  
3.  İçinde **başlatmak için hata ayıklayıcı** listesinden **yerel Windows hata ayıklayıcı**. İçinde **hata ayıklayıcı türü** listesinden **yalnızca GPU**. Bu hata ayıklayıcı kesme noktalarında GPU'da çalışan kod bölüneceği seçmeniz gerekir.  
  
4.  Seçin **Tamam** düğmesi.  
  
5.  GPU kodunda bir kesme noktası ayarlayın.  
  
6.  Menü çubuğunda, **hata ayıklama**, **hata ayıklamayı Başlat**. Uygulama kesme noktasına ulaşmak bekler.  
  
7.  Bir menü çubuğu seçin **hata ayıklama**, **Windows**, **GPU iş parçacıkları**.  
  
### <a name="to-change-to-a-different-active-thread"></a>Farklı bir etkin iş parçacığı değiştirmek için  
  
-   Sütununu çift tıklatın. (Klavye: satırı seçin ve ENTER tuşuna basın.)  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Belirli döşeme ve iş parçacığı görüntülemek için  
  
1.  Seçin **değiştirici genişletin veya iş parçacığı** GPU iş parçacıkları penceresinde düğmesine.  
  
2.  Kutucuk ve iş parçacığı değerleri, metin kutularına girin.  
  
3.  Ok bulunan düğmesini seçin.  
  
### <a name="to-display-or-hide-a-column"></a>Bir sütunu sakla ya da görüntülemek için  
  
-   GPU iş parçacıkları penceresi için kısayol menüsünü açın, **sütunları**, göstermek veya gizlemek istediğiniz sütunu seçin.  
  
### <a name="to-sort-by-a-column"></a>Bir sütuna göre sıralamak için  
  
-   Sütun başlığı seçin.  
  
### <a name="to-group-threads"></a>İş parçacıklarını gruplandırma  
  
-   GPU iş parçacıkları penceresi için kısayol menüsünü açın, **Group By**, görüntülenen sütun adlarından birini seçin. Seçin **hiçbiri** iş parçacıklarının çözmek için.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Dondurma veya çözme iş parçacığı bir satır için  
  
-   Satır için kısayol menüsünü açın ve seçin **dondurma** veya **çözme**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>İş parçacığı satırının işaretleme veya işaretini kaldırma için  
  
-   İş parçacığının Bayrak sütunu seçin veya iş parçacığı için kısayol menüsünü açın ve seçin **bayrağı** veya **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını görüntülemek için  
  
-   GPU iş parçacıkları penceresinde bayrak düğmesini seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Nasıl yapılır: paralel İzleme penceresini kullanma](../debugger/how-to-use-the-parallel-watch-window.md)   
 [İzlenecek yol: C++ AMP Uygulamasında Hata Ayıklama](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)



