---
title: Visual Studio hata ayıklayıcısı sözlüğü | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d1b837bc468d3d0c848827e709f8329d91a7ffe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869450"
---
# <a name="visual-studio-debugger-glossary"></a>Visual Studio Hata Ayıklayıcısı Sözlüğü
İçinde kullanılan terimleri şunlardır [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklama SDK'sı.  
  
## <a name="terms"></a>Koşulları  
 ilişkili bir kesme noktası  
 Bir kesme noktası için bir soyutlamayı, kod içinde ayarlayabilirsiniz. İlişkili bir kesme noktası ve bir kesme noktası yönerge kodu stream'de arasında bire bir ilişki yoktur. Bellekten kod, bağlı kesme noktaları arasındaki bağlamayı.  
  
 nedensellik ilişkilerini  
 Birden çok fiziksel iş parçacıkları, işlemler ve makine mantıksal bir yürütme iş parçacığı izlemek ve bu iş parçacığının etkin kalma süresi söz konusu mantıksal iş parçacığının herhangi bir anda çağrı yığınını yeniden olanağı sağlar.  
  
 Kod bağlamı  
 Bir konumdaki kodda hata ayıklama altyapısı tarafından tanınan bir Özet sağlar. Çalışma zamanı mimarileri için kod bağlamı bir programın yönerge stream'de bir adrestir. Hangi kod yönergeleri ile gösterilebilir değil nontraditional diller için kod bağlamı başka yollarla temsil edilebilir.  
  
 kod yolu  
 Burada bir dalın alınması veya bir işlev çağrısı yapılan kod yürütme bir noktayı temsil eder. Bir yığın izlemesi temelde işlevi çağrısı kod yolları bir listesidir.  
  
 hata ayıklama altyapısı (DE)  
 Bir bileşen, hata ayıklama çalışma zamanı mimarisini sağlar. Hata ayıklama altyapısı yorumlayıcı veya işletim sistemi ile birlikte çalışır ve yürütme denetimi, kesme noktaları ve ifade değerlendirme gibi hata ayıklama hizmetleri sağlar.  
  
 Belge bağlamı  
 Hata ayıklama altyapısı tarafından tanınan bir kaynak dosyası belgedeki bir konumdaki bir Özet sağlar. Çoğu dil için bir belge bağlamına kaynak dosyada bir konumdur. Kaynak dosyasını bir metin olmayabilir nontraditional diller için bir belge bağlamı başka bir yolla tarafından temsil edilebilir. Ayrıca bkz: *belge konumu*.  
  
 Belge konumu  
 Bir konumdaki IDE'ye bilinen kaynak dosyada bir Özet sağlar. Çoğu dil için belge konumunu kaynak dosyada bir konumdur. Nontraditional diller için belge konumunu başka şekillerde temsil edilebilir. Ayrıca bkz: *belge bağlamına*.  
  
 hata kesme noktası  
 Bir bekleyen kesme noktasının hata tanımlamak için bir Özet. Bir hata kesme noktası bekleyen kesme noktasının veya bekleyen kesme noktasının bağlamanın dışında bir kod konuma engelleyen diğer bilgilerle ilişkili ifade bekleyen kesme noktasının konumunu hata açıklayabilir.  
  
 Değerlendirme bağlamı  
 İfade değerlendirme için programlama bir bağlamın bir Özet sağlar. Genellikle, bir değerlendirme bağlamı bir kapsamıdır. Bir ifadenin bağlamında ifade değerlendirme yaparken oluşturma noktasında eşleşen kapsam kuralları ifade bağlamı sağlar. Örneğin, bir yığın çerçevesinde oluşturulan bir ifade bağlamı, yerel değişkenler, yöntem parametreleri, sınıf üyeleri (varsa) ve genel değişkenler değerlendirmesi için bağlamı sağlayacaktır.  
  
 ele geçirilen özel durum  
 Geçerli yığın çerçevesi bir yerde özel durum işleme mekanizmasını olsa bile, bir hata ayıklama altyapısı tarafından ele geçirilse bir özel durum.  
  
 JustMyCode  
 Yalnızca bir kullanıcıya ait kodu hata ayıklama ve sistem kodu gibi tüm ara kod yoksayılıyor kavramı — kaynak kodu, sistem kodunu kullanılabilir olsa bile.  
  
 bekleyen kesme noktası  
 Önce sırasında ve sonrasında kesme noktaları için bir Özet sağlar kodudur yüklenir ve kesme noktaları sanallaştırmak için yol. Bir bekleyen kesme noktası:  
  
- Bir veya daha fazla program kodunda bir kesme noktası bağlamak için gerekli tüm bilgileri içerir.  
  
- Bir veya daha fazla program içinde birden çok kod konumlara bağlayabilirsiniz.  
  
- Hiçbir zaman kendisi koduna bağlar.  
  
  Her zaman kod yükler, bir programdaki tüm bekleyen kesme noktalarını bunlar bağlayabilirsiniz olmadığını görmek için denetlenir. Bir bekleyen kesme noktasının, bağlanan tüm bağımlı kesme noktalarını içerecek şekilde bildirilir.  
  
  process  
  Fiziksel bir Win32 işlemi. Bir işlem birden çok programları içerebilir. Ayrıca bkz: *program*.  
  
  program  
  Belirli bir çalışma zamanı mimarisi içinde çalışan tek bir ad. Ayrıca bkz: *işlem*.  
  
  oturum hata ayıklama Yöneticisi (SDM)  
  Herhangi bir sayıda herhangi bir sayıda makine üzerinde birden çok işlem programlarında hata ayıklama hata ayıklama altyapısı herhangi bir sayıda yönetir. Temel düzeyde, SDM çoğaltıcı hata ayıklama altyapısını ' dir. Ayrıca, SDM IDE hata ayıklama oturumu birleşik bir görünümünü sağlar.  
  
  yığın çerçevesi  
  Belirli bir çerçeve olan hesaplamayı durumunu ve iç içe geçmiş işlev çağrıları belirli düzeyini temsil eder.  
  
  thread  
  En az bir programda yığın tabanlı yönerge yürütme genelleştirilmiş kavramı.  
  
  Uyarı kesme noktası  
  Bir bekleyen kesme noktasının bir uyarı tanımlamak için bir Özet. Bir uyarı kesme noktası neden bekleyen kesme noktası henüz bir kod konuma bağlı olmayan bir nedeni açıklanmaktadır. Bu kodun henüz bekleyen kesme noktasının tarafından açıklanan konumu veya başka bir nedenle yüklememiş emin olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)