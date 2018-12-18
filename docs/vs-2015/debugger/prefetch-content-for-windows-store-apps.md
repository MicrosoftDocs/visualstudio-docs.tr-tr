---
title: Windows Store uygulamaları için içeriği önceden getirme | Microsoft Docs
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
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ad7c09e163833c295be45a7ee81e2e0587fa6b2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797409"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Windows Mağazası uygulamaları için önceden getirilmiş içerikler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca Windows için geçerlidir] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Windows Store uygulamanızı daha iyi yanıt vermesi için web sayfalarını veya resimleri, gibi bazı web içeriği uygulamanın önceden yüklemek için Windows isteyebilir [WinINet](http://msdn.microsoft.com/en-us/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)önbellek. Önceden getiriliyor bu işlev çağrılır. Başlatmada kullanılan içerik için özellikle etkili ancak çok sık kullanılan diğer içeriklere hazırlık. Yöntemlerinin [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) sınıfı dağıtılacak istediğiniz içeriğin bir URI'leri belirtmenize olanak tanır. Bkz. Windows SDK'sı [içeriği önceden getirme örnek](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) uygulamanıza ContentPrefetcher işlevselliği ekleme örnekleri için.  
  
 Windows zaman ve önceden getiriliyor gerçekleşmesi gerektiğini belirlemek için buluşsal yöntemler ve hangi kaynakların indirilecek kullanır. Buluşsal yöntemler, hesap sistem ağ ve güç koşulları, kullanıcı uygulama kullanım geçmişi ve önceki önceden getirme girişimleri sonuçlarını alın. Visual Studio'da kullanabileceğiniz **tetikleyici Windows Store uygulaması hazırlık** ContentPrefetcher buluşsal yöntemler yoksaymak ve tüm belirtilen web içeriğin önceden yüklenmesi için Windows zorlamak için komutu. Bu, uygulamanın davranışı veya içeriği (yüklenen veya yüklü değil) bilinen bir durumda önceden getirme ile performansı test etmek istiyorsanız yararlı olabilir.  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>ContentPrefetcher önceden yüklenmesini zorlamak için kaynakları belirtilen  
 Bu yordam, zaten ContentPrefetcher işlevselliği ayarlayın ve içerik bir URI'leri uygulaması projenizde önceden yükleme için belirtilen olduğunu varsayar. Belirtilen kaynaklar yeni veya değiştirilmiş bir içeriği önceden yüklenmesini zorlamak için seçtiğiniz önce uygulamayı durdurmak ve başlatmak sahip **tetikleyici Windows Store uygulaması hazırlık** komutu. Önce bir URI'leri kaydetmek için uygulamayı çalıştırın. **Tetikle Windows Store App** komutu sonra içerik indirmek ve önbelleğine eklemek için ContentPrefetcher zorlar. Uygulamayı sonraki çalıştırmalarında içeriği önceden yüklenmiş olduğunu varsayabilirsiniz.  
  
1. Önceden getirme içerik URI'leri uygulamayı kaydetmek için uygulamayı başlatın. Üzerinde **hata ayıklama** menüsünde seçin **hata ayıklamayı Başlat** (klavye kısayolu: F5).  
  
2. Üzerinde **hata ayıklama** menüsünde seçin **hata ayıklamayı Durdur** (klavye kısayolu: Shift + F5).  
  
3. Üzerinde **hata ayıklama** menüsünde seçin **diğer hata ayıklama hedefleri** seçip **tetikleyici Windows Store uygulaması hazırlık**.  
  
   Artık, hata ayıklama, test veya önceden getirilmiş web kaynakları uygulamanızla analiz edin.  
  
> [!NOTE]
>  Belirtilen web içerik eklediğinizde veya zaman bu adımları yineleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Blog gönderisi: önceden getirme Windows Store uygulamaları için Visual Studio 2013 güncelleştirme 2'de tetikleme](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)



