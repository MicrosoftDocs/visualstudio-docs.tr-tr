---
title: Tanılama veri ve sistem tarafından oluşturulan günlükleri
ms.date: 05/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: michma
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f55d8a0f32886ed477026e298ed2c8c5d6e26f16
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34478350"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Visual Studio tarafından toplanan sistem tarafından oluşturulan günlükleri

Visual Studio toplar sorunları gidermek ve aracılığıyla ürünün kalitesini artırmak için sistem tarafından oluşturulan günlükleri [Visual Studio Müşteri Deneyimini Geliştirme Programı](visual-studio-experience-improvement-program.md). Bu makalede türlerini topladığımız veri ve biz bunu nasıl kullandığı hakkında bazı bilgiler sağlar. Ayrıca, kişisel ve hassas bilgilerin yanlışlıkla açığa çıkmasına uzantısı yazarlar nasıl önleyebilirsiniz ipuçları sağlar.

## <a name="types-of-collected-data"></a>Toplanan veri türleri

Visual Studio sistem tarafından oluşturulan günlükleri çökme, askıda, UI yanıt vermeyi durdurma sorununu ve yüksek CPU veya bellek kullanımını toplar. Kullanım veya ürün yükleme sırasında oluşan hatalar hakkında bilgileri de toplarız. Toplanan veriler hatası göre değişir ve Yığın izlemeleri, bellek dökümlerini ve özel durum bilgileri aşağıdakileri içerebilir:

- Yüksek CPU kullanımı ve yanıt vermeyi durdurma sorununu için ilgili Visual Studio iş parçacığı Yığın izlemeleri toplanır.

- Örneğin, kilitlenme, askıda veya yüksek bellek kullanımı, bir sorun olduğu bazı iş parçacığı Yığın izlemeleri olmayan kök belirlemek için yeterli durumlarda neden bir bellek topladığımız *döküm*. Hata oluştuğunda döküm işlemin durumunu temsil eder.

- Beklenmeyen hata koşulları, disk üzerindeki bir dosyasına yazmaya çalışırken hata Örneğin, bir özel durum için şu özel durum hakkında bilgi toplayın. Bilgiler, özel durum, özel durumun oluştuğu iş parçacığı yığın izlemesi, özel durum ve belirli özel durumla ilgili diğer bilgileri ile ilişkili ileti adını içerir.

   Toplanan verilerin aşağıdaki örnek, bir özel durum adı, yığın izleme ve özel durum iletisi gösterir:

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

## <a name="how-we-use-system-generated-logs"></a>Sistem tarafından oluşturulan günlükleri nasıl kullanırız

Bir hata kök nedenini belirlemek için iş akışı hata ve önemine türüne bağlı olarak değişir.

### <a name="error-classification"></a>Hata sınıflandırma

Günlükleri bağlı olarak, hataları sınıflandırılmış ve bunların araştırma önceliğini belirlemek için sayılır. Örneğin, biz keşfedebilir "System.IO. \__Error.WinIOError ""System.IO.FileStream.Init "sürümünde 500 kez oluştu \<x >, ürün ve bu sürümde oluşumu en yüksek hızı sahiptir.

### <a name="work-items-for-tracking"></a>İzleme için iş öğeleri

İş öğeleri tek tek, Önceliklendirilmiş hataları için oluşturulan ve araştırma için mühendisleri atandı. Bu iş öğeleri genellikle Sınıflandırma, öncelik ve hata türü için ilgili tanılama bilgileri içerir. Bu bilgiler hata için toplanan sistem tarafından oluşturulan günlükleri türetilir. Örneğin, bir iş öğesi için bir kilitlenme kilitlenme oluştuğu yığın izlemesi içerebilir.

### <a name="error-investigation"></a>Hata araştırma

Mühendisleri hata kök nedenini belirlemek için bir iş öğesinin kullanılabilir bilgileri kullanın. Bazı durumlarda, bunlar iş öğesi, varsa daha daha fazla bilgi gerekiyor; bu durumda, toplanan özgün sistem tarafından oluşturulan günlüğüne başvurun. Örneğin, bir mühendislik ürün çökmeyle anlamak için bellek dökümü inceleyin.

## <a name="tips-for-extension-authors"></a>Uzantı yazarları için ipuçları

Uzantı yazarlar kullanarak kişisel olmayan kişisel bilgileri ve diğer hassas bilgiler adlarını kendi modülleri, türleri ve yöntemleri riskini sınırlamanız gerekir. Yığında kodu ile bir kilitlenme veya benzer bir hata koşuluna meydana gelirse, bu bilgileri sistem tarafından oluşturulan günlükleri bir parçası olarak toplanan.

## <a name="opt-out-of-data-collection"></a>Veri toplama dışında iptal et

Topladığımız veri ve erişim ve saklama kısıtlamalar amacı verildiğinde, Visual Studio ve Windows için varsayılan gizlilik ayarları kullanmanızı öneririz. Ancak, [çıkma](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) , Visual Studio deneyimini geliştirme programı. Tüm programları için sistem tarafından oluşturulan günlük toplama dışında kabul etmek için bkz: [Tanılama, geri bildirim ve Windows 10 gizlilik](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Seçenekler, kullandığınız Windows sürümüne bağlı olarak değişebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Müşteri Deneyimi Geliştirme Programı](visual-studio-experience-improvement-program.md)
- [Tanılama, geri bildirim ve Windows 10 gizlilik](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)