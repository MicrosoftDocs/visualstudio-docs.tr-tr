---
title: COM sunucusunda ve kapsayıcısında hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a495b90f68d0a12d9fb34babf28aca073580f2aa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788010"
---
# <a name="com-server-and-container-debugging"></a>COM Sunucusunda ve Kapsayıcısında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

COM uygulamaları programcının doğrudan denetimi dışında görevleri gerçekleştirin. DLL'ler arasındaki iletişim, kullanım nesneler üzerinde sayar ve beklenmeyen davranışlara burada karşılaşabileceğiniz alanları birkaçı Pano işlemlerdir. Bu durumda, ilk adımınız sorunun kaynağını izlemektir.  
  
 Visual Studio hata ayıklayıcı üzerinden ve kapsayıcılar ve sunucular içine Adımlama destekler. Bu uzaktan yordam çağrısı (RPC) adım yeteneğini içerir.  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> Aynı çözümdeki bir COM sunucusu ve hata ayıklama  
 COM sunucusunda ve aynı çözüm içinde iki proje kullanarak kapsayıcı ayıklayabilirsiniz. Her bir proje ve hata ayıklama uygun kesme noktaları ayarlayın. Kapsayıcı içine bir kesme noktasına denk gelir sunucunun bir çağrı yaptığında, kapsayıcı (diğer bir deyişle, hata ayıklama bitene kadar), sunucu kodu dönene kadar bekler.  
  
 Bir COM kapsayıcısında hata ayıklama standart bir programın hatalarının ayıklanmasına benzer. Olaya (örneğin, veri üzerinde kapsayıcı uygulaması sürükleyerek), bir geri çağırma oluşturur hata ayıklaması yaparken bir farktır. Bu durumda, bir kesme noktası içindeki geri arama işlevi ayarlamanız gerekir.  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Kapsayıcı bilgileri olmadan bir sunucu uygulamasında hata ayıklama  
 Sahip değil ya da kapsayıcı uygulamanızı hata ayıklama bilgilerini kullanmak istiyor musunuz, sunucu uygulamasının hata ayıklamayı başlatma işlemi üç adımdan şöyledir:  
  
1.  Sunucunun normal bir uygulama olarak hatalarını ayıklamaya başlayın.  
  
2.  Kesme noktaları, istediğiniz şekilde ayarlayın.  
  
3.  Kapsayıcı uygulamasını başlatın.  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Bir sunucu veya etki alanı yalıtımı (SDI) uygulama hata ayıklama  
 Bir SDI sunucu uygulaması hata ayıklaması yaptığınız varsa, belirtmeniz gerekir `/Embedding` veya `/Automation` içinde **komut satırı bağımsız değişkenleri** özelliğinde *proje* özellik sayfaları iletişim kutusu için C/C++, C#, veya Visual Basic projeleri.  
  
 Bu komut satırı bağımsız değişkenleri ile onu başlatan bir kapsayıcıdan artırmadığı hata ayıklayıcı sunucu uygulaması başlatabilirsiniz. Program Yöneticisi'nden veya Dosya Yöneticisi kapsayıcıyı başlangıç hata ayıklayıcıda çalışmaya server örneğini kullanmak için kapsayıcısını neden olur.  
  
 Erişim için *proje* özellik sayfaları iletişim kutusu, Çözüm Gezgini'nde projenize sağ tıklayın ve kısayol menüsünden Özellikler'i seçin. Komut satırı bağımsız değişkenleri özelliğini bulmak için yapılandırma özellikleri kategoriyi genişletmek ve hata ayıklama Sayfası'nı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM ve ActiveX Hata Ayıklaması](../debugger/com-and-activex-debugging.md)



