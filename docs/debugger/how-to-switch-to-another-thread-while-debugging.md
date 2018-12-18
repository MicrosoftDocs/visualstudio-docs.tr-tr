---
title: Hata ayıklarken başka bir iş parçacığına geçme
ms.custom: seodec18
ms.date: 04/27/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45ace6f26f241ecdc39b88060fc4edc6c2e47d91
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057054"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio"></a>Nasıl yapılır: Visual Studio'da hata ayıklarken başka bir iş parçacığına geçiş
Çok iş parçacıklı uygulamada hata ayıklaması yaparken, başka bir iş parçacığına çalıştığınız iş parçacığına geçmek için birkaç yöntemden birini kullanabilirsiniz.

> [!NOTE]
> Hangi iş parçacığı yürütme sırasını denetlemek istiyorsanız, yapmanız [dondurma ve iş parçacıklarını çözme](../debugger/get-started-debugging-multithreaded-apps.md).

Kod Düzenleyicisi ve farklı birden çok iş parçacıklı hata ayıklama windows iş parçacıklarında incelediğinizde, sarı ok geçerli iş parçacığı gösterir. Kıvrık kuyruklu yeşil bir ok, geçerli olmayan bir iş parçacığı geçerli hata ayıklayıcı bağlam sahip olduğunu gösterir.
  
### <a name="to-switch-to-any-thread-that-appears"></a>Görünen tüm iş parçacığına geçiş yapmak için 
  
-   İçinde **iş parçacıkları** veya **paralel izleme** penceresinde iş parçacığını çift tıklayın.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Bir kaynak penceresinde bir iş parçacığına geçiş yapmak için  
  
-   Sol kanaldaki içinde bir iş parçacığı işaret simgesine sağ tıklayın ![iş parçacığı işaret](../debugger/media/dbg-thread-marker.png "ThreadMarker"), işaret **geçin**, tıkladıktan sonra geçiş yapmak istediğiniz o iş parçacığı adı . Yalnızca bu belirli bir konumdaki iş parçacıkları kısayol menüsünü gösterir.  
  
     Hiçbir iş parçacığı işaretçileri görünüyorsa, sağ **iş parçacıkları** penceresi doğrulayın **kaynak iş parçacıklarını Göster** seçilir.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Hata ayıklama konumu araç çubuğunda bir iş parçacığına geçiş yapmak için  
  
1.  Üzerinde **hata ayıklama konumu** araç çubuğunda tıklatın **iş parçacığı** listesi.  
  
2.  Listede, geçiş yapmak istediğiniz iş parçacığı tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok İş Parçacıklı Uygulamaların Hatalarını Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
