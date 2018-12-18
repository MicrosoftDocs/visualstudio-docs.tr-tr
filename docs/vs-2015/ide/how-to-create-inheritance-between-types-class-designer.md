---
title: 'Nasıl yapılır: (Sınıf Tasarımcısı) türler arasında devralma oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5bcc052589f090eaad8aace8c491f74d3bbfefe9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257783"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Nasıl yapılır: (Sınıf Tasarımcısı) türler arasında devralma oluşturma 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir sınıf diyagramında Sınıf Tasarımcısı kullanarak iki tür arasında devralma ilişkisi oluşturmak için türetilmiş bir tür ile temel türü veya türleri bağlanın. İki sınıf arasındaki, bir sınıf ve arabirim arasında veya iki arabirim arasında bir devralma ilişkisi olabilir.  
  
### <a name="to-create-an-inheritance-between-types"></a>Bir türler arasında devralma oluşturma  
  
1.  Çözüm Gezgini'nde, bir projeden bir sınıf diyagramı (.cd) dosyası açın.  
  
     Bir sınıf diyagramı yoksa, oluşturun. Bkz: [nasıl yapılır: sınıf diyagramları ekleme (Sınıf Tasarımcısı) projelerine](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2.  İçinde **araç kutusu**altında **Sınıf Tasarımcısı**, tıklayın **devralma**.  
  
3.  Sınıf diyagramında devralım çizgisi başlayarak, istediğiniz türlerini arasında Çiz:  
  
    -   Temel sınıfın türetilmiş bir sınıf  
  
    -   Uygulanan arabirimi uygulayan sınıfı  
  
    -   Genişletilmiş arabirimi için bir genişletme arabirimi  
  
4.  İsteğe bağlı olarak, genel bir türden türetilmiş bir tür olduğunda, devralım çizgisi tıklayın. İçinde **özellikleri** penceresinde **tür bağımsız değişkenleri** genel tür için istediğiniz türüyle eşleşecek şekilde özelliği.  
  
    > [!NOTE]
    >  Ardından tüm soyut üye bir soyut sınıfı en az bir soyut üye içermesi durumunda, soyut olmayan devralma sınıfları olarak uygulanır.   
    >   
    >  Varolan genel türleri görselleştirebilir olsa da, yeni genel türler oluşturulamıyor. Ayrıca, varolan genel türler için tür parametrelerini değiştiremezsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Devralma](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)   
 [Devralma temelleri](http://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5)   
 [Nasıl yapılır: (Sınıf Tasarımcısı) türler arasında devralmayı görüntüleme](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Sınıf Tasarımcısında Visual C++ Sınıfları](../ide/visual-cpp-classes-in-class-designer.md)



