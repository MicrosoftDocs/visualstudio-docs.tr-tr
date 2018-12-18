---
title: Unity için Visual Studio araçlarına genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: f403a1001cb32376b91da472acdebaa31cc91682
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744250"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçlarına Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu bölümde daha özellikleri Visual Studio Araçları Unity teklifler ve Unity ile daha üretken olmak için bunları nasıl kullanabileceğinizi öğreneceksiniz.  
  
 Unity için Visual Studio Araçları ile (*VSTU*), oyun ve düzenleyici betikleri C# dilinde yazın ve ardından, güçlü bir hata ayıklayıcı hataları bulma ve düzeltme için Visual Studio'yu kullanabilirsiniz. Sözdizimi renklendirme Unity'nın ShaderLab gölgelendirici dili ve daha iyi hata ayıklayıcı Görselleştirmelerini MonoBehavior Sihirbazı için geliştirilmiş kod oluşturma için VSTU en son sürümünü içerir. VSTU, Unity proje dosyalarınızı, konsol iletileri ve daha az zaman için ve Unity Düzenleyicisi'nden kod yazarken geçiş ayırmasına oyununuzu Visual Studio'ya başlatma özelliğini de getirir.  
  
 Bu özellikler hakkında daha fazla bilgi için okumaya devam edin.  
  
## <a name="integration-with-unity"></a>Unity ile tümleştirme  
 Unity için visual Studio Araçları ve geriye her zaman Visual Studio ve Unity Düzenleyicisi arasında geçiş yapmak zorunda üretkenlik Geliştirici olmaz mıydı. İşte bu Unity için Visual Studio Araçları Visual Studio'dan ayrılmanıza gerek kalmadan iş yapmaya devam kolaylaştırır.  
  
-   **Unity Proje Gezgini** tüm Unity projenizi Visual Studio'da Unity Düzenleyicisi'nde görüntülenen aynı hiyerarşiyi kullanarak görüntüler.  
  
-   Unity Konsolu Tümleştirmesi Hata penceresi Visual Studio'nun içinde Unity konsolundan çıkış görüntüler.  
  
-   Visual Studio – geri Unity için F5 tuşuna basarak geçiş gerek oyununuzu hatalarını ayıklamaya başlayın.  
  
## <a name="superior-debugging"></a>Üst düzey hata ayıklama  
 Unity oyununuzu C# betik ve DLL'leri, tek başına çalışıp çalışmadığını veya Unity Editor'daki hata ayıklamak için Visual Studio'nun güçlü hata ayıklayıcı bağlanın. Visual Studio'dan beklediğiniz tüm hata ayıklama özelliklerini kullanabilirsiniz.  
  
- Kesme, koşullu kesme noktaları da dahil olmak üzere.  
  
- İzleme penceresinde karmaşık ifadeleri takip edin.  
  
- Değişkenleri ve bağımsız değişkenleri inceleyin ve değerlerini değiştirin.  
  
- Karmaşık nesnelerde ve veri yapılarında detaya gidin.  
  
  Unity oyununuzu, ağınızdaki başka bir makinede çalışırken bile ayıklayabilirsiniz.  
  
## <a name="productivity"></a>Üretkenlik  
 Yazma ve C# kodu yeniden düzenleme için Visual Studio'nun kurulu üretkenlik ek olarak, Unity için Visual Studio Araçları, Unity geliştiricileri için fazladan üretkenlik özellikleri sağlar.  
  
-   Sözdizimi renklendirme Unity'nın ShaderLab dil için hataları haline gelmeden önce hataları, gölgelendiriciler içinde nokta yardımcı olur. Yalnızca ShaderLab dosyalarınızı Visual Studio'da açın.  
  
-   MonoBehavior sihirbaz Unity davranışları listesini göz atmanızı sağlar ve davranışları hakkında bilginiz olmayabilir için ortak kod oluşturur. CTRL + SHIFT + M tuşlarına basın.  
  
-   En sık kullandığınız Unity davranışlarıyla ilgili bilgi sahibi olduğunuzda hızlı MonoBehavior sihirbaz bunları larına koyar. CTRL + ALT + Q tuşlarına basın.  
  
-   Visual Studio'da Unity belgelere erişebilir. Yalnızca API çağrısı hakkında bilgi edinin ve ardından CTRL + ALT + M, CTRL + H tuşuna istediğiniz vurgulayın.  
  
-   Bu özelliklerin tümünü ve daha fazla klavye kısayolları ile erişin.  
  
## <a name="visual-studio-tools-for-unity-api"></a>Unity API için Visual Studio Araçları  
 Özelleştirme ve sağlanan API'leri kullanarak Unity için Visual Studio Araçları davranışını genişletme.  
  
-   Unity için visual Studio Araçları, Visual Studio için Unity konsolundan akışını sağlamak için günlük geri çağırma kaydeder. Günlük bilgileri Düzenleyicisi betikleriniz varsa, Visual Studio için ileti göndermek için aynı geri çağırma içine takabilirsiniz. Daha fazla bilgi için günlük geri örneğe bakın.  
  
-   Unity stili geri ProjectFileGeneration kullanarak Unity için Visual Studio Araçları proje dosyalarını nasıl oluşturur değiştirebilirsiniz. Daha fazla bilgi için proje dosyası oluşturma örneğe bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Unity giriş sayfası](http://unity3d.com)

