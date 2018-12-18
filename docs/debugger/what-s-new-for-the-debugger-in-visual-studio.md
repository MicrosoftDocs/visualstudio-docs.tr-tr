---
title: Hata Ayıklayıcı'Visual Studio 2017'deki yenilikler | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 342cb6c1f014c94bd86363415177ec747b0dc1b7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943147"
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>Hata Ayıklayıcısı'ndaki yenilikler nelerdir? [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Hata ayıklayıcı bu yeni özellikler içerir:

- 15.5, yeni **Snapshot Debugger** ilgilendiğiniz kod yürütüldüğünde, üretim uygulamalarınızı anlık görüntüsünü alır. Bir anlık görüntüsünü almak için hata ayıklayıcı açmasını sağlamak için anlık görüntü noktaları ve günlüğe kaydetme noktaları kodunuzda ayarlayın. Hata ayıklayıcı, tam olarak üretim uygulamanızın trafiğini etkilemeden, çıktığına görmenizi sağlar. Snapshot Debugger, üretim ortamlarında ortaya çıkan sorunları çözmek için gereken süreyi ciddi ölçüde azaltmaya yardımcı olabilir.

    Anlık görüntü koleksiyonunu, Azure App Service'te çalışan aşağıdaki web uygulamaları için kullanılabilir:

  * .NET Framework 4.6.1 üzerinde çalışan ASP.NET uygulamalarından veya üzeri.
  * .NET Core 2.0 veya daha sonra Windows üzerinde çalışan ASP.NET Core uygulamaları.

    Daha fazla bilgi için [Snapshot Debugger'ı kullanarak canlı ASP.NET uygulamaları için hata ayıklama](../debugger/debug-live-azure-applications.md).

- Yalnızca, 15.5 Visual Studio Enterprise sürümünde yeni **IntelliTrace geri adım** otomatik olarak adım olay her bir kesme noktası ve hata ayıklayıcı uygulamanızın anlık görüntüsünü alır. Kaydedilen anlık görüntü, önceki kesme noktaları veya adımlara geri dönün ve daha önce olduğu gibi uygulama durumunu görüntülemek etkinleştirin. IntelliTrace geri adım atma önceki uygulama durumu görmek istiyorsanız ancak hata ayıklamayı yeniden başlatın veya istenen uygulama durumu yeniden istemediğiniz durumlarda size zaman kazandırabilir.

    Gidin ve anlık görüntüleri kullanarak görüntüle **adım geriye dönük** ve **İleri** hata ayıklama araç çubuğu düğmeleri. Bu düğmeler görünen olaylar gidin **olayları** sekmesinde **tanılama araçları** penceresi.

    ![Geri ve İleri düğmelerini adım](../debugger/media/intellitrace-step-back-icons-description.png  "adım geri ve İleri düğmelerini")

    Daha fazla bilgi için [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md) sayfası.

- **Özel durum Yardımcısı** özel durum Yardımcısı'nı değiştirir ve hatanın oluştuğu kalıcı olmayan iletişim kutusunda görüntülenir. **Özel durum Yardımcısı** herhangi bir iç özel durumlar, hata ayıklayıcı (varsa) tarafından ek çözümleme için daha hızlı erişim ve anında erişim sağlayan **özel durum ayarları** özel durum için. Görmek için gereken bir şey engelleyip engellemediğini özel durum Yardımcısı de kayan görünümüne sürüklenebilir.

    Örneğin, bir **NullReferenceException** artık null başvuru (ek bilgiler) sahip bir değişkeni gösterir.

    ![Hata Ayıklayıcı'nın özel durum Yardımcısı](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Daha fazla bilgi için [Visual Studio'da yeni bir özel durum Yardımcısı kullanarak](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) blog gönderisi.

- Artık bir hata ayıklayıcıda seçerek duraklatıldığı sırada kod satırı için çalıştırabilirsiniz **yürütme işlemini burada Çalıştır** yeşil ok simgesi (gördüğünüz simgesi bir kod satırının gelindiğinde). Bu, geçici kesme noktaları ayarlama gereğini ortadan kaldırır.

    ![Hata ayıklayıcı için tıklatın çalıştırmasını](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Özel durumlarda koşulları ayarlayabilirsiniz **özel durum ayarları** iletişim kutusu (kullanarak bunu yapabilirsiniz **koşulu Düzenle** özel durum Ayarları iletişim kutusunda veya sağ tıklama menüsünü kullanarak simgesi özel durum.) Şu anda desteklenen koşullar dahil etmek veya hariç tutmak için bir özel durum için modül adlarını içerir.

    ![Bir özel durum koşullara](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Daha fazla iliştirmek istediğiniz işlemi hızla tanımlamanıza yardımcı olacak yeni bir arama özelliği içerikleri iletişim kutusu işleme iliştirin.

    ![Aramada iliştirme](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Bu yeni özellikler hakkında daha fazla bilgi için bkz. [için sürüm notları [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes#debuggingdiag).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da hata ayıklama](../debugger/index.md)
- [Hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)