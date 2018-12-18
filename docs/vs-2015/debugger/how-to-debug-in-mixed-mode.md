---
title: 'Nasıl yapılır: karışık modda hata ayıklama | Microsoft Docs'
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
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ee85e5822d4792046c755c85d699dd6a9a5d26
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737156"
---
# <a name="how-to-debug-in-mixed-mode"></a>Nasıl Yapılır: Karışık Modda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki yordamlarda, karma mod hata ayıklama olarak da bilinir, hem yönetilen hem de yerel kod hatalarını ayıklamak açıklanır. Olup DLL ya da uygulama yerel kod halinde yazılmış bağlı olarak bunu yapmak için iki senaryo vardır:  
  
-   DLL'nizi çağıran arama uygulaması yerel kodda yazılır. Bu durumda, DLL yönetilir ve hem yönetilen hem de yerel hata ayıklayıcıları hem de hata ayıklamak için etkinleştirilmesi gerekir. Bu iade  **\<Proje > özellik sayfaları** iletişim kutusu. Bunu nasıl yapacağınız mı DLL projesi veya çağıran uygulama projesinden hata ayıklamaya başladığınızda üzerinde bağlıdır.  
  
-   DLL'nizi çağıran arama uygulaması yönetilen kodda yazılır ve DLL dosyanızı yerel kodda yazılır.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Karışık mod hata ayıklamayı etkinleştirmek için  
  
1.  İçinde **Çözüm Gezgini**, projeyi seçin.  
  
2.  Üzerinde **görünümü** menüsünü tıklatın **özellik sayfaları**.  
  
3.  İçinde  **\<Proje > özellik sayfaları** iletişim kutusunda **yapılandırma özellikleri** düğümüne tıklayın ve ardından **hata ayıklama**.  
  
4.  Ayarlama **hata ayıklayıcı türü** için **karma** veya **otomatik**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: DLL Projesinde Hata Ayıklama](../debugger/how-to-debug-from-a-dll-project.md)



