---
title: Sorun giderme ve bilinen sorunlar (Unity için Visual Studio Araçları) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 94240d5af43944b23890a32b757fe1b4f14b77ec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755514"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Sorun Giderme ve Bilinen Sorunlar (Unity için Visual Studio Araçları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu bölümde, bilinen sorunların açıklamalarını Unity için Visual Studio Araçları ile sık karşılaşılan sorunlara çözümler bulmak ve Unity için Visual Studio Araçları hata bildirimi tarafından geliştirilmesine nasıl yardımcı olabileceğini öğrenin.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Unity için Visual Studio Araçları ile ilgili bazı yaygın sorunları çözmek için aşağıdaki bölümlere bakın.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>UnityVS, Unity için Visual Studio Araçları geçirme  
 Unity için Visual Studio Araçları için UnityVS geçiriyorsanız, Unity projelerinize ait yeni Visual Studio çözümleri oluşturmak gerekir.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Unity projeniz UnityVS 1.8 ' Visual Studio Araçları için Unity 1.9 geçirmek için  
  
1.  Unity projenizden eski çözüm ve proje dosyaları silin. Visual Studio .sln Unity proje kök dizininde bulun ve. * proj dosyaları ve tüm bunları silin.  
  
2.  Unity paketini için Visual Studio Araçları, Unity projesine içeri aktarmalısınız. VSTU paketini içeri aktarma hakkında daha fazla bilgi için Unity için Visual Studio Araçları yapılandırma bakın [Başlarken](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) sayfası.  
  
3.  Yeni çözüm ve proje dosyalarını oluşturur. Bunları şimdi Unity Editor'ana menüsündeki oluşturmak istiyorsanız seçin **Visual Studio Araçları**, **proje dosyaları oluştur**. Aksi takdirde, istiyorsanız bu adımı atlayabilirsiniz; Unity için Visual Studio Araçları oluşturacağını yeni dosyalar otomatik olarak seçtiğiniz zaman **Visual Studio Araçları**, **Visual Studio'da Aç**.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Visual Studio Unity için Visual Studio Araçları oluşturulan çözüm yüklenmiyor  
 Daha fazla bilgi için [bu stackoverflow sorusunun yanıtını](http://stackoverflow.com/a/24035907/36702).  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>Windows 8'de Visual Studio Unity hedef Framework'ü indirmek sorar.  
 UnityVS, Windows 8'de varsayılan olarak yüklü değilse .net framework 3.5 gerektirir. Bu sorunu gidermek için indirmek ve .net framework 3.5 yüklemek için yönergeleri izleyin.  
  
## <a name="known-issues"></a>Bilinen Sorunlar  
 Bilinen sorunlar vardır, hata ayıklayıcı Unity'nın daha eski C# Derleyici sürümü ile nasıl etkileştiğini gelen neden Visual Studio Araçları Unity için. Bu sorunları çözmek için çalışıyoruz ancak bu sırada aşağıdaki sorunlarla karşılaşabilirsiniz.  
  
-   Hata ayıklama sırasında Unity bazen kilitleniyor.  
  
-   Unity bazen hata ayıklama sırasında donuyor.  
  
-   İçine ve dışına yöntemleri bazen Adımlama özellikle yineleyiciler veya switch deyimleri içinde yanlış bir şekilde davranır.  
  
## <a name="reporting-errors"></a>Hata Raporlama  
 Lütfen kilitlenen, donuyor veya diğer hatalarla karşılaşırsanız, hata raporları göndermek kalite Unity için Visual Studio Araçları'nın geliştirmemize yardımcı olun. Bu, bize araştırmak ve Unity için Visual Studio Araçları'ndaki sorunları gidermeye yardımcı olur. Teşekkür ederiz!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Visual Studio donuyor olduğunda bir hata bildirme  
 Visual Studio bazen Unity için Visual Studio Araçları ile hata ayıklama sırasında donuyor raporlar vardır, ancak bu sorunu anlamak için daha fazla veriye ihtiyacımız. Bize aşağıdaki adımları izleyerek araştırmanıza yardımcı olabilir.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Visual Studio Unity için Visual Studio Araçları ile hata ayıklama sırasında donuyor bildirmek için  
  
1. Visual Studio'nun yeni bir örneğini açın.  
  
2. İşleme İliştir'iletişim kutusunda açın. Yeni Visual Studio örneğinde ana menüsündeki seçin **hata ayıklama**, **iliştirme**.  
  
3. Hata ayıklayıcı, Visual Studio dondurulmuş örneğine ekleyin. İçinde **iliştirme** iletişim kutusunda, Visual Studio'dan dondurulmuş örneğini seçin **kullanılabilir işlemler** tablosuna ve sonra seçin **iliştirme** düğmesi.  
  
4. Hata ayıklayıcı duraklatın. Yeni Visual Studio örneğinde ana menüsündeki seçin **hata ayıklama**, **tümünü Kes** veya tuşuna basarak **Ctrl + Alt + Break**.  
  
5. Bir iş parçacığı dökümü oluşturun. Komut penceresinde komut enter tuşuna basarak aşağıdaki **Enter**.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Yapmanız gerekebilecek **komut** pencere ilk görünür. Visual Studio'da ana menüde seçin **görünümü**, **diğer Windows**, **komut penceresi**.  
  
6. Son olarak, iş parçacığı-dökümü gönderme [ vstusp@microsoft.com ](mailto:vstusp@microsoft.com), ne zaman yapmakta olduğunuz açıklaması ile birlikte Visual Studio dondurulmuş hale geldi.

