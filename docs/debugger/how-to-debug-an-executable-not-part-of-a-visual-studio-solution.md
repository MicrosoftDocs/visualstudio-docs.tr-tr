---
title: Visual Studio çözümünün parçası olmayan bir uygulamanın hatalarını ayıklamak
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8c408ca42f82c0419c6570068e2a83e97f2371e9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066619"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Visual Studio çözümünün parçası olmayan bir uygulamanın hatalarını ayıklamak (C++, C#, Visual Basic F#)

Uygulama hata ayıklaması yapmak isteyebilirniz (*.exe* dosyası), Visual Studio çözümünün parçası değildir. Visual Studio dışında bir uygulama veya bir başkasının oluşturmuş olabilir veya uygulamayı başka bir yerde öğesinden alındı. 

Visual Studio dışında uygulamayı başlatın ve sonra onu kullanarak eklemek için Visual Studio'da mevcut olmayan bir uygulamanın hatalarını ayıklamak için alıştığınız olduğu **iliştirme** Visual Studio hata ayıklayıcısı. Daha fazla bilgi için [çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Bir uygulamaya ekleme, birkaç saniye sürebilir el ile yapılacak adımlar gerektirir. Bu gecikme nedeniyle ekleme bir başlatma sorunu hataları ayıklamanıza yardımcı olmaz veya kullanıcı için beklemez bir uygulama girin ve hızlı şekilde biten. 

Bu durumda, uygulama için bir Visual Studio EXE projesi oluşturabilir, veya varolan içine alma C#, Visual Basic veya C++ çözüm. Programlama dillerinin tümü EXE projelerini desteklemez. 

>[!IMPORTANT]
>Uygulamaya ekleme ya da Visual Studio çözüme ekleme Visual Studio'da tasarlanmadı bir uygulama için hata ayıklama özellikleri sınırlıdır. 
>
>Kaynak kodu varsa, en iyi yaklaşım bir Visual Studio projesine kod aktarmaktır. Ardından, uygulamayı hata ayıklama yapısını çalıştırın.
>
>Kaynak kodu yoksa ve uygulama yok [hata ayıklama bilgileri](../debugger/how-to-set-debug-and-release-configurations.md) kullanılabilir hata ayıklama özellikleri uyumlu bir biçimde çok az. 

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Var olan bir uygulama için yeni bir EXE projesi oluşturmak için  
   
1. Visual Studio'da **dosya** > **açık** > **proje**.  
   
1. İçinde **Proje Aç** iletişim kutusunda **tüm proje dosyaları**, açılır menüde yanındaki seçili değilse **dosya adı**.  
   
1. Gidin *.exe* dosya, onu seçip **açık**.  
   
   Dosya, yeni, geçici bir Visual Studio çözümü içinde görünür.

1. Uygulamayı hata ayıklama gibi bir yürütme komutu seçerek Başlat **hata ayıklamayı Başlat**, gelen **hata ayıklama** menüsü.    
  
### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Bir uygulama var olan bir Visual Studio çözümüne aktarmak için  
  
1.  Bir C++ ile C#, veya Visual Basic çözümünü Visual Studio'da Aç seçin **dosya** > **Ekle** > **mevcut proje**.  
  
1. İçinde **Proje Aç** iletişim kutusunda **tüm proje dosyaları**, açılır menüde yanındaki seçili değilse **dosya adı**.  
   
1. Gidin *.exe* dosya, onu seçip **açık**.  
   
   Dosya, geçerli çözüm altında yeni bir proje olarak görüntülenir.  
   
1. Yeni dosya seçildi uygulama hata ayıklama gibi bir yürütme komutu seçerek Başlat **hata ayıklamayı Başlat**, gelen **hata ayıklama** menüsü.    
  
### <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [DBG dosyaları](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))