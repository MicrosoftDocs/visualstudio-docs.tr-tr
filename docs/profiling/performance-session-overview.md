---
title: Performans oturumuna genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a385b425ee8dead7df0faad302e6cf270b739034
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828539"
---
# <a name="performance-session-overview"></a>Performans oturumuna genel bakış
Bu genel bakışta profil oluşturma hakkındaki temel bilgileri açıklar. Performans çalışmaya yeni başladığınız geliştiriciler görürsünüz nasıl [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma araçları bunları hızlı bir şekilde üretken ve kodlarını performansını artırmaya yardımcı olabilir. Profil oluşturma deneyimli geliştiriciler, belirli bir profil oluşturma araçları özellikleri ve süreçleri hakkında genel bir bakış elde edebilirsiniz.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil oluşturma araçları, kaynak kodundaki performans sorunlarını belirleyin ve olası çözümleri performansını karşılaştırın yardımcı olur. Profil oluşturma araçları sihirbazları yanı sıra varsayılan ayarları, birçok performans sorununu anında Öngörüler verebilirsiniz. Profil oluşturma araçları, Seçenekler ve özellikler, profil oluşturma işlemi üzerinde tam denetim sağlar. Bu denetim, kod bölümleri, blok düzeyinde zamanlama bilgileri koleksiyonunu ve verilerinizdeki ek işlemci ve sistem performans verilerinin eklenmesi kesin hedefleme içerir.  
  
 Profil oluşturma araçları kullanmanın temel işlemini aşağıdakileri yapın:  
  
1. Performans oturumu koleksiyonu yöntemi ve toplamak istediğiniz verileri belirleyerek yapılandırın.  
  
2. Performans oturumu uygulamayı çalıştırarak profil oluşturma verilerini toplayın.  
  
3. Performans sorunu tanımlamak için verileri analiz edin.  
  
4. Kodda değişiklik [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE) için kod uygulama performansını artırır  
  
5. Değiştirilen kod profil oluşturma verilerini toplamak ve profil oluşturma verileri özgün ve değiştirilen verilerin karşılaştırabilirsiniz.  
  
6. Performansı artırma belgeleri bir rapor oluşturuyorsunuz.  
  
   Profil oluşturma tarafından sağlanan bilgileri çalışmak için Sembol bilgilerini profil oluşturmak istediğiniz ikili dosyaların ve Windows işletim sistemi ikili dosyaları için kullanılabilir olmalıdır.  
  
## <a name="configure-the-performance-session"></a>Performans oturumu yapılandırma  
 Profil oluşturma oturumunu yapılandırmak için kullanmak istediğiniz profil yöntemi ve toplamak istediğiniz verileri seçin. Profil oluşturma araçları **performans Sihirbazı** aracılığıyla temel yapılandırması için rehberlik sağlayabilir ve daha fazla seçenek eklemek için performans oturumu özellik sayfalarını kullanabilirsiniz:  
  
- Örnekleme, izleme ve bellek ayırma profil oluşturma yöntemleri içerir.  
  
- Veri değerleri, saat, işlemci ve işletim sistemi performans sayaçları ve sayfa hataları ve çekirdek geçişleri gibi uygulama olayları içerir.  
  
  Bir performans oturumu yapılandırabileceğiniz bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proje proje çözümün bir parçası veya rasgele ikili dosyaları aracılığıyla profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Performans oturumu özellik sayfaları'nda oturum özellikleri belirtebilirsiniz veya profil oluşturma Sihirbazı'nı kullanabilirsiniz.  
  
## <a name="collect-profiling-data"></a>Profil oluşturma verilerini topla  
 Profil oluşturma verileri toplamayı Başlat **performans Gezgini**. Duraklatma ve topladığınız veri miktarını sınırlamak için profil oluşturmayı sürdürün. Ayrıca, zaten çalışan bir işleme ekleyebilirsiniz.  
  
 Uygulama başlatıldıktan hemen sonra **veri koleksiyonu denetimi** penceresi görünür [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Gelen **veri koleksiyonu denetimi** penceresinde, profil uygulamanızın belirli bölümlerini duraklatma ve toplama işlemi sürdürülüyor. Ayrıca **veri koleksiyonu denetimi** toplanan verileri işaretleri eklemek için penceresi. İşaretleri, profili görünümlerde görüntülenmesi ve profil oluşturma verilerini filtrelemek için kullanılabilir kullanıcı tanımlı veri noktalarıdır.  
  
 Hedef uygulama kapatıldığında, profil oluşturma araçları profil oluşturma veri dosyası (*.vsp) oluşturur ve Özet rapor görünümü'nde görüntüler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.  
  
## <a name="analyze-the-data-and-identify-performance-issues"></a>Verileri analiz etmek ve performans sorunlarını belirleme  
 Bir profil oluşturma sonlandırdığınızda, veriler, analiz ve özeti profil oluşturma araçlarında görüntülenen **performans raporu** windows görüntüleyin. Profil oluşturma verilerini çağrı yığını ve hedef uygulamanın tekil işlevler için toplanır. Görünümleri görüntüler işlemler, iş parçacıkları, modüller, İşlevler ve uygulamanın kaynak kodu satırlarını veri aralıkları için performans analizi raporu. Profil oluşturma verilerini bir işlev için değerler aşağıdakileri içerir:  
  
- İşlev ve (değerler dahil) işlev tarafından çağrılan alt işlevler harcanan toplam süreyi.  
  
- İşleve (özel değerler) yalnızca kod yürütülürken harcanan süre.  
  
  Üzerinde on iki farklı görünümleri en verimli şekilde profil oluşturma verilerini analiz etmek etkinleştirin. Görünüm özelleştirmeleri, filtreleme ve sıralama performans sorunlarına neden olan işlevler bulmak için veri sağlar. Sıcak yol filtreleme, çağrı ağacında ve modül görünümlerde en etkin yol hemen vurgulama sağlar.  
  
## <a name="modify-the-application-code"></a>Uygulama kodu değiştirin  
 Bir veya daha fazla ilgili performans sorunlarını yalıtıncaya sonra kullanarak kodu değiştirebilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE ve ardından değişikliklerinizi için profil oluşturma verilerini.  
  
## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Yeniden profil oluşturma verilerini toplamak ve profil oluşturma çalıştırmaları arasında verileri karşılaştırın  
 Profil oluşturma araçları karşılaştırma rapor görünümü modülü, işlev veya satır performans iki seçili profil oluşturma veri dosyaları arasındaki farkı görüntüler. Karşılaştırmak istediğiniz ve tek tek dosyaları görünümleri ve karşılaştırma görünümü arasında geçiş yapabilirsiniz profil oluşturma veri değerlerini belirtebilirsiniz.  
  
## <a name="generate-a-report-of-the-results"></a>Sonuçların bir rapor oluşturma  
 E-postalar ve elektronik tablolar halinde herhangi bir performans raporu görünüm satırlarını yapıştırın ve bir veya daha fazla görünüm verilerini içeren raporlar oluşturabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Genel bakış](../profiling/overviews-performance-tools.md)   
 [İzlenecek yol: Performans sorunlarını tanımlama](../profiling/walkthrough-identifying-performance-problems.md)