---
title: 'Nasıl yapılır: iş akışı hata ayıklayıcısını çağırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: acfbe34bc4a3d3c1139f8b1e821d9996fb8c712b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295743"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Nasıl yapılır: iş akışı hata ayıklayıcısını çağırma
Genellikle, diğer Visual Studio programlama dillerinde yazılan programlar yalnızca hata ayıklama gibi iş akışı hata ayıklama. İş akışı hata ayıklayıcısını aşağıdaki şekillerde başlayabilirsiniz:  
  
-   Seçin **iliştirme** üzerinde **hata ayıklama** menüsünde, iş akışı örneği için çalışan ana bilgisayar işlemi seçin. Bu yordam, yönetilen kod içinde bir ana bilgisayar işlemi ekleme olarak aynıdır.  
  
-   Tuşuna **F5** iş akışı örneği çalıştırmaya başlayın ya da bir kesme noktasına isabet sonra çalışmaya devam eder.  
  
-   Uzaktan hata ayıklamayı kullanın. Uzaktan hata ayıklama hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzaktan hata ayıklamayı etkinleştir](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  İş akışı uygulaması x86 hedefliyorsa mimarisi ve uzaktan hata ayıklama sürece çalışmaz sonra bir 64 bit işletim sistemi çalıştıran bir makinede barındırıldığı [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzak makine veya hedef iş akışı uygulaması değiştirildiğinde yüklenir **Herhangi bir CPU**.  
  
### <a name="stepping-through-code"></a>Kod boyunca ilerleme  
  
-   **Adım içinde**: kullanarak bir etkinlik adım **F11**. Hata ayıklama adımlarında içinde tanımlanan herhangi bir işleyici. Hiçbir tutucusu tanımlanmazsa, etkinliğin adım veya diğer etkinlikler içeren bileşik etkinliklerle ilk yürütme etkinliğini adım.  
  
-   **Adım çıkışı:** dışında bir etkinlik kullanıldığında adım **Shift-F11**. Bir etkinlik dışına Adımlama geçerli etkinliği ve tüm eşdüzey tamamlanana kadar etkinlikleri çalıştırır. Hata ayıklayıcı, ardından geçerli etkinliğin üst öğede keser. Bir kod işleyicisinden Adımlama, hata ayıklayıcı işleyici ilişkilendirildiği faaliyete keser.  
  
-   **Step Over**: bir etkinlik kullanıldığında üzerinden adım **F10**. Bileşik bir etkinlik Adımlama olduğunda hata ayıklayıcı birleşik etkinlik ilk yürütülebilir alt keser. Gibi bir olmayan-bileşik Adımlama olduğunda bir <xref:System.Activities.Statements.Assign> etkinliği, hata ayıklayıcı, üzerinde bir sonraki etkinliğe etkinlik ve ilişkili işleyiciler ve sonları yürütür. Ardından, çalıştırılan etkinlik son alt etkinliğin bileşik bir etkinlik ise, yürütme sonrasında hata ayıklayıcı üst etkinlik keser.  
  
### <a name="debugging-with-f5"></a>F5 tuşuna basarak hata ayıklama  
  
-   Bir iş akışı konsol uygulaması projesi oluşturuyorsanız tuşuna basmanız yeterlidir **F5** uygulama ve iş akışı hata ayıklamayı başlatmak için. Etkinlik kitaplığı, kendi oluşturuyorsanız, bir yürütülebilir ana bilgisayar uygulaması bir başlangıç projesi olarak olmalıdır. Başlangıç projesi ayarlama **Çözüm Gezgini**, ana proje adını sağ tıklatın ve seçin **başlangıç projesi olarak ayarla**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: iş akışlarında kesme noktası ayarlama](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [İş Akışı Tasarımcısı ile İş Akışlarında Hata Ayıklama](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)