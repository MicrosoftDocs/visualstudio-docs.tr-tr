---
title: Sorun raporları için özel veriler
ms.date: 06/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21515d6e9841d943cf91799224afdebf8326e07e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836833"
---
# <a name="developer-community-data-privacy"></a>Geliştirici Topluluğu veri gizliliği

Varsayılan olarak, tüm bilgiler, sorun raporları hakkında [Geliştirici topluluğu](https://developercommunity.visualstudio.com/), herhangi bir yorum ve yanıtları dahil olmak üzere, genel olarak görülebilir. Sorunları, çözümler ve diğer kullanıcıların bulunan geçici çözümleri görmek tüm topluluğuna izin verdiğinden, bu yararlıdır. Ancak, veri veya kimlik gizliliğini endişeleriniz varsa seçeneğiniz vardır.

## <a name="identity-privacy"></a>Kimlik gizliliği

Kimliğinizi göstermeden hakkında endişeleriniz varsa [yeni bir Microsoft hesabı oluşturma](https://signup.live.com/) ilgili tüm ayrıntıları açıklamaz. Raporunuzu oluşturmak için bu hesabı kullanın.

## <a name="data-privacy"></a>Veri gizliliği

Veri gizliliği hakkında endişeleriniz varsa, özel bir başlık ya da her zaman genel ilk rapor içeriği tutmak istediğiniz herhangi bir şey yerleştirmeyin. Bunun yerine, rapor oluşturma ve ardından ayrıntılar özel olarak ayrı bir açıklama için göndereceğiz unutmayın. Sorun raporu oluşturduktan sonra yanıtları ve eklerini kimlerin görebileceğini belirtebilirsiniz:

1. Oluşturduğunuz bir raporda seçin **açıklama ekleme** özel bir sorunun açıklamasını oluşturmak için.

2. Yanıt Düzenleyicisi'nde, aşağıdaki denetim kullanmak **Gönder** ve **iptal** yanıtınız hedef kitlesini belirtmek için düğmeler. Seçin **Moderatörler ve özgün posteri Viewable** Microsoft çalışanları ve kendiniz için görünürlük sınırlamak için.

   ![Geliştirici topluluğu denetimde gizlilik](media/developer-community-privacy-control.png)

   Yalnızca belirttiğiniz kişiler, açıklamayı ve tüm görüntüleri, bağlantılar veya kod içine dahil görebilirsiniz. Bus'dan yorum altında özgün açıklamayı olarak aynı görünürlük vardır. Yanıtları gizlilik denetimi kısıtlı görünürlük durumunu doğru şekilde göstermiyor olsa bile bu geçerlidir.

3. Açıklama ve tüm diğer bilgileri, görüntüleri ve dosya ekleri, yineleme için gereken ekleyin. Seçin **Gönder** özel olarak bu bilgileri göndermek düğmesi.

   > [!NOTE]
   > Ekli dosya çubuğunda bir 2 GB'lık sınırı ve en fazla 10 dosya yok. Daha büyük bir dosya karşıya yükleme gerekiyorsa, yeni bir sorun raporu gönderme veya bir Microsoft çalışanı özel bir yorum gelen istek bir karşıya yükleme URL'si.

Gizliliğinizi korumak ve hassas bilgiler genel görünümü dışında tutmak için Microsoft ile tüm etkileşimler yanıtlara görünürlük sınırlı bir yorum altında tutmak için dikkatli olun. Diğer açıklamaları yanıtlar hassas bilgilerin yanlışlıkla açığa neden olabilir.

## <a name="data-we-collect"></a>Topladığımız veriler

Varsa **sorun bildir** başlatılan Visual Studio Yükleyicisi'nden en son kurulum günlüğü'nü toplarız.

Varsa **sorun bildir** başlatılan bir veya daha fazla aşağıdaki veri türlerini topladığımız Visual Studio'dan:

- Olay günlüğü girişlerinden Watson ve .NET

- Visual Studio bellek içi etkinlik günlüğü dosyası

- PerfWatson dosyaları, Watson toplama etkinse, gelen *VSFeedbackPerfWatsonData* klasörü

- LiveShare günlük dosyaları, varsa, gelen *VSFeedbackVSRTCLogs* klasörü

- Xamarin günlük dosyaları, varsa, gelen *%LOCALAPPDATA%\Xamarin\Logs*

- Varsa, Nuget günlük dosyaları, gelen *%TEMP%\NuGetScratch\nuget-dg\nugetSpec.dg*

- Varsa web hata ayıklayıcı günlük dosyaları:

   - *%Temp%\vscode-Chrome-Debug.txt*

   - *%Temp%\vscode-node-debug2.txt*

   - *%Temp%\vscode-Edge-Debug.txt*

- Bir ekran dahil seçeneğini belirlerseniz,

- Veri içeren bir kayıt eklemek isterseniz kaydı:

   - Sorunu yeniden oluşturma adımları

   - ETL izleme dosyası

   - Döküm dosyası

    > [!NOTE]
    > Raporu göndermeden önce göndermek istemediğiniz veri kaydını silebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile ilgili bir sorun bildirme](how-to-report-a-problem-with-visual-studio-2017.md)
- [C++ sorun rapor veri gizliliği](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)