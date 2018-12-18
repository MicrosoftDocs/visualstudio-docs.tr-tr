---
title: Web denetim kitaplığı (yönetilen kod için) | Microsoft Docs
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
- debugging DLLs
- debugging [Visual Studio], Web control libraries
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a523d593b4c61a7ca730cc60a6ed22a1be541f9c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807601"
---
# <a name="web-control-library-managed-code"></a>Web Kontrol Kitaplığı (Yönetilen Kod)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Web Denetim Kitaplığı proje şablonu, bir DLL oluşturur. Sınıf kitaplığının DLL olduğundan, doğrudan çalıştıramazsınız. Oluşturmalısınız bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] denetim katıştırır sayfası. Daha fazla bilgi için [Web denetim kitaplığı şablonu](http://msdn.microsoft.com/en-us/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Bir Web denetim kitaplığı (yöntemi 1) hata ayıklamak için  
  
1.  Varolan Web Denetim Kitaplığı projesini açın veya yeni bir tane oluşturun.  
  
2.  Oluşturma bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] denetim katıştırır sayfası.  
  
3.  Barındıran Web sitesinde [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] adlı bir alt dizin oluşturma, test bandı `/Code`.  
  
4.  Kaynak kodu denetimine kopyalayın `/Code` alt.  
  
5.  Kaynak kodunda açın `/Code` alt ve kesme noktaları ayarlayın.  
  
6.  Test bandı için işaret eden bir URL ile bir tarayıcı penceresi açın. Denetiminde bir kesme noktası isabet edilir ve hata ayıklamaya başlayabilirsiniz.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Bir Web denetim kitaplığı (yöntem 2) hata ayıklamak için  
  
1.  Konak uygulama projesini ve Web denetimi projenin aynı çözüm içinde oluşturun.  
  
2.  İçinde **Çözüm Gezgini**, konak uygulamaya sağ tıklayın ve seçin **Başvuru Ekle**.  
  
3.  Web denetim projesine bir başvuru ekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET Web Uygulamaları](../debugger/debugging-preparation-aspnet-web-applications.md)



