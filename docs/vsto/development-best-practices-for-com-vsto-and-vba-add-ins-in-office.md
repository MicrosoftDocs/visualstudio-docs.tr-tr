---
title: COM, VSTO ve VBA eklentileri için Office geliştirme en iyi uygulamalar
ms.custom: ''
ms.date: 07/25/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3f821b9769b9353fbee6379ddc1b3826f87ac2de
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671099"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>COM, VSTO ve VBA eklentileri için Office geliştirme en iyi uygulamalar
  Office için COM, VSTO veya VBA eklentileri geliştiriyorsanız, bu makalede açıklanan geliştirme en iyi uygulamaları izleyin.   Bu, olmanıza yardımcı olur:

-  Eklentilerinizi farklı sürümleri ve dağıtılmasına Office uyumluluğu.
-  Azaltılmış karmaşıklık eklentisi kullanıcılar ve BT yöneticileri için dağıtım.
-  Eklentinizi, istenmeyen yükleme veya çalışma zamanı hataları gerçekleşmez.

>Not: Kullanarak [Masaüstü köprüsü](/windows/uwp/porting/desktop-to-uwp-root) , COM hazırlamak için VSTO veya VBA eklentisi için Windows Store desteklenmiyor. COM, VSTO ve VBA eklentileri, Windows Store veya Office Store dağıtılamıyor. 
  
## <a name="do-not-check-for-office-during-installation"></a>Office için yükleme sırasında denetleme  
 Office Eklentisi yükleme işlemi sırasında yüklü olup olmadığını algılama eklenti sahip önerilmemektedir. Office yüklü değilse, eklentiyi yükleyin ve kullanıcı Office yüklendikten sonra buna erişebilir. 
  
## <a name="use-embedded-interop-types-nopia"></a>Gömülü birlikte çalışma türleri (NoPIA) kullanın  
Çözümünüz .NET 4.0 kullanıyorsa ya da daha sonra katıştırılmış birlikte çalışma türleri (NoPIA) yerine Office birincil birlikte çalışma derlemeleri (PIA bağlı olarak) yeniden dağıtılabilir. Ekleme türü kullanarak çözümünüzü, yükleme boyutunu azaltır ve gelecekte uyumluluk sağlar. Office 2010 yeniden dağıtılabilir PIA birlikte gelen Office son sürümünü oluştu. Daha fazla bilgi için [izlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](https://msdn.microsoft.com/library/ee317478.aspx) ve [tür eşdeğerliği ve katıştırılmış birlikte çalışma türleri](/windows/uwp/porting/desktop-to-uwp-root).

Çözümünüz .NET önceki bir sürümünü kullanıyorsa, .NET 4.0 veya sonraki sürümü kullanmak için çözümünüzün güncelleştirmenizi öneririz. .NET 4.0 veya sonraki sürümü kullanarak daha yeni sürümlerinde Windows çalışma zamanı önkoşulları azaltır.
  
## <a name="avoid-depending-on-specific-office-versions"></a>Bağlı olarak belirli Office sürümleri kaçının  
Çözümünüzü yalnızca Office daha yeni sürümlerde kullanılabilir olan işlevsellik kullanıyorsa, çalışma zamanında (örneğin, özel durum işleme veya sürüm denetimi tarafından kullanarak) özelliği (Eğer Mümkünse, özellik düzeyinde) bulunduğunu doğrulayın. Nesne modelinde gibi desteklenen API'leri kullanarak, belirli sürümler yerine, en düşük sürümlerle doğrulama [Application.Version özelliği](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Yüklemeleri, ortamlar ve sürümler arasında değiştirebilirsiniz çünkü Office ikili meta verileri, yükleme yolları veya kayıt defteri anahtarlarını kullanan önerilmemektedir.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Hem 32-bit hem de 64 bit Office kullanımını etkinleştir   
Yalnızca belirli bir bit genişliği için kullanılabilen kitaplıkları çözümünüzü bağımlı sürece, varsayılan derleme hedefini hem 32-bit (x86) hem de 64-bit (x64) desteklemelidir. Office'in 64 bit sürümü, özellikle büyük veri ortamlarda bir benimseme artmaktadır. Destek hem 32-bit hem de 64-bit, 32-bit ve 64 bit Office sürümleri arasında geçiş kullanıcılarınızın kolaylaştırır.

VBA kodu yazarken kullanmak için 64-bit güvenli ifadeleri bildirme ve değişkenleri uygun'olarak Dönüştür. Ayrıca, belgeler için her bit genişliği kod sağlayarak Office 32 bit veya 64 bit sürümlerini çalıştıran kullanıcılar arasında paylaşılabilen emin olun. Daha fazla bilgi için [uygulamalara genel bakış için 64 bit Visual Basic](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Kısıtlı ortamlarını destekler   
Çözümünüzü kullanıcı hesabı ayrıcalık veya yönetici ayrıcalıkları gerektirmez. Ayrıca, çözüm ayarlama veya değiştirme bağlı olmaması gerekir:

- Geçerli çalışma dizini.
- DLL dizinleri yükleyin.
- YOLU değişken.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Kayıt değiştirme konumunu paylaşılan veriler ve ayarlar
Çözüm, bir eklenti ve Office harici bir işlemde oluşuyorsa, verileri veya ayarları eklenti ve dış işlem arasındaki değişimi için kullanıcının uygulama verisi klasörü veya kayıt defteri kullanmayın. Bunun yerine, kullanıcının geçici klasörü, Belgeler klasörünü veya çözümünüzün yükleme dizini kullanmayı düşünün.

## <a name="increment-the-version-number-with-each-update"></a>Her bir güncelleştirmeyle sürüm numarasını Artır
Çözümünüzde ikili dosyaları sürüm numarasını ayarlayın ve her bir güncelleştirme ile artırın. Bu sürümler arasındaki değişiklikleri tanımlamak ve uyumluluğunu değerlendirmek kullanıcılar için kolaylaştırır.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>En son Office sürümleri için destek bildirimleri sağlayın
Müşteriler, COM, VSTO ve VBA çalıştıran Office eklentileri için destek bildirimleri sağlamak için ISV seçmenizi istiyoruz. Office 365 ProPlus'ı kullanarak, açık destek deyimleri yardımcı müşterileri listeleme hazırlık araçları destek anlayın. 

Office istemci uygulamaları (Word veya Excel gibi) için destek bildirimleri sağlamak için önce eklentilerinizi geçerli Office sürümde çalıştırın ve ardından eklentinizi gelecekteki bir sürümde keserse güncelleştirmeler sağlamayı tamamlama doğrulayın. Microsoft yeni bir derleme veya Office için bir güncelleştirme yayımladığında eklentilerinizi test etmek zorunda değildir. Microsoft Office'te COM, VSTO ve VBA genişletilebilirlik platform nadiren değiştirir ve bu değişiklikleri iyi belgelenmiştir.

>Önemli: Microsoft hazırlık raporlar ve ISV iletişim bilgileri için desteklenen eklentileri listesini tutar. Listelenen eklentinizi almak için bkz. [ https://aka.ms/readyforwindows ](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Yükleme veya sorunları yüklenirken hata ayıklama yardımcı olması için işlem İzleyicisi'ni kullanın
Eklentinizi uyumluluk sorunları yükleme veya yük varsa, bunlar dosya veya kayıt defteri erişim sorunlarıyla ilgili olabilir. Kullanım [işlem İzleyicisi](/sysinternals/downloads/procmon) veya benzer bir hata ayıklama araç oturum ve sorunun belirlenmesine yardımcı olacak bir çalışma ortamı karşı davranışını karşılaştırın.
