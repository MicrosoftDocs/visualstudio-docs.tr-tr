---
title: Doğrulama ve SharePoint kodda hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 327e7be43fc60142fc50634ec61f6fd9499461e2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120577"
---
# <a name="verify-and-debug-sharepoint-code"></a>Doğrulayın ve SharePoint kodda hata ayıklama
IntelliTrace ve birim testi kullanarak, daha kolay SharePoint çözümlerini hata ayıklama ve bunları her bir yöntemin düzgün çalıştığından emin olun. Bu özellikler, diğer proje türleri için aynı yordamları izleyerek Visual Studio'da SharePoint projeleri için kullanabilirsiniz.

## <a name="intellitrace"></a>IntelliTrace
IntelliTrace kullanarak, yalnızca geçerli durumu, SharePoint çözüm aynı zamanda geçmiş ve gerçekleşen bağlam oluşan olaylarla belirleyebilirsiniz. Çeşitli noktalara zamanında olaylarının nerede kaydedilmiş bir SharePoint çözüm içinde ileri ve geri gidin ve durumları ve her noktada değişkenlerin değerleri gözden geçirin. Bu dinamik Gezinti kullanarak, daha hızlı ve kolay bir şekilde SharePoint çözümlerini çok sayıda kesme noktalarını ayarlayın gerek kalmadan ayıklayabilirsiniz. Hata ayıklama oturumu için bir IntelliTrace günlüğü kaydedebilirsiniz (*.iTrace*) dosya, daha sonra Visual Studio Kurumsal açın ve sonrası crash hata ayıklama gerçekleştirin. *.İTrace* dosyası, böylece daha kolay hatalara neden çıkışı hesaplayabilir ne zaman ve nerede belirli SharePoint hataları oluştu hakkında ayrıntılı bilgi içerir. Bilgileri *.iTrace* dosya Birleşik Günlük sistem (ULS) SharePoint oluşturur tam hata günlüğü bir alt kümesidir. Bu bilgiler SharePoint'e bir kullanıcı profili açık veya kapalı gibi ve özelliklerini bir SharePoint Proje yüklenir, okuma, veya değiştirildiğinde, belirli olayları içerir. IntelliTrace kayıtları olayları yapılandırabilirsiniz. Daha fazla bilgi için bkz: [IntelliTrace verilerini kaydedilmiş kullanma](/visualstudio/debugger/using-saved-intellitrace-data).

SharePoint'te bir hata ortaya çıkarsa, söz konusu hatayla için bir "bağıntı kimliği" tanımlayıcı hata iletişim kutusu görüntüler. Listelenen olaylardan bağıntı kimlikleri alabilirsiniz *.iTrace* dosya. Verilen bağıntı Kimliğine sahip olayları tümünün listesini görüntülemek için Kimliğinde girebilirsiniz **analiz** IntelliTrace Özet sayfasını bölümü. Bu bölümde, yalnızca oluşan olaylarla adlarını veya işlev adı, çıkış ve giriş noktaları, parametreler ve dönüş değerleri gibi kendi çağrısı bilgilerle birlikte olayların adları görüntülenip görüntülenmeyeceğini seçebilirsiniz.

Visual Studio olayları seçerek IntelliTrace elde edebilirsiniz **F5** anahtarı. SharePoint'e özgü olaylar almak için ancak, SharePoint çözümlerinde IntelliTrace verilerini Microsoft Monitoring Agent'ı kullanarak toplamanız gerekir. Bu aracı IntelliTrace verilerini toplar ve oluşturur *.iTrace* dosyaları Visual Studio dışında dağıtılan uygulamalar için. Daha fazla bilgi için bkz: [IntelliTrace özellikleri](/visualstudio/debugger/intellitrace-features) ve [IntelliTrace tek başına toplayıcıyı kullanma](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

## <a name="unit-test"></a>Birim testi
Hata, yazma ve test yöntemleri içinde test kod çalıştırma birim testi, gerçekleştirerek kodunuzu daha kolay bulabilirsiniz. Bu yöntem boş değişkenleri ve mantık ve SharePoint nesne modelini temel alan projenizi işlevselliğini doğrulamak için kullanabileceğiniz bir onay deyimi içerir. Daha fazla bilgi için bkz: [Birim Test kodunuzu](/visualstudio/test/unit-test-your-code).

### <a name="support-for-microsoft-fakes-framework"></a>Microsoft Fakes framework desteği
SharePoint projeleri desteği, .NET Framework temel alınarak uygulamalarda saplamalar ve dolgular temsilci tabanlı oluşturabilirsiniz bir yalıtım Framework Microsoft Fakes sınayın. Fakes framework kullanarak oluşturmak, korumanıza ve sahte uygulamaları için birim testleri ekleme. Bu saplamalar ve dolgular ortamından birim testleri yalıtma. Korumalı olmayan sınıfları veya arabirimleri ile geçersiz kılınabilir yöntemleri tüketir kodu test etmek için yer tutucular oluşturabilirsiniz. Bir alternatif dolgu uygulanması için sabit kodlanmış çağrıları sealed sınıfları statik veya kılınamaz yöntemleriyle yönlendirmek için dolgular oluşturabilirsiniz. Ayrıca temsilciler saplama türlerini ve dolgusu türleri ile dinamik olarak tek tek saplama üyeleri davranışını özelleştirmek için kullanabilirsiniz. Daha fazla bilgi için bkz: [yalıtma kodu altında Microsoft Fakes ile Test](/visualstudio/test/isolating-code-under-test-with-microsoft-fakes).

## <a name="related-articles"></a>İlgili makaleler

|Başlık|Açıklama|
|-----------|-----------------|
|[IntelliTrace](/visualstudio/debugger/intellitrace)|IntelliTrace'i kullanarak Visual Studio çözümleri daha kolay hata ayıklama açıklar.|
|[İzlenecek yol: IntelliTrace'i kullanarak SharePoint uygulama hata ayıklama](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Bulunacak gösterilmiştir IntelliTrace'i kullanarak SharePoint Proje hatalarını kodlama.|
|[Kodunuza Birim Testi Uygulama](/visualstudio/test/unit-test-your-code)|Birim testleri kullanarak kodunuzda mantık hataları bulmak açıklar.|

## <a name="see-also"></a>Ayrıca bkz.
[Kod Kalitesini Geliştirme](/visualstudio/test/improve-code-quality)
