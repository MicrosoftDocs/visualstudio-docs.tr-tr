---
title: Türleri görsel tasarımcıların gösterme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c19fe00713bd328574e5a05cc6f6f3a60f18ddf9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791559"
---
# <a name="exposing-types-to-visual-designers"></a>Türleri Görsel Tasarımcıların Kullanımına Sunma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sınıfı ve tür tanımlarını tasarım zamanında bir görsel tasarımcı görüntülemek için erişiminiz olmalıdır. Geçerli proje (başvurular ve bunların bağımlılıklarını) tam bağımlılık kümesini içeren derlemeler önceden tanımlanmış kümesinden sınıfları yüklenir. Görsel tasarımcılar için gerekli erişim sınıfları ve özel araçları tarafından oluşturulan dosyaları içinde tanımlanan türler için de olabilir.  
  
 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Ve [!INCLUDE[csprcs](../../includes/csprcs-md.md)] proje sistemleri üretilen sınıfları ve türleri, geçici taşınabilir erişmek için destek sağlar yürütülebilir dosyalar (geçici PEs). Böylece türleri Bu derlemelerden yüklenmedi ve tasarımcılar, kullanıma sunulan özel bir araç tarafından oluşturulan herhangi bir dosya geçici bir bütünleştirilmiş kod içine derlenmiş. Her özel aracın çıktısının ayrı bir geçici PE derlenir ve başarısı veya başarısızlığı geçici bu derleme yalnızca olup olmadığını oluşturulan dosyanın derlenebilir üzerinde bağlıdır. Bir proje, bir bütün olarak oluşturulamayabilir olsa da, tek tek geçici PEs tasarımcılar, kullanılabilir olabilir.  
  
 Bu değişiklikler özel aracın çalıştırmanın sonuçlarını olması koşuluyla proje sistemi bir özel aracı çıkış dosyasına değişiklikleri izlemek için tam destek sağlar. Özel aracın her çalıştırıldığında yeni bir geçici PE oluşturulur ve tasarımcılar, uygun bildirimler gönderilir.  
  
> [!NOTE]
>  Geçici program oluşturma yürütülebilir dosyası arka planda gerektiğinden, derleme başarısız olursa hata kullanıcıya raporlanır.  
  
 Geçici PE destekten yararlanın özel araçlar, aşağıdaki kurallara uymalıdır:  
  
-   `GeneratesDesignTimeSource` 1 olarak kayıt defterinde ayarlamanız gerekir.  
  
     Hiçbir programı yürütülebilir dosyanın derleme, bu ayar olmadan gerçekleşir.  
  
-   Oluşturulan kodun genel proje ayarı aynı dilde olması gerekir.  
  
     Geçici PE ne özel araç istenen uzantı olarak raporlar bağımsız olarak derlenir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> koşuluyla `GeneratesDesignTimeSource` kayıt defterinde 1 olarak ayarlanır. Uzantısı .vb veya .cs .jsl olması gerekmez; Bu uzantıyı olabilir.  
  
-   Özel araç tarafından oluşturulan kodu geçerli olması gerekir ve kendi yalnızca başvuruları projedeki mevcut kümesini kullanarak zaman derlemelisiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> tamamlandıktan yürütülüyor.  
  
     Geçici PE derlendiğinde, özel araç çıktısı için derleyici sağlanan yalnızca kaynak dosyası değil. Bu nedenle, bir geçici PE kullanan özel bir araç, diğer dosyalar projesinde bağımsız olarak derlenebilir Çıkış dosyalarını oluşturmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [BuildManager nesnesine giriş](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Tek dosya oluşturucular ekleme](../../extensibility/internals/implementing-single-file-generators.md)   
 [Bir projenin varsayılan Namespace belirleme](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Tek Dosya Oluşturucuları Kaydetme](../../extensibility/internals/registering-single-file-generators.md)

