---
title: IntelliTrace | Microsoft Docs
ms.custom: ''
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2ee2e3662e550e013b2f8436cc32ee9585a419d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825427"
---
# <a name="intellitrace"></a>IntelliTrace

Kodunuzun yürütme geçmişini izlemek ve kaydetmek için IntelliTrace kullandığınızda, uygulamanızın hata ayıklama daha az zaman ayırabilirsiniz. IntelliTrace aşağıdakileri yapmanıza olanak sağladığından hataları kolayca bulabilirsiniz:

- Kayıt belirli olayları

   İlgili kodu, görünen verileri incelemek **Yereller** penceresi sırasında hata ayıklayıcı olayları ve çağrı bilgileri işlevi

- Yeniden oluşturulması zor olan veya dağıtımda gerçekleşen hataları hata ayıklama

IntelliTrace, Visual Studio Enterprise edition (ancak Professional veya Community sürümlerini değil) kullanabilirsiniz.

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|||
|-|-|
|**Uygulamamın IntelliTrace ile hata ayıklama:**<br /><br /> -Geçmişteki olayları göster.<br />-Geçmiş olaylar ile ilgili çağrı bilgilerini göster.<br />-IntelliTrace Oturumumu Kaydet.<br />-Intellitrace'in topladığı verileri kontrol et.|- [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md)<br />- [İzlenecek yol: IntelliTrace'i kullanma](../debugger/walkthrough-using-intellitrace.md)<br />- [IntelliTrace özellikleri](../debugger/intellitrace-features.md)<br />- [Geçmiş hata ayıklama](../debugger/historical-debugging.md)|
|**Test Yöneticisi'nde bir sınama oturumu sırasında IntelliTrace verisi Topla**|- [El ile testlerde daha fazla tanılama verisi toplama](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|
|**Dağıtılmış uygulamalardan IntelliTrace verilerini toplama**|- [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Bir IntelliTrace günlük dosyasından (.iTrace dosyası) hata ayıklamayı başlatın.**|- [Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)|

## <a name="IntelliTraceSupport"></a> IntelliTrace ile hangi uygulamaların ayıklayabilirim?

| | |
|---------------------| - |
| **Tam destek** | -.NET Framework 2.0 veya üzeri sürümleri kullanan Visual Basic ve Visual C# uygulamalar.<br/>ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows iş akışı, SharePoint 2010, SharePoint 2013 ve 64-bit uygulamalar da dahil olmak üzere çoğu uygulamada hata ayıklaması yapabilirsiniz.<br/>IntelliTrace ile SharePoint uygulamalarında hata ayıklamak için bkz: [izlenecek yol: bir SharePoint uygulaması tarafından IntelliTrace kullanarak hata ayıklama](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> Microsoft Azure uygulamalarında IntelliTrace ile hata ayıklamak için bkz: [bulut hizmet yayımlanan IntelliTrace ve Visual Studio ile hata ayıklama](/azure/vs-azure-tools-intellitrace-debug-published-cloud-services). |
| **Sınırlı destek** | -Windows Destek IntelliTrace geri adım atmayı kullanarak anlık görüntüleri görüntüleme hedefleyen yerel uygulamalar. Yalnızca hata ayıklayıcı ve özel durum olaylarını desteklenir.<br />-.NET core ve ASP.NET Core uygulamaları yerel hata ayıklama belirli olaylar yalnızca (MVC denetleyicisi, ADO.NET ve HTTPClicent olaylar) desteklenir. Tek başına Toplayıcı, .NET Core veya ASP.NET Core uygulamaları için desteklenmez.<br />-Deneysel olarak F # uygulamaları<br />-Yalnızca olaylar için desteklenen UWP uygulamaları |
| **Desteklenmiyor** | -Diğer diller ve komut dosyası<br />-Windows Hizmetleri, Silverlight, Xbox veya [!INCLUDE[winmobile](../debugger/includes/winmobile_md.md)] uygulamaları |

> [!NOTE]
> Zaten çalışan bir işlemde hata ayıklamak istiyorsanız, yalnızca IntelliTrace olayları (çağrı bilgileri) toplayabilir. Yerel makinede yalnızca bir 32 bit veya 64-bit işleme iliştirebilirsiniz. İşleme İliştir önce meydana gelen olayları toplanmadı.

##  <a name="IntelliTraceVSTraditional"></a> Neden IntelliTrace ile hata ayıklama?

Geleneksel veya *canlı* hata ayıklama sadece uygulamanızın geçerli durumunu gösterir, geçmiş olaylar hakkında sınırlı veri ile. Bu olayları uygulamanın mevcut durumuna göre ya da sahip veya bu olayları uygulamanızı yeniden çalıştırarak yeniden oluşturmanız gerekir.

IntelliTrace bu zamanlardaki belirli olayları ve verileri kaydederek bu geleneksel hata ayıklama deneyimini genişletir. Bu, özellikle hatanın bulunduğu son adım, uygulamanızda, yeniden başlatmadan ne görmenize olanak sağlar. IntelliTrace geleneksel hata ayıklama işlemi sırasında varsayılan olarak açıktır ve görünmez ve otomatik olarak veri toplar. Bu, geleneksel hata ayıklama ve IntelliTrace hata ayıklama arasında kaydedilen bilgileri görmek için kolayca geçiş yapmanızı sağlar. Bkz: [IntelliTrace özellikleri](../debugger/intellitrace-features.md) ve [IntelliTrace hangi verileri toplar?](#WhatData)

IntelliTrace yeniden oluşturulması zor olan veya dağıtımda gerçekleşen hataları ayıklamaya da yardımcı olabilir. IntelliTrace verisi toplayabilir ve bir IntelliTrace günlük dosyasına (.iTrace dosyası) kaydedebilirsiniz. Bir .iTrace dosyası özel durumlar, performans olayları, Web istekleri, test verileri, iş parçacıkları, modüller ve diğer sistem bilgileri ile ilgili ayrıntıları içerir. Visual Studio Enterprise'da bu dosyayı açmak, bir öğe seçin ve IntelliTrace ile hata ayıklamaya başlayabilirsiniz. Bu, herhangi bir olaya dosyasına gidin ve zaman içinde o noktadaki uygulamanız hakkındaki özel ayrıntıları sağlar.

Bu kaynaklardan IntelliTrace verisi kaydedebilirsiniz:

- Visual Studio 2017 Enterprise, Visual Studio 2015 Enterprise veya Visual Studio Ultimate'nın önceki sürümlerini bir IntelliTrace oturumu.

- Microsoft Test Yöneticisi'nde bir sınama oturumu

- IIS'de barındırılan ASP.NET web uygulamaları ya da Microsoft Monitoring Agent kullandığınızda dağıtımda tek başına ya da System Center 2012 ile birlikte çalışan SharePoint 2010 ve SharePoint 2013 uygulamaları. Bkz: [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md) ve [Microsoft Monitoring Agent ile izleme](http://technet.microsoft.com/library/dn465153.aspx).

  IntelliTrace'in hata ayıklamada yardımcı olması ile ilgili bazı örnekler aşağıdadır:

- Uygulamanız bir veri dosyasını bozdu, ancak bu olayın nerede meydana geldiğini bilmiyorsunuz.

     IntelliTrace olmadan, tüm olası dosya erişimlerini bulmanız, bu erişimlere kesme noktaları yerleştirmek için kodu aracılığıyla bakmamız gerekiyor ve sorunun nerede meydana geldiğini bulmak için uygulamanızı yeniden çalıştırın. Her olay meydana geldiğinde IntelliTrace ile tüm toplanan dosya erişimi olaylarını ve belirli ayrıntıları hakkında uygulamanızı görebilirsiniz.

- Bir özel durum gerçekleşir.

     IntelliTrace olmadan, bir özel durum hakkında bir ileti alırsınız ama özel duruma yol açan olaylar hakkında daha bilgi yok. Özel duruma yol açan çağrı zincirini görmek için çağrı yığınını inceleyebilirsiniz ancak bu çağrılar sırasında gerçekleşen olayların sırasını göremezsiniz. IntelliTrace ile özel durumdan önce meydana gelen olayları inceleyebilirsiniz.

- Uygulamanız sınama bilgisayarında çöküyor ancak geliştirme bilgisayarında başarıyla çalışır.

     Microsoft Test Yöneticisi'nden IntelliTrace verisi toplayabilir, verileri .iTrace dosyasına kaydedebilir ve bu dosyayı daha sonra incelemek için Team Foundation Server çalışma öğesine ekleyebilirsiniz. Bkz: [el ile testlerde daha fazla tanılama verisi toplama](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts) ve [kullanım kaydedilen IntelliTrace verilerini](../debugger/using-saved-intellitrace-data.md).

- Dağıtılan bir uygulamada hata veya kilitlenme oluşur.

     Uygulamayı yayımlamadan önce Microsoft Azure tabanlı uygulamalar için IntelliTrace veri toplamayı yapılandırabilirsiniz. Uygulamanız çalışırken, IntelliTrace veriyi bir .iTrace dosyasına kaydeder. Bkz: [IntelliTrace ve Visual Studio ile yayımlanan bulut hizmeti hata ayıklama](http://go.microsoft.com/fwlink/?LinkID=262248).

     IIS 7.0, 7.5 ve 8.0'da barındırılan ASP.NET web uygulamaları ve SharePoint 2010 ya da SharePoint 2013 uygulamalarında, IntelliTrace verisini bir .iTrace dosyasına kaydetmek için Microsoft İzleme Aracısı'nı tek başına ya da System Center 2012 ile birlikte kullanın.

     Bu, dağıtımdaki uygulamalarla ilgili sorunları tanılamak istediğinizde kullanışlıdır. Bkz: [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md).

##  <a name="WhatData"></a> IntelliTrace hangi verileri toplar?

**Olay bilgilerini toplama**

Varsayılan olarak, IntelliTrace yalnızca IntelliTrace olayları kaydeder: hata ayıklayıcı olayları, özel durumlar, .NET Framework olayları ve hata ayıklamaya yardımcı olabilecek diğer sistem olaylarıdır. Hata ayıklayıcı olayları ve her zaman toplanan özel durumlar dışında toplamak istediğiniz IntelliTrace olaylarının türlerini seçebilirsiniz. Bkz: [IntelliTrace özellikleri](../debugger/intellitrace-features.md).

- **Hata ayıklayıcı olayları**

     IntelliTrace her zaman Visual Studio hata ayıklayıcıda gerçekleşen olayları kaydeder. Örneğin, uygulamanızın başlatma bir hata ayıklayıcı olayıdır. Diğer hata ayıklayıcı olayları, uygulamanızın yürütmeyi kesmesine neden olan Durma olaylarıdır. Örneğin, programınız bir kesme noktasına denk gelir, bir izleme noktasına denk veya yürüten bir **adım** komutu.

     Varsayılan olarak, performansa yardımcı olmak için IntelliTrace hata ayıklayıcı olayında olası her değeri kaydetmez. Bunun yerine, bu değerleri kaydeder:

  - Değerler **Yereller** penceresi. Tutun **Yereller** penceresinde bu değerleri görmek için açık.

  - Değerler **Otolar** penceresi **Otolar** penceresini aç

  - Kaynak penceresinde değerini görmek için bir değişkenin üzerine fare işaretçisini getirdiğinizde görüntülenen DataTips değerleri. IntelliTrace sabitlenmiş DataTips değerlerini toplamaz.

    IntelliTrace olayları ve anlık görüntüler modu etkin olduğunda, IntelliTrace her hata ayıklayıcıya uygulamanın işlem anlık görüntüsünü alma **kesme noktası** ve **adım** olay. Bu değerleri kaydeder **Yereller**, **Otolar**, ve **Watch** windows, windows veya açık olup ne olursa olsun. Tüm sabitlenmiş veri ipuçları değerlerde de toplanacak.

- **Özel Durumlar**

     IntelliTrace özel durum türünü ve iletisini bu tür özel durumlar için kaydeder:

    - Özel durumun ortaya çıktığı ve yakalandığı yönetilen özel durumlar

    - Yönetilmeyen özel durumlar

- **.NET framework olayları**

   Varsayılan olarak, IntelliTrace en sık görülen .NET Framework olaylarını kaydeder. Örneğin, bir onay kutusu denetimi olayında, IntelliTrace ror onay kutusunun durumunu ve metnini toplar.

- **SharePoint 2010 ve SharePoint 2013 uygulama olayları**

     Kullanıcı profili olayları ve SharePoint 2010 ile Visual Studio dışında çalışan 2013 uygulamaları için birleşik Günlük Kaydetme Sistemi (ULS) olaylarının alt kümesini kaydedebilirsiniz. Bu olayları bir .iTrace dosyasına kaydedebilirsiniz. Visual Studio Enterprise 2017, Visual Studio Enterprise 2015, Visual Studio Ultimate, bir önceki sürümünü gerektirir veya [Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) çalışan **izleme** modu.

     .iTrace dosyasını açtığınızda, eşleşen web isteğini bulmak için bir SharePoint bağıntı kimliği girin, kayıtlı olayları görüntüleyin ve belirli bir olaydan hata ayıklamaya başlayın. Dosya işlenmeyen özel durumlar içeriyorsa, bir bağıntı kimliği seçerek bir özel durumu hata ayıklamaya başlayabilirsiniz.

     Bkz.

    - [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md)

    - [Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)

    - [İzlenecek yol: IntelliTrace'i Kullanarak SharePoint Uygulamasında Hata Ayıklama](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Anlık Görüntü Yakala**

Her bir kesme noktasında anlık görüntülerini yakalamak ve hata ayıklayıcı, olay adımı için IntelliTrace'i yapılandırabilirsiniz. IntelliTrace, en karmaşık değişkenleri görüntüleyebilir ve nevyhodnocovat sağlayan her anlık görüntü tam uygulama durumunu kaydeder.

Bkz: [IntelliTrace kullanarak önceki uygulama durumlarını incelemek](../debugger/view-historical-application-state.md).

**İşlev çağrısı bilgilerini toplama**

İşlev çağrı bilgilerini toplamak için IntelliTrace'i yapılandırabilirsiniz. Bu bilgiler çağrı yığını geçmişini görmenizi sağlar ve koddaki çağrılarda geri veya ileri hareket edebilmenize izin verir. Her işlev çağrısı için IntelliTrace bu verileri kaydeder:

- İşlev adı
- İşlev giriş noktalarında parametre olarak gönderilen ve işlev çıkış noktalarında döndürülen temel veri türlerinin değerleri
- Okunduklarında veya değiştirildiklerinde otomatik özelliklerin değerleri
- Birinci düzey alt nesnelerin işaretçileri, ancak değerleri yalnızca boş veya değil şeklinde verilir

> [!NOTE]
> IntelliTrace yalnızca dizilerdeki ilk 256 nesneyi ve dizelerdeki ilk 256 karakteri toplar.

Bkz: [geçmiş hata ayıklama ile uygulamanızı denetleyin](../debugger/historical-debugging-inspect-app.md).

**Modül bilgilerini toplama**

IntelliTrace'in ne kadar çağrı bilgisi topladığını denetlemek için, yalnızca istediğiniz modülleri belirtin. Bu uygulamanızın toplama esnasındaki performansını iyileştirmeye yardımcı olabilir. Bölümüne bakın [ne kadar bilgi Intellitrace'in topladığı denetim](../debugger/intellitrace-features.md#ControlCallData) IntelliTrace özellikleri.

## <a name="AffectPerformance"></a> IntelliTrace uygulamamı yavaş?

Varsayılan olarak, IntelliTrace yalnızca seçili IntelliTrace olaylarının verilerini toplar. Bu işlem sonrasında veya aşağı yapısı ve kuruluşuna kodunuzun bağlı olarak uygulamanızı yavaşlatabilir değil. Örneğin, IntelliTrace bir olayı sıklıkla kaydediyorsa, bu sizin uygulamanızı yavaşlatabilir. Bu ayrıca, uygulamanızı yeniden düzenlemeyi düşünmenizi neden olabilir.

Çağrı bilgilerini toplama uygulamanızı önemli ölçüde yavaşlatabilir. Diske kaydettiğiniz IntelliTrace herhangi bir günlük dosyasının (.iTrace dosyaları) boyutunu da artırabilir. Bu etkileri en aza indirmek için yalnızca ilginiz dahilinde olan modüller için çağrı bilgilerini toplayın.  .İTrace dosyalarınızın en büyük boyutunu değiştirmek için Git **Araçları**, **seçenekleri**, **IntelliTrace**, **Gelişmiş**.

## <a name="in-this-section"></a>Bu bölümde

[IntelliTrace Özellikleri](../debugger/intellitrace-features.md)

[Dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md)

[Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)

### <a name="blogs"></a>Bloglar

[Microsoft DevOps](https://blogs.msdn.microsoft.com/devops/)

### <a name="forums"></a>Forumlar

[Visual Studio tanılama](http://go.microsoft.com/fwlink/?LinkId=262263)
