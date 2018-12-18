---
title: Hata ayıklayıcıda GPU iş parçacıkları görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4f4577fc7e1a26481ff4ab5aa94888cf5668adf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825365"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Nasıl Yapılır: GPU İş Parçacıkları Penceresini Kullanma
GPU iş parçacıkları penceresinde inceleyin ve uygulamada hata ayıklaması yaptığınız GPU üzerinde çalışan iş parçacıklarının çalışın. GPU üzerinde çalışan uygulamalar hakkında daha fazla bilgi için bkz: [C++ AMP'ye genel bakış](/cpp/parallel/amp/cpp-amp-overview).  
  
 GPU iş parçacıkları penceresi, her satır tüm sütunları aynı değerleri içeren GPU iş parçacıkları kümesini temsil eden bir tablo içeriyor. Sıralama, yeniden sıralama, kaldırmak ve sütunları olan öğeleri gruplayın. Bayrak, işaretsiz dondurma, (askıya alma) ve GPU iş parçacıkları penceresinden (devam) iş parçacıklarını çözme. Aşağıdaki sütunlar, GPU iş parçacıkları penceresinde görüntülenir:  
  
- Özel dikkat edilmesi gereken istediğiniz bir iş parçacığını işaretle Bayrak sütunu.  
  
- Sarı bir ok geçerli iş parçacığı gösterir geçerli iş parçacığı sütunu.  
  
- **İş parçacığı sayısı** sütunuyla aynı konumda iş parçacığı sayısını görüntüler.  
  
- **Satırı** her iş parçacığı grubunun bulunduğu kod satırını görüntülüyor sütunu.  
  
- **Adresi** her iş parçacığı grubunun bulunduğu yönerge adresini görüntüleyen bir sütun. Bu sütun varsayılan olarak gizlidir.  
  
- **Konumu** kaynak kodu konumu olan sütun.  
  
- **Durumu** iş parçacığının etkin, engellenmiş, başlatılmamış veya tam olup olmadığını gösteren bir sütun.  
  
- **Döşeme** satırdaki iş parçacıkları için döşeme dizinini gösteren sütunu.  
  
  Tablo üstbilgisinin kutucuğu ve iş parçacığı görüntülenmesini gösterir.  
  
  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>GPU iş parçacıkları penceresini görüntülemek için  
  
1.  İçinde **Çözüm Gezgini**, proje için kısayol menüsünü açın ve ardından **özellikleri**.  
  
2.  İçinde **özellik sayfaları** proje penceresi altında **yapılandırma özellikleri**, seçin **hata ayıklama**.  
  
3.  İçinde **başlatmak için hata ayıklayıcı** listesinden **yerel Windows hata ayıklayıcı**. İçinde **hata ayıklayıcı türü** listesinden **yalnızca GPU**. Bu hata ayıklayıcı kesme noktalarında GPU'da çalışan kod bölüneceği seçmeniz gerekir.  
  
4.  Seçin **Tamam** düğmesi.  
  
5.  GPU kodunda bir kesme noktası ayarlayın.  
  
6.  Menü çubuğunda, **hata ayıklama**, **hata ayıklamayı Başlat**. Uygulama kesme noktasına ulaşmak bekler.  
  
7.  Bir menü çubuğu seçin **hata ayıklama**, **Windows**, **GPU iş parçacıkları**.  
  
### <a name="to-switch-to-a-different-thread"></a>Farklı bir iş parçacığına geçiş yapmak için  
  
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
 [İzlenecek yol: C++ AMP Uygulamasında Hata Ayıklama](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)