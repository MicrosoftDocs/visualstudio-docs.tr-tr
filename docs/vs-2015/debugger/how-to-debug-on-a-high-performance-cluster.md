---
title: 'Nasıl yapılır: yüksek performanslı kümede hata ayıklama | Microsoft Docs'
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
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75f2a96df18137f04b8b7637940c70378842e23d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747729"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Nasıl Yapılır: Yüksek Performanslı Kümede Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yüksek performanslı kümede çoklu işlem program hata ayıklama uzak bilgisayardaki sıradan bir programın hata ayıklama gibi değildir. Ancak, bazı ek hususlar vardır. Genel Uzaktan Kurulum gereksinimleri için bkz [uzaktan hata ayıklama](../debugger/remote-debugging.md).  
  
 Yüksek performanslı kümede hata ayıklaması yaparken, tüm kullanabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] windows ve uzaktan hata ayıklama için kullanılabilir olan teknikleri hata ayıklama. Ancak, uzaktan hata ayıklaması yaptığınızdan, harici konsol penceresi kullanılabilir değil.  
  
 **İş parçacıkları** penceresi ve **işlemleri** penceresi özellikle paralel uygulamalarda hata ayıklama için yararlıdır. Bu windows kullanma hakkında daha fazla ipucu için bkz. [nasıl yapılır: işlemler penceresini kullanma](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) ve [nasıl yapılır: iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-threads-window.md).  
  
 Aşağıdaki yordamlar, yüksek performanslı kümede hata ayıklama için özellikle yararlı olan bazı teknikleri gösterir.  
  
 Paralel uygulamada hata ayıklaması yaparken, belirli bir iş parçacığı, işlem veya bilgisayarda bir kesme noktası ayarlamak isteyebilirsiniz. Bu, normal bir kesme noktası oluşturarak ve sonra bir kesme noktası filtresi ekleyerek yapabilirsiniz.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Kesme noktası filtresi iletişim kutusunu açmak için  
  
1.  Bir kaynak penceresinde kesme noktası glifine sağ **ayrıştırılmış kodu** penceresinde **çağrı yığını** penceresinde veya **kesme noktaları** penceresi.  
  
2.  Kısayol menüsünde **filtre**. Bu seçenek üst düzey veya alt menüsü altında görünebilir **kesme noktaları**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Belirli bir bilgisayarda bir kesme noktası ayarlamak için  
  
1.  Bilgisayar adını alın **işlemleri** penceresi.  
  
2.  Bir kesme noktası seçin ve açın **kesme noktası filtresi** önceki yordamda açıklanan iletişim kutusu.  
  
3.  İçinde **kesme noktası filtresi** iletişim kutusunda:  
  
     MachineName =*yourmachinename*  
  
     Daha karmaşık bir filtre oluşturmak için kullanarak ifadeleri birleştirebilirsiniz `&`, AND işleci `||`, OR işleci `!`, NOT işleci ve parantezler.  
  
4.  **Tamam**'ı tıklatın.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Belirli bir işlemde bir kesme noktası ayarlamak için  
  
1.  İşlem adı alma veya işlem kimlik numarasını **işlemleri** penceresi.  
  
2.  Bir kesme noktası seçin ve açın **kesme noktası filtresi** ve ilk yordamdaki gibi iletişim kutusu.  
  
3.  İçinde **kesme noktası filtresi** iletişim kutusunda:  
  
     `ProcessName =`  *yourprocessname*  
  
     —veya—  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     Daha karmaşık bir filtre oluşturmak için kullanarak ifadeleri birleştirebilirsiniz `&`, AND işleci `||`, OR işleci `!`, NOT işleci ve parantezler.  
  
4.  **Tamam**'ı tıklatın.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Belirli bir iş parçacığında bir kesme noktası ayarlamak için  
  
1.  İş parçacığı adı veya iş parçacığı kimlik numarasını **iş parçacıkları** penceresi.  
  
2.  Bir kesme noktası seçin ve açın **kesme noktası filtresi** bölümündeki ilk yordamda açıklandığı gibi iletişim kutusu.  
  
3.  İçinde **kesme noktası filtresi** iletişim kutusunda:  
  
     `ThreadName =` *yourthreadname*  
  
     —veya—  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     Daha karmaşık bir filtre oluşturmak için kullanarak ifadeleri birleştirebilirsiniz `&`, AND işleci `||`, OR işleci `!`, NOT işleci ve parantezler.  
  
4.  **Tamam**'ı tıklatın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, adlı bir bilgisayarda bir kesme noktası için bir filtre oluşturma işlemi gösterilmektedir `marvin` ve adlı bir iş parçacığı `fourier1`.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)   
 [Nasıl yapılır: işlemler penceresini kullanma](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Nasıl yapılır: iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-threads-window.md)   
 [İş parçacıklarında ve işlemlerde](http://msdn.microsoft.com/en-us/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Kesme Noktalarını Kullanma](../debugger/using-breakpoints.md)



