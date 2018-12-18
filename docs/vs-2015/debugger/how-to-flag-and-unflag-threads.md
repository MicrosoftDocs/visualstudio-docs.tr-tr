---
title: 'Nasıl yapılır: iş parçacıklarını bayrakla işaretleme ve bayrak | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5816007476da56321e58182e636b54a5a5697994
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817496"
---
# <a name="how-to-flag-and-unflag-threads"></a>Nasıl Yapılır: İş Parçacıklarını Bayrakla İşaretleme ve İşareti Geri Alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir simge ile işaretleyerek özel dikkat vermek istediğiniz bir iş parçacığı işaretleyebilirsiniz **iş parçacıkları**, **Paralel Yığınlar**, **paralel izleme**, ve **GPU İş parçacığı** windows. Başkalarının bayraklı iş parçacıklarını diğer iş parçacıklarından ayırt etmek ve bu simgeyi yardımcı olabilir.  
  
 Bayraklı iş parçacıklarını ayrıca Al, özel olarak değerlendirilmesi **iş parçacığı** listesini **hata ayıklama konumu** araç çubuğu. Bu liste tüm iş parçacıkları veya yalnızca bayraklı iş parçacıklarını gösterebilirsiniz. Bir iş parçacığı bayrak olduğunda **iş parçacığı** listesi yalnızca bayraklı iş parçacıklarını gösterecek şekilde otomatik olarak geçer, ancak geçiş yapabilirsiniz tüm iş parçacıklarının uygun şekilde geri gösterilecek.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>İş parçacıkları penceresini kullanarak bir iş parçacığını işaretleme veya işaretini kaldırma için  
  
-   İçinde **iş parçacıkları** penceresinde ilgilendiğiniz iş parçacığı bulup seçmek veya bayrağını temizlemek için bayrak simgesine tıklayın.  
  
### <a name="to-unflag-all-threads"></a>İçin tüm iş parçacıklarının işaretini kaldır  
  
-   İçinde **iş parçacıkları** penceresinde herhangi bir iş parçacığı sağ tıklayın ve ardından **tüm iş parçacıklarını bayrakla**.  
  
### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını görüntülemek için  
  
-   Hata ayıklama penceresinde bayrak düğmesini seçin.  
  
### <a name="to-flag-just-my-code"></a>Bayrak yalnızca kendi kodum  
  
1.  Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresi, bayrak simgesine tıklayın.  
  
2.  Aşağı açılan listesinde, tıklayın **bayrağı yalnızca benim kodum**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Seçili modüller ile ilişkili iş parçacıklarını için  
  
1.  Araç çubuğunda **iş parçacıkları** penceresi, bayrak simgesine tıklayın.  
  
2.  Aşağı açılan listesinde, tıklayın **bayrak Özel Modül Seçimi**.  
  
3.  İçinde **modülleri seçin** iletişim kutusunda, istediğiniz modülleri seçin.  
  
4.  (İsteğe bağlı) İçinde **arama** belirli modüller için aranacak bir dize olarak yazın.  
  
5.  **Tamam**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [İzlenecek Yol: Çok İş Parçacıklı Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-multithreaded-application.md)



