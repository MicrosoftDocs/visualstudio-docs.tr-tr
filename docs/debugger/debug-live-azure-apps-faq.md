---
title: Anlık görüntü hata ayıklama ile ilgili SSS | Microsoft Docs
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13b35746a7b0d639d4c954c8ef1a5221973e1abc
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154352"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Sık sorulan Visual Studio'da anlık görüntü hatalarını ayıklama sorular

Snapshot Debugger'ı kullanarak canlı Azure uygulamalarında hata ayıklaması yaparken sorulan sorular listesi aşağıda verilmiştir.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Bir anlık görüntü alma performans maliyeti nedir?

Snapshot Debugger, uygulamanızın bir anlık görüntüsünü yakalar, uygulamanın işlem Çatal ve çatalı oluşturulan kopya askıya alınıyor. Anlık görüntü hata ayıklaması yaparken, işlem çatalı kopyasını karşı hata ayıklama. Bu işlem yalnızca 10-20 milisaniye ancak tam bir yığın Uygulamanın kopyalamaz. Bunun yerine, yalnızca sayfa tablosu kopyalar ve sayfalarını yazma kopyalamak için ayarlar. Uygulamanızın nesnelerin yığın değişiklik bazıları varsa, bunların ilgili sayfalarını ardından kopyalanır. Her anlık görüntü, bu nedenle (bazında çoğu uygulama için kilobayt yüzlerce) küçük bir bellek içi maliyeti vardır. 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Ölçeği genişletilen Azure App Service (Uygulamam birden çok örneğini) varsa ne olur?

Anlık görüntü noktaları her tek örnekli uygulandığından, uygulamanızın birden çok örneğe sahip olduğunda. Belirtilen koşulları ile İsabet yalnızca ilk anlık görüntü noktası anlık görüntüsünü oluşturur. Birden çok anlık görüntü noktaları varsa, sonraki anlık görüntüleri oluşturulan ilk anlık görüntüyle aynı örnekten gelir. Uygulama günlükleri için gönderilen günlüğe kaydetme noktaları her örneğinden iletileri gönderirken çıkış penceresine gönderilen günlüğe kaydetme noktaları yalnızca bir örneği, gelen iletileri gösterir. 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Nasıl Snapshot Debugger sembolleri?

Snapshot Debugger, Azure App Service için yerel veya dağıtılmış uygulama için eşleştirme sembolleri sahip olmasını gerektirir. (Katıştırılmış pdb şu anda desteklenmemektedir.) Snapshot Debugger, Azure uygulama hizmetiniz semboller otomatik olarak indirir. Visual Studio 2017'den itibaren aynı zamanda Azure App Service'e dağıtma sürüm 15.2, uygulamanızın sembolleri dağıtır.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Snapshot Debugger, sürüm derlemeleri uygulamamın karşı çalışır mı?

Evet - Snapshot Debugger, sürüm derlemeleri karşı çalışmaya yöneliktir. Bir anlık görüntü noktası bir işlevde yerleştirildiğinde, işlev hata ayıklanabilir yapmak geri bir hata ayıklama sürümünü için derlenmiştir. Snapshot Debugger durdurduğunuzda, İşlevler için yayın derlemesi döndürülür. 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Günlüğe kaydetme noktaları üretim uygulamamda yan etkilere neden olabilir?

Hayır - uygulamanıza eklediğiniz herhangi bir günlük iletisi hemen değerlendirilir. Bunlar, uygulamanızda yan etkileri neden olamaz. Ancak, bazı yerel özellikler günlüğe kaydetme noktası hata erişilebilir olmayabilir. 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Snapshot Debugger sunucumu yük altında ise çalışır mı?

Evet, anlık görüntü hata ayıklama sunucuları yük altında çalışabilir. Snapshot Debugger kısıtlar ve anlık görüntüleri durumlarda yakalamaz boş bellek miktarı sunucunuzdaki yetersiz olduğunda.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Snapshot Debugger'ı nasıl kaldırabilirim?

Uygulama hizmetinizde aşağıdaki adımlarla Snapshot Debugger site uzantısını kaldırabilirsiniz:

1. Uygulamanızı kapatın bulut Gezgini'nde Visual Studio ya da Azure portal aracılığıyla hizmet.
1. Uygulama hizmetinizin Kudu sitesine gidin (diğer bir deyişle, yourappservice. **SCM**. azurewebsites.net) gidin **Site uzantıları**.
1. Snapshot Debugger site uzantısını kaldırmak için X tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio’da hata ayıklama](../debugger/index.md)  
[Snapshot Debugger'ı kullanarak canlı ASP.NET uygulamalarının hatalarını ayıklama](../debugger/debug-live-azure-applications.md)  
[Anlık görüntü hata ayıklama için sorun giderme ve bilinen sorunlar](../debugger/debug-live-azure-apps-troubleshooting.md)
