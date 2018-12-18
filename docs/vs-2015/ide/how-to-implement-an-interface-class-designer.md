---
title: 'Nasıl yapılır: arabirimi uygulama (Sınıf Tasarımcısı) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9a196f49765623966a48b07eef3abe3f8ca7e5a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900546"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Nasıl Yapılır: Arabirimi Uygulama (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı'nda, sınıf diyagramı üzerinde arabirim yöntemleri için kod sağlayan bir sınıf bağlanarak bir arabirim uygulayabilir. Sınıf Tasarımcısı, bir arabirim uygulaması oluşturur ve arabirim ve sınıfları arasındaki ilişki devralma ilişkisi görüntüler. Devralım çizgisi sınıf ve arabirim arasında çizim veya sınıf görünümünden arabirimi sürükleyerek bir arabirim uygulayabilir.  
  
> [!TIP]
>  Diğer türleri oluşturma aynı şekilde arabirimleri oluşturabilirsiniz. Arabirimi var, ancak sınıf diyagramı üzerinde görünmesini değil, sonra ilk görüntüleyin. Daha fazla bilgi için [nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma](../ide/how-to-create-types-by-using-class-designer.md) ve [nasıl yapılır: Varolan türleri görüntüleme (Sınıf Tasarımcısı)](../ide/how-to-view-existing-types-class-designer.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Devralım çizgisi çizerek bir arabirim uygulamak için  
  
1. Sınıf diyagramında, arabirimi ve arabirimini uygulayan sınıf görüntüler.  
  
2. Devralım çizgisi, sınıf ve arabirim çizin.  
  
    Lolipop sınıfa iliştirilen görünür ve devralma ilişkisi arabirim adını içeren bir etiket tanımlar. Visual Studio tüm arabirim üyeleri için saplamalar oluşturur.  
  
   Daha fazla bilgi için [nasıl yapılır: devralma arasında türleri oluşturmak (Sınıf Tasarımcısı)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>Sınıf Görünümü penceresinden bir arabirim uygulamak için  
  
1.  Sınıf diyagramı üzerinde arabirim uygulamak istediğiniz sınıf görüntüler.  
  
2.  Sınıf Görünümü açın ve arabirimi bulun.  
  
    > [!TIP]
    >  Sınıf Görünümü açık değilse, sınıf görünümünden açın **görünümü** menüsü. Sınıf Görünümü hakkında daha fazla bilgi için bkz: [Viewing Classes and Their Members](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Arabirim düğümü diyagramında sınıf şekline sürükleyin.  
  
     Lolipop sınıfa iliştirilen görünür ve devralma ilişkisi arabirim adını içeren bir etiket tanımlar. Visual Studio tüm arabirim üyeleri için saplamalar oluşturur; Bu noktada, arabirim uygulanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma](../ide/how-to-create-types-by-using-class-designer.md)   
 [Nasıl yapılır: Varolan türleri görüntüleme (Sınıf Tasarımcısı)](../ide/how-to-view-existing-types-class-designer.md)   
 [Nasıl yapılır: (Sınıf Tasarımcısı) türler arasında devralma oluşturma](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Sınıfları ve Türleri Yeniden Düzenleme (Sınıf Tasarımcısı)](../ide/refactoring-classes-and-types-class-designer.md)



