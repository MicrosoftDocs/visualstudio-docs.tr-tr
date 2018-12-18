---
title: Müşteri Deneyimi Geliştirme Programı
description: Visual Studio'da gizlilik ayarlarının nasıl yönetileceğini öğrenin.
ms.date: 05/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba68d0d369d178606777944c9dc4dcd633a503f4
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280650"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Visual Studio Müşteri Deneyimini Geliştirme Programı

Visual Studio Müşteri Deneyimi Geliştirme Programı (VSCEIP), zaman içinde Visual Studio geliştirmesine yardımcı olmak için tasarlanmıştır. Bu program [hatalar hakkında bilgi toplar](../ide/diagnostic-data-collection.md), bilgisayar donanımı ve kullanıcıların bilgisayardaki görevlerini kesintiye uğratmadan kişi Visual Studio nasıl kullanır. Toplanan bilgiler, Microsoft'un hangi özellikleri iyileştireceğini belirlemesine yardımcı olur. Bu belge içinde veya dışında VSCEIP opt alınmaktadır.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]

## <a name="opt-in-or-out"></a>Giriş veya çıkış iptal et

VSCEIP varsayılan olarak açıktır. Kapatın veya, bu yönergeleri izleyerek yeniden açın:

1. Visual Studio'yu başlatın.

1. Gelen **yardımcı** menüsündeki **geri bildirim gönder**ve ardından **ayarları**.

   **Visual Studio Deneyimini Geliştirme Programı** iletişim kutusu açılır.

1. Geri çevirmek için seçin **Hayır, katılmak istiyorum değil**ve ardından **Tamam**.
   Kabul için seçin **Evet, katılmak istiyorum**ve ardından **Tamam**.

   ![Visual Studio Deneyimini Geliştirme Programı iletişim](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Kayıt defteri ayarları

Yüklerseniz [derleme araçları Visual Studio için](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), VSCEIP yapılandırmak için kayıt defterini güncelleştirmeniz gerekir. Kurumsal müşteriler, kayıt defteri tabanlı bir ilke ayarlayarak içinde veya dışında VSCEIP kabul etmek için bir Grup İlkesi oluşturabilirsiniz.

İlgili kayıt defteri anahtarı ve ayarlar aşağıdaki gibidir:

64-bit işletim sistemlerinde, anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM** 32-bit işletim sistemlerinde, anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM** olduğunda Grup İlkesi olan etkinse, anahtar = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

Giriş = **OptIn**

Değer = (DWORD)
- **0** alma (VSCEIP Kapat) seçti
- **1** (VSCEIP etkinleştirin) seçti

> [!CAUTION]
> Kayıt defterinin hatalı düzenlenmesi sisteminize ciddi şekilde zarar verebilir. Kayıt defterinde değişiklik yapmadan önce, bilgisayarınızdaki tüm değerli verileri yedeklemelisiniz. Aynı zamanda **bilinen son iyi yapılandırma** el ile yapılan değişiklikler uygulandıktan sonra sorunlarla karşılaşırsanız başlangıç seçeneği.

İşlenen veya aktarılan VSCEIP tarafından toplanan, bilgileri hakkında daha fazla bilgi için bkz [Microsoft gizlilik bildirimi](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio tarafından toplanan tanılama bilgileri](diagnostic-data-collection.md)
* [Bizimle iletişime geçin](../ide/talk-to-us.md)
* [Visual Studio ile ilgili bir sorun bildirme](../ide/how-to-report-a-problem-with-visual-studio-2017.md)
* [Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/)
* [Microsoft gizlilik bildirimi](https://privacy.microsoft.com/privacystatement)
