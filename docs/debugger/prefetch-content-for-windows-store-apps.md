---
title: UWP uygulamalarında önceden getirilmiş içeriğin kullanarak hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 72c4b305152694e8d3664b54aef3477d2f8b1fec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854593"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>UWP uygulamalarında önceden getirilmiş içeriğin Visual Studio kullanarak hata ayıklama
  
 UWP uygulamanızın daha iyi yanıt vermesi için web sayfalarını veya resimleri, gibi bazı web içeriği uygulamanın önceden yüklemek için Windows isteyebilir [WinINet](/windows/desktop/WinInet/about-wininet) önbellek. Önceden getiriliyor bu işlev çağrılır. Başlatmada kullanılan içerik için özellikle etkili ancak çok sık kullanılan diğer içeriklere hazırlık. Yöntemlerinin [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) sınıfı dağıtılacak istediğiniz içeriğin bir URI'leri belirtmenize olanak tanır. Bkz. Windows SDK'sı [içeriği önceden getirme örnek](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) uygulamanıza ContentPrefetcher işlevselliği ekleme örnekleri için.  
  
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
 [Blog gönderisi: önceden getirme Windows Store uygulamaları için Visual Studio 2013 güncelleştirme 2'de tetikleme](https://blogs.msdn.microsoft.com/devops/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)